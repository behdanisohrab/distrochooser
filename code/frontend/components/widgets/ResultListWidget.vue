<!--
distrochooser
Copyright (C) 2014-2025 Christoph Müller  <mail@chmr.eu>

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
-->
<template>
  <div>
    <div
      v-for="(choosable, index) in props.widget.choosables.sort(
        (a, b) => b.rank - a.rank
      )"
      :key="index"
    >
      <RankedChoosable :choosable="choosable" />
    </div>
    <div class="alert alert-info" v-if="props.widget.choosables.length == 0">
      <b><LanguageTranslation translation-key="NO_RESULTS_TITLE"/></b>
      <p>
        <LanguageTranslation translation-key="NO_RESULTS_TEXT"/>
      </p>
    </div>
  </div>
</template>
<script setup lang="ts">
import type { ResultListWidget } from "../../sdk";
import RankedChoosable from "./RankedChoosable.vue";
import { useSessionStore } from "../../states/session";

interface WidgetProps {
  widget: ResultListWidget;
}

const props = defineProps<WidgetProps>();
const store = useSessionStore();
</script>
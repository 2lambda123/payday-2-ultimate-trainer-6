<script>
import { useSettingsStore } from "@/stores/settings";

import NavBar from "@/components/NavBar.vue";
import GameRestartRequiredIcon from "@/components/icons/GameRestartRequiredIcon.vue";

export default {
    components: {
        NavBar,
        GameRestartRequiredIcon
    },
    created() {
        this.settingsStore = useSettingsStore();
    }
}
</script>

<template>
    <NavBar />

    <div style="max-width: 600px;" class="container my-5">
        <div class="card">
            <div class="card-header">{{ $t("main.game") }}</div>
            <div class="card-body p-4">
                <div class="form-check form-switch mb-3">
                    <input id="enable-pause-stats-publishing" v-model="settingsStore.enablePauseStatsPublishing" class="form-check-input" type="checkbox" @change="setPauseStatsPublishing">
                    <label for="enable-pause-stats-publishing" class="form-check-label">{{ $t("main.pause_stats_publishing_to_steam_epic") }}
                        <GameRestartRequiredIcon class="ms-3" />
                    </label>
                </div>
                <div class="form-check form-switch">
                    <input id="enable-hide-mod-list" v-model="settingsStore.enableHideModList" class="form-check-input" type="checkbox" @change="setHideModList">
                    <label for="enable-hide-mod-list" class="form-check-label">{{ $t("main.hide_my_mod_list") }}
                        <GameRestartRequiredIcon class="ms-3" />
                    </label>
                </div>
            </div>
        </div>
    </div>
</template>

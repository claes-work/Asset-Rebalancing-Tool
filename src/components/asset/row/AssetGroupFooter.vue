<template>
  <div class="asset-group-footer" @click="assetStore.toggleWholeGroupSelectedFlag(thisGroup)">
    <p>{{thisGroup.name}}</p>
    <ActualValueColumn
        :value="totalValue"
        :percentage="totalPercentage"
    />
    <SingleValue class="total-target-percentage"
                 :valueArray="totalTargetPercentage"
                 :unit="'%'"
    />
    <SingleValue
        :valueArray="totalDeviation"
        :unit="'%'"
    />
  </div>
</template>

<script>
import SingleValue        from '@/components/asset/row/column/SingleValue'
import ActualValueColumn  from '@/components/asset/row/column/ActualValueColumn'
import {useAssetStore} from '@/stores/AssetStore';

export default {
  name: 'AssetGroupFooter',
  components: {
    SingleValue,
    ActualValueColumn
  },
  props: {
    thisGroup: {
      type: Object,
      required: true
    }
  },
  computed: {

    // The total value of this group
    totalValue() {
      return this.thisGroup.totalValue
    },

    // The total percentage of this group
    totalPercentage() {
      return this.thisGroup.totalPercentage
    },

    // The total target percentage of this group
    totalTargetPercentage() {
      return this.assetStore.getValueArray(this.thisGroup.totalTargetPercentage)
    },

    // The total deviation of this group
    totalDeviation() {
      return this.assetStore.getValueArray(this.thisGroup.totalDeviation)
    }
  },
  setup() {
    const assetStore = useAssetStore()
    return {
      assetStore
    }
  }
}
</script>

<style scoped>
.asset-group-footer {
  width: 100%;
  height: 45px;
  background-color: var(--tertiary-background-color);
  border-radius: 0 0 var(--primary-border-radius) var(--primary-border-radius);
  display: flex;
  align-items: center;
  column-gap: 50px;
  padding-left: 10px;
  padding-right: 11px;
  cursor: pointer;
}

.asset-group-footer p {
  flex: 1;
  color: var(--primary-text-color);
}

.asset-group-footer span {
}

/* Because the footer has a smaller height than the assets */
.asset-group-footer .single-value-wrapper {
  margin-top: -8px;
}

.asset-group-footer .actual-value-wrapper {
  margin-right: 12px;
}

.group-value {
  color: var(--primary-text-color);
}

.total-target-percentage {
  margin-right: 42px;
  margin-left: 10px;
}
</style>
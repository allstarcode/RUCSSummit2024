<script lang="ts">
  import { allData } from '../data/ScheduleData';
  import type { Schedule } from '../index';
  import ScheduleBlock from './ScheduleBlock.svelte';

  const data: Schedule = allData;
</script>

{#each data as day}
  {#each day.activities as activity}
    <ScheduleBlock
      name={activity.name}
      time={activity.time}
      duration={activity.duration}
      actType={activity.actType}
      links={activity.links}
      daynum={day.daynum}
    />
  {/each}
{/each}
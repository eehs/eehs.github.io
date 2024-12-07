---
layout: post
title: "Resizing LVM Partitions"
permalink: resizing-lvm-partitions
tags: Linux, Storage
---

## Purpose
This short guide is meant for those of us who, more often that not find themselves struggling to remember the order to resizing LVM partitions, *myself* included. 😀
<br><br>

## Configuration in four steps
Given you already have a working configuration of LVM up and running on Linux, with the appropriate *physical volumes (PV)* and *logical volumes (LV)* inside a *volume group (VG)*. There is an order to how we go about resizing them, which can be summed up in four steps.

> Note to self: Backup current state before proceeding and verify the results of each step.

1. Resize the disk partition on your machine to include/discard the unpartitioned/partitioned space you want.

2. Resize your LVM *physical volume* with `pvresize <disk partition path>`.

3. Resize your LVM *logical volume* with `lvresize <logical volume path> -l <size>`.

4. Grow your LVM *logical volume* on the file system level with `resize2fs`.

<br><br>
If hell hasn't broken loose in some shape or form, you should have successfully resized your LVM partitions.

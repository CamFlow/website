---
title: "Attributes"
date: 2018-01-28T21:55:52+01:00
anchor: "attributes"
weight: 20
---

**cf:machine_id** machine unique identifier. (uint32)

**cf:boot_id** boot identifier, unique per machine. (uint32)

**cf:id** vertex/edge identifier, unique per boot+machine. (uint64)

**cf:date** date captured when vertex/edge is recorded in userspace. (string)

**cf:jiffies** [jiffies](http://www.makelinux.net/ldd3/chp-7-sect-1) captured when vertex/edge is recorded in kernel (uint64)

## Edge attributes

**cf:offset** offset on file object (int64)

## Vertex attributes

**cf:version** object version (version correspond to a state of an object). (uint32)

**cf:uid** [user ID](https://en.wikipedia.org/wiki/User_identifier). (uint32)

**cf:gid** [group ID](https://en.wikipedia.org/wiki/Group_identifier). (uint32)

**cf:pid** [process identifier](https://en.wikipedia.org/wiki/Process_identifier). (uint32)

**cf:vpid** [virtual process identifier](https://lwn.net/Articles/259217/). (uint32)

**cf:XXXns** ino corresponding to a given [namespace](http://man7.org/linux/man-pages/man7/namespaces.7.html). (uint32)

**cf:secctx** security context as defined by the major [linux security module](https://www.kernel.org/doc/Documentation/security/LSM.txt) (e.g. [SELinux](https://fedoraproject.org/wiki/Security_context), [AppArmor](http://wiki.apparmor.net/index.php/AppArmorInterfaces#Security_contexts) depending on your distribution). (string)

**cf:mode** inode mode. (uint32)

**cf:ino** inode number. (uint32)

**cf:uuid** [superblock](http://www.linfo.org/superblock) uuid. (uuid)

**cf:length** size of path/value/name/content attribute when present. (uint32)

**cf:valid** iattribute valid value. (uint32)

**cf:atime** access time. (int64)

**cf:ctime** change time. (int64)

**cf:mtime** modification time. (int64)

**cf:truncated** if the value/name/content have been truncated. (boolean)

**cf:content** IP packet content value. (binary)

**cf:seq** IP sequence number. (uint32)

**cf:sender** packet sender IP address. (string)

**cf:receiver** packet receiver IP address. (string)

**cf:address** IP address. (JSON struct)

**cf:pathname** pathname. (string)

**cf:value** environment/argument variable value. (string)

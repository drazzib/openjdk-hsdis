openjdk-hsdis
=============

OpenJDK disassembler plugin for HotSpot JVM (based on binutils)

History
-------
Recent versions of HotSpot (including current builds of JDK7 and JDK6)
can load a plug-in disassembler for diagnosing code quality.

This plugin comes from actual OpenJDK source repository (and is based on binutils
tools for disassembler).

Why this repository ?
---------------------
This is just a "repackaging" of original hsdis based on source code from
http://hg.openjdk.java.net/jdk7u/jdk7u/hotspot/file/tip/src/share/tools/hsdis/

Build Debian package
--------------------
+ Download this version of hsdis:
```
git clone git://github.com/drazzib/openjdk-hsdis.git
cd openjdk-hsdis
```

+ Install build-dependencies
```
sudo apt-get install build-essential devscripts
sudo mk-build-deps -i -r
```

+ Build package
```
debuild --no-lintian -b -uc -us
```

+ Install package
```
sudo debi --with-depends
sudo apt-get --purge remove openjdk-hsdis-build-deps
```

Enjoy your disassembler
-----------------------
```
JDK7=/usr/lib/jvm/java-7-openjdk-amd64
XJAVA="$JDK7/bin/java -XX:+UnlockDiagnosticVMOptions -XX:+PrintAssembly"
$XJAVA -Xcomp -cp ~/Classes hello
$XJAVA -Xcomp -cp ~/Classes -XX:PrintAssemblyOptions=hsdis-print-bytes hello
$XJAVA -XX:-PrintAssembly -XX:+PrintStubCode
$XJAVA -XX:-PrintAssembly -XX:+PrintInterpreter
$XJAVA -XX:-PrintAssembly -XX:+PrintSignatureHandlers
```

License
-------
```
Copyright (c) 2008, Oracle and/or its affiliates. All rights reserved.

This code is free software; you can redistribute it and/or modify it
under the terms of the GNU General Public License version 2 only, as
published by the Free Software Foundation.
  
This code is distributed in the hope that it will be useful, but WITHOUT
ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License
version 2 for more details (a copy is included in the LICENSE file that
accompanied this code).
 
You should have received a copy of the GNU General Public License version
2 along with this work; if not, write to the Free Software Foundation,
Inc., 51 Franklin St, Fifth Floor, Boston, MA 02110-1301 USA.
  
Please contact Oracle, 500 Oracle Parkway, Redwood Shores, CA 94065 USA
or visit www.oracle.com if you need additional information or have any
questions.
```
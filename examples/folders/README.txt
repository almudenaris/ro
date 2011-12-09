ro:Folder example RO
====================

Example of a Research Object using ro:Folder and ro:FolderEntry 
to structure aggregated resources into folders.

See the .ro/ folder for the RDF/Turtle resource maps describing each of
thse folders, in additoin to the ro:Manifest for the research object
itself.  The filename structure and identifier scheme here
is non-normative and is a suggestion only.


The RO model does not (yet) assign a name to the top-level ro:Folder,
which in this example has been called <.ro/root> - although its children
are in this example organised directly within the folder structure of
the Research Object. 

The Research Object aggregates all individual resources that are
organised into the folders, no matter at what folder level they have
ro:FolderEntry instances. The ro:Folder instances themselves, as
instances of ro:Resource - are also aggregated by the
research object.

Each ore:ResourceMap (each .ttl file in this example) contains relevant
links to other resource maps, as if it was a REST resource. As a
minimum a resource map for a ro:Folder should contain a link to the
aggregating research object's ro:Manifest, and for each ro:FolderEntry
to a resource which is another ro:Folder, a link to its ore:ResourceMap.


In this example, the ro:Folder entries mainly correspond to the actual
resource paths, for instance <b/file3.txt> has the folder entry with an
ro:entryName "file3", and is a proxy of the ro:Folder <b> which has the
ro:entryName "b" within the root folder <.ro/root> (which is not
contained by any FolderEntry).

There is no requirements for the entry names to match parts of the URI
of the aggregated resource, this is examplified in this example where
the aggregated resource  <http://www.example.com/external.txt> has
folder entries both as "a/other.txt" and "b/external.txt" in this
imagined "check out" of a complete researc object.

Secondly, aggregated resources, even if they are ro:Resource instances,
are not required to be present within an ro:Folder structure. In this
RO, this is examplified by the aggregation of another research object
<http://www.example.org/another-ro/> which does not appear as an
FolderEntry.




Content:

.                   ro:ResourceObject aggregating all except <.ro/*>
./.ro               Research Object metadata
./.ro/manifest.ttl  ro:Manifest / ore:ResourceMap describing <.>
./.ro/root.ttl      ore:ResourceMap describing <.ro/root>
./.ro/root          Top-level ro:Folder <.ro/root>
./.ro/root/a.ttl    ore:ResourceMap describing the ro:Folder <a/>
./.ro/root/b        *)
./.ro/root/b.ttl    ore:ResourceMap describing <b/>
./.ro/root/b/c.ttl  ore:ResourceMap describing <b/c/> 
./file1.txt         ro:Resource <file1.txt>
./a                 ro:Folder <a/>
./a/other.txt       ro:Resource <http://www.example.com/external.txt>
./a/file2.txt       ro:Resource <a/file2.txt>
./b                 ro:Folder <b/>
./b/external.txt    ro:Resource <http://www.example.com/external.txt>
./b/file3.txt       ro:Resource <b/file3.txt>
./b/c               ro:Folder <b/c/>
./b/c/file4.txt     ro:Resource <b/c/file4.txt>

*) The metadata folder <.ro/root/b/> does not represent anything in the
   research object, and is in this example used to organize the
   ore:ResourceMap.  If the ore:ResourceMap documents describing the
   ro:Folder are delivered through Content Negotiation directly on the
   ro:Folder resource, like <b/c/>, there is no need for this folder
   structure. 


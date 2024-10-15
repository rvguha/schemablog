---
layout: post
title: "Introducing 'Role'"
date: 2014-06-16
---

<div dir="ltr" style="text-align: left;">
<span style="font-family: Calibri; font-size: 11pt;">To date, schema.org
has supported relatively simple relations between entities.  For example, if we wanted to describe Joe
Montana as an athlete on the San Francisco 49ers team, we might represent this
using the newly proposed "athlete" property of a SportsTeam. </span><br />
<span style="font-family: inherit;"><br /></span>
<span id="docs-internal-guid-e9c1bb3e-90df-9821-95d3-6257338dbd46"><span style="font-size: 15px; vertical-align: baseline; white-space: pre-wrap;"><span style="font-family: inherit;"></span></span></span><br />
<div class="separator" style="clear: both; text-align: center;">
<br /></div>
<div class="separator" style="clear: both; text-align: center;">
<a href="http://1.bp.blogspot.com/-h-nBek0AUlk/U58Xo-yuc_I/AAAAAAAAI5M/ORErxieZ7Fg/s1600/sdo-sports-image0.png" style="margin-left: 1em; margin-right: 1em;"><img alt="" border="0" src="http://1.bp.blogspot.com/-h-nBek0AUlk/U58Xo-yuc_I/AAAAAAAAI5M/ORErxieZ7Fg/s1600/sdo-sports-image0.png" title="San Fran 49ers linked by a 'member' arrow to Joe Montana." /></a></div>
<br />
<div style="font-family: Calibri; font-size: 11.0pt; margin: 0in;">
This is a pretty
clear structure, but it doesn't offer anywhere to attach further information
about the relationship.  Building on our example,
let's say we wanted to also indicate that Joe Montana only played for the San
Francisco 49ers from 1979 to 1992 and that his position was "Quarterback".</div>
<div style="font-family: Calibri; font-size: 11.0pt; margin: 0in;">
<br /></div>
<div style="font-family: Calibri; font-size: 11.0pt; margin: 0in;">
To accomplish this,
we introduce a new type called <a href="http://schema.org/Role">Role</a>.  The
new Role type serves to elaborate or qualify these more simple relationships.
We have been motivated by concrete problems around organizational affiliations
such as those occurring in music and sports. In both cases it is important to
specify time periods in a sporting or musical career.</div>
<div style="font-family: Calibri; font-size: 11.0pt; margin: 0in;">
<br /></div>
<div style="font-family: Calibri; font-size: 11.0pt; margin: 0in;">
To specify the role
being played, the Role entity reuses the initial property from, and then extends the semantics of the relationship by way of additional properties
like "<a href="http://schema.org/startDate">startDate</a>".</div>
<br />
<div style="font-family: Calibri; font-size: 11.0pt; margin: 0in;">
<br /></div>
<div dir="ltr" style="line-height: 1.15; margin-bottom: 0pt; margin-top: 0pt;">
<span style="background-color: transparent; color: black; font-size: 15px; font-style: normal; font-variant: normal; font-weight: normal; text-decoration: none; vertical-align: baseline; white-space: pre-wrap;"><span id="docs-internal-guid-e9c1bb3e-a577-1d27-5da3-def9efa5742f"><span style="font-family: Arial; vertical-align: baseline;"></span></span></span></div>
<div class="separator" style="clear: both; text-align: center;">
<br /></div>
<div class="separator" style="clear: both; text-align: center;">
<a href="http://4.bp.blogspot.com/-jf3x5HkGVF8/U58cxdWKZoI/AAAAAAAAI5g/bIha2aZn3Ek/s1600/sdo-athlete-role.png" style="margin-left: 1em; margin-right: 1em;"><img alt="" border="0" src="http://4.bp.blogspot.com/-jf3x5HkGVF8/U58cxdWKZoI/AAAAAAAAI5g/bIha2aZn3Ek/s1600/sdo-athlete-role.png" title="San Fran 49ers having an 'athlete' link to a Role, which in turn has another 'athlete' link to Joe Montana, as well as a startDate of 1979." /></a></div>
<div class="separator" style="clear: both; text-align: center;">
<br /></div>
<div class="separator" style="clear: both; text-align: center;">
<span id="docs-internal-guid-e9c1bb3e-a586-f8c9-8247-cd6a755f7ce5"><span style="font-family: Arial; font-size: 15px; vertical-align: baseline; white-space: pre-wrap;"></span></span></div>
<div class="separator" style="clear: both; text-align: center;">
<br /></div>
<div dir="ltr" style="line-height: 1.15; margin-bottom: 0pt; margin-top: 0pt;">
<div class="separator" style="clear: both; text-align: center;">
<br /></div>
<div style="font-family: Calibri; font-size: 11.0pt; margin: 0in;">
In essence, we are
replacing the "athlete" property's original value (a <a href="http://schema.org/Person">Person</a> node) with an intermediary node (Role). The
original node is moved one hop away and becomes the value of the re-used "athlete" property. After considering several designs, we chose this
approach as the simplest.</div>
<div style="font-family: Calibri; font-size: 11.0pt; margin: 0in;">
<br /></div>
<div style="font-family: Calibri; font-size: 11.0pt; margin: 0in;">
The Role schema
allows algorithms to collapse down to the simple graph from a more complicated
Role-based description. In the example above, we can assume Joe Montana is a
valid value for the "athlete" property on the 49ers SportsTeam. More
formally, if some Role R has incoming property P from entity A, and A also has
an outgoing occurrence of property P to entity B, we can assume it is
reasonable to describe A as having a 'P' property whose value is B. </div>
<div style="font-family: Calibri; font-size: 11.0pt; margin: 0in;">
<br /></div>
<div style="font-family: Calibri; font-size: 11.0pt; margin: 0in;">
These details are
more important to consumers of schema.org than publishers, as they allow for
backwards compatibility, while also permitting any schema.org property to be
used with roles. </div>
<div style="font-family: Calibri; font-size: 11.0pt; margin: 0in;">
<br /></div>
<div style="font-family: Calibri; font-size: 11.0pt; margin: 0in;">
The Role type (much
like URL) can be used with any schema.org types. We will not clutter the site
with statements emphasizing this, except in cases (e.g. around sports and
music) where the Role mechanism is particularly useful. We have added examples
of Role usage in Microdata, RDFa and JSON-LD notation to the <a href="http://schema.org/Role">site</a>, and look forward to seeing more
detailed schema.org descriptions using this mechanism.</div>
<br /></div>
<div style="font-family: Calibri; font-size: 11.0pt; margin: 0in;">
As we continue to
evolve the site we expect to add more properties and sub-types that have been
designed to work with the Role type. For now, we introduce two kinds of Role:
<a href="http://schema.org/OrganizationRole" target="_blank">OrganizationRole</a> and <a href="http://schema.org/PerformanceRole" target="_blank">PerformanceRole</a>. In the sporting example shown above, the
Role node (the red circle) would be an <a href="http://schema.org/OrganizationRole" target="_blank">OrganizationRole</a> and in addition to
defining the "startDate" and "endDate" for that role, we
might also define indicate Joe Montana was a quarterback by using the
"<a href="http://schema.org/namedPosition" target="_blank">namesPosition</a>" property. Similarly, the <a href="http://schema.org/PerformanceRole" target="_blank">PerformanceRole</a> type
provides a <a href="http://schema.org/characterName" target="_blank">characterName</a> property that might be used to describe Bill Murray's
role in Ghostbusters. The Role pattern works here too. See the <a href="http://schema.org/Role">schema.org site</a> for full RDFa, Microdata and JSON-LD markup, including the Ghostbusters example shown here:</div>
<span style="font-family: inherit; font-size: 15px; white-space: pre-wrap;"><br /></span><br />
<span style="font-family: Arial; font-size: 15px; vertical-align: baseline; white-space: pre-wrap;"><br /></span>
<div class="separator" style="clear: both; text-align: center;">
<a href="http://3.bp.blogspot.com/-9ZNmMYVIvkQ/U58dliwFPbI/AAAAAAAAI5s/KociBJuFDBo/s1600/sdo-ghostbusters-role.png" style="margin-left: 1em; margin-right: 1em;"><img alt="" border="0" src="http://3.bp.blogspot.com/-9ZNmMYVIvkQ/U58dliwFPbI/AAAAAAAAI5s/KociBJuFDBo/s1600/sdo-ghostbusters-role.png" title="Ghostbusters has an actor Role, which has an actor property with value Bill Murray. The Role also indicates a characterName: Dr. Peter Venkman." /></a></div>
<span style="font-family: Arial; font-size: 15px; vertical-align: baseline; white-space: pre-wrap;"><br /></span>
<span style="font-family: inherit; font-size: 15px; white-space: pre-wrap;"><br /></span>
<span id="docs-internal-guid-e9c1bb3e-91bd-b02f-0cd8-f0e48e85f868"><span style="font-family: Arial; font-size: 15px; vertical-align: baseline; white-space: pre-wrap;"></span></span><br />
<span style="font-size: 15px; vertical-align: baseline; white-space: pre-wrap;"><span style="font-family: inherit;"><br /></span></span>
<span style="font-size: 15px; vertical-align: baseline; white-space: pre-wrap;"><span style="font-family: inherit;">---</span></span><br />
<span style="font-size: 15px; white-space: pre-wrap;"><span style="font-family: inherit;">Vicki Tardif Holland (Google)</span></span><br />
<span style="font-size: 15px; white-space: pre-wrap;"><span style="font-family: inherit;">Jason Johnson (Microsoft)</span></span></div>
## 1 Overview

It’s important to understand that different types of authenticators
unlock different use cases and user experiences. The webauthn/FIDO APIs
support these different use cases, but relying parties must take care to
utilize the APIs correctly, e.g., by requesting the appropriate
transport or attachment type for the particular use case they are
addressing. If not done correctly, you risk confusing your users, making
authentication more complicated than necessary for them, or locking them
out of their account. Below is an overview of the use cases unlocked by
the different types of authenticators:


<table>
<thead>
<tr class="header">
<th></th>
<th></th>
<th colspan="2">Physical manifestation of the authenticator</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td>Platform</td>
<td>Roaming</td>
</tr>
<tr class="even">
<td rowspan="2">Capabilities of authenticator</td>
<td>User-verifying</td>
<td><ul>
<li>
<p>convenient <em><strong>reauthentication</strong></em> UX</p>
</li>
</ul></td>
<td><ul>
<li>
<p>phishing-resistant 2nd factor</p>
</li>
<li>

phishing-resistant <em><strong>single-step account bootstrapping</strong></em> <a href=#footnote-3>[3]</a>
</li>
</ul></td>
</tr>
<tr class="odd">
<td>Not-user-verifying</td>
<td><ul>
<li>defense-in-depth against malware <a href=#footnote-4>[4]</a></li>
</ul></td>
<td><ul>
<li>
<p>phishing-resistant 2nd factor</p>
</li>
<li>
<p>low-security single-step account bootstrapping <a href=#footnote-5>[5]</a></p>
</li>
</ul></td>
</tr>
</tbody>
</table>

Below we will get into more detail of how relying parties should
implement support for these different use cases, but we will approach
this from a user-journey perspective: what should you (as the relying
party) do during the login step, during the reauthentication step, etc.


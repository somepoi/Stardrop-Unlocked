# Legal Notice

This repository is a modified fork of [Floogen/Stardrop](https://github.com/Floogen/Stardrop), distributed under the **GNU General Public License v3.0** (GPLv3).

The modification removes client-side UI checks (`IsPremium`) and adds a browser-based fallback that lets free-tier Nexus Mods users download mods through Stardrop using the existing [NXM link flow](https://github.com/Nexus-Mods/node-nexus-api/blob/master/docs/classes/_nexus_.nexus.md).

---

## License Compliance

This fork exercises rights explicitly granted by GPLv3:

- **§2 (Basic Permissions)** — unrestricted right to run and modify covered works.
- **§5 (Conveying Modified Source Versions)** — right to distribute modified code, subject to marking changes, preserving the license, and providing source.
- **§3 (Protecting Users' Legal Rights)** — "No covered work shall be deemed part of an effective technological measure under any applicable law fulfilling obligations under article 11 of the WIPO copyright treaty." The licensor waives anti-circumvention claims under DMCA §1201 and EU InfoSoc Directive Art. 6 for all covered works.

All distribution obligations under GPLv3 §5 are satisfied: modifications are marked, the license is preserved, and full source is publicly available.

## No Technological Protection Measure Is Present

The removed code is an `if (IsPremium == false)` conditional in open, GPL-licensed source. It is not encryption, authentication, access control, or any form of DRM. It does not meet the definition of an "effective technological measure" under 17 U.S.C. §1201(a)(3)(B), which requires a measure that "in the ordinary course of its operation, requires the application of information, or a process or a treatment, with the authority of the copyright owner, to gain access to the work."

A UI conditional in client-side open source code does not control access to any copyrighted work. Mods hosted on Nexus Mods are freely available to all registered users regardless of subscription tier. See also: [EFF's analysis of the youtube-dl reinstatement](https://www.eff.org/deeplinks/2020/11/github-reinstates-youtube-dl-after-riaas-abuse-dmca); [GitHub's policy clarification on anti-circumvention claims](https://github.blog/news-insights/policy-news-and-insights/standing-up-for-developers-youtube-dl-is-back/).

## No Unauthorized Access

This fork does not bypass, circumvent, or interfere with Nexus Mods servers, authentication, or API rate limiting. Free users authenticate with their own valid API key and download through the documented API flow (`key` + `expires` parameters from NXM links). No premium credentials are forged, spoofed, or reused.

Under *Van Buren v. United States*, 593 U.S. 374 (2021), the Computer Fraud and Abuse Act covers only access to information a person is not entitled to obtain at all — not the manner in which authorized access is used. Free Nexus Mods users are authorized to download mods; this fork changes only which UI presents that capability.

## Nexus Mods API Usage

The download flow for free users is unchanged from what Nexus documents: the user clicks "Slow Download" on the Nexus website, which generates an NXM link containing `key` and `expires` parameters. Stardrop passes these to the `/v1/games/{game}/mods/{mod_id}/files/{file_id}/download_link.json` endpoint, which is the documented API behavior for non-premium users. No scraping, automation beyond normal client usage, or rate-limit evasion is involved.

## References

- [GNU GPLv3 — Full Text](https://www.gnu.org/licenses/gpl-3.0.en.html) (§2, §3, §5)
- [17 U.S.C. §1201](https://www.law.cornell.edu/uscode/text/17/1201)
- [*Van Buren v. United States*, 593 U.S. 374 (2021)](https://supreme.justia.com/cases/federal/us/593/374/)
- [EFF: GitHub Reinstates youtube-dl](https://www.eff.org/deeplinks/2020/11/github-reinstates-youtube-dl-after-riaas-abuse-dmca)
- [GitHub: Standing Up for Developers](https://github.blog/news-insights/policy-news-and-insights/standing-up-for-developers-youtube-dl-is-back/)
- [Nexus Mods API Documentation](https://github.com/Nexus-Mods/node-nexus-api/blob/master/docs/classes/_nexus_.nexus.md)
- [Nexus Mods Terms of Service](https://help.nexusmods.com/article/18-terms-of-service)

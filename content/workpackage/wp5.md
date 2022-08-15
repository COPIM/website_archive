---
title: "WP5: Thoth"
weight: 50
date: "2020-01-01"
lastmod: "2022-02-03"
image: "images/thoth-banner.png"
image_alt_text: "logo for Thoth"
external_url: "https://thoth.pub"

---

WP5 is developing technical protocols and infrastructure to better integrate open access books into institutional library, digital learning and repository systems. This will support wider discovery and dissemination of open access books. Existing print and ebook distribution channels are difficult for new or open access publishers to engage with, requiring submission of metadata in multiple different formats (e.g. MARC, ONIX, KBART), and many platforms requiring multiple different metadata submissions; In addition, existing distribution channels are not well suited to open access content, while entirely new discovery and dissemination platforms are emerging (e.g. Google Books/Scholar). Guided by the perspective of new and emerging not-for-profit open access presses that have not yet been sufficiently integrated into existing discovery systems, knowledge bases, and supply routes, the aim of WP5 is to develop methods and systems to better integrate the catalogues of open access publishers into curated research records. The implementation of “best practices” workflows for open access book publishers will allow their catalogues to be better integrated into the scholarly record (discoverability, reach, persistence), increasing the impact of open access books. WP5 will build an Open Dissemination System (ODS) for open access books and a shared “best practices” digital catalogue. The ODS is to be built as a decentralised system, using open source code, open protocols and standards and distributed databases—all under collective control. Doing so will ensure the system cannot be operated for the benefit of a single entity (either commercial or not).

## Frequently Asked Questions

<details>
  <summary>
    What is Thoth?
  </summary>

[Thoth](https://thoth.pub) is a metadata creation, management, and dissemination platform specifically tailored to tackle the problems of getting open access works into the book supply chain. The platform provides publishers with a tool to gather all of the metadata needed to dissemination books, such as information on titles, authors, publication dates, and the like, as well as metadata specific to digital and open access books, such as persistent identifiers for products, file addresses, and contributors and their institutional affiliations. The data model is granular enough that publishers can add metadata on chapters within books, or include information on multiple reader-facing outlets where a book can be found. Thoth enables the wide dissemination of these records by transforming them into a variety of both industry-standard and distributor-specific metadata formats, and exposing all records openly under a CC-0 license via open APIs.

</details>

<details>
  <summary>
    Why is Thoth needed?
  </summary>

The initial idea for [Thoth](https://thoth.pub) emerged out of the shared experience of a number of scholar-led presses, who, after facing the significant challenges of starting up publishing programs, came to realize that their next major challenge was to get their books into the scholarly record and more widely discoverable. The established supply chain for scholarly books is difficult to access for new publishers and not designed to handle open access books. Most small or new publishers lack access to the specialized title management systems used by bigger publishers, and even those expensive systems are not oriented to open access books. Bigger publishers are also better able to navigate the supply chain because they have dedicated staff, such as metadata specialists and marketing managers, who focus entirely on distribution. Thoth hopes to level the playing field between large and small publishers by alleviating some of the difficulties faced by scholar-led presses.

[Thoth](https://thoth.pub) approaches these problems by:

* Making it easier for publishers to create and manage metadata for their titles. The platform’s data model and interface provide a scaffolding for good metadata practices.
* Encouraging publisher workflow practices that lead to more-complete and higher-quality metadata. Thoth enables publishers to iteratively create and enhance a title’s metadata as it moves through the publication process, and its Traffic Light system will display the status of a record as evaluated by the requirements of downstream distributors.
* Easing the substantial burden of submitting records to multiple distributors. Publishers need to create a metadata record only once, which can then be exported in the many forms and formats required by intermediaries.
* Reducing the amount of insider knowledge needed to strategically navigate the scholarly book supply chain. The Thoth team is putting in the legwork of making organizational and technical connections with distributors so that publishers don’t have to.

</details>

<details>
  <summary>
    Who will use Thoth?
  </summary>

While the primary focus of [Thoth](https://thoth.pub) is on the needs of newer, smaller scholar-led presses, including some of the new university presses, we are finding that the service might be attractive to other segments of the scholarly publishing sector, including library publishing programs, and mid-sized university presses that publish some, but not all, of their titles in open access editions.

</details>

<details>
  <summary>
    How is Thoth pronounced?
  </summary>

Thoth (/toʊt, θoʊθ/, Greek Θώθ < Coptic Ⲑⲱⲟⲩⲧ < Egyptian ḏḥwtj)

Vincent is allegedly the only person in WP5 who knows how to properly pronounce “Thoth,” but we have not let our wild variety of pronunciations hinder our discussions. The group seems to be converging toward “towt,” as in “tote bag.” (For audio of the British and American English pronunciation of “tote,” see the Cambridge Dictionary: https://dictionary.cambridge.org/us/pronunciation/english/tote)

</details>

<details>
  <summary>
    What is Thoth's relationship with openness?
  </summary>

Several different types of openness are central to Thoth’s approach to building a platform that reflects and forwards the values of open infrastructure. The openness of Thoth’s source code, metadata records, and focus on open access books, orient the project not only toward the flourishing of scholar-led publishers but to the growth of a healthier scholarly communication ecology, more directly managed by the scholarly community and guarded against platform lock-in.

Thoth embeds openness in its design in three ways:

* Its overarching aim is to support the success of scholar-led open-access presses, and the wide circulation of the books they publish.

* It seeks to enlarge the amount of open bibliographic metadata circulating by releasing records under CC-0 licenses, making them accessible, reusable, and open for enhancement and sharing.

* The code behind the Thoth platform is open source, available for anyone to use, reproduce, and distribute under an Apache 2.0 license, available on Github: https://github.com/thoth-pub/thoth. While the service-model we are developing provides publishers with an account on the main Thoth instance, for a fee, anyone can download the code, host, configure, and further develop their own instance of Thoth.

</details>

<details>
  <summary>
    How does Thoth fit into the broader COPIM project?
  </summary>

Because Thoth stores metadata records as structured data, it is becoming an integral part of other COPIM work packages, enabling them to pull the data into their own systems. [Work Package 2](https://www.copim.ac.uk/workpackage/wp2/)’s Open Book Collective’s website will populate its catalogue by pulling through the Thoth API; [Work Package 7](https://www.copim.ac.uk/workpackage/wp7/) will distribute all data needed for book preservation through Thoth; and [Work Package 6](https://www.copim.ac.uk/workpackage/wp6/)’s Experimental Publishing Compendium is looking at pulling records for books published by participating presses.

Member presses are also looking at ways of reusing the records in Thoth. Open Book Publishers’ [new website](https://www.openbookpublishers.com/) pulls title data from Thoth instead of entering all of this data first in its content management system, and then in Thoth. The website code will ultimately be available open-source, making it easy for smaller publishers to set up and customise their own easy-to-maintain sites.

</details>

<details>
  <summary>
    People
  </summary>

* Rupert Gatti
* Vincent van Gerven Oei
* Javier Arias
* Ross Higman
* Livy Snyder
* Graham Stone
* Niels Stern & Ronald Snijder

</details>

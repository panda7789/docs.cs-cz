---
title: Mapování modelu objektu syndikace WCF na Atom a RSS
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0365eb37-98cc-4b13-80fb-f1e78847a748
ms.openlocfilehash: 67fbbb035a3a6683cefbf24e299f32579b674bbd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597251"
---
# <a name="how-the-wcf-syndication-object-model-maps-to-atom-and-rss"></a>Mapování modelu objektu syndikace WCF na Atom a RSS
Při vývoji služby syndikace Windows Communication Foundation (WCF) vytvoříte kanály a položky pomocí následujících tříd:  
  
- <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
- <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
- <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
- <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
- <xref:System.ServiceModel.Syndication.TextSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.UrlSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.XmlSyndicationContent>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>Může být serializován do libovolného formátu syndikace, pro který je definován formátovací modul. WCF se dodává se dvěma formátovacími moduly: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> a <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> .  
  
 Objektový model kolem <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> je úzce zarovnán se specifikací Atom 1,0, než specifikace RSS 2,0. Důvodem je, že Atom 1,0 je důležitější specifikace, která definuje prvky, které jsou nejednoznačné nebo jsou vynechány specifikací RSS 2,0. Z tohoto důvodu mnoho položek v modelu objektu Syndikace WCF nemá přímo reprezentaci ve specifikaci RSS 2,0. Při serializaci <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> objektů do kanálu RSS 2,0 umožňuje WCF serializovat datové prvky specifické pro Atom jako prvky rozšíření kvalifikované na obor názvů, které odpovídají specifikaci Atom. Můžete to řídit pomocí parametru předaného <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> konstruktoru.  
  
 Ukázky kódu v tomto tématu používají jednu ze dvou metod, které jsou zde definovány k provedení samotné serializace.  
  
 `SerializeFeed`serializace informačního kanálu syndikace.  
  
 [!code-csharp[SyndicationMapping#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#10)]
 [!code-vb[SyndicationMapping#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#10)]  
  
 `SerializeItem`zaserializace syndikační položky.  
  
 [!code-csharp[SyndicationMapping#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#11)]
 [!code-vb[SyndicationMapping#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#11)]  
  
## <a name="syndicationfeed"></a>SyndicationFeed  
 Následující příklad kódu ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.SyndicationFeed> třídu na Atom 1,0 a RSS 2,0.  
  
 [!code-csharp[SyndicationMapping#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#0)]
 [!code-vb[SyndicationMapping#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#0)]  
  
 Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationFeed> je serializován do Atom 1,0.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<feed xml:lang="EN-US" xmlns="http://www.w3.org/2005/Atom">  
  <title type="text">My Feed Title</title>  
  <subtitle type="text">My Feed Description</subtitle>  
  <id>FeedID</id>  
  <rights type="text">Copyright 2007</rights>  
  <updated>2007-08-29T13:57:17-07:00</updated>  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <logo>http://server/image.jpg</logo>  
  <generator>Sample Code</generator>  
  <link rel="alternate" href="http://myfeeduri/" />  
  <entry>  
    <id>ItemID</id>  
    <title type="text">Item Title</title>  
    <summary type="text">Item Summary</summary>  
    <published>2007-08-29T00:00:00-07:00</published>  
    <updated>2007-08-29T13:57:17-07:00</updated>  
    <author>  
      <name>Jesper Aaberg</name>  
      <uri>http://Jesper/Aaberg</uri>  
      <email>Jesper@Aaberg.com</email>  
    </author>  
    <contributor>  
      <name>Lene Aaling</name>  
      <uri>http://Lene/Aaling</uri>  
      <email>Lene@Aaling.com</email>  
    </contributor>  
    <link rel="alternate" href="http://myitemuri/" />  
    <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
    <content type="text">Item Content</content>  
    <rights type="text">Copyright 2007</rights>  
    <source>  
      <title type="text">My Feed Title</title>  
      <subtitle type="text">My Feed Description</subtitle>  
      <id>FeedID</id>  
      <rights type="text">Copyright 2007</rights>  
      <updated>2007-08-29T13:57:17-07:00</updated>  
      <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
      <logo>http://server/image.jpg</logo>  
      <generator>Sample Code</generator>  
      <link rel="alternate" href="http://myfeeduri/" />  
    </source>  
  </entry>  
</feed>  
```  
  
 Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationFeed> je serializován do kanálu RSS 2,0.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<rss xmlns:a10="http://www.w3.org/2005/Atom" version="2.0">  
  <channel>  
    <title>My Feed Title</title>  
    <link>http://myfeeduri/</link>  
    <description>My Feed Description</description>  
    <language>EN-US</language>  
    <copyright>Copyright 2007</copyright>  
    <lastBuildDate>Wed, 29 Aug 2007 13:57:17 -0700</lastBuildDate>  
    <category domain="categoryScheme">categoryName</category>  
    <generator>Sample Code</generator>  
    <image>  
      <url>http://server/image.jpg</url>  
      <title>My Feed Title</title>  
      <link>http://myfeeduri/</link>  
    </image>  
    <a10:id>FeedID</a10:id>  
    <item>  
      <guid isPermaLink="false">ItemID</guid>  
      <link>http://myitemuri/</link>  
      <author>Jesper@Aaberg.com</author>  
      <category domain="categoryScheme">categoryName</category>  
      <title>Item Title</title>  
      <description>Item Summary</description>  
      <source>My Feed Title</source>  
      <pubDate>Wed, 29 Aug 2007 00:00:00 -0700</pubDate>  
      <a10:updated>2007-08-29T13:57:17-07:00</a10:updated>  
      <a10:rights type="text">Copyright 2007</a10:rights>  
      <a10:content type="text">Item Content</a10:content>  
      <a10:contributor>  
        <a10:name>Lene Aaling</a10:name>  
        <a10:uri>http://Lene/Aaling</a10:uri>  
        <a10:email>Lene@Aaling.com</a10:email>  
      </a10:contributor>  
    </item>  
  </channel>  
</rss>  
```  
  
## <a name="syndicationitem"></a>SyndicationItem  
 Následující příklad kódu ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.SyndicationItem> třídu na Atom 1,0 a RSS 2,0.  
  
 [!code-csharp[SyndicationMapping#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#1)]
 [!code-vb[SyndicationMapping#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#1)]  
  
 Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationItem> je serializován do Atom 1,0.  
  
```xml  
<entry xmlns="http://www.w3.org/2005/Atom">  
  <id>ItemID</id>  
  <title type="text">Item Title</title>  
  <summary type="text">Item Summary</summary>  
  <published>2007-08-29T00:00:00-07:00</published>  
  <updated>2007-08-29T14:07:09-07:00</updated>  
  <author>  
    <name>Jesper Aaberg</name>  
    <uri>http://Contoso/Aaberg</uri>  
    <email>Jesper.Aaberg@contoso.com</email>  
  </author>  
  <author>  
    <name>Syed Abbas</name>  
    <uri>http://Contoso/Abbas</uri>  
    <email>Syed.Abbas@contoso.com</email>  
  </author>  
  <contributor>  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
  <contributor>  
    <name>Kim Abercrombie</name>  
    <uri>http://Contoso/Abercrombie</uri>  
    <email>Kim.Abercrombie@contoso.com</email>  
  </contributor>  
  <link rel="alternate" href="http://myitemuri/" />  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <content type="text">Item Content</content>  
  <rights type="text">Copyright 2007</rights>  
  <source>  
    <title type="text">My Feed Title</title>  
    <subtitle type="text">My Feed Description</subtitle>  
    <link rel="alternate" href="http://myfeeduri/" />  
  </source>  
</entry>  
```  
  
 Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationItem> je serializován do kanálu RSS 2,0.  
  
```xml  
<item>  
  <guid isPermaLink="false">ItemID</guid>  
  <link>http://myitemuri/</link>  
  <author xmlns="http://www.w3.org/2005/Atom">  
    <name>Jesper Aaberg</name>  
    <uri>http://Jesper/Aaberg</uri>  
    <email>Jesper@Aaberg.com</email>  
  </author>  
  <author xmlns="http://www.w3.org/2005/Atom">  
    <name>Syed Abbas</name>  
    <uri>http://Contoso/Abbas</uri>  
    <email>Syed.Abbas@contoso.com</email>  
  </author>  
  <category domain="categoryScheme">categoryName</category>  
  <category domain="categoryScheme">categoryName</category>  
  <title>Item Title</title>  
  <description>Item Summary</description>  
  <source>My Feed Title</source>  
  <pubDate>Wed, 29 Aug 2007 00:00:00 -0700</pubDate>  
  <updated xmlns="http://www.w3.org/2005/Atom">2007-08-29T14:07:09-07:00</updated>  
  <rights type="text" xmlns="http://www.w3.org/2005/Atom">Copyright 2007</rights>  
  <content type="text" xmlns="http://www.w3.org/2005/Atom">Item Content</content>  
  <contributor xmlns="http://www.w3.org/2005/Atom">  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
  <contributor xmlns="http://www.w3.org/2005/Atom">  
    <name>Kim Abercrombie</name>  
    <uri>http://Contoso/Abercrombie</uri>  
    <email>Kim.Abercrombie@contoso.com</email>  
  </contributor>  
</item>  
```  
  
## <a name="syndicationperson"></a>SyndicationPerson  
 Následující příklad kódu ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.SyndicationPerson> třídu na Atom 1,0 a RSS 2,0.  
  
 [!code-csharp[SyndicationMapping#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#2)]
 [!code-vb[SyndicationMapping#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#2)]  
  
 Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationPerson> je serializován do Atom 1,0.  
  
```xml  
  <author>  
    <name>Jesper Aaberg</name>  
    <uri>http://Contoso/Aaberg</uri>  
    <email>Jesper.Aaberg@contoso.com</email>  
  </author>  
<contributor>  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
```  
  
 Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationPerson> je třída serializována do kanálu RSS 2,0, pokud pouze jeden <xref:System.ServiceModel.Syndication.SyndicationPerson> existuje v `Authors` kolekci nebo v `Contributors` uvedeném pořadí.  
  
```xml  
<author>Jesper.Aaberg@contoso.com</author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
```  
  
 Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationPerson> je třída serializována do kanálu RSS 2,0, pokud více než jeden <xref:System.ServiceModel.Syndication.SyndicationPerson> existuje v `Authors` kolekci nebo v `Contributors` uvedeném pořadí.  
  
```xml  
<a10:author>  
    <a10:name>Jesper Aaberg</a10:name>  
    <a10:uri>http://Contoso/Aaberg</a10:uri>  
    <a10:email>Jesper.Aaberg@contoso.com</a10:email>  
</a10:author>  
<a10:author>  
    <a10:name>Syed Abbas</a10:name>  
    <a10:uri>http://Contoso/Abbas</a10:uri>  
    <a10:email>Syed.Abbas@contoso.com</a10:email>  
</a10:author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
<a10:contributor>  
    <a10:name>Kim Abercrombie</a10:name>  
    <a10:uri>http://Contoso/Abercrombie</a10:uri>  
    <a10:email>Kim.Abercrombie@contoso.com</a10:email>  
</a10:contributor>  
```  
  
## <a name="syndicationlink"></a>SyndicationLink  
 Následující příklad kódu ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.SyndicationLink> třídu na Atom 1,0 a RSS 2,0.  
  
 [!code-csharp[SyndicationMapping#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#3)]
 [!code-vb[SyndicationMapping#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#3)]  
  
 Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationLink> je serializován do Atom 1,0.  
  
 `<link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
 Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationLink> je serializován do kanálu RSS 2,0.  
  
 `<a10:link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
## <a name="syndicationcategory"></a>SyndicationCategory  
 Následující příklad kódu ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.SyndicationCategory> třídu na Atom 1,0 a RSS 2,0.  
  
 [!code-csharp[SyndicationMapping#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#4)]
 [!code-vb[SyndicationMapping#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#4)]  
  
 Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationCategory> je serializován do Atom 1,0.  
  
 `<category term="categoryName" label="categoryLabel" scheme="categoryScheme" />`  
  
 Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationCategory> je serializován do kanálu RSS 2,0.  
  
 `<category domain="categoryScheme">categoryName</category>`  
  
## <a name="textsyndicationcontent"></a>TextSyndicationContent  
 Následující příklad kódu ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.TextSyndicationContent> třídu do Atom 1,0 a RSS 2,0, když <xref:System.ServiceModel.Syndication.TextSyndicationContent> je vytvořen s obsahem HTML.  
  
 [!code-csharp[SyndicationMapping#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#5)]
 [!code-vb[SyndicationMapping#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#5)]  
  
 Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> je třída s obsahem HTML serializována do Atom 1,0.  
  
 `<content type="html"><html> some html </html></content>`  
  
 Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> je třída s obsahem HTML serializována do kanálu RSS 2,0.  
  
 `<description><html> some html </html></description>`  
  
 Následující příklad kódu ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.TextSyndicationContent> třídu do Atom 1,0 a RSS 2,0, když <xref:System.ServiceModel.Syndication.TextSyndicationContent> je vytvořen obsah s prostým textem.  
  
 [!code-csharp[SyndicationMapping#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#6)]
 [!code-vb[SyndicationMapping#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#6)]  
  
 Následující kód XML ukazuje, jakým způsobem <xref:System.ServiceModel.Syndication.TextSyndicationContent> je třída s obsahem prostého textu serializována do Atom 1,0.  
  
 `<content type="text">Some Plain Text</content>`  
  
 Následující kód XML ukazuje, jakým způsobem <xref:System.ServiceModel.Syndication.TextSyndicationContent> je třída s obsahem prostého textu serializována do kanálu RSS 2,0.  
  
 `<description>Some Plain Text</description>`  
  
 Následující příklad kódu ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.TextSyndicationContent> třídu do Atom 1,0 a RSS 2,0 při <xref:System.ServiceModel.Syndication.TextSyndicationContent> vytvoření pomocí obsahu XHTML.  
  
 [!code-csharp[SyndicationMapping#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#7)]
 [!code-vb[SyndicationMapping#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#7)]  
  
 Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> Třída s obsahem XHTML je serializována do Atom 1,0.  
  
 `<content type="xhtml">`  
  
 `<html> some xhtml </html>`  
  
 `</content>`  
  
 Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> je třída s obsahem XHTML serializována do kanálu RSS 2,0.  
  
 `<description><html> some xhtml </html></description>`  
  
## <a name="urlsyndicationcontent"></a>UrlSyndicationContent  
 Následující příklad kódu ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.UrlSyndicationContent> třídu na Atom 1,0 a RSS 2,0.  
  
 [!code-csharp[SyndicationMapping#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#8)]
 [!code-vb[SyndicationMapping#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#8)]  
  
 Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.UrlSyndicationContent> je třída serializována do Atom 1,0.  
  
 `<content type="audio" src="http://someurl/" />`  
  
 Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.UrlSyndicationContent> je třída s obsahem XHTML serializována do kanálu RSS 2,0.  
  
 `<description />`  
  
 `<content type="audio" src="http://Contoso/someurl/" xmlns="http://www.w3.org/2005/Atom" />`  
  
## <a name="xmlsyndicationcontent"></a>XmlSyndicationContent  
 Následující příklad kódu ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.XmlSyndicationContent> třídu na Atom 1,0 a RSS 2,0.  
  
 [!code-csharp[SyndicationMapping#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#9)]
 [!code-vb[SyndicationMapping#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#9)]  
  
 Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.XmlSyndicationContent> je třída serializována do Atom 1,0.  
  
 `<content type="mytype">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
 Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.XmlSyndicationContent> je třída s obsahem XHTML serializována do kanálu RSS 2,0.  
  
 `<content type="mytype" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
## <a name="see-also"></a>Viz také

- [Syndikace WCF – přehled](wcf-syndication-overview.md)
- [Architektura syndikace](architecture-of-syndication.md)
- [Postupy: Vytvoření základního kanálu RSS](how-to-create-a-basic-rss-feed.md)
- [Postupy: Vytvoření základního informačního kanálu Atom](how-to-create-a-basic-atom-feed.md)
- [Postupy: Zveřejnění informačního kanálu ve formátu Atom i RSS](how-to-expose-a-feed-as-both-atom-and-rss.md)

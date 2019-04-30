---
title: Mapování modelu objektu syndikace WCF na Atom a RSS
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0365eb37-98cc-4b13-80fb-f1e78847a748
ms.openlocfilehash: b5a7f68edc49a02bb99ca05765d4582b798e72ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855202"
---
# <a name="how-the-wcf-syndication-object-model-maps-to-atom-and-rss"></a>Mapování modelu objektu syndikace WCF na Atom a RSS
Při vývoji syndikace služby Windows Communication Foundation (WCF), můžete vytvořit kanály a položky pomocí následující třídy:  
  
- <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
- <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
- <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
- <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
- <xref:System.ServiceModel.Syndication.TextSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.UrlSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.XmlSyndicationContent>  
  
 A <xref:System.ServiceModel.Syndication.SyndicationFeed> lze serializovat do jakékoli souhrnný formát, pro který je definován formátovacím modulem. WCF se dodává se dvěma formátovací moduly: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> a <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>.  
  
 Objektový model kolem <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> zarovnán lépe než RSS 2.0 specifikace specifikaci Atom 1.0. Je to proto Atom 1.0 je mnohem vyšší specifikace, která určuje prvky, které jsou nejednoznačný nebo není uveden ze specifikace RSS 2.0. Z tohoto důvodu mnoho položek v modelu objektu syndikace WCF nemají žádnou přímou reprezentaci ve specifikaci RSS 2.0. Při serializaci <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> objektů do RSS 2.0 WCF umožňuje serializovat specifické pro formát Atom datové prvky jako rozšíření kvalifikovaný v oboru názvů elementy, které odpovídají specifikaci Atom. Můžete to ovládacím prvkem parametr předán <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> konstruktoru.  
  
 Ukázky kódu v tomto tématu využívají jednu ze dvou metod lze tam definovat provedete skutečné serializace.  
  
 `SerializeFeed` serializuje informačního kanálu syndikace.  
  
 [!code-csharp[SyndicationMapping#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#10)]
 [!code-vb[SyndicationMapping#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#10)]  
  
 `SerializeItem` serializuje položky syndikace.  
  
 [!code-csharp[SyndicationMapping#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#11)]
 [!code-vb[SyndicationMapping#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#11)]  
  
## <a name="syndicationfeed"></a>SyndicationFeed  
 Následující příklad kódu ukazuje, jak k serializaci <xref:System.ServiceModel.Syndication.SyndicationFeed> třídy Atom 1.0 a RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#0)]
 [!code-vb[SyndicationMapping#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#0)]  
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationFeed> serializován Atom 1.0.  
  
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
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationFeed> serializovat do RSS 2.0.  
  
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
 Následující příklad kódu ukazuje, jak k serializaci <xref:System.ServiceModel.Syndication.SyndicationItem> třídy Atom 1.0 a RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#1)]
 [!code-vb[SyndicationMapping#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#1)]  
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationItem> serializován Atom 1.0.  
  
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
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationItem> serializovat do RSS 2.0.  
  
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
 Následující příklad kódu ukazuje, jak k serializaci <xref:System.ServiceModel.Syndication.SyndicationPerson> třídy Atom 1.0 a RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#2)]
 [!code-vb[SyndicationMapping#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#2)]  
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationPerson> serializován Atom 1.0.  
  
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
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationPerson> RSS 2.0 je serializována třídu, pokud pouze jeden <xref:System.ServiceModel.Syndication.SyndicationPerson> existuje v `Authors` nebo `Contributors` kolekcí, v uvedeném pořadí.  
  
```xml  
<author>Jesper.Aaberg@contoso.com</author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
```  
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationPerson> RSS 2.0 je serializována třídu, pokud více než jeden <xref:System.ServiceModel.Syndication.SyndicationPerson> existuje v `Authors` nebo `Contributors` kolekcí, v uvedeném pořadí.  
  
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
 Následující příklad kódu ukazuje, jak k serializaci <xref:System.ServiceModel.Syndication.SyndicationLink> třídy Atom 1.0 a RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#3)]
 [!code-vb[SyndicationMapping#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#3)]  
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationLink> serializován Atom 1.0.  
  
 `<link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationLink> serializovat do RSS 2.0.  
  
 `<a10:link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
## <a name="syndicationcategory"></a>SyndicationCategory  
 Následující příklad kódu ukazuje, jak k serializaci <xref:System.ServiceModel.Syndication.SyndicationCategory> třídy Atom 1.0 a RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#4)]
 [!code-vb[SyndicationMapping#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#4)]  
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationCategory> serializován Atom 1.0.  
  
 `<category term="categoryName" label="categoryLabel" scheme="categoryScheme" />`  
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationCategory> serializovat do RSS 2.0.  
  
 `<category domain="categoryScheme">categoryName</category>`  
  
## <a name="textsyndicationcontent"></a>TextSyndicationContent  
 Následující příklad kódu ukazuje, jak k serializaci <xref:System.ServiceModel.Syndication.TextSyndicationContent> třídy Atom 1.0 a RSS 2.0 při <xref:System.ServiceModel.Syndication.TextSyndicationContent> se vytvoří s obsah ve formátu HTML.  
  
 [!code-csharp[SyndicationMapping#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#5)]
 [!code-vb[SyndicationMapping#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#5)]  
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> Atom 1.0 je serializována třídu obsah ve formátu HTML.  
  
 `<content type="html"><html> some html </html></content>`  
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> RSS 2.0 je serializována třídu obsah ve formátu HTML.  
  
 `<description><html> some html </html></description>`  
  
 Následující příklad kódu ukazuje, jak k serializaci <xref:System.ServiceModel.Syndication.TextSyndicationContent> třídy Atom 1.0 a RSS 2.0 při <xref:System.ServiceModel.Syndication.TextSyndicationContent> se vytvoří s obsahem prostého textu.  
  
 [!code-csharp[SyndicationMapping#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#6)]
 [!code-vb[SyndicationMapping#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#6)]  
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> Atom 1.0 je serializována třídu s obsahem prostého textu.  
  
 `<content type="text">Some Plain Text</content>`  
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> RSS 2.0 je serializována třídu s obsahem prostého textu.  
  
 `<description>Some Plain Text</description>`  
  
 Následující příklad kódu ukazuje, jak k serializaci <xref:System.ServiceModel.Syndication.TextSyndicationContent> třídy Atom 1.0 a RSS 2.0 při <xref:System.ServiceModel.Syndication.TextSyndicationContent> se vytvoří s obsahem XHTML.  
  
 [!code-csharp[SyndicationMapping#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#7)]
 [!code-vb[SyndicationMapping#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#7)]  
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> je serializována třídu s obsahem XHTML Atom 1.0.  
  
 `<content type="xhtml">`  
  
 `<html> some xhtml </html>`  
  
 `</content>`  
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> RSS 2.0 je serializována třídu s obsahem XHTML.  
  
 `<description><html> some xhtml </html></description>`  
  
## <a name="urlsyndicationcontent"></a>UrlSyndicationContent  
 Následující příklad kódu ukazuje, jak k serializaci <xref:System.ServiceModel.Syndication.UrlSyndicationContent> třídy Atom 1.0 a RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#8)]
 [!code-vb[SyndicationMapping#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#8)]  
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.UrlSyndicationContent> je třída serializované Atom 1.0.  
  
 `<content type="audio" src="http://someurl/" />`  
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.UrlSyndicationContent> RSS 2.0 je serializována třídu s obsahem XHTML.  
  
 `<description />`  
  
 `<content type="audio" src="http://Contoso/someurl/" xmlns="http://www.w3.org/2005/Atom" />`  
  
## <a name="xmlsyndicationcontent"></a>XmlSyndicationContent  
 Následující příklad kódu ukazuje, jak k serializaci <xref:System.ServiceModel.Syndication.XmlSyndicationContent> třídy Atom 1.0 a RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#9)]
 [!code-vb[SyndicationMapping#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#9)]  
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.XmlSyndicationContent> je třída serializované Atom 1.0.  
  
 `<content type="mytype">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
 Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.XmlSyndicationContent> RSS 2.0 je serializována třídu s obsahem XHTML.  
  
 `<content type="mytype" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
## <a name="see-also"></a>Viz také:

- [Přehled syndikace WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)
- [Architektura syndikace](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)
- [Postupy: Vytvoření základního kanálu RSS](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-rss-feed.md)
- [Postupy: Vytvoření základního informačního kanálu Atom](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-atom-feed.md)
- [Postupy: Zveřejnění informačního kanálu ve formátu Atom i RSS](../../../../docs/framework/wcf/feature-details/how-to-expose-a-feed-as-both-atom-and-rss.md)

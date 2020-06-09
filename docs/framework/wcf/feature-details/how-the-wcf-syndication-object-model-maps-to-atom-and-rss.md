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
# <a name="how-the-wcf-syndication-object-model-maps-to-atom-and-rss"></a><span data-ttu-id="77f0c-102">Mapování modelu objektu syndikace WCF na Atom a RSS</span><span class="sxs-lookup"><span data-stu-id="77f0c-102">How the WCF Syndication Object Model Maps to Atom and RSS</span></span>
<span data-ttu-id="77f0c-103">Při vývoji služby syndikace Windows Communication Foundation (WCF) vytvoříte kanály a položky pomocí následujících tříd:</span><span class="sxs-lookup"><span data-stu-id="77f0c-103">When developing a Windows Communication Foundation (WCF) syndication service, you create feeds and items using the following classes:</span></span>  
  
- <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
- <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
- <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
- <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
- <xref:System.ServiceModel.Syndication.TextSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.UrlSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.XmlSyndicationContent>  
  
 <span data-ttu-id="77f0c-104"><xref:System.ServiceModel.Syndication.SyndicationFeed>Může být serializován do libovolného formátu syndikace, pro který je definován formátovací modul.</span><span class="sxs-lookup"><span data-stu-id="77f0c-104">A <xref:System.ServiceModel.Syndication.SyndicationFeed> can be serialized into any syndication format for which a formatter is defined.</span></span> <span data-ttu-id="77f0c-105">WCF se dodává se dvěma formátovacími moduly: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> a <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> .</span><span class="sxs-lookup"><span data-stu-id="77f0c-105">WCF ships with two formatters: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> and <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>.</span></span>  
  
 <span data-ttu-id="77f0c-106">Objektový model kolem <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> je úzce zarovnán se specifikací Atom 1,0, než specifikace RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-106">The object model around <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> is aligned more closely with the Atom 1.0 specification than the RSS 2.0 specification.</span></span> <span data-ttu-id="77f0c-107">Důvodem je, že Atom 1,0 je důležitější specifikace, která definuje prvky, které jsou nejednoznačné nebo jsou vynechány specifikací RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-107">This is because Atom 1.0 is a more substantial specification that defines elements that are ambiguous or omitted from the RSS 2.0 specification.</span></span> <span data-ttu-id="77f0c-108">Z tohoto důvodu mnoho položek v modelu objektu Syndikace WCF nemá přímo reprezentaci ve specifikaci RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-108">Because of this, many items in the WCF syndication object model have no direct representation in the RSS 2.0 specification.</span></span> <span data-ttu-id="77f0c-109">Při serializaci <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> objektů do kanálu RSS 2,0 umožňuje WCF serializovat datové prvky specifické pro Atom jako prvky rozšíření kvalifikované na obor názvů, které odpovídají specifikaci Atom.</span><span class="sxs-lookup"><span data-stu-id="77f0c-109">When serializing <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> objects into RSS 2.0, WCF allows you to serialize Atom-specific data elements as namespace-qualified extension elements that conform to the Atom specification.</span></span> <span data-ttu-id="77f0c-110">Můžete to řídit pomocí parametru předaného <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="77f0c-110">You can control this with a parameter passed to the <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> constructor.</span></span>  
  
 <span data-ttu-id="77f0c-111">Ukázky kódu v tomto tématu používají jednu ze dvou metod, které jsou zde definovány k provedení samotné serializace.</span><span class="sxs-lookup"><span data-stu-id="77f0c-111">The code samples in this topic use one of two methods defined here to do the actual serialization.</span></span>  
  
 <span data-ttu-id="77f0c-112">`SerializeFeed`serializace informačního kanálu syndikace.</span><span class="sxs-lookup"><span data-stu-id="77f0c-112">`SerializeFeed` serializes a syndication feed.</span></span>  
  
 [!code-csharp[SyndicationMapping#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#10)]
 [!code-vb[SyndicationMapping#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#10)]  
  
 <span data-ttu-id="77f0c-113">`SerializeItem`zaserializace syndikační položky.</span><span class="sxs-lookup"><span data-stu-id="77f0c-113">`SerializeItem` serializes a syndication item.</span></span>  
  
 [!code-csharp[SyndicationMapping#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#11)]
 [!code-vb[SyndicationMapping#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#11)]  
  
## <a name="syndicationfeed"></a><span data-ttu-id="77f0c-114">SyndicationFeed</span><span class="sxs-lookup"><span data-stu-id="77f0c-114">SyndicationFeed</span></span>  
 <span data-ttu-id="77f0c-115">Následující příklad kódu ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.SyndicationFeed> třídu na Atom 1,0 a RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-115">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationFeed> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#0)]
 [!code-vb[SyndicationMapping#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#0)]  
  
 <span data-ttu-id="77f0c-116">Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationFeed> je serializován do Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-116">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationFeed> is serialized to Atom 1.0.</span></span>  
  
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
  
 <span data-ttu-id="77f0c-117">Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationFeed> je serializován do kanálu RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-117">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationFeed> is serialized to RSS 2.0.</span></span>  
  
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
  
## <a name="syndicationitem"></a><span data-ttu-id="77f0c-118">SyndicationItem</span><span class="sxs-lookup"><span data-stu-id="77f0c-118">SyndicationItem</span></span>  
 <span data-ttu-id="77f0c-119">Následující příklad kódu ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.SyndicationItem> třídu na Atom 1,0 a RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-119">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationItem> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#1)]
 [!code-vb[SyndicationMapping#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#1)]  
  
 <span data-ttu-id="77f0c-120">Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationItem> je serializován do Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-120">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationItem> is serialized to Atom 1.0.</span></span>  
  
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
  
 <span data-ttu-id="77f0c-121">Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationItem> je serializován do kanálu RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-121">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationItem> is serialized to RSS 2.0.</span></span>  
  
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
  
## <a name="syndicationperson"></a><span data-ttu-id="77f0c-122">SyndicationPerson</span><span class="sxs-lookup"><span data-stu-id="77f0c-122">SyndicationPerson</span></span>  
 <span data-ttu-id="77f0c-123">Následující příklad kódu ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.SyndicationPerson> třídu na Atom 1,0 a RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-123">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationPerson> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#2)]
 [!code-vb[SyndicationMapping#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#2)]  
  
 <span data-ttu-id="77f0c-124">Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationPerson> je serializován do Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-124">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> is serialized to Atom 1.0.</span></span>  
  
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
  
 <span data-ttu-id="77f0c-125">Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationPerson> je třída serializována do kanálu RSS 2,0, pokud pouze jeden <xref:System.ServiceModel.Syndication.SyndicationPerson> existuje v `Authors` kolekci nebo v `Contributors` uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="77f0c-125">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> class is serialized to RSS 2.0 if only one <xref:System.ServiceModel.Syndication.SyndicationPerson> exists in the `Authors` or `Contributors` collections, respectively.</span></span>  
  
```xml  
<author>Jesper.Aaberg@contoso.com</author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
```  
  
 <span data-ttu-id="77f0c-126">Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationPerson> je třída serializována do kanálu RSS 2,0, pokud více než jeden <xref:System.ServiceModel.Syndication.SyndicationPerson> existuje v `Authors` kolekci nebo v `Contributors` uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="77f0c-126">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> class is serialized to RSS 2.0 if more than one <xref:System.ServiceModel.Syndication.SyndicationPerson> exists in the `Authors` or `Contributors` collections, respectively.</span></span>  
  
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
  
## <a name="syndicationlink"></a><span data-ttu-id="77f0c-127">SyndicationLink</span><span class="sxs-lookup"><span data-stu-id="77f0c-127">SyndicationLink</span></span>  
 <span data-ttu-id="77f0c-128">Následující příklad kódu ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.SyndicationLink> třídu na Atom 1,0 a RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-128">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationLink> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#3)]
 [!code-vb[SyndicationMapping#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#3)]  
  
 <span data-ttu-id="77f0c-129">Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationLink> je serializován do Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-129">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationLink> is serialized to Atom 1.0.</span></span>  
  
 `<link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
 <span data-ttu-id="77f0c-130">Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationLink> je serializován do kanálu RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-130">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationLink> is serialized to RSS 2.0.</span></span>  
  
 `<a10:link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
## <a name="syndicationcategory"></a><span data-ttu-id="77f0c-131">SyndicationCategory</span><span class="sxs-lookup"><span data-stu-id="77f0c-131">SyndicationCategory</span></span>  
 <span data-ttu-id="77f0c-132">Následující příklad kódu ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.SyndicationCategory> třídu na Atom 1,0 a RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-132">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationCategory> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#4)]
 [!code-vb[SyndicationMapping#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#4)]  
  
 <span data-ttu-id="77f0c-133">Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationCategory> je serializován do Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-133">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationCategory> is serialized to Atom 1.0.</span></span>  
  
 `<category term="categoryName" label="categoryLabel" scheme="categoryScheme" />`  
  
 <span data-ttu-id="77f0c-134">Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.SyndicationCategory> je serializován do kanálu RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-134">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationCategory> is serialized to RSS 2.0.</span></span>  
  
 `<category domain="categoryScheme">categoryName</category>`  
  
## <a name="textsyndicationcontent"></a><span data-ttu-id="77f0c-135">TextSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="77f0c-135">TextSyndicationContent</span></span>  
 <span data-ttu-id="77f0c-136">Následující příklad kódu ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.TextSyndicationContent> třídu do Atom 1,0 a RSS 2,0, když <xref:System.ServiceModel.Syndication.TextSyndicationContent> je vytvořen s obsahem HTML.</span><span class="sxs-lookup"><span data-stu-id="77f0c-136">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with HTML content.</span></span>  
  
 [!code-csharp[SyndicationMapping#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#5)]
 [!code-vb[SyndicationMapping#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#5)]  
  
 <span data-ttu-id="77f0c-137">Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> je třída s obsahem HTML serializována do Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-137">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with HTML content is serialized to Atom 1.0.</span></span>  
  
 `<content type="html"><html> some html </html></content>`  
  
 <span data-ttu-id="77f0c-138">Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> je třída s obsahem HTML serializována do kanálu RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-138">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with HTML content is serialized to RSS 2.0.</span></span>  
  
 `<description><html> some html </html></description>`  
  
 <span data-ttu-id="77f0c-139">Následující příklad kódu ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.TextSyndicationContent> třídu do Atom 1,0 a RSS 2,0, když <xref:System.ServiceModel.Syndication.TextSyndicationContent> je vytvořen obsah s prostým textem.</span><span class="sxs-lookup"><span data-stu-id="77f0c-139">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with plain text content.</span></span>  
  
 [!code-csharp[SyndicationMapping#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#6)]
 [!code-vb[SyndicationMapping#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#6)]  
  
 <span data-ttu-id="77f0c-140">Následující kód XML ukazuje, jakým způsobem <xref:System.ServiceModel.Syndication.TextSyndicationContent> je třída s obsahem prostého textu serializována do Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-140">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with plain text content is serialized to Atom 1.0.</span></span>  
  
 `<content type="text">Some Plain Text</content>`  
  
 <span data-ttu-id="77f0c-141">Následující kód XML ukazuje, jakým způsobem <xref:System.ServiceModel.Syndication.TextSyndicationContent> je třída s obsahem prostého textu serializována do kanálu RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-141">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with plain text content is serialized to RSS 2.0.</span></span>  
  
 `<description>Some Plain Text</description>`  
  
 <span data-ttu-id="77f0c-142">Následující příklad kódu ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.TextSyndicationContent> třídu do Atom 1,0 a RSS 2,0 při <xref:System.ServiceModel.Syndication.TextSyndicationContent> vytvoření pomocí obsahu XHTML.</span><span class="sxs-lookup"><span data-stu-id="77f0c-142">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with XHTML content.</span></span>  
  
 [!code-csharp[SyndicationMapping#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#7)]
 [!code-vb[SyndicationMapping#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#7)]  
  
 <span data-ttu-id="77f0c-143">Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> Třída s obsahem XHTML je serializována do Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-143">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with XHTML content is serialized to Atom 1.0.</span></span>  
  
 `<content type="xhtml">`  
  
 `<html> some xhtml </html>`  
  
 `</content>`  
  
 <span data-ttu-id="77f0c-144">Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> je třída s obsahem XHTML serializována do kanálu RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-144">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<description><html> some xhtml </html></description>`  
  
## <a name="urlsyndicationcontent"></a><span data-ttu-id="77f0c-145">UrlSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="77f0c-145">UrlSyndicationContent</span></span>  
 <span data-ttu-id="77f0c-146">Následující příklad kódu ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.UrlSyndicationContent> třídu na Atom 1,0 a RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-146">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#8)]
 [!code-vb[SyndicationMapping#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#8)]  
  
 <span data-ttu-id="77f0c-147">Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.UrlSyndicationContent> je třída serializována do Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-147">The following XML shows how the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class is serialized to Atom 1.0.</span></span>  
  
 `<content type="audio" src="http://someurl/" />`  
  
 <span data-ttu-id="77f0c-148">Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.UrlSyndicationContent> je třída s obsahem XHTML serializována do kanálu RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-148">The following XML shows how the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<description />`  
  
 `<content type="audio" src="http://Contoso/someurl/" xmlns="http://www.w3.org/2005/Atom" />`  
  
## <a name="xmlsyndicationcontent"></a><span data-ttu-id="77f0c-149">XmlSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="77f0c-149">XmlSyndicationContent</span></span>  
 <span data-ttu-id="77f0c-150">Následující příklad kódu ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.XmlSyndicationContent> třídu na Atom 1,0 a RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-150">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#9)]
 [!code-vb[SyndicationMapping#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#9)]  
  
 <span data-ttu-id="77f0c-151">Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.XmlSyndicationContent> je třída serializována do Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-151">The following XML shows how the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class is serialized to Atom 1.0.</span></span>  
  
 `<content type="mytype">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
 <span data-ttu-id="77f0c-152">Následující kód XML ukazuje, jak <xref:System.ServiceModel.Syndication.XmlSyndicationContent> je třída s obsahem XHTML serializována do kanálu RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="77f0c-152">The following XML shows how the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<content type="mytype" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
## <a name="see-also"></a><span data-ttu-id="77f0c-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="77f0c-153">See also</span></span>

- [<span data-ttu-id="77f0c-154">Syndikace WCF – přehled</span><span class="sxs-lookup"><span data-stu-id="77f0c-154">WCF Syndication Overview</span></span>](wcf-syndication-overview.md)
- [<span data-ttu-id="77f0c-155">Architektura syndikace</span><span class="sxs-lookup"><span data-stu-id="77f0c-155">Architecture of Syndication</span></span>](architecture-of-syndication.md)
- [<span data-ttu-id="77f0c-156">Postupy: Vytvoření základního kanálu RSS</span><span class="sxs-lookup"><span data-stu-id="77f0c-156">How to: Create a Basic RSS Feed</span></span>](how-to-create-a-basic-rss-feed.md)
- [<span data-ttu-id="77f0c-157">Postupy: Vytvoření základního informačního kanálu Atom</span><span class="sxs-lookup"><span data-stu-id="77f0c-157">How to: Create a Basic Atom Feed</span></span>](how-to-create-a-basic-atom-feed.md)
- [<span data-ttu-id="77f0c-158">Postupy: Zveřejnění informačního kanálu ve formátu Atom i RSS</span><span class="sxs-lookup"><span data-stu-id="77f0c-158">How to: Expose a Feed as Both Atom and RSS</span></span>](how-to-expose-a-feed-as-both-atom-and-rss.md)

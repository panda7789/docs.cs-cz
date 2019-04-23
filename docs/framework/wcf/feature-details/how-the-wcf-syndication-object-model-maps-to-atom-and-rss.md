---
title: Mapování modelu objektu syndikace WCF na Atom a RSS
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0365eb37-98cc-4b13-80fb-f1e78847a748
ms.openlocfilehash: b5a7f68edc49a02bb99ca05765d4582b798e72ef
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127384"
---
# <a name="how-the-wcf-syndication-object-model-maps-to-atom-and-rss"></a><span data-ttu-id="cf3bd-102">Mapování modelu objektu syndikace WCF na Atom a RSS</span><span class="sxs-lookup"><span data-stu-id="cf3bd-102">How the WCF Syndication Object Model Maps to Atom and RSS</span></span>
<span data-ttu-id="cf3bd-103">Při vývoji syndikace služby Windows Communication Foundation (WCF), můžete vytvořit kanály a položky pomocí následující třídy:</span><span class="sxs-lookup"><span data-stu-id="cf3bd-103">When developing a Windows Communication Foundation (WCF) syndication service, you create feeds and items using the following classes:</span></span>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.TextSyndicationContent>  
  
-   <xref:System.ServiceModel.Syndication.UrlSyndicationContent>  
  
-   <xref:System.ServiceModel.Syndication.XmlSyndicationContent>  
  
 <span data-ttu-id="cf3bd-104">A <xref:System.ServiceModel.Syndication.SyndicationFeed> lze serializovat do jakékoli souhrnný formát, pro který je definován formátovacím modulem.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-104">A <xref:System.ServiceModel.Syndication.SyndicationFeed> can be serialized into any syndication format for which a formatter is defined.</span></span> <span data-ttu-id="cf3bd-105">WCF se dodává se dvěma formátovací moduly: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> a <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-105">WCF ships with two formatters: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> and <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>.</span></span>  
  
 <span data-ttu-id="cf3bd-106">Objektový model kolem <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> zarovnán lépe než RSS 2.0 specifikace specifikaci Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-106">The object model around <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> is aligned more closely with the Atom 1.0 specification than the RSS 2.0 specification.</span></span> <span data-ttu-id="cf3bd-107">Je to proto Atom 1.0 je mnohem vyšší specifikace, která určuje prvky, které jsou nejednoznačný nebo není uveden ze specifikace RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-107">This is because Atom 1.0 is a more substantial specification that defines elements that are ambiguous or omitted from the RSS 2.0 specification.</span></span> <span data-ttu-id="cf3bd-108">Z tohoto důvodu mnoho položek v modelu objektu syndikace WCF nemají žádnou přímou reprezentaci ve specifikaci RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-108">Because of this, many items in the WCF syndication object model have no direct representation in the RSS 2.0 specification.</span></span> <span data-ttu-id="cf3bd-109">Při serializaci <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> objektů do RSS 2.0 WCF umožňuje serializovat specifické pro formát Atom datové prvky jako rozšíření kvalifikovaný v oboru názvů elementy, které odpovídají specifikaci Atom.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-109">When serializing <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> objects into RSS 2.0, WCF allows you to serialize Atom-specific data elements as namespace-qualified extension elements that conform to the Atom specification.</span></span> <span data-ttu-id="cf3bd-110">Můžete to ovládacím prvkem parametr předán <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-110">You can control this with a parameter passed to the <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> constructor.</span></span>  
  
 <span data-ttu-id="cf3bd-111">Ukázky kódu v tomto tématu využívají jednu ze dvou metod lze tam definovat provedete skutečné serializace.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-111">The code samples in this topic use one of two methods defined here to do the actual serialization.</span></span>  
  
 <span data-ttu-id="cf3bd-112">`SerializeFeed` serializuje informačního kanálu syndikace.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-112">`SerializeFeed` serializes a syndication feed.</span></span>  
  
 [!code-csharp[SyndicationMapping#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#10)]
 [!code-vb[SyndicationMapping#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#10)]  
  
 <span data-ttu-id="cf3bd-113">`SerializeItem` serializuje položky syndikace.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-113">`SerializeItem` serializes a syndication item.</span></span>  
  
 [!code-csharp[SyndicationMapping#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#11)]
 [!code-vb[SyndicationMapping#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#11)]  
  
## <a name="syndicationfeed"></a><span data-ttu-id="cf3bd-114">SyndicationFeed</span><span class="sxs-lookup"><span data-stu-id="cf3bd-114">SyndicationFeed</span></span>  
 <span data-ttu-id="cf3bd-115">Následující příklad kódu ukazuje, jak k serializaci <xref:System.ServiceModel.Syndication.SyndicationFeed> třídy Atom 1.0 a RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-115">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationFeed> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#0)]
 [!code-vb[SyndicationMapping#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#0)]  
  
 <span data-ttu-id="cf3bd-116">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationFeed> serializován Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-116">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationFeed> is serialized to Atom 1.0.</span></span>  
  
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
  
 <span data-ttu-id="cf3bd-117">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationFeed> serializovat do RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-117">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationFeed> is serialized to RSS 2.0.</span></span>  
  
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
  
## <a name="syndicationitem"></a><span data-ttu-id="cf3bd-118">SyndicationItem</span><span class="sxs-lookup"><span data-stu-id="cf3bd-118">SyndicationItem</span></span>  
 <span data-ttu-id="cf3bd-119">Následující příklad kódu ukazuje, jak k serializaci <xref:System.ServiceModel.Syndication.SyndicationItem> třídy Atom 1.0 a RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-119">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationItem> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#1)]
 [!code-vb[SyndicationMapping#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#1)]  
  
 <span data-ttu-id="cf3bd-120">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationItem> serializován Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-120">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationItem> is serialized to Atom 1.0.</span></span>  
  
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
  
 <span data-ttu-id="cf3bd-121">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationItem> serializovat do RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-121">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationItem> is serialized to RSS 2.0.</span></span>  
  
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
  
## <a name="syndicationperson"></a><span data-ttu-id="cf3bd-122">SyndicationPerson</span><span class="sxs-lookup"><span data-stu-id="cf3bd-122">SyndicationPerson</span></span>  
 <span data-ttu-id="cf3bd-123">Následující příklad kódu ukazuje, jak k serializaci <xref:System.ServiceModel.Syndication.SyndicationPerson> třídy Atom 1.0 a RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-123">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationPerson> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#2)]
 [!code-vb[SyndicationMapping#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#2)]  
  
 <span data-ttu-id="cf3bd-124">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationPerson> serializován Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-124">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> is serialized to Atom 1.0.</span></span>  
  
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
  
 <span data-ttu-id="cf3bd-125">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationPerson> RSS 2.0 je serializována třídu, pokud pouze jeden <xref:System.ServiceModel.Syndication.SyndicationPerson> existuje v `Authors` nebo `Contributors` kolekcí, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-125">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> class is serialized to RSS 2.0 if only one <xref:System.ServiceModel.Syndication.SyndicationPerson> exists in the `Authors` or `Contributors` collections, respectively.</span></span>  
  
```xml  
<author>Jesper.Aaberg@contoso.com</author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
```  
  
 <span data-ttu-id="cf3bd-126">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationPerson> RSS 2.0 je serializována třídu, pokud více než jeden <xref:System.ServiceModel.Syndication.SyndicationPerson> existuje v `Authors` nebo `Contributors` kolekcí, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-126">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> class is serialized to RSS 2.0 if more than one <xref:System.ServiceModel.Syndication.SyndicationPerson> exists in the `Authors` or `Contributors` collections, respectively.</span></span>  
  
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
  
## <a name="syndicationlink"></a><span data-ttu-id="cf3bd-127">SyndicationLink</span><span class="sxs-lookup"><span data-stu-id="cf3bd-127">SyndicationLink</span></span>  
 <span data-ttu-id="cf3bd-128">Následující příklad kódu ukazuje, jak k serializaci <xref:System.ServiceModel.Syndication.SyndicationLink> třídy Atom 1.0 a RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-128">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationLink> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#3)]
 [!code-vb[SyndicationMapping#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#3)]  
  
 <span data-ttu-id="cf3bd-129">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationLink> serializován Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-129">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationLink> is serialized to Atom 1.0.</span></span>  
  
 `<link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
 <span data-ttu-id="cf3bd-130">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationLink> serializovat do RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-130">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationLink> is serialized to RSS 2.0.</span></span>  
  
 `<a10:link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
## <a name="syndicationcategory"></a><span data-ttu-id="cf3bd-131">SyndicationCategory</span><span class="sxs-lookup"><span data-stu-id="cf3bd-131">SyndicationCategory</span></span>  
 <span data-ttu-id="cf3bd-132">Následující příklad kódu ukazuje, jak k serializaci <xref:System.ServiceModel.Syndication.SyndicationCategory> třídy Atom 1.0 a RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-132">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationCategory> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#4)]
 [!code-vb[SyndicationMapping#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#4)]  
  
 <span data-ttu-id="cf3bd-133">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationCategory> serializován Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-133">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationCategory> is serialized to Atom 1.0.</span></span>  
  
 `<category term="categoryName" label="categoryLabel" scheme="categoryScheme" />`  
  
 <span data-ttu-id="cf3bd-134">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.SyndicationCategory> serializovat do RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-134">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationCategory> is serialized to RSS 2.0.</span></span>  
  
 `<category domain="categoryScheme">categoryName</category>`  
  
## <a name="textsyndicationcontent"></a><span data-ttu-id="cf3bd-135">TextSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="cf3bd-135">TextSyndicationContent</span></span>  
 <span data-ttu-id="cf3bd-136">Následující příklad kódu ukazuje, jak k serializaci <xref:System.ServiceModel.Syndication.TextSyndicationContent> třídy Atom 1.0 a RSS 2.0 při <xref:System.ServiceModel.Syndication.TextSyndicationContent> se vytvoří s obsah ve formátu HTML.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-136">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with HTML content.</span></span>  
  
 [!code-csharp[SyndicationMapping#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#5)]
 [!code-vb[SyndicationMapping#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#5)]  
  
 <span data-ttu-id="cf3bd-137">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> Atom 1.0 je serializována třídu obsah ve formátu HTML.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-137">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with HTML content is serialized to Atom 1.0.</span></span>  
  
 `<content type="html"><html> some html </html></content>`  
  
 <span data-ttu-id="cf3bd-138">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> RSS 2.0 je serializována třídu obsah ve formátu HTML.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-138">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with HTML content is serialized to RSS 2.0.</span></span>  
  
 `<description><html> some html </html></description>`  
  
 <span data-ttu-id="cf3bd-139">Následující příklad kódu ukazuje, jak k serializaci <xref:System.ServiceModel.Syndication.TextSyndicationContent> třídy Atom 1.0 a RSS 2.0 při <xref:System.ServiceModel.Syndication.TextSyndicationContent> se vytvoří s obsahem prostého textu.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-139">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with plain text content.</span></span>  
  
 [!code-csharp[SyndicationMapping#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#6)]
 [!code-vb[SyndicationMapping#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#6)]  
  
 <span data-ttu-id="cf3bd-140">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> Atom 1.0 je serializována třídu s obsahem prostého textu.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-140">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with plain text content is serialized to Atom 1.0.</span></span>  
  
 `<content type="text">Some Plain Text</content>`  
  
 <span data-ttu-id="cf3bd-141">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> RSS 2.0 je serializována třídu s obsahem prostého textu.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-141">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with plain text content is serialized to RSS 2.0.</span></span>  
  
 `<description>Some Plain Text</description>`  
  
 <span data-ttu-id="cf3bd-142">Následující příklad kódu ukazuje, jak k serializaci <xref:System.ServiceModel.Syndication.TextSyndicationContent> třídy Atom 1.0 a RSS 2.0 při <xref:System.ServiceModel.Syndication.TextSyndicationContent> se vytvoří s obsahem XHTML.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-142">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with XHTML content.</span></span>  
  
 [!code-csharp[SyndicationMapping#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#7)]
 [!code-vb[SyndicationMapping#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#7)]  
  
 <span data-ttu-id="cf3bd-143">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> je serializována třídu s obsahem XHTML Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-143">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with XHTML content is serialized to Atom 1.0.</span></span>  
  
 `<content type="xhtml">`  
  
 `<html> some xhtml </html>`  
  
 `</content>`  
  
 <span data-ttu-id="cf3bd-144">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> RSS 2.0 je serializována třídu s obsahem XHTML.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-144">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<description><html> some xhtml </html></description>`  
  
## <a name="urlsyndicationcontent"></a><span data-ttu-id="cf3bd-145">UrlSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="cf3bd-145">UrlSyndicationContent</span></span>  
 <span data-ttu-id="cf3bd-146">Následující příklad kódu ukazuje, jak k serializaci <xref:System.ServiceModel.Syndication.UrlSyndicationContent> třídy Atom 1.0 a RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-146">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#8)]
 [!code-vb[SyndicationMapping#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#8)]  
  
 <span data-ttu-id="cf3bd-147">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.UrlSyndicationContent> je třída serializované Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-147">The following XML shows how the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class is serialized to Atom 1.0.</span></span>  
  
 `<content type="audio" src="http://someurl/" />`  
  
 <span data-ttu-id="cf3bd-148">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.UrlSyndicationContent> RSS 2.0 je serializována třídu s obsahem XHTML.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-148">The following XML shows how the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<description />`  
  
 `<content type="audio" src="http://Contoso/someurl/" xmlns="http://www.w3.org/2005/Atom" />`  
  
## <a name="xmlsyndicationcontent"></a><span data-ttu-id="cf3bd-149">XmlSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="cf3bd-149">XmlSyndicationContent</span></span>  
 <span data-ttu-id="cf3bd-150">Následující příklad kódu ukazuje, jak k serializaci <xref:System.ServiceModel.Syndication.XmlSyndicationContent> třídy Atom 1.0 a RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-150">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#9)]
 [!code-vb[SyndicationMapping#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#9)]  
  
 <span data-ttu-id="cf3bd-151">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.XmlSyndicationContent> je třída serializované Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-151">The following XML shows how the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class is serialized to Atom 1.0.</span></span>  
  
 `<content type="mytype">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
 <span data-ttu-id="cf3bd-152">Následující XML ukazuje jak <xref:System.ServiceModel.Syndication.XmlSyndicationContent> RSS 2.0 je serializována třídu s obsahem XHTML.</span><span class="sxs-lookup"><span data-stu-id="cf3bd-152">The following XML shows how the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<content type="mytype" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
## <a name="see-also"></a><span data-ttu-id="cf3bd-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf3bd-153">See also</span></span>

- [<span data-ttu-id="cf3bd-154">Přehled syndikace WCF</span><span class="sxs-lookup"><span data-stu-id="cf3bd-154">WCF Syndication Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)
- [<span data-ttu-id="cf3bd-155">Architektura syndikace</span><span class="sxs-lookup"><span data-stu-id="cf3bd-155">Architecture of Syndication</span></span>](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)
- [<span data-ttu-id="cf3bd-156">Postupy: Vytvoření základního kanálu RSS</span><span class="sxs-lookup"><span data-stu-id="cf3bd-156">How to: Create a Basic RSS Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-rss-feed.md)
- [<span data-ttu-id="cf3bd-157">Postupy: Vytvoření základního informačního kanálu Atom</span><span class="sxs-lookup"><span data-stu-id="cf3bd-157">How to: Create a Basic Atom Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-atom-feed.md)
- [<span data-ttu-id="cf3bd-158">Postupy: Zveřejnění informačního kanálu ve formátu Atom i RSS</span><span class="sxs-lookup"><span data-stu-id="cf3bd-158">How to: Expose a Feed as Both Atom and RSS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-expose-a-feed-as-both-atom-and-rss.md)

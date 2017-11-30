---
title: Namespace XPath navigace
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: beb6265e8b245893cd7fa5edca28ba1b081481ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xpath-namespace-navigation"></a><span data-ttu-id="e4b45-102">Namespace XPath navigace</span><span class="sxs-lookup"><span data-stu-id="e4b45-102">XPath Namespace Navigation</span></span>
<span data-ttu-id="e4b45-103">Chcete-li používat dotazy jazyka XPath s dokumenty XML, budete muset správně adres obory názvů XML a elementů obsažených ve obory názvů.</span><span class="sxs-lookup"><span data-stu-id="e4b45-103">To use XPath queries with XML documents, you have to correctly address XML namespaces and the elements contained by namespaces.</span></span> <span data-ttu-id="e4b45-104">Obory názvů zabránilo nejednoznačnosti, které může dojít, když se názvy jsou použity v více než jeden kontextu; například název `ID` mohou odkazovat na více než jeden identifikátor přidružený ke různé prvky dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="e4b45-104">Namespaces prevent ambiguities that can occur when names are used in more than one context; for example, the name `ID` may refer to more than one identifier associated with different elements of an XML document.</span></span> <span data-ttu-id="e4b45-105">Syntaxe Namespace určuje identifikátory URI, názvů a předpony, které rozlišení prvků dokument XML.</span><span class="sxs-lookup"><span data-stu-id="e4b45-105">Namespace syntax specifies URIs, names, and prefixes that distinguish the elements of an XML document.</span></span>  
  
 <span data-ttu-id="e4b45-106">V příkladu v tomto tématu demonstruje použití předpony v dokumentu XML se navigace <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="e4b45-106">The example in this topic demonstrates the use of prefixes in navigating an XML document with <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="e4b45-107">Další informace o syntaxi a obory názvů najdete v tématu [obory názvů XML](http://go.microsoft.com/fwlink/?linkid=140245).</span><span class="sxs-lookup"><span data-stu-id="e4b45-107">For more information about namespaces and syntax, see [Understanding XML Namespaces](http://go.microsoft.com/fwlink/?linkid=140245).</span></span>  
  
## <a name="namespace-declarations"></a><span data-ttu-id="e4b45-108">Namespace – deklarace</span><span class="sxs-lookup"><span data-stu-id="e4b45-108">Namespace Declarations</span></span>  
 <span data-ttu-id="e4b45-109">Namespace – deklarace Zkontrolujte elementy dokumentu XML odlišit a adresovatelné při použití instance <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="e4b45-109">Namespace declarations make the elements of an XML document distinguishable and addressable when using an instance of <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="e4b45-110">Namespace předpony zadejte stručný syntaxe pro adresování obory názvů.</span><span class="sxs-lookup"><span data-stu-id="e4b45-110">Namespace prefixes provide a brief syntax for addressing namespaces.</span></span>  
  
 <span data-ttu-id="e4b45-111">Formuláře jsou definovány předpony: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` v této syntaxe předponu "`e`" je zkratka pro formální identifikátor URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e4b45-111">Prefixes are defined by the form: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` In this syntax the prefix "`e`" is an abbreviation for the formal URI of the namespace.</span></span> <span data-ttu-id="e4b45-112">Můžete identifikovat `Body` element jako člena `Envelope` oboru názvů pomocí syntaxe: `e:Body`.</span><span class="sxs-lookup"><span data-stu-id="e4b45-112">You can identify the `Body` element as a member of the `Envelope` namespace by using the syntax: `e:Body`.</span></span>  
  
 <span data-ttu-id="e4b45-113">V následujícím dokumentu XML se bude odkazovat jako `response.xml` v příkladu navigace v další části.</span><span class="sxs-lookup"><span data-stu-id="e4b45-113">The following XML document will be referenced as `response.xml` in the navigation example in the next section.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<e:Envelope xmlns:e="http://schemas.xmlsoap.org/soap/envelope/">  
  <e:Body>  
    <s:Search xmlns:s="http://schemas.microsoft.com/v1/Search">  
      <r:request xmlns:r="http://schemas.microsoft.com/v1/Search/metadata"   
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance">  
      </r:request>  
    </s:Search>  
  </e:Body>  
</e:Envelope>  
```  
  
## <a name="navigation-by-namespace-prefix"></a><span data-ttu-id="e4b45-114">Navigace podle předpony Namespace</span><span class="sxs-lookup"><span data-stu-id="e4b45-114">Navigation by Namespace Prefix</span></span>  
 <span data-ttu-id="e4b45-115">Kód v této části používá <xref:System.Xml.XPath.XPathNavigator> a <xref:System.Xml.XmlNamespaceManager> objektů k výběru `Search` elementu z dokumentu XML v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="e4b45-115">The code in this section uses <xref:System.Xml.XPath.XPathNavigator> and <xref:System.Xml.XmlNamespaceManager> objects to select the `Search` element from the XML document in the previous section.</span></span> <span data-ttu-id="e4b45-116">Dotaz `xpath` zahrnuje předpony oboru názvů na každý prvek v cestě.</span><span class="sxs-lookup"><span data-stu-id="e4b45-116">The query `xpath` includes namespace prefixes on each element in the path.</span></span> <span data-ttu-id="e4b45-117">Určení přesné identity obory názvů, které obsahují každý prvek zaručuje správné navigace k `Search` element podle <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e4b45-117">Specifying the precise identity of the namespaces that contain each element assures correct navigation to the `Search` element by the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method.</span></span>  
  
```  
using (XmlReader reader = XmlReader.Create("response.xml"))  
            {  
                XPathDocument doc = new XPathDocument(reader);  
                XPathNavigator nav = doc.CreateNavigator();  
                XmlNamespaceManager nsmgr =  
                         new XmlNamespaceManager(nav.NameTable);  
                nsmgr.AddNamespace("e",   
                         @"http://schemas.xmlsoap.org/soap/envelope/");  
                nsmgr.AddNamespace("s",   
                            @"http://schemas.microsoft.com/v1/Search");  
                nsmgr.AddNamespace("r",   
                   @"http://schemas.microsoft.com/v1/Search/metadata");  
                nsmgr.AddNamespace("i",   
                         @"http://www.w3.org/2001/XMLSchema-instance");  
  
                string xpath = "/e:Envelope/e:Body/s:Search";  
  
                XPathNavigator element = nav.SelectSingleNode(xpath, nsmgr);  
  
                Console.WriteLine("Element Prefix:" + element.Prefix +   
                           " Local name:" + element.LocalName);  
                Console.WriteLine("Namespace URI: " +   
                            element.NamespaceURI);  
  
            }  
```  
  
 <span data-ttu-id="e4b45-118">Přesnost plně kvalifikované názvy oborů názvů a je větší než pro vaše pohodlí.</span><span class="sxs-lookup"><span data-stu-id="e4b45-118">The precision of fully qualifying namespaces and names is more than a convenience.</span></span> <span data-ttu-id="e4b45-119">Trochu experimenty s definice dokumentu a kódu v předchozích příkladech ověří, že navigační bez element plně kvalifikované názvy vyvolá výjimek.</span><span class="sxs-lookup"><span data-stu-id="e4b45-119">A little experimentation with the document definition and code in the previous examples will verify that navigation without fully qualified element names throws exceptions.</span></span> <span data-ttu-id="e4b45-120">Například definice elementu: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`a dotazů: řetězec `xpath = "/s:Envelope/s:Body/Search";` bez Předpona oboru názvů na `Search` element vrátí `null` místo `Search` elementu.</span><span class="sxs-lookup"><span data-stu-id="e4b45-120">For example, the element definition: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`, and query: string `xpath = "/s:Envelope/s:Body/Search";` without the namespace prefix on the `Search` element returns `null` instead of the `Search` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4b45-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4b45-121">See Also</span></span>  
 [<span data-ttu-id="e4b45-122">Přístup k datům XML pomocí objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="e4b45-122">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="e4b45-123">Výběr, Evaluating a porovnávání dat XML pomocí objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="e4b45-123">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)

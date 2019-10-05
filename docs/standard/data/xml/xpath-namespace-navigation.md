---
title: Navigace oboru názvů XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f6facc047d87c503313015eff4e869861cd6b301
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957003"
---
# <a name="xpath-namespace-navigation"></a><span data-ttu-id="f7885-102">Navigace oboru názvů XPath</span><span class="sxs-lookup"><span data-stu-id="f7885-102">XPath Namespace Navigation</span></span>
<span data-ttu-id="f7885-103">Chcete-li používat dotazy XPath s dokumenty XML, je nutné správně adresovat obory názvů XML a prvky obsažené v oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="f7885-103">To use XPath queries with XML documents, you have to correctly address XML namespaces and the elements contained by namespaces.</span></span> <span data-ttu-id="f7885-104">Obory názvů zabraňují nejednoznačnosti, ke kterým může dojít, když se názvy používají ve více než jednom kontextu. například název `ID` může odkazovat na více než jeden identifikátor přidružený k různým prvkům dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f7885-104">Namespaces prevent ambiguities that can occur when names are used in more than one context; for example, the name `ID` may refer to more than one identifier associated with different elements of an XML document.</span></span> <span data-ttu-id="f7885-105">Syntaxe oboru názvů určuje identifikátory URI, názvy a předpony, které odlišují prvky dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f7885-105">Namespace syntax specifies URIs, names, and prefixes that distinguish the elements of an XML document.</span></span>  
  
 <span data-ttu-id="f7885-106">Příklad v tomto tématu ukazuje použití předpon v navigaci dokumentu XML s <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="f7885-106">The example in this topic demonstrates the use of prefixes in navigating an XML document with <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="f7885-107">Další informace o oborech názvů a syntaxi naleznete v tématu [soubory XML: porozumění oborům názvů XML](https://docs.microsoft.com/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="f7885-107">For more information about namespaces and syntax, see [XML Files: Understanding XML Namespaces](https://docs.microsoft.com/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span></span>  
  
## <a name="namespace-declarations"></a><span data-ttu-id="f7885-108">Deklarace oboru názvů</span><span class="sxs-lookup"><span data-stu-id="f7885-108">Namespace Declarations</span></span>  
 <span data-ttu-id="f7885-109">Deklarace oboru názvů umožňují, aby prvky dokumentu XML byly rozlišené a adresovatelné při použití instance <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="f7885-109">Namespace declarations make the elements of an XML document distinguishable and addressable when using an instance of <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="f7885-110">Předpony oboru názvů poskytují stručnou syntaxi pro adresování oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="f7885-110">Namespace prefixes provide a brief syntax for addressing namespaces.</span></span>  
  
 <span data-ttu-id="f7885-111">Předpony jsou definovány ve formě: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` v této syntaxi je prefixem "`e`" zkratka pro formální identifikátor URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f7885-111">Prefixes are defined by the form: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` In this syntax the prefix "`e`" is an abbreviation for the formal URI of the namespace.</span></span> <span data-ttu-id="f7885-112">Element `Body` můžete identifikovat jako člen oboru názvů `Envelope` pomocí syntaxe: `e:Body`.</span><span class="sxs-lookup"><span data-stu-id="f7885-112">You can identify the `Body` element as a member of the `Envelope` namespace by using the syntax: `e:Body`.</span></span>  
  
 <span data-ttu-id="f7885-113">Následující dokument XML bude v navigačním příkladu v následující části odkazován jako `response.xml`.</span><span class="sxs-lookup"><span data-stu-id="f7885-113">The following XML document will be referenced as `response.xml` in the navigation example in the next section.</span></span>  
  
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
  
## <a name="navigation-by-namespace-prefix"></a><span data-ttu-id="f7885-114">Navigace podle předpony oboru názvů</span><span class="sxs-lookup"><span data-stu-id="f7885-114">Navigation by Namespace Prefix</span></span>  
 <span data-ttu-id="f7885-115">Kód v této části používá @no__t objekty-0 a <xref:System.Xml.XmlNamespaceManager> k výběru prvku `Search` z dokumentu XML v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="f7885-115">The code in this section uses <xref:System.Xml.XPath.XPathNavigator> and <xref:System.Xml.XmlNamespaceManager> objects to select the `Search` element from the XML document in the previous section.</span></span> <span data-ttu-id="f7885-116">Dotaz `xpath` zahrnuje předpony oboru názvů pro každý prvek v cestě.</span><span class="sxs-lookup"><span data-stu-id="f7885-116">The query `xpath` includes namespace prefixes on each element in the path.</span></span> <span data-ttu-id="f7885-117">Určení přesné identity oborů názvů, které obsahují jednotlivé prvky, zajišťuje správné procházení prvku `Search` metodou <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>.</span><span class="sxs-lookup"><span data-stu-id="f7885-117">Specifying the precise identity of the namespaces that contain each element assures correct navigation to the `Search` element by the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method.</span></span>  
  
```csharp  
using (XmlReader reader = XmlReader.Create("response.xml"))  
{  
    XPathDocument doc = new XPathDocument(reader);  
    XPathNavigator nav = doc.CreateNavigator();
  
    XmlNamespaceManager nsmgr = new XmlNamespaceManager(nav.NameTable);  
    nsmgr.AddNamespace("e", @"http://schemas.xmlsoap.org/soap/envelope/");  
    nsmgr.AddNamespace("s", @"http://schemas.microsoft.com/v1/Search");  
    nsmgr.AddNamespace("r", @"http://schemas.microsoft.com/v1/Search/metadata");  
    nsmgr.AddNamespace("i", @"http://www.w3.org/2001/XMLSchema-instance");  
  
    string xpath = "/e:Envelope/e:Body/s:Search";  
  
    XPathNavigator element = nav.SelectSingleNode(xpath, nsmgr);  
  
    Console.WriteLine("Element Prefix:" + element.Prefix +   
    " Local name:" + element.LocalName);  
    Console.WriteLine("Namespace URI: " + element.NamespaceURI);  
}  
```  
  
 <span data-ttu-id="f7885-118">Přesnost plně kvalifikovaného oboru názvů a názvů je větší než pohodlí.</span><span class="sxs-lookup"><span data-stu-id="f7885-118">The precision of fully qualifying namespaces and names is more than a convenience.</span></span> <span data-ttu-id="f7885-119">Trochu experimentování s definicí dokumentu a kódem v předchozích příkladech ověří, zda navigace bez úplných názvů prvků vyvolá výjimky.</span><span class="sxs-lookup"><span data-stu-id="f7885-119">A little experimentation with the document definition and code in the previous examples will verify that navigation without fully qualified element names throws exceptions.</span></span> <span data-ttu-id="f7885-120">Například definice elementu: `<Search xmlns="http://schemas.microsoft.com/v1/Search">` a dotaz: řetězec `xpath = "/s:Envelope/s:Body/Search";` bez předpony oboru názvů na elementu `Search` vrátí `null` namísto prvku `Search`.</span><span class="sxs-lookup"><span data-stu-id="f7885-120">For example, the element definition: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`, and query: string `xpath = "/s:Envelope/s:Body/Search";` without the namespace prefix on the `Search` element returns `null` instead of the `Search` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7885-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7885-121">See also</span></span>

- [<span data-ttu-id="f7885-122">Přístup k datům XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f7885-122">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="f7885-123">Výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f7885-123">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)

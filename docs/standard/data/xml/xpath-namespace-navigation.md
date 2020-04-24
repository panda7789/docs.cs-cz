---
title: Navigace oboru názvů XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
ms.openlocfilehash: f35318b1439b762bf7c87cff217ed1787e8d007c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156319"
---
# <a name="xpath-namespace-navigation"></a><span data-ttu-id="04b91-102">Navigace oboru názvů XPath</span><span class="sxs-lookup"><span data-stu-id="04b91-102">XPath Namespace Navigation</span></span>
<span data-ttu-id="04b91-103">Chcete-li používat dotazy XPath s dokumenty XML, je nutné správně adresovat obory názvů XML a prvky obsažené v oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="04b91-103">To use XPath queries with XML documents, you have to correctly address XML namespaces and the elements contained by namespaces.</span></span> <span data-ttu-id="04b91-104">Obory názvů zabraňují nejednoznačnosti, ke kterým může dojít, když se názvy používají ve více než jednom kontextu. název `ID` může například odkazovat na více než jeden identifikátor přidružený k různým prvkům dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="04b91-104">Namespaces prevent ambiguities that can occur when names are used in more than one context; for example, the name `ID` may refer to more than one identifier associated with different elements of an XML document.</span></span> <span data-ttu-id="04b91-105">Syntaxe oboru názvů určuje identifikátory URI, názvy a předpony, které odlišují prvky dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="04b91-105">Namespace syntax specifies URIs, names, and prefixes that distinguish the elements of an XML document.</span></span>  
  
 <span data-ttu-id="04b91-106">Příklad v tomto tématu ukazuje použití předpon v tématu navigace v dokumentu XML s <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="04b91-106">The example in this topic demonstrates the use of prefixes in navigating an XML document with <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="04b91-107">Další informace o oborech názvů a syntaxi naleznete v tématu [soubory XML: porozumění oborům názvů XML](https://docs.microsoft.com/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="04b91-107">For more information about namespaces and syntax, see [XML Files: Understanding XML Namespaces](https://docs.microsoft.com/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span></span>  
  
## <a name="namespace-declarations"></a><span data-ttu-id="04b91-108">Deklarace oboru názvů</span><span class="sxs-lookup"><span data-stu-id="04b91-108">Namespace Declarations</span></span>  
 <span data-ttu-id="04b91-109">Deklarace oboru názvů usnadňují prvky dokumentu XML, které by měly být rozlišené a adresovatelné při <xref:System.Xml.XPath.XPathNavigator>použití instance.</span><span class="sxs-lookup"><span data-stu-id="04b91-109">Namespace declarations make the elements of an XML document distinguishable and addressable when using an instance of <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="04b91-110">Předpony oboru názvů poskytují stručnou syntaxi pro adresování oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="04b91-110">Namespace prefixes provide a brief syntax for addressing namespaces.</span></span>  
  
 <span data-ttu-id="04b91-111">Předpony jsou definovány formulářem: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` v této syntaxi je prefixem`e`zkratka pro formální identifikátor URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="04b91-111">Prefixes are defined by the form: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` In this syntax the prefix "`e`" is an abbreviation for the formal URI of the namespace.</span></span> <span data-ttu-id="04b91-112">`Body` Element můžete identifikovat jako člena `Envelope` oboru názvů pomocí syntaxe: `e:Body`.</span><span class="sxs-lookup"><span data-stu-id="04b91-112">You can identify the `Body` element as a member of the `Envelope` namespace by using the syntax: `e:Body`.</span></span>  
  
 <span data-ttu-id="04b91-113">Následující dokument XML bude odkazován jako `response.xml` v navigačním příkladu v následující části.</span><span class="sxs-lookup"><span data-stu-id="04b91-113">The following XML document will be referenced as `response.xml` in the navigation example in the next section.</span></span>  
  
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
  
## <a name="navigation-by-namespace-prefix"></a><span data-ttu-id="04b91-114">Navigace podle předpony oboru názvů</span><span class="sxs-lookup"><span data-stu-id="04b91-114">Navigation by Namespace Prefix</span></span>  
 <span data-ttu-id="04b91-115">Kód v této části používá <xref:System.Xml.XPath.XPathNavigator> a <xref:System.Xml.XmlNamespaceManager> objekty pro výběr `Search` elementu z dokumentu XML v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="04b91-115">The code in this section uses <xref:System.Xml.XPath.XPathNavigator> and <xref:System.Xml.XmlNamespaceManager> objects to select the `Search` element from the XML document in the previous section.</span></span> <span data-ttu-id="04b91-116">Dotaz `xpath` obsahuje předpony oboru názvů u každého elementu v cestě.</span><span class="sxs-lookup"><span data-stu-id="04b91-116">The query `xpath` includes namespace prefixes on each element in the path.</span></span> <span data-ttu-id="04b91-117">Určení přesné identity oborů názvů, které obsahují jednotlivé prvky, zajišťuje správné procházení `Search` prvku <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metodou.</span><span class="sxs-lookup"><span data-stu-id="04b91-117">Specifying the precise identity of the namespaces that contain each element assures correct navigation to the `Search` element by the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="04b91-118">Přesnost plně kvalifikovaného oboru názvů a názvů je větší než pohodlí.</span><span class="sxs-lookup"><span data-stu-id="04b91-118">The precision of fully qualifying namespaces and names is more than a convenience.</span></span> <span data-ttu-id="04b91-119">Trochu experimentování s definicí dokumentu a kódem v předchozích příkladech ověří, zda navigace bez úplných názvů prvků vyvolá výjimky.</span><span class="sxs-lookup"><span data-stu-id="04b91-119">A little experimentation with the document definition and code in the previous examples will verify that navigation without fully qualified element names throws exceptions.</span></span> <span data-ttu-id="04b91-120">`<Search xmlns="http://schemas.microsoft.com/v1/Search">`Například definice prvku: a dotaz: řetězec `xpath = "/s:Envelope/s:Body/Search";` bez předpony oboru názvů na `Search` elementu vrátí `null` místo `Search` elementu.</span><span class="sxs-lookup"><span data-stu-id="04b91-120">For example, the element definition: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`, and query: string `xpath = "/s:Envelope/s:Body/Search";` without the namespace prefix on the `Search` element returns `null` instead of the `Search` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04b91-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="04b91-121">See also</span></span>

- [<span data-ttu-id="04b91-122">Přístup k datům XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="04b91-122">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="04b91-123">Výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="04b91-123">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)

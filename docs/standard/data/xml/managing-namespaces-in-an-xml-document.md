---
title: "Správa oborů názvů v dokumentu XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e9761afe8b56e15edba6e0319cce9a02501a6bb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="managing-namespaces-in-an-xml-document"></a><span data-ttu-id="177d9-102">Správa oborů názvů v dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="177d9-102">Managing Namespaces in an XML Document</span></span>
<span data-ttu-id="177d9-103">Obory názvů XML přidružit předdefinované a vlastní identifikátory URI názvy prvků a atributů v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="177d9-103">XML namespaces associate element and attribute names in an XML document with custom and predefined URIs.</span></span> <span data-ttu-id="177d9-104">Chcete-li vytvořit těchto přidružení, definice předpony oboru názvů identifikátory URI a používání předpon, k vyfiltrování názvy prvků a atributů v datech XML.</span><span class="sxs-lookup"><span data-stu-id="177d9-104">To create these associations, you define prefixes for namespace URIs, and use those prefixes to qualify element and attribute names in XML data.</span></span> <span data-ttu-id="177d9-105">Obory názvů zabránit elementu a atributu kolize názvů a povolte elementů a atributů se stejným názvem, zpracovávají a ověřit jinak.</span><span class="sxs-lookup"><span data-stu-id="177d9-105">Namespaces prevent element and attribute name collisions, and enable elements and attributes of the same name to be handled and validated differently.</span></span>  
  
<a name="declare"></a>   
## <a name="declaring-namespaces"></a><span data-ttu-id="177d9-106">Deklarace oborů názvů</span><span class="sxs-lookup"><span data-stu-id="177d9-106">Declaring namespaces</span></span>  
 <span data-ttu-id="177d9-107">Pro deklaraci oboru názvů na element, můžete použít `xmlns:` atribut:</span><span class="sxs-lookup"><span data-stu-id="177d9-107">To declare a namespace on an element, you use the `xmlns:` attribute:</span></span>  
  
 `xmlns:<name>=<"uri">`  
  
 <span data-ttu-id="177d9-108">kde `<name>` je Předpona oboru názvů a `<"uri">` je identifikátor URI, který identifikuje obor názvů.</span><span class="sxs-lookup"><span data-stu-id="177d9-108">where `<name>` is the namespace prefix and `<"uri">` is the URI that identifies the namespace.</span></span> <span data-ttu-id="177d9-109">Po deklarujete předponu, můžete přidružit identifikátor URI oboru názvů a kvalifikaci elementů a atributů v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="177d9-109">After you declare the prefix, you can use it to qualify elements and attributes in an XML document and associate them with the namespace URI.</span></span> <span data-ttu-id="177d9-110">Protože Předpona oboru názvů se používá v celém dokumentu, mělo by být krátký délku.</span><span class="sxs-lookup"><span data-stu-id="177d9-110">Because the namespace prefix is used throughout a document, it should be short in length.</span></span>  
  
 <span data-ttu-id="177d9-111">Tento příklad definuje dvě `BOOK` elementy.</span><span class="sxs-lookup"><span data-stu-id="177d9-111">This example defines two `BOOK` elements.</span></span> <span data-ttu-id="177d9-112">První elementu je kvalifikovaný předponu, `mybook`, a druhý prvkem je kvalifikovaný předponu, `bb`.</span><span class="sxs-lookup"><span data-stu-id="177d9-112">The first element element is qualified by the prefix, `mybook`, and the second element is qualified by the prefix, `bb`.</span></span> <span data-ttu-id="177d9-113">Každý předpona je spojena s jiný identifikátor URI oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="177d9-113">Each prefix is associated with a different namespace URI:</span></span>  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines">  
```  
  
 <span data-ttu-id="177d9-114">Chcete-li označit, že element je součástí konkrétní obor názvů, přidejte k němu Předpona oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="177d9-114">To signify that an element is a part of a particular namespace, add the namespace prefix to it.</span></span> <span data-ttu-id="177d9-115">Například pokud `Author` níž prvek patří `mybook` obor názvů, je deklarován jako `<mybook:Author>`.</span><span class="sxs-lookup"><span data-stu-id="177d9-115">For example, if a `Author` element belongs to the `mybook` namespace, it is declared as `<mybook:Author>`.</span></span>  
  
<a name="scope"></a>   
## <a name="declaration-scope"></a><span data-ttu-id="177d9-116">Deklarace oboru</span><span class="sxs-lookup"><span data-stu-id="177d9-116">Declaration scope</span></span>  
 <span data-ttu-id="177d9-117">Obor názvů je efektivní z bodu deklarace až do konce element byla deklarována v.</span><span class="sxs-lookup"><span data-stu-id="177d9-117">A namespace is effective from its point of declaration until the end of the element it was declared in.</span></span> <span data-ttu-id="177d9-118">V tomto příkladu obor názvů definované v `BOOK` element se nevztahuje na elementy mimo `BOOK` elementu, jako `Publisher` element:</span><span class="sxs-lookup"><span data-stu-id="177d9-118">In this example, the namespace defined in the `BOOK` element doesn't apply to elements outside the `BOOK` element, such as the `Publisher` element:</span></span>  
  
```xml  
<Author>Joe Smith</Author>  
<BOOK xmlns:book="http://www.contoso.com">  
    <title>My Wonderful Day</title>  
      <price>$3.95</price>  
</BOOK>  
<Publisher>  
    <Name>MSPress</Name>  
</Publisher>  
```  
  
 <span data-ttu-id="177d9-119">Před použitím, ale nemá zobrazí v horní části dokumentu XML, musí být deklarován obor názvů.</span><span class="sxs-lookup"><span data-stu-id="177d9-119">A namespace must be declared before it can be used, but it doesn't have to appear at the top of the XML document.</span></span>  
  
 <span data-ttu-id="177d9-120">Pokud používáte více obory názvů v dokumentu XML, můžete definovat jeden obor názvů jako výchozí obor názvů k vytvoření čisticí vypadající dokument.</span><span class="sxs-lookup"><span data-stu-id="177d9-120">When you use multiple namespaces in an XML document, you can define one namespace as the default namespace to create a cleaner looking document.</span></span> <span data-ttu-id="177d9-121">Výchozí obor názvů je v kořenovém elementu deklarována a platí pro všechny neúplné elementy v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="177d9-121">The default namespace is declared in the root element and applies to all unqualified elements in the document.</span></span> <span data-ttu-id="177d9-122">Výchozí obory názvů budou použity pouze elementy, nikoli atributy.</span><span class="sxs-lookup"><span data-stu-id="177d9-122">Default namespaces apply to elements only, not to attributes.</span></span>  
  
 <span data-ttu-id="177d9-123">Chcete-li použít výchozí obor názvů, vynechejte předponu a dvojtečka z deklarace na element:</span><span class="sxs-lookup"><span data-stu-id="177d9-123">To use the default namespace, omit the prefix and the colon from the declaration on the element:</span></span>  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
```  
  
## <a name="managing-namespaces"></a><span data-ttu-id="177d9-124">Správa oborů názvů</span><span class="sxs-lookup"><span data-stu-id="177d9-124">Managing namespaces</span></span>  
 <span data-ttu-id="177d9-125"><xref:System.Xml.XmlNamespaceManager> Třída ukládá kolekce identifikátorů URI oboru názvů a předpony a umožňuje vyhledávat, přidávat a odebírat obory názvů z této kolekce.</span><span class="sxs-lookup"><span data-stu-id="177d9-125">The <xref:System.Xml.XmlNamespaceManager> class stores a collection of namespace URIs and their prefixes, and lets you look up, add, and remove namespaces from this collection.</span></span> <span data-ttu-id="177d9-126">V některých kontextech Tato třída je vyžadována pro lepší výkon zpracování XML.</span><span class="sxs-lookup"><span data-stu-id="177d9-126">In certain contexts, this class is required for better XML processing performance.</span></span> <span data-ttu-id="177d9-127">Například <xref:System.Xml.Xsl.XsltContext> třídy používá <xref:System.Xml.XmlNamespaceManager> pro podporu jazyka XPath.</span><span class="sxs-lookup"><span data-stu-id="177d9-127">For example, the <xref:System.Xml.Xsl.XsltContext> class uses <xref:System.Xml.XmlNamespaceManager> for XPath support.</span></span>  
  
 <span data-ttu-id="177d9-128">Obor názvů manager nebude provádět žádné ověření na obory názvů, ale předpokládá, že již byla ověřena předpony a obory názvů a v souladu s [obory názvů W3C](http://www.w3.org/TR/REC-xml-names/) specifikace.</span><span class="sxs-lookup"><span data-stu-id="177d9-128">The namespace manager doesn't perform any validation on the namespaces, but assumes that prefixes and namespaces have already been verified and conform to the [W3C Namespaces](http://www.w3.org/TR/REC-xml-names/) specification.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="177d9-129">[Technologie LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) nepoužívá <xref:System.Xml.XmlNamespaceManager> ke správě oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="177d9-129">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) doesn't use <xref:System.Xml.XmlNamespaceManager> to manage namespaces.</span></span> <span data-ttu-id="177d9-130">V tématu [práci s obory názvů XML](http://msdn.microsoft.com/library/e3003209-3234-45be-a832-47feb7927430) v dokumentaci k LINQ informace o správě oborů názvů při použití technologie LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="177d9-130">See [Working with XML Namespaces](http://msdn.microsoft.com/library/e3003209-3234-45be-a832-47feb7927430) in the LINQ documentation for information about managing namespaces when using LINQ to XML.</span></span>  
  
 <span data-ttu-id="177d9-131">Tady jsou některé úlohy správy a vyhledávání můžete provádět pomocí <xref:System.Xml.XmlNamespaceManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="177d9-131">Here are some of the management and lookup tasks you can perform with the <xref:System.Xml.XmlNamespaceManager> class.</span></span> <span data-ttu-id="177d9-132">Další informace a příklady naleznete na následujících odkazech na odkaz na stránku pro každé metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="177d9-132">For more information and examples, follow the links to the reference page for each method or property.</span></span>  
  
|<span data-ttu-id="177d9-133">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="177d9-133">To</span></span>|<span data-ttu-id="177d9-134">Použití</span><span class="sxs-lookup"><span data-stu-id="177d9-134">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="177d9-135">Přidat obor názvů</span><span class="sxs-lookup"><span data-stu-id="177d9-135">Add a namespace</span></span>|<span data-ttu-id="177d9-136"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A>– Metoda</span><span class="sxs-lookup"><span data-stu-id="177d9-136"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> method</span></span>|  
|<span data-ttu-id="177d9-137">Odebrat obor názvů</span><span class="sxs-lookup"><span data-stu-id="177d9-137">Remove a namespace</span></span>|<span data-ttu-id="177d9-138"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A>– Metoda</span><span class="sxs-lookup"><span data-stu-id="177d9-138"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> method</span></span>|  
|<span data-ttu-id="177d9-139">Najít identifikátor URI pro výchozí obor názvů</span><span class="sxs-lookup"><span data-stu-id="177d9-139">Find the URI for the default namespace</span></span>|<span data-ttu-id="177d9-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A>Vlastnost</span><span class="sxs-lookup"><span data-stu-id="177d9-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> property</span></span>|  
|<span data-ttu-id="177d9-141">Najít identifikátor URI pro předponu oboru názvů</span><span class="sxs-lookup"><span data-stu-id="177d9-141">Find the URI for a namespace prefix</span></span>|<span data-ttu-id="177d9-142"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A>– Metoda</span><span class="sxs-lookup"><span data-stu-id="177d9-142"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> method</span></span>|  
|<span data-ttu-id="177d9-143">Najít předponu pro identifikátor URI oboru názvů</span><span class="sxs-lookup"><span data-stu-id="177d9-143">Find the prefix for a namespace URI</span></span>|<span data-ttu-id="177d9-144"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A>– Metoda</span><span class="sxs-lookup"><span data-stu-id="177d9-144"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> method</span></span>|  
|<span data-ttu-id="177d9-145">Získat seznam obory názvů v aktuálním uzlu</span><span class="sxs-lookup"><span data-stu-id="177d9-145">Get a list of namespaces in the current node</span></span>|<span data-ttu-id="177d9-146"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A>– Metoda</span><span class="sxs-lookup"><span data-stu-id="177d9-146"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> method</span></span>|  
|<span data-ttu-id="177d9-147">Obor obor názvů</span><span class="sxs-lookup"><span data-stu-id="177d9-147">Scope a namespace</span></span>|<span data-ttu-id="177d9-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A>a <xref:System.Xml.XmlNamespaceManager.PopScope%2A> metody</span><span class="sxs-lookup"><span data-stu-id="177d9-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> and <xref:System.Xml.XmlNamespaceManager.PopScope%2A> methods</span></span>|  
|<span data-ttu-id="177d9-149">Zkontrolujte, zda je předpona je definována v aktuálním oboru</span><span class="sxs-lookup"><span data-stu-id="177d9-149">Check whether a prefix is defined in the current scope</span></span>|<span data-ttu-id="177d9-150"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A>– Metoda</span><span class="sxs-lookup"><span data-stu-id="177d9-150"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> method</span></span>|  
|<span data-ttu-id="177d9-151">Získejte název tabulku použita k vyhledání předpony a identifikátory URI</span><span class="sxs-lookup"><span data-stu-id="177d9-151">Get the name table used to look up prefixes and URIs</span></span>|<span data-ttu-id="177d9-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A>Vlastnost</span><span class="sxs-lookup"><span data-stu-id="177d9-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> property</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="177d9-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="177d9-153">See Also</span></span>  
 <xref:System.Xml.XmlNamespaceManager>  
 [<span data-ttu-id="177d9-154">XML – dokumenty a Data</span><span class="sxs-lookup"><span data-stu-id="177d9-154">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)

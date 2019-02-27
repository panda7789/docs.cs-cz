---
title: Správa oborů názvů v dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b0ace73d81783852242a52bec006b0ad2edaadd
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836133"
---
# <a name="managing-namespaces-in-an-xml-document"></a><span data-ttu-id="90c20-102">Správa oborů názvů v dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="90c20-102">Managing Namespaces in an XML Document</span></span>
<span data-ttu-id="90c20-103">Obory názvů XML přidružit identifikátory URI předdefinované a vlastní názvy prvků a atributů v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="90c20-103">XML namespaces associate element and attribute names in an XML document with custom and predefined URIs.</span></span> <span data-ttu-id="90c20-104">Tato přidružení vytvoříte definovat předpony pro obor názvů URI a použijte tyto předpony kvalifikovat názvy prvků a atributů v datech XML.</span><span class="sxs-lookup"><span data-stu-id="90c20-104">To create these associations, you define prefixes for namespace URIs, and use those prefixes to qualify element and attribute names in XML data.</span></span> <span data-ttu-id="90c20-105">Obory názvů zabránit kolize názvů prvků a atributů a povolit elementů a atributů se stejným názvem, zpracovat a ověřen jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="90c20-105">Namespaces prevent element and attribute name collisions, and enable elements and attributes of the same name to be handled and validated differently.</span></span>  
  
<a name="declare"></a>   
## <a name="declaring-namespaces"></a><span data-ttu-id="90c20-106">Deklarace oborů názvů</span><span class="sxs-lookup"><span data-stu-id="90c20-106">Declaring namespaces</span></span>  
 <span data-ttu-id="90c20-107">K deklarování oboru názvů pro element, použijete `xmlns:` atribut:</span><span class="sxs-lookup"><span data-stu-id="90c20-107">To declare a namespace on an element, you use the `xmlns:` attribute:</span></span>  
  
 `xmlns:<name>=<"uri">`  
  
 <span data-ttu-id="90c20-108">kde `<name>` je Předpona oboru názvů a `<"uri">` je identifikátor URI pro určení oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="90c20-108">where `<name>` is the namespace prefix and `<"uri">` is the URI that identifies the namespace.</span></span> <span data-ttu-id="90c20-109">Po deklaraci předpona, která vám pomůže ho kvalifikovat prvkům a atributům v dokumentu XML a přidružit je k oboru názvů identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="90c20-109">After you declare the prefix, you can use it to qualify elements and attributes in an XML document and associate them with the namespace URI.</span></span> <span data-ttu-id="90c20-110">Předpona oboru názvů, protože se používají v celém dokumentu by mělo být krátký délku.</span><span class="sxs-lookup"><span data-stu-id="90c20-110">Because the namespace prefix is used throughout a document, it should be short in length.</span></span>  
  
 <span data-ttu-id="90c20-111">Tento příklad definuje dvě `BOOK` elementy.</span><span class="sxs-lookup"><span data-stu-id="90c20-111">This example defines two `BOOK` elements.</span></span> <span data-ttu-id="90c20-112">První prvek je kvalifikována předponu, `mybook`, a druhý prvek je kvalifikována předponu, `bb`.</span><span class="sxs-lookup"><span data-stu-id="90c20-112">The first element is qualified by the prefix, `mybook`, and the second element is qualified by the prefix, `bb`.</span></span> <span data-ttu-id="90c20-113">Každou předponu je přidružen jiný obor názvů identifikátoru URI:</span><span class="sxs-lookup"><span data-stu-id="90c20-113">Each prefix is associated with a different namespace URI:</span></span>  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines">  
```  
  
 <span data-ttu-id="90c20-114">Chcete-li označit, že element je součástí konkrétní obor názvů, přidejte do ní Předpona oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="90c20-114">To signify that an element is a part of a particular namespace, add the namespace prefix to it.</span></span> <span data-ttu-id="90c20-115">Například pokud `Author` element patří do `mybook` obor názvů, je deklarována jako `<mybook:Author>`.</span><span class="sxs-lookup"><span data-stu-id="90c20-115">For example, if a `Author` element belongs to the `mybook` namespace, it is declared as `<mybook:Author>`.</span></span>  
  
<a name="scope"></a>   
## <a name="declaration-scope"></a><span data-ttu-id="90c20-116">Deklarace oboru</span><span class="sxs-lookup"><span data-stu-id="90c20-116">Declaration scope</span></span>  
 <span data-ttu-id="90c20-117">Obor názvů je účinné z místa deklarace až do konce element byl deklarován v.</span><span class="sxs-lookup"><span data-stu-id="90c20-117">A namespace is effective from its point of declaration until the end of the element it was declared in.</span></span> <span data-ttu-id="90c20-118">V tomto příkladu obor názvů definovaný v `BOOK` element neplatí pro prvky mimo `BOOK` elementu, například `Publisher` element:</span><span class="sxs-lookup"><span data-stu-id="90c20-118">In this example, the namespace defined in the `BOOK` element doesn't apply to elements outside the `BOOK` element, such as the `Publisher` element:</span></span>  
  
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
  
 <span data-ttu-id="90c20-119">Obor názvů musí být deklarována, než je možné, ale nemusí se zobrazí v horní části dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="90c20-119">A namespace must be declared before it can be used, but it doesn't have to appear at the top of the XML document.</span></span>  
  
 <span data-ttu-id="90c20-120">Při použití více oborů názvů v dokumentu XML, můžete definovat jeden obor názvů jako výchozí obor názvů a vytvoříte čisticí vypadající textový dokument.</span><span class="sxs-lookup"><span data-stu-id="90c20-120">When you use multiple namespaces in an XML document, you can define one namespace as the default namespace to create a cleaner looking document.</span></span> <span data-ttu-id="90c20-121">Výchozí obor názvů je deklarován v kořenovém prvku a platí pro všechny nekvalifikované elementy v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="90c20-121">The default namespace is declared in the root element and applies to all unqualified elements in the document.</span></span> <span data-ttu-id="90c20-122">Výchozí obory názvů budou použity pouze prvky, nikoli atributů.</span><span class="sxs-lookup"><span data-stu-id="90c20-122">Default namespaces apply to elements only, not to attributes.</span></span>  
  
 <span data-ttu-id="90c20-123">Pokud chcete použít výchozí obor názvů, vynechte předponu a identit od deklarace na element:</span><span class="sxs-lookup"><span data-stu-id="90c20-123">To use the default namespace, omit the prefix and the colon from the declaration on the element:</span></span>  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
```  
  
## <a name="managing-namespaces"></a><span data-ttu-id="90c20-124">Správa oborů názvů</span><span class="sxs-lookup"><span data-stu-id="90c20-124">Managing namespaces</span></span>  
 <span data-ttu-id="90c20-125"><xref:System.Xml.XmlNamespaceManager> Třídy ukládá kolekce identifikátorů URI oboru názvů a jejich předpony a umožňuje vyhledat, přidání a odebrání oborů názvů z této kolekce.</span><span class="sxs-lookup"><span data-stu-id="90c20-125">The <xref:System.Xml.XmlNamespaceManager> class stores a collection of namespace URIs and their prefixes, and lets you look up, add, and remove namespaces from this collection.</span></span> <span data-ttu-id="90c20-126">V některých kontextech Tato třída je povinné pro lepší výkon pro zpracování XML.</span><span class="sxs-lookup"><span data-stu-id="90c20-126">In certain contexts, this class is required for better XML processing performance.</span></span> <span data-ttu-id="90c20-127">Například <xref:System.Xml.Xsl.XsltContext> třídy používá <xref:System.Xml.XmlNamespaceManager> pro podporu jazyka XPath.</span><span class="sxs-lookup"><span data-stu-id="90c20-127">For example, the <xref:System.Xml.Xsl.XsltContext> class uses <xref:System.Xml.XmlNamespaceManager> for XPath support.</span></span>  
  
 <span data-ttu-id="90c20-128">Obor názvů správce neprovede žádné ověření na obory názvů, ale předpokládá, že již byly ověřeny předpony a obory názvů a v souladu s [obory názvů W3C](https://www.w3.org/TR/REC-xml-names/) specifikace.</span><span class="sxs-lookup"><span data-stu-id="90c20-128">The namespace manager doesn't perform any validation on the namespaces, but assumes that prefixes and namespaces have already been verified and conform to the [W3C Namespaces](https://www.w3.org/TR/REC-xml-names/) specification.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90c20-129">[Technologie LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) nepoužívejte <xref:System.Xml.XmlNamespaceManager> ke správě oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="90c20-129">[LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) don't use <xref:System.Xml.XmlNamespaceManager> to manage namespaces.</span></span> <span data-ttu-id="90c20-130">Zobrazit [práce s názvovými prostory XML (C#)](../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md) a [práce s názvovými prostory XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md) v LINQ dokumentaci informace o správě oborů názvů, při použití technologie LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="90c20-130">See [Working with XML Namespaces (C#)](../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md) and [Working with XML Namespaces (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md) in the LINQ documentation for information about managing namespaces when using LINQ to XML.</span></span>  
  
 <span data-ttu-id="90c20-131">Tady jsou některé úlohy správy a vyhledávání můžete provádět pomocí <xref:System.Xml.XmlNamespaceManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="90c20-131">Here are some of the management and lookup tasks you can perform with the <xref:System.Xml.XmlNamespaceManager> class.</span></span> <span data-ttu-id="90c20-132">Další informace a příklady najdete na odkazech na referenční stránce pro každou metodu nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="90c20-132">For more information and examples, follow the links to the reference page for each method or property.</span></span>  
  
|<span data-ttu-id="90c20-133">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="90c20-133">To</span></span>|<span data-ttu-id="90c20-134">Použití</span><span class="sxs-lookup"><span data-stu-id="90c20-134">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="90c20-135">Přidat obor názvů</span><span class="sxs-lookup"><span data-stu-id="90c20-135">Add a namespace</span></span>|<span data-ttu-id="90c20-136"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> – Metoda</span><span class="sxs-lookup"><span data-stu-id="90c20-136"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> method</span></span>|  
|<span data-ttu-id="90c20-137">Odebrat obor názvů</span><span class="sxs-lookup"><span data-stu-id="90c20-137">Remove a namespace</span></span>|<span data-ttu-id="90c20-138"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> – Metoda</span><span class="sxs-lookup"><span data-stu-id="90c20-138"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> method</span></span>|  
|<span data-ttu-id="90c20-139">Najít identifikátor URI pro výchozí obor názvů</span><span class="sxs-lookup"><span data-stu-id="90c20-139">Find the URI for the default namespace</span></span>|<span data-ttu-id="90c20-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> Vlastnost</span><span class="sxs-lookup"><span data-stu-id="90c20-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> property</span></span>|  
|<span data-ttu-id="90c20-141">Najít identifikátor URI pro předponu oboru názvů</span><span class="sxs-lookup"><span data-stu-id="90c20-141">Find the URI for a namespace prefix</span></span>|<span data-ttu-id="90c20-142"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> – Metoda</span><span class="sxs-lookup"><span data-stu-id="90c20-142"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> method</span></span>|  
|<span data-ttu-id="90c20-143">Najít předponu pro obor názvů identifikátoru URI</span><span class="sxs-lookup"><span data-stu-id="90c20-143">Find the prefix for a namespace URI</span></span>|<span data-ttu-id="90c20-144"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> – Metoda</span><span class="sxs-lookup"><span data-stu-id="90c20-144"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> method</span></span>|  
|<span data-ttu-id="90c20-145">Získání seznamu oborů názvů v aktuálním uzlu</span><span class="sxs-lookup"><span data-stu-id="90c20-145">Get a list of namespaces in the current node</span></span>|<span data-ttu-id="90c20-146"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> – Metoda</span><span class="sxs-lookup"><span data-stu-id="90c20-146"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> method</span></span>|  
|<span data-ttu-id="90c20-147">Určení rozsahu oboru názvů</span><span class="sxs-lookup"><span data-stu-id="90c20-147">Scope a namespace</span></span>|<span data-ttu-id="90c20-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> a <xref:System.Xml.XmlNamespaceManager.PopScope%2A> metody</span><span class="sxs-lookup"><span data-stu-id="90c20-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> and <xref:System.Xml.XmlNamespaceManager.PopScope%2A> methods</span></span>|  
|<span data-ttu-id="90c20-149">Zkontrolujte, zda je v aktuálním oboru definovánu předponu</span><span class="sxs-lookup"><span data-stu-id="90c20-149">Check whether a prefix is defined in the current scope</span></span>|<span data-ttu-id="90c20-150"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> – Metoda</span><span class="sxs-lookup"><span data-stu-id="90c20-150"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> method</span></span>|  
|<span data-ttu-id="90c20-151">Získejte název tabulky použitý při vyhledávání předpon a identifikátory URI</span><span class="sxs-lookup"><span data-stu-id="90c20-151">Get the name table used to look up prefixes and URIs</span></span>|<span data-ttu-id="90c20-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> Vlastnost</span><span class="sxs-lookup"><span data-stu-id="90c20-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> property</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="90c20-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90c20-153">See also</span></span>

- <xref:System.Xml.XmlNamespaceManager>
- [<span data-ttu-id="90c20-154">Dokumenty a data XML</span><span class="sxs-lookup"><span data-stu-id="90c20-154">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)

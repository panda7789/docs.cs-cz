---
title: Správa oborů názvů v dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
ms.openlocfilehash: 1b3e57c0a8a37574a92d23cf1d623301cc54b984
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796149"
---
# <a name="managing-namespaces-in-an-xml-document"></a><span data-ttu-id="50159-102">Správa oborů názvů v dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="50159-102">Managing Namespaces in an XML Document</span></span>
<span data-ttu-id="50159-103">Obory názvů XML přiřadí prvky a názvy atributů v dokumentu XML s vlastními a předdefinovanými identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="50159-103">XML namespaces associate element and attribute names in an XML document with custom and predefined URIs.</span></span> <span data-ttu-id="50159-104">Chcete-li vytvořit tato přidružení, definujete předpony pro identifikátor URI oboru názvů a použijete tyto předpony pro kvalifikaci názvů elementů a atributů v datech XML.</span><span class="sxs-lookup"><span data-stu-id="50159-104">To create these associations, you define prefixes for namespace URIs, and use those prefixes to qualify element and attribute names in XML data.</span></span> <span data-ttu-id="50159-105">Obory názvů zabraňují kolizím názvů prvků a atributů a umožňují, aby elementy a atributy stejného názvu byly zpracovány a ověřovány jinak.</span><span class="sxs-lookup"><span data-stu-id="50159-105">Namespaces prevent element and attribute name collisions, and enable elements and attributes of the same name to be handled and validated differently.</span></span>  
  
<a name="declare"></a>
## <a name="declaring-namespaces"></a><span data-ttu-id="50159-106">Deklarace oborů názvů</span><span class="sxs-lookup"><span data-stu-id="50159-106">Declaring namespaces</span></span>  
 <span data-ttu-id="50159-107">Chcete-li deklarovat obor názvů pro element, použijte `xmlns:` atribut:</span><span class="sxs-lookup"><span data-stu-id="50159-107">To declare a namespace on an element, you use the `xmlns:` attribute:</span></span>  
  
 `xmlns:<name>=<"uri">`  
  
 <span data-ttu-id="50159-108">kde `<name>` je předpona oboru názvů `<"uri">` a je identifikátor URI, který identifikuje obor názvů.</span><span class="sxs-lookup"><span data-stu-id="50159-108">where `<name>` is the namespace prefix and `<"uri">` is the URI that identifies the namespace.</span></span> <span data-ttu-id="50159-109">Po deklaraci předpony ji můžete použít k získání prvků a atributů v dokumentu XML a jejich přidružení k identifikátoru URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="50159-109">After you declare the prefix, you can use it to qualify elements and attributes in an XML document and associate them with the namespace URI.</span></span> <span data-ttu-id="50159-110">Vzhledem k tomu, že předpona oboru názvů se používá v celém dokumentu, měla by být krátká délka.</span><span class="sxs-lookup"><span data-stu-id="50159-110">Because the namespace prefix is used throughout a document, it should be short in length.</span></span>  
  
 <span data-ttu-id="50159-111">Tento příklad definuje dva `BOOK` prvky.</span><span class="sxs-lookup"><span data-stu-id="50159-111">This example defines two `BOOK` elements.</span></span> <span data-ttu-id="50159-112">První prvek je kvalifikován předponou `mybook`, a druhý prvek je kvalifikován předponou,. `bb`</span><span class="sxs-lookup"><span data-stu-id="50159-112">The first element is qualified by the prefix, `mybook`, and the second element is qualified by the prefix, `bb`.</span></span> <span data-ttu-id="50159-113">Každá předpona je přidružená k jinému identifikátoru URI oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="50159-113">Each prefix is associated with a different namespace URI:</span></span>  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines" />
</mybook>
```  
  
 <span data-ttu-id="50159-114">Chcete-li označit, že element je součástí konkrétního oboru názvů, přidejte do něj předponu oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="50159-114">To signify that an element is a part of a particular namespace, add the namespace prefix to it.</span></span> <span data-ttu-id="50159-115">Například pokud `Author` prvek patří do `mybook` oboru názvů, je deklarován jako. `<mybook:Author>`</span><span class="sxs-lookup"><span data-stu-id="50159-115">For example, if a `Author` element belongs to the `mybook` namespace, it is declared as `<mybook:Author>`.</span></span>  
  
<a name="scope"></a>
## <a name="declaration-scope"></a><span data-ttu-id="50159-116">Rozsah deklarace</span><span class="sxs-lookup"><span data-stu-id="50159-116">Declaration scope</span></span>  
 <span data-ttu-id="50159-117">Obor názvů je platný od svého bodu deklarace až do konce elementu, ve kterém byl deklarován.</span><span class="sxs-lookup"><span data-stu-id="50159-117">A namespace is effective from its point of declaration until the end of the element it was declared in.</span></span> <span data-ttu-id="50159-118">V tomto příkladu se obor názvů definovaný v `BOOK` elementu nevztahuje na prvky mimo `BOOK` prvek, jako je `Publisher` například element:</span><span class="sxs-lookup"><span data-stu-id="50159-118">In this example, the namespace defined in the `BOOK` element doesn't apply to elements outside the `BOOK` element, such as the `Publisher` element:</span></span>  
  
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
  
 <span data-ttu-id="50159-119">Obor názvů musí být deklarován dříve, než může být použit, ale nemusí být zobrazen v horní části dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="50159-119">A namespace must be declared before it can be used, but it doesn't have to appear at the top of the XML document.</span></span>  
  
 <span data-ttu-id="50159-120">Použijete-li v dokumentu XML více oborů názvů, můžete definovat jeden obor názvů jako výchozí obor názvů pro vytvoření čisticího dokumentu.</span><span class="sxs-lookup"><span data-stu-id="50159-120">When you use multiple namespaces in an XML document, you can define one namespace as the default namespace to create a cleaner looking document.</span></span> <span data-ttu-id="50159-121">Výchozí obor názvů je deklarován v kořenovém elementu a vztahuje se na všechny nekvalifikované prvky v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="50159-121">The default namespace is declared in the root element and applies to all unqualified elements in the document.</span></span> <span data-ttu-id="50159-122">Výchozí obory názvů platí pouze pro prvky, nikoli pro atributy.</span><span class="sxs-lookup"><span data-stu-id="50159-122">Default namespaces apply to elements only, not to attributes.</span></span>  
  
 <span data-ttu-id="50159-123">Chcete-li použít výchozí obor názvů, vynechejte předponu a dvojtečku z deklarace elementu:</span><span class="sxs-lookup"><span data-stu-id="50159-123">To use the default namespace, omit the prefix and the colon from the declaration on the element:</span></span>  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
...
</BOOK>
```  
  
## <a name="managing-namespaces"></a><span data-ttu-id="50159-124">Správa oborů názvů</span><span class="sxs-lookup"><span data-stu-id="50159-124">Managing namespaces</span></span>  
 <span data-ttu-id="50159-125"><xref:System.Xml.XmlNamespaceManager> Třída ukládá kolekci identifikátorů URI oboru názvů a jejich předpon a umožňuje vyhledat, přidat a odebrat obory názvů z této kolekce.</span><span class="sxs-lookup"><span data-stu-id="50159-125">The <xref:System.Xml.XmlNamespaceManager> class stores a collection of namespace URIs and their prefixes, and lets you look up, add, and remove namespaces from this collection.</span></span> <span data-ttu-id="50159-126">V některých kontextech je tato třída potřebná pro lepší výkon zpracování XML.</span><span class="sxs-lookup"><span data-stu-id="50159-126">In certain contexts, this class is required for better XML processing performance.</span></span> <span data-ttu-id="50159-127">Například <xref:System.Xml.Xsl.XsltContext> třída používá <xref:System.Xml.XmlNamespaceManager> pro podporu XPath.</span><span class="sxs-lookup"><span data-stu-id="50159-127">For example, the <xref:System.Xml.Xsl.XsltContext> class uses <xref:System.Xml.XmlNamespaceManager> for XPath support.</span></span>  
  
 <span data-ttu-id="50159-128">Správce oboru názvů neprovádí žádné ověřování u oborů názvů, ale předpokládá, že předpony a obory názvů již byly ověřeny a odpovídají specifikaci [oborů názvů W3C](https://www.w3.org/TR/REC-xml-names/) .</span><span class="sxs-lookup"><span data-stu-id="50159-128">The namespace manager doesn't perform any validation on the namespaces, but assumes that prefixes and namespaces have already been verified and conform to the [W3C Namespaces](https://www.w3.org/TR/REC-xml-names/) specification.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50159-129">Technologie LINQ TO XML v [jazyce C#](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) a [Visual Basic](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) Nepoužívejte <xref:System.Xml.XmlNamespaceManager> ke správě oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="50159-129">LINQ TO XML in [C#](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [Visual Basic](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) don't use <xref:System.Xml.XmlNamespaceManager> to manage namespaces.</span></span> <span data-ttu-id="50159-130">Informace o správě oborů názvů při použití LINQ to XML naleznete v tématu [práce s obory názvů XML (C#)](../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md) a [práce s obory názvů XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md) v dokumentaci LINQ.</span><span class="sxs-lookup"><span data-stu-id="50159-130">See [Working with XML Namespaces (C#)](../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md) and [Working with XML Namespaces (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md) in the LINQ documentation for information about managing namespaces when using LINQ to XML.</span></span>  
  
 <span data-ttu-id="50159-131">Tady jsou některé úlohy správy a vyhledávání, které můžete s <xref:System.Xml.XmlNamespaceManager> třídou provádět.</span><span class="sxs-lookup"><span data-stu-id="50159-131">Here are some of the management and lookup tasks you can perform with the <xref:System.Xml.XmlNamespaceManager> class.</span></span> <span data-ttu-id="50159-132">Další informace a příklady naleznete v odkazech na referenční stránku pro jednotlivé metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="50159-132">For more information and examples, follow the links to the reference page for each method or property.</span></span>  
  
|<span data-ttu-id="50159-133">Akce</span><span class="sxs-lookup"><span data-stu-id="50159-133">To</span></span>|<span data-ttu-id="50159-134">Použití</span><span class="sxs-lookup"><span data-stu-id="50159-134">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="50159-135">Přidat obor názvů</span><span class="sxs-lookup"><span data-stu-id="50159-135">Add a namespace</span></span>|<span data-ttu-id="50159-136">Metoda <xref:System.Xml.XmlNamespaceManager.AddNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="50159-136"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> method</span></span>|  
|<span data-ttu-id="50159-137">Odebrání oboru názvů</span><span class="sxs-lookup"><span data-stu-id="50159-137">Remove a namespace</span></span>|<span data-ttu-id="50159-138">Metoda <xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="50159-138"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> method</span></span>|  
|<span data-ttu-id="50159-139">Najít identifikátor URI pro výchozí obor názvů</span><span class="sxs-lookup"><span data-stu-id="50159-139">Find the URI for the default namespace</span></span>|<span data-ttu-id="50159-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A>majetek</span><span class="sxs-lookup"><span data-stu-id="50159-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> property</span></span>|  
|<span data-ttu-id="50159-141">Najít identifikátor URI pro předponu oboru názvů</span><span class="sxs-lookup"><span data-stu-id="50159-141">Find the URI for a namespace prefix</span></span>|<span data-ttu-id="50159-142">Metoda <xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="50159-142"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> method</span></span>|  
|<span data-ttu-id="50159-143">Vyhledání předpony pro identifikátor URI oboru názvů</span><span class="sxs-lookup"><span data-stu-id="50159-143">Find the prefix for a namespace URI</span></span>|<span data-ttu-id="50159-144">Metoda <xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A></span><span class="sxs-lookup"><span data-stu-id="50159-144"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> method</span></span>|  
|<span data-ttu-id="50159-145">Získá seznam oborů názvů v aktuálním uzlu.</span><span class="sxs-lookup"><span data-stu-id="50159-145">Get a list of namespaces in the current node</span></span>|<span data-ttu-id="50159-146">Metoda <xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A></span><span class="sxs-lookup"><span data-stu-id="50159-146"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> method</span></span>|  
|<span data-ttu-id="50159-147">Obor oboru názvů</span><span class="sxs-lookup"><span data-stu-id="50159-147">Scope a namespace</span></span>|<span data-ttu-id="50159-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A>a <xref:System.Xml.XmlNamespaceManager.PopScope%2A> metody</span><span class="sxs-lookup"><span data-stu-id="50159-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> and <xref:System.Xml.XmlNamespaceManager.PopScope%2A> methods</span></span>|  
|<span data-ttu-id="50159-149">Ověří, jestli je v aktuálním oboru definovaná předpona.</span><span class="sxs-lookup"><span data-stu-id="50159-149">Check whether a prefix is defined in the current scope</span></span>|<span data-ttu-id="50159-150">Metoda <xref:System.Xml.XmlNamespaceManager.HasNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="50159-150"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> method</span></span>|  
|<span data-ttu-id="50159-151">Získat tabulku názvů použitou k vyhledání předpon a identifikátorů URI</span><span class="sxs-lookup"><span data-stu-id="50159-151">Get the name table used to look up prefixes and URIs</span></span>|<span data-ttu-id="50159-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A>majetek</span><span class="sxs-lookup"><span data-stu-id="50159-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> property</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="50159-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="50159-153">See also</span></span>

- <xref:System.Xml.XmlNamespaceManager>
- [<span data-ttu-id="50159-154">Dokumenty a data XML</span><span class="sxs-lookup"><span data-stu-id="50159-154">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)

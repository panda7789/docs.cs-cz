---
title: Odebrat pomocí objektem XPathNavigator nastaveným na Data XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87dc7d83692f081f2c48a34cef8a33564f0e3089
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577030"
---
# <a name="remove-xml-data-using-xpathnavigator"></a><span data-ttu-id="ed81c-102">Odebrat pomocí objektem XPathNavigator nastaveným na Data XML</span><span class="sxs-lookup"><span data-stu-id="ed81c-102">Remove XML Data using XPathNavigator</span></span>
<span data-ttu-id="ed81c-103"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které slouží k odebírání uzlů a hodnoty dokument XML.</span><span class="sxs-lookup"><span data-stu-id="ed81c-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="ed81c-104">Chcete-li používat tyto metody <xref:System.Xml.XPath.XPathNavigator> objekt musí být upravitelné, který je jeho <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> musí být vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="ed81c-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="ed81c-105"><xref:System.Xml.XPath.XPathNavigator> objekty, které můžete upravit dokument XML, které jsou vytvořené pomocí <xref:System.Xml.XmlDocument.CreateNavigator%2A> metodu <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="ed81c-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="ed81c-106"><xref:System.Xml.XPath.XPathNavigator> objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídy jsou jen pro čtení a jakýkoli pokus o úpravu metody použijte <xref:System.Xml.XPath.XPathNavigator> objekt vytvořený <xref:System.Xml.XPath.XPathDocument> objekt výsledkem <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="ed81c-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="ed81c-107">Další informace o vytváření upravitelné <xref:System.Xml.XPath.XPathNavigator> objekty, najdete v části [čtení dat XML pomocí XPathDocument třídou XMLDocument nastavenou na](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="ed81c-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="removing-nodes"></a><span data-ttu-id="ed81c-108">Odebrání uzlů</span><span class="sxs-lookup"><span data-stu-id="ed81c-108">Removing Nodes</span></span>  
 <span data-ttu-id="ed81c-109"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda odebrat uzly ze dokument XML.</span><span class="sxs-lookup"><span data-stu-id="ed81c-109">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to remove nodes from an XML document.</span></span>  
  
### <a name="removing-a-node"></a><span data-ttu-id="ed81c-110">Odebrání uzlu</span><span class="sxs-lookup"><span data-stu-id="ed81c-110">Removing a Node</span></span>  
 <span data-ttu-id="ed81c-111"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda odstranit aktuální uzel <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěný na z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ed81c-111">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to delete the current node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on from an XML document.</span></span>  
  
 <span data-ttu-id="ed81c-112">Poté, co uzel byl odstraněn pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda, již není dostupný z kořenové složky <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="ed81c-112">After a node has been deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method, it is no longer reachable from the root of the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="ed81c-113">Po odstranění uzlu, <xref:System.Xml.XPath.XPathNavigator> je umístěn na nadřazený uzel odstraněné uzlu.</span><span class="sxs-lookup"><span data-stu-id="ed81c-113">After a node has been deleted, the <xref:System.Xml.XPath.XPathNavigator> is positioned on the parent node of the deleted node.</span></span>  
  
 <span data-ttu-id="ed81c-114">Operace odstranění nemá vliv na polohu všech <xref:System.Xml.XPath.XPathNavigator> umístěný na uzlu odstraněného objektu.</span><span class="sxs-lookup"><span data-stu-id="ed81c-114">A delete operation doesn't affect the position of any <xref:System.Xml.XPath.XPathNavigator> object positioned on the deleted node.</span></span> <span data-ttu-id="ed81c-115">Tyto <xref:System.Xml.XPath.XPathNavigator> objekty jsou platné v tom smyslu, že můžete přesunout v rámci odstraněné podstrom, ale nelze přesunout do hlavní uzel stromu pomocí uzlu regulární nastavit metody navigace <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="ed81c-115">These <xref:System.Xml.XPath.XPathNavigator> objects are valid in the sense that they can move within the deleted subtree, but cannot be moved to the main node tree using the regular node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed81c-116"><xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> Metodu <xref:System.Xml.XPath.XPathNavigator> třídu lze použít k přesunutí těchto <xref:System.Xml.XPath.XPathNavigator> objekty zpět do hlavní uzel stromu, nebo je z hlavní uzel stromu do odstraněného podstrom.</span><span class="sxs-lookup"><span data-stu-id="ed81c-116">The <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class can be used to move these <xref:System.Xml.XPath.XPathNavigator> objects back into the main node tree, or from the main node tree to the deleted subtree.</span></span>  
  
 <span data-ttu-id="ed81c-117">V následujícím příkladu `price` element první `book` element `contosoBooks.xml` soubor se odstraní pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ed81c-117">In the following example, the `price` element of the first `book` element of the `contosoBooks.xml` file is deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span> <span data-ttu-id="ed81c-118">Pozice <xref:System.Xml.XPath.XPathNavigator> objektu po `price` odstraněn prvek je v nadřazené `book` elementu.</span><span class="sxs-lookup"><span data-stu-id="ed81c-118">The position of the <xref:System.Xml.XPath.XPathNavigator> object after the `price` element is deleted is on the parent `book` element.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.DeleteSelf()  
  
Console.WriteLine("Position after delete: {0}", navigator.Name)  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.DeleteSelf();  
  
Console.WriteLine("Position after delete: {0}", navigator.Name);  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="ed81c-119">V příkladu trvá `contosoBooks.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="ed81c-119">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a><span data-ttu-id="ed81c-120">Odebrání uzlu atributu.</span><span class="sxs-lookup"><span data-stu-id="ed81c-120">Removing an Attribute Node</span></span>  
 <span data-ttu-id="ed81c-121">Atribut uzly jsou odebrat z dokumentu XML pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ed81c-121">Attribute nodes are removed from an XML document using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span>  
  
 <span data-ttu-id="ed81c-122">Po odstranění do atribut uzlu, již není dostupný z kořenový uzel <xref:System.Xml.XmlDocument> objektu a <xref:System.Xml.XPath.XPathNavigator> objekt je umístěn na nadřazený element.</span><span class="sxs-lookup"><span data-stu-id="ed81c-122">After an attribute node has been deleted, it is no longer reachable from the root node of an <xref:System.Xml.XmlDocument> object and the <xref:System.Xml.XPath.XPathNavigator> object is positioned on the parent element.</span></span>  
  
#### <a name="default-attributes"></a><span data-ttu-id="ed81c-123">Výchozí atributy</span><span class="sxs-lookup"><span data-stu-id="ed81c-123">Default Attributes</span></span>  
 <span data-ttu-id="ed81c-124">Bez ohledu na to, v případě metody slouží k odebírání atributy jsou speciální omezení odebrání atributů, které jsou definovány jako výchozí atributy v souboru DTD protokolu nebo schématu XML pro dokument XML.</span><span class="sxs-lookup"><span data-stu-id="ed81c-124">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the DTD or XML Schema for the XML document.</span></span> <span data-ttu-id="ed81c-125">Výchozí atributy nelze odebrat, pokud mají být odebrán také na element, který náleží do.</span><span class="sxs-lookup"><span data-stu-id="ed81c-125">Default attributes cannot be removed unless the element they belong to is also removed.</span></span> <span data-ttu-id="ed81c-126">Výchozí atributy jsou vždy k dispozici pro prvky, které mají výchozí atributy deklarovat a v důsledku toho odstranění výsledků výchozí atribut ve nahrazení atributu vkládání do elementu a inicializovat na výchozí hodnotu, která byla definována.</span><span class="sxs-lookup"><span data-stu-id="ed81c-126">Default attributes are always present for elements that have default attributes declared, and as a result, deleting a default attribute results in a replacement attribute being inserted into the element and initialized to the default value that was declared.</span></span>  
  
## <a name="removing-values"></a><span data-ttu-id="ed81c-127">Odebírání hodnot</span><span class="sxs-lookup"><span data-stu-id="ed81c-127">Removing Values</span></span>  
 <span data-ttu-id="ed81c-128"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody odebrat netypová a zadali hodnoty z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ed81c-128">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to remove untyped and typed values from an XML document.</span></span>  
  
### <a name="removing-untyped-values"></a><span data-ttu-id="ed81c-129">Odebrání Netypové hodnoty</span><span class="sxs-lookup"><span data-stu-id="ed81c-129">Removing Untyped Values</span></span>  
 <span data-ttu-id="ed81c-130"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda jednoduše vloží netypové `string` hodnota předaná jako parametr jako hodnotu uzlu <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na.</span><span class="sxs-lookup"><span data-stu-id="ed81c-130">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="ed81c-131">Předávání prázdného řetězce <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metoda odebere hodnotu, aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="ed81c-131">Passing an empty string to the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method removes the value of the current node.</span></span>  
  
 <span data-ttu-id="ed81c-132">Následující příklad odebere hodnotu `price` element první `book` element v `contosoBooks.xml` souboru pomocí <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ed81c-132">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetValue("")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetValue("");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="ed81c-133">V příkladu trvá `contosoBooks.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="ed81c-133">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a><span data-ttu-id="ed81c-134">Odebrání zadávaných hodnot</span><span class="sxs-lookup"><span data-stu-id="ed81c-134">Removing Typed Values</span></span>  
 <span data-ttu-id="ed81c-135">Pokud je typ uzlu schématu XML W3C jednoduchý typ, nová hodnota vložená <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metoda bude zkontrolován omezující vlastnosti pro jednoduchý typ. předtím, než je hodnota nastavená.</span><span class="sxs-lookup"><span data-stu-id="ed81c-135">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="ed81c-136">Pokud nová hodnota není platná podle typu uzlu (například nastavení hodnotu `-1` u elementu, jehož typ je `xs:positiveInteger`), výsledkem výjimka.</span><span class="sxs-lookup"><span data-stu-id="ed81c-136">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span> <span data-ttu-id="ed81c-137"><xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> Metoda také nelze předat `null` jako parametr.</span><span class="sxs-lookup"><span data-stu-id="ed81c-137">The <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method also cannot be passed `null` as a parameter.</span></span> <span data-ttu-id="ed81c-138">V důsledku odebrání hodnoty typu uzlu musí odpovídat typ schématu uzlu.</span><span class="sxs-lookup"><span data-stu-id="ed81c-138">As a result removing the value of a typed node must comply with the schema type of the node.</span></span>  
  
 <span data-ttu-id="ed81c-139">Následující příklad odebere hodnotu `price` element první `book` element v `contosoBooks.xml` souboru pomocí <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metoda podle nastavení na hodnotu `0`.</span><span class="sxs-lookup"><span data-stu-id="ed81c-139">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method by setting the value to `0`.</span></span> <span data-ttu-id="ed81c-140">Hodnota uzlu není odebrána, ale byla odebrána cenu knihy podle jeho datového typu z `xs:decimal`.</span><span class="sxs-lookup"><span data-stu-id="ed81c-140">The value of the node is not removed, but the price of the book has been removed according to its data type of `xs:decimal`.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(0)  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(0);  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
## <a name="namespace-nodes"></a><span data-ttu-id="ed81c-141">Namespace uzly</span><span class="sxs-lookup"><span data-stu-id="ed81c-141">Namespace Nodes</span></span>  
 <span data-ttu-id="ed81c-142">Namespace uzly nelze odstranit ze <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="ed81c-142">Namespace nodes cannot be deleted from an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="ed81c-143">Pokusí se odstranit uzly oboru názvů pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody za následek výjimku.</span><span class="sxs-lookup"><span data-stu-id="ed81c-143">Attempts to delete namespace nodes using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method results in an exception.</span></span>  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="ed81c-144">InnerXml a OuterXml vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ed81c-144">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="ed81c-145"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třída změnit kód XML uzlů <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na.</span><span class="sxs-lookup"><span data-stu-id="ed81c-145">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="ed81c-146"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Změny vlastností kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěný na s Analyzovaná obsah daného XML `string`.</span><span class="sxs-lookup"><span data-stu-id="ed81c-146">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="ed81c-147">Podobně <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> změny vlastností kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěný na i aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="ed81c-147">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="ed81c-148">Kromě metod popsaných v tomto tématu <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti lze použít k odebrání uzlů a hodnoty ze dokument XML.</span><span class="sxs-lookup"><span data-stu-id="ed81c-148">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="ed81c-149">Další informace o používání <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> najdete v části vlastnosti, jimiž upravíte uzly, [upravit Data XML pomocí objektem XPathNavigator nastaveným](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="ed81c-149">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to modify nodes, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="ed81c-150">Uložení dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="ed81c-150">Saving an XML Document</span></span>  
 <span data-ttu-id="ed81c-151">Ukládají se změny provedené v <xref:System.Xml.XmlDocument> objektu jako výsledek metody popsané v tomto tématu se provádí pomocí metody <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="ed81c-151">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="ed81c-152">Další informace o ukládání změny <xref:System.Xml.XmlDocument> objektu, najdete v části [ukládání a zápis dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="ed81c-152">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed81c-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed81c-153">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="ed81c-154">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="ed81c-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="ed81c-155">Vložení dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ed81c-155">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="ed81c-156">Změna dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ed81c-156">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)

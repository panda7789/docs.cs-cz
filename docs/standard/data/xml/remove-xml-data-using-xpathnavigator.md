---
title: Odebrání dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1827e40256bc4307006ce081cbb6cbc44a89a0bc
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44267060"
---
# <a name="remove-xml-data-using-xpathnavigator"></a><span data-ttu-id="f1858-102">Odebrání dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f1858-102">Remove XML Data using XPathNavigator</span></span>
<span data-ttu-id="f1858-103"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které slouží k odebrání uzlů a hodnot z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f1858-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="f1858-104">Chcete-li používat tyto metody <xref:System.Xml.XPath.XPathNavigator> objekt musí být upravitelné, to znamená, jeho <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> musí být vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="f1858-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="f1858-105"><xref:System.Xml.XPath.XPathNavigator> objekty, které můžete upravit dokument XML jsou vytvářeny <xref:System.Xml.XmlDocument.CreateNavigator%2A> metodu <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="f1858-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="f1858-106"><xref:System.Xml.XPath.XPathNavigator> objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídy jsou jen pro čtení a žádný pokus o použití metod pro posunutí úprav <xref:System.Xml.XPath.XPathNavigator> objekt vytvořený pomocí <xref:System.Xml.XPath.XPathDocument> výsledkem objektu <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="f1858-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="f1858-107">Další informace o vytváření upravitelné <xref:System.Xml.XPath.XPathNavigator> objekty, najdete [čtení dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="f1858-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="removing-nodes"></a><span data-ttu-id="f1858-108">Odebrání uzlů</span><span class="sxs-lookup"><span data-stu-id="f1858-108">Removing Nodes</span></span>  
 <span data-ttu-id="f1858-109"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda odebrání uzlů z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f1858-109">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to remove nodes from an XML document.</span></span>  
  
### <a name="removing-a-node"></a><span data-ttu-id="f1858-110">Odebrání uzlu</span><span class="sxs-lookup"><span data-stu-id="f1858-110">Removing a Node</span></span>  
 <span data-ttu-id="f1858-111"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda odstranit aktuální uzel <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f1858-111">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to delete the current node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on from an XML document.</span></span>  
  
 <span data-ttu-id="f1858-112">Poté, co uzel byl odstraněn pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda, už nejsou dostupné z kořenového adresáře <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="f1858-112">After a node has been deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method, it is no longer reachable from the root of the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="f1858-113">Po odstranění uzlu <xref:System.Xml.XPath.XPathNavigator> je umístěn na nadřazený uzel z odstraněného uzlu.</span><span class="sxs-lookup"><span data-stu-id="f1858-113">After a node has been deleted, the <xref:System.Xml.XPath.XPathNavigator> is positioned on the parent node of the deleted node.</span></span>  
  
 <span data-ttu-id="f1858-114">Operace odstranění nemá vliv na pozici žádné <xref:System.Xml.XPath.XPathNavigator> objektu umístěn na odstraněného uzlu.</span><span class="sxs-lookup"><span data-stu-id="f1858-114">A delete operation doesn't affect the position of any <xref:System.Xml.XPath.XPathNavigator> object positioned on the deleted node.</span></span> <span data-ttu-id="f1858-115">Tyto <xref:System.Xml.XPath.XPathNavigator> objekty jsou platné v tom smyslu, že můžete přesouvat v rámci podstrom odstranila, ale nelze přesunout do hlavního uzlu stromové struktury pomocí regulárních uzel nastavení metody navigace <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="f1858-115">These <xref:System.Xml.XPath.XPathNavigator> objects are valid in the sense that they can move within the deleted subtree, but cannot be moved to the main node tree using the regular node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1858-116"><xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> Metodu <xref:System.Xml.XPath.XPathNavigator> třídy lze použít k přesunutí těchto <xref:System.Xml.XPath.XPathNavigator> objektů zpět do hlavního uzlu stromu, nebo je z hlavního uzlu stromu odstraněné podstrom.</span><span class="sxs-lookup"><span data-stu-id="f1858-116">The <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class can be used to move these <xref:System.Xml.XPath.XPathNavigator> objects back into the main node tree, or from the main node tree to the deleted subtree.</span></span>  
  
 <span data-ttu-id="f1858-117">V následujícím příkladu `price` prvek první `book` elementu `contosoBooks.xml` soubor se odstraní pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="f1858-117">In the following example, the `price` element of the first `book` element of the `contosoBooks.xml` file is deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span> <span data-ttu-id="f1858-118">Pozice <xref:System.Xml.XPath.XPathNavigator> objektu po `price` odstranit prvek je v nadřazené `book` elementu.</span><span class="sxs-lookup"><span data-stu-id="f1858-118">The position of the <xref:System.Xml.XPath.XPathNavigator> object after the `price` element is deleted is on the parent `book` element.</span></span>  
  
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
  
 <span data-ttu-id="f1858-119">V příkladu přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="f1858-119">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a><span data-ttu-id="f1858-120">Odebrání uzlu atributu</span><span class="sxs-lookup"><span data-stu-id="f1858-120">Removing an Attribute Node</span></span>  
 <span data-ttu-id="f1858-121">Odeberou se z dokumentu XML pomocí uzlů atributů <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f1858-121">Attribute nodes are removed from an XML document using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span>  
  
 <span data-ttu-id="f1858-122">Po odstranění uzlu atributu, již není dosažitelný z kořenového uzlu <xref:System.Xml.XmlDocument> objektu a <xref:System.Xml.XPath.XPathNavigator> objekt je umístěn na nadřazený element.</span><span class="sxs-lookup"><span data-stu-id="f1858-122">After an attribute node has been deleted, it is no longer reachable from the root node of an <xref:System.Xml.XmlDocument> object and the <xref:System.Xml.XPath.XPathNavigator> object is positioned on the parent element.</span></span>  
  
#### <a name="default-attributes"></a><span data-ttu-id="f1858-123">Výchozí atributy</span><span class="sxs-lookup"><span data-stu-id="f1858-123">Default Attributes</span></span>  
 <span data-ttu-id="f1858-124">Bez ohledu na použitou k odebrání atributů metodu jsou zvláštní omezení týkající se odebrání atributů, které jsou definovány jako výchozí atributy v souboru DTD nebo schématu XML pro dokument XML.</span><span class="sxs-lookup"><span data-stu-id="f1858-124">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the DTD or XML Schema for the XML document.</span></span> <span data-ttu-id="f1858-125">Výchozí atributy nelze odebrat, pokud je odebrána také elementu, do kterých patří.</span><span class="sxs-lookup"><span data-stu-id="f1858-125">Default attributes cannot be removed unless the element they belong to is also removed.</span></span> <span data-ttu-id="f1858-126">Výchozí atributy jsou vždy k dispozici pro prvky, které mají výchozí atributy deklarovány a proto odstranění výchozí atribut výsledky v nahrazení atributu do elementu a inicializovat na výchozí hodnotu, která byla deklarována.</span><span class="sxs-lookup"><span data-stu-id="f1858-126">Default attributes are always present for elements that have default attributes declared, and as a result, deleting a default attribute results in a replacement attribute being inserted into the element and initialized to the default value that was declared.</span></span>  
  
## <a name="removing-values"></a><span data-ttu-id="f1858-127">Odebrání hodnoty</span><span class="sxs-lookup"><span data-stu-id="f1858-127">Removing Values</span></span>  
 <span data-ttu-id="f1858-128"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody odebrat netypová a zadané hodnoty z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f1858-128">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to remove untyped and typed values from an XML document.</span></span>  
  
### <a name="removing-untyped-values"></a><span data-ttu-id="f1858-129">Odebrání Netypové hodnoty</span><span class="sxs-lookup"><span data-stu-id="f1858-129">Removing Untyped Values</span></span>  
 <span data-ttu-id="f1858-130"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda jednoduše vloží netypové `string` předanou jako parametr jako hodnotu uzlu <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na.</span><span class="sxs-lookup"><span data-stu-id="f1858-130">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="f1858-131">Prázdný řetězec k předání <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metoda odebere hodnotu pro aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="f1858-131">Passing an empty string to the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method removes the value of the current node.</span></span>  
  
 <span data-ttu-id="f1858-132">Následující příklad odebere hodnotu `price` prvek první `book` element v `contosoBooks.xml` soubor pomocí <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f1858-132">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="f1858-133">V příkladu přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="f1858-133">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a><span data-ttu-id="f1858-134">Odebrání zadaných hodnot</span><span class="sxs-lookup"><span data-stu-id="f1858-134">Removing Typed Values</span></span>  
 <span data-ttu-id="f1858-135">Pokud je typ uzlu W3C XML schématu jednoduché zadejte, nová hodnota vkládat stisknutím <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metoda je porovnávána s omezující vlastnosti pro jednoduchý typ. předtím, než je hodnota nastavena.</span><span class="sxs-lookup"><span data-stu-id="f1858-135">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="f1858-136">Pokud je nová hodnota není platná pro typ uzlu (například nastavíte hodnotu `-1` na element, jehož typ je `xs:positiveInteger`), je výsledkem výjimky.</span><span class="sxs-lookup"><span data-stu-id="f1858-136">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span> <span data-ttu-id="f1858-137"><xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> Metody nelze předat také `null` jako parametr.</span><span class="sxs-lookup"><span data-stu-id="f1858-137">The <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method also cannot be passed `null` as a parameter.</span></span> <span data-ttu-id="f1858-138">V důsledku odstranění hodnotu typu uzlu musí být v souladu s typem schématu uzlu.</span><span class="sxs-lookup"><span data-stu-id="f1858-138">As a result removing the value of a typed node must comply with the schema type of the node.</span></span>  
  
 <span data-ttu-id="f1858-139">Následující příklad odebere hodnotu `price` prvek první `book` element v `contosoBooks.xml` soubor pomocí <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metoda nastavením hodnoty `0`.</span><span class="sxs-lookup"><span data-stu-id="f1858-139">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method by setting the value to `0`.</span></span> <span data-ttu-id="f1858-140">Hodnota uzlu se neodebere, ale podle jeho datového typu byla odebrána cena knihu `xs:decimal`.</span><span class="sxs-lookup"><span data-stu-id="f1858-140">The value of the node is not removed, but the price of the book has been removed according to its data type of `xs:decimal`.</span></span>  
  
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
  
## <a name="namespace-nodes"></a><span data-ttu-id="f1858-141">Namespace uzly</span><span class="sxs-lookup"><span data-stu-id="f1858-141">Namespace Nodes</span></span>  
 <span data-ttu-id="f1858-142">Namespace uzly nelze odstranit ze <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="f1858-142">Namespace nodes cannot be deleted from an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="f1858-143">Pokusí se odstranit obor názvů uzlů pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metodu vede k výjimce.</span><span class="sxs-lookup"><span data-stu-id="f1858-143">Attempts to delete namespace nodes using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method results in an exception.</span></span>  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="f1858-144">InnerXml a OuterXml vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f1858-144">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="f1858-145"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy změnit kód XML uzlů <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na.</span><span class="sxs-lookup"><span data-stu-id="f1858-145">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="f1858-146"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Vlastnost se změní kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na s analyzovaný obsah XML daného `string`.</span><span class="sxs-lookup"><span data-stu-id="f1858-146">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="f1858-147">Podobně <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnost se změní kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na i samotný uzel aktuální.</span><span class="sxs-lookup"><span data-stu-id="f1858-147">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="f1858-148">Kromě metod popsaných v tomto tématu <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti můžete použít k odebrání uzlů a hodnot z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f1858-148">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="f1858-149">Další informace o používání <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti, které chcete upravit uzly, najdete v článku [upravit dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="f1858-149">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to modify nodes, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="f1858-150">Uložení dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="f1858-150">Saving an XML Document</span></span>  
 <span data-ttu-id="f1858-151">Ukládají se změny provedené <xref:System.Xml.XmlDocument> objekt výsledku z metod popsaných v tomto tématu se provádí pomocí metody <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="f1858-151">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="f1858-152">Další informace o uložení změny <xref:System.Xml.XmlDocument> objektu, najdete v článku [ukládání a zápis dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="f1858-152">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1858-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1858-153">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="f1858-154">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="f1858-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="f1858-155">Vložení dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f1858-155">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="f1858-156">Změna dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f1858-156">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)

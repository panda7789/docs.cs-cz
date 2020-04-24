---
title: Odebrání dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
ms.openlocfilehash: 062a98a9cc10e6be00f165cf617de2d92d65acbf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710359"
---
# <a name="remove-xml-data-using-xpathnavigator"></a><span data-ttu-id="28d72-102">Odebrání dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="28d72-102">Remove XML Data using XPathNavigator</span></span>
<span data-ttu-id="28d72-103"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které slouží k odebrání uzlů a hodnot z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="28d72-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="28d72-104">Aby bylo možné tyto metody použít, musí <xref:System.Xml.XPath.XPathNavigator> být objekt upravitelný, to znamená, že <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> jeho vlastnost musí `true`být.</span><span class="sxs-lookup"><span data-stu-id="28d72-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="28d72-105"><xref:System.Xml.XPath.XPathNavigator>objekty, které mohou upravovat dokument XML, jsou vytvořeny <xref:System.Xml.XmlDocument.CreateNavigator%2A> metodou <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="28d72-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="28d72-106"><xref:System.Xml.XPath.XPathNavigator>objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídou jsou jen pro čtení a všechny pokusy o použití metod úprav <xref:System.Xml.XPath.XPathNavigator> objektu vytvořeného <xref:System.Xml.XPath.XPathDocument> objektem mají za následek. <xref:System.NotSupportedException></span><span class="sxs-lookup"><span data-stu-id="28d72-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="28d72-107">Další informace o vytváření upravitelných <xref:System.Xml.XPath.XPathNavigator> objektů najdete v tématu [čtení dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="28d72-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="removing-nodes"></a><span data-ttu-id="28d72-108">Odebírání uzlů</span><span class="sxs-lookup"><span data-stu-id="28d72-108">Removing Nodes</span></span>  
 <span data-ttu-id="28d72-109"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metodu pro odebrání uzlů z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="28d72-109">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to remove nodes from an XML document.</span></span>  
  
### <a name="removing-a-node"></a><span data-ttu-id="28d72-110">Odebrání uzlu</span><span class="sxs-lookup"><span data-stu-id="28d72-110">Removing a Node</span></span>  
 <span data-ttu-id="28d72-111"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metodu pro odstranění aktuálního uzlu, na kterém je <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěný z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="28d72-111">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to delete the current node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on from an XML document.</span></span>  
  
 <span data-ttu-id="28d72-112">Poté, co byl uzel odstraněn pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody, již není dosažitelný z kořenu <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="28d72-112">After a node has been deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method, it is no longer reachable from the root of the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="28d72-113">Po odstranění uzlu <xref:System.Xml.XPath.XPathNavigator> je umístěn v nadřazeném uzlu odstraněného uzlu.</span><span class="sxs-lookup"><span data-stu-id="28d72-113">After a node has been deleted, the <xref:System.Xml.XPath.XPathNavigator> is positioned on the parent node of the deleted node.</span></span>  
  
 <span data-ttu-id="28d72-114">Operace odstranění nemá vliv na pozici žádného <xref:System.Xml.XPath.XPathNavigator> objektu umístěného na odstraněném uzlu.</span><span class="sxs-lookup"><span data-stu-id="28d72-114">A delete operation doesn't affect the position of any <xref:System.Xml.XPath.XPathNavigator> object positioned on the deleted node.</span></span> <span data-ttu-id="28d72-115">Tyto <xref:System.Xml.XPath.XPathNavigator> objekty jsou platné v tom smyslu, že mohou být přesunuty v odstraněném podstromu, ale nelze je přesunout do hlavního stromu uzlu pomocí regulárních metod navigace pro <xref:System.Xml.XPath.XPathNavigator> třídu.</span><span class="sxs-lookup"><span data-stu-id="28d72-115">These <xref:System.Xml.XPath.XPathNavigator> objects are valid in the sense that they can move within the deleted subtree, but cannot be moved to the main node tree using the regular node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28d72-116">Metodu třídy lze použít k přesunutí těchto <xref:System.Xml.XPath.XPathNavigator> objektů zpět do hlavního stromu uzlu nebo z hlavního stromu uzlu do odstraněného podstromu. <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A></span><span class="sxs-lookup"><span data-stu-id="28d72-116">The <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class can be used to move these <xref:System.Xml.XPath.XPathNavigator> objects back into the main node tree, or from the main node tree to the deleted subtree.</span></span>  
  
 <span data-ttu-id="28d72-117">V následujícím `price` příkladu je prvek prvního `book` prvku `contosoBooks.xml` souboru odstraněn pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="28d72-117">In the following example, the `price` element of the first `book` element of the `contosoBooks.xml` file is deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span> <span data-ttu-id="28d72-118">Pozice <xref:System.Xml.XPath.XPathNavigator> objektu po odstranění `price` elementu je v nadřazeném `book` elementu.</span><span class="sxs-lookup"><span data-stu-id="28d72-118">The position of the <xref:System.Xml.XPath.XPathNavigator> object after the `price` element is deleted is on the parent `book` element.</span></span>  
  
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
  
 <span data-ttu-id="28d72-119">Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="28d72-119">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a><span data-ttu-id="28d72-120">Odebrání uzlu atributu</span><span class="sxs-lookup"><span data-stu-id="28d72-120">Removing an Attribute Node</span></span>  
 <span data-ttu-id="28d72-121">Uzly atributů jsou odebrány z dokumentu XML pomocí <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="28d72-121">Attribute nodes are removed from an XML document using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span>  
  
 <span data-ttu-id="28d72-122">Po odstranění uzlu atributu již není dosažitelný z kořenového uzlu <xref:System.Xml.XmlDocument> objektu a <xref:System.Xml.XPath.XPathNavigator> objekt je umístěn v nadřazeném elementu.</span><span class="sxs-lookup"><span data-stu-id="28d72-122">After an attribute node has been deleted, it is no longer reachable from the root node of an <xref:System.Xml.XmlDocument> object and the <xref:System.Xml.XPath.XPathNavigator> object is positioned on the parent element.</span></span>  
  
#### <a name="default-attributes"></a><span data-ttu-id="28d72-123">Výchozí atributy</span><span class="sxs-lookup"><span data-stu-id="28d72-123">Default Attributes</span></span>  
 <span data-ttu-id="28d72-124">Bez ohledu na metodu použitou k odebrání atributů existují zvláštní omezení na odebrání atributů, které jsou definovány jako výchozí atributy ve schématu DTD nebo XML pro dokument XML.</span><span class="sxs-lookup"><span data-stu-id="28d72-124">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the DTD or XML Schema for the XML document.</span></span> <span data-ttu-id="28d72-125">Výchozí atributy nelze odebrat, pokud je odebrán také element, ke kterému patří.</span><span class="sxs-lookup"><span data-stu-id="28d72-125">Default attributes cannot be removed unless the element they belong to is also removed.</span></span> <span data-ttu-id="28d72-126">Výchozí atributy jsou vždy přítomny pro prvky, které mají deklarované výchozí atributy, a v důsledku toho odstranění výchozího atributu má za následek vložení nahrazujícího atributu do elementu a inicializovaného na výchozí hodnotu, která byla deklarována.</span><span class="sxs-lookup"><span data-stu-id="28d72-126">Default attributes are always present for elements that have default attributes declared, and as a result, deleting a default attribute results in a replacement attribute being inserted into the element and initialized to the default value that was declared.</span></span>  
  
## <a name="removing-values"></a><span data-ttu-id="28d72-127">Odebírají se hodnoty.</span><span class="sxs-lookup"><span data-stu-id="28d72-127">Removing Values</span></span>  
 <span data-ttu-id="28d72-128"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje metody <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> k odebrání netypových a typových hodnot z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="28d72-128">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to remove untyped and typed values from an XML document.</span></span>  
  
### <a name="removing-untyped-values"></a><span data-ttu-id="28d72-129">Odebrání netypových hodnot</span><span class="sxs-lookup"><span data-stu-id="28d72-129">Removing Untyped Values</span></span>  
 <span data-ttu-id="28d72-130"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda jednoduše vloží netypové `string` hodnoty předané jako parametr jako hodnotu uzlu, na kterém <xref:System.Xml.XPath.XPathNavigator> je objekt aktuálně umístěn.</span><span class="sxs-lookup"><span data-stu-id="28d72-130">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="28d72-131">Předáním prázdného řetězce <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metodě dojde k odebrání hodnoty aktuálního uzlu.</span><span class="sxs-lookup"><span data-stu-id="28d72-131">Passing an empty string to the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method removes the value of the current node.</span></span>  
  
 <span data-ttu-id="28d72-132">Následující příklad `price` odebere hodnotu prvku prvního `book` prvku v `contosoBooks.xml` souboru pomocí <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="28d72-132">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="28d72-133">Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="28d72-133">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a><span data-ttu-id="28d72-134">Odebírají se typové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="28d72-134">Removing Typed Values</span></span>  
 <span data-ttu-id="28d72-135">Pokud je typ uzlu jednoduchý typ schématu W3C XML, je nová hodnota vložená <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodou zkontrolována proti omezující vlastnosti jednoduchého typu před nastavením hodnoty.</span><span class="sxs-lookup"><span data-stu-id="28d72-135">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="28d72-136">Pokud nová hodnota není platná podle typu uzlu (například nastavení hodnoty `-1` na elementu, jehož typ je `xs:positiveInteger`), výsledkem je výjimka.</span><span class="sxs-lookup"><span data-stu-id="28d72-136">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span> <span data-ttu-id="28d72-137"><xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> Metodu nelze předat `null` také jako parametr.</span><span class="sxs-lookup"><span data-stu-id="28d72-137">The <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method also cannot be passed `null` as a parameter.</span></span> <span data-ttu-id="28d72-138">Výsledkem odebrání hodnoty typového uzlu musí odpovídat typu schématu uzlu.</span><span class="sxs-lookup"><span data-stu-id="28d72-138">As a result removing the value of a typed node must comply with the schema type of the node.</span></span>  
  
 <span data-ttu-id="28d72-139">Následující `price` příklad odebere hodnotu prvku prvního `book` prvku v `contosoBooks.xml` souboru pomocí <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody nastavením hodnoty na. `0`</span><span class="sxs-lookup"><span data-stu-id="28d72-139">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method by setting the value to `0`.</span></span> <span data-ttu-id="28d72-140">Hodnota uzlu není odebrána, ale cena knihy byla odebrána podle jeho datového typu `xs:decimal`.</span><span class="sxs-lookup"><span data-stu-id="28d72-140">The value of the node is not removed, but the price of the book has been removed according to its data type of `xs:decimal`.</span></span>  
  
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
  
## <a name="namespace-nodes"></a><span data-ttu-id="28d72-141">Uzly oboru názvů</span><span class="sxs-lookup"><span data-stu-id="28d72-141">Namespace Nodes</span></span>  
 <span data-ttu-id="28d72-142">Uzly oboru názvů nelze odstranit z <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="28d72-142">Namespace nodes cannot be deleted from an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="28d72-143">Při pokusu o odstranění uzlů oboru <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> názvů pomocí metody dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="28d72-143">Attempts to delete namespace nodes using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method results in an exception.</span></span>  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="28d72-144">Vlastnosti InnerXml a OuterXml</span><span class="sxs-lookup"><span data-stu-id="28d72-144">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="28d72-145">Vlastnosti <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator> třídy <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> a třídy mění kód XML uzlů, na kterých je objekt aktuálně umístěn.</span><span class="sxs-lookup"><span data-stu-id="28d72-145">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="28d72-146"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Vlastnost změní kód XML podřízených uzlů, na kterých je <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěn, s analyzovaným obsahem daného XML `string`.</span><span class="sxs-lookup"><span data-stu-id="28d72-146">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="28d72-147">Podobně <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnost mění kód XML podřízených uzlů, na kterých je <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěn, i v samotném aktuálním uzlu.</span><span class="sxs-lookup"><span data-stu-id="28d72-147">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="28d72-148">Kromě metod popsaných v tomto tématu lze vlastnosti <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> použít k odebrání uzlů a hodnot z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="28d72-148">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="28d72-149">Další informace o použití vlastností <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> pro úpravu uzlů naleznete v tématu [Úprava dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) .</span><span class="sxs-lookup"><span data-stu-id="28d72-149">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to modify nodes, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="28d72-150">Uložení dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="28d72-150">Saving an XML Document</span></span>  
 <span data-ttu-id="28d72-151">Uložení změn provedených v <xref:System.Xml.XmlDocument> objektu jako výsledek metod popsaných v tomto tématu se provádí pomocí metod <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="28d72-151">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="28d72-152">Další informace o ukládání změn provedených v <xref:System.Xml.XmlDocument> objektu naleznete v tématu [ukládání a zápis dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="28d72-152">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28d72-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="28d72-153">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="28d72-154">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="28d72-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="28d72-155">Vložení dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="28d72-155">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="28d72-156">Změna dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="28d72-156">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)

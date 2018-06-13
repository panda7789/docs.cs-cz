---
title: Upravit pomocí objektem XPathNavigator nastaveným na Data XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb31c2ea504472a8707d700ff84b8c367467b607
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579116"
---
# <a name="modify-xml-data-using-xpathnavigator"></a><span data-ttu-id="ddac4-102">Upravit pomocí objektem XPathNavigator nastaveným na Data XML</span><span class="sxs-lookup"><span data-stu-id="ddac4-102">Modify XML Data using XPathNavigator</span></span>
<span data-ttu-id="ddac4-103"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které používají k úpravě uzly a hodnoty v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ddac4-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to modify nodes and values in an XML document.</span></span> <span data-ttu-id="ddac4-104">Chcete-li používat tyto metody <xref:System.Xml.XPath.XPathNavigator> objekt musí být upravitelné, který je jeho <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> musí být vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="ddac4-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="ddac4-105"><xref:System.Xml.XPath.XPathNavigator> objekty, které můžete upravit dokument XML, které jsou vytvořené pomocí <xref:System.Xml.XmlDocument.CreateNavigator%2A> metodu <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="ddac4-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="ddac4-106"><xref:System.Xml.XPath.XPathNavigator> objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídy jsou jen pro čtení a žádný pokus o použití úpravy metody <xref:System.Xml.XPath.XPathNavigator> objekt vytvořený <xref:System.Xml.XPath.XPathDocument> objektu vést <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="ddac4-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object result in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="ddac4-107">Další informace o vytváření upravitelné <xref:System.Xml.XPath.XPathNavigator> objekty, najdete v části [čtení dat XML pomocí XPathDocument třídou XMLDocument nastavenou na](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="ddac4-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="modifying-nodes"></a><span data-ttu-id="ddac4-108">Úprava uzly</span><span class="sxs-lookup"><span data-stu-id="ddac4-108">Modifying Nodes</span></span>  
 <span data-ttu-id="ddac4-109">Jednoduché technik pro změnu hodnoty uzlu je použít <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="ddac4-109">A simple technique for changing the value of a node is to use the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="ddac4-110">Následující tabulka uvádí důsledky z těchto metod pro různé typy uzlů.</span><span class="sxs-lookup"><span data-stu-id="ddac4-110">The following table lists the effects of these methods on different node types.</span></span>  
  
|<xref:System.Xml.XPath.XPathNodeType>|<span data-ttu-id="ddac4-111">Změnit data</span><span class="sxs-lookup"><span data-stu-id="ddac4-111">Data Changed</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|<span data-ttu-id="ddac4-112">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="ddac4-112">Not supported.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|<span data-ttu-id="ddac4-113">Obsah elementu.</span><span class="sxs-lookup"><span data-stu-id="ddac4-113">The content of the element.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|<span data-ttu-id="ddac4-114">Hodnota atributu.</span><span class="sxs-lookup"><span data-stu-id="ddac4-114">The value of the attribute.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|<span data-ttu-id="ddac4-115">Obsah textu.</span><span class="sxs-lookup"><span data-stu-id="ddac4-115">The text content.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|<span data-ttu-id="ddac4-116">Obsah, s výjimkou cíl.</span><span class="sxs-lookup"><span data-stu-id="ddac4-116">The content, excluding the target.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|<span data-ttu-id="ddac4-117">Obsah komentář.</span><span class="sxs-lookup"><span data-stu-id="ddac4-117">The content of the comment.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|<span data-ttu-id="ddac4-118">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="ddac4-118">Not Supported.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="ddac4-119">Úpravy <xref:System.Xml.XPath.XPathNodeType.Namespace> uzly nebo <xref:System.Xml.XPath.XPathNodeType.Root> uzel není podporován.</span><span class="sxs-lookup"><span data-stu-id="ddac4-119">Editing <xref:System.Xml.XPath.XPathNodeType.Namespace> nodes or the <xref:System.Xml.XPath.XPathNodeType.Root> node is not supported.</span></span>  
  
 <span data-ttu-id="ddac4-120"><xref:System.Xml.XPath.XPathNavigator> Třída rovněž poskytuje sadu metod používaných k vložení a odebrání uzlů.</span><span class="sxs-lookup"><span data-stu-id="ddac4-120">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of methods used to insert and remove nodes.</span></span> <span data-ttu-id="ddac4-121">Další informace o vložení a odebrání uzlů z dokumentu XML, najdete v článku [vložit Data XML pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) a [odebrat Data XML pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) témata.</span><span class="sxs-lookup"><span data-stu-id="ddac4-121">For more information about inserting and removing nodes from an XML document, see the [Insert XML Data using XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) and [Remove XML Data using XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) topics.</span></span>  
  
### <a name="modifying-untyped-values"></a><span data-ttu-id="ddac4-122">Úprava Netypové hodnoty</span><span class="sxs-lookup"><span data-stu-id="ddac4-122">Modifying Untyped Values</span></span>  
 <span data-ttu-id="ddac4-123"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda jednoduše vloží netypové `string` hodnota předaná jako parametr jako hodnotu uzlu <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na.</span><span class="sxs-lookup"><span data-stu-id="ddac4-123">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="ddac4-124">Hodnota je vložen bez jakéhokoli typu nebo bez ověření, že nová hodnota je platná podle typu uzlu, pokud je k dispozici informace o schématu.</span><span class="sxs-lookup"><span data-stu-id="ddac4-124">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="ddac4-125">V následujícím příkladu <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metoda se používá k aktualizaci všech `price` elementů v `contosoBooks.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="ddac4-125">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="ddac4-126">V příkladu trvá `contosoBooks.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="ddac4-126">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a><span data-ttu-id="ddac4-127">Úprava zadávaných hodnot</span><span class="sxs-lookup"><span data-stu-id="ddac4-127">Modifying Typed Values</span></span>  
 <span data-ttu-id="ddac4-128">Pokud je typ uzlu schématu XML W3C jednoduchý typ, nová hodnota vložená <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metoda bude zkontrolován omezující vlastnosti pro jednoduchý typ. předtím, než je hodnota nastavená.</span><span class="sxs-lookup"><span data-stu-id="ddac4-128">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="ddac4-129">Pokud nová hodnota není platná podle typu uzlu (například nastavení hodnotu `-1` u elementu, jehož typ je `xs:positiveInteger`), výsledkem výjimka.</span><span class="sxs-lookup"><span data-stu-id="ddac4-129">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="ddac4-130">V následujícím příkladu se pokusí změnit hodnotu `price` element první `book` element v `contosoBooks.xml` do souboru <xref:System.DateTime> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ddac4-130">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="ddac4-131">Vzhledem k tomu, že typ schématu XML `price` element je definován jako `xs:decimal` v `contosoBooks.xsd` soubory, to vede k výjimce.</span><span class="sxs-lookup"><span data-stu-id="ddac4-131">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
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
  
navigator.SetTypedValue(DateTime.Now)  
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
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 <span data-ttu-id="ddac4-132">V příkladu trvá `contosoBooks.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="ddac4-132">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="ddac4-133">Tento příklad také trvá `contosoBooks.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="ddac4-133">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a><span data-ttu-id="ddac4-134">Účinky úpravy dat silného typu XML</span><span class="sxs-lookup"><span data-stu-id="ddac4-134">The Effects of Editing Strongly Typed XML Data</span></span>  
 <span data-ttu-id="ddac4-135"><xref:System.Xml.XPath.XPathNavigator> Třída používá schéma XML W3C jako základ pro popisující silného typu XML.</span><span class="sxs-lookup"><span data-stu-id="ddac4-135">The <xref:System.Xml.XPath.XPathNavigator> class uses the W3C XML Schema as a basis for describing strongly-typed XML.</span></span> <span data-ttu-id="ddac4-136">Elementů a atributů může být označený poznámkou, s informací o typu založené na ověření na základě dokument schématu XML W3C.</span><span class="sxs-lookup"><span data-stu-id="ddac4-136">Elements and attributes can be annotated with type information based on validation against a W3C XML Schema document.</span></span> <span data-ttu-id="ddac4-137">Prvky, které může obsahovat další elementy nebo atributy se označují jako komplexní typy, zatímco ty, které může obsahovat pouze textové obsah se nazývají jednoduché typy.</span><span class="sxs-lookup"><span data-stu-id="ddac4-137">Elements that can contain other elements or attributes are called complex types, while those that can only contain textual content are called simple types.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ddac4-138">Atributy mohou mít pouze jednoduché typy.</span><span class="sxs-lookup"><span data-stu-id="ddac4-138">Attributes can only have simple types.</span></span>  
  
 <span data-ttu-id="ddac4-139">Elementu nebo atributu může být považuje za schématu platný, pokud je ve shodě se všechna pravidla, které jsou specifické pro jeho definice typu.</span><span class="sxs-lookup"><span data-stu-id="ddac4-139">An element or attribute can be considered to be schema-valid if it conforms to all the rules specific to its type definition.</span></span> <span data-ttu-id="ddac4-140">Element, který má jednoduchý typ `xs:int` obsahovat numerická hodnota mezi -2147483648 a 2147483647 schématu platný.</span><span class="sxs-lookup"><span data-stu-id="ddac4-140">An element that has the simple type `xs:int` has to contain a numeric value between -2147483648 and 2147483647 to be schema-valid.</span></span> <span data-ttu-id="ddac4-141">Pro komplexní typy je závislá na schéma platnosti jeho podřízených elementů a atributů schématu platnost elementu.</span><span class="sxs-lookup"><span data-stu-id="ddac4-141">For complex types, the schema-validity of the element is dependent on the schema-validity of its child elements and attributes.</span></span> <span data-ttu-id="ddac4-142">Proto pokud element je platné před jeho definice komplexního typu, všechny její podřízené elementy a atributy jsou platné pro jejich definice typu.</span><span class="sxs-lookup"><span data-stu-id="ddac4-142">Thus if an element is valid against its complex type definition, all its child elements and attributes are valid against their type definitions.</span></span> <span data-ttu-id="ddac4-143">Podobně pokud ani jeden z podřízené elementy nebo atributy elementu je neplatný pro jeho definice typu nebo má neznámý platnosti, element je také buď neplatný, nebo neznámé platnosti.</span><span class="sxs-lookup"><span data-stu-id="ddac4-143">Similarly, if even one of the child elements or attributes of an element is invalid against its type definition, or has an unknown validity, the element is also either invalid or of unknown validity.</span></span>  
  
 <span data-ttu-id="ddac4-144">Vzhledem k tomu, že platnost elementu je závislá na platnost jeho podřízených elementů a atributů, změny buď za následek změny platnosti elementu, pokud byl dříve platný.</span><span class="sxs-lookup"><span data-stu-id="ddac4-144">Given that the validity of an element is dependent on the validity of its child elements and attributes, modifications to either result in altering the validity of the element if it was previously valid.</span></span> <span data-ttu-id="ddac4-145">Konkrétně Pokud podřízené elementy nebo atributy elementu se přidají, aktualizovat nebo odstranit, pak platnosti elementu stává neznámé.</span><span class="sxs-lookup"><span data-stu-id="ddac4-145">Specifically, if the child elements or attributes of an element are inserted, updated, or deleted, then the validity of the element becomes unknown.</span></span> <span data-ttu-id="ddac4-146">To je reprezentována <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> vlastnost elementu <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnost je nastavená na <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span><span class="sxs-lookup"><span data-stu-id="ddac4-146">This is represented by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the element's <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property being set to <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span></span> <span data-ttu-id="ddac4-147">Kromě toho tato vliv uspořádá sebe směrem nahoru rekurzivně napříč v dokumentu XML protože platnost nadřazeného elementu (a jeho nadřazený element a tak dále) se také stane neznámé.</span><span class="sxs-lookup"><span data-stu-id="ddac4-147">Furthermore, this effect cascades upwards recursively across the XML document, because the validity of the element's parent element (and its parent element, and so on) also becomes unknown.</span></span>  
  
 <span data-ttu-id="ddac4-148">Další informace o ověřování schématu a <xref:System.Xml.XPath.XPathNavigator> třídy najdete v tématu [ověřování schématu pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="ddac4-148">For more information about schema validation and the <xref:System.Xml.XPath.XPathNavigator> class, see [Schema Validation using XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).</span></span>  
  
### <a name="modifying-attributes"></a><span data-ttu-id="ddac4-149">Úprava atributů</span><span class="sxs-lookup"><span data-stu-id="ddac4-149">Modifying Attributes</span></span>  
 <span data-ttu-id="ddac4-150"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody slouží k úpravě bez typu a zadaných atributů uzly, jakož i jiné typy uzlů uvedené v části "Úprava uzlů".</span><span class="sxs-lookup"><span data-stu-id="ddac4-150">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods can be used to modify untyped and typed attribute nodes as well as the other node types listed in the "Modifying Nodes" section.</span></span>  
  
 <span data-ttu-id="ddac4-151">Následující příklad změní hodnotu `genre` atribut první `book` element v `books.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="ddac4-151">The following example changes the value of the `genre` attribute of the first `book` element in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
navigator.MoveToChild("book", String.Empty)  
navigator.MoveToAttribute("genre", String.Empty)  
  
navigator.SetValue("non-fiction")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
navigator.MoveToChild("book", String.Empty);  
navigator.MoveToAttribute("genre", String.Empty);  
  
navigator.SetValue("non-fiction");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="ddac4-152">Další informace o <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody, najdete v částech "Úprava Netypové hodnoty" a "Úprava zadali hodnoty".</span><span class="sxs-lookup"><span data-stu-id="ddac4-152">For more information about the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods, see the "Modifying Untyped Values" and "Modifying Typed Values" sections.</span></span>  
  
## <a name="innerxml-and-outerxml-properties"></a><span data-ttu-id="ddac4-153">InnerXml a OuterXml vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ddac4-153">InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="ddac4-154"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třída změnit kód XML uzlů <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na.</span><span class="sxs-lookup"><span data-stu-id="ddac4-154">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="ddac4-155"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Změny vlastností kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěný na s Analyzovaná obsah daného XML `string`.</span><span class="sxs-lookup"><span data-stu-id="ddac4-155">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="ddac4-156">Podobně <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> změny vlastností kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěný na i aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="ddac4-156">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="ddac4-157">Následující příklad používá <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnost změnit hodnotu `price` elementu a vložit nový `discount` atribut v prvním `book` element v `contosoBooks.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="ddac4-157">The following example uses the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property to modify the value of the `price` element and insert a new `discount` attribute on the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml");  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>"  
  
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
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>";  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="ddac4-158">V příkladu trvá `contosoBooks.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="ddac4-158">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a><span data-ttu-id="ddac4-159">Úprava Namespace uzly</span><span class="sxs-lookup"><span data-stu-id="ddac4-159">Modifying Namespace Nodes</span></span>  
 <span data-ttu-id="ddac4-160">V modelu DOM (Document Object), deklarace oboru názvů, které jsou zpracovány jako v případě, že jsou regulární atributy, které můžete vložit, aktualizovat a odstranit.</span><span class="sxs-lookup"><span data-stu-id="ddac4-160">In the Document Object Model (DOM), namespace declarations are treated as if they are regular attributes that can be inserted, updated and deleted.</span></span> <span data-ttu-id="ddac4-161"><xref:System.Xml.XPath.XPathNavigator> – Třída neumožňuje tyto operace na uzlech obor názvů, protože změna hodnotu uzlu oboru názvů můžete změnit identitu elementů a atributů v rámci oboru názvů uzlu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ddac4-161">The <xref:System.Xml.XPath.XPathNavigator> class does not allow such operations on namespace nodes because altering the value of a namespace node can change the identity of the elements and attributes within the scope of the namespace node as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="ddac4-162">V předchozím příkladu XML dojde ke změně následujícím způsobem, to každý element v dokumentu efektivně přejmenuje, protože se změní hodnota každý prvek identifikátor URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ddac4-162">If the XML example above is changed in the following way, this effectively renames every element in the document because the value of each element's namespace URI is changed.</span></span>  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="ddac4-163">Vkládání uzly oboru názvů, které nejsou v konfliktu s deklarace oboru názvů v oboru, který se vloží do povolilo <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="ddac4-163">Inserting namespace nodes that do not conflict with namespace declarations at the scope that they are inserted in is allowed by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="ddac4-164">V takovém případě deklarace oboru názvů nejsou deklarovat na nižší obory v dokumentu XML a nevede přejmenování, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ddac4-164">In this case, the namespace declarations are not declared at lower scopes in the XML document and does not result in renaming as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="ddac4-165">Pokud se v předchozím příkladu XML změnil následujícím způsobem, deklarace oboru názvů správně rozšířeny napříč v dokumentu XML níže oboru další deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ddac4-165">If the XML example above is changed in the following way, the namespace declarations are correctly propagated across the XML document below the scope of the other namespace declaration.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/">  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="ddac4-166">V XML příkladu výše, atribut `a:parent-id` na zadává `parent` element v `http://www.contoso.com/parent-id` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ddac4-166">In the XML example above, the attribute `a:parent-id` is inserted on the `parent` element in the `http://www.contoso.com/parent-id` namespace.</span></span> <span data-ttu-id="ddac4-167"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Metoda slouží k vložení atribut při umístěný na `parent` elementu.</span><span class="sxs-lookup"><span data-stu-id="ddac4-167">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method is used to insert the attribute while positioned on the `parent` element.</span></span> <span data-ttu-id="ddac4-168">`http://www.contoso.com` Deklaraci oboru názvů je automaticky vkládat <xref:System.Xml.XPath.XPathNavigator> třídu k zachování konzistence zbývající části dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ddac4-168">The `http://www.contoso.com` namespace declaration is automatically inserted by the <xref:System.Xml.XPath.XPathNavigator> class to preserve the consistency of the rest of the XML document.</span></span>  
  
## <a name="modifying-entity-reference-nodes"></a><span data-ttu-id="ddac4-169">Úprava uzly odkaz Entity</span><span class="sxs-lookup"><span data-stu-id="ddac4-169">Modifying Entity Reference Nodes</span></span>  
 <span data-ttu-id="ddac4-170">Uzly odkaz na entitu v <xref:System.Xml.XmlDocument> objekt jsou jen pro čtení a nelze je upravit pomocí <xref:System.Xml.XPath.XPathNavigator> nebo <xref:System.Xml.XmlNode> třídy.</span><span class="sxs-lookup"><span data-stu-id="ddac4-170">Entity reference nodes in an <xref:System.Xml.XmlDocument> object are read-only and cannot be edited using either the <xref:System.Xml.XPath.XPathNavigator> or <xref:System.Xml.XmlNode> classes.</span></span> <span data-ttu-id="ddac4-171">Výsledkem žádné pokusu o změnu uzlu odkazu entity <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="ddac4-171">Any attempt to modify an entity reference node results in an <xref:System.InvalidOperationException>.</span></span>  
  
## <a name="modifying-xsinil-nodes"></a><span data-ttu-id="ddac4-172">Úprava xsi: nil uzly</span><span class="sxs-lookup"><span data-stu-id="ddac4-172">Modifying xsi:nil Nodes</span></span>  
 <span data-ttu-id="ddac4-173">Doporučení schématu XML W3C zavádí koncepci elementu se povolenou hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="ddac4-173">The W3C XML Schema recommendation introduces the concept of an element being nillable.</span></span> <span data-ttu-id="ddac4-174">Když je element povolenou hodnotu Null, je možné pro element nemají žádný obsah a být stále platné.</span><span class="sxs-lookup"><span data-stu-id="ddac4-174">When an element is nillable, it is possible for the element to have no content and still be valid.</span></span> <span data-ttu-id="ddac4-175">Koncept elementu se povolenou je podobný koncept k objektu se `null`.</span><span class="sxs-lookup"><span data-stu-id="ddac4-175">The concept of an element being nillable is similar to the concept of an object being `null`.</span></span> <span data-ttu-id="ddac4-176">Hlavní rozdíl je, že `null` objekt nemůže mít přístup k žádným způsobem, při `xsi:nil` element stále existují vlastnosti, například atributy, které jsou přístupné, ale nemá žádný obsah (podřízené elementy nebo text).</span><span class="sxs-lookup"><span data-stu-id="ddac4-176">The main difference is that a `null` object cannot be accessed in any way, while an `xsi:nil` element still has properties such as attributes that can be accessed, but has no content (child elements or text).</span></span> <span data-ttu-id="ddac4-177">Existenci `xsi:nil` atributu s hodnotou `true` v elementu v kódu XML dokumentu slouží k označení, že element nemá žádný obsah.</span><span class="sxs-lookup"><span data-stu-id="ddac4-177">The existence of the `xsi:nil` attribute with a value of `true` on an element in an XML document is used to indicate that an element has no content.</span></span>  
  
 <span data-ttu-id="ddac4-178">Pokud <xref:System.Xml.XPath.XPathNavigator> objekt se používá k přidání obsahu do platný element s `xsi:nil` atributu s hodnotou `true`, hodnota jeho `xsi:nil` je nastavena na hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="ddac4-178">If an <xref:System.Xml.XPath.XPathNavigator> object is used to add content to a valid element with an `xsi:nil` attribute with a value of `true`, the value of its `xsi:nil` attribute is set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ddac4-179">Pokud obsah elementu se `xsi:nil` atribut nastaven na `false` je odstranit, hodnota atributu není změněna na `true`.</span><span class="sxs-lookup"><span data-stu-id="ddac4-179">If the content of an element with an `xsi:nil` attribute set to `false` is deleted, the value of the attribute is not changed to `true`.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="ddac4-180">Uložení dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="ddac4-180">Saving an XML Document</span></span>  
 <span data-ttu-id="ddac4-181">Ukládají se změny provedené v <xref:System.Xml.XmlDocument> objektu jako výsledek úprav metod popsaných v tomto tématu se provádí pomocí metody <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="ddac4-181">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the editing methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="ddac4-182">Další informace o ukládání změny <xref:System.Xml.XmlDocument> objektu, najdete v části [ukládání a zápis dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="ddac4-182">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddac4-183">Viz také</span><span class="sxs-lookup"><span data-stu-id="ddac4-183">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="ddac4-184">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="ddac4-184">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="ddac4-185">Vložení dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ddac4-185">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="ddac4-186">Odebrání dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ddac4-186">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)

---
title: Změna dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
ms.openlocfilehash: 3b64bc8666274798ebaefc87ef3883fcec1ef6b1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288833"
---
# <a name="modify-xml-data-using-xpathnavigator"></a><span data-ttu-id="9f14c-102">Změna dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="9f14c-102">Modify XML Data using XPathNavigator</span></span>
<span data-ttu-id="9f14c-103"><xref:System.Xml.XPath.XPathNavigator>Třída poskytuje sadu metod, které slouží k úpravě uzlů a hodnot v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="9f14c-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to modify nodes and values in an XML document.</span></span> <span data-ttu-id="9f14c-104">Aby bylo možné tyto metody použít, <xref:System.Xml.XPath.XPathNavigator> musí být objekt upravitelný, to znamená, že jeho <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> vlastnost musí být `true` .</span><span class="sxs-lookup"><span data-stu-id="9f14c-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="9f14c-105"><xref:System.Xml.XPath.XPathNavigator>objekty, které mohou upravovat dokument XML, jsou vytvořeny <xref:System.Xml.XmlDocument.CreateNavigator%2A> metodou <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="9f14c-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="9f14c-106"><xref:System.Xml.XPath.XPathNavigator>objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídou jsou jen pro čtení a všechny pokusy o použití metod úprav <xref:System.Xml.XPath.XPathNavigator> objektu vytvořeného objektem mají za <xref:System.Xml.XPath.XPathDocument> následek <xref:System.NotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="9f14c-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object result in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="9f14c-107">Další informace o vytváření upravitelných <xref:System.Xml.XPath.XPathNavigator> objektů najdete v tématu [čtení dat XML pomocí XPathDocument a XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="9f14c-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="modifying-nodes"></a><span data-ttu-id="9f14c-108">Úprava uzlů</span><span class="sxs-lookup"><span data-stu-id="9f14c-108">Modifying Nodes</span></span>  
 <span data-ttu-id="9f14c-109">Jednoduchá technika pro změnu hodnoty uzlu je použití <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metod a <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="9f14c-109">A simple technique for changing the value of a node is to use the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="9f14c-110">V následující tabulce jsou uvedeny účinky těchto metod na různé typy uzlů.</span><span class="sxs-lookup"><span data-stu-id="9f14c-110">The following table lists the effects of these methods on different node types.</span></span>  
  
|<xref:System.Xml.XPath.XPathNodeType>|<span data-ttu-id="9f14c-111">Data změněna</span><span class="sxs-lookup"><span data-stu-id="9f14c-111">Data Changed</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|<span data-ttu-id="9f14c-112">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="9f14c-112">Not supported.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|<span data-ttu-id="9f14c-113">Obsah elementu.</span><span class="sxs-lookup"><span data-stu-id="9f14c-113">The content of the element.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|<span data-ttu-id="9f14c-114">Hodnota atributu</span><span class="sxs-lookup"><span data-stu-id="9f14c-114">The value of the attribute.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|<span data-ttu-id="9f14c-115">Textový obsah.</span><span class="sxs-lookup"><span data-stu-id="9f14c-115">The text content.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|<span data-ttu-id="9f14c-116">Obsah s výjimkou cíle.</span><span class="sxs-lookup"><span data-stu-id="9f14c-116">The content, excluding the target.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|<span data-ttu-id="9f14c-117">Obsah komentáře</span><span class="sxs-lookup"><span data-stu-id="9f14c-117">The content of the comment.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|<span data-ttu-id="9f14c-118">Nepodporuje se.</span><span class="sxs-lookup"><span data-stu-id="9f14c-118">Not Supported.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="9f14c-119">Úprava <xref:System.Xml.XPath.XPathNodeType.Namespace> uzlů nebo <xref:System.Xml.XPath.XPathNodeType.Root> uzlu není podporována.</span><span class="sxs-lookup"><span data-stu-id="9f14c-119">Editing <xref:System.Xml.XPath.XPathNodeType.Namespace> nodes or the <xref:System.Xml.XPath.XPathNodeType.Root> node is not supported.</span></span>  
  
 <span data-ttu-id="9f14c-120"><xref:System.Xml.XPath.XPathNavigator>Třída také poskytuje sadu metod, které se používají pro vkládání a odebírání uzlů.</span><span class="sxs-lookup"><span data-stu-id="9f14c-120">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of methods used to insert and remove nodes.</span></span> <span data-ttu-id="9f14c-121">Další informace o vkládání a odebírání uzlů z dokumentu XML naleznete v tématu [vložení dat XML pomocí XPathNavigator](insert-xml-data-using-xpathnavigator.md) a [Odebrání XML data pomocí témat XPathNavigator](remove-xml-data-using-xpathnavigator.md) .</span><span class="sxs-lookup"><span data-stu-id="9f14c-121">For more information about inserting and removing nodes from an XML document, see the [Insert XML Data using XPathNavigator](insert-xml-data-using-xpathnavigator.md) and [Remove XML Data using XPathNavigator](remove-xml-data-using-xpathnavigator.md) topics.</span></span>  
  
### <a name="modifying-untyped-values"></a><span data-ttu-id="9f14c-122">Úprava netypových hodnot</span><span class="sxs-lookup"><span data-stu-id="9f14c-122">Modifying Untyped Values</span></span>  
 <span data-ttu-id="9f14c-123"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A>Metoda jednoduše vloží netypové `string` hodnoty předané jako parametr jako hodnotu uzlu, <xref:System.Xml.XPath.XPathNavigator> na kterém je objekt aktuálně umístěn.</span><span class="sxs-lookup"><span data-stu-id="9f14c-123">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="9f14c-124">Hodnota je vložena bez jakéhokoli typu nebo bez ověření, že nová hodnota je platná podle typu uzlu, pokud jsou k dispozici informace o schématu.</span><span class="sxs-lookup"><span data-stu-id="9f14c-124">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="9f14c-125">V následujícím příkladu <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> je metoda použita k aktualizaci všech `price` prvků v `contosoBooks.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="9f14c-125">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="9f14c-126">Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="9f14c-126">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a><span data-ttu-id="9f14c-127">Úprava zadaných hodnot</span><span class="sxs-lookup"><span data-stu-id="9f14c-127">Modifying Typed Values</span></span>  
 <span data-ttu-id="9f14c-128">Pokud je typ uzlu jednoduchý typ schématu W3C XML, je nová hodnota vložená <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodou zkontrolována proti omezující vlastnosti jednoduchého typu před nastavením hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9f14c-128">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="9f14c-129">Pokud nová hodnota není platná podle typu uzlu (například nastavení hodnoty `-1` na elementu, jehož typ je `xs:positiveInteger` ), výsledkem je výjimka.</span><span class="sxs-lookup"><span data-stu-id="9f14c-129">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="9f14c-130">Následující příklad se pokusí změnit hodnotu `price` prvku prvního `book` prvku v `contosoBooks.xml` souboru na <xref:System.DateTime> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9f14c-130">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="9f14c-131">Vzhledem k tomu, že typ schématu XML `price` elementu je definován jako `xs:decimal` v `contosoBooks.xsd` souborech, výsledkem je výjimka.</span><span class="sxs-lookup"><span data-stu-id="9f14c-131">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
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
  
 <span data-ttu-id="9f14c-132">Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="9f14c-132">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="9f14c-133">Příklad také přebírá `contosoBooks.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="9f14c-133">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a><span data-ttu-id="9f14c-134">Důsledky úprav dat XML se silnými typy</span><span class="sxs-lookup"><span data-stu-id="9f14c-134">The Effects of Editing Strongly Typed XML Data</span></span>  
 <span data-ttu-id="9f14c-135"><xref:System.Xml.XPath.XPathNavigator>Třída používá schéma W3C XML jako základ pro popis silného typu XML.</span><span class="sxs-lookup"><span data-stu-id="9f14c-135">The <xref:System.Xml.XPath.XPathNavigator> class uses the W3C XML Schema as a basis for describing strongly typed XML.</span></span> <span data-ttu-id="9f14c-136">Elementy a atributy lze opatřit poznámkami pomocí informací o typu na základě ověřování v dokumentu schématu W3C XML.</span><span class="sxs-lookup"><span data-stu-id="9f14c-136">Elements and attributes can be annotated with type information based on validation against a W3C XML Schema document.</span></span> <span data-ttu-id="9f14c-137">Prvky, které mohou obsahovat další elementy nebo atributy, se nazývají komplexní typy, zatímco ty, které mohou obsahovat pouze textový obsah, se nazývají jednoduché typy.</span><span class="sxs-lookup"><span data-stu-id="9f14c-137">Elements that can contain other elements or attributes are called complex types, while those that can only contain textual content are called simple types.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9f14c-138">Atributy můžou mít jenom jednoduché typy.</span><span class="sxs-lookup"><span data-stu-id="9f14c-138">Attributes can only have simple types.</span></span>  
  
 <span data-ttu-id="9f14c-139">Element nebo atribut lze považovat za schéma – platný, pokud odpovídá všem pravidlům, která jsou specifická pro jeho definici typu.</span><span class="sxs-lookup"><span data-stu-id="9f14c-139">An element or attribute can be considered to be schema-valid if it conforms to all the rules specific to its type definition.</span></span> <span data-ttu-id="9f14c-140">Element, který má jednoduchý typ, `xs:int` musí obsahovat číselnou hodnotu mezi-2147483648 a 2147483647, aby bylo schématu platné.</span><span class="sxs-lookup"><span data-stu-id="9f14c-140">An element that has the simple type `xs:int` has to contain a numeric value between -2147483648 and 2147483647 to be schema-valid.</span></span> <span data-ttu-id="9f14c-141">U komplexních typů je platnost schématu platnosti elementu závislá na schématu platnosti svých podřízených prvků a atributů.</span><span class="sxs-lookup"><span data-stu-id="9f14c-141">For complex types, the schema-validity of the element is dependent on the schema-validity of its child elements and attributes.</span></span> <span data-ttu-id="9f14c-142">Proto pokud je element platný proti definici komplexního typu, všechny jeho podřízené prvky a atributy jsou platné proti definicím jejich typu.</span><span class="sxs-lookup"><span data-stu-id="9f14c-142">Thus if an element is valid against its complex type definition, all its child elements and attributes are valid against their type definitions.</span></span> <span data-ttu-id="9f14c-143">Podobně, pokud je i jeden z podřízených elementů nebo atributů elementu neplatný proti své definici typu nebo má neznámou platnost, prvek je také buď neplatný, nebo neznámou platnost.</span><span class="sxs-lookup"><span data-stu-id="9f14c-143">Similarly, if even one of the child elements or attributes of an element is invalid against its type definition, or has an unknown validity, the element is also either invalid or of unknown validity.</span></span>  
  
 <span data-ttu-id="9f14c-144">Vzhledem k tomu, že platnost elementu je závislá na platnosti svých podřízených prvků a atributů, úpravy v důsledku změny platnosti prvku, pokud byl dříve platný.</span><span class="sxs-lookup"><span data-stu-id="9f14c-144">Given that the validity of an element is dependent on the validity of its child elements and attributes, modifications to either result in altering the validity of the element if it was previously valid.</span></span> <span data-ttu-id="9f14c-145">Konkrétně, pokud jsou podřízené prvky nebo atributy elementu vloženy, aktualizovány nebo smazány, pak platnost elementu bude neznáma.</span><span class="sxs-lookup"><span data-stu-id="9f14c-145">Specifically, if the child elements or attributes of an element are inserted, updated, or deleted, then the validity of the element becomes unknown.</span></span> <span data-ttu-id="9f14c-146">Toto je reprezentované <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> vlastností <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnosti elementu nastavenou na <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown> .</span><span class="sxs-lookup"><span data-stu-id="9f14c-146">This is represented by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the element's <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property being set to <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span></span> <span data-ttu-id="9f14c-147">Kromě toho tento efekt kaskádě provede v dokumentu XML rekurzivně nahoru, protože platnost nadřazeného elementu elementu (a jeho nadřazeného elementu atd.) je také neznámá.</span><span class="sxs-lookup"><span data-stu-id="9f14c-147">Furthermore, this effect cascades upwards recursively across the XML document, because the validity of the element's parent element (and its parent element, and so on) also becomes unknown.</span></span>  
  
 <span data-ttu-id="9f14c-148">Další informace o ověřování schématu a <xref:System.Xml.XPath.XPathNavigator> třídě naleznete v tématu [ověřování schématu pomocí XPathNavigator](schema-validation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="9f14c-148">For more information about schema validation and the <xref:System.Xml.XPath.XPathNavigator> class, see [Schema Validation using XPathNavigator](schema-validation-using-xpathnavigator.md).</span></span>  
  
### <a name="modifying-attributes"></a><span data-ttu-id="9f14c-149">Úprava atributů</span><span class="sxs-lookup"><span data-stu-id="9f14c-149">Modifying Attributes</span></span>  
 <span data-ttu-id="9f14c-150"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A>Metody a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> lze použít pro úpravu netypových a typových uzlů atributů a také jiných typů uzlů uvedených v části "Změna uzlů".</span><span class="sxs-lookup"><span data-stu-id="9f14c-150">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods can be used to modify untyped and typed attribute nodes as well as the other node types listed in the "Modifying Nodes" section.</span></span>  
  
 <span data-ttu-id="9f14c-151">Následující příklad změní hodnotu `genre` atributu prvního `book` prvku v `books.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="9f14c-151">The following example changes the value of the `genre` attribute of the first `book` element in the `books.xml` file.</span></span>  
  
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
  
 <span data-ttu-id="9f14c-152">Další informace o <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodách a naleznete v částech "úpravy netypových hodnot" a "úpravy zadaných hodnot".</span><span class="sxs-lookup"><span data-stu-id="9f14c-152">For more information about the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods, see the "Modifying Untyped Values" and "Modifying Typed Values" sections.</span></span>  
  
## <a name="innerxml-and-outerxml-properties"></a><span data-ttu-id="9f14c-153">Vlastnosti InnerXml a OuterXml</span><span class="sxs-lookup"><span data-stu-id="9f14c-153">InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="9f14c-154"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy a třídy mění kód XML uzlů, <xref:System.Xml.XPath.XPathNavigator> na kterých je objekt aktuálně umístěn.</span><span class="sxs-lookup"><span data-stu-id="9f14c-154">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="9f14c-155"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>Vlastnost změní kód XML podřízených uzlů, <xref:System.Xml.XPath.XPathNavigator> na kterých je objekt aktuálně umístěn, s analyzovaným obsahem daného XML `string` .</span><span class="sxs-lookup"><span data-stu-id="9f14c-155">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="9f14c-156">Podobně <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnost mění kód XML podřízených uzlů, <xref:System.Xml.XPath.XPathNavigator> na kterých je objekt aktuálně umístěn, i v samotném aktuálním uzlu.</span><span class="sxs-lookup"><span data-stu-id="9f14c-156">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="9f14c-157">V následujícím příkladu je použita <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnost pro úpravu hodnoty `price` prvku a vložení nového `discount` atributu do prvního `book` prvku v `contosoBooks.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="9f14c-157">The following example uses the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property to modify the value of the `price` element and insert a new `discount` attribute on the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
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
  
 <span data-ttu-id="9f14c-158">Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="9f14c-158">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a><span data-ttu-id="9f14c-159">Úprava uzlů oboru názvů</span><span class="sxs-lookup"><span data-stu-id="9f14c-159">Modifying Namespace Nodes</span></span>  
 <span data-ttu-id="9f14c-160">V model DOM (Document Object Model) (DOM) se deklarace oborů názvů považují za, jako by se jednalo o běžné atributy, které se dají vkládat, aktualizovat a odstraňovat.</span><span class="sxs-lookup"><span data-stu-id="9f14c-160">In the Document Object Model (DOM), namespace declarations are treated as if they are regular attributes that can be inserted, updated and deleted.</span></span> <span data-ttu-id="9f14c-161"><xref:System.Xml.XPath.XPathNavigator>Třída nepovoluje takové operace na uzlech oboru názvů, protože změna hodnoty uzlu oboru názvů může změnit identitu prvků a atributů v rámci oboru oboru názvů, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9f14c-161">The <xref:System.Xml.XPath.XPathNavigator> class does not allow such operations on namespace nodes because altering the value of a namespace node can change the identity of the elements and attributes within the scope of the namespace node as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="9f14c-162">Pokud se výše uvedený příklad XML změní následujícím způsobem, tato možnost efektivně přejmenuje každý prvek v dokumentu, protože se změnila hodnota identifikátoru URI oboru názvů každého elementu.</span><span class="sxs-lookup"><span data-stu-id="9f14c-162">If the XML example above is changed in the following way, this effectively renames every element in the document because the value of each element's namespace URI is changed.</span></span>  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="9f14c-163">Vložení uzlů oboru názvů, které nejsou v konfliktu s deklaracemi oboru názvů v oboru, ve kterém jsou vloženy, je povoleno <xref:System.Xml.XPath.XPathNavigator> třídou.</span><span class="sxs-lookup"><span data-stu-id="9f14c-163">Inserting namespace nodes that do not conflict with namespace declarations at the scope that they are inserted in is allowed by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="9f14c-164">V tomto případě deklarace oboru názvů nejsou deklarovány v nižších oborech v dokumentu XML a nevedou k přejmenování, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9f14c-164">In this case, the namespace declarations are not declared at lower scopes in the XML document and does not result in renaming as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="9f14c-165">Pokud se výše uvedený příklad XML změní následujícím způsobem, deklarace oboru názvů jsou správně šířeny v rámci dokumentu XML pod rozsahem jiné deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9f14c-165">If the XML example above is changed in the following way, the namespace declarations are correctly propagated across the XML document below the scope of the other namespace declaration.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/" />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="9f14c-166">Ve výše uvedeném příkladu XML `a:parent-id` je atribut vložen na `parent` prvek v `http://www.contoso.com/parent-id` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9f14c-166">In the XML example above, the attribute `a:parent-id` is inserted on the `parent` element in the `http://www.contoso.com/parent-id` namespace.</span></span> <span data-ttu-id="9f14c-167"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>Metoda se používá k vložení atributu při umístění na `parent` element.</span><span class="sxs-lookup"><span data-stu-id="9f14c-167">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method is used to insert the attribute while positioned on the `parent` element.</span></span> <span data-ttu-id="9f14c-168">`http://www.contoso.com`Deklarace oboru názvů je automaticky vložena <xref:System.Xml.XPath.XPathNavigator> třídou, která zachovává konzistenci zbytku dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="9f14c-168">The `http://www.contoso.com` namespace declaration is automatically inserted by the <xref:System.Xml.XPath.XPathNavigator> class to preserve the consistency of the rest of the XML document.</span></span>  
  
## <a name="modifying-entity-reference-nodes"></a><span data-ttu-id="9f14c-169">Úprava uzlů odkazů na entity</span><span class="sxs-lookup"><span data-stu-id="9f14c-169">Modifying Entity Reference Nodes</span></span>  
 <span data-ttu-id="9f14c-170">Uzly odkazů na entity v <xref:System.Xml.XmlDocument> objektu jsou jen pro čtení a nelze je upravovat pomocí <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XmlNode> tříd nebo.</span><span class="sxs-lookup"><span data-stu-id="9f14c-170">Entity reference nodes in an <xref:System.Xml.XmlDocument> object are read-only and cannot be edited using either the <xref:System.Xml.XPath.XPathNavigator> or <xref:System.Xml.XmlNode> classes.</span></span> <span data-ttu-id="9f14c-171">Jakýkoli pokus o změnu uzlu odkazu na entitu má za následek <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="9f14c-171">Any attempt to modify an entity reference node results in an <xref:System.InvalidOperationException>.</span></span>  
  
## <a name="modifying-xsinil-nodes"></a><span data-ttu-id="9f14c-172">Úprava uzlů xsi: nil</span><span class="sxs-lookup"><span data-stu-id="9f14c-172">Modifying xsi:nil Nodes</span></span>  
 <span data-ttu-id="9f14c-173">Doporučení schématu W3C XML zavádí koncept prvku, který je nillable.</span><span class="sxs-lookup"><span data-stu-id="9f14c-173">The W3C XML Schema recommendation introduces the concept of an element being nillable.</span></span> <span data-ttu-id="9f14c-174">Když je element nillable, je možné, že element nemá žádný obsah a bude nadále platný.</span><span class="sxs-lookup"><span data-stu-id="9f14c-174">When an element is nillable, it is possible for the element to have no content and still be valid.</span></span> <span data-ttu-id="9f14c-175">Koncept prvku, který je nillable, je podobný konceptu objektu, který je `null` .</span><span class="sxs-lookup"><span data-stu-id="9f14c-175">The concept of an element being nillable is similar to the concept of an object being `null`.</span></span> <span data-ttu-id="9f14c-176">Hlavním rozdílem je, že k `null` objektu nelze přistup jakýmkoli způsobem, zatímco `xsi:nil` element stále obsahuje vlastnosti, jako jsou například atributy, které lze použít, ale nemá žádný obsah (podřízené prvky nebo text).</span><span class="sxs-lookup"><span data-stu-id="9f14c-176">The main difference is that a `null` object cannot be accessed in any way, while an `xsi:nil` element still has properties such as attributes that can be accessed, but has no content (child elements or text).</span></span> <span data-ttu-id="9f14c-177">Existence `xsi:nil` atributu s hodnotou `true` elementu v dokumentu XML slouží k označení toho, že element nemá žádný obsah.</span><span class="sxs-lookup"><span data-stu-id="9f14c-177">The existence of the `xsi:nil` attribute with a value of `true` on an element in an XML document is used to indicate that an element has no content.</span></span>  
  
 <span data-ttu-id="9f14c-178">Pokud <xref:System.Xml.XPath.XPathNavigator> je objekt použit k přidání obsahu do platného prvku s `xsi:nil` atributem s hodnotou `true` , hodnota jeho `xsi:nil` atributu je nastavena na `false` .</span><span class="sxs-lookup"><span data-stu-id="9f14c-178">If an <xref:System.Xml.XPath.XPathNavigator> object is used to add content to a valid element with an `xsi:nil` attribute with a value of `true`, the value of its `xsi:nil` attribute is set to `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9f14c-179">Pokud je obsah elementu s `xsi:nil` atributem nastaveným na hodnotu `false` odstraněn, hodnota atributu není změněna na `true` .</span><span class="sxs-lookup"><span data-stu-id="9f14c-179">If the content of an element with an `xsi:nil` attribute set to `false` is deleted, the value of the attribute is not changed to `true`.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="9f14c-180">Uložení dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="9f14c-180">Saving an XML Document</span></span>  
 <span data-ttu-id="9f14c-181">Uložení změn provedených <xref:System.Xml.XmlDocument> v objektu jako výsledek metod úprav popsaných v tomto tématu se provádí pomocí metod <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="9f14c-181">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the editing methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="9f14c-182">Další informace o ukládání změn provedených v <xref:System.Xml.XmlDocument> objektu naleznete v tématu [ukládání a zápis dokumentu](saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="9f14c-182">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f14c-183">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f14c-183">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="9f14c-184">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="9f14c-184">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="9f14c-185">Vložení dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="9f14c-185">Insert XML Data using XPathNavigator</span></span>](insert-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="9f14c-186">Odebrání dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="9f14c-186">Remove XML Data using XPathNavigator</span></span>](remove-xml-data-using-xpathnavigator.md)

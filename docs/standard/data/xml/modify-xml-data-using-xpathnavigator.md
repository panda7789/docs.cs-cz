---
title: Změna dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 219327d246416cfb3d76919680aa74a58bae5fb3
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085869"
---
# <a name="modify-xml-data-using-xpathnavigator"></a><span data-ttu-id="6c781-102">Změna dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="6c781-102">Modify XML Data using XPathNavigator</span></span>
<span data-ttu-id="6c781-103"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které slouží k úpravě uzly a hodnoty v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="6c781-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to modify nodes and values in an XML document.</span></span> <span data-ttu-id="6c781-104">Chcete-li používat tyto metody <xref:System.Xml.XPath.XPathNavigator> objekt musí být upravitelné, to znamená, jeho <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> musí být vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="6c781-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="6c781-105"><xref:System.Xml.XPath.XPathNavigator> objekty, které můžete upravit dokument XML jsou vytvářeny <xref:System.Xml.XmlDocument.CreateNavigator%2A> metodu <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="6c781-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="6c781-106"><xref:System.Xml.XPath.XPathNavigator> objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídy jsou jen pro čtení a žádný pokus o použití metod pro posunutí úprav <xref:System.Xml.XPath.XPathNavigator> objekt vytvořený pomocí <xref:System.Xml.XPath.XPathDocument> výsledek v objektu <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="6c781-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object result in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="6c781-107">Další informace o vytváření upravitelné <xref:System.Xml.XPath.XPathNavigator> objekty, najdete [čtení dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="6c781-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="modifying-nodes"></a><span data-ttu-id="6c781-108">Úprava uzlů</span><span class="sxs-lookup"><span data-stu-id="6c781-108">Modifying Nodes</span></span>  
 <span data-ttu-id="6c781-109">Jednoduchý postup pro změnu hodnoty uzlu je použít <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="6c781-109">A simple technique for changing the value of a node is to use the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="6c781-110">V následující tabulce jsou uvedeny účinky z těchto metod na různé typy uzlů.</span><span class="sxs-lookup"><span data-stu-id="6c781-110">The following table lists the effects of these methods on different node types.</span></span>  
  
|<xref:System.Xml.XPath.XPathNodeType>|<span data-ttu-id="6c781-111">Změny dat</span><span class="sxs-lookup"><span data-stu-id="6c781-111">Data Changed</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|<span data-ttu-id="6c781-112">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="6c781-112">Not supported.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|<span data-ttu-id="6c781-113">Obsah elementu.</span><span class="sxs-lookup"><span data-stu-id="6c781-113">The content of the element.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|<span data-ttu-id="6c781-114">Hodnota atributu.</span><span class="sxs-lookup"><span data-stu-id="6c781-114">The value of the attribute.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|<span data-ttu-id="6c781-115">Textový obsah.</span><span class="sxs-lookup"><span data-stu-id="6c781-115">The text content.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|<span data-ttu-id="6c781-116">Obsah, s výjimkou cíl.</span><span class="sxs-lookup"><span data-stu-id="6c781-116">The content, excluding the target.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|<span data-ttu-id="6c781-117">Obsah komentář.</span><span class="sxs-lookup"><span data-stu-id="6c781-117">The content of the comment.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|<span data-ttu-id="6c781-118">Nepodporuje se.</span><span class="sxs-lookup"><span data-stu-id="6c781-118">Not Supported.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="6c781-119">Úpravy <xref:System.Xml.XPath.XPathNodeType.Namespace> uzly nebo <xref:System.Xml.XPath.XPathNodeType.Root> uzel není podporován.</span><span class="sxs-lookup"><span data-stu-id="6c781-119">Editing <xref:System.Xml.XPath.XPathNodeType.Namespace> nodes or the <xref:System.Xml.XPath.XPathNodeType.Root> node is not supported.</span></span>  
  
 <span data-ttu-id="6c781-120"><xref:System.Xml.XPath.XPathNavigator> Třída rovněž poskytuje sadu metod používaných pro vložení a odebrání uzlů.</span><span class="sxs-lookup"><span data-stu-id="6c781-120">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of methods used to insert and remove nodes.</span></span> <span data-ttu-id="6c781-121">Další informace o vkládání a odstranění uzlů z dokumentu XML, najdete v článku [vložení dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) a [odebrání dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) témata.</span><span class="sxs-lookup"><span data-stu-id="6c781-121">For more information about inserting and removing nodes from an XML document, see the [Insert XML Data using XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) and [Remove XML Data using XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) topics.</span></span>  
  
### <a name="modifying-untyped-values"></a><span data-ttu-id="6c781-122">Úprava Netypové hodnoty</span><span class="sxs-lookup"><span data-stu-id="6c781-122">Modifying Untyped Values</span></span>  
 <span data-ttu-id="6c781-123"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda jednoduše vloží netypové `string` předanou jako parametr jako hodnotu uzlu <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na.</span><span class="sxs-lookup"><span data-stu-id="6c781-123">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="6c781-124">Hodnota je vložen bez jakéhokoli typu nebo bez ověření, že nová hodnota je platná pro typ uzlu, pokud je k dispozici informace o schématu.</span><span class="sxs-lookup"><span data-stu-id="6c781-124">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="6c781-125">V následujícím příkladu <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metoda se používá k aktualizaci všech `price` prvků v `contosoBooks.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="6c781-125">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="6c781-126">V příkladu přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="6c781-126">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a><span data-ttu-id="6c781-127">Úprava zadaných hodnot</span><span class="sxs-lookup"><span data-stu-id="6c781-127">Modifying Typed Values</span></span>  
 <span data-ttu-id="6c781-128">Pokud je typ uzlu W3C XML schématu jednoduché zadejte, nová hodnota vkládat stisknutím <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metoda je porovnávána s omezující vlastnosti pro jednoduchý typ. předtím, než je hodnota nastavena.</span><span class="sxs-lookup"><span data-stu-id="6c781-128">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="6c781-129">Pokud je nová hodnota není platná pro typ uzlu (například nastavíte hodnotu `-1` na element, jehož typ je `xs:positiveInteger`), je výsledkem výjimky.</span><span class="sxs-lookup"><span data-stu-id="6c781-129">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="6c781-130">V následujícím příkladu se pokusí změnit hodnotu `price` prvek první `book` prvek `contosoBooks.xml` do souboru <xref:System.DateTime> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6c781-130">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="6c781-131">Protože typ schématu XML `price` element je definován jako `xs:decimal` v `contosoBooks.xsd` souborů, v důsledku výjimky.</span><span class="sxs-lookup"><span data-stu-id="6c781-131">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
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
  
 <span data-ttu-id="6c781-132">V příkladu přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="6c781-132">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="6c781-133">Tento příklad využívá taky `contosoBooks.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="6c781-133">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a><span data-ttu-id="6c781-134">Účinky úpravy dat XML silného typu</span><span class="sxs-lookup"><span data-stu-id="6c781-134">The Effects of Editing Strongly Typed XML Data</span></span>  
 <span data-ttu-id="6c781-135"><xref:System.Xml.XPath.XPathNavigator> Třída používá W3C XML schématu jako základ pro popisující XML silného typu.</span><span class="sxs-lookup"><span data-stu-id="6c781-135">The <xref:System.Xml.XPath.XPathNavigator> class uses the W3C XML Schema as a basis for describing strongly-typed XML.</span></span> <span data-ttu-id="6c781-136">Elementy a atributy, mohou být opatřeny poznámkami s informací o typu podle ověřování podle W3C XML schématu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6c781-136">Elements and attributes can be annotated with type information based on validation against a W3C XML Schema document.</span></span> <span data-ttu-id="6c781-137">Prvky, které může obsahovat další elementy nebo atributy se nazývají komplexní typy, zatímco ty, které může obsahovat jenom textový obsah se nazývají jednoduché typy.</span><span class="sxs-lookup"><span data-stu-id="6c781-137">Elements that can contain other elements or attributes are called complex types, while those that can only contain textual content are called simple types.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c781-138">Jednoduché typy může mít pouze atributy.</span><span class="sxs-lookup"><span data-stu-id="6c781-138">Attributes can only have simple types.</span></span>  
  
 <span data-ttu-id="6c781-139">Elementu nebo atributu může být považovány za schématu platný, pokud splňuje všechna pravidla, které jsou specifické pro své definice typu.</span><span class="sxs-lookup"><span data-stu-id="6c781-139">An element or attribute can be considered to be schema-valid if it conforms to all the rules specific to its type definition.</span></span> <span data-ttu-id="6c781-140">Element, který má jednoduchý typ `xs:int` musí obsahovat číselná hodnota mezi -2147483648 a 2147483647 schématu platný.</span><span class="sxs-lookup"><span data-stu-id="6c781-140">An element that has the simple type `xs:int` has to contain a numeric value between -2147483648 and 2147483647 to be schema-valid.</span></span> <span data-ttu-id="6c781-141">U komplexních typů schématu platnosti elementu je závislá na schéma platnost jeho podřízené prvky a atributy.</span><span class="sxs-lookup"><span data-stu-id="6c781-141">For complex types, the schema-validity of the element is dependent on the schema-validity of its child elements and attributes.</span></span> <span data-ttu-id="6c781-142">Proto pokud element je platný pro jeho definice komplexní typ, všechny jeho podřízené prvky a atributy jsou platné pro jejich definice typu.</span><span class="sxs-lookup"><span data-stu-id="6c781-142">Thus if an element is valid against its complex type definition, all its child elements and attributes are valid against their type definitions.</span></span> <span data-ttu-id="6c781-143">Podobně, pokud ještě jeden z podřízených elementů nebo atributů elementu není platná před jeho definice typu, nebo má neznámý platnosti, element je také buď neplatná nebo neznámá platnosti.</span><span class="sxs-lookup"><span data-stu-id="6c781-143">Similarly, if even one of the child elements or attributes of an element is invalid against its type definition, or has an unknown validity, the element is also either invalid or of unknown validity.</span></span>  
  
 <span data-ttu-id="6c781-144">Vzhledem k tomu, že platnost elementu je závislá na platnost jeho podřízené prvky a atributy, způsobit změny buď změna platnosti elementu, pokud byla dříve platný.</span><span class="sxs-lookup"><span data-stu-id="6c781-144">Given that the validity of an element is dependent on the validity of its child elements and attributes, modifications to either result in altering the validity of the element if it was previously valid.</span></span> <span data-ttu-id="6c781-145">Konkrétně podřízené elementy nebo atributy elementu se přidají, aktualizována nebo odstraněna, pak platnosti prvek stane neznámý.</span><span class="sxs-lookup"><span data-stu-id="6c781-145">Specifically, if the child elements or attributes of an element are inserted, updated, or deleted, then the validity of the element becomes unknown.</span></span> <span data-ttu-id="6c781-146">To je reprezentována <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> vlastnost elementu, který <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnost nastavena na <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span><span class="sxs-lookup"><span data-stu-id="6c781-146">This is represented by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the element's <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property being set to <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span></span> <span data-ttu-id="6c781-147">Kromě toho tento efekt uspořádá sebe nahoru rekurzivně v dokumentu XML, protože platnost nadřazeného elementu (a jeho nadřazeného elementu a tak dále) se také stane neznámý.</span><span class="sxs-lookup"><span data-stu-id="6c781-147">Furthermore, this effect cascades upwards recursively across the XML document, because the validity of the element's parent element (and its parent element, and so on) also becomes unknown.</span></span>  
  
 <span data-ttu-id="6c781-148">Další informace o ověřování schématu a <xref:System.Xml.XPath.XPathNavigator> najdete v tématu [ověření schématu pomocí XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="6c781-148">For more information about schema validation and the <xref:System.Xml.XPath.XPathNavigator> class, see [Schema Validation using XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).</span></span>  
  
### <a name="modifying-attributes"></a><span data-ttu-id="6c781-149">Úprava atributů</span><span class="sxs-lookup"><span data-stu-id="6c781-149">Modifying Attributes</span></span>  
 <span data-ttu-id="6c781-150"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody slouží k úpravě typové a netypové atribut uzlů, jakož i jiné typy uzlů uvedených v části "Úpravy uzly".</span><span class="sxs-lookup"><span data-stu-id="6c781-150">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods can be used to modify untyped and typed attribute nodes as well as the other node types listed in the "Modifying Nodes" section.</span></span>  
  
 <span data-ttu-id="6c781-151">Následující příklad změní hodnotu `genre` atribut první `book` prvek `books.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="6c781-151">The following example changes the value of the `genre` attribute of the first `book` element in the `books.xml` file.</span></span>  
  
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
  
 <span data-ttu-id="6c781-152">Další informace o <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody, naleznete v částech "Úpravy Netypové hodnoty" a "Úprava zadané hodnoty".</span><span class="sxs-lookup"><span data-stu-id="6c781-152">For more information about the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods, see the "Modifying Untyped Values" and "Modifying Typed Values" sections.</span></span>  
  
## <a name="innerxml-and-outerxml-properties"></a><span data-ttu-id="6c781-153">InnerXml a OuterXml vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6c781-153">InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="6c781-154"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy změnit kód XML uzlů <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na.</span><span class="sxs-lookup"><span data-stu-id="6c781-154">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="6c781-155"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Vlastnost se změní kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na s analyzovaný obsah XML daného `string`.</span><span class="sxs-lookup"><span data-stu-id="6c781-155">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="6c781-156">Podobně <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnost se změní kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na i samotný uzel aktuální.</span><span class="sxs-lookup"><span data-stu-id="6c781-156">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="6c781-157">V následujícím příkladu <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnost na hodnotu změnit `price` elementu a vložit nový `discount` atribut na první `book` prvek v `contosoBooks.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="6c781-157">The following example uses the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property to modify the value of the `price` element and insert a new `discount` attribute on the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
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
  
 <span data-ttu-id="6c781-158">V příkladu přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="6c781-158">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a><span data-ttu-id="6c781-159">Úprava uzlů Namespace</span><span class="sxs-lookup"><span data-stu-id="6c781-159">Modifying Namespace Nodes</span></span>  
 <span data-ttu-id="6c781-160">V Document Object Model (DOM), deklarace oboru názvů jsou považovány, jako by šlo regulární atributy, které lze vložit, aktualizovat a odstranit.</span><span class="sxs-lookup"><span data-stu-id="6c781-160">In the Document Object Model (DOM), namespace declarations are treated as if they are regular attributes that can be inserted, updated and deleted.</span></span> <span data-ttu-id="6c781-161"><xref:System.Xml.XPath.XPathNavigator> Třídy nepovoluje tyto operace na uzly oboru názvů, protože změna hodnota uzlu oboru názvů můžete změnit identitu této elementů a atributů v rámci oboru uzel oboru názvů, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6c781-161">The <xref:System.Xml.XPath.XPathNavigator> class does not allow such operations on namespace nodes because altering the value of a namespace node can change the identity of the elements and attributes within the scope of the namespace node as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="6c781-162">Pokud se výše uvedený příklad XML změní následujícím způsobem, to každý prvek v dokumentu efektivně přejmenuje, vzhledem k tomu, že se změní hodnota identifikátoru URI oboru názvů každý prvek.</span><span class="sxs-lookup"><span data-stu-id="6c781-162">If the XML example above is changed in the following way, this effectively renames every element in the document because the value of each element's namespace URI is changed.</span></span>  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="6c781-163">Vkládání uzly oboru názvů, které nejsou v konfliktu s deklarací oboru názvů v oboru, který se vloží do povoluje <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="6c781-163">Inserting namespace nodes that do not conflict with namespace declarations at the scope that they are inserted in is allowed by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="6c781-164">Deklarace oboru názvů v tomto případě nejsou deklarovány na nižší obory v dokumentu XML a nemá za následek přejmenování, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6c781-164">In this case, the namespace declarations are not declared at lower scopes in the XML document and does not result in renaming as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="6c781-165">Pokud výše uvedený příklad XML se změní následujícím způsobem, deklarace oboru názvů se rozšíří správně v následujícím oboru dalších deklarace oboru názvů dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="6c781-165">If the XML example above is changed in the following way, the namespace declarations are correctly propagated across the XML document below the scope of the other namespace declaration.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/">  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="6c781-166">V příkladu XML výše, atribut `a:parent-id` disku do mechaniky na `parent` prvek `http://www.contoso.com/parent-id` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6c781-166">In the XML example above, the attribute `a:parent-id` is inserted on the `parent` element in the `http://www.contoso.com/parent-id` namespace.</span></span> <span data-ttu-id="6c781-167"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Metody slouží k vložení Přestože umístěn na atribut `parent` elementu.</span><span class="sxs-lookup"><span data-stu-id="6c781-167">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method is used to insert the attribute while positioned on the `parent` element.</span></span> <span data-ttu-id="6c781-168">`http://www.contoso.com` Deklarace oboru názvů se automaticky vložit <xref:System.Xml.XPath.XPathNavigator> třídy pro zachování konzistence zbývající části dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="6c781-168">The `http://www.contoso.com` namespace declaration is automatically inserted by the <xref:System.Xml.XPath.XPathNavigator> class to preserve the consistency of the rest of the XML document.</span></span>  
  
## <a name="modifying-entity-reference-nodes"></a><span data-ttu-id="6c781-169">Úprava uzlů odkaz na entitu</span><span class="sxs-lookup"><span data-stu-id="6c781-169">Modifying Entity Reference Nodes</span></span>  
 <span data-ttu-id="6c781-170">Uzly odkaz na entitu v <xref:System.Xml.XmlDocument> objektu jsou jen pro čtení a nejde upravovat pomocí buď <xref:System.Xml.XPath.XPathNavigator> nebo <xref:System.Xml.XmlNode> třídy.</span><span class="sxs-lookup"><span data-stu-id="6c781-170">Entity reference nodes in an <xref:System.Xml.XmlDocument> object are read-only and cannot be edited using either the <xref:System.Xml.XPath.XPathNavigator> or <xref:System.Xml.XmlNode> classes.</span></span> <span data-ttu-id="6c781-171">Výsledkem jakýkoliv pokus upravit uzlu odkazu entity <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="6c781-171">Any attempt to modify an entity reference node results in an <xref:System.InvalidOperationException>.</span></span>  
  
## <a name="modifying-xsinil-nodes"></a><span data-ttu-id="6c781-172">Úprava xsi: nil uzly</span><span class="sxs-lookup"><span data-stu-id="6c781-172">Modifying xsi:nil Nodes</span></span>  
 <span data-ttu-id="6c781-173">Doporučení W3C XML schématu zavádí koncepci element je nepovinné.</span><span class="sxs-lookup"><span data-stu-id="6c781-173">The W3C XML Schema recommendation introduces the concept of an element being nillable.</span></span> <span data-ttu-id="6c781-174">Pokud element je nepovinné, je možné pro element nemají žádný obsah a stále platit.</span><span class="sxs-lookup"><span data-stu-id="6c781-174">When an element is nillable, it is possible for the element to have no content and still be valid.</span></span> <span data-ttu-id="6c781-175">Je podobný koncept objektu se koncept element je nepovinné `null`.</span><span class="sxs-lookup"><span data-stu-id="6c781-175">The concept of an element being nillable is similar to the concept of an object being `null`.</span></span> <span data-ttu-id="6c781-176">Hlavní rozdíl je, že `null` objekt nelze získat přístup k žádným způsobem, zatímco `xsi:nil` element stále má vlastnosti, jako jsou atributy, které lze získat přístup, ale nemá žádný obsah (podřízené elementy nebo text).</span><span class="sxs-lookup"><span data-stu-id="6c781-176">The main difference is that a `null` object cannot be accessed in any way, while an `xsi:nil` element still has properties such as attributes that can be accessed, but has no content (child elements or text).</span></span> <span data-ttu-id="6c781-177">Existence `xsi:nil` atributu s hodnotou `true` v elementu ve formátu XML dokumentu se používá k označení, že element nemá žádný obsah.</span><span class="sxs-lookup"><span data-stu-id="6c781-177">The existence of the `xsi:nil` attribute with a value of `true` on an element in an XML document is used to indicate that an element has no content.</span></span>  
  
 <span data-ttu-id="6c781-178">Pokud <xref:System.Xml.XPath.XPathNavigator> objektu se používá k přidání obsahu na platný element s `xsi:nil` atributu s hodnotou `true`, hodnota jeho `xsi:nil` atribut je nastaven na `false`.</span><span class="sxs-lookup"><span data-stu-id="6c781-178">If an <xref:System.Xml.XPath.XPathNavigator> object is used to add content to a valid element with an `xsi:nil` attribute with a value of `true`, the value of its `xsi:nil` attribute is set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c781-179">Pokud obsah elementu se `xsi:nil` atribut nastaven na `false` je odstraněn, hodnota atributu se nezmění na `true`.</span><span class="sxs-lookup"><span data-stu-id="6c781-179">If the content of an element with an `xsi:nil` attribute set to `false` is deleted, the value of the attribute is not changed to `true`.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="6c781-180">Uložení dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="6c781-180">Saving an XML Document</span></span>  
 <span data-ttu-id="6c781-181">Ukládají se změny provedené <xref:System.Xml.XmlDocument> jak výsledky úprav metod popsaných v tomto tématu se provádí pomocí metody <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="6c781-181">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the editing methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="6c781-182">Další informace o uložení změny <xref:System.Xml.XmlDocument> objektu, najdete v článku [ukládání a zápis dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="6c781-182">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c781-183">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c781-183">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="6c781-184">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="6c781-184">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="6c781-185">Vložení dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="6c781-185">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="6c781-186">Odebrání dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="6c781-186">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)

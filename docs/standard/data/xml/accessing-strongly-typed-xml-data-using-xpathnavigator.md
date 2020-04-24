---
title: Přístup k datům XML silného typu pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
ms.openlocfilehash: e6ec30e3c7c2318b199122cd63c7f56584707a98
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78158048"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a><span data-ttu-id="cae18-102">Přístup k datům XML silného typu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="cae18-102">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>
<span data-ttu-id="cae18-103">Jako instance datového modelu XPath 2,0 může <xref:System.Xml.XPath.XPathNavigator> třída obsahovat data silného typu, která se mapují na typy modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="cae18-103">As an instance of the XPath 2.0 data model, the <xref:System.Xml.XPath.XPathNavigator> class can contain strongly-typed data that maps to common language runtime (CLR) types.</span></span> <span data-ttu-id="cae18-104">V souladu s datovým modelem XPath 2,0 mohou obsahovat pouze elementy a atributy data silného typu.</span><span class="sxs-lookup"><span data-stu-id="cae18-104">According to the XPath 2.0 data model, only elements and attributes can contain strongly-typed data.</span></span> <span data-ttu-id="cae18-105"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje mechanismy pro přístup k datům v rámci <xref:System.Xml.XPath.XPathDocument> objektu <xref:System.Xml.XmlDocument> nebo jako data silného typu a mechanismy pro převod z jednoho datového typu na jiný.</span><span class="sxs-lookup"><span data-stu-id="cae18-105">The <xref:System.Xml.XPath.XPathNavigator> class provides mechanisms for accessing data within an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object as strongly-typed data as well as mechanisms for converting from one data type to another.</span></span>  
  
## <a name="type-information-exposed-by-xpathnavigator"></a><span data-ttu-id="cae18-106">Informace o typech vystavených pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="cae18-106">Type Information Exposed by XPathNavigator</span></span>  
 <span data-ttu-id="cae18-107">Data XML 1,0 jsou technicky bez typu, pokud se nezpracovávají pomocí DTD, schématu definice jazyka XML (XSD) nebo jiného mechanismu.</span><span class="sxs-lookup"><span data-stu-id="cae18-107">XML 1.0 data is technically without type, unless processed with a DTD, XML schema definition language (XSD) schema, or other mechanism.</span></span> <span data-ttu-id="cae18-108">Existuje několik kategorií typů informací, které mohou být přidruženy k elementu nebo atributu XML.</span><span class="sxs-lookup"><span data-stu-id="cae18-108">There are a number of categories of type information that can be associated with an XML element or attribute.</span></span>  
  
- <span data-ttu-id="cae18-109">Jednoduché typy CLR: žádné jazyky schématu XML nepodporují přímo typy modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="cae18-109">Simple CLR Types: None of the XML Schema languages support Common Language Runtime (CLR) types directly.</span></span> <span data-ttu-id="cae18-110">Vzhledem k tomu, že je vhodné, aby bylo možné zobrazit jednoduchý element a obsah atributu jako nejvhodnější typ CLR, lze veškerý jednoduchý obsah zadat jako <xref:System.String> v případě nepřítomnosti informací o schématu pomocí jakýchkoli přidaných informací o schématu, který potenciálně může tento obsah snadno použít pro přesnější typ.</span><span class="sxs-lookup"><span data-stu-id="cae18-110">Because it is useful to be able to view simple element and attribute content as the most appropriate CLR type, all simple content can be typed as <xref:System.String> in the absence of schema information with any added schema information potentially refining this content to a more appropriate type.</span></span> <span data-ttu-id="cae18-111">Můžete najít nejlépe vyhovující typ CLR jednoduchého prvku a obsahu atributu pomocí <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cae18-111">You can find the best matching CLR type of simple element and attribute content by using the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property.</span></span> <span data-ttu-id="cae18-112">Další informace o mapování z vestavěných typů schématu na typy CLR naleznete v tématu [Podpora typů v třídách System. XML](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="cae18-112">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="cae18-113">Seznamy jednoduchých typů (CLR): element nebo atribut s jednoduchým obsahem může obsahovat seznam hodnot oddělených prázdným znakem.</span><span class="sxs-lookup"><span data-stu-id="cae18-113">Lists of Simple (CLR) Types: An element or attribute with simple content can contain a list of values separated by white space.</span></span> <span data-ttu-id="cae18-114">Hodnoty jsou určeny schématem XML jako "typ seznamu".</span><span class="sxs-lookup"><span data-stu-id="cae18-114">The values are specified by an XML Schema to be a "list type."</span></span> <span data-ttu-id="cae18-115">V případě absence schématu XML by takový jednoduchý obsah byl považován za jediný textový uzel.</span><span class="sxs-lookup"><span data-stu-id="cae18-115">In the absence of an XML Schema, such simple content would be treated as a single text node.</span></span> <span data-ttu-id="cae18-116">Pokud je k dispozici schéma XML, tento jednoduchý obsah může být vystaven jako řada atomických hodnot, z nichž každý má jednoduchý typ, který se mapuje na kolekci objektů CLR.</span><span class="sxs-lookup"><span data-stu-id="cae18-116">When an XML Schema is available, this simple content can be exposed as a series of atomic values each having a simple type that maps to a collection of CLR objects.</span></span> <span data-ttu-id="cae18-117">Další informace o mapování z vestavěných typů schématu na typy CLR naleznete v tématu [Podpora typů v třídách System. XML](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="cae18-117">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="cae18-118">Zadaná hodnota: atribut, který je ověřený schématem nebo element s jednoduchým typem, má zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cae18-118">Typed Value: A schema-validated attribute or element with a simple type has a typed value.</span></span> <span data-ttu-id="cae18-119">Tato hodnota je primitivního typu, jako je číselná hodnota, řetězec nebo typ data.</span><span class="sxs-lookup"><span data-stu-id="cae18-119">This value is a primitive type such as a numeric, string, or date type.</span></span> <span data-ttu-id="cae18-120">Všechny předdefinované jednoduché typy v XSD lze namapovat na typy CLR, které poskytují přístup k hodnotě uzlu jako vhodnější typ místo pouze jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="cae18-120">All the built-in simple types in XSD can be mapped to CLR types that provide access to the value of a node as a more appropriate type instead of just as a <xref:System.String>.</span></span> <span data-ttu-id="cae18-121">Element s atributy nebo podřízenými prvky je považován za komplexní typ.</span><span class="sxs-lookup"><span data-stu-id="cae18-121">An element with attributes or element children is considered to be a complex type.</span></span> <span data-ttu-id="cae18-122">Zadaná hodnota komplexního typu s jednoduchým obsahem (pouze textové uzly jako podřízené položky) je stejná jako u jednoduchého typu jejího obsahu.</span><span class="sxs-lookup"><span data-stu-id="cae18-122">The typed value of a complex type with simple content (only text nodes as children) is the same as that of the simple type of its content.</span></span> <span data-ttu-id="cae18-123">Zadaná hodnota komplexního typu se složitým obsahem (jeden nebo více podřízených elementů) je řetězcová hodnota zřetězení všech podřízených textových uzlů vrácených jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="cae18-123">The typed value of a complex type with complex content (one or more child elements) is the string value of the concatenation of all its child text nodes returned as a <xref:System.String>.</span></span> <span data-ttu-id="cae18-124">Další informace o mapování z vestavěných typů schématu na typy CLR naleznete v tématu [Podpora typů v třídách System. XML](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="cae18-124">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="cae18-125">Název typu specifického pro jazyk schématu: ve většině případů jsou typy CLR, které jsou nastaveny jako vedlejší účinky použití externího schématu, použity k poskytnutí přístupu k hodnotě uzlu.</span><span class="sxs-lookup"><span data-stu-id="cae18-125">Schema-Language Specific Type Name: In most cases, the CLR types, which are set as a side-effect of applying an external schema, are used to provide access to the value of a node.</span></span> <span data-ttu-id="cae18-126">Mohou však nastat situace, kdy budete chtít prostudovat typ přidružený ke konkrétnímu schématu použitému pro dokument XML.</span><span class="sxs-lookup"><span data-stu-id="cae18-126">However, there may be situations where you may want to examine the type associated with a particular schema applied to an XML document.</span></span> <span data-ttu-id="cae18-127">Například můžete chtít Hledat v dokumentu XML a extrahovat všechny prvky, které jsou určeny tak, aby měly obsah typu "PurchaseOrder" podle připojeného schématu.</span><span class="sxs-lookup"><span data-stu-id="cae18-127">For example, you may wish to search through an XML document, extracting all elements that are determined to have content of type "PurchaseOrder" according to an attached schema.</span></span> <span data-ttu-id="cae18-128">Tyto informace o typu lze nastavit pouze v důsledku ověřování schématu a k těmto informacím jsou přistupované prostřednictvím <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> vlastností <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> a <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="cae18-128">Such type information can be set only as a result of schema validation and this information is accessed through the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> and <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="cae18-129">Další informace najdete níže v části post PSVI (podrobnějšího ověření schématu).</span><span class="sxs-lookup"><span data-stu-id="cae18-129">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
- <span data-ttu-id="cae18-130">Odraz typu specifického pro jazyk schématu: v jiných případech můžete chtít získat další podrobnosti o typu specifického pro schéma, který se použije pro dokument XML.</span><span class="sxs-lookup"><span data-stu-id="cae18-130">Schema-Language Specific Type Reflection: In other cases, you may want to obtain further details of the schema-specific type applied to an XML document.</span></span> <span data-ttu-id="cae18-131">Například při čtení souboru XML může být vhodné extrahovat `maxOccurs` atribut pro každý platný uzel v dokumentu XML, aby bylo možné provést nějaký vlastní výpočet.</span><span class="sxs-lookup"><span data-stu-id="cae18-131">For example, when reading an XML file, you may want to extract the `maxOccurs` attribute for each valid node in the XML document in order to perform some custom calculation.</span></span> <span data-ttu-id="cae18-132">Vzhledem k tomu, že tyto informace jsou nastaveny pouze pomocí ověřování schématu, jsou <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> k ní přistupované prostřednictvím vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="cae18-132">Because this information is set only through schema validation, it is accessed through the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="cae18-133">Další informace najdete níže v části post PSVI (podrobnějšího ověření schématu).</span><span class="sxs-lookup"><span data-stu-id="cae18-133">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
## <a name="xpathnavigator-typed-accessors"></a><span data-ttu-id="cae18-134">Přistupující objekty XPathNavigator typovaného typu</span><span class="sxs-lookup"><span data-stu-id="cae18-134">XPathNavigator Typed Accessors</span></span>  
 <span data-ttu-id="cae18-135">V následující tabulce jsou uvedeny různé vlastnosti a metody <xref:System.Xml.XPath.XPathNavigator> třídy, které lze použít pro přístup k informacím o typu uzlu.</span><span class="sxs-lookup"><span data-stu-id="cae18-135">The following table shows the various properties and methods of the <xref:System.Xml.XPath.XPathNavigator> class that can be used to access the type information about a node.</span></span>  
  
|<span data-ttu-id="cae18-136">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="cae18-136">Property</span></span>|<span data-ttu-id="cae18-137">Popis</span><span class="sxs-lookup"><span data-stu-id="cae18-137">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|<span data-ttu-id="cae18-138">Obsahuje informace o typu schématu XML pro uzel, pokud je platný.</span><span class="sxs-lookup"><span data-stu-id="cae18-138">This contains the XML schema type information for the node if it is valid.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|<span data-ttu-id="cae18-139">Obsahuje informační sadu po ověření schématu uzlu, který se přidá po ověření.</span><span class="sxs-lookup"><span data-stu-id="cae18-139">This contains the Post Schema Validation Infoset of the node that is added after validation.</span></span> <span data-ttu-id="cae18-140">To zahrnuje informace o typu schématu XML a také informace o platnosti.</span><span class="sxs-lookup"><span data-stu-id="cae18-140">This includes the XML schema type information, as well as validity information.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|<span data-ttu-id="cae18-141">Typ CLR typové hodnoty uzlu.</span><span class="sxs-lookup"><span data-stu-id="cae18-141">The CLR type of the typed value of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|<span data-ttu-id="cae18-142">Obsah uzlu jako jednu nebo více hodnot CLR, jejichž typ je co nejblíže typu schématu XML uzlu.</span><span class="sxs-lookup"><span data-stu-id="cae18-142">The content of the node as one or more CLR values whose type is the closest match to the XML schema type of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<span data-ttu-id="cae18-143"><xref:System.String> Hodnota aktuálního uzlu přetypování na <xref:System.Boolean> hodnotu podle pravidel přetypování XPath 2,0 pro `xs:boolean`.</span><span class="sxs-lookup"><span data-stu-id="cae18-143">The <xref:System.String> value of the current node cast to a <xref:System.Boolean> value, according to the XPath 2.0 casting rules for `xs:boolean`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<span data-ttu-id="cae18-144"><xref:System.String> Hodnota aktuálního uzlu přetypování na <xref:System.DateTime> hodnotu podle pravidel přetypování XPath 2,0 pro `xs:datetime`.</span><span class="sxs-lookup"><span data-stu-id="cae18-144">The <xref:System.String> value of the current node cast to a <xref:System.DateTime> value, according to the XPath 2.0 casting rules for `xs:datetime`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<span data-ttu-id="cae18-145"><xref:System.String> Hodnota aktuálního uzlu přetypování na <xref:System.Double> hodnotu podle pravidel přetypování XPath 2,0 pro `xsd:double`.</span><span class="sxs-lookup"><span data-stu-id="cae18-145">The <xref:System.String> value of the current node cast to a <xref:System.Double> value, according to the XPath 2.0 casting rules for `xsd:double`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<span data-ttu-id="cae18-146"><xref:System.String> Hodnota aktuálního uzlu přetypování na <xref:System.Int32> hodnotu podle pravidel přetypování XPath 2,0 pro `xs:integer`.</span><span class="sxs-lookup"><span data-stu-id="cae18-146">The <xref:System.String> value of the current node cast to a <xref:System.Int32> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<span data-ttu-id="cae18-147"><xref:System.String> Hodnota aktuálního uzlu přetypování na <xref:System.Int64> hodnotu podle pravidel přetypování XPath 2,0 pro `xs:integer`.</span><span class="sxs-lookup"><span data-stu-id="cae18-147">The <xref:System.String> value of the current node cast to a <xref:System.Int64> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|<span data-ttu-id="cae18-148">Obsah přetypování uzlu na cílový typ podle pravidel přetypování XPath 2,0.</span><span class="sxs-lookup"><span data-stu-id="cae18-148">The contents of the node cast to the target type according to the XPath 2.0 casting rules.</span></span>|  
  
 <span data-ttu-id="cae18-149">Další informace o mapování z vestavěných typů schématu na typy CLR naleznete v tématu [Podpora typů v třídách System. XML](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="cae18-149">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="the-post-schema-validation-infoset-psvi"></a><span data-ttu-id="cae18-150">Informační sada po ověření schématu (PSVI)</span><span class="sxs-lookup"><span data-stu-id="cae18-150">The Post Schema Validation Infoset (PSVI)</span></span>  
 <span data-ttu-id="cae18-151">Procesor schématu XML přijímá jako vstup XML informační sadu a převede je do informační sady po ověření schématu (PSVI).</span><span class="sxs-lookup"><span data-stu-id="cae18-151">An XML Schema processor accepts an XML Infoset as input and converts it into a Post Schema Validation Infoset (PSVI).</span></span> <span data-ttu-id="cae18-152">PSVI je původní vstupní informační sada XML s přidanými novými informacemi a novými vlastnostmi přidanými k existujícím položkám informací.</span><span class="sxs-lookup"><span data-stu-id="cae18-152">A PSVI is the original input XML infoset with new information items added and new properties added to existing information items.</span></span> <span data-ttu-id="cae18-153">Do informační sady XML v PSVI jsou přidány tři široké třídy informací, které jsou zpřístupněny v <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="cae18-153">There are three broad classes of information added to the XML Infoset in the PSVI that are exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
1. <span data-ttu-id="cae18-154">Výsledky ověření: informace o tom, zda byl prvek nebo atribut úspěšně ověřen nebo nikoli.</span><span class="sxs-lookup"><span data-stu-id="cae18-154">Validation Outcomes: Information as to whether an element or attribute was successfully validated or not.</span></span> <span data-ttu-id="cae18-155">Tato <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> vlastnost je vystavena vlastností <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="cae18-155">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
2. <span data-ttu-id="cae18-156">Výchozí informace: označení, zda byla hodnota elementu nebo atributu získána prostřednictvím výchozích hodnot zadaných ve schématu nebo nikoli.</span><span class="sxs-lookup"><span data-stu-id="cae18-156">Default Information: Indications as to whether the value of the element or attribute was obtained via default values specified in the schema or not.</span></span> <span data-ttu-id="cae18-157">Tato <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> vlastnost je vystavena vlastností <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="cae18-157">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
3. <span data-ttu-id="cae18-158">Anotace typu: odkazy na komponenty schématu, které mohou být definice typu nebo deklarace element a atributu.</span><span class="sxs-lookup"><span data-stu-id="cae18-158">Type Annotations: References to schema components that may be type definitions or element and attribute declarations.</span></span> <span data-ttu-id="cae18-159"><xref:System.Xml.XPath.XPathNavigator.XmlType%2A> Vlastnost <xref:System.Xml.XPath.XPathNavigator> obsahuje konkrétní informace o typu uzlu, pokud je platný.</span><span class="sxs-lookup"><span data-stu-id="cae18-159">The <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property of the <xref:System.Xml.XPath.XPathNavigator> contains the specific type information of the node if it is valid.</span></span> <span data-ttu-id="cae18-160">Pokud je platnost uzlu neznámá, například při ověření, následně upraveno.</span><span class="sxs-lookup"><span data-stu-id="cae18-160">If the validity of a node is unknown, such as when it was validated then subsequently edited.</span></span> <span data-ttu-id="cae18-161">pak je <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> vlastnost nastavena na, `null` ale informace o typu jsou stále k dispozici z různých vlastností <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="cae18-161">then the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property is set to `null` but type information is still available from the various properties of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="cae18-162">Následující příklad znázorňuje použití informací v informačním okně po ověření schématu vystaveném pomocí <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="cae18-162">The following example illustrates using information in the Post Schema Validation Infoset exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("books.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("published", "http://www.contoso.com/books")  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name)  
Console.WriteLine(navigator.SchemaInfo.Validity)  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("books.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("published", "http://www.contoso.com/books");  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name);  
Console.WriteLine(navigator.SchemaInfo.Validity);  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs);  
```  
  
 <span data-ttu-id="cae18-163">Příklad přebírá `books.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="cae18-163">The example takes the `books.xml` file as input.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="cae18-164">Příklad také převezme `books.xsd` schéma jako vstup.</span><span class="sxs-lookup"><span data-stu-id="cae18-164">The example also takes the `books.xsd` schema as input.</span></span>  
  
```xml  
<xs:schema xmlns="http://www.contoso.com/books"
attributeFormDefault="unqualified" elementFormDefault="qualified"
targetNamespace="http://www.contoso.com/books"
xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="publishedType">  
        <xs:restriction base="xs:date">  
            <xs:minInclusive value="2003-01-01" />  
            <xs:maxInclusive value="2003-12-31" />  
        </xs:restriction>  
    </xs:simpleType>  
    <xs:complexType name="bookType">  
        <xs:sequence>  
            <xs:element name="title" type="xs:string"/>  
            <xs:element name="price" type="xs:decimal"/>  
            <xs:element name="published" type="publishedType"/>  
        </xs:sequence>  
    </xs:complexType>  
    <xs:complexType name="booksType">  
        <xs:sequence>  
            <xs:element name="book" type="bookType" />  
        </xs:sequence>  
    </xs:complexType>  
    <xs:element name="books" type="booksType" />  
</xs:schema>  
```  
  
## <a name="obtain-typed-values-using-valueas-properties"></a><span data-ttu-id="cae18-165">Získání typových hodnot pomocí vlastností ValueAs</span><span class="sxs-lookup"><span data-stu-id="cae18-165">Obtain Typed Values Using ValueAs Properties</span></span>  
 <span data-ttu-id="cae18-166">Zadanou hodnotu uzlu lze načíst přístupem k <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> vlastnosti. <xref:System.Xml.XPath.XPathNavigator></span><span class="sxs-lookup"><span data-stu-id="cae18-166">The typed value of a node can be retrieved by accessing the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="cae18-167">V některých případech je vhodné převést typovou hodnotu uzlu na jiný typ.</span><span class="sxs-lookup"><span data-stu-id="cae18-167">In certain cases you may want to convert the typed value of a node to a different type.</span></span> <span data-ttu-id="cae18-168">Běžným příkladem je získání číselné hodnoty z uzlu XML.</span><span class="sxs-lookup"><span data-stu-id="cae18-168">A common example is to get a numeric value from an XML node.</span></span> <span data-ttu-id="cae18-169">Zvažte například následující neověřený a Netypový dokument XML.</span><span class="sxs-lookup"><span data-stu-id="cae18-169">For example, consider the following unvalidated and untyped XML document.</span></span>  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="cae18-170">Pokud <xref:System.Xml.XPath.XPathNavigator> `price` je umístěn na elementu, <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> vlastnost `null` <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> <xref:System.String>by měla být a <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> vlastnost by měla být řetězec. `10.00`</span><span class="sxs-lookup"><span data-stu-id="cae18-170">If the <xref:System.Xml.XPath.XPathNavigator> is positioned on the `price` element the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property would be `null`, the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property would be <xref:System.String>, and the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property would be the string `10.00`.</span></span>  
  
 <span data-ttu-id="cae18-171">Je však možné i nadále extrahovat hodnotu jako číselnou hodnotu pomocí <xref:System.Xml.XPath.XPathItem.ValueAs%2A>metod, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>nebo <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> a vlastností.</span><span class="sxs-lookup"><span data-stu-id="cae18-171">However, it is still possible to extract the value as a numeric value using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, or <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> method and properties.</span></span> <span data-ttu-id="cae18-172">Následující příklad ilustruje provádění takového přetypování pomocí <xref:System.Xml.XPath.XPathItem.ValueAs%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cae18-172">The following example illustrates performing such a cast using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A> method.</span></span>  
  
```vb  
Dim document As New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "")  
navigator.MoveToChild("book", "")  
navigator.MoveToChild("price", "")  
  
Dim price = navigator.ValueAs(GetType(Decimal))  
Dim discount As Decimal = 0.2  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * discount))  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "");  
navigator.MoveToChild("book", "");  
navigator.MoveToChild("price", "");  
  
Decimal price = (decimal)navigator.ValueAs(typeof(decimal));  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * (decimal)0.20));  
```  
  
 <span data-ttu-id="cae18-173">Další informace o mapování z vestavěných typů schématu na typy CLR naleznete v tématu [Podpora typů v třídách System. XML](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="cae18-173">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cae18-174">Viz také</span><span class="sxs-lookup"><span data-stu-id="cae18-174">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="cae18-175">Podpora typu v třídách System.Xml</span><span class="sxs-lookup"><span data-stu-id="cae18-175">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
- [<span data-ttu-id="cae18-176">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="cae18-176">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="cae18-177">Navigace v sadě uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="cae18-177">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="cae18-178">Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="cae18-178">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="cae18-179">Extrahování dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="cae18-179">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)

---
title: Přístup k datům XML silného typu pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1905e9f1d80931bd15cff5f3d0a92ceee29435ef
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59319882"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a><span data-ttu-id="a840c-102">Přístup k datům XML silného typu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a840c-102">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>
<span data-ttu-id="a840c-103">Jako instanci datového modelu, XPath 2.0 <xref:System.Xml.XPath.XPathNavigator> třídy mohou obsahovat silného typu dat, která se mapuje na common language runtime (CLR) typy.</span><span class="sxs-lookup"><span data-stu-id="a840c-103">As an instance of the XPath 2.0 data model, the <xref:System.Xml.XPath.XPathNavigator> class can contain strongly-typed data that maps to common language runtime (CLR) types.</span></span> <span data-ttu-id="a840c-104">Podle modelu dat XPath 2.0 může obsahovat pouze prvky a atributy dat silného typu.</span><span class="sxs-lookup"><span data-stu-id="a840c-104">According to the XPath 2.0 data model, only elements and attributes can contain strongly-typed data.</span></span> <span data-ttu-id="a840c-105"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje mechanismus pro přístup k datům v rámci <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> jako silného typu dat, stejně jako mechanismus pro převod z jednoho datového typu na jiný objekt.</span><span class="sxs-lookup"><span data-stu-id="a840c-105">The <xref:System.Xml.XPath.XPathNavigator> class provides mechanisms for accessing data within an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object as strongly-typed data as well as mechanisms for converting from one data type to another.</span></span>  
  
## <a name="type-information-exposed-by-xpathnavigator"></a><span data-ttu-id="a840c-106">Informace o typu vystavené objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="a840c-106">Type Information Exposed by XPathNavigator</span></span>  
 <span data-ttu-id="a840c-107">Data XML 1.0 je technicky bez typu, pokud zpracovává se DTD, XML definice jazyk (XSD) schématu nebo jinému kontrolnímu mechanismu.</span><span class="sxs-lookup"><span data-stu-id="a840c-107">XML 1.0 data is technically without type, unless processed with a DTD, XML schema definition language (XSD) schema, or other mechanism.</span></span> <span data-ttu-id="a840c-108">Existuje mnoho kategorií informací o typu, který může být přidružen k elementu XML nebo atributu.</span><span class="sxs-lookup"><span data-stu-id="a840c-108">There are a number of categories of type information that can be associated with an XML element or attribute.</span></span>  
  
-   <span data-ttu-id="a840c-109">Typy CLR jednoduchý: Žádný z těchto jazyků schématu XML nepodporuje typy Common Language Runtime (CLR) přímo.</span><span class="sxs-lookup"><span data-stu-id="a840c-109">Simple CLR Types: None of the XML Schema languages support Common Language Runtime (CLR) types directly.</span></span> <span data-ttu-id="a840c-110">Protože je výhodné mít možnost zobrazit jednoduchý prvek a obsah atributů jako nejvhodnější typ CLR, všechny jednoduchý obsah lze zadat jako <xref:System.String> chybí informace o schématu s žádným přidány informace o schématu potenciálně upřesnění tento obsah více příslušného typu.</span><span class="sxs-lookup"><span data-stu-id="a840c-110">Because it is useful to be able to view simple element and attribute content as the most appropriate CLR type, all simple content can be typed as <xref:System.String> in the absence of schema information with any added schema information potentially refining this content to a more appropriate type.</span></span> <span data-ttu-id="a840c-111">Můžete najít nejvhodnější typ CLR jednoduchý obsah elementu a atribut s použitím <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a840c-111">You can find the best matching CLR type of simple element and attribute content by using the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property.</span></span> <span data-ttu-id="a840c-112">Další informace o mapování z předdefinovaných typů schématu pro typy CLR naleznete v tématu [podpora typu v třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="a840c-112">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
-   <span data-ttu-id="a840c-113">Seznam typů jednoduché (CLR): Prvek nebo atribut s jednoduchým obsahem může obsahovat seznam hodnoty oddělené symbolem mezery.</span><span class="sxs-lookup"><span data-stu-id="a840c-113">Lists of Simple (CLR) Types: An element or attribute with simple content can contain a list of values separated by white space.</span></span> <span data-ttu-id="a840c-114">Hodnoty jsou určena pomocí schématu XML jako "typ seznamu".</span><span class="sxs-lookup"><span data-stu-id="a840c-114">The values are specified by an XML Schema to be a "list type."</span></span> <span data-ttu-id="a840c-115">Chybí schématu XML budou považované za jeden textový uzel takové jednoduchý obsah.</span><span class="sxs-lookup"><span data-stu-id="a840c-115">In the absence of an XML Schema, such simple content would be treated as a single text node.</span></span> <span data-ttu-id="a840c-116">Pokud schéma XML je k dispozici, může být tento jednoduchý obsah vystavena jako hodnoty řadu atomických, každý s jednoduchý typ, který se mapuje na kolekci objektů CLR.</span><span class="sxs-lookup"><span data-stu-id="a840c-116">When an XML Schema is available, this simple content can be exposed as a series of atomic values each having a simple type that maps to a collection of CLR objects.</span></span> <span data-ttu-id="a840c-117">Další informace o mapování z předdefinovaných typů schématu pro typy CLR naleznete v tématu [podpora typu v třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="a840c-117">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
-   <span data-ttu-id="a840c-118">Zadaná hodnota: Ověření schématu atribut nebo element s jednoduchý typ má zadanou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="a840c-118">Typed Value: A schema-validated attribute or element with a simple type has a typed value.</span></span> <span data-ttu-id="a840c-119">Tato hodnota je primitivní typ, jako je například číselná, řetězec nebo typ date.</span><span class="sxs-lookup"><span data-stu-id="a840c-119">This value is a primitive type such as a numeric, string, or date type.</span></span> <span data-ttu-id="a840c-120">Všechny integrované jednoduché typy v XSD je možné mapovat na typy CLR, které poskytují přístup k hodnotě uzel jako vhodnější typ namísto pouze jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a840c-120">All the built-in simple types in XSD can be mapped to CLR types that provide access to the value of a node as a more appropriate type instead of just as a <xref:System.String>.</span></span> <span data-ttu-id="a840c-121">Element s atributy nebo podřízené položky elementu se považuje za komplexní.</span><span class="sxs-lookup"><span data-stu-id="a840c-121">An element with attributes or element children is considered to be a complex type.</span></span> <span data-ttu-id="a840c-122">Zadaná hodnota komplexní typ s jednoduchým obsahem (pouze textové uzly jako podřízené objekty) je stejné jako u jednoduchého typu jeho obsahu.</span><span class="sxs-lookup"><span data-stu-id="a840c-122">The typed value of a complex type with simple content (only text nodes as children) is the same as that of the simple type of its content.</span></span> <span data-ttu-id="a840c-123">Zadaná hodnota komplexní typ se složitým obsahem (jeden nebo více podřízených prvků) je zřetězení všechny jeho podřízené uzly text vrácena jako hodnotu řetězce <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a840c-123">The typed value of a complex type with complex content (one or more child elements) is the string value of the concatenation of all its child text nodes returned as a <xref:System.String>.</span></span> <span data-ttu-id="a840c-124">Další informace o mapování z předdefinovaných typů schématu pro typy CLR naleznete v tématu [podpora typu v třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="a840c-124">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
-   <span data-ttu-id="a840c-125">Název schématu jazyka specifického typu: Ve většině případů typů CLR, které jsou nastavené jako vedlejší efekt použití externí schéma, slouží k poskytnutí přístupu k hodnotě uzlu.</span><span class="sxs-lookup"><span data-stu-id="a840c-125">Schema-Language Specific Type Name: In most cases, the CLR types, which are set as a side-effect of applying an external schema, are used to provide access to the value of a node.</span></span> <span data-ttu-id="a840c-126">Mohou však nastat situace, kde můžete prozkoumat typ přidružený k konkrétní schématu použitého pro dokument XML.</span><span class="sxs-lookup"><span data-stu-id="a840c-126">However, there may be situations where you may want to examine the type associated with a particular schema applied to an XML document.</span></span> <span data-ttu-id="a840c-127">Například můžete chtít Hledat v dokumentu XML, extrahování všechny elementy, které jsou určeny s obsahem typu "PurchaseOrder" podle připojených schématu.</span><span class="sxs-lookup"><span data-stu-id="a840c-127">For example, you may wish to search through an XML document, extracting all elements that are determined to have content of type "PurchaseOrder" according to an attached schema.</span></span> <span data-ttu-id="a840c-128">Tyto informace o typu lze nastavit pouze v důsledku ověřování schématu a tyto informace se přistupuje přes <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> a <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="a840c-128">Such type information can be set only as a result of schema validation and this information is accessed through the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> and <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="a840c-129">Další informace naleznete v části příspěvku schématu ověření informační sada (PSVI) níže.</span><span class="sxs-lookup"><span data-stu-id="a840c-129">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
-   <span data-ttu-id="a840c-130">Jazykové schéma reflexe konkrétního typu: V ostatních případech můžete chtít získat další podrobnosti o konkrétní schématu typu použitý pro dokument XML.</span><span class="sxs-lookup"><span data-stu-id="a840c-130">Schema-Language Specific Type Reflection: In other cases, you may want to obtain further details of the schema-specific type applied to an XML document.</span></span> <span data-ttu-id="a840c-131">Například při čtení souboru XML, můžete k extrakci `maxOccurs` atribut pro každý platný uzel v dokumentu XML, aby bylo možné provést některé vlastní výpočet.</span><span class="sxs-lookup"><span data-stu-id="a840c-131">For example, when reading an XML file, you may want to extract the `maxOccurs` attribute for each valid node in the XML document in order to perform some custom calculation.</span></span> <span data-ttu-id="a840c-132">Protože tyto informace je nastavena pouze pomocí ověření schématu, je přístupný prostřednictvím <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="a840c-132">Because this information is set only through schema validation, it is accessed through the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="a840c-133">Další informace naleznete v části příspěvku schématu ověření informační sada (PSVI) níže.</span><span class="sxs-lookup"><span data-stu-id="a840c-133">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
## <a name="xpathnavigator-typed-accessors"></a><span data-ttu-id="a840c-134">XPathNavigator zadali přístupové objekty</span><span class="sxs-lookup"><span data-stu-id="a840c-134">XPathNavigator Typed Accessors</span></span>  
 <span data-ttu-id="a840c-135">V následující tabulce jsou uvedeny různé vlastnosti a metody <xref:System.Xml.XPath.XPathNavigator> třídu, která umožňuje přístup k informacím o typu o uzlu.</span><span class="sxs-lookup"><span data-stu-id="a840c-135">The following table shows the various properties and methods of the <xref:System.Xml.XPath.XPathNavigator> class that can be used to access the type information about a node.</span></span>  
  
|<span data-ttu-id="a840c-136">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="a840c-136">Property</span></span>|<span data-ttu-id="a840c-137">Popis</span><span class="sxs-lookup"><span data-stu-id="a840c-137">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|<span data-ttu-id="a840c-138">Pokud je platný obsahuje informace o typu schématu XML pro uzel.</span><span class="sxs-lookup"><span data-stu-id="a840c-138">This contains the XML schema type information for the node if it is valid.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|<span data-ttu-id="a840c-139">Tato položka obsahuje schéma po ověření informační sadu uzlu, které se přidají po ověření.</span><span class="sxs-lookup"><span data-stu-id="a840c-139">This contains the Post Schema Validation Infoset of the node that is added after validation.</span></span> <span data-ttu-id="a840c-140">To zahrnuje informace o typu schématu XML, jakož i informace platnosti.</span><span class="sxs-lookup"><span data-stu-id="a840c-140">This includes the XML schema type information, as well as validity information.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|<span data-ttu-id="a840c-141">Typ CLR hodnotu typu uzlu.</span><span class="sxs-lookup"><span data-stu-id="a840c-141">The CLR type of the typed value of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|<span data-ttu-id="a840c-142">Obsah uzlu CLR jeden nebo více hodnot, jehož typ je nejvíce odpovídá schématu XML typu uzlu.</span><span class="sxs-lookup"><span data-stu-id="a840c-142">The content of the node as one or more CLR values whose type is the closest match to the XML schema type of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<span data-ttu-id="a840c-143"><xref:System.String> Hodnota pro aktuální uzel přetypována na <xref:System.Boolean> hodnoty, podle pravidla přetypování XPath 2.0 pro `xs:boolean`.</span><span class="sxs-lookup"><span data-stu-id="a840c-143">The <xref:System.String> value of the current node cast to a <xref:System.Boolean> value, according to the XPath 2.0 casting rules for `xs:boolean`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<span data-ttu-id="a840c-144"><xref:System.String> Hodnota pro aktuální uzel přetypována na <xref:System.DateTime> hodnoty, podle pravidla přetypování XPath 2.0 pro `xs:datetime`.</span><span class="sxs-lookup"><span data-stu-id="a840c-144">The <xref:System.String> value of the current node cast to a <xref:System.DateTime> value, according to the XPath 2.0 casting rules for `xs:datetime`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<span data-ttu-id="a840c-145"><xref:System.String> Hodnota pro aktuální uzel přetypována na <xref:System.Double> hodnoty, podle pravidla přetypování XPath 2.0 pro `xsd:double`.</span><span class="sxs-lookup"><span data-stu-id="a840c-145">The <xref:System.String> value of the current node cast to a <xref:System.Double> value, according to the XPath 2.0 casting rules for `xsd:double`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<span data-ttu-id="a840c-146"><xref:System.String> Hodnota pro aktuální uzel přetypována na <xref:System.Int32> hodnoty, podle pravidla přetypování XPath 2.0 pro `xs:integer`.</span><span class="sxs-lookup"><span data-stu-id="a840c-146">The <xref:System.String> value of the current node cast to a <xref:System.Int32> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<span data-ttu-id="a840c-147"><xref:System.String> Hodnota pro aktuální uzel přetypována na <xref:System.Int64> hodnoty, podle pravidla přetypování XPath 2.0 pro `xs:integer`.</span><span class="sxs-lookup"><span data-stu-id="a840c-147">The <xref:System.String> value of the current node cast to a <xref:System.Int64> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|<span data-ttu-id="a840c-148">Obsah uzlu přetypovat na typ cíle podle pravidel přetypování XPath 2.0.</span><span class="sxs-lookup"><span data-stu-id="a840c-148">The contents of the node cast to the target type according to the XPath 2.0 casting rules.</span></span>|  
  
 <span data-ttu-id="a840c-149">Další informace o mapování z předdefinovaných typů schématu pro typy CLR naleznete v tématu [podpora typu v třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="a840c-149">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="the-post-schema-validation-infoset-psvi"></a><span data-ttu-id="a840c-150">Příspěvek schéma ověřování v informační sadu (PSVI)</span><span class="sxs-lookup"><span data-stu-id="a840c-150">The Post Schema Validation Infoset (PSVI)</span></span>  
 <span data-ttu-id="a840c-151">Procesor schématu XML přijímá informační sadu XML jako vstup a převede jej do schéma ověření informační sada (PSVI Post).</span><span class="sxs-lookup"><span data-stu-id="a840c-151">An XML Schema processor accepts an XML Infoset as input and converts it into a Post Schema Validation Infoset (PSVI).</span></span> <span data-ttu-id="a840c-152">PSVI je původní vstupní XML informační sadu se nové informace položky přidané a přidání existující položky informace nových vlastností.</span><span class="sxs-lookup"><span data-stu-id="a840c-152">A PSVI is the original input XML infoset with new information items added and new properties added to existing information items.</span></span> <span data-ttu-id="a840c-153">Existují tři různé třídy informací pro informační sadu XML v PSVI, které jsou vystavené <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="a840c-153">There are three broad classes of information added to the XML Infoset in the PSVI that are exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
1. <span data-ttu-id="a840c-154">Výsledky ověření: Informace o tom, zda elementu nebo atributu byl úspěšně ověřen nebo ne.</span><span class="sxs-lookup"><span data-stu-id="a840c-154">Validation Outcomes: Information as to whether an element or attribute was successfully validated or not.</span></span> <span data-ttu-id="a840c-155">To je zveřejněný prostřednictvím <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="a840c-155">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
2. <span data-ttu-id="a840c-156">Informace o výchozím nastavení: Označení, zda hodnota elementu nebo atributu byl získán prostřednictvím výchozí hodnoty zadané ve schématu, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="a840c-156">Default Information: Indications as to whether the value of the element or attribute was obtained via default values specified in the schema or not.</span></span> <span data-ttu-id="a840c-157">To je zveřejněný prostřednictvím <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="a840c-157">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
3. <span data-ttu-id="a840c-158">Poznámky: Odkazy na schéma komponenty, které mohou být typ definice nebo deklarace prvků a atributů.</span><span class="sxs-lookup"><span data-stu-id="a840c-158">Type Annotations: References to schema components that may be type definitions or element and attribute declarations.</span></span> <span data-ttu-id="a840c-159"><xref:System.Xml.XPath.XPathNavigator.XmlType%2A> Vlastnost <xref:System.Xml.XPath.XPathNavigator> obsahuje informace o konkrétním typu uzlu, pokud je platný.</span><span class="sxs-lookup"><span data-stu-id="a840c-159">The <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property of the <xref:System.Xml.XPath.XPathNavigator> contains the specific type information of the node if it is valid.</span></span> <span data-ttu-id="a840c-160">Pokud platnost uzel neznámý, například když se ověřila pak následně upravit.</span><span class="sxs-lookup"><span data-stu-id="a840c-160">If the validity of a node is unknown, such as when it was validated then subsequently edited.</span></span> <span data-ttu-id="a840c-161">pak bude <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> je nastavena na `null` je stále k dispozici různé vlastnosti informací o typu, ale <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="a840c-161">then the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property is set to `null` but type information is still available from the various properties of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="a840c-162">Následující příklad ukazuje, použijte informace v vystavené informační po Schema ověření sadu <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="a840c-162">The following example illustrates using information in the Post Schema Validation Infoset exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
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
  
 <span data-ttu-id="a840c-163">V příkladu přebírá `books.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="a840c-163">The example takes the `books.xml` file as input.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="a840c-164">Tento příklad využívá taky `books.xsd` schématu jako vstup.</span><span class="sxs-lookup"><span data-stu-id="a840c-164">The example also takes the `books.xsd` schema as input.</span></span>  
  
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
  
## <a name="obtain-typed-values-using-valueas-properties"></a><span data-ttu-id="a840c-165">Získání zadaných hodnot pomocí vlastností ValueAs</span><span class="sxs-lookup"><span data-stu-id="a840c-165">Obtain Typed Values Using ValueAs Properties</span></span>  
 <span data-ttu-id="a840c-166">Zadaná hodnota uzlu je možné načíst podle přístupu <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> vlastnost <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="a840c-166">The typed value of a node can be retrieved by accessing the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="a840c-167">V některých případech můžete převést hodnotu typu uzlu do jiného typu.</span><span class="sxs-lookup"><span data-stu-id="a840c-167">In certain cases you may want to convert the typed value of a node to a different type.</span></span> <span data-ttu-id="a840c-168">Běžným příkladem je k získání číselné hodnoty z uzlu XML.</span><span class="sxs-lookup"><span data-stu-id="a840c-168">A common example is to get a numeric value from an XML node.</span></span> <span data-ttu-id="a840c-169">Představte si třeba neověřený a netypové následujícího dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="a840c-169">For example, consider the following unvalidated and untyped XML document.</span></span>  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="a840c-170">Pokud <xref:System.Xml.XPath.XPathNavigator> je umístěn na `price` element <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> by být vlastnost `null`, <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> by být vlastnost <xref:System.String>a <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> vlastnost bude řetězec `10.00`.</span><span class="sxs-lookup"><span data-stu-id="a840c-170">If the <xref:System.Xml.XPath.XPathNavigator> is positioned on the `price` element the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property would be `null`, the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property would be <xref:System.String>, and the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property would be the string `10.00`.</span></span>  
  
 <span data-ttu-id="a840c-171">Je však stále možné extrahovat hodnotu jako číselnou hodnotu použití <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, nebo <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a840c-171">However, it is still possible to extract the value as a numeric value using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, or <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> method and properties.</span></span> <span data-ttu-id="a840c-172">Následující příklad ukazuje takový typu přetypování pomocí provádí <xref:System.Xml.XPath.XPathItem.ValueAs%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a840c-172">The following example illustrates performing such a cast using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="a840c-173">Další informace o mapování z předdefinovaných typů schématu pro typy CLR naleznete v tématu [podpora typu v třídách System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="a840c-173">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a840c-174">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a840c-174">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="a840c-175">Podpora typu v třídách System.Xml</span><span class="sxs-lookup"><span data-stu-id="a840c-175">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
- [<span data-ttu-id="a840c-176">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="a840c-176">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="a840c-177">Navigace v sadě uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a840c-177">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="a840c-178">Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a840c-178">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="a840c-179">Extrahování dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a840c-179">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)

---
title: Import a export schémat
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: 0da32b50-ccd9-463a-844c-7fe803d3bf44
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fe4ef5b17013bf1a9abf5fd1ca0807fe4d335df4
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="schema-import-and-export"></a><span data-ttu-id="17254-102">Import a export schémat</span><span class="sxs-lookup"><span data-stu-id="17254-102">Schema Import and Export</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="17254-103"> zahrnuje nové Serializační stroj <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="17254-103"> includes a new serialization engine, the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="17254-104">`DataContractSerializer` Překládá mezi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objekty a XML (v obou směrech).</span><span class="sxs-lookup"><span data-stu-id="17254-104">The `DataContractSerializer` translates between [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objects and XML (in both directions).</span></span> <span data-ttu-id="17254-105">Vedle sebe, serializátor [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zahrnuje přidružené schéma import a export mechanismy schématu.</span><span class="sxs-lookup"><span data-stu-id="17254-105">In addition to the serializer itself, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] includes associated schema import and schema export mechanisms.</span></span> <span data-ttu-id="17254-106">*Schéma* formální, přesné a strojově čitelným popis obrazec XML, který produkuje serializátor nebo který deserializátor přístup.</span><span class="sxs-lookup"><span data-stu-id="17254-106">*Schema* is a formal, precise, and machine-readable description of the shape of XML that the serializer produces or that the deserializer can access.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="17254-107"> jazyk definice schématu XML World Wide Web Consortium (W3C) (XSD) se používá jako jeho reprezentace schématu, která je široce vzájemná spolupráce s mnoha platformy třetí strany.</span><span class="sxs-lookup"><span data-stu-id="17254-107"> uses the World Wide Web Consortium (W3C) XML Schema definition language (XSD) as its schema representation, which is widely interoperable with numerous third-party platforms.</span></span>  
  
 <span data-ttu-id="17254-108">Komponentu import schématu <xref:System.Runtime.Serialization.XsdDataContractImporter>, trvá dokument schématu XSD a generuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] třídy (obvykle třídy kontraktu dat) tak, aby serializovaných formuláře odpovídají daného schématu.</span><span class="sxs-lookup"><span data-stu-id="17254-108">The schema import component, <xref:System.Runtime.Serialization.XsdDataContractImporter>, takes an XSD schema document and generates [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] classes (normally data contract classes) such that the serialized forms correspond to the given schema.</span></span>  
  
 <span data-ttu-id="17254-109">Například následující fragment schématu:</span><span class="sxs-lookup"><span data-stu-id="17254-109">For example, the following schema fragment:</span></span>  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 <span data-ttu-id="17254-110">generuje následujícího typu (zjednodušená mírně pro lepší čitelnost).</span><span class="sxs-lookup"><span data-stu-id="17254-110">generates the following type (simplified slightly for better readability).</span></span>  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 <span data-ttu-id="17254-111">Všimněte si, že typ generovaného následuje několik osvědčené postupy kontraktu dat (v nalezen [osvědčené postupy: Správa verzí kontraktů dat](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)):</span><span class="sxs-lookup"><span data-stu-id="17254-111">Note that the generated type follows several data contract best practices (found in [Best Practices: Data Contract Versioning](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)):</span></span>  
  
-   <span data-ttu-id="17254-112">Typ implementuje <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="17254-112">The type implements the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.</span></span> <span data-ttu-id="17254-113">Další informace najdete v tématu [kontrakty dat dopřednou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="17254-113">For more information, see [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span></span>  
  
-   <span data-ttu-id="17254-114">Datové členy jsou implementované jako veřejné vlastnosti, které balí privátním polím.</span><span class="sxs-lookup"><span data-stu-id="17254-114">Data members are implemented as public properties that wrap private fields.</span></span>  
  
-   <span data-ttu-id="17254-115">Třída je konkrétní třídu a dodatky můžete provedeny beze změny generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="17254-115">The class is a partial class, and additions can be made without modifying generated code.</span></span>  
  
 <span data-ttu-id="17254-116"><xref:System.Runtime.Serialization.XsdDataContractExporter> Umožňuje opačný – trvat typů, které jsou serializovat pomocí `DataContractSerializer` a generovat dokument schématu XSD.</span><span class="sxs-lookup"><span data-stu-id="17254-116">The <xref:System.Runtime.Serialization.XsdDataContractExporter> enables you to do the reverse—take types that are serializable with the `DataContractSerializer` and generate an XSD Schema document.</span></span>  
  
## <a name="fidelity-is-not-guaranteed"></a><span data-ttu-id="17254-117">Přesnost není zaručena.</span><span class="sxs-lookup"><span data-stu-id="17254-117">Fidelity Is Not Guaranteed</span></span>  
 <span data-ttu-id="17254-118">Není zaručeno, že schéma nebo typy provést výměnu zpráv s celkový přesnost.</span><span class="sxs-lookup"><span data-stu-id="17254-118">It is not guaranteed that schema or types make a round trip with total fidelity.</span></span> <span data-ttu-id="17254-119">(A *odezvy* znamená pro import schématu vytvořit sadu tříd a exportovat výsledek se znovu vytvořit schéma.) Stejné schéma nemusí být vrácena.</span><span class="sxs-lookup"><span data-stu-id="17254-119">(A *round trip* means to import a schema to create a set of classes, and export the result to create a schema again.) The same schema may not be returned.</span></span> <span data-ttu-id="17254-120">Prohodit proces není zaručena také k zachování přesnost.</span><span class="sxs-lookup"><span data-stu-id="17254-120">Reversing the process is also not guaranteed to preserve fidelity.</span></span> <span data-ttu-id="17254-121">(Typ pro generování schématem exportovat a pak naimportujete typ zpět.</span><span class="sxs-lookup"><span data-stu-id="17254-121">(Export a type to generate its schema, and then import the type back.</span></span> <span data-ttu-id="17254-122">Nepravděpodobné, že je vrácen stejného typu.)</span><span class="sxs-lookup"><span data-stu-id="17254-122">It is unlikely the same type is returned.)</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="17254-123">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="17254-123">Supported Types</span></span>  
 <span data-ttu-id="17254-124">Datový model kontrakt podporuje omezenou podmnožinou WC3 schématu.</span><span class="sxs-lookup"><span data-stu-id="17254-124">The data contract model supports only a limited subset of the WC3 schema.</span></span> <span data-ttu-id="17254-125">Žádné schéma, které nejsou v souladu s touto sadou způsobí výjimku během procesu importu.</span><span class="sxs-lookup"><span data-stu-id="17254-125">Any schema that does not conform to this subset will cause an exception during the import process.</span></span> <span data-ttu-id="17254-126">Například neexistuje žádný způsob, jak určit, že se data členem kontraktu dat by měly být serializovány jako atribut XML.</span><span class="sxs-lookup"><span data-stu-id="17254-126">For example, there is no way to specify that a data member of a data contract should be serialized as an XML attribute.</span></span> <span data-ttu-id="17254-127">Proto schémat, které vyžadují použití atributy XML nejsou podporovány a způsobí, že výjimky během importu, protože není možné vygenerovat kontraktu dat s správné projekce XML.</span><span class="sxs-lookup"><span data-stu-id="17254-127">Thus, schemas that require the use of XML attributes are not supported and will cause exceptions during import, because it is impossible to generate a data contract with the correct XML projection.</span></span>  
  
 <span data-ttu-id="17254-128">Například následující fragment schématu nelze importovat pomocí výchozího nastavení pro import.</span><span class="sxs-lookup"><span data-stu-id="17254-128">For example, the following schema fragment cannot be imported using the default import settings.</span></span>  
  
 [!code-xml[c_SchemaImportExport#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  
  
 <span data-ttu-id="17254-129">Další informace najdete v tématu [Přehled schématu kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).</span><span class="sxs-lookup"><span data-stu-id="17254-129">For more information, see [Data Contract Schema Reference](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).</span></span> <span data-ttu-id="17254-130">Pokud schéma nevyhovuje pravidlům kontraktu dat, použijte modul různých serializace.</span><span class="sxs-lookup"><span data-stu-id="17254-130">If a schema does not conform to the data contract rules, use a different serialization engine.</span></span> <span data-ttu-id="17254-131">Například <xref:System.Xml.Serialization.XmlSerializer> používá mechanismus import vlastní samostatné schéma.</span><span class="sxs-lookup"><span data-stu-id="17254-131">For example, the <xref:System.Xml.Serialization.XmlSerializer> uses its own separate schema import mechanism.</span></span> <span data-ttu-id="17254-132">Je taky speciální import režim, ve kterém je rozšířena rozsahu podporované schématu.</span><span class="sxs-lookup"><span data-stu-id="17254-132">Also, there is a special import mode in which the range of supported schema is expanded.</span></span> <span data-ttu-id="17254-133">Další informace najdete v části o generování <xref:System.Xml.Serialization.IXmlSerializable> typy v [import schématu pro generování tříd](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).</span><span class="sxs-lookup"><span data-stu-id="17254-133">For more information, see the section about generating <xref:System.Xml.Serialization.IXmlSerializable> types in [Importing Schema to Generate Classes](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).</span></span>  
  
 <span data-ttu-id="17254-134">`XsdDataContractExporter` Podporuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, které mohou serializovat s příznakem `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="17254-134">The `XsdDataContractExporter` supports any [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types that can be serialized with the `DataContractSerializer`.</span></span> <span data-ttu-id="17254-135">Další informace najdete v tématu [typy nepodporuje serializátor kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).</span><span class="sxs-lookup"><span data-stu-id="17254-135">For more information, see [Types Supported by the Data Contract Serializer](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).</span></span> <span data-ttu-id="17254-136">Všimněte si, že schématu generována pomocí `XsdDataContractExporter` je obvykle platný datový, `XsdDataContractImporter` můžete použít (Pokud <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> slouží k přizpůsobení schématu).</span><span class="sxs-lookup"><span data-stu-id="17254-136">Note that schema generated using the `XsdDataContractExporter` is normally valid data that the `XsdDataContractImporter` can use (unless the <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> is used to customize the schema).</span></span>  
  
 <span data-ttu-id="17254-137">Další informace o používání <xref:System.Runtime.Serialization.XsdDataContractImporter>, najdete v části [import schématu pro generování tříd](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).</span><span class="sxs-lookup"><span data-stu-id="17254-137">For more information about using the <xref:System.Runtime.Serialization.XsdDataContractImporter>, see [Importing Schema to Generate Classes](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).</span></span>  
  
 <span data-ttu-id="17254-138">Další informace o používání <xref:System.Runtime.Serialization.XsdDataContractExporter>, najdete v části [export schémat ze tříd](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).</span><span class="sxs-lookup"><span data-stu-id="17254-138">For more information about using the <xref:System.Runtime.Serialization.XsdDataContractExporter>, see [Exporting Schemas from Classes](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17254-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="17254-139">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 <xref:System.Runtime.Serialization.XsdDataContractExporter>  
 [<span data-ttu-id="17254-140">Import schématu pro generování tříd</span><span class="sxs-lookup"><span data-stu-id="17254-140">Importing Schema to Generate Classes</span></span>](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)  
 [<span data-ttu-id="17254-141">Export schémat ze tříd</span><span class="sxs-lookup"><span data-stu-id="17254-141">Exporting Schemas from Classes</span></span>](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)

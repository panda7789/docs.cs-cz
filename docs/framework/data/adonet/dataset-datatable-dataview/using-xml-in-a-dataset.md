---
title: Použití XML v datové sadě
ms.date: 03/30/2017
ms.assetid: 35138159-e199-49ec-baf7-1ec6777e171e
ms.openlocfilehash: ca04f524685e080be6af12a4df6eda585a908683
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784251"
---
# <a name="using-xml-in-a-dataset"></a><span data-ttu-id="10a06-102">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="10a06-102">Using XML in a DataSet</span></span>
<span data-ttu-id="10a06-103">Pomocí ADO.NET můžete vyplnit <xref:System.Data.DataSet> datový proud XML nebo dokument.</span><span class="sxs-lookup"><span data-stu-id="10a06-103">With ADO.NET you can fill a <xref:System.Data.DataSet> from an XML stream or document.</span></span> <span data-ttu-id="10a06-104">Datový proud XML nebo dokument můžete použít k poskytnutí <xref:System.Data.DataSet> dat, informací o schématu nebo obojího.</span><span class="sxs-lookup"><span data-stu-id="10a06-104">You can use the XML stream or document to supply to the <xref:System.Data.DataSet> either data, schema information, or both.</span></span> <span data-ttu-id="10a06-105">Informace poskytnuté z datového proudu XML nebo dokumentu lze kombinovat se stávajícími informacemi o schématu, které <xref:System.Data.DataSet>již existují v nástroji.</span><span class="sxs-lookup"><span data-stu-id="10a06-105">The information supplied from the XML stream or document can be combined with existing data or schema information already present in the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="10a06-106">ADO.NET také umožňuje vytvořit reprezentaci <xref:System.Data.DataSet>XML s a bez jejího schématu, aby bylo možné <xref:System.Data.DataSet> přenést přenos přes protokol HTTP pro použití jinou aplikací nebo platformou podporující XML.</span><span class="sxs-lookup"><span data-stu-id="10a06-106">ADO.NET also allows you to create an XML representation of a <xref:System.Data.DataSet>, with or without its schema, in order to transport the <xref:System.Data.DataSet> across HTTP for use by another application or XML-enabled platform.</span></span> <span data-ttu-id="10a06-107">V jazyce XML reprezentace <xref:System.Data.DataSet>a jsou data zapsána do XML a schématu, pokud je vložena do reprezentace, jsou zapsána pomocí jazyka XML Schema Definition Language (XSD).</span><span class="sxs-lookup"><span data-stu-id="10a06-107">In an XML representation of a <xref:System.Data.DataSet>, the data is written in XML and the schema, if it is included inline in the representation, is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="10a06-108">Schéma XML a XML poskytují pohodlný formát pro přenos obsahu <xref:System.Data.DataSet> a ze vzdálených klientů.</span><span class="sxs-lookup"><span data-stu-id="10a06-108">XML and XML Schema provide a convenient format for transferring the contents of a <xref:System.Data.DataSet> to and from remote clients.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="10a06-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="10a06-109">In This Section</span></span>  
 [<span data-ttu-id="10a06-110">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="10a06-110">DiffGrams</span></span>](diffgrams.md)  
 <span data-ttu-id="10a06-111">Poskytuje podrobné informace o formátu DiffGram, formátu XML, který se používá ke čtení a zápisu obsahu <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="10a06-111">Provides details on the DiffGram, an XML format used to read and write the contents of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="10a06-112">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="10a06-112">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)  
 <span data-ttu-id="10a06-113">Popisuje různé možnosti, které je <xref:System.Data.DataSet> třeba vzít v úvahu při načítání obsahu z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="10a06-113">Discusses different options to consider when loading the contents of a <xref:System.Data.DataSet> from an XML document.</span></span>  
  
 [<span data-ttu-id="10a06-114">Kopírování obsahu datové sady jako dat XML</span><span class="sxs-lookup"><span data-stu-id="10a06-114">Writing DataSet Contents as XML Data</span></span>](writing-dataset-contents-as-xml-data.md)  
 <span data-ttu-id="10a06-115">Popisuje, jak vygenerovat obsah a <xref:System.Data.DataSet> jako data XML, a různé možnosti formátu XML, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="10a06-115">Discusses how to generate the contents of a <xref:System.Data.DataSet> as XML data, and the different XML format options you can use.</span></span>  
  
 [<span data-ttu-id="10a06-116">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="10a06-116">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)  
 <span data-ttu-id="10a06-117">Popisuje metody používané pro načtení schématu <xref:System.Data.DataSet> z kódu XML. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="10a06-117">Discusses the <xref:System.Data.DataSet> methods used to load the schema of a <xref:System.Data.DataSet> from XML.</span></span>  
  
 [<span data-ttu-id="10a06-118">Zápis informací o schématu datové sady jako XSD</span><span class="sxs-lookup"><span data-stu-id="10a06-118">Writing DataSet Schema Information as XSD</span></span>](writing-dataset-schema-information-as-xsd.md)  
 <span data-ttu-id="10a06-119">Popisuje použití pro schéma XML a způsob, jak jej vygenerovat <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="10a06-119">Discusses the uses for an XML Schema and how to generate one from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="10a06-120">Synchronizace datové sady a datového dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="10a06-120">DataSet and XmlDataDocument Synchronization</span></span>](dataset-and-xmldatadocument-synchronization.md)  
 <span data-ttu-id="10a06-121">Popisuje možnosti dostupné v .NET Framework synchronního přístupu k relačním i hierarchickým zobrazením jedné sady dat a ukazuje, jak vytvořit synchronní vztah mezi <xref:System.Data.DataSet> <xref:System.Xml.XmlDataDocument>a a.</span><span class="sxs-lookup"><span data-stu-id="10a06-121">Discusses the capability available in the .NET Framework of synchronous access to both relational and hierarchical views of a single set of data, and shows how to create a synchronous relationship between a <xref:System.Data.DataSet> and an <xref:System.Xml.XmlDataDocument>.</span></span>  
  
 [<span data-ttu-id="10a06-122">Vnoření datových relací</span><span class="sxs-lookup"><span data-stu-id="10a06-122">Nesting DataRelations</span></span>](nesting-datarelations.md)  
 <span data-ttu-id="10a06-123">Popisuje důležitost vnořených <xref:System.Data.DataRelation> objektů, které představují obsah a <xref:System.Data.DataSet> jako data XML, a popisuje, jak je vytvořit.</span><span class="sxs-lookup"><span data-stu-id="10a06-123">Discusses the importance of nested <xref:System.Data.DataRelation> objects when representing the contents of a <xref:System.Data.DataSet> as XML data, and describes how to create them.</span></span>  
  
 [<span data-ttu-id="10a06-124">Odvozování relační struktury datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="10a06-124">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="10a06-125">Popisuje relační strukturu neboli schéma <xref:System.Data.DataSet> , které je vytvořeno ze schématu XML.</span><span class="sxs-lookup"><span data-stu-id="10a06-125">Describes the relational structure, or schema, of a <xref:System.Data.DataSet> that is created from XML Schema.</span></span>  
  
 [<span data-ttu-id="10a06-126">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="10a06-126">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)  
 <span data-ttu-id="10a06-127">Popisuje výslednou relační strukturu neboli schéma <xref:System.Data.DataSet> , které je vytvořeno při odvození z prvků XML.</span><span class="sxs-lookup"><span data-stu-id="10a06-127">Describes the resulting relational structure, or schema, of a <xref:System.Data.DataSet> that is created when inferred from XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="10a06-128">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="10a06-128">Related Sections</span></span>  
 [<span data-ttu-id="10a06-129">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="10a06-129">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="10a06-130">Popisuje architekturu a komponenty ADO.NET a jejich použití pro přístup k existujícím zdrojům dat a také ke správě aplikačních dat.</span><span class="sxs-lookup"><span data-stu-id="10a06-130">Describes the ADO.NET architecture and components, and how to use them to access existing data sources as well as to manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10a06-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10a06-131">See also</span></span>

- [<span data-ttu-id="10a06-132">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="10a06-132">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="10a06-133">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="10a06-133">ADO.NET Overview</span></span>](../ado-net-overview.md)

---
title: "Odvození omezení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 98ea3d5fa4427b391ef06b3fc6ace9a05dfb819a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="inference-limitations"></a><span data-ttu-id="00801-102">Odvození omezení</span><span class="sxs-lookup"><span data-stu-id="00801-102">Inference Limitations</span></span>
<span data-ttu-id="00801-103">Proces odvození <xref:System.Data.DataSet> schématu z XML může mít za následek různé schémata v závislosti na elementy XML v každý dokument.</span><span class="sxs-lookup"><span data-stu-id="00801-103">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="00801-104">Zvažte například následující dokumenty XML.</span><span class="sxs-lookup"><span data-stu-id="00801-104">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="00801-105">Dokument1:</span><span class="sxs-lookup"><span data-stu-id="00801-105">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="00801-106">Document2:</span><span class="sxs-lookup"><span data-stu-id="00801-106">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="00801-107">Pro "Dokument1," proces odvození vytváří **datovou sadu** s názvem "Prvek DocumentElement" a tabulka s názvem "Element1,", protože "Element1" je opakující se prvek.</span><span class="sxs-lookup"><span data-stu-id="00801-107">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="00801-108">**Datová sada:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="00801-108">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="00801-109">**Tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="00801-109">**Table:** Element1</span></span>  
  
|<span data-ttu-id="00801-110">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="00801-110">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="00801-111">Text1</span><span class="sxs-lookup"><span data-stu-id="00801-111">Text1</span></span>|  
|<span data-ttu-id="00801-112">Text2</span><span class="sxs-lookup"><span data-stu-id="00801-112">Text2</span></span>|  
  
 <span data-ttu-id="00801-113">Ale pro "Document2," vytvoří proces odvození **datovou sadu** s názvem "NewDataSet" a tabulka s názvem "Prvek DocumentElement."</span><span class="sxs-lookup"><span data-stu-id="00801-113">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="00801-114">"Element1" je jako sloupec odvodit, protože nemá žádné atributy a žádné podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="00801-114">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="00801-115">**Datová sada:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="00801-115">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="00801-116">**Tabulka:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="00801-116">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="00801-117">Element1</span><span class="sxs-lookup"><span data-stu-id="00801-117">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="00801-118">Text1</span><span class="sxs-lookup"><span data-stu-id="00801-118">Text1</span></span>|  
  
 <span data-ttu-id="00801-119">Tyto dva dokumenty XML může byla určených k vytvoření stejného schématu, ale proces odvození vytváří velmi odlišné výsledky podle elementů obsažených v každém dokumentu.</span><span class="sxs-lookup"><span data-stu-id="00801-119">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="00801-120">Abyste se vyhnuli rozporů může dojít, když generování schématu z dokumentu XML, doporučujeme explicitně zadáte pomocí jazyka pro definici schématu XML (XSD) nebo XML-Data Reduced (XDR) při načítání schématu **datovou sadu** z SOUBOR XML.</span><span class="sxs-lookup"><span data-stu-id="00801-120">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="00801-121">Další informace o explicitně určit **datovou sadu** schématu se schématem XML, najdete v části [odvozování relační strukturu datové sady z schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="00801-121">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00801-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="00801-122">See Also</span></span>  
 [<span data-ttu-id="00801-123">Odvození relační strukturu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="00801-123">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="00801-124">Načítání datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="00801-124">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="00801-125">Načítání informací o schématu sady dat z XML</span><span class="sxs-lookup"><span data-stu-id="00801-125">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="00801-126">Pomocí XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="00801-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="00801-127">Datové sady, DataTables a DataView</span><span class="sxs-lookup"><span data-stu-id="00801-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="00801-128">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="00801-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

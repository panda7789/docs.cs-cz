---
title: Odvození omezení
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: d113df98cdd339300b3e75ceda49a56d4f346d3c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44190675"
---
# <a name="inference-limitations"></a><span data-ttu-id="b384a-102">Odvození omezení</span><span class="sxs-lookup"><span data-stu-id="b384a-102">Inference Limitations</span></span>
<span data-ttu-id="b384a-103">Proces odvození <xref:System.Data.DataSet> schéma ze souboru XML může vést k různými schématy v závislosti na prvky XML v jednotlivých dokumentech.</span><span class="sxs-lookup"><span data-stu-id="b384a-103">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="b384a-104">Představte si třeba následující dokumenty XML.</span><span class="sxs-lookup"><span data-stu-id="b384a-104">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="b384a-105">Dokument1:</span><span class="sxs-lookup"><span data-stu-id="b384a-105">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b384a-106">Document2:</span><span class="sxs-lookup"><span data-stu-id="b384a-106">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b384a-107">Pro "Dokument1," vytvoří procesu odvození **datovou sadu** s názvem "Prvek DocumentElement" a tabulku s názvem "Element1", "Element1" představuje opakující se prvek proto.</span><span class="sxs-lookup"><span data-stu-id="b384a-107">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="b384a-108">**Datová sada:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b384a-108">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="b384a-109">**Tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="b384a-109">**Table:** Element1</span></span>  
  
|<span data-ttu-id="b384a-110">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="b384a-110">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="b384a-111">Text1</span><span class="sxs-lookup"><span data-stu-id="b384a-111">Text1</span></span>|  
|<span data-ttu-id="b384a-112">Text2</span><span class="sxs-lookup"><span data-stu-id="b384a-112">Text2</span></span>|  
  
 <span data-ttu-id="b384a-113">Ale pro "Document2," vytvoří procesu odvození **datovou sadu** s názvem "NewDataSet" a tabulku s názvem "Prvek DocumentElement."</span><span class="sxs-lookup"><span data-stu-id="b384a-113">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="b384a-114">"Element1" je odvozen jako sloupec, protože nemá žádné atributy a žádné podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="b384a-114">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="b384a-115">**Datová sada:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="b384a-115">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="b384a-116">**Tabulka:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b384a-116">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="b384a-117">element1</span><span class="sxs-lookup"><span data-stu-id="b384a-117">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="b384a-118">Text1</span><span class="sxs-lookup"><span data-stu-id="b384a-118">Text1</span></span>|  
  
 <span data-ttu-id="b384a-119">Tyto dva dokumenty XML byl asi zamýšlený k vytvoření stejné schéma, ale procesu odvození vytváří velmi odlišné výsledky podle elementů obsažených v jednotlivých dokumentech.</span><span class="sxs-lookup"><span data-stu-id="b384a-119">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="b384a-120">Aby se zabránilo nedostatky, které mohou nastat při generování schématu z dokumentu XML, doporučujeme explicitně zadat pomocí jazyka pro definici schématu XML (XSD) nebo XML-Data Reduced (XDR) při načítání schématu **datovou sadu** z SOUBOR XML.</span><span class="sxs-lookup"><span data-stu-id="b384a-120">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="b384a-121">Další informace o explicitním zadáním **datovou sadu** schéma pomocí schématu XML, naleznete v tématu [odvozování relační struktury datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="b384a-121">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b384a-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="b384a-122">See Also</span></span>  
 [<span data-ttu-id="b384a-123">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="b384a-123">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="b384a-124">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="b384a-124">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="b384a-125">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="b384a-125">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="b384a-126">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="b384a-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="b384a-127">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="b384a-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="b384a-128">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="b384a-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

---
title: Odvození omezení
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 10347abc5b01edb4ec6fbf97221d44f4bfb88f54
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784577"
---
# <a name="inference-limitations"></a><span data-ttu-id="c964c-102">Odvození omezení</span><span class="sxs-lookup"><span data-stu-id="c964c-102">Inference Limitations</span></span>
<span data-ttu-id="c964c-103">Proces odvození <xref:System.Data.DataSet> schématu z kódu XML může mít za následek různá schémata v závislosti na prvcích XML v jednotlivých dokumentech.</span><span class="sxs-lookup"><span data-stu-id="c964c-103">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="c964c-104">Zvažte například následující dokumenty XML.</span><span class="sxs-lookup"><span data-stu-id="c964c-104">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="c964c-105">Document1</span><span class="sxs-lookup"><span data-stu-id="c964c-105">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="c964c-106">Document2</span><span class="sxs-lookup"><span data-stu-id="c964c-106">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="c964c-107">Pro "Document1", proces odvození vytvoří **datovou sadu** s názvem "DocumentElement" a tabulku s názvem "Element1", protože "Element1" je opakující se element.</span><span class="sxs-lookup"><span data-stu-id="c964c-107">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="c964c-108">**Integrován** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="c964c-108">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="c964c-109">**Stolní** Element1</span><span class="sxs-lookup"><span data-stu-id="c964c-109">**Table:** Element1</span></span>  
  
|<span data-ttu-id="c964c-110">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="c964c-110">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="c964c-111">Text1</span><span class="sxs-lookup"><span data-stu-id="c964c-111">Text1</span></span>|  
|<span data-ttu-id="c964c-112">Text2</span><span class="sxs-lookup"><span data-stu-id="c964c-112">Text2</span></span>|  
  
 <span data-ttu-id="c964c-113">Pro "Document2" ale proces odvození vytvoří **datovou sadu** s názvem "NewDataSet" a tabulku s názvem "DocumentElement".</span><span class="sxs-lookup"><span data-stu-id="c964c-113">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="c964c-114">"Element1" je odvozen jako sloupec, protože nemá žádné atributy a žádné podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="c964c-114">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="c964c-115">**Integrován** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="c964c-115">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="c964c-116">**Stolní** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="c964c-116">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="c964c-117">Element1</span><span class="sxs-lookup"><span data-stu-id="c964c-117">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="c964c-118">Text1</span><span class="sxs-lookup"><span data-stu-id="c964c-118">Text1</span></span>|  
  
 <span data-ttu-id="c964c-119">Tyto dva dokumenty XML mohou být určeny k vytvoření stejného schématu, ale proces odvození vytváří velmi různé výsledky na základě prvků obsažených v jednotlivých dokumentech.</span><span class="sxs-lookup"><span data-stu-id="c964c-119">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="c964c-120">Aby nedocházelo ke konfliktům, ke kterým může dojít při generování schématu z dokumentu XML, doporučujeme při načítání **datové sady** z XML explicitně zadat schéma pomocí jazyka XSD (XML Schema Definition Language) nebo souboru XDR (XML – data s omezením).</span><span class="sxs-lookup"><span data-stu-id="c964c-120">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="c964c-121">Další informace o explicitním určení schématu **datové sady** pomocí schématu XML naleznete v tématu [odvozování relační struktury datové sady ze schématu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="c964c-121">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c964c-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c964c-122">See also</span></span>

- [<span data-ttu-id="c964c-123">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="c964c-123">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="c964c-124">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="c964c-124">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="c964c-125">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="c964c-125">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="c964c-126">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="c964c-126">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="c964c-127">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="c964c-127">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="c964c-128">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c964c-128">ADO.NET Overview</span></span>](../ado-net-overview.md)

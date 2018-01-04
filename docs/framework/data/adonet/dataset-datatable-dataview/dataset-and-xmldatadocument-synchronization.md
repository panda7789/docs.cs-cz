---
title: "Datové sady a XmlDataDocument synchronizace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: acc68fd36d2887e5e951f9ba5adc20e8cfd87fd2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="dataset-and-xmldatadocument-synchronization"></a><span data-ttu-id="08da8-102">Datové sady a XmlDataDocument synchronizace</span><span class="sxs-lookup"><span data-stu-id="08da8-102">DataSet and XmlDataDocument Synchronization</span></span>
<span data-ttu-id="08da8-103">Technologie ADO.NET <xref:System.Data.DataSet> vám poskytne relační znázornění dat.</span><span class="sxs-lookup"><span data-stu-id="08da8-103">The ADO.NET <xref:System.Data.DataSet> provides you with a relational representation of data.</span></span> <span data-ttu-id="08da8-104">Hierarchický přístup k datům můžete použít k dispozici v rozhraní .NET Framework XML třídy.</span><span class="sxs-lookup"><span data-stu-id="08da8-104">For hierarchical data access, you can use the XML classes available in the .NET Framework.</span></span> <span data-ttu-id="08da8-105">Tyto dvě reprezentace dat v minulosti, již byly použity samostatně.</span><span class="sxs-lookup"><span data-stu-id="08da8-105">Historically, these two representations of data have been used separately.</span></span> <span data-ttu-id="08da8-106">Ale rozhraní .NET Framework umožňuje v reálném čase, synchronní přístup k hierarchické a relační reprezentace dat prostřednictvím **datovou sadu** objektu a <xref:System.Xml.XmlDataDocument> objektu v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="08da8-106">However, the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the **DataSet** object and the <xref:System.Xml.XmlDataDocument> object, respectively.</span></span>  
  
 <span data-ttu-id="08da8-107">Když **datovou sadu** je synchronizován se službou **XmlDataDocument**, jsou oba objekty práce s jedinou sadu dat.</span><span class="sxs-lookup"><span data-stu-id="08da8-107">When a **DataSet** is synchronized with an **XmlDataDocument**, both objects are working with a single set of data.</span></span> <span data-ttu-id="08da8-108">To znamená, že pokud dojde ke změně k **datovou sadu**, změna se projeví v **XmlDataDocument**a naopak.</span><span class="sxs-lookup"><span data-stu-id="08da8-108">This means that if a change is made to the **DataSet**, the change will be reflected in the **XmlDataDocument**, and vice versa.</span></span> <span data-ttu-id="08da8-109">Vztah mezi **datovou sadu** a **XmlDataDocument** vytvoří flexibilitu tím, že jednu aplikaci, použití jedné sady dat, pro přístup k celé sadě služeb vytvořené kolem **datovou sadu** (například ovládací prvky webových formulářů a systém Windows Forms a sady Visual Studio .NET Designer), a také sadu služeb XML, včetně šablony stylů XSL (Extensible Language), XSL transformace XSLT () a cestu XML Jazyka (XPath).</span><span class="sxs-lookup"><span data-stu-id="08da8-109">The relationship between the **DataSet** and the **XmlDataDocument** creates great flexibility by allowing a single application, using a single set of data, to access the entire suite of services built around the **DataSet** (such as Web Forms and Windows Forms controls, and Visual Studio .NET designers), as well as the suite of XML services including Extensible Stylesheet Language (XSL), XSL Transformations (XSLT), and XML Path Language (XPath).</span></span> <span data-ttu-id="08da8-110">Nemáte vybrat sadu služeb k cíli s aplikací; obě možnosti jsou dostupné.</span><span class="sxs-lookup"><span data-stu-id="08da8-110">You do not have to choose which set of services to target with the application; both are available.</span></span>  
  
 <span data-ttu-id="08da8-111">Existuje několik způsobů, které můžete synchronizovat **datovou sadu** s **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="08da8-111">There are several ways that you can synchronize a **DataSet** with an **XmlDataDocument**.</span></span> <span data-ttu-id="08da8-112">Můžeš:</span><span class="sxs-lookup"><span data-stu-id="08da8-112">You can:</span></span>  
  
-   <span data-ttu-id="08da8-113">Naplnění **datovou sadu** pomocí schématu (tedy relační struktura) a data a pak proveďte synchronizaci s novou **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="08da8-113">Populate a **DataSet** with schema (that is, a relational structure) and data and then synchronize it with a new **XmlDataDocument**.</span></span> <span data-ttu-id="08da8-114">To poskytuje hierarchické zobrazení stávající relační data.</span><span class="sxs-lookup"><span data-stu-id="08da8-114">This provides a hierarchical view of existing relational data.</span></span> <span data-ttu-id="08da8-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="08da8-115">For example:</span></span>  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema and data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema and data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    ```  
  
-   <span data-ttu-id="08da8-116">Naplnění **datovou sadu** se schématem pouze (například silného typu **datovou sadu**), synchronizovat se službou **XmlDataDocument**a pak můžete načíst  **XmlDataDocument** z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="08da8-116">Populate a **DataSet** with schema only (such as a strongly typed **DataSet**), synchronize it with an **XmlDataDocument**, and then load the **XmlDataDocument** from an XML document.</span></span> <span data-ttu-id="08da8-117">To poskytuje relační zobrazení stávající hierarchické data.</span><span class="sxs-lookup"><span data-stu-id="08da8-117">This provides a relational view of existing hierarchical data.</span></span> <span data-ttu-id="08da8-118">Názvy tabulek a názvy sloupců v vaše **datovou sadu** schématu shodovat s názvy elementů XML, které chcete synchronizovat se službou.</span><span class="sxs-lookup"><span data-stu-id="08da8-118">The table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="08da8-119">Toto porovnání se malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="08da8-119">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="08da8-120">Všimněte si, že schéma **datovou sadu** pouze musí odpovídat elementů XML, které chcete vystavit v relačním zobrazení.</span><span class="sxs-lookup"><span data-stu-id="08da8-120">Note that the schema of the **DataSet** only needs to match the XML elements that you want to expose in your relational view.</span></span> <span data-ttu-id="08da8-121">Tímto způsobem může mít velký dokumentu XML a velmi malé relační "okna" na tomto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="08da8-121">This way, you can have a very large XML document and a very small relational "window" on that document.</span></span> <span data-ttu-id="08da8-122">**XmlDataDocument** zachovává celý dokument XML, i když **datovou sadu** zpřístupní pouze malou část.</span><span class="sxs-lookup"><span data-stu-id="08da8-122">The **XmlDataDocument** preserves the entire XML document even though the **DataSet** only exposes a small portion of it.</span></span> <span data-ttu-id="08da8-123">(Podrobný příklad tohoto najdete v tématu [synchronizace datovou sadu s XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)</span><span class="sxs-lookup"><span data-stu-id="08da8-123">(For a detailed example of this, see [Synchronizing a DataSet with an XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)</span></span>  
  
     <span data-ttu-id="08da8-124">Následující příklad kódu ukazuje postup vytvoření **datovou sadu** a naplnění schématem a synchronizaci se službou **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="08da8-124">The following code example shows the steps for creating a **DataSet** and populating its schema, then synchronizing it with an **XmlDataDocument**.</span></span> <span data-ttu-id="08da8-125">Všimněte si, že **datovou sadu** schématu pouze musí odpovídat elementy ze **XmlDataDocument** , kterou chcete vystavit pomocí **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="08da8-125">Note that the **DataSet** schema only needs to match the elements from the **XmlDataDocument** that you want to expose using the **DataSet**.</span></span>  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema, but not data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema, but not data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
     <span data-ttu-id="08da8-126">Nelze načíst **XmlDataDocument** Pokud synchronizovat se službou **datovou sadu** obsahující data.</span><span class="sxs-lookup"><span data-stu-id="08da8-126">You cannot load an **XmlDataDocument** if it is synchronized with a **DataSet** that contains data.</span></span> <span data-ttu-id="08da8-127">Bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="08da8-127">An exception will be thrown.</span></span>  
  
-   <span data-ttu-id="08da8-128">Vytvořte novou **XmlDataDocument** načíst z dokumentu XML a pak přístup relační zobrazení dat pomocí **datovou sadu** vlastnost **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="08da8-128">Create a new **XmlDataDocument** and load it from an XML document, and then access the relational view of the data using the **DataSet** property of the **XmlDataDocument**.</span></span> <span data-ttu-id="08da8-129">Je nutné nastavit schéma **datovou sadu** před zobrazením dat v **XmlDataDocument** pomocí **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="08da8-129">You need to set the schema of the **DataSet** before you can view any of the data in the **XmlDataDocument** using the **DataSet**.</span></span> <span data-ttu-id="08da8-130">Znovu, názvy názvy tabulek a sloupců ve vaší **datovou sadu** schématu shodovat s názvy elementů XML, které chcete synchronizovat se službou.</span><span class="sxs-lookup"><span data-stu-id="08da8-130">Again, the table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="08da8-131">Toto porovnání se malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="08da8-131">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="08da8-132">Následující příklad kódu ukazuje, jak pro přístup k relační zobrazení dat v **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="08da8-132">The following code example shows how to access the relational view of the data in an **XmlDataDocument**.</span></span>  
  
    ```vb  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument  
    Dim dataSet As DataSet = xmlDoc.DataSet  
  
    ' Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    XmlDataDocument xmlDoc = new XmlDataDocument();  
    DataSet dataSet = xmlDoc.DataSet;  
  
    // Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
 <span data-ttu-id="08da8-133">Další výhodou synchronizaci **XmlDataDocument** s **datovou sadu** je, že se zachová, i přesnost dokument XML.</span><span class="sxs-lookup"><span data-stu-id="08da8-133">Another advantage of synchronizing an **XmlDataDocument** with a **DataSet** is that the fidelity of an XML document is preserved.</span></span> <span data-ttu-id="08da8-134">Pokud **datovou sadu** se naplní ze dokument XML pomocí **ReadXml**, když data se nezapisují zpět jako dokument XML pomocí **WriteXml** můžou výrazně lišit od původní dokument XML.</span><span class="sxs-lookup"><span data-stu-id="08da8-134">If the **DataSet** is populated from an XML document using **ReadXml**, when the data is written back as an XML document using **WriteXml** it may differ dramatically from the original XML document.</span></span> <span data-ttu-id="08da8-135">Důvodem je, že **datovou sadu** nespravuje formátování, například mezera nebo hierarchické informace, například pořadí elementu z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="08da8-135">This is because the **DataSet** does not maintain formatting, such as white space, or hierarchical information, such as element order, from the XML document.</span></span> <span data-ttu-id="08da8-136">**Datovou sadu** také neobsahuje elementy z dokumentu XML, které byly ignorovány, protože neodpovídá schématu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="08da8-136">The **DataSet** also does not contain elements from the XML document that were ignored because they did not match the schema of the **Dataset**.</span></span> <span data-ttu-id="08da8-137">Synchronizace **XmlDataDocument** s **datovou sadu** umožňuje formátování a hierarchická struktura element původního dokumentu XML udržovat v **XmlDataDocument**, zatímco **datovou sadu** obsahuje pouze data schématu informace a vhodné **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="08da8-137">Synchronizing an **XmlDataDocument** with a **DataSet** allows the formatting and hierarchical element structure of the original XML document to be maintained in the **XmlDataDocument**, while the **DataSet** contains only data and schema information appropriate to the **DataSet**.</span></span>  
  
 <span data-ttu-id="08da8-138">Při synchronizaci **datovou sadu** s **XmlDataDocument**, výsledky se můžou lišit v závislosti na tom, jestli vaše <xref:System.Data.DataRelation> jsou vnořené objekty.</span><span class="sxs-lookup"><span data-stu-id="08da8-138">When synchronizing a **DataSet** with an **XmlDataDocument**, results may differ depending on whether or not your <xref:System.Data.DataRelation> objects are nested.</span></span> <span data-ttu-id="08da8-139">Další informace najdete v tématu [vnoření DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="08da8-139">For more information, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="08da8-140">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="08da8-140">In This Section</span></span>  
 [<span data-ttu-id="08da8-141">Synchronizace datové sady s datovým dokumentem XML</span><span class="sxs-lookup"><span data-stu-id="08da8-141">Synchronizing a DataSet with an XmlDataDocument</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 <span data-ttu-id="08da8-142">Demonstruje synchronizaci silného typu **datovou sadu**, s minimálním schématu s **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="08da8-142">Demonstrates synchronizing a strongly typed **DataSet**, with minimal schema, with an **XmlDataDocument**.</span></span>  
  
 [<span data-ttu-id="08da8-143">Provedení dotazu XPath u datové sady</span><span class="sxs-lookup"><span data-stu-id="08da8-143">Performing an XPath Query on a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 <span data-ttu-id="08da8-144">Demonstruje provádění dotazu XPath na obsah **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="08da8-144">Demonstrates performing an XPath query on the contents of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="08da8-145">Použití transformace XSLT u datové sady</span><span class="sxs-lookup"><span data-stu-id="08da8-145">Applying an XSLT Transform to a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 <span data-ttu-id="08da8-146">Demonstruje použití transformaci XSLT na obsah **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="08da8-146">Demonstrates applying an XSLT transform to the contents of a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="08da8-147">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="08da8-147">Related Sections</span></span>  
 [<span data-ttu-id="08da8-148">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="08da8-148">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="08da8-149">Popisuje, jak **datovou sadu** komunikuje s XML jako zdroj dat, včetně načítání a zachování obsahu **datovou sadu** jako XML data.</span><span class="sxs-lookup"><span data-stu-id="08da8-149">Describes how the **DataSet** interacts with XML as a data source, including loading and persisting the contents of a **DataSet** as XML data.</span></span>  
  
 [<span data-ttu-id="08da8-150">Vnoření datových relací</span><span class="sxs-lookup"><span data-stu-id="08da8-150">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 <span data-ttu-id="08da8-151">Popisuje význam vnořené **DataRelation** objekty při představující obsah **datovou sadu** jako data XML a popisuje, jak vytvořit tyto vztahy.</span><span class="sxs-lookup"><span data-stu-id="08da8-151">Discusses the importance of nested **DataRelation** objects when representing the contents of a **DataSet** as XML data, and describes how to create these relations.</span></span>  
  
 [<span data-ttu-id="08da8-152">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="08da8-152">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="08da8-153">Popisuje **datovou sadu** a způsobu jeho použití spravovat data aplikací a komunikovat s zdrojů dat včetně relačních databází a XML.</span><span class="sxs-lookup"><span data-stu-id="08da8-153">Describes the **DataSet** and how to use it to manage application data and to interact with data sources including relational databases and XML.</span></span>  
  
 <xref:System.Xml.XmlDataDocument>  
 <span data-ttu-id="08da8-154">Obsahuje referenční informace o **XmlDataDocument** třídy.</span><span class="sxs-lookup"><span data-stu-id="08da8-154">Contains reference information about the **XmlDataDocument** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08da8-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="08da8-155">See Also</span></span>  
 [<span data-ttu-id="08da8-156">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="08da8-156">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

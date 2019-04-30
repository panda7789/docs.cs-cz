---
title: Synchronizace datové sady a datového dokumentu XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: ea597d7caca3174b17ce16a1e9d70c022e3e75c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879811"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a><span data-ttu-id="32f83-102">Synchronizace datové sady a datového dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="32f83-102">DataSet and XmlDataDocument Synchronization</span></span>
<span data-ttu-id="32f83-103">ADO.NET <xref:System.Data.DataSet> vám poskytuje relační vyjádření data.</span><span class="sxs-lookup"><span data-stu-id="32f83-103">The ADO.NET <xref:System.Data.DataSet> provides you with a relational representation of data.</span></span> <span data-ttu-id="32f83-104">Hierarchický přístup k datům můžete použít třídy XML, který je k dispozici v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="32f83-104">For hierarchical data access, you can use the XML classes available in the .NET Framework.</span></span> <span data-ttu-id="32f83-105">Tyto dvě reprezentace dat v minulosti, již byly použity samostatně.</span><span class="sxs-lookup"><span data-stu-id="32f83-105">Historically, these two representations of data have been used separately.</span></span> <span data-ttu-id="32f83-106">Ale rozhraní .NET Framework umožňuje v reálném čase, která je synchronní přístup k relačních a hierarchických reprezentace dat prostřednictvím **datovou sadu** objektu a <xref:System.Xml.XmlDataDocument> objektu v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="32f83-106">However, the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the **DataSet** object and the <xref:System.Xml.XmlDataDocument> object, respectively.</span></span>  
  
 <span data-ttu-id="32f83-107">Při **datovou sadu** synchronizována s **XmlDataDocument**, oba objekty pracujete jediné datové sady.</span><span class="sxs-lookup"><span data-stu-id="32f83-107">When a **DataSet** is synchronized with an **XmlDataDocument**, both objects are working with a single set of data.</span></span> <span data-ttu-id="32f83-108">To znamená, že pokud je provedena změna **datovou sadu**, změna se projeví ve **XmlDataDocument**a naopak.</span><span class="sxs-lookup"><span data-stu-id="32f83-108">This means that if a change is made to the **DataSet**, the change will be reflected in the **XmlDataDocument**, and vice versa.</span></span> <span data-ttu-id="32f83-109">Vztah mezi **datovou sadu** a **XmlDataDocument** vytvoří velkou flexibilitu tím, že jednu aplikaci, pro přístup k celé sadě služeb vytvořených pomocí jediné sady dat kolem **datovou sadu** (jako je například ovládací prvky webových formulářů a Windows Forms a návrháři Visual Studio .NET), a také sadu XML služeb včetně XML Path, šablony stylů XSL (Extensible Language) a transformace XSL (XSLT) Jazyk (XPath).</span><span class="sxs-lookup"><span data-stu-id="32f83-109">The relationship between the **DataSet** and the **XmlDataDocument** creates great flexibility by allowing a single application, using a single set of data, to access the entire suite of services built around the **DataSet** (such as Web Forms and Windows Forms controls, and Visual Studio .NET designers), as well as the suite of XML services including Extensible Stylesheet Language (XSL), XSL Transformations (XSLT), and XML Path Language (XPath).</span></span> <span data-ttu-id="32f83-110">Není potřeba vybrat sadu služeb k cílové aplikaci; obě jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="32f83-110">You do not have to choose which set of services to target with the application; both are available.</span></span>  
  
 <span data-ttu-id="32f83-111">Existuje několik způsobů, které můžete synchronizovat **datovou sadu** s **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="32f83-111">There are several ways that you can synchronize a **DataSet** with an **XmlDataDocument**.</span></span> <span data-ttu-id="32f83-112">Můžete:</span><span class="sxs-lookup"><span data-stu-id="32f83-112">You can:</span></span>  
  
- <span data-ttu-id="32f83-113">Naplnit **datovou sadu** schéma (tedy relační struktury) a data a pak je synchronizovat s novou **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="32f83-113">Populate a **DataSet** with schema (that is, a relational structure) and data and then synchronize it with a new **XmlDataDocument**.</span></span> <span data-ttu-id="32f83-114">To poskytuje hierarchické zobrazení stávajících relačních dat.</span><span class="sxs-lookup"><span data-stu-id="32f83-114">This provides a hierarchical view of existing relational data.</span></span> <span data-ttu-id="32f83-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="32f83-115">For example:</span></span>  
  
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
  
- <span data-ttu-id="32f83-116">Naplnit **datovou sadu** jenom se schématem (jako jsou silného typu **datovou sadu**), proveďte synchronizaci s **XmlDataDocument**a pak načíst  **Objekt XmlDataDocument** z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="32f83-116">Populate a **DataSet** with schema only (such as a strongly typed **DataSet**), synchronize it with an **XmlDataDocument**, and then load the **XmlDataDocument** from an XML document.</span></span> <span data-ttu-id="32f83-117">To poskytuje relační zobrazení existující hierarchická data.</span><span class="sxs-lookup"><span data-stu-id="32f83-117">This provides a relational view of existing hierarchical data.</span></span> <span data-ttu-id="32f83-118">Názvy tabulek a názvy sloupců v vaše **datovou sadu** schématu musí odpovídat názvům elementů XML, které chcete synchronizovat se službou.</span><span class="sxs-lookup"><span data-stu-id="32f83-118">The table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="32f83-119">Tato shoda se malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="32f83-119">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="32f83-120">Všimněte si, že schéma **datovou sadu** potřebuje pouze tak, aby odpovídaly elementů XML, které chcete vystavit v relačním zobrazení.</span><span class="sxs-lookup"><span data-stu-id="32f83-120">Note that the schema of the **DataSet** only needs to match the XML elements that you want to expose in your relational view.</span></span> <span data-ttu-id="32f83-121">Tímto způsobem může mít velmi velké dokumentů XML a velmi malé relační "okno" pro daný dokument.</span><span class="sxs-lookup"><span data-stu-id="32f83-121">This way, you can have a very large XML document and a very small relational "window" on that document.</span></span> <span data-ttu-id="32f83-122">**XmlDataDocument** zachová celý dokument XML, i když **datovou sadu** zpřístupňuje pouze malou část.</span><span class="sxs-lookup"><span data-stu-id="32f83-122">The **XmlDataDocument** preserves the entire XML document even though the **DataSet** only exposes a small portion of it.</span></span> <span data-ttu-id="32f83-123">(Podrobný příklad tohoto objektu, najdete v části [synchronizace datové sady s datovým dokumentem XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)</span><span class="sxs-lookup"><span data-stu-id="32f83-123">(For a detailed example of this, see [Synchronizing a DataSet with an XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)</span></span>  
  
     <span data-ttu-id="32f83-124">Následující příklad kódu ukazuje postup vytvoření **datovou sadu** a naplnění jeho schématu, a synchronizace s **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="32f83-124">The following code example shows the steps for creating a **DataSet** and populating its schema, then synchronizing it with an **XmlDataDocument**.</span></span> <span data-ttu-id="32f83-125">Všimněte si, že **datovou sadu** pouze musí odpovídat prvky ze schématu **XmlDataDocument** , kterou chcete zpřístupnit pomocí **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="32f83-125">Note that the **DataSet** schema only needs to match the elements from the **XmlDataDocument** that you want to expose using the **DataSet**.</span></span>  
  
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
  
     <span data-ttu-id="32f83-126">Nelze načíst **XmlDataDocument** Pokud synchronizována s **datovou sadu** , který obsahuje data.</span><span class="sxs-lookup"><span data-stu-id="32f83-126">You cannot load an **XmlDataDocument** if it is synchronized with a **DataSet** that contains data.</span></span> <span data-ttu-id="32f83-127">bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="32f83-127">An exception will be thrown.</span></span>  
  
- <span data-ttu-id="32f83-128">Vytvořte nový **XmlDataDocument** a načtěte ho z dokumentu XML a pak přístup k relačním zobrazení dat pomocí **datovou sadu** vlastnost **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="32f83-128">Create a new **XmlDataDocument** and load it from an XML document, and then access the relational view of the data using the **DataSet** property of the **XmlDataDocument**.</span></span> <span data-ttu-id="32f83-129">Je nutné nastavit schéma **datovou sadu** před zobrazením datům v **XmlDataDocument** pomocí **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="32f83-129">You need to set the schema of the **DataSet** before you can view any of the data in the **XmlDataDocument** using the **DataSet**.</span></span> <span data-ttu-id="32f83-130">Znovu, názvy tabulek a sloupců názvy v vaše **datovou sadu** schématu musí odpovídat názvům elementů XML, které chcete synchronizovat se službou.</span><span class="sxs-lookup"><span data-stu-id="32f83-130">Again, the table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="32f83-131">Tato shoda se malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="32f83-131">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="32f83-132">Následující příklad kódu ukazuje, jak získat přístup k relačním zobrazení dat v **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="32f83-132">The following code example shows how to access the relational view of the data in an **XmlDataDocument**.</span></span>  
  
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
  
 <span data-ttu-id="32f83-133">Další výhodou synchronizace **XmlDataDocument** s **datovou sadu** je, že se zachová věrnost dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="32f83-133">Another advantage of synchronizing an **XmlDataDocument** with a **DataSet** is that the fidelity of an XML document is preserved.</span></span> <span data-ttu-id="32f83-134">Pokud **datovou sadu** se vyplní z dokumentu XML pomocí **ReadXml**, když se data zapíšou zpátky jako dokument XML pomocí **WriteXml** může výrazně lišit od původní dokument XML.</span><span class="sxs-lookup"><span data-stu-id="32f83-134">If the **DataSet** is populated from an XML document using **ReadXml**, when the data is written back as an XML document using **WriteXml** it may differ dramatically from the original XML document.</span></span> <span data-ttu-id="32f83-135">Je to proto, **datovou sadu** nespravuje formátování, například mezery nebo hierarchické informace, jako například pořadí elementů z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="32f83-135">This is because the **DataSet** does not maintain formatting, such as white space, or hierarchical information, such as element order, from the XML document.</span></span> <span data-ttu-id="32f83-136">**Datovou sadu** také neobsahuje prvky z dokumentu XML, které byly ignorovány, protože neodpovídá schématu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="32f83-136">The **DataSet** also does not contain elements from the XML document that were ignored because they did not match the schema of the **Dataset**.</span></span> <span data-ttu-id="32f83-137">Synchronizace **XmlDataDocument** s **datovou sadu** umožňuje formátování a hierarchické struktury elementu původního dokumentu XML na webu **XmlDataDocument**, zatímco **datovou sadu** obsahuje pouze data spolu se schématem informace, třeba **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="32f83-137">Synchronizing an **XmlDataDocument** with a **DataSet** allows the formatting and hierarchical element structure of the original XML document to be maintained in the **XmlDataDocument**, while the **DataSet** contains only data and schema information appropriate to the **DataSet**.</span></span>  
  
 <span data-ttu-id="32f83-138">Při synchronizaci **datovou sadu** s **XmlDataDocument**, výsledky můžou lišit v závislosti na tom, jestli se vaše <xref:System.Data.DataRelation> jsou vnořené objekty.</span><span class="sxs-lookup"><span data-stu-id="32f83-138">When synchronizing a **DataSet** with an **XmlDataDocument**, results may differ depending on whether or not your <xref:System.Data.DataRelation> objects are nested.</span></span> <span data-ttu-id="32f83-139">Další informace najdete v tématu [vnoření datových relací](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="32f83-139">For more information, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="32f83-140">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="32f83-140">In This Section</span></span>  
 [<span data-ttu-id="32f83-141">Synchronizace datové sady s datovým dokumentem XML</span><span class="sxs-lookup"><span data-stu-id="32f83-141">Synchronizing a DataSet with an XmlDataDocument</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 <span data-ttu-id="32f83-142">Ukazuje synchronizace silného typu **datovou sadu**, s minimálními schématu s **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="32f83-142">Demonstrates synchronizing a strongly typed **DataSet**, with minimal schema, with an **XmlDataDocument**.</span></span>  
  
 [<span data-ttu-id="32f83-143">Provedení dotazu XPath u datové sady</span><span class="sxs-lookup"><span data-stu-id="32f83-143">Performing an XPath Query on a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 <span data-ttu-id="32f83-144">Ukazuje provedení dotazu XPath na obsah **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="32f83-144">Demonstrates performing an XPath query on the contents of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="32f83-145">Použití transformace XSLT u datové sady</span><span class="sxs-lookup"><span data-stu-id="32f83-145">Applying an XSLT Transform to a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 <span data-ttu-id="32f83-146">Ukazuje použití transformace XSLT s obsahem **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="32f83-146">Demonstrates applying an XSLT transform to the contents of a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="32f83-147">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="32f83-147">Related Sections</span></span>  
 [<span data-ttu-id="32f83-148">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="32f83-148">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="32f83-149">Popisuje, jak **datovou sadu** komunikuje s XML jako zdroj dat, včetně načítání a při zachování obsahu **datovou sadu** jako XML data.</span><span class="sxs-lookup"><span data-stu-id="32f83-149">Describes how the **DataSet** interacts with XML as a data source, including loading and persisting the contents of a **DataSet** as XML data.</span></span>  
  
 [<span data-ttu-id="32f83-150">Vnoření datových relací</span><span class="sxs-lookup"><span data-stu-id="32f83-150">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 <span data-ttu-id="32f83-151">Tento článek popisuje význam vnořené **DataRelation** objekty při vyjadřování obsah **datovou sadu** jako data XML a popisuje, jak vytvořit tyto vztahy.</span><span class="sxs-lookup"><span data-stu-id="32f83-151">Discusses the importance of nested **DataRelation** objects when representing the contents of a **DataSet** as XML data, and describes how to create these relations.</span></span>  
  
 [<span data-ttu-id="32f83-152">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="32f83-152">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="32f83-153">Popisuje **datovou sadu** a jak ji používat ke správě dat aplikací a k interakci se zdroji dat, včetně relačních databází a XML.</span><span class="sxs-lookup"><span data-stu-id="32f83-153">Describes the **DataSet** and how to use it to manage application data and to interact with data sources including relational databases and XML.</span></span>  
  
 <xref:System.Xml.XmlDataDocument>  
 <span data-ttu-id="32f83-154">Obsahuje referenční informace o **XmlDataDocument** třídy.</span><span class="sxs-lookup"><span data-stu-id="32f83-154">Contains reference information about the **XmlDataDocument** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32f83-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32f83-155">See also</span></span>

- [<span data-ttu-id="32f83-156">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="32f83-156">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

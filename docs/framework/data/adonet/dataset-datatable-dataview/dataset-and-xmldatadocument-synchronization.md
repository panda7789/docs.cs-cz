---
title: Synchronizace datové sady a datového dokumentu XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: 3bbe28423385cae0f09f301c03b2b1a59edf101d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205066"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a><span data-ttu-id="0a1bb-102">Synchronizace datové sady a datového dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="0a1bb-102">DataSet and XmlDataDocument Synchronization</span></span>
<span data-ttu-id="0a1bb-103">ADO.NET <xref:System.Data.DataSet> poskytuje relační znázornění dat.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-103">The ADO.NET <xref:System.Data.DataSet> provides you with a relational representation of data.</span></span> <span data-ttu-id="0a1bb-104">Pro hierarchický přístup k datům můžete použít třídy XML, které jsou k dispozici v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-104">For hierarchical data access, you can use the XML classes available in the .NET Framework.</span></span> <span data-ttu-id="0a1bb-105">V minulosti se tato dvě reprezentace dat používala samostatně.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-105">Historically, these two representations of data have been used separately.</span></span> <span data-ttu-id="0a1bb-106">.NET Framework však umožňuje synchronní přístup k relačním i hierarchickému znázornění dat prostřednictvím objektu **DataSet** a <xref:System.Xml.XmlDataDocument> objektu v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-106">However, the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the **DataSet** object and the <xref:System.Xml.XmlDataDocument> object, respectively.</span></span>  
  
 <span data-ttu-id="0a1bb-107">Pokud je **datová sada** synchronizována s **objektu XmlDataDocument**, oba objekty pracují s jedinou sadou dat.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-107">When a **DataSet** is synchronized with an **XmlDataDocument**, both objects are working with a single set of data.</span></span> <span data-ttu-id="0a1bb-108">To znamená, že pokud je provedena změna v **datové sadě**, změna se projeví v **objektu XmlDataDocument**a naopak.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-108">This means that if a change is made to the **DataSet**, the change will be reflected in the **XmlDataDocument**, and vice versa.</span></span> <span data-ttu-id="0a1bb-109">Vztah mezi datovou **sadou** a **objektu XmlDataDocument** vytváří skvělou flexibilitu tím, že umožňuje jediné aplikaci, která používá jedinou sadu dat, přístup k celé sadě služeb postavené kolem **datové sady** (například webové formuláře a Ovládací prvky model Windows Forms a Visual Studio .NET Designer) a také sadu XML Services, včetně jazyka XSL (Extensible Stylesheet Language), XSL Transformes (XSLT) a jazyka XML Path (XPath).</span><span class="sxs-lookup"><span data-stu-id="0a1bb-109">The relationship between the **DataSet** and the **XmlDataDocument** creates great flexibility by allowing a single application, using a single set of data, to access the entire suite of services built around the **DataSet** (such as Web Forms and Windows Forms controls, and Visual Studio .NET designers), as well as the suite of XML services including Extensible Stylesheet Language (XSL), XSL Transformations (XSLT), and XML Path Language (XPath).</span></span> <span data-ttu-id="0a1bb-110">Nemusíte vybírat, kterou sadu služeb chcete s aplikací cílit; jsou k dispozici obě.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-110">You do not have to choose which set of services to target with the application; both are available.</span></span>  
  
 <span data-ttu-id="0a1bb-111">Existuje několik způsobů, jak můžete **datovou sadu** synchronizovat s **objektu XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-111">There are several ways that you can synchronize a **DataSet** with an **XmlDataDocument**.</span></span> <span data-ttu-id="0a1bb-112">Můžete:</span><span class="sxs-lookup"><span data-stu-id="0a1bb-112">You can:</span></span>  
  
- <span data-ttu-id="0a1bb-113">Naplňte **datovou sadu** pomocí schématu (tj. relační struktury) a dat a pak ji synchronizujte s novým **objektu XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-113">Populate a **DataSet** with schema (that is, a relational structure) and data and then synchronize it with a new **XmlDataDocument**.</span></span> <span data-ttu-id="0a1bb-114">Tato část poskytuje hierarchické zobrazení existujících relačních dat.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-114">This provides a hierarchical view of existing relational data.</span></span> <span data-ttu-id="0a1bb-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="0a1bb-115">For example:</span></span>  
  
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
  
- <span data-ttu-id="0a1bb-116">Naplňte **datovou sadu** pouze schématu (například **datovou sadu**se silnými typy), synchronizujte ji s **objektu XmlDataDocument**a pak načtěte **objektu XmlDataDocument** z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-116">Populate a **DataSet** with schema only (such as a strongly typed **DataSet**), synchronize it with an **XmlDataDocument**, and then load the **XmlDataDocument** from an XML document.</span></span> <span data-ttu-id="0a1bb-117">To poskytuje relační pohled na existující hierarchická data.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-117">This provides a relational view of existing hierarchical data.</span></span> <span data-ttu-id="0a1bb-118">Názvy tabulek a sloupců ve schématu **datové sady** se musí shodovat s názvy elementů XML, se kterými se mají synchronizovat.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-118">The table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="0a1bb-119">Toto porovnávání rozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-119">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="0a1bb-120">Všimněte si, že schéma **datové sady** musí odpovídat pouze elementům XML, které mají být vystavení v relačním zobrazení.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-120">Note that the schema of the **DataSet** only needs to match the XML elements that you want to expose in your relational view.</span></span> <span data-ttu-id="0a1bb-121">Tímto způsobem můžete mít velmi velký dokument XML a velmi malé relační "okno" v tomto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-121">This way, you can have a very large XML document and a very small relational "window" on that document.</span></span> <span data-ttu-id="0a1bb-122">**Objektu XmlDataDocument** zachovává celý dokument XML, i když **datová sada** zpřístupňuje jenom malou část.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-122">The **XmlDataDocument** preserves the entire XML document even though the **DataSet** only exposes a small portion of it.</span></span> <span data-ttu-id="0a1bb-123">(Podrobný příklad naleznete v tématu [synchronizace datové sady s objektu XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md).)</span><span class="sxs-lookup"><span data-stu-id="0a1bb-123">(For a detailed example of this, see [Synchronizing a DataSet with an XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md).)</span></span>  
  
     <span data-ttu-id="0a1bb-124">Následující příklad kódu ukazuje kroky pro vytvoření **datové sady** a naplnění schématu a následné synchronizaci s **objektu XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-124">The following code example shows the steps for creating a **DataSet** and populating its schema, then synchronizing it with an **XmlDataDocument**.</span></span> <span data-ttu-id="0a1bb-125">Všimněte si, že schéma **datové sady** musí odpovídat pouze prvkům z **objektu XmlDataDocument** , které chcete zpřístupnit pomocí **datové sady**.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-125">Note that the **DataSet** schema only needs to match the elements from the **XmlDataDocument** that you want to expose using the **DataSet**.</span></span>  
  
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
  
     <span data-ttu-id="0a1bb-126">Nelze načíst **objektu XmlDataDocument** , pokud je synchronizován s **datovou sadou** , která obsahuje data.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-126">You cannot load an **XmlDataDocument** if it is synchronized with a **DataSet** that contains data.</span></span> <span data-ttu-id="0a1bb-127">Vyvolá se výjimka.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-127">An exception will be thrown.</span></span>  
  
- <span data-ttu-id="0a1bb-128">Vytvořte nový **objektu XmlDataDocument** a načtěte ho z dokumentu XML a potom k relačnímu zobrazení dat použijte vlastnost **DataSet** třídy **objektu XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-128">Create a new **XmlDataDocument** and load it from an XML document, and then access the relational view of the data using the **DataSet** property of the **XmlDataDocument**.</span></span> <span data-ttu-id="0a1bb-129">Než budete moct zobrazit všechna data v **objektu XmlDataDocument** pomocí **datové sady**, musíte nastavit schéma **datové sady** .</span><span class="sxs-lookup"><span data-stu-id="0a1bb-129">You need to set the schema of the **DataSet** before you can view any of the data in the **XmlDataDocument** using the **DataSet**.</span></span> <span data-ttu-id="0a1bb-130">Názvy tabulek a názvy sloupců ve schématu **datové sady** se znovu musí shodovat s názvy elementů XML, se kterými se mají synchronizovat.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-130">Again, the table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="0a1bb-131">Toto porovnávání rozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-131">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="0a1bb-132">Následující příklad kódu ukazuje, jak získat přístup k relačnímu zobrazení dat v **objektu XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-132">The following code example shows how to access the relational view of the data in an **XmlDataDocument**.</span></span>  
  
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
  
 <span data-ttu-id="0a1bb-133">Další výhodou synchronizace **objektu XmlDataDocument** s datovou **sadou** je, že se zachová věrnost dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-133">Another advantage of synchronizing an **XmlDataDocument** with a **DataSet** is that the fidelity of an XML document is preserved.</span></span> <span data-ttu-id="0a1bb-134">Pokud je **datová sada** naplněna z dokumentu XML pomocí **ReadXml**, když jsou data zapsána zpět jako dokument XML pomocí **WriteXml** , může se výrazně lišit od původního dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-134">If the **DataSet** is populated from an XML document using **ReadXml**, when the data is written back as an XML document using **WriteXml** it may differ dramatically from the original XML document.</span></span> <span data-ttu-id="0a1bb-135">Důvodem je, že **datová sada** neuchovává formátování, jako jsou prázdné znaky nebo hierarchické informace, jako je například pořadí prvků, z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-135">This is because the **DataSet** does not maintain formatting, such as white space, or hierarchical information, such as element order, from the XML document.</span></span> <span data-ttu-id="0a1bb-136">**Datová sada** neobsahuje také prvky z dokumentu XML, které byly ignorovány, protože neodpovídaly schématu sady **dat**.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-136">The **DataSet** also does not contain elements from the XML document that were ignored because they did not match the schema of the **Dataset**.</span></span> <span data-ttu-id="0a1bb-137">Synchronizace **objektu XmlDataDocument** s datovou **sadou** umožňuje zachovat formátování a hierarchické struktury prvků původního dokumentu XML, který má být udržován v **objektu XmlDataDocument**, zatímco **datová sada** obsahuje pouze data a informace o schématu, které jsou vhodné pro **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-137">Synchronizing an **XmlDataDocument** with a **DataSet** allows the formatting and hierarchical element structure of the original XML document to be maintained in the **XmlDataDocument**, while the **DataSet** contains only data and schema information appropriate to the **DataSet**.</span></span>  
  
 <span data-ttu-id="0a1bb-138">Při synchronizaci **datové sady** s **objektu XmlDataDocument**se mohou výsledky lišit v závislosti na tom, zda <xref:System.Data.DataRelation> jsou objekty vnořené.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-138">When synchronizing a **DataSet** with an **XmlDataDocument**, results may differ depending on whether or not your <xref:System.Data.DataRelation> objects are nested.</span></span> <span data-ttu-id="0a1bb-139">Další informace najdete v tématu [vnořování datových vztahů](nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="0a1bb-139">For more information, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0a1bb-140">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0a1bb-140">In This Section</span></span>  
 [<span data-ttu-id="0a1bb-141">Synchronizace datové sady s datovým dokumentem XML</span><span class="sxs-lookup"><span data-stu-id="0a1bb-141">Synchronizing a DataSet with an XmlDataDocument</span></span>](synchronizing-a-dataset-with-an-xmldatadocument.md)  
 <span data-ttu-id="0a1bb-142">Ukazuje, jak synchronizovat silně typovou **datovou sadu**s minimálním schématem s **objektu XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-142">Demonstrates synchronizing a strongly typed **DataSet**, with minimal schema, with an **XmlDataDocument**.</span></span>  
  
 [<span data-ttu-id="0a1bb-143">Provedení dotazu XPath u datové sady</span><span class="sxs-lookup"><span data-stu-id="0a1bb-143">Performing an XPath Query on a DataSet</span></span>](performing-an-xpath-query-on-a-dataset.md)  
 <span data-ttu-id="0a1bb-144">Ukazuje, jak provést dotaz XPath na obsah **datové sady**.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-144">Demonstrates performing an XPath query on the contents of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="0a1bb-145">Použití transformace XSLT u datové sady</span><span class="sxs-lookup"><span data-stu-id="0a1bb-145">Applying an XSLT Transform to a DataSet</span></span>](applying-an-xslt-transform-to-a-dataset.md)  
 <span data-ttu-id="0a1bb-146">Ukazuje použití transformace XSLT na obsah **datové sady**.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-146">Demonstrates applying an XSLT transform to the contents of a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0a1bb-147">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0a1bb-147">Related Sections</span></span>  
 [<span data-ttu-id="0a1bb-148">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="0a1bb-148">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="0a1bb-149">Popisuje, jak **datová sada** komunikuje s XML jako zdroj dat, včetně načítání a uchovávání obsahu **datové sady** jako XML data.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-149">Describes how the **DataSet** interacts with XML as a data source, including loading and persisting the contents of a **DataSet** as XML data.</span></span>  
  
 [<span data-ttu-id="0a1bb-150">Vnoření datových relací</span><span class="sxs-lookup"><span data-stu-id="0a1bb-150">Nesting DataRelations</span></span>](nesting-datarelations.md)  
 <span data-ttu-id="0a1bb-151">Popisuje důležitost vnořených objektů **DataRelation** při reprezentaci obsahu **datové sady** jako XML dat a popisuje, jak tyto relace vytvořit.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-151">Discusses the importance of nested **DataRelation** objects when representing the contents of a **DataSet** as XML data, and describes how to create these relations.</span></span>  
  
 [<span data-ttu-id="0a1bb-152">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="0a1bb-152">DataSets, DataTables, and DataViews</span></span>](index.md)  
 <span data-ttu-id="0a1bb-153">Popisuje **datovou sadu** a její použití ke správě aplikačních dat a k interakci se zdroji dat, včetně relačních databází a XML.</span><span class="sxs-lookup"><span data-stu-id="0a1bb-153">Describes the **DataSet** and how to use it to manage application data and to interact with data sources including relational databases and XML.</span></span>  
  
 <xref:System.Xml.XmlDataDocument>  
 <span data-ttu-id="0a1bb-154">Obsahuje referenční informace o třídě **objektu XmlDataDocument** .</span><span class="sxs-lookup"><span data-stu-id="0a1bb-154">Contains reference information about the **XmlDataDocument** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a1bb-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a1bb-155">See also</span></span>

- [<span data-ttu-id="0a1bb-156">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="0a1bb-156">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

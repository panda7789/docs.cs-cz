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
# <a name="dataset-and-xmldatadocument-synchronization"></a>Datové sady a XmlDataDocument synchronizace
Technologie ADO.NET <xref:System.Data.DataSet> vám poskytne relační znázornění dat. Hierarchický přístup k datům můžete použít k dispozici v rozhraní .NET Framework XML třídy. Tyto dvě reprezentace dat v minulosti, již byly použity samostatně. Ale rozhraní .NET Framework umožňuje v reálném čase, synchronní přístup k hierarchické a relační reprezentace dat prostřednictvím **datovou sadu** objektu a <xref:System.Xml.XmlDataDocument> objektu v uvedeném pořadí.  
  
 Když **datovou sadu** je synchronizován se službou **XmlDataDocument**, jsou oba objekty práce s jedinou sadu dat. To znamená, že pokud dojde ke změně k **datovou sadu**, změna se projeví v **XmlDataDocument**a naopak. Vztah mezi **datovou sadu** a **XmlDataDocument** vytvoří flexibilitu tím, že jednu aplikaci, použití jedné sady dat, pro přístup k celé sadě služeb vytvořené kolem **datovou sadu** (například ovládací prvky webových formulářů a systém Windows Forms a sady Visual Studio .NET Designer), a také sadu služeb XML, včetně šablony stylů XSL (Extensible Language), XSL transformace XSLT () a cestu XML Jazyka (XPath). Nemáte vybrat sadu služeb k cíli s aplikací; obě možnosti jsou dostupné.  
  
 Existuje několik způsobů, které můžete synchronizovat **datovou sadu** s **XmlDataDocument**. Můžeš:  
  
-   Naplnění **datovou sadu** pomocí schématu (tedy relační struktura) a data a pak proveďte synchronizaci s novou **XmlDataDocument**. To poskytuje hierarchické zobrazení stávající relační data. Příklad:  
  
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
  
-   Naplnění **datovou sadu** se schématem pouze (například silného typu **datovou sadu**), synchronizovat se službou **XmlDataDocument**a pak můžete načíst  **XmlDataDocument** z dokumentu XML. To poskytuje relační zobrazení stávající hierarchické data. Názvy tabulek a názvy sloupců v vaše **datovou sadu** schématu shodovat s názvy elementů XML, které chcete synchronizovat se službou. Toto porovnání se malá a velká písmena.  
  
     Všimněte si, že schéma **datovou sadu** pouze musí odpovídat elementů XML, které chcete vystavit v relačním zobrazení. Tímto způsobem může mít velký dokumentu XML a velmi malé relační "okna" na tomto dokumentu. **XmlDataDocument** zachovává celý dokument XML, i když **datovou sadu** zpřístupní pouze malou část. (Podrobný příklad tohoto najdete v tématu [synchronizace datovou sadu s XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)  
  
     Následující příklad kódu ukazuje postup vytvoření **datovou sadu** a naplnění schématem a synchronizaci se službou **XmlDataDocument**. Všimněte si, že **datovou sadu** schématu pouze musí odpovídat elementy ze **XmlDataDocument** , kterou chcete vystavit pomocí **datovou sadu**.  
  
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
  
     Nelze načíst **XmlDataDocument** Pokud synchronizovat se službou **datovou sadu** obsahující data. Bude vyvolána výjimka.  
  
-   Vytvořte novou **XmlDataDocument** načíst z dokumentu XML a pak přístup relační zobrazení dat pomocí **datovou sadu** vlastnost **XmlDataDocument**. Je nutné nastavit schéma **datovou sadu** před zobrazením dat v **XmlDataDocument** pomocí **datovou sadu**. Znovu, názvy názvy tabulek a sloupců ve vaší **datovou sadu** schématu shodovat s názvy elementů XML, které chcete synchronizovat se službou. Toto porovnání se malá a velká písmena.  
  
     Následující příklad kódu ukazuje, jak pro přístup k relační zobrazení dat v **XmlDataDocument**.  
  
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
  
 Další výhodou synchronizaci **XmlDataDocument** s **datovou sadu** je, že se zachová, i přesnost dokument XML. Pokud **datovou sadu** se naplní ze dokument XML pomocí **ReadXml**, když data se nezapisují zpět jako dokument XML pomocí **WriteXml** můžou výrazně lišit od původní dokument XML. Důvodem je, že **datovou sadu** nespravuje formátování, například mezera nebo hierarchické informace, například pořadí elementu z dokumentu XML. **Datovou sadu** také neobsahuje elementy z dokumentu XML, které byly ignorovány, protože neodpovídá schématu **datovou sadu**. Synchronizace **XmlDataDocument** s **datovou sadu** umožňuje formátování a hierarchická struktura element původního dokumentu XML udržovat v **XmlDataDocument**, zatímco **datovou sadu** obsahuje pouze data schématu informace a vhodné **datovou sadu**.  
  
 Při synchronizaci **datovou sadu** s **XmlDataDocument**, výsledky se můžou lišit v závislosti na tom, jestli vaše <xref:System.Data.DataRelation> jsou vnořené objekty. Další informace najdete v tématu [vnoření DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Synchronizace datové sady s datovým dokumentem XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 Demonstruje synchronizaci silného typu **datovou sadu**, s minimálním schématu s **XmlDataDocument**.  
  
 [Provedení dotazu XPath u datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 Demonstruje provádění dotazu XPath na obsah **datovou sadu**.  
  
 [Použití transformace XSLT u datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 Demonstruje použití transformaci XSLT na obsah **datovou sadu**.  
  
## <a name="related-sections"></a>Související oddíly  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Popisuje, jak **datovou sadu** komunikuje s XML jako zdroj dat, včetně načítání a zachování obsahu **datovou sadu** jako XML data.  
  
 [Vnoření datových relací](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 Popisuje význam vnořené **DataRelation** objekty při představující obsah **datovou sadu** jako data XML a popisuje, jak vytvořit tyto vztahy.  
  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Popisuje **datovou sadu** a způsobu jeho použití spravovat data aplikací a komunikovat s zdrojů dat včetně relačních databází a XML.  
  
 <xref:System.Xml.XmlDataDocument>  
 Obsahuje referenční informace o **XmlDataDocument** třídy.  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

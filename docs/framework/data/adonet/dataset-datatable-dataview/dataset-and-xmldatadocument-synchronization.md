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
# <a name="dataset-and-xmldatadocument-synchronization"></a>Synchronizace datové sady a datového dokumentu XML
ADO.NET <xref:System.Data.DataSet> vám poskytuje relační vyjádření data. Hierarchický přístup k datům můžete použít třídy XML, který je k dispozici v rozhraní .NET Framework. Tyto dvě reprezentace dat v minulosti, již byly použity samostatně. Ale rozhraní .NET Framework umožňuje v reálném čase, která je synchronní přístup k relačních a hierarchických reprezentace dat prostřednictvím **datovou sadu** objektu a <xref:System.Xml.XmlDataDocument> objektu v uvedeném pořadí.  
  
 Při **datovou sadu** synchronizována s **XmlDataDocument**, oba objekty pracujete jediné datové sady. To znamená, že pokud je provedena změna **datovou sadu**, změna se projeví ve **XmlDataDocument**a naopak. Vztah mezi **datovou sadu** a **XmlDataDocument** vytvoří velkou flexibilitu tím, že jednu aplikaci, pro přístup k celé sadě služeb vytvořených pomocí jediné sady dat kolem **datovou sadu** (jako je například ovládací prvky webových formulářů a Windows Forms a návrháři Visual Studio .NET), a také sadu XML služeb včetně XML Path, šablony stylů XSL (Extensible Language) a transformace XSL (XSLT) Jazyk (XPath). Není potřeba vybrat sadu služeb k cílové aplikaci; obě jsou k dispozici.  
  
 Existuje několik způsobů, které můžete synchronizovat **datovou sadu** s **XmlDataDocument**. Můžete:  
  
- Naplnit **datovou sadu** schéma (tedy relační struktury) a data a pak je synchronizovat s novou **XmlDataDocument**. To poskytuje hierarchické zobrazení stávajících relačních dat. Příklad:  
  
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
  
- Naplnit **datovou sadu** jenom se schématem (jako jsou silného typu **datovou sadu**), proveďte synchronizaci s **XmlDataDocument**a pak načíst  **Objekt XmlDataDocument** z dokumentu XML. To poskytuje relační zobrazení existující hierarchická data. Názvy tabulek a názvy sloupců v vaše **datovou sadu** schématu musí odpovídat názvům elementů XML, které chcete synchronizovat se službou. Tato shoda se malá a velká písmena.  
  
     Všimněte si, že schéma **datovou sadu** potřebuje pouze tak, aby odpovídaly elementů XML, které chcete vystavit v relačním zobrazení. Tímto způsobem může mít velmi velké dokumentů XML a velmi malé relační "okno" pro daný dokument. **XmlDataDocument** zachová celý dokument XML, i když **datovou sadu** zpřístupňuje pouze malou část. (Podrobný příklad tohoto objektu, najdete v části [synchronizace datové sady s datovým dokumentem XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)  
  
     Následující příklad kódu ukazuje postup vytvoření **datovou sadu** a naplnění jeho schématu, a synchronizace s **XmlDataDocument**. Všimněte si, že **datovou sadu** pouze musí odpovídat prvky ze schématu **XmlDataDocument** , kterou chcete zpřístupnit pomocí **datovou sadu**.  
  
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
  
     Nelze načíst **XmlDataDocument** Pokud synchronizována s **datovou sadu** , který obsahuje data. bude vyvolána výjimka.  
  
- Vytvořte nový **XmlDataDocument** a načtěte ho z dokumentu XML a pak přístup k relačním zobrazení dat pomocí **datovou sadu** vlastnost **XmlDataDocument**. Je nutné nastavit schéma **datovou sadu** před zobrazením datům v **XmlDataDocument** pomocí **datovou sadu**. Znovu, názvy tabulek a sloupců názvy v vaše **datovou sadu** schématu musí odpovídat názvům elementů XML, které chcete synchronizovat se službou. Tato shoda se malá a velká písmena.  
  
     Následující příklad kódu ukazuje, jak získat přístup k relačním zobrazení dat v **XmlDataDocument**.  
  
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
  
 Další výhodou synchronizace **XmlDataDocument** s **datovou sadu** je, že se zachová věrnost dokumentu XML. Pokud **datovou sadu** se vyplní z dokumentu XML pomocí **ReadXml**, když se data zapíšou zpátky jako dokument XML pomocí **WriteXml** může výrazně lišit od původní dokument XML. Je to proto, **datovou sadu** nespravuje formátování, například mezery nebo hierarchické informace, jako například pořadí elementů z dokumentu XML. **Datovou sadu** také neobsahuje prvky z dokumentu XML, které byly ignorovány, protože neodpovídá schématu **datovou sadu**. Synchronizace **XmlDataDocument** s **datovou sadu** umožňuje formátování a hierarchické struktury elementu původního dokumentu XML na webu **XmlDataDocument**, zatímco **datovou sadu** obsahuje pouze data spolu se schématem informace, třeba **datovou sadu**.  
  
 Při synchronizaci **datovou sadu** s **XmlDataDocument**, výsledky můžou lišit v závislosti na tom, jestli se vaše <xref:System.Data.DataRelation> jsou vnořené objekty. Další informace najdete v tématu [vnoření datových relací](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Synchronizace datové sady s datovým dokumentem XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 Ukazuje synchronizace silného typu **datovou sadu**, s minimálními schématu s **XmlDataDocument**.  
  
 [Provedení dotazu XPath u datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 Ukazuje provedení dotazu XPath na obsah **datovou sadu**.  
  
 [Použití transformace XSLT u datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 Ukazuje použití transformace XSLT s obsahem **datovou sadu**.  
  
## <a name="related-sections"></a>Související oddíly  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Popisuje, jak **datovou sadu** komunikuje s XML jako zdroj dat, včetně načítání a při zachování obsahu **datovou sadu** jako XML data.  
  
 [Vnoření datových relací](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 Tento článek popisuje význam vnořené **DataRelation** objekty při vyjadřování obsah **datovou sadu** jako data XML a popisuje, jak vytvořit tyto vztahy.  
  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Popisuje **datovou sadu** a jak ji používat ke správě dat aplikací a k interakci se zdroji dat, včetně relačních databází a XML.  
  
 <xref:System.Xml.XmlDataDocument>  
 Obsahuje referenční informace o **XmlDataDocument** třídy.  
  
## <a name="see-also"></a>Viz také:

- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

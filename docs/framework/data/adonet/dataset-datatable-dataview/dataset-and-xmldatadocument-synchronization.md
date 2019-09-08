---
title: Synchronizace datové sady a datového dokumentu XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: e76e81153cb7d074fe975744c6b6041ee04be90f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785426"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a>Synchronizace datové sady a datového dokumentu XML
ADO.NET <xref:System.Data.DataSet> poskytuje relační znázornění dat. Pro hierarchický přístup k datům můžete použít třídy XML, které jsou k dispozici v .NET Framework. V minulosti se tato dvě reprezentace dat používala samostatně. .NET Framework však umožňuje synchronní přístup k relačním i hierarchickému znázornění dat prostřednictvím objektu **DataSet** a <xref:System.Xml.XmlDataDocument> objektu v reálném čase.  
  
 Pokud je **datová sada** synchronizována s **objektu XmlDataDocument**, oba objekty pracují s jedinou sadou dat. To znamená, že pokud je provedena změna v **datové sadě**, změna se projeví v **objektu XmlDataDocument**a naopak. Vztah mezi **datovou sadou** a **objektu XmlDataDocument** vytváří skvělou flexibilitu tím, že umožňuje jediné aplikaci, která používá jedinou sadu dat, přístup k celé sadě služeb postavené kolem **datové sady** (například webové formuláře a Ovládací prvky model Windows Forms a Visual Studio .NET Designer) a také sadu XML Services, včetně jazyka XSL (Extensible Stylesheet Language), XSL Transformes (XSLT) a jazyka XML Path (XPath). Nemusíte vybírat, kterou sadu služeb chcete s aplikací cílit; jsou k dispozici obě.  
  
 Existuje několik způsobů, jak můžete **datovou sadu** synchronizovat s **objektu XmlDataDocument**. Můžete:  
  
- Naplňte **datovou sadu** pomocí schématu (tj. relační struktury) a dat a pak ji synchronizujte s novým **objektu XmlDataDocument**. Tato část poskytuje hierarchické zobrazení existujících relačních dat. Příklad:  
  
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
  
- Naplňte **datovou sadu** pouze schématu (například **datovou sadu**se silnými typy), synchronizujte ji s **objektu XmlDataDocument**a pak načtěte **objektu XmlDataDocument** z dokumentu XML. To poskytuje relační pohled na existující hierarchická data. Názvy tabulek a sloupců ve schématu **datové sady** se musí shodovat s názvy elementů XML, se kterými se mají synchronizovat. Toto porovnávání rozlišuje velká a malá písmena.  
  
     Všimněte si, že schéma **datové sady** musí odpovídat pouze elementům XML, které mají být vystavení v relačním zobrazení. Tímto způsobem můžete mít velmi velký dokument XML a velmi malé relační "okno" v tomto dokumentu. **Objektu XmlDataDocument** zachovává celý dokument XML, i když **datová sada** zpřístupňuje jenom malou část. (Podrobný příklad naleznete v tématu [synchronizace datové sady s objektu XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md).)  
  
     Následující příklad kódu ukazuje kroky pro vytvoření **datové sady** a naplnění schématu a následné synchronizaci s **objektu XmlDataDocument**. Všimněte si, že schéma **datové sady** musí odpovídat pouze prvkům z **objektu XmlDataDocument** , které chcete zpřístupnit pomocí **datové sady**.  
  
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
  
     Nelze načíst **objektu XmlDataDocument** , pokud je synchronizován s **datovou sadou** , která obsahuje data. Vyvolá se výjimka.  
  
- Vytvořte nový **objektu XmlDataDocument** a načtěte ho z dokumentu XML a potom k relačnímu zobrazení dat použijte vlastnost **DataSet** třídy **objektu XmlDataDocument**. Než budete moct zobrazit všechna data v **objektu XmlDataDocument** pomocí **datové sady**, musíte nastavit schéma **datové sady** . Názvy tabulek a názvy sloupců ve schématu **datové sady** se znovu musí shodovat s názvy elementů XML, se kterými se mají synchronizovat. Toto porovnávání rozlišuje velká a malá písmena.  
  
     Následující příklad kódu ukazuje, jak získat přístup k relačnímu zobrazení dat v **objektu XmlDataDocument**.  
  
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
  
 Další výhodou synchronizace **objektu XmlDataDocument** s **datovou sadou** je, že se zachová věrnost dokumentu XML. Pokud je **datová sada** naplněna z dokumentu XML pomocí **ReadXml**, když jsou data zapsána zpět jako dokument XML pomocí **WriteXml** , může se výrazně lišit od původního dokumentu XML. Důvodem je, že **datová sada** neuchovává formátování, jako jsou prázdné znaky nebo hierarchické informace, jako je například pořadí prvků, z dokumentu XML. **Datová sada** neobsahuje také prvky z dokumentu XML, které byly ignorovány, protože neodpovídaly schématu sady **dat**. Synchronizace **objektu XmlDataDocument** s **datovou sadou** umožňuje zachovat formátování a hierarchické struktury prvků původního dokumentu XML, který má být udržován v **objektu XmlDataDocument**, zatímco **datová sada** obsahuje pouze data a informace o schématu, které jsou vhodné pro **datovou sadu**.  
  
 Při synchronizaci **datové sady** s **objektu XmlDataDocument**se mohou výsledky lišit v závislosti na tom, zda <xref:System.Data.DataRelation> jsou objekty vnořené. Další informace najdete v tématu [vnořování datových vztahů](nesting-datarelations.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Synchronizace datové sady s datovým dokumentem XML](synchronizing-a-dataset-with-an-xmldatadocument.md)  
 Ukazuje, jak synchronizovat silně typovou **datovou sadu**s minimálním schématem s **objektu XmlDataDocument**.  
  
 [Provedení dotazu XPath u datové sady](performing-an-xpath-query-on-a-dataset.md)  
 Ukazuje, jak provést dotaz XPath na obsah **datové sady**.  
  
 [Použití transformace XSLT u datové sady](applying-an-xslt-transform-to-a-dataset.md)  
 Ukazuje použití transformace XSLT na obsah **datové sady**.  
  
## <a name="related-sections"></a>Související oddíly  
 [Použití XML v datové sadě](using-xml-in-a-dataset.md)  
 Popisuje, jak **datová sada** komunikuje s XML jako zdroj dat, včetně načítání a uchovávání obsahu **datové sady** jako XML data.  
  
 [Vnoření datových relací](nesting-datarelations.md)  
 Popisuje důležitost vnořených objektů **DataRelation** při reprezentaci obsahu **datové sady** jako XML dat a popisuje, jak tyto relace vytvořit.  
  
 [Datové sady, datové tabulky a datová zobrazení](index.md)  
 Popisuje **datovou sadu** a její použití ke správě aplikačních dat a k interakci se zdroji dat, včetně relačních databází a XML.  
  
 <xref:System.Xml.XmlDataDocument>  
 Obsahuje referenční informace o třídě **objektu XmlDataDocument** .  
  
## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](../ado-net-overview.md)

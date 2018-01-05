---
title: "Načítání informací o schématu sady dat z XML"
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
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e41eb1168774a5ebfc17147f65901de0e432789f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="loading-dataset-schema-information-from-xml"></a>Načítání informací o schématu sady dat z XML
Schéma <xref:System.Data.DataSet> (jeho tabulek, sloupců, vztahů a omezení) je možné definovat prostřednictvím kódu programu, vytvořené **vyplnění** nebo **FillSchema** metody <xref:System.Data.Common.DataAdapter>, nebo načíst z Dokument XML. Načíst **datovou sadu** informace o schématu z dokumentu XML, můžete použít buď **ReadXmlSchema** nebo **InferXmlSchema** metodu **datovou sadu**. **ReadXmlSchema** umožňuje načíst nebo odvození **datovou sadu** informace o schématu z dokumentu obsahující schématu XML definition language (XSD) schématu nebo dokumentu XML se vloženého schématu XML. **InferXmlSchema** umožňuje odvození schématu z dokumentu XML při ignoruje určité obory názvů XML, který určíte.  
  
> [!NOTE]
>  Řazení v tabulce **datovou sadu** nemusí být zachová, i když používáte webové služby nebo serializace XML pro přenos **datovou sadu** v paměti, byla vytvořena pomocí XSD konstruktory (jako jsou vnořené relace). Proto příjemce **datovou sadu** by neměl závisí na tabulky v tomto případě řazení. Ale tabulky pořadí je vždy zachováno Pokud schéma **datovou sadu** přenášení byl načten z XSD souborů, namísto vytváří v paměti.  
  
## <a name="readxmlschema"></a>ReadXmlSchema  
 Načíst schéma **datovou sadu** z dokumentu XML bez načítání žádná data, můžete použít **ReadXmlSchema** metodu **datovou sadu**. **ReadXmlSchema** vytvoří **datovou sadu** schéma definované pomocí schématu XML definition language (XSD) schématu.  
  
 **ReadXmlSchema** metoda přebírá jediný argument název souboru, datového proudu, nebo **XmlReader** obsahující dokument XML, který má být načten. V dokumentu XML může obsahovat pouze schématu, nebo může obsahovat vložené schéma s elementů XML obsahující data. Podrobnosti o zápis vloženého schématu jako schématu XML najdete v tématu [odvozování relační strukturu datové sady z schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
 Pokud v dokumentu XML předaný **ReadXmlSchema** obsahuje žádné informace o schématu vložené **ReadXmlSchema** schéma z elementů v dokumentu XML odvodí. Pokud **datovou sadu** již obsahuje schéma, bude aktuální schéma rozšířeno přidáním nové tabulky, pokud dosud neexistují. Nové sloupce nebudou přidány do přidat do existující tabulky. Pokud sloupec se přidat, již existuje v **datovou sadu** , ale má nekompatibilní typ se sloupcem nalezen v souboru XML, je vyvolána výjimka. Podrobnosti o **ReadXmlSchema** odvodí schématu z dokumentu XML, najdete na stránce [odvození datovou sadu relační struktura z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).  
  
 I když **ReadXmlSchema** načte nebo odvodí pouze schéma **datovou sadu**, **ReadXml** metodu **datovou sadu** načte nebo odvodí, že oba schéma a data obsažená v dokumentu XML. Další informace najdete v tématu [načítání datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).  
  
 Následující příklady kódu ukazují, jak načíst **datovou sadu** schématu z dokumentu XML nebo datový proud. V prvním příkladu zobrazuje název souboru schématu XML je předán **ReadXmlSchema** metoda. Druhý příklad ukazuje **System.IO.StreamReader**.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As System.IO.StreamReader = New System.IO.StreamReader ("schema.xsd");  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema(xmlStream)  
xmlStream.Close()  
```  
  
```csharp  
System.IO.StreamReader xmlStream = new System.IO.StreamReader("schema.xsd");  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema(xmlStream);  
xmlStream.Close();  
```  
  
## <a name="inferxmlschema"></a>InferXmlSchema  
 Můžete také určit, aby **datovou sadu** odvodit jeho schématu z dokumentu XML pomocí **InferXmlSchema** metodu **datovou sadu**. **InferXmlSchema** funguje stejně jako proveďte obojí **ReadXml** s **XmlReadMode** z **InferSchema** (načte data a také odvodí, že schéma) a  **ReadXmlSchema** Pokud žádné vložené schéma obsahuje dokument, který je čten. Ale **InferXmlSchema** poskytuje další možnost umožňuje zadat konkrétní obory názvů XML, který se má ignorovat při je odvodit schématu. **InferXmlSchema** má dva vyžaduje argumenty: umístění v dokumentu XML určeného názvu souboru datového proudu, nebo **XmlReader**; a obory názvů XML, který se má ignorovat operací pole řetězců.  
  
 Zvažte například následující kód XML:  
  
```xml  
<NewDataSet xmlns:od="urn:schemas-microsoft-com:officedata">  
<Categories>  
  <CategoryID od:adotype="3">1</CategoryID>   
  <CategoryName od:maxLength="15" od:adotype="130">Beverages</CategoryName>   
  <Description od:adotype="203">Soft drinks and teas</Description>   
</Categories>  
<Products>  
  <ProductID od:adotype="20">1</ProductID>   
  <ReorderLevel od:adotype="3">10</ReorderLevel>   
  <Discontinued od:adotype="11">0</Discontinued>   
</Products>  
</NewDataSet>  
```  
  
 Z důvodu atributy určené pro prvky v předchozí dokument XML jak **ReadXmlSchema** metoda a **ReadXml** metoda s **XmlReadMode** z **InferSchema** by vytváření tabulek pro každý element v dokumentu: **kategorie**, **CategoryID**, **CategoryName**, **Popis**, **produkty**, **ProductID**, **MinimálníÚroveň**, a **zastaví**. (Další informace najdete v tématu [odvození datovou sadu relační struktura z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) Však může být vhodnější struktura vytvořit jenom **kategorie** a **produkty** tabulky a pak vytvořit **CategoryID**, **CategoryName** , a **popis** sloupců v **kategorie** tabulky, a **ProductID**, **MinimálníÚroveň**, a **Nákup ukončen** sloupců v **produkty** tabulky. K zajištění, že schéma odvozené ignoruje atributy určené v elementy XML, použijte **InferXmlSchema** metoda a zadejte obor názvů XML pro **officedata** budou ignorovány, jak je znázorněno Následující příklad.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a>Viz také  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Odvozování relační struktury datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [Odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

---
title: Načtení informací o schématu datové sady z XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: db0df68aa89cdd5c8bf94ad95a2b8bc9b36d5685
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786217"
---
# <a name="loading-dataset-schema-information-from-xml"></a>Načtení informací o schématu datové sady z XML
Schéma <xref:System.Data.DataSet> (jeho tabulky, sloupce, relace a omezení) lze definovat programově, vytvořené metodami <xref:System.Data.Common.DataAdapter> **Fill** nebo **FillSchema** , nebo načteny z dokumentu XML. Chcete-li načíst informace o schématu **datové sady** z dokumentu XML, lze použít metodu **ReadXmlSchema** nebo **InferXmlSchema** pro **datovou sadu**. **ReadXmlSchema** umožňuje načíst nebo odvodit informace o schématu **datové sady** z dokumentu, který obsahuje schéma XSD (XML Schema Definition Language), nebo dokumentu XML s vloženým schématem XML. **InferXmlSchema** umožňuje odvodit schéma z dokumentu XML a ignorovat určité obory názvů XML, které zadáte.  
  
> [!NOTE]
> Řazení tabulky v **sadě dat** nemusí být zachováno, pokud použijete webové služby nebo serializaci XML k přenosu **datové sady** , která byla vytvořena v paměti, pomocí konstrukcí XSD (jako jsou vnořené relace). Proto by příjemce **datové sady** neměl záviset na řazení tabulky v tomto případě. Řazení tabulky je však vždy zachované, pokud je schéma přenášené **datové sady** načteno ze souborů XSD namísto vytvoření v paměti.  
  
## <a name="readxmlschema"></a>ReadXmlSchema  
 Chcete-li načíst schéma **datové sady** z dokumentu XML bez načtení dat, můžete použít metodu **ReadXmlSchema** **datové sady**. **ReadXmlSchema** vytvoří schéma **datové sady** definované pomocí schématu XSD (XML Schema Definition Language).  
  
 Metoda **ReadXmlSchema** přijímá jeden argument názvu souboru, datový proud nebo objekt **XMLREADER** obsahující dokument XML, který má být načten. Dokument XML může obsahovat pouze schéma nebo může obsahovat schéma vložené s prvky XML obsahující data. Podrobnosti o zápisu vloženého schématu jako schématu XML naleznete v tématu [odvozování relační struktury datové sady ze schématu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
 Pokud dokument XML předaný do **ReadXmlSchema** neobsahuje žádné vložené informace o schématu, **ReadXmlSchema** bude odvodit schéma z prvků v dokumentu XML. Pokud **datová sada** již obsahuje schéma, aktuální schéma bude rozšířeno přidáním nových tabulek, pokud ještě neexistují. Do existujících tabulek nebudou přidány nové sloupce. Pokud již přidávaný sloupec v **datové sadě** existuje, ale má nekompatibilní typ se sloupcem nalezeným v kódu XML, je vyvolána výjimka. Podrobnosti o tom, jak **ReadXmlSchema** odvodí schéma z dokumentu XML, naleznete v tématu [odvození relační struktury datové sady z XML](inferring-dataset-relational-structure-from-xml.md).  
  
 I když **ReadXmlSchema** načítá nebo odvodí pouze schéma **datové sady**, metoda **ReadXml** **datové sady** načte nebo odvodí schéma i data obsažená v dokumentu XML. Další informace naleznete v tématu [načtení datové sady z XML](loading-a-dataset-from-xml.md).  
  
 Následující příklady kódu ukazují, jak načíst schéma **datové sady** z dokumentu XML nebo datového proudu. První příklad ukazuje název souboru schématu XML, který je předán metodě **ReadXmlSchema** . Druhý příklad ukazuje **System. IO. StreamReader**.  
  
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
 Můžete také instruovat **datovou sadu** , aby odvodit schéma z dokumentu XML pomocí metody **InferXmlSchema** **datové sady**. **InferXmlSchema** funguje stejně jako **ReadXml** s **XmlReadModeem** **InferSchema** (načítá data a také odvodit schéma) a **ReadXmlSchema** , pokud dokument, který čte, neobsahuje žádné vložené schéma. **InferXmlSchema** však poskytuje další funkce, které vám umožní určit konkrétní obory názvů XML, které se mají ignorovat při odvození schématu. **InferXmlSchema** přebírá dva povinné argumenty: umístění dokumentu XML, určené názvem souboru, datovým proudem nebo **XmlReader**; a pole řetězců pro obory názvů XML, které bude operace ignorovat.  
  
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
  
 Z důvodu atributů zadaných pro prvky v předchozím dokumentu XML, by metoda **ReadXmlSchema** a metoda **ReadXml** s **XmlReadModeem** **InferSchema** vytvořila tabulky pro každý prvek v dokumentů **Kategorie**, **KódKategorie**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**a **ukončeno**. (Další informace najdete v tématu [odvození relační struktury datové sady z XML](inferring-dataset-relational-structure-from-xml.md).) Vhodnější strukturou je však vytvořit pouze tabulky **Categories** a **Products** a následně vytvořit sloupce **KódKategorie**, **CategoryName**a **Description** v tabulce **categories (kategorie** ) a  **ProductID**, **ReorderLevel**a **vyřazené** sloupce v tabulce **Products** . Aby bylo zajištěno, že odvozené schéma ignoruje atributy zadané v elementech XML, použijte metodu **InferXmlSchema** a určete obor názvů XML pro **officedata** , jak je znázorněno v následujícím příkladu.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a>Viz také:

- [Použití XML v datové sadě](using-xml-in-a-dataset.md)
- [Odvozování relační struktury datové sady ze schématu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Odvození relační struktury datové sady z XML](inferring-dataset-relational-structure-from-xml.md)
- [Načtení datové sady z XML](loading-a-dataset-from-xml.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)

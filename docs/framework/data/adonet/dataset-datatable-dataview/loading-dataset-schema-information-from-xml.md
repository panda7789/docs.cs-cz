---
title: Načtení informací o schématu datové sady z XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 69994c546fea842ffef1c8c43d6d6f5bc35e0629
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151049"
---
# <a name="loading-dataset-schema-information-from-xml"></a>Načtení informací o schématu datové sady z XML
Schéma <xref:System.Data.DataSet> (jeho tabulky, sloupce, vztahy a omezení) lze definovat programově, vytvořené metodami **Fill** nebo **FillSchema** <xref:System.Data.Common.DataAdapter>aplikace , nebo načtené z dokumentu XML. Chcete-li načíst informace o schématu **DataSet** z dokumentu XML, můžete použít metodu **ReadXmlSchema** nebo **InferXmlSchema** **datové sady**. **ReadXmlSchema** umožňuje načíst nebo odvodit informace o schématu **DataSet** z dokumentu obsahujícího schéma jazyka definice schématu XML (XSD) nebo dokumentu XML s vložených schématem XML. **InferXmlSchema** umožňuje odvodit schéma z dokumentu XML při ignorování určitých oborů názvů XML, které zadáte.  
  
> [!NOTE]
> Pořadí tabulek v **datové sadě** nemusí být zachováno při použití webových služeb nebo serializace XML k přenosu **dataset,** který byl vytvořen v paměti pomocí xsd konstrukce (například vnořené vztahy). Proto příjemce **DataSet** by neměla záviset na pořadí tabulky v tomto případě. Pořadí tabulek je však vždy zachována, pokud schéma **DataSet** přenášené byl číst ze souborů XSD, namísto vytváření v paměti.  
  
## <a name="readxmlschema"></a>Readxmlschema  
 Chcete-li načíst schéma **datasady** z dokumentu XML bez načtení dat, můžete použít metodu **ReadXmlSchema** **dataset**. **ReadXmlSchema** vytvoří schéma **DataSet** definované pomocí schématu jazyka definice schématu XML (XSD).  
  
 Metoda **ReadXmlSchema** přebírá jeden argument názvu souboru, datového proudu nebo **xmlreaderu** obsahujícího načíst dokument XML. Dokument XML může obsahovat pouze schéma nebo může obsahovat schéma vložených s prvky XML obsahujícími data. Podrobnosti o zápisu vřádnického schématu jako schématu XML naleznete v [tématu Deriving DataSet Relační struktura ze schématu XML (XSD).](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
  
 Pokud dokument XML předaný **readxmlschem a** neobsahuje žádné informace o inline schématu, **readxmlschema** odvodí schéma z prvků v dokumentu XML. Pokud **DataSet** již obsahuje schéma, aktuální schéma bude rozšířeno přidáním nové tabulky, pokud již neexistují. Nové sloupce nebudou přidány do existujících tabulek. Pokud přidávaný sloupec již v **datové sadě** existuje, ale má nekompatibilní typ se sloupcem nalezeným ve formátu XML, je vyvolána výjimka. Podrobnosti o tom, jak **ReadXmlSchema** odvozuje schéma z dokumentu XML, naleznete [v tématu Odvození relační struktury datové sady z XML](inferring-dataset-relational-structure-from-xml.md).  
  
 Přestože **ReadXmlSchema** načte nebo odvodí pouze schéma **DataSet**, **ReadXml** metoda **DataSet** načte nebo odvodí schéma a data obsažená v dokumentu XML. Další informace naleznete [v tématu Loading a DataSet from XML](loading-a-dataset-from-xml.md).  
  
 Následující příklady kódu ukazují, jak načíst schéma **DataSet** z dokumentu XML nebo datového proudu. První příklad ukazuje název souboru schématu XML předávaný metodě **ReadXmlSchema.** Druhý příklad ukazuje **System.IO.StreamReader**.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As New System.IO.StreamReader("schema.xsd")
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
 Můžete také dát pokyn **DataSet** odvodit jeho schéma z dokumentu XML pomocí **InferXmlSchema** metoda **DataSet**. **InferXmlSchema** funguje stejně jako **readxml** s **XmlReadMode** **inferSchema** (načte data i infers schéma) a **ReadXmlSchema,** pokud čtený dokument neobsahuje žádné inline schéma. **InferXmlSchema** však poskytuje další možnost umožňuje zadat konkrétní obory názvů XML, které mají být ignorovány při odvození schématu. **InferXmlSchema** přebírá dva požadované argumenty: umístění dokumentu XML určené názvem souboru, datový proud nebo **XmlReader**; a pole názvů XML, které má být operací ignorováno.  
  
 Zvažte například následující xml:  
  
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
  
 Z důvodu atributů určených pro prvky v předchozím dokumentu XML by metoda **ReadXmlSchema** i metoda **ReadXml** s **xmlreadmode** **inferschema vytvořily** tabulky pro každý prvek v dokumentu: **Kategorie**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**a **Ukončeno**. (Další informace naleznete [v tématu Odvození relační struktury datové sady z jazyka XML](inferring-dataset-relational-structure-from-xml.md).) Vhodnější strukturou by však bylo vytvoření pouze **tabulek Kategorie** a **produkty** a potom vytvoření **sloupců CategoryID**, **CategoryName**a **Description** v tabulce **Kategorie** a **ProductID**, **ReorderLevel**a **Ukončeno** ve sloupcích V tabulce **Produkty.** Chcete-li zajistit, aby odvozené schéma ignorovalo atributy zadané v elementech XML, použijte metodu **InferXmlSchema** a zadejte obor názvů XML pro **data sady Office,** která mají být ignorována, jak je znázorněno v následujícím příkladu.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a>Viz také

- [Použití XML v datové sadě](using-xml-in-a-dataset.md)
- [Odvozování relační struktury datové sady ze schématu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Odvození relační struktury datové sady z XML](inferring-dataset-relational-structure-from-xml.md)
- [Načtení datové sady z XML](loading-a-dataset-from-xml.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)

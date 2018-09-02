---
title: Načítání informací o schématu datové sady z XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: a076dcbbe79a7ec0dfbd727e0d0c752bd4675eef
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398603"
---
# <a name="loading-dataset-schema-information-from-xml"></a>Načítání informací o schématu datové sady z XML
Schéma <xref:System.Data.DataSet> (jeho tabulky, sloupce, relace a omezení) lze definovat prostřednictvím kódu programu, vytvořené **vyplnit** nebo **FillSchema** metody <xref:System.Data.Common.DataAdapter>, nebo načtena z Dokument XML. Načíst **datovou sadu** informace o schématu z dokumentu XML, můžete použít buď **ReadXmlSchema** nebo **InferXmlSchema** metodu **datovésady**. **ReadXmlSchema** umožňuje načíst nebo odvodit **datovou sadu** informace o schématu z dokumentu obsahující jazyk (XSD) schématu definice schématu XML nebo dokument XML s vloženého schématu XML. **InferXmlSchema** umožňuje odvození schématu z dokumentu XML při ignoruje některé obory názvů XML, který zadáte.  
  
> [!NOTE]
>  Pořadí v tabulce **datovou sadu** nemusí být zachová, i když používáte webové služby nebo serializace XML pro přenos **datovou sadu** v paměti, který byl vytvořen pomocí konstrukce XSD (například vnořené relace). Proto příjemce **datovou sadu** neměli spoléhat na tabulky v tomto případě řazení. Ale tabulka pořadí je vždy zachováno Pokud schéma **datovou sadu** přenášených byl načten z soubory XSD, namísto vytváření v paměti.  
  
## <a name="readxmlschema"></a>ReadXmlSchema  
 Načíst schéma **datovou sadu** z dokumentu XML bez načtení všech dat, můžete použít **ReadXmlSchema** metodu **datovou sadu**. **ReadXmlSchema** vytvoří **datovou sadu** schéma, které jsou definovány pomocí jazyk (XSD) schématu definice schématu XML.  
  
 **ReadXmlSchema** metoda přijímá jeden argument názvu souboru datového proudu, nebo **XmlReader** obsahující dokumentu XML, který se má načíst. Dokument XML může obsahovat pouze schéma, nebo může obsahovat vložené schéma elementů XML obsahující data. Podrobnosti o vytváření vložené schéma jako schématu XML, naleznete v tématu [odvozování relační struktury datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
 Pokud dokument XML předán **ReadXmlSchema** neobsahuje žádné informace o schématu vložené **ReadXmlSchema** odvodí schéma z prvků v dokumentu XML. Pokud **datovou sadu** již obsahuje schéma s aktuální schéma rozšíříme přidáním nové tabulky, pokud ještě neexistují. Nové sloupce nebude přidán do přidat do existující tabulky. Pokud již přidán sloupec existuje v **datovou sadu** , ale má nekompatibilní typ se sloupcem nalezen v souboru XML, je vyvolána výjimka. Podrobné informace o tom **ReadXmlSchema** odvodí schéma z dokumentu XML, naleznete v tématu [odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).  
  
 I když **ReadXmlSchema** načte nebo odvodí schéma z **datovou sadu**, **ReadXml** metodu **datovou sadu** načte nebo odvodí obojí schéma a data obsažená v dokumentu XML. Další informace najdete v tématu [načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).  
  
 Následující příklady kódu ukazují, jak načíst **datovou sadu** schématu z dokumentu XML nebo datového proudu. První příklad ukazuje název souboru schématu XML předána **ReadXmlSchema** metody. Druhý příklad ukazuje **System.IO.StreamReader**.  
  
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
 Můžete taky nastavit **datovou sadu** odvodit jeho schématu z dokumentu XML pomocí **InferXmlSchema** metodu **datovou sadu**. **InferXmlSchema** funguje stejně jako obojí **ReadXml** s **XmlReadMode** z **InferSchema** (načte data stejně jako odvodí schéma) a **ReadXmlSchema** Pokud dokument čtená neobsahuje žádné vložené schéma. Ale **InferXmlSchema** poskytuje další možnost umožňuje zadat konkrétní obory názvů XML ignorován odvodit schéma. **InferXmlSchema** přebírá dva argumenty požadované: umístění dokumentu XML, které jsou určeny názvem souboru, datový proud nebo **XmlReader**; a pole řetězců oborů názvů XML pro operaci ignorovat.  
  
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
  
 Z důvodu atributy určené pro prvky v předchozí dokument XML jak **ReadXmlSchema** metoda a **ReadXml** metodu s **XmlReadMode** z **InferSchema** by vytvoření tabulek pro každý prvek v dokumentu: **kategorie**, **CategoryID**, **CategoryName**, **Popis**, **produkty**, **ProductID**, **MinimálníÚroveň**, a **ukončena**. (Další informace najdete v tématu [odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) Však může být vhodnější struktura vytvořit pouze **kategorie** a **produkty** tabulky a pak vytvořte **CategoryID**, **CategoryName** , a **popis** sloupců **kategorie** tabulky, a **ProductID**, **MinimálníÚroveň**, a **Vyřazeno** sloupců **produkty** tabulky. K zajištění, že odvozené schématu ignoruje atributy určené v elementů XML, použijte **InferXmlSchema** – metoda a určete obor názvů XML pro **officedata** ignorovány, jak je znázorněno Následující příklad.  
  
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
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

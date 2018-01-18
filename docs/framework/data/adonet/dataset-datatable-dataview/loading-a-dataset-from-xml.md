---
title: "Načítání datové sady z XML"
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
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1d0c98224b8b508fec5fe584388872757a9dfdf3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="loading-a-dataset-from-xml"></a>Načítání datové sady z XML
Obsah technologie ADO.NET <xref:System.Data.DataSet> lze vytvořit z datového proudu XML nebo dokumentu. Kromě toho s rozhraním .NET Framework máte flexibilitu přes načtení informací ze souboru XML a jak schéma nebo relační struktura <xref:System.Data.DataSet> je vytvořena.  
  
 K vyplnění <xref:System.Data.DataSet> s daty ze souboru XML, použijte **ReadXml** metodu <xref:System.Data.DataSet> objektu. **ReadXml** metoda čte z soubor datového proudu, nebo **XmlReader**a jako argumenty trvá zdroj XML plus volitelný **XmlReadMode** argument. (Další informace o **XmlReader**, najdete v části [NIB: čtení dat XML s XmlTextReader](http://msdn.microsoft.com/en-us/762c069b-b50c-41b8-936e-39eacfb0d540).) **ReadXml** metoda načte obsah datový proud XML nebo dokumentu a zatížení <xref:System.Data.DataSet> s daty. Vytvoří také relační schéma <xref:System.Data.DataSet> v závislosti na tom **XmlReadMode** zadaný a jestli relační schéma už existuje.  
  
 Následující tabulka popisuje možnosti **XmlReadMode** argument.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Auto**|Toto nastavení je výchozí. Prozkoumá XML a vybere nejvíc příslušnou možnost v následujícím pořadí:<br /><br /> – Pokud XML je prvek formátu DiffGram **formát DiffGram** se používá.<br />-Pokud <xref:System.Data.DataSet> obsahuje schéma nebo XML obsahuje vložené schéma, **ReadSchema** se používá.<br />-Pokud <xref:System.Data.DataSet> neobsahuje schéma a soubor XML neobsahuje vložené schéma, **InferSchema** se používá.<br /><br /> Pokud znáte formát XML, který je čten, pro nejlepší výkon doporučujeme, abyste nastavili explicitního **XmlReadMode**, spíš než přijmout **automaticky** výchozí.|  
|**ReadSchema**|Načte všechny vložené schéma a načte dat a schématu.<br /><br /> Pokud <xref:System.Data.DataSet> již obsahuje schéma, přidat nové tabulky z vloženého schématu existující schéma v <xref:System.Data.DataSet>. Pokud žádné tabulky v vloženého schématu již existuje v <xref:System.Data.DataSet>, je vyvolána výjimka. Nebudete moct změnit schéma existující tabulky pomocí **XmlReadMode.ReadSchema**.<br /><br /> Pokud <xref:System.Data.DataSet> neobsahuje schématu a neexistuje žádný vložené schéma, nenačtou žádná data.<br /><br /> Vložené schéma lze definovat pomocí schématu XML definition language (XSD) schématu. Podrobnosti o zápis vloženého schématu jako schématu XML najdete v tématu [odvozování relační strukturu datové sady z schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).|  
|**IgnoreSchema**|Ignoruje všechny vložené schéma a načte data do existující <xref:System.Data.DataSet> schématu. Všechna data, která neodpovídá existující schéma se zahodí. Pokud neexistuje žádné schéma v <xref:System.Data.DataSet>, je načtena žádná data.<br /><br /> Pokud jsou data formát DiffGram **IgnoreSchema** má stejné funkce jako **formát DiffGram** *.*|  
|**InferSchema**|Ignoruje všechny vložené schéma a odvodí, že schéma za strukturu dat XML a pak načte data.<br /><br /> Pokud <xref:System.Data.DataSet> již obsahuje schéma, je aktuální schéma rozšířeno přidáním sloupce do existující tabulky. Navíc tabulky se nepřidají, pokud nejsou existující tabulky. Pokud odvozené tabulky s jiný obor názvů již existuje, nebo pokud žádné odvozené sloupce v konfliktu s existující sloupce, je vyvolána výjimka.<br /><br /> Podrobnosti o **ReadXmlSchema** odvodí schématu z dokumentu XML, najdete na stránce [odvození datovou sadu relační struktura z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).|  
|**DiffGram**|Načte prvek formátu DiffGram a přidá data na aktuální schéma. **Formát DiffGram** nové řádky s existující kde jedinečný identifikátor hodnoty shodují, řádky sloučí. Najdete v části "Slučování dat z XML" na konci tohoto tématu. Další informace o DiffGrams najdete v tématu [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).|  
|**Fragment**|Pokračuje, dokud nebude dosaženo konce datový proud čtení více fragmentů kódu XML. Fragmenty, které odpovídají <xref:System.Data.DataSet> schématu se připojí k příslušné tabulky. Fragmenty, které neodpovídají <xref:System.Data.DataSet> schématu se zahodí.|  
  
> [!NOTE]
>  Pokud předáte **XmlReader** k **ReadXml** tedy umístěného součástí způsob dokument XML **ReadXml** na další uzel elementu, bude číst a který považovat kořenu Element čtení až do konce uzlu elementu. To neplatí zadáte-li **XmlReadMode.Fragment**.  
  
## <a name="dtd-entities"></a>DTD entity  
 Pokud soubor XML obsahuje entity definovaná ve schématu definice (DTD) typu dokumentu, bude vyvolána výjimka, pokud se pokus o načtení <xref:System.Data.DataSet> předáním soubor název, datový proud nebo bez ověřování **XmlReader** k  **ReadXml**. Místo toho je nutné vytvořit **třídy XmlValidatingReader**, s **EntityHandling příslušným** nastavena na **EntityHandling.ExpandEntities**a předejte vaší  **Třídy XmlValidatingReader** k **ReadXml**. **Třídy XmlValidatingReader** bude rozšiřovat entity před čtením <xref:System.Data.DataSet>.  
  
 Následující příklady kódu ukazují, jak načíst <xref:System.Data.DataSet> z datový proud XML. V prvním příkladu zobrazuje název souboru je předán **ReadXml** metoda. Druhý příklad ukazuje řetězec, který obsahuje XML vrácení načíst pomocí <xref:System.IO.StringReader>.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema);  
```  
  
```vb  
Dim dataSet As DataSet = New DataSet  
Dim dataTable As DataTable = New DataTable("table1")  
dataTable.Columns.Add("col1", Type.GetType("System.String"))  
dataSet.Tables.Add(dataTable)  
  
Dim xmlData As String = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>"  
  
Dim xmlSR As System.IO.StringReader = New System.IO.StringReader(xmlData)  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
DataTable dataTable = new DataTable("table1");  
dataTable.Columns.Add("col1", typeof(string));  
dataSet.Tables.Add(dataTable);  
  
string xmlData = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>";  
  
System.IO.StringReader xmlSR = new System.IO.StringReader(xmlData);  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema);  
```  
  
> [!NOTE]
>  Když zavoláte **ReadXml** načíst velmi velký soubor, se můžete setkat nízký výkon. K zajištění nejlepšího výkonu pro **ReadXml**, na velký soubor, volání <xref:System.Data.DataTable.BeginLoadData%2A> metoda pro každou tabulku v <xref:System.Data.DataSet>a pak zavolají **ReadXml**. Nakonec volání <xref:System.Data.DataTable.EndLoadData%2A> pro každou tabulku v <xref:System.Data.DataSet>, jak je znázorněno v následujícím příkladu.  
  
```vb  
Dim dataTable As DataTable  
  
For Each dataTable In dataSet.Tables  
   dataTable.BeginLoadData()  
Next  
  
dataSet.ReadXml("file.xml")  
  
For Each dataTable in dataSet.Tables  
   dataTable.EndLoadData()  
Next  
```  
  
```csharp  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.BeginLoadData();  
  
dataSet.ReadXml("file.xml");   
  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.EndLoadData();  
```  
  
> [!NOTE]
>  Pokud schéma XSD pro vaše <xref:System.Data.DataSet> zahrnuje **cílový obor názvů**, nemusí být načtena data a výjimkami, může dojít, pokud volání **ReadXml** načíst <xref:System.Data.DataSet> se souborem XML, který obsahuje prvky s žádné opravňující oboru názvů. V takovém případě číst nekvalifikované prvky, nastavení **elementFormDefault** rovno "kvalifikovaný" v schéma XSD. Příklad:  
  
```xml  
<xsd:schema id="customDataSet"   
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"   
  xmlns="http://www.tempuri.org/customDataSet.xsd"   
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a>Slučování dat z XML  
 Pokud <xref:System.Data.DataSet> už obsahuje data, přidávání nových dat z XML s daty, která je již v <xref:System.Data.DataSet>. **ReadXml** nesloučí z XML do <xref:System.Data.DataSet> žádný řádek informace s odpovídajícími primárními klíči. Pokud chcete přepsat existující řádek informace se novými informacemi ze souboru XML, použijte **ReadXml** pro vytvoření nového <xref:System.Data.DataSet>a potom <xref:System.Data.DataSet.Merge%2A> nové <xref:System.Data.DataSet> do existujících <xref:System.Data.DataSet>. Všimněte si, že načtení formát DiffGram pomocí **ReadXML** s **XmlReadMode** z **formát DiffGram** bude Sloučit řádky, které mají stejný jedinečný identifikátor.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [Odvozování relační struktury datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [Odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Načtení informací o schématu datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

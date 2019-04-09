---
title: Načtení datové sady z XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 0c53e3a15bcbe61db7da1edb31ecd3fd562603f5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099893"
---
# <a name="loading-a-dataset-from-xml"></a>Načtení datové sady z XML
Obsah technologie ADO.NET <xref:System.Data.DataSet> lze vytvořit z datový proud XML nebo dokumentu. Kromě toho, s použitím rozhraní .NET Framework máte velkou flexibilitu nad načtení informací ze souboru XML a jak schématu nebo relační struktura <xref:System.Data.DataSet> se vytvoří.  
  
 K vyplnění <xref:System.Data.DataSet> s daty ze souboru XML, použijte **ReadXml** metodu <xref:System.Data.DataSet> objektu. **ReadXml** metoda načteme soubor datového proudu, nebo **XmlReader**a jako argumenty přijímá zdrojový soubor XML a volitelně **XmlReadMode** argument. Další informace o **XmlReader**, naleznete v tématu [čtení dat XML pomocí XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)). **ReadXml** metoda přečte obsah datový proud XML nebo dokumentu a zatížením <xref:System.Data.DataSet> s daty. Vytvoří také relační schéma <xref:System.Data.DataSet> v závislosti na tom **XmlReadMode** zadaný a jestli relační schéma už existuje.  
  
 Následující tabulka popisuje možnosti pro **XmlReadMode** argument.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Auto**|Toto nastavení je výchozí. Zkontroluje kód XML a zvolí nejvhodnější možnost v následujícím pořadí:<br /><br /> – Pokud kód XML má formát DiffGram, **formát DiffGram** se používá.<br />– Pokud <xref:System.Data.DataSet> obsahuje schéma nebo kód XML obsahuje vložené schéma, **ReadSchema** se používá.<br />– Pokud <xref:System.Data.DataSet> neobsahuje schéma a soubor XML neobsahuje vložené schéma, **InferSchema** se používá.<br /><br /> Pokud znáte formátu XML, který je čten, pro zajištění nejlepšího výkonu se doporučuje nastavit explicitní **XmlReadMode**, spíše než přijmout **automaticky** výchozí.|  
|**ReadSchema**|Přečte všechny vložené schéma a načítá data a schéma.<br /><br /> Pokud <xref:System.Data.DataSet> již obsahuje schéma, jsou přidány nové tabulky z vložené schéma stávající schéma v <xref:System.Data.DataSet>. Pokud žádné tabulky ve vložené schéma už ve <xref:System.Data.DataSet>, je vyvolána výjimka. Není možné upravit schéma z existující tabulky pomocí **XmlReadMode.ReadSchema**.<br /><br /> Pokud <xref:System.Data.DataSet> neobsahuje schématu a neexistuje žádné vložené schéma, nenačtou žádná data.<br /><br /> Vložené schéma lze definovat pomocí jazyk (XSD) schématu definice schématu XML. Podrobnosti o vytváření vložené schéma jako schématu XML, naleznete v tématu [odvozování relační struktury datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).|  
|**IgnoreSchema**|Ignoruje všechny vložené schéma a načte data do existujících <xref:System.Data.DataSet> schématu. Všechna data, která se neshoduje s existujícím schématu se zahodí. Pokud neexistuje žádné schéma v <xref:System.Data.DataSet>, je načtena žádná data.<br /><br /> Pokud jsou data formát DiffGram **IgnoreSchema** má stejné funkce jako **formát DiffGram** *.*|  
|**InferSchema**|Ignoruje všechny vložené schéma a odvodí z něj schéma na struktuře dat XML a pak načte data.<br /><br /> Pokud <xref:System.Data.DataSet> již obsahuje schéma, je aktuální schéma rozšířeno přidáním sloupce do existující tabulky. Pokud nejsou existující tabulky se nepřidá další tabulky. Pokud odvozené tabulky s jiný obor názvů již existuje, nebo pokud všechny odvozené sloupce v konfliktu s existující sloupce, je vyvolána výjimka.<br /><br /> Podrobné informace o tom **ReadXmlSchema** odvodí schéma z dokumentu XML, naleznete v tématu [odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).|  
|**DiffGram**|Načte formát DiffGram a přidá data na aktuální schéma. **Formát DiffGram** sloučí s existující řádky kde jedinečný identifikátor hodnoty odpovídat nové řádky. Viz "Slučování dat z XML" na konci tohoto tématu. Další informace o DiffGrams najdete v tématu [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).|  
|**Fragment**|Pokračuje, dokud nebude dosaženo konce datového proudu pro čtení více fragmentů XML. Počet fragmentů, které odpovídají <xref:System.Data.DataSet> schématu jsou připojeny k příslušné tabulky. Fragmenty, které neodpovídají <xref:System.Data.DataSet> schématu se zahodí.|  
  
> [!NOTE]
>  Pokud předáte **XmlReader** k **ReadXml** , který je umístěný součástí tak, jak do dokumentu XML, **ReadXml** budou pro čtení k dalším uzlu elementu a bude zacházet s, která jako kořenový adresář element, až do konce uzlu elementu pouze pro čtení. Tato akce není požadována při zadání **XmlReadMode.Fragment**.  
  
## <a name="dtd-entities"></a>Entity DTD  
 Pokud soubor XML obsahuje entity, které jsou definované ve schématu dokumentu typ definice (DTD), bude vyvolána výjimka, pokud se pokusíte načíst <xref:System.Data.DataSet> předáním souboru název, datový proud nebo bez ověřování **XmlReader** k  **ReadXml**. Místo toho je nutné vytvořit **objekt XmlValidatingReader**, s **EntityHandling příslušným** nastavena na **se element EntityHandling.ExpandEntities**a předat vaše  **Objekt XmlValidatingReader** k **ReadXml**. **Objekt XmlValidatingReader** se rozbalí entity před čtením <xref:System.Data.DataSet>.  
  
 Následující příklady kódu ukazují, jak načíst <xref:System.Data.DataSet> z datový proud XML. První příklad ukazuje, názvu souboru, který je předáván **ReadXml** metody. Druhý příklad ukazuje řetězec, který obsahuje XML je načíst s použitím <xref:System.IO.StringReader>.  
  
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
>  Při volání **ReadXml** načíst velmi velkých souborů, může dojít nízký výkon. K zajištění nejlepšího výkonu pro **ReadXml**, na velkých souborů, zavolejte <xref:System.Data.DataTable.BeginLoadData%2A> metoda pro každou tabulku v <xref:System.Data.DataSet>a pak vyvolejte **ReadXml**. Nakonec proveďte volání <xref:System.Data.DataTable.EndLoadData%2A> za každou tabulku <xref:System.Data.DataSet>, jak je znázorněno v následujícím příkladu.  
  
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
>  Pokud schéma XSD pro vaše <xref:System.Data.DataSet> zahrnuje **oborem názvů targetNamespace**, nemusí být data načtena a mohou nastat výjimky, při volání metody **ReadXml** načíst <xref:System.Data.DataSet> s XML, který obsahuje elementy bez kvalifikovaného oboru názvů. Chcete-li načíst nekvalifikované elementy v tomto případě, nastavte **elementFormDefault** na hodnotu "qualified" ve schématu XSD. Příklad:  
  
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
 Pokud <xref:System.Data.DataSet> již obsahuje data, budou přidána nová data z XML do datového již v <xref:System.Data.DataSet>. **ReadXml** nesloučí ze souboru XML do <xref:System.Data.DataSet> žádný řádek informace s odpovídajícími primárních klíčů. Chcete-li přepsat existující řádek informace novými informacemi ze souboru XML, použijte **ReadXml** k vytvoření nového <xref:System.Data.DataSet>a potom <xref:System.Data.DataSet.Merge%2A> nové <xref:System.Data.DataSet> do existujících <xref:System.Data.DataSet>. Všimněte si, že načtení formát DiffGram pomocí **ReadXML** s **XmlReadMode** z **formát DiffGram** sloučí řádky, které mají stejný jedinečný identifikátor.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)
- [Odvozování relační struktury datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [Načtení informací o schématu datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

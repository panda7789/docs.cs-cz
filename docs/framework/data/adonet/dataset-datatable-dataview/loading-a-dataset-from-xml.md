---
title: Načtení datové sady z XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 4c8b26651a1f4050145b6d43e03f9d4cc3d68202
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785278"
---
# <a name="loading-a-dataset-from-xml"></a>Načtení datové sady z XML
Obsah ADO.NET <xref:System.Data.DataSet> lze vytvořit z datového proudu XML nebo dokumentu. Kromě toho s .NET Framework máte skvělou flexibilitu nad tím, které informace jsou načteny z XML a jak se vytváří schéma nebo relační struktura <xref:System.Data.DataSet> .  
  
 Chcete-li <xref:System.Data.DataSet> vyplnit data z XML, použijte metodu <xref:System.Data.DataSet> ReadXml objektu. Metoda **ReadXml** čte ze souboru, datového proudu nebo objektu **XmlReader**a přijímá jako argumenty zdroj XML a volitelný argument **XmlReadMode** . Další informace o objektu **XmlReader**najdete v tématu věnovaném [čtení dat XML pomocí třídy XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)). Metoda **ReadXml** čte obsah datového proudu XML nebo dokumentu a načítá <xref:System.Data.DataSet> data. Vytvoří také relační schéma <xref:System.Data.DataSet> v závislosti na zadané **XmlReadMode** a nezávisle na tom, zda relační schéma již existuje.  
  
 Následující tabulka popisuje možnosti pro argument **XmlReadMode** .  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Auto**|Toto nastavení je výchozí. Ověří XML a zvolí nejvhodnější možnost v následujícím pořadí:<br /><br /> – Pokud je kód XML formátu DiffGram, použije se formát **DiffGram** .<br />– Pokud <xref:System.Data.DataSet> obsahuje schéma nebo XML obsahuje vložené schéma, použije se **ReadSchema** .<br />– Pokud <xref:System.Data.DataSet> neobsahuje schéma a XML neobsahuje vložené schéma, použije se **InferSchema** .<br /><br /> Pokud znáte formát XML, který je právě čten, doporučujeme pro nejlepší výkon nastavit explicitní **XmlReadMode**místo toho, abyste přijali **Automatické** výchozí hodnoty.|  
|**ReadSchema**|Přečte jakékoli vložené schéma a načte data a schéma.<br /><br /> Pokud již schéma obsahuje, přidají se nové tabulky z vloženého schématu do stávajícího schématu <xref:System.Data.DataSet>v. <xref:System.Data.DataSet> Pokud některé tabulky ve vloženém schématu již existují v <xref:System.Data.DataSet>, je vyvolána výjimka. Schéma existující tabulky nebudete moct změnit pomocí **XmlReadMode. ReadSchema**.<br /><br /> <xref:System.Data.DataSet> Pokud neobsahuje schéma a není k dispozici žádné vložené schéma, nebudou čtena žádná data.<br /><br /> Vložené schéma lze definovat pomocí schématu XML Schema Definition Language (XSD). Podrobnosti o zápisu vloženého schématu jako schématu XML naleznete v tématu [odvozování relační struktury datové sady ze schématu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).|  
|**IgnoreSchema**|Ignoruje všechna vložená schémata a načte data do stávajícího <xref:System.Data.DataSet> schématu. Všechna data, která neodpovídají existujícímu schématu, budou zahozena. Pokud v <xref:System.Data.DataSet>nástroji neexistuje žádné schéma, nejsou načtena žádná data.<br /><br /> Pokud jsou data formátem DiffGram, **ignoreschema** má stejné funkce jako formát **DiffGram** *.*|  
|**InferSchema**|Ignoruje všechna vložená schématu a odvodí schéma podle struktury dat XML a potom načte data.<br /><br /> <xref:System.Data.DataSet> Pokud již schéma obsahuje, aktuální schéma je rozšířeno přidáním sloupců do existujících tabulek. Pokud nejsou k dispozici žádné tabulky, nebudou přidány další tabulky. Výjimka je vyvolána, pokud již existuje odvozená tabulka s jiným oborem názvů, nebo pokud jsou všechny odvozené sloupce v konfliktu se stávajícími sloupci.<br /><br /> Podrobnosti o tom, jak **ReadXmlSchema** odvodí schéma z dokumentu XML, naleznete v tématu [odvození relační struktury datové sady z XML](inferring-dataset-relational-structure-from-xml.md).|  
|**Formát**|Přečte formát DiffGram a přidá data do aktuálního schématu. Formát **DiffGram** sloučí nové řádky se stávajícími řádky, kde se shodují hodnoty jedinečného identifikátoru. Viz téma "sloučení dat z XML" na konci tohoto tématu. Další informace o formátech DiffGram naleznete v tématu [DiffGram](diffgrams.md).|  
|**Zpomalen**|Pokračuje v čtení více fragmentů XML, dokud není dosaženo konce datového proudu. Fragmenty, které <xref:System.Data.DataSet> odpovídají schématu, jsou připojeny k příslušným tabulkám. Fragmenty, které neodpovídají <xref:System.Data.DataSet> schématu, jsou zahozeny.|  
  
> [!NOTE]
> Pokud předáte **třídu XmlReader** k **ReadXml** , která je umístěna do dokumentu XML, **ReadXml** se přečte do dalšího uzlu elementu a bude se považovat za kořenový prvek, který se bude načítat až do konce uzlu elementu. To se nevztahuje, pokud zadáte **XmlReadMode. fragment**.  
  
## <a name="dtd-entities"></a>Entity DTD  
 Pokud váš kód XML obsahuje entity definované v rámci schématu definice typu dokumentu (DTD), bude vyvolána výjimka, pokud se pokusíte načíst objekt <xref:System.Data.DataSet> předáním názvu souboru, datového proudu nebo neověření objektu **XmlReader** do **ReadXml**. Místo toho musíte vytvořit **XmlValidatingReader**s **EntityHandling** nastavenou na **EntityHandling. ExpandEntities**a předat **XmlValidatingReader** **ReadXml.** **XmlValidatingReader** rozšíří entity před jejich čtením <xref:System.Data.DataSet>.  
  
 Následující příklady kódu ukazují, jak načíst <xref:System.Data.DataSet> z datového proudu XML. První příklad ukazuje název souboru předávaný do metody **ReadXml** . Druhý příklad ukazuje řetězec, který obsahuje kód XML, který je načítán <xref:System.IO.StringReader>pomocí.  
  
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
> Pokud zavoláte **ReadXml** , abyste načetli velmi velký soubor, může dojít ke zpomalení výkonu. Pro zajištění nejlepšího výkonu pro **ReadXml**, ve velkém souboru volejte <xref:System.Data.DataTable.BeginLoadData%2A> metodu pro <xref:System.Data.DataSet>každou tabulku v a pak zavolejte **ReadXml**. Nakonec zavolejte <xref:System.Data.DataTable.EndLoadData%2A> pro každou tabulku <xref:System.Data.DataSet>v, jak je znázorněno v následujícím příkladu.  
  
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
> Pokud schéma <xref:System.Data.DataSet> XSD pro váš obsahuje **obor názvů targetNamespace**, data pravděpodobně nebudou načtena a při volání **ReadXml** pro načtení <xref:System.Data.DataSet> kódu XML, který obsahuje prvky bez kvalifikovaného oboru názvů, může dojít k výjimkám. Chcete-li v tomto případě číst nekvalifikované prvky, nastavte **elementFormDefault** ve schématu XSD na hodnotu kvalifikováno. Příklad:  
  
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
 Pokud již data obsahují, jsou nová data z XML přidána do dat, která jsou již přítomna <xref:System.Data.DataSet>v nástroji. <xref:System.Data.DataSet> **ReadXml** se nesloučí z kódu XML do <xref:System.Data.DataSet> žádné informace o řádku s vyhovujícími primárními klíči. Chcete-li přepsat stávající informace o řádcích novými informacemi z XML, vytvořte pomocí **ReadXml** nové <xref:System.Data.DataSet>a pak <xref:System.Data.DataSet.Merge%2A> nový <xref:System.Data.DataSet> do existující <xref:System.Data.DataSet>. Všimněte si, že načtení formátu DiffGram pomocí **ReadXml** s **XmlReadModeem** formátu **DiffGram** sloučí řádky, které mají stejný jedinečný identifikátor.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [Použití XML v datové sadě](using-xml-in-a-dataset.md)
- [DiffGrams](diffgrams.md)
- [Odvozování relační struktury datové sady ze schématu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Odvození relační struktury datové sady z XML](inferring-dataset-relational-structure-from-xml.md)
- [Načtení informací o schématu datové sady z XML](loading-dataset-schema-information-from-xml.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)

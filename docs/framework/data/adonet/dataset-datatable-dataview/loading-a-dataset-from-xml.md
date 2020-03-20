---
title: Načtení datové sady z XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: c21ed3bb31add285d64272040680433fff4e16fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151062"
---
# <a name="loading-a-dataset-from-xml"></a>Načtení datové sady z XML
Obsah ADO.NET <xref:System.Data.DataSet> lze vytvořit z datového proudu XML nebo dokumentu. Kromě toho s rozhraním .NET Framework máte velkou flexibilitu nad tím, jaké informace jsou načteny z XML a jak <xref:System.Data.DataSet> je vytvořeno schéma nebo relační struktura.  
  
 Chcete-li <xref:System.Data.DataSet> vyplnit data z XML, použijte <xref:System.Data.DataSet> metodu **ReadXml** objektu. Metoda **ReadXml** čte ze souboru, datového proudu nebo **xmlreaderu**a bere jako argumenty zdroj xml a volitelný argument **XmlReadMode.** Další informace o **aplikaci XmlReader**naleznete v [tématu Čtení dat XML pomocí aplikace XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)). Metoda **ReadXml** přečte obsah datového proudu XML <xref:System.Data.DataSet> nebo dokumentu a načte data. Vytvoří také relační schéma <xref:System.Data.DataSet> v závislosti na zadaném **xmlreadmode** a zda již existuje relační schéma.  
  
 Následující tabulka popisuje možnosti argumentu **XmlReadMode.**  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Automaticky**|Toto nastavení je výchozí. Zkontroluje XML a vybere nejvhodnější možnost v následujícím pořadí:<br /><br /> - Pokud je XML DiffGram, použije se **DiffGram.**<br />- Pokud <xref:System.Data.DataSet> obsahuje schéma nebo XML obsahuje inline schéma, **readschema** se používá.<br />- Pokud <xref:System.Data.DataSet> neobsahuje schéma a XML neobsahuje inline schéma, **inferSchema** se používá.<br /><br /> Pokud znáte formát přečteného jazyka XML, doporučujeme pro dosažení nejlepšího výkonu nastavit explicitní **režim XmlReadMode**, nikoli **přijmout výchozí hodnotu Automaticky.**|  
|**ReadSchema**|Přečte libovolné vložkové schéma a načte data a schéma.<br /><br /> Pokud <xref:System.Data.DataSet> již obsahuje schéma, nové tabulky jsou přidány z inline schématu do existujícího schématu <xref:System.Data.DataSet>v . Pokud všechny tabulky v inline schématu již <xref:System.Data.DataSet>existují v , je vyvolána výjimka. Schéma existující tabulky nebude možné upravit pomocí **souboru XmlReadMode.ReadSchema**.<br /><br /> Pokud <xref:System.Data.DataSet> neobsahuje schéma a neexistuje žádné inline schéma, jsou přečtena žádná data.<br /><br /> Inline schéma lze definovat pomocí schématu definice schématu XML (XSD). Podrobnosti o zápisu vřádnického schématu jako schématu XML naleznete v [tématu Deriving DataSet Relační struktura ze schématu XML (XSD).](deriving-dataset-relational-structure-from-xml-schema-xsd.md)|  
|**Ignorujíschema**|Ignoruje jakékoli vložkové schéma a načte <xref:System.Data.DataSet> data do existujícího schématu. Všechna data, která neodpovídá existujícímu schématu, jsou zahozena. Pokud v souboru <xref:System.Data.DataSet>neexistuje žádné schéma , nebudou načtena žádná data.<br /><br /> Pokud data je DiffGram, **IgnoreSchema** má stejné funkce jako **DiffGram** *.*|  
|**InferSchema**|Ignoruje jakékoli vložkové schéma a odvodí schéma podle struktury dat XML a pak data načte.<br /><br /> Pokud <xref:System.Data.DataSet> již obsahuje schéma, aktuální schéma je rozšířeno přidáním sloupců do existujících tabulek. Další tabulky nebudou přidány, pokud neexistují existující tabulky. Výjimka je vyvolána, pokud odvozená tabulka již existuje s jiným oborem názvů nebo pokud jsou odvozené sloupce v konfliktu s existujícími sloupci.<br /><br /> Podrobnosti o tom, jak **ReadXmlSchema** odvozuje schéma z dokumentu XML, naleznete [v tématu Odvození relační struktury datové sady z XML](inferring-dataset-relational-structure-from-xml.md).|  
|**Diffgram**|Přečte DiffGram a přidá data do aktuálního schématu. **DiffGram** sloučí nové řádky s existujícími řádky, kde se shodovat hodnoty jedinečného identifikátoru. Viz "Sloučení dat z XML" na konci tohoto tématu. Další informace o diffgrams naleznete v [tématu DiffGrams](diffgrams.md).|  
|**Fragment**|Pokračuje ve čtení více fragmentů XML, dokud není dosaženo konce datového proudu. Fragmenty, které <xref:System.Data.DataSet> odpovídají schématu jsou připojeny k příslušné tabulky. Fragmenty, které neodpovídají schématu <xref:System.Data.DataSet> jsou zahozeny.|  
  
> [!NOTE]
> Pokud předáte **XmlReader** **readxml,** který je umístěn část cesty do dokumentu XML, **ReadXml** bude číst do uzlu dalšího prvku a bude zacházet jako kořenový prvek, čtení až do konce uzlu elementu. To neplatí, pokud zadáte **XmlReadMode.Fragment**.  
  
## <a name="dtd-entities"></a>DTD entity  
 Pokud váš jazyk XML obsahuje entity definované ve schématu definice typu dokumentu (DTD), bude vyvolána výjimka, pokud se pokusíte **XmlReader** načíst **ReadXml** <xref:System.Data.DataSet> soubor ud. Místo toho je nutné vytvořit **XmlValidatingReader**, s **EntityHandling** nastavena **na EntityHandling.ExpandEntities**a předat **XmlValidatingReader** **readxml**. **XmlValidatingReader** rozšíří entity před čtením <xref:System.Data.DataSet>.  
  
 Následující příklady kódu ukazují, <xref:System.Data.DataSet> jak načíst datový proud XML. První příklad ukazuje název souboru předávaný metodě **ReadXml.** Druhý příklad ukazuje řetězec, který obsahuje <xref:System.IO.StringReader>xml načtený pomocí .  
  
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
> Pokud zavoláte **ReadXml** načíst velmi velký soubor, může dojít ke snížení výkonu. Chcete-li zajistit nejlepší výkon pro **readxml** <xref:System.Data.DataTable.BeginLoadData%2A> , ve velkém <xref:System.Data.DataSet>souboru volejte metodu pro každou tabulku v oblasti aplikace a potom zavolejte **ReadXml**. Nakonec volejte <xref:System.Data.DataTable.EndLoadData%2A> pro každou <xref:System.Data.DataSet>tabulku v , jak je znázorněno v následujícím příkladu.  
  
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
> Pokud schéma XSD pro vaše <xref:System.Data.DataSet> zahrnuje **targetNamespace**, data nemusí být číst a může dojít k výjimkám, při volání **ReadXml** načíst <xref:System.Data.DataSet> s XML, který obsahuje prvky bez opravňující obor názvů. Chcete-li číst neúplné prvky v tomto případě, nastavte **elementFormDefault** rovna "kvalifikované" ve schématu XSD. Například:  
  
```xml  
<xsd:schema id="customDataSet"
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"
  xmlns="http://www.tempuri.org/customDataSet.xsd"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a>Sloučení dat z XML  
 Pokud <xref:System.Data.DataSet> již obsahuje data, nová data z XML se přidají <xref:System.Data.DataSet>k datům, která jsou již v rozhraní . **ReadXml** se nesloučí <xref:System.Data.DataSet> z XML do žádné informace o řádku s odpovídající primární klíče. Chcete-li přepsat existující informace o řádcích novými informacemi z <xref:System.Data.DataSet.Merge%2A> XML, vytvořte pomocí **readxml** <xref:System.Data.DataSet>nového a potom nového <xref:System.Data.DataSet> do existujícího <xref:System.Data.DataSet>. Všimněte si, že načítání DiffGram pomocí **ReadXML** s **XmlReadMode** **DiffGram** sloučí řádky, které mají stejný jedinečný identifikátor.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [Použití XML v datové sadě](using-xml-in-a-dataset.md)
- [DiffGrams](diffgrams.md)
- [Odvozování relační struktury datové sady ze schématu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Odvození relační struktury datové sady z XML](inferring-dataset-relational-structure-from-xml.md)
- [Načtení informací o schématu datové sady z XML](loading-dataset-schema-information-from-xml.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)

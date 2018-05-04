---
title: DiffGrams
ms.date: 03/30/2017
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
ms.openlocfilehash: 2b04fd69af94ce49fb5973af5ac74c2933fe58bf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="diffgrams"></a>DiffGrams
Prvek formátu DiffGram je formátu XML, který identifikuje aktuální a původní verze datové prvky. <xref:System.Data.DataSet> Používá formát DiffGram formát pro načtení a zachovat její obsah a k serializaci její obsah pro přenos přes síťové připojení. Když <xref:System.Data.DataSet> je zapsána jako formát DiffGram, vyplní formát DiffGram všechny potřebné informace přesně znovu vytvořit obsah, když není schéma služby <xref:System.Data.DataSet>, včetně hodnoty ve sloupcích i **původní** a **aktuální** verze řádku, řádku informace o chybě a pořadí řádků.  
  
 Při odesílání a načítání <xref:System.Data.DataSet> z webové služby XML, je implicitně použít formát DiffGram formát. Kromě toho při načítání obsahu <xref:System.Data.DataSet> pomocí XML **ReadXml** metoda, nebo při zápisu obsahu <xref:System.Data.DataSet> v XML pomocí **WriteXml** metodu, můžete zadat aby se obsah lze číst nebo zapisovat jako prvek formátu DiffGram. Další informace najdete v tématu [načítání datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) a [zápis obsah datovou sadu jako XML Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Zatímco formát formát DiffGram slouží především rozhraní .NET Framework jako formát serializace pro obsah <xref:System.Data.DataSet>, DiffGrams můžete také použít k úpravě data v tabulkách v databázi Microsoft SQL Server.  
  
 Prvek formátu Diffgram je generován zápisu obsahu pro všechny tabulky  **\<formát diffgram >** element.  
  
### <a name="to-generate-a-diffgram"></a>Chcete-li generovat formát Diffgram  
  
1.  Vygenerujte seznam tabulek kořenové (tedy tabulky bez některé z nadřazených).  
  
2.  Pro každou tabulku a jeho následníky v seznamu vypsat aktuální verze všech řádků v první části formát Diffgram.  
  
3.  Pro každou tabulku v <xref:System.Data.DataSet>, vypsat původní verzi všechny řádky, pokud existuje v  **\<před >** oddílu formát Diffgram.  
  
4.  Pro řádků s chybami, zapisovat chyby obsah  **\<chyby >** oddílu formát Diffgram.  
  
 Prvek formátu Diffgram je zpracovávána v pořadí od začátku souboru XML na konec.  
  
### <a name="to-process-a-diffgram"></a>Při zpracování prvek formátu Diffgram  
  
1.  Proces v první části formát Diffgram, který obsahuje aktuální verze řádků.  
  
2.  Zpracování druhý nebo  **\<před >** oddíl, který obsahuje původní verze řádku upravit a odstranit řádky.  
  
    > [!NOTE]
    >  Pokud řádek je označen jako odstraněný, operace odstranění odstranit řádku následníky také, v závislosti na `Cascade` vlastnost aktuálního <xref:System.Data.DataSet>.  
  
3.  Proces  **\<chyby >** části. Nastavte informace o chybě pro zadaný řádků a sloupců pro každou položku v této části.  
  
> [!NOTE]
>  Pokud nastavíte <xref:System.Data.XmlWriteMode> do formátu Diffgram, obsah cíle <xref:System.Data.DataSet> a původní <xref:System.Data.DataSet> se můžou lišit.  
  
## <a name="diffgram-format"></a>Formát DiffGram formátu  
 Formát DiffGram formát je rozdělené do tří částí: aktuálních dat, původní (nebo "před") dat a chyby části, jak je znázorněno v následujícím příkladu.  
  
```xml  
<?xml version="1.0"?>  
<diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  
   <DataInstance>  
   </DataInstance>  
  
  <diffgr:before>  
  </diffgr:before>  
  
  <diffgr:errors>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
 Formát formát DiffGram zahrnuje následující bloky dat:  
  
 **\<**  ***DataInstance***  **>**  
 Název tohoto elementu, ***DataInstance***, se používá pro účely vysvětlení v této dokumentaci. A ***DataInstance*** reprezentuje element <xref:System.Data.DataSet> nebo řádek <xref:System.Data.DataTable>. Místo *DataInstance*, element by obsahovat název <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable>. Tento blok formátu formát DiffGram obsahuje aktuální data, zda byl upraven, nebo ne. Je označeny prvek, nebo řádek, který byl změněn **diffgr:hasChanges** poznámky.  
  
 **\<diffgr: před >**  
 Tento blok formátu formát DiffGram obsahuje původní verzi řádek. Elementy v tomto bloku se shodují se elementů v ***DataInstance*** blokovat, s využitím **diffgr:id** poznámky.  
  
 **\<diffgr:Errors >**  
 Tento blok formátu formát DiffGram obsahuje informace o chybě pro konkrétního řádku ***DataInstance*** bloku. Elementy v tomto bloku se shodují se elementů v ***DataInstance*** blokovat, s využitím **diffgr:id** poznámky.  
  
## <a name="diffgram-annotations"></a>Formát DiffGram poznámky  
 DiffGrams se týkají elementy ze jiný formát DiffGram bloků, které představují různé řádek verze nebo informace o chybě v pomocí jsme několik poznámek <xref:System.Data.DataSet>.  
  
 Následující tabulka popisuje formát DiffGram poznámky, které jsou definovány v oboru názvů formátu DiffGram **urn: schémata-microsoft-com: XML-formát diffgram-v1**.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|**id**|Použít spárovat elementů v  **\<diffgr: před >** a  **\<diffgr:errors >** bloky elementům ve **\<** ***DataInstance*** **>** bloku. Hodnoty s **diffgr:id** poznámky jsou ve tvaru *[TableName] [RowIdentifier]*. Příklad: `<Customers diffgr:id="Customers1">`.|  
|**parentId**|Identifikuje které element z **\<** ***DataInstance*** **>** blok je nadřazeného elementu aktuálního elementu. Hodnoty s **diffgr:parentId** poznámky jsou ve tvaru *[TableName] [RowIdentifier]*. Příklad: `<Orders diffgr:parentId="Customers1">`.|  
|**haschanges –**|Identifikuje řádek **\<** ***DataInstance*** **>** blokovat jako upravená. **Haschanges –** poznámky může mít jednu z následujících dvou hodnot:<br /><br /> **Vložit**<br /> Identifikuje **Added** řádek.<br /><br /> **Upravit**<br /> Identifikuje **změněné** řádek, který obsahuje **původní** verze řádku v  **\<diffgr: před >** bloku. Všimněte si, že **odstraněné** řádky budou mít **původní** verze řádku v  **\<diffgr: před >** bloku, ale zde bude žádný element s poznámkami ve **\<** ***DataInstance*** **>** bloku.|  
|**hasErrors**|Identifikuje řádek **\<** ***DataInstance*** **>** blokovat s **RowError**. Chyba prvek je umístěn v  **\<diffgr:errors >** bloku.|  
|**Chyba**|Obsahuje text **RowError** pro konkrétní prvek,  **\<diffgr:errors >** bloku.|  
  
 <xref:System.Data.DataSet> Zahrnuje další poznámky při čtení nebo zápisu jako prvek formátu DiffGram její obsah. Následující tabulka popisuje tyto další poznámky, které jsou definovány v oboru názvů **urn: schémata-microsoft-com: XML-msdata**.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|**Atributu RowOrder**|Zachová řádek pořadí původní data a identifikuje index v řádku v konkrétní <xref:System.Data.DataTable>.|  
|**Skryté**|Určuje sloupec tak, že má **ColumnMapping** vlastnost nastavena na hodnotu **MappingType.Hidden**. Atribut je zapsaný ve formátu **msdata: Skrytá** *[ColumnName]*= "*hodnotu*". Příklad: `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.<br /><br /> Všimněte si, že skrytých sloupců zapíšou jenom jako atribut formátu DiffGram pokud obsahují data. Jinak jsou ignorovány.|  
  
## <a name="sample-diffgram"></a>Formát DiffGram ukázka  
 Níže je uveden příklad formátu DiffGram formátu. Tento příklad ukazuje výsledek aktualizace na řádek v tabulce, než změny byly potvrzeny. Řádek s CustomerID "ALFKI" byla upravena, ale neaktualizuje. V důsledku toho je **aktuální** řádek s **diffgr:id** z označena "jako Zákazníci1" v **\<** ***DataInstance*** **>** bloku a **původní** řádek s **diffgr:id** z označena "jako Zákazníci1" v  **\<diffgr: před >** bloku. Obsahuje řádek s CustomerID "ANATR" **RowError**, takže je opatřen poznámkou `diffgr:hasErrors="true"` a související prvek,  **\<diffgr:errors >** bloku.  
  
```xml  
<diffgr:diffgram xmlns:msdata="urn:schemas-microsoft-com:xml-msdata" xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
  <CustomerDataSet>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0" diffgr:hasChanges="modified">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>New Company</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers2" msdata:rowOrder="1" diffgram:hasErrors="true">  
      <CustomerID>ANATR</CustomerID>  
      <CompanyName>Ana Trujillo Emparedados y Helados</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers3" msdata:rowOrder="2">  
      <CustomerID>ANTON</CustomerID>  
      <CompanyName>Antonio Moreno Taquera</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers4" msdata:rowOrder="3">  
      <CustomerID>AROUT</CustomerID>  
      <CompanyName>Around the Horn</CompanyName>  
    </Customers>  
  </CustomerDataSet>  
  <diffgr:before>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>Alfreds Futterkiste</CompanyName>  
    </Customers>  
  </diffgr:before>  
  <diffgr:errors>  
    <Customers diffgr:id="Customers2" diffgr:Error="An optimistic concurrency violation has occurred for this row."/>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
## <a name="see-also"></a>Viz také  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Kopírování obsahu datové sady jako dat XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

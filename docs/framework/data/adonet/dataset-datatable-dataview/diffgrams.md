---
title: DiffGrams
ms.date: 03/30/2017
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
ms.openlocfilehash: 048c5331028bbe2bb232302637dbb12bcdd2adc3
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313512"
---
# <a name="diffgrams"></a>DiffGrams
Formát DiffGram je formát XML, který identifikuje aktuální a původní verzí datové prvky. <xref:System.Data.DataSet> Používá formát DiffGram formát pro načtení a uložení jeho obsah a k serializaci jeho obsah pro přenos přes síťové připojení. Když <xref:System.Data.DataSet> je zapsán jako formát DiffGram, naplní formát DiffGram přesně znovu vytvořit obsah, i když není schéma, o všechny potřebné informace <xref:System.Data.DataSet>, včetně hodnot sloupců z obou **původní** a **aktuální** verze řádků, informace o chybě řádek a řádek pořadí.  
  
 Při posílání a stahování <xref:System.Data.DataSet> z webové služby XML, je implicitně používá formát DiffGram formátu. Kromě toho při načítání obsahu <xref:System.Data.DataSet> pomocí XML **ReadXml** metodu, nebo při zápisu obsah <xref:System.Data.DataSet> v XML pomocí **WriteXml** metodu, můžete zadat že obsah nelze číst ani zapisovat jako formát DiffGram. Další informace najdete v tématu [načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) a [zápis obsahu datové sady jako dat XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Zatímco formát DiffGram formátu je převážně používána rozhraní .NET Framework jako formát serializace pro obsah <xref:System.Data.DataSet>, můžete také použít DiffGrams upravovat data v tabulkách v databázi Microsoft SQL Server.  
  
 Formát Diffgram je generován zatímco zapisuje obsah pro všechny tabulky  **\<formát diffgram >** elementu.  
  
### <a name="to-generate-a-diffgram"></a>Chcete-li generovat formát Diffgram  
  
1. Vygeneruje seznam kořenových tabulky (to znamená, že tabulky bez jakékoli nadřazené).  
  
2. Pro každou tabulku a její potomci v seznamu vypsat aktuální verzi všech řádků v první části formát Diffgram.  
  
3. Pro každou tabulku v <xref:System.Data.DataSet>, vypsat původní verzi všechny řádky, pokud existuje v  **\<před >** část formát Diffgram.  
  
4. Pro obsah v Chyba při zápisu řádků s chybami,  **\<chyby >** část formát Diffgram.  
  
 Formát Diffgram, jsou zpracovávána v pořadí od začátku souboru XML do konce.  
  
### <a name="to-process-a-diffgram"></a>Ke zpracování formát Diffgram  
  
1. Proces první část formát Diffgram, která obsahuje aktuální verzi řádky.  
  
2. Zpracování druhý nebo  **\<před >** oddíl, který obsahuje původní verze řádku upravit a odstranit řádky.  
  
    > [!NOTE]
    >  Pokud řádek je označen jako odstraněný, operace odstranění odstraněním řádku následníky, v závislosti na tom `Cascade` vlastnost aktuálního <xref:System.Data.DataSet>.  
  
3. Proces  **\<chyby >** oddílu. Nastavte informace o chybě pro zadaný řádek a sloupec pro každou položku v této části.  
  
> [!NOTE]
>  Pokud jste nastavili <xref:System.Data.XmlWriteMode> na formát Diffgram obsah cíle <xref:System.Data.DataSet> a původní <xref:System.Data.DataSet> se může lišit.  
  
## <a name="diffgram-format"></a>Formát DiffGram formátu  
 Formát DiffGram formátu je rozdělen na tři části: aktuální data, původní (nebo "před") dat a části chyby, jak je znázorněno v následujícím příkladu.  
  
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
  
 Formát DiffGram formátu se skládá z následujících bloků dat:  
  
 **\<**  ***DataInstance***  **>**  
 Název tohoto elementu ***DataInstance***, se používá pro účely vysvětlení v této dokumentaci. A ***DataInstance*** reprezentuje element <xref:System.Data.DataSet> nebo řádek <xref:System.Data.DataTable>. Místo *DataInstance*, element bude obsahovat název <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable>. Tento blok formát DiffGram formátu obsahuje aktuální data, zda byl upraven, nebo ne. Je označen elementu, nebo řádek, který byl změněn **diffgr:hasChanges** poznámky.  
  
 **\<diffgr: před >**  
 Tento blok formát DiffGram formátu obsahuje původní verzi řádku. Prvky v tomto bloku budou odpovídat na prvky ***DataInstance*** blokovat, s využitím **diffgr:id** poznámky.  
  
 **\<diffgr:errors>**  
 Tento blok formát DiffGram formátu obsahuje informace o chybách u konkrétního řádku ***DataInstance*** bloku. Prvky v tomto bloku budou odpovídat na prvky ***DataInstance*** blokovat, s využitím **diffgr:id** poznámky.  
  
## <a name="diffgram-annotations"></a>Formát DiffGram poznámky  
 DiffGrams použít několik poznámek prvky z různých formát DiffGram bloky, které představují verze různých řádků nebo informace o chybě v <xref:System.Data.DataSet>.  
  
 Následující tabulka popisuje formát DiffGram poznámky, které jsou definovány v oboru názvů formát DiffGram **urn: schémata-microsoft-schemas-formát diffgram-v1**.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|**id**|Použít na dvojici prvků v  **\<diffgr: před >** a  **\<diffgr:errors >** bloky na prvky **\<** ***DataInstance*** **>** bloku. Hodnoty s **diffgr:id** poznámky jsou ve formě *[TableName] [RowIdentifier]*. Například: `<Customers diffgr:id="Customers1">`.|  
|**parentId**|Určuje které elementy ze **\<** ***DataInstance*** **>** blok je nadřazený element aktuálního prvku. Hodnoty s **diffgr:parentId** poznámky jsou ve formě *[TableName] [RowIdentifier]*. Například: `<Orders diffgr:parentId="Customers1">`.|  
|**hasChanges**|Označuje řádek v **\<** ***DataInstance*** **>** blokovat, jako jsou změny. **Haschanges –** anotace může mít jednu z následujících dvou hodnot:<br /><br /> **Vložit**<br /> Identifikuje **přidané** řádek.<br /><br /> **Upravit**<br /> Identifikuje **změněné** řádku, který obsahuje **původní** verze řádku v  **\<diffgr: před >** bloku. Všimněte si, že **odstraněné** řádky budou mít **původní** verze řádku v  **\<diffgr: před >** bloku, ale nebudou mít žádný element s poznámkami v **\<** ***DataInstance*** **>** bloku.|  
|**hasErrors**|Označuje řádek v **\<** ***DataInstance*** **>** blokovat s **RowError**. Chyba prvek je umístěn v  **\<diffgr:errors >** bloku.|  
|**Chyba**|Obsahuje text **RowError** pro konkrétní element v  **\<diffgr:errors >** bloku.|  
  
 <xref:System.Data.DataSet> Zahrnuje další poznámky při čtení nebo zápisu formát DiffGram jeho obsah. Následující tabulka popisuje tyto další poznámky, které jsou definovány v oboru názvů **urn: schémata-microsoft-com: XML-msdata**.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|**RowOrder**|Zachovává pořadí řádku původní data a identifikuje index řádku v konkrétní <xref:System.Data.DataTable>.|  
|**Hidden**|Identifikuje sloupce tak, že má **ColumnMapping** vlastnost nastavena na hodnotu **MappingType.Hidden**. Atribut je napsané ve formátu **msdata: skrytý** *[Názevsloupce]*= "*hodnotu*". Například: `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.<br /><br /> Všimněte si, že skryté sloupce zapíšou jenom jako atribut formát DiffGram pokud obsahují data. V opačném případě se ignorují.|  
  
## <a name="sample-diffgram"></a>Formát DiffGram vzorku  
 Níže je uveden příklad formát DiffGram formátu. Tento příklad ukazuje výsledek aktualizace na řádek v tabulce předtím, než se změny byly potvrzeny. Řádek s CustomerID "ALFKI" má byla upravena, ale není aktualizovaná. V důsledku toho je **aktuální** řádek s **diffgr:id** z "Customers1" v **\<** ***DataInstance*** **>** bloku a **původní** řádek s **diffgr:id** z "Customers1" v  **\<diffgr: před >** bloku. Řádek s CustomerID "ANATR" zahrnuje **RowError**, takže je opatřen poznámkou `diffgr:hasErrors="true"` a související prvek,  **\<diffgr:errors >** bloku.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [Načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [Kopírování obsahu datové sady jako dat XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)
- [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

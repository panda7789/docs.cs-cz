---
title: DiffGrams
ms.date: 03/30/2017
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
ms.openlocfilehash: 2c521ef33c98234dac5f4b819a800cd524218462
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151153"
---
# <a name="diffgrams"></a>DiffGrams
DiffGram je formát XML, který identifikuje aktuální a původní verze datových prvků. Používá <xref:System.Data.DataSet> formát DiffGram k načtení a zachování jeho obsahu a serializovat jeho obsah pro přenos přes síťové připojení. Pokud <xref:System.Data.DataSet> je zapsán jako DiffGram, naplní DiffGram se všemi potřebnými informacemi přesně znovu obsah, i <xref:System.Data.DataSet>když ne schéma , včetně hodnoty sloupců z **původní** a **aktuální** verze řádku, informace o chybě řádku a pořadí řádků.  
  
 Při odesílání a <xref:System.Data.DataSet> načítání z webové služby XML se implicitně používá formát DiffGram. <xref:System.Data.DataSet> Navíc při načítání obsahu z XML pomocí **ReadXml** metody nebo při zápisu obsahu <xref:System.Data.DataSet> v XML pomocí **WriteXml** metoda, můžete určit, že obsah číst nebo zapisovat jako DiffGram. Další informace naleznete [v tématu Načítání datové sady z xml](loading-a-dataset-from-xml.md) a [zápisu obsahu datové sady jako dat XML](writing-dataset-contents-as-xml-data.md).  
  
 Zatímco formát DiffGram je primárně používán rozhraním .NET Framework jako <xref:System.Data.DataSet>formát serializace pro obsah a , můžete také použít DiffGrams k úpravě dat v tabulkách v databázi serveru Microsoft SQL Server.  
  
 Diffgram je generován zápisem obsahu všech tabulek do ** \<prvku diffgram>.**  
  
### <a name="to-generate-a-diffgram"></a>Generování diffgramu  
  
1. Vygenerujte seznam kořenových tabulek (to znamená tabulek bez nadřazených).  
  
2. Pro každou tabulku a její následníky v seznamu napište aktuální verzi všech řádků v první části Diffgram.  
  
3. Pro každou tabulku <xref:System.Data.DataSet>v , zapište původní verzi všech řádků, pokud existuje, v ** \<části před>** diffgram.  
  
4. Pro řádky, které mají chyby, zapište obsah chyb v ** \<části chyby>** Diffgram.  
  
 Diffgram je zpracován v pořadí od začátku souboru XML až do konce.  
  
### <a name="to-process-a-diffgram"></a>Zpracování diffgramu  
  
1. Zpracujte první část diffgramu, který obsahuje aktuální verzi řádků.  
  
2. Zpracujte druhý nebo ** \<před oddíl>,** který obsahuje původní verzi řádku upravených a odstraněných řádků.  
  
    > [!NOTE]
    > Pokud je řádek označen odstraněn, operace odstranění můžete odstranit potomky řádku `Cascade` také, v <xref:System.Data.DataSet>závislosti na vlastnosti aktuální .  
  
3. Zpracujte ** \<chyby>** části. Nastavte informace o chybě pro zadaný řádek a sloupec pro každou položku v této části.  
  
> [!NOTE]
> Pokud nastavíte <xref:System.Data.XmlWriteMode> na Diffgram, obsah <xref:System.Data.DataSet> cíle <xref:System.Data.DataSet> a originál se může lišit.  
  
## <a name="diffgram-format"></a>Formát DiffGram  
 Formát DiffGram je rozdělen do tří částí: aktuální data, původní (nebo "před") data a část chyb, jak je znázorněno v následujícím příkladu.  
  
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
  
 Formát DiffGram se skládá z následujících datových bloků:  
  
 **\<**  ***Instance data***  **>**  
 Název tohoto prvku ***DataInstance***se používá pro účely vysvětlení v této dokumentaci. Prvek ***DataInstance*** představuje <xref:System.Data.DataSet> nebo řádek <xref:System.Data.DataTable>. Místo *DataInstance*by prvek obsahoval název <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable>. Tento blok formátu DiffGram obsahuje aktuální data, ať už byla změněna či nikoli. Prvek nebo řádek, který byl změněn, je identifikován s anotací **diffgr:hasChanges.**  
  
 **\<diffgr:před>**  
 Tento blok formátu DiffGram obsahuje původní verzi řádku. Prvky v tomto bloku jsou porovnány s prvky v bloku ***DataInstance*** pomocí anotace **diffgr:id.**  
  
 **\<diffgr:>chyb**  
 Tento blok formátu DiffGram obsahuje informace o chybě pro určitý řádek v bloku ***DataInstance.*** Prvky v tomto bloku jsou porovnány s prvky v bloku ***DataInstance*** pomocí anotace **diffgr:id.**  
  
## <a name="diffgram-annotations"></a>Poznámky diffgram  
 DiffGrams používají několik anotací ke propojení prvků z různých bloků DiffGram, <xref:System.Data.DataSet>které představují různé verze řádků nebo informace o chybě v rozhraní .  
  
 Následující tabulka popisuje poznámky DiffGram, které jsou definovány v urně oboru názvů **DiffGram:schemas-microsoft-com:xml-diffgram-v1**.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|**Id**|Slouží ke spárování prvků v ** \<diffgr:before>** a **\<** **>** ** \<diffgr:errors>** bloky na prvky v bloku ***DataInstance.*** Hodnoty s poznámkou **diffgr:id** jsou ve tvaru *[TableName][RowIdentifier]*. Například: `<Customers diffgr:id="Customers1">`.|  
|**Parentid**|Určuje, který prvek **\<** z bloku ***DataInstance*** **>** je nadřazeným prvkem aktuálního prvku. Hodnoty s poznámkou **diffgr:parentId** jsou ve tvaru *[TableName][RowIdentifier]*. Například: `<Orders diffgr:parentId="Customers1">`.|  
|**hasChanges**|Identifikuje řádek v **\<** bloku ***DataInstance*** **>** jako upravený. Anotace **hasChanges** může mít jednu z následujících dvou hodnot:<br /><br /> **Vložen**<br /> Identifikuje **přidaný** řádek.<br /><br /> **Upravené**<br /> Identifikuje **Upravený** řádek, který obsahuje **verzi původního** řádku v ** \<bloku diffgr:before>.** Všimněte si, že **odstraněné** řádky budou mít **verzi původního** řádku v ** \<bloku diffgr:before>,** ale v **\<** bloku ***DataInstance*** **>** nebude žádný anotovaný prvek.|  
|**Haserrors**|**\<** Identifikuje řádek v bloku ***DataInstance*** **>** s **RowError**. Chybový prvek je umístěn v ** \<bloku diffgr:errors>.**|  
|**Chyba**|Obsahuje text **RowError** pro konkrétní prvek v ** \<diffgr:errors>** bloku.|  
  
 Obsahuje <xref:System.Data.DataSet> další poznámky při čtení nebo zápisu jeho obsah jako DiffGram. Následující tabulka popisuje tyto další poznámky, které jsou definovány v **oboru názvů urn:schemas-microsoft-com:xml-msdata**.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|**Pořadí řádků**|Zachová pořadí řádků původních dat a identifikuje index řádku <xref:System.Data.DataTable>v určitém souboru .|  
|**Skrytý**|Identifikuje sloupec jako sloupec s vlastností **ColumnMapping** nastavenou na **MappingType.Hidden**. Atribut je zapsán ve formátu **msdata:hidden** *[ColumnName]*="*value*". Například: `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.<br /><br /> Všimněte si, že skryté sloupce jsou zapsány pouze jako atribut DiffGram, pokud obsahují data. V opačném případě jsou ignorovány.|  
  
## <a name="sample-diffgram"></a>Ukázkový diffgram  
 Příklad formátu DiffGram je uveden níže. Tento příklad ukazuje výsledek aktualizace řádku v tabulce před změny byly potvrzeny. Řádek s CustomerID "ALFKI" byl změněn, ale nebyl aktualizován. Výsledkem je **aktuální** řádek s **diffgr:id** "Customers1" v **\<** ***bloku DataInstance*** **>** a **Původní** řádek s **diffgr:id** "Customers1" v ** \<bloku diffgr:before>.** Řádek s CustomerID "ANATR" obsahuje **RowError**, takže je anotován s `diffgr:hasErrors="true"` a je související prvek v ** \<diffgr:errors>** bloku.  
  
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

- [Použití XML v datové sadě](using-xml-in-a-dataset.md)
- [Načtení datové sady z XML](loading-a-dataset-from-xml.md)
- [Kopírování obsahu datové sady jako dat XML](writing-dataset-contents-as-xml-data.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)

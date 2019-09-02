---
title: DiffGrams
ms.date: 03/30/2017
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
ms.openlocfilehash: b9e6fb4ce1c2c7ee7d081a1cb2106d30960853c7
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204889"
---
# <a name="diffgrams"></a>DiffGrams
Formát DiffGram je formát XML, který identifikuje aktuální a původní verzi datových prvků. <xref:System.Data.DataSet> Používá formát formátu DiffGram k načtení a uchování jeho obsahu a k serializaci jeho obsahu pro přenos přes síťové připojení. Když je zapsán jako formát formátu DiffGram, naplní formát DiffGram všemi potřebnými informacemi, aby bylo možné obsah přesně znovu vytvořit, ale ne schématu <xref:System.Data.DataSet>, včetně hodnot sloupců z **originálu** i <xref:System.Data.DataSet>  **Aktuální** verze řádku, informace o chybě řádku a pořadí řádků.  
  
 Při odesílání a načítání <xref:System.Data.DataSet> z webové služby XML je formát formátu DiffGram implicitně použit. Kromě <xref:System.Data.DataSet> toho při načítání obsahu z XML pomocí metody **ReadXml** nebo při psaní obsahu <xref:System.Data.DataSet> v XML pomocí metody **WriteXml** můžete určit, že se má obsah číst nebo zapisovat jako formát formátu DiffGram. Další informace naleznete v tématu [načtení datové sady z XML](loading-a-dataset-from-xml.md) a [zápis obsahu datové sady jako XML data](writing-dataset-contents-as-xml-data.md).  
  
 Přestože formát formátu DiffGram je primárně používán .NET Framework jako formát serializace pro obsah a <xref:System.Data.DataSet>, můžete také pomocí formátu DiffGram upravovat data v tabulkách v databázi Microsoft SQL Server.  
  
 Formát DiffGram je vygenerován zápisem obsahu všech tabulek do  **\<prvku DiffGram >** .  
  
### <a name="to-generate-a-diffgram"></a>Generování DiffGram  
  
1. Vygeneruje seznam kořenových tabulek (tj. tabulky bez nadřazeného objektu).  
  
2. Pro každou tabulku a její následníky v seznamu zapište aktuální verzi všech řádků v prvním oddílu DiffGram.  
  
3. Pro každou tabulku v <xref:System.Data.DataSet>nástroji zapište původní verzi všech řádků, pokud existují,  **\<v části před >** ve vlastnosti DiffGram.  
  
4. V případě řádků, které obsahují chyby, zapište obsah chyby v  **\<části chyby >** oddílu DiffGram.  
  
 Formát DiffGram je zpracován v pořadí od začátku souboru XML do konce.  
  
### <a name="to-process-a-diffgram"></a>Zpracování DiffGram  
  
1. Zpracuje první oddíl ovládacího panelu DiffGram, který obsahuje aktuální verzi řádků.  
  
2. Zpracujte druhý nebo  **\<před >** oddíl, který obsahuje původní verzi řádku změněného a odstraněného řádku.  
  
    > [!NOTE]
    > Pokud je řádek označený jako odstraněný, může operace odstranění odstranit i následníky daného řádku, a to v závislosti na `Cascade` vlastnosti aktuálního. <xref:System.Data.DataSet>  
  
3. Zpracujte > chybového oddílu.  **\<** Nastavte informace o chybě pro zadaný řádek a sloupec pro jednotlivé položky v této části.  
  
> [!NOTE]
> Pokud nastavíte <xref:System.Data.XmlWriteMode> formát DiffGram, obsah cíle <xref:System.Data.DataSet> a původní <xref:System.Data.DataSet> se může lišit.  
  
## <a name="diffgram-format"></a>Formát formátu DiffGram  
 Formát formátu DiffGram je rozdělen na tři části: aktuální data, původní data (nebo "před") a část s chybami, jak je znázorněno v následujícím příkladu.  
  
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
  
 Formát formátu DiffGram se skládá z následujících bloků dat:  
  
 **\<**  ***DataInstance***  **>**  
 Název tohoto elementu, DataInstance, se používá pro vysvětlení pro účely v této dokumentaci. Element ***DataInstance*** představuje <xref:System.Data.DataSet> řádek <xref:System.Data.DataTable>nebo. Namísto prvku *DataInstance*by element obsahoval název <xref:System.Data.DataSet> nebo. <xref:System.Data.DataTable> Tento blok formátu DiffGram obsahuje aktuální data, zda byla upravena nebo nikoli. Prvek nebo řádek, který byl změněn, je identifikován pomocí anotace **diffgr: hasChanges** .  
  
 **\<diffgr:before>**  
 Tento blok formátu DiffGram obsahuje původní verzi řádku. Prvky v tomto bloku se shodují s prvky v bloku ***DataInstance*** pomocí anotace **diffgr: ID** .  
  
 **\<diffgr:errors>**  
 Tento blok formátu DiffGram obsahuje informace o chybě pro určitý řádek v bloku DataInstance . Prvky v tomto bloku se shodují s prvky v bloku ***DataInstance*** pomocí anotace **diffgr: ID** .  
  
## <a name="diffgram-annotations"></a>Poznámky ke DiffGram  
 Formát DiffGram používá několik poznámek k přidružení prvků z různých bloků DiffGram, které reprezentují různé verze řádků nebo informace o <xref:System.Data.DataSet>chybách v.  
  
 V následující tabulce jsou popsány poznámky formátu DiffGram definované v oboru názvů **urn: schemas-microsoft-com: XML-DiffGram-v1**.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|**id**|Slouží k párování prvků v  **\<diffgr: před >** a **\<**  **\<diffgr: chyby >** bloky do prvků v bloku DataInstance. **>** Hodnoty s poznámkou **diffgr: ID** jsou ve formátu *[TableName] [RowIdentifier]* . Například: `<Customers diffgr:id="Customers1">`.|  
|**parentId**|Určuje, který prvek z **\<** bloku DataInstance **>** je nadřazeným prvkem aktuálního prvku. Hodnoty s poznámkou **diffgr: parentID** jsou ve formátu *[TableName] [RowIdentifier]* . Například: `<Orders diffgr:parentId="Customers1">`.|  
|**hasChanges**|Identifikuje řádek v **\<** bloku DataInstance **>** jako změněný. **HasChanges** anotace může mít jednu z následujících dvou hodnot:<br /><br /> **vložený**<br /> Identifikuje **přidaný** řádek.<br /><br /> **změn**<br /> Určuje **upravený** řádek, který obsahuje **původní**  **\<verzi řádku v diffgr: před >** bloku. Všimněte si , že odstraněné řádky budou mít **>** **původní** **\<**  **\<verzi řádku v diffgr: před >** blok, ale v bloku DataInstance nebude žádný žádný element s poznámkami.|  
|**hasErrors**|Identifikuje řádek v **\<** bloku DataInstance **>** pomocí **RowError**. Element Error je umístěný v  **\<diffgr: Errors >** Block.|  
|**Chyba**|Obsahuje text **RowError** pro určitý element v  **\<bloku diffgr: Errors >** .|  
  
 <xref:System.Data.DataSet> Zahrnuje další poznámky při čtení nebo zápisu jeho obsahu jako formátu DiffGram. Následující tabulka popisuje tyto další poznámky, které jsou definovány v oboru názvů **urn: schemas-microsoft-com: XML-msdata**.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|**RowOrder**|Zachovává pořadí řádků původních dat a identifikuje index řádku v konkrétní <xref:System.Data.DataTable>.|  
|**Hidden**|Určuje sloupec, který má vlastnost **ColumnMapping** nastavenou na **MappingType. Hidden**. Atribut je zapsán ve formátu **msdata: Hidden** *[ColumnName]* = "*Value*". Například: `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.<br /><br /> Skryté sloupce se zapisují jenom jako atribut DiffGram, pokud obsahují data. V opačném případě jsou ignorovány.|  
  
## <a name="sample-diffgram"></a>Ukázka souboru DiffGram  
 Příklad formátu DiffGram je uveden níže. Tento příklad ukazuje výsledek aktualizace řádku v tabulce předtím, než byly změny potvrzeny. Řádek s ID zákazníka "ALFKI" byl změněn, ale nebyl aktualizován. Výsledkem je, **\<** že v bloku DataInstance **>** je **aktuální** řádek s **diffgr: ID** "Customers1" a **původní** řádek s **diffgr: ID** "Customers1" v  **\< diffgr: před** blokem >. Řádek s ID položky (KódZákazníka) "ANATR" obsahuje **RowError**, takže je opatřen s `diffgr:hasErrors="true"` poznámkami a existuje  **\<související element v diffgr: Errors >** Block.  
  
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

- [Použití XML v datové sadě](using-xml-in-a-dataset.md)
- [Načtení datové sady z XML](loading-a-dataset-from-xml.md)
- [Kopírování obsahu datové sady jako dat XML](writing-dataset-contents-as-xml-data.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

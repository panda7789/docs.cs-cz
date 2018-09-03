---
title: Kopírování obsahu datové sady jako dat XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: ff63c63be9bbfab7c3a9600f259abdea81be4260
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482258"
---
# <a name="writing-dataset-contents-as-xml-data"></a>Kopírování obsahu datové sady jako dat XML
Napište reprezentaci v jazyce XML v ADO.NET <xref:System.Data.DataSet>, s nebo bez jeho schématu. Je-li informace o schématu zahrnuty vložené XML, je zapsán pomocí jazyka pro definici schématu XML (XSD). Schéma obsahuje definice tabulky <xref:System.Data.DataSet> a také definice relace a omezení.  
  
 Když <xref:System.Data.DataSet> je zapsán jako data XML, řádky v tabulce <xref:System.Data.DataSet> jsou napsané v jejich aktuálních verzí. Ale <xref:System.Data.DataSet> lze také zapsat jako formát DiffGram tak, aby aktuální a původní hodnoty řádky budou zahrnuty.  
  
 Reprezentace XML <xref:System.Data.DataSet> lze zapsat do souboru, datový proud **XmlWriter**, nebo řetězec. Tyto možnosti poskytují flexibilitu pro způsob přenosu reprezentace XML <xref:System.Data.DataSet>. K získání reprezentace XML <xref:System.Data.DataSet> jako řetězec, použijte **getxml –** způsob, jak je znázorněno v následujícím příkladu.  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **Getxml –** vrátí reprezentaci XML <xref:System.Data.DataSet> bez informací o schématu. Zápis informací o schématu z <xref:System.Data.DataSet> (jako schéma XML) na řetězec pomocí **GetXmlSchema**.  
  
 K zápisu <xref:System.Data.DataSet> do souboru datového proudu, nebo **XmlWriter**, použijte **WriteXml** – metoda. První parametr předáte do **WriteXml** je cílem výstupu XML. Například řetězec obsahující název souboru, předejte **System.IO.TextWriter** objektu a tak dále. Můžete předat volitelný druhý parametr **XmlWriteMode** k určení, jak se výstup XML má být proveden zápis.  
  
 V následující tabulce jsou uvedeny možnosti **XmlWriteMode**.  
  
|Možnost XmlWriteMode|Popis|  
|-------------------------|-----------------|  
|**IgnoreSchema**|Zapíše aktuální obsah <xref:System.Data.DataSet> jako data XML bez schématu XML. Toto nastavení je výchozí.|  
|**WriteSchema**|Zapíše aktuální obsah <xref:System.Data.DataSet> jako dat XML pomocí relační struktury jako vložené schéma XML.|  
|**Formát DiffGram**|Zapíše celý <xref:System.Data.DataSet> jako formát DiffGram, včetně aktuální a původní hodnoty. Další informace najdete v tématu [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).|  
  
 Při zápisu reprezentaci v jazyce XML <xref:System.Data.DataSet> obsahující **DataRelation** objekty, bude pravděpodobně chcete, aby výsledný XML obsahuje podřízené řádky každá relace vnořené jejich souvisejících nadřazených prvků. Chcete-li to provést, nastavte **vnořené** vlastnost **DataRelation** k **true** po přidání **DataRelation** k <xref:System.Data.DataSet>. Další informace najdete v tématu [vnoření datových relací](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
 Následují dva příklady toho, jak reprezentaci XML pro zápis <xref:System.Data.DataSet> do souboru. První příklad předá název souboru pro výslednou XML jako řetězec do **WriteXml**. Druhý příklad předává **System.IO.StreamWriter** objektu.  
  
```vb  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema)  
```  
  
```csharp  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema);  
```  
  
```vb  
Dim xmlSW As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xml")  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema)  
xmlSW.Close()  
```  
  
```csharp  
System.IO.StreamWriter xmlSW = new System.IO.StreamWriter("Customers.xml");  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema);  
xmlSW.Close();  
```  
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a>Mapování sloupců na XML elementů, atributů a Text  
 Můžete určit, jak je reprezentovaná sloupec tabulky v XML pomocí **ColumnMapping** vlastnost **DataColumn** objektu. V následující tabulce jsou uvedeny různé **MappingType** hodnoty **ColumnMapping** vlastnost sloupec tabulky a výsledného kódu XML.  
  
|Hodnota MappingType|Popis|  
|-----------------------|-----------------|  
|**Element**|Toto nastavení je výchozí. Sloupec je zapsán jako element XML, kde vlastnost ColumnName je název elementu a obsah sloupce se zapisují jako text elementu. Příklad:<br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**Atribut**|Sloupec je zapsán jako atribut XML elementu XML pro aktuální řádek, kde vlastnost ColumnName je název atributu a obsah sloupce se zapisují jako hodnota atributu. Příklad:<br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**SimpleContent**|Obsah sloupce se zapisují jako text v elementu jazyka XML pro aktuální řádek. Příklad:<br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> Všimněte si, že **SimpleContent** nelze nastavit pro sloupec tabulky, který má **Element** sloupce nebo vnořené relace.|  
|**Skryté**|Sloupec není zapsán ve výstupu XML.|  
  
## <a name="see-also"></a>Viz také  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [Vnoření datových relací](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [Zápis informací o schématu datové sady jako XSD](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

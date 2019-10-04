---
title: Kopírování obsahu datové sady jako dat XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: 9a63e79b2fce137ba9d21db861850a471cb42b9f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833970"
---
# <a name="writing-dataset-contents-as-xml-data"></a>Kopírování obsahu datové sady jako dat XML
V ADO.NET můžete napsat reprezentaci XML <xref:System.Data.DataSet> s jeho schématem nebo bez něj. Pokud jsou informace o schématu zahrnuty do vloženého kódu XML, jsou zapsány pomocí jazyka XSD (XML Schema Definition Language). Schéma obsahuje definice tabulky <xref:System.Data.DataSet> a definice vztahu a omezení.  
  
 Pokud je <xref:System.Data.DataSet> zapsána jako data XML, řádky v <xref:System.Data.DataSet> jsou zapsány v jejich aktuálních verzích. @No__t-0 však lze také zapsat jako formát formátu DiffGram, aby byly zahrnuty aktuální i původní hodnoty řádků.  
  
 Reprezentace XML <xref:System.Data.DataSet> může být zapsána do souboru, datového proudu, **XmlWriter**nebo řetězce. Tyto možnosti poskytují skvělou flexibilitu při přenosu XML reprezentace <xref:System.Data.DataSet>. Chcete-li získat reprezentaci XML <xref:System.Data.DataSet> jako řetězce, použijte metodu **GetXml –** , jak je znázorněno v následujícím příkladu.  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **GetXml –** vrátí reprezentaci XML <xref:System.Data.DataSet> bez informací o schématu. Chcete-li zapsat informace o schématu z <xref:System.Data.DataSet> (jako schématu XML) do řetězce, použijte **GetXmlSchema**.  
  
 Chcete-li zapsat <xref:System.Data.DataSet> do souboru, datového proudu nebo **XmlWriter**, použijte metodu **WriteXml** . První parametr, který předáte metodě **WriteXml** , je cílem výstupu XML. Například předejte řetězec obsahující název souboru, **System. IO. TextWriter** a tak dále. Můžete předat volitelný druhý parametr **XmlWriteMode** , který určuje, jak se má zapsat výstup XML.  
  
 V následující tabulce jsou uvedeny možnosti pro **XmlWriteMode**.  
  
|XmlWriteMode – možnost|Popis|  
|-------------------------|-----------------|  
|**IgnoreSchema**|Zapíše aktuální obsah <xref:System.Data.DataSet> jako dat XML bez schématu XML. Toto nastavení je výchozí.|  
|**Hodnotu WriteSchema**|Zapíše aktuální obsah <xref:System.Data.DataSet> jako XML data s relační strukturou jako vložené schéma XML.|  
|**Formát**|Zapíše celé <xref:System.Data.DataSet> jako formát DiffGram, včetně původní a aktuální hodnoty. Další informace najdete v tématu formát [DiffGram](diffgrams.md).|  
  
 Při psaní reprezentace XML <xref:System.Data.DataSet> obsahující objekty **DataRelation** budete pravděpodobně chtít, aby výsledný kód XML měl podřízené řádky jednotlivých vztahů vnořené v rámci svých souvisejících nadřazených prvků. Chcete-li to provést, nastavte **vnořenou** vlastnost **DataRelation** na **hodnotu true** , když přidáte **DataRelation** do <xref:System.Data.DataSet>. Další informace najdete v tématu [vnořování datových vztahů](nesting-datarelations.md).  
  
 Níže jsou uvedeny dva příklady zápisu reprezentace XML <xref:System.Data.DataSet> do souboru. První příklad předá název souboru pro výsledný kód XML jako řetězec pro **WriteXml**. Druhý příklad předává objekt **System. IO. StreamWriter** .
  
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
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a>Mapování sloupců na elementy XML, atributy a text  
 Můžete určit způsob reprezentace sloupce tabulky v XML pomocí vlastnosti **ColumnMapping** objektu **DataColumn** . V následující tabulce jsou uvedeny různé hodnoty **MappingType** pro vlastnost **ColumnMapping** sloupce tabulky a výsledný kód XML.  
  
|Hodnota MappingType|Popis|  
|-----------------------|-----------------|  
|**Element**|Toto nastavení je výchozí. Sloupec je zapsán jako XML element, kde ColumnName je název elementu a obsah sloupce je zapsán jako text elementu. Příklad:<br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**Atribut**|Sloupec je zapsán jako atribut XML elementu XML pro aktuální řádek, kde ColumnName je název atributu a obsah sloupce je zapsán jako hodnota atributu. Příklad:<br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**SimpleContent**|Obsah sloupce je zapsán jako text v elementu XML pro aktuální řádek. Příklad:<br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> Všimněte si, že **element simpleContent** nelze nastavit pro sloupec tabulky, která má sloupce **elementů** nebo vnořené relace.|  
|**Neobsahuje**|Sloupec není napsaný ve výstupu XML.|  
  
## <a name="see-also"></a>Viz také:

- [Použití XML v datové sadě](using-xml-in-a-dataset.md)
- [DiffGrams](diffgrams.md)
- [Vnoření datových relací](nesting-datarelations.md)
- [Zápis informací o schématu datové sady jako XSD](writing-dataset-schema-information-as-xsd.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)

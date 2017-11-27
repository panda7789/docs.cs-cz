---
title: "Zápis obsah datovou sadu jako XML Data"
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
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d43fd8ec006f92131056d389ed2153263f7b7f1c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="writing-dataset-contents-as-xml-data"></a>Zápis obsah datovou sadu jako XML Data
V technologii ADO.NET můžete napsat reprezentaci XML <xref:System.Data.DataSet>, s nebo bez jeho schématu. Pokud informace o schématu zahrnuty vložené se souborem XML, je zapsán pomocí jazyka definice schématu XML (XSD). Schéma obsahuje definice tabulky <xref:System.Data.DataSet> a také definice relace a omezení.  
  
 Když <xref:System.Data.DataSet> je zapsána jako data XML, řádky v <xref:System.Data.DataSet> jsou zapsány ve své aktuální verze. Ale <xref:System.Data.DataSet> lze zapsat také jako prvek formátu DiffGram tak, že budou zahrnuty aktuální a původní hodnoty řádků.  
  
 Reprezentace XML <xref:System.Data.DataSet> lze zapisovat do souboru, datového proudu **XmlWriter**, nebo řetězec. Tyto možnosti poskytují flexibilitu pro způsob přenosu reprezentaci XML <xref:System.Data.DataSet>. K získání reprezentaci XML <xref:System.Data.DataSet> jako řetězec, použijte **getxml –** metoda, jak je znázorněno v následujícím příkladu.  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **Getxml –** vrátí reprezentaci XML <xref:System.Data.DataSet> bez informace o schématu. Při zápisu informací schématu z <xref:System.Data.DataSet> (jako schématu XML) na řetězec, použijte **GetXmlSchema**.  
  
 Zápis <xref:System.Data.DataSet> do souboru, datového proudu, nebo **XmlWriter**, použijte **WriteXml** metoda. První parametr je předat do **WriteXml** je cílem výstup XML. Například předat řetězec obsahující název souboru, **System.IO.TextWriter** objekt a tak dále. Abyste mohli předávat volitelný druhý parametr funkce **XmlWriteMode** k určení, jak je výstup XML k zapsání.  
  
 Následující tabulka znázorňuje možnosti pro **XmlWriteMode**.  
  
|Možnost XmlWriteMode|Popis|  
|-------------------------|-----------------|  
|**IgnoreSchema**|Zapíše aktuální obsah <xref:System.Data.DataSet> jako data XML bez schématu XML. Toto nastavení je výchozí.|  
|**WriteSchema**|Zapíše aktuální obsah <xref:System.Data.DataSet> jako data XML s relační struktura jako vloženého schématu XML.|  
|**Formát DiffGram**|Zapíše celý <xref:System.Data.DataSet> jako formát DiffGram, včetně aktuální a původní hodnoty. Další informace najdete v tématu [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).|  
  
 Při zápisu reprezentaci XML <xref:System.Data.DataSet> obsahující **DataRelation** objekty, pravděpodobně budete chtít výsledný kód XML má řádky podřízené každý vztah vnořených ve svých související nadřazené elementy. K tomu, nastavte **vnořené** vlastnost **DataRelation** k **true** při přidání **DataRelation** k <xref:System.Data.DataSet>. Další informace najdete v tématu [vnoření DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
 Následují dva příklady, jak napsat reprezentaci XML <xref:System.Data.DataSet> do souboru. V prvním příkladu předá název souboru pro výsledný soubor XML jako řetězec tak, aby **WriteXml**. V druhém příkladu předá **System.IO.StreamWriter** objektu.  
  
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
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a>Mapování sloupce XML elementy, atributy a Text  
 Můžete určit, jak je reprezentována sloupec tabulky v kódu XML pomocí **ColumnMapping** vlastnost **DataColumn** objektu. V následující tabulce jsou uvedeny rozdíly **MappingType** hodnoty **ColumnMapping** vlastnost sloupec tabulky a výsledný soubor XML.  
  
|Hodnota MappingType|Popis|  
|-----------------------|-----------------|  
|**Element**|Toto nastavení je výchozí. Sloupec je zapsána jako element XML, kde ColumnName je název elementu a obsah sloupce se zapisují jako text elementu. Příklad:<br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**Atribut**|Sloupec je zapsána jako atribut XML elementu XML pro aktuální řádek, kde ColumnName je název atributu, a obsah sloupce se zapisují jako hodnota atributu. Příklad:<br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**SimpleContent**|Obsah sloupce jsou zapsány jako text v elementu XML pro aktuální řádek. Příklad:<br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> Všimněte si, že **SimpleContent** nelze nastavit pro sloupec tabulky, který má **Element** sloupce nebo vnořené relace.|  
|**Skryté**|Sloupec není napsán v výstup XML.|  
  
## <a name="see-also"></a>Viz také  
 [Pomocí XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [DataRelations vnoření](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [Zápis informací o schématu datovou sadu jako XSD](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)  
 [Datové sady, DataTables a DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

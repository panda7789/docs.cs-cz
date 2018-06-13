---
title: Zápis informací o schématu datovou sadu jako XSD
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: b2012b32b0751bc093b9b3267cbbfc2e1a408156
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760996"
---
# <a name="writing-dataset-schema-information-as-xsd"></a>Zápis informací o schématu datovou sadu jako XSD
Můžete napsat schéma <xref:System.Data.DataSet> jako schématu XML definition language (XSD) schématu, tak, aby vám ho přenosu s nebo bez souvisejících dat v dokumentu XML. Schéma XML lze zapisovat do souboru, datového proudu <xref:System.Xml.XmlWriter>, nebo řetězec; je vhodné pro generování silného typu **datovou sadu**. Další informace o silného typu **datovou sadu** objekty, najdete v části [typové datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).  
  
 Můžete určit, jak jsou reprezentována sloupec tabulky ve schématu XML pomocí **ColumnMapping** vlastnost <xref:System.Data.DataColumn> objektu. Další informace najdete v tématu "Mapování sloupců XML elementy, atributy a Text" v [zápis obsah datovou sadu jako XML Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Zápis schéma **datovou sadu** jako schématu XML do souboru, datového proudu, nebo **XmlWriter**, použijte **WriteXmlSchema** metodu **datovou sadu**. **WriteXmlSchema** přijímá jeden parametr, který určuje cíl výsledné schématu XML. Následující příklady kódu ukazují, jak napsat schéma XML **datovou sadu** do souboru předáním řetězec obsahující název souboru a <xref:System.IO.StreamWriter> objektu.  
  
```vb  
dataSet.WriteXmlSchema("Customers.xsd")  
```  
  
```csharp  
dataSet.WriteXmlSchema("Customers.xsd");  
```  
  
```vb  
Dim writer As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xsd")  
dataSet.WriteXmlSchema(writer)  
writer.Close()  
```  
  
```csharp  
System.IO.StreamWriter writer = new System.IO.StreamWriter("Customers.xsd");  
dataSet.WriteXmlSchema(writer);  
writer.Close();  
```  
  
 K získání schématu **datovou sadu** a zapsat jako řetězec schématu XML, použijte **GetXmlSchema** metoda, jak je znázorněno v následujícím příkladu.  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a>Viz také  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Kopírování obsahu datové sady jako dat XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [Typové datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

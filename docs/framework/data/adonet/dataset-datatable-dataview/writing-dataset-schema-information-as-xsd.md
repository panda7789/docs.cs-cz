---
title: Zápis informací o schématu datové sady jako XSD
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: 8403f9d9be88f34e473fd3512f5499193245d227
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59099440"
---
# <a name="writing-dataset-schema-information-as-xsd"></a>Zápis informací o schématu datové sady jako XSD
Lze zapsat schéma <xref:System.Data.DataSet> jako jazyk (XSD) schématu definice schématu XML, takže, mohou přenášet, s nebo bez souvisejících dat v dokumentu XML. Schéma XML lze zapsat do souboru, datový proud <xref:System.Xml.XmlWriter>, nebo řetězec; jde použít ke generování silného typu **datovou sadu**. Další informace o silně typované **datovou sadu** objekty, najdete [typované datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).  
  
 Můžete určit, jak je reprezentovaná sloupec tabulky ve schématu XML pomocí **ColumnMapping** vlastnost <xref:System.Data.DataColumn> objektu. Další informace najdete v tématu "Mapování sloupců XML elementů, atributů a Text" [zápis obsahu datové sady jako dat XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Chcete-li zapsat schéma **datovou sadu** jako schéma XML do souboru, datový proud, nebo **XmlWriter**, použít **WriteXmlSchema** metodu **datovou sadu**. **WriteXmlSchema** přijímá jeden parametr, který určuje cíl výsledného schématu XML. Následující příklady kódu ukazují, jak zapsat schéma XML **datovou sadu** do souboru tím, že předáte řetězec obsahující název souboru a <xref:System.IO.StreamWriter> objektu.  
  
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
  
 Získat schéma **datovou sadu** a zapsat jako řetězec schématu XML, použijte **GetXmlSchema** způsob, jak je znázorněno v následujícím příkladu.  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a>Viz také:

- [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [Kopírování obsahu datové sady jako dat XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)
- [Typové datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)
- [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

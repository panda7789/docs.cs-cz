---
title: Generování datových sad se silnými typy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: 9bff69e28aa17da87da7e94d4e110c0375f043ae
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203701"
---
# <a name="generating-strongly-typed-datasets"></a>Generování datových sad se silnými typy
Vzhledem ke schématu XML, které vyhovuje standardu XSD (XML Schema Definition Language), můžete vytvořit silně typované <xref:System.Data.DataSet> pomocí nástroje XSD. exe, který je součástí sady Windows Software Development Kit (SDK).  
  
 (Chcete-li vytvořit XSD z databázových tabulek <xref:System.Data.DataSet.WriteXmlSchema%2A> , přečtěte si nebo [práce s datovými sadami v sadě Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).  
  
 Následující kód ukazuje syntaxi pro generování **datové sady** pomocí tohoto nástroje.  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 V této syntaxi `/d` direktiva instruuje nástroj, aby vygeneroval **datovou sadu**, `/l:` a sdělí nástroji, který jazyk má použít (například C# nebo Visual Basic .NET). Volitelná `/eld` direktiva určuje, že můžete použít LINQ to DataSet k dotazování proti vygenerované **datové sadě.** Tato možnost se používá, když `/d` je také určena možnost. Další informace najdete v tématu [dotazování na typové datové sady](../querying-typed-datasets.md). Volitelná `/n:` direktiva říká nástroji, aby vygenerovala obor názvů pro **datovou sadu** s názvem **xsdschema. Namespace**. Výstup příkazu je XSDSchemaFileName.cs, který lze zkompilovat a použít v aplikaci ADO.NET. Vygenerovaný kód může být kompilován jako knihovna nebo modul.  
  
 Následující kód ukazuje syntaxi pro zkompilování generovaného kódu jako knihovny pomocí C# kompilátoru (CSc. exe).  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 Direktiva instruuje nástroj, aby jej mohl kompilovat do knihovny `/r:` a direktivy určují závislé knihovny vyžadované ke kompilaci. `/t:` Výstup příkazu je XSDSchemaFileName. dll, který může být předán kompilátoru při kompilování aplikace ADO.NET s `/r:` direktivou.  
  
 Následující kód ukazuje syntaxi pro přístup k oboru názvů předanému do souboru XSD. exe v aplikaci ADO.NET.  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 Následující příklad kódu používá typovou datovou **sadu** s názvem **CustomerDataSet** k načtení seznamu zákazníků z databáze **Northwind** . Jakmile se data načtou pomocí metody **Fill** , příklad projde každý zákazník v tabulce **Customers** pomocí typovaného objektu **CustomersRow** (**DataRow**). To poskytuje přímý přístup k sloupci **KódZákazníka** , na rozdíl od přes DataColumnCollection.  
  
```vb  
Dim customers As CustomerDataSet= New CustomerDataSet()  
Dim adapter As SqlDataAdapter New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers;", _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=Northwind")  
  
adapter.Fill(customers, "Customers")  
  
Dim customerRow As CustomerDataSet.CustomersRow  
For Each customerRow In customers.Customers  
  Console.WriteLine(customerRow.CustomerID)  
Next  
```  
  
```csharp  
CustomerDataSet customers = new CustomerDataSet();  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers;",  
  "Data Source=(local);Integrated " +  
  "Security=SSPI;Initial Catalog=Northwind");  
  
adapter.Fill(customers, "Customers");  
  
foreach(CustomerDataSet.CustomersRow customerRow in customers.Customers)  
  Console.WriteLine(customerRow.CustomerID);  
```  
  
 Následuje schéma XML použité pro příklad.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet" xmlns="" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [Typové datové sady](typed-datasets.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

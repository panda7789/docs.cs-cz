---
title: Generování datových sad se silnými typy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: 198d7f616d843a3c90b8d32cf33096ee253d2935
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832740"
---
# <a name="generating-strongly-typed-datasets"></a>Generování datových sad se silnými typy
Zadané schéma XML, který vyhovuje schématu XML definice jazyk (XSD) standard, můžete vygenerovat silného typu <xref:System.Data.DataSet> nástrojem XSD.exe s Windows Software Development Kit (SDK).  
  
 (Vytvoření xsd z tabulky databáze najdete v tématu <xref:System.Data.DataSet.WriteXmlSchema%2A> nebo [práce s datovými sadami v sadě Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).  
  
 Následující kód ukazuje syntaxi pro generování **datovou sadu** pomocí tohoto nástroje.  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 V této syntaxe `/d` směrnice instruuje nástroj v režimu generování **datovou sadu**a `/l:` instruuje nástroj jaký jazyk se má použít (například C# nebo Visual Basic .NET). Volitelný `/eld` direktiva Určuje, které můžete použít [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] k dotazu vůči generované **datové sady.** Tato možnost se používá při `/d` je také zadán. Další informace najdete v tématu [dotazování typované datové sady](../../../../../docs/framework/data/adonet/querying-typed-datasets.md). Volitelný `/n:` – direktiva Určuje nástroj, který také generovat obor názvů pro **datovou sadu** volá **XSDSchema.Namespace**. Výstup příkazu je XSDSchemaFileName.cs, které je možné zkompilovat a použít v aplikaci ADO.NET. Generovaný kód lze zkompilovat jako knihovny nebo modulu.  
  
 Následující kód ukazuje syntaxi pro kompilaci vygenerovaného kódu jako knihovny pomocí kompilátoru jazyka C# (csc.exe).  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 `/t:` Směrnice instruuje nástroj pro kompilaci do knihovny a `/r:` direktivy zadat závislé knihovny požadovaných pro kompilaci. Výstup příkazu je XSDSchemaFileName.dll, které mohou být předána do kompilátor při kompilaci aplikace pomocí technologie ADO.NET `/r:` směrnice.  
  
 Následující kód ukazuje syntaxi pro přístup k oboru názvů předán XSD.exe v aplikaci ADO.NET.  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 Následující příklad kódu používá typovaného **datovou sadu** s názvem **CustomerDataSet** načíst seznam zákazníků **Northwind** databáze. Po načtení dat pomocí **vyplnit** metody v příkladu prochází každého zákazníka v **zákazníkům** tabulky pomocí zadaného **CustomersRow** ( **Objekt DataRow**) objektu. To poskytuje přímý přístup k **CustomerID** sloupců, nikoli až **DataColumnCollection**.  
  
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
  
 Následuje schéma XML pro příklad.  
  
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
- [Typové datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)
- [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

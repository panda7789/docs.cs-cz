---
title: Generování silného typu datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: 95bb536416a043fc392d0c4e94378239ae3ee37f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758026"
---
# <a name="generating-strongly-typed-datasets"></a>Generování silného typu datové sady
Zadané schéma XML, který odpovídá schématu XML definice jazyka (XSD) standard, můžete vygenerovat silného typu <xref:System.Data.DataSet> pomocí nástroje XSD.exe součástí [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].  
  
 (Vytvoření xsd z tabulek databáze naleznete v tématu <xref:System.Data.DataSet.WriteXmlSchema%2A> nebo [práce s datovými sadami v sadě Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).  
  
 Následující kód ukazuje syntaxi pro generování **datovou sadu** pomocí tohoto nástroje.  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 V této syntaxe `/d` – direktiva informuje nástroj pro generování **datovou sadu**a `/l:` informuje nástroj jaké jazyka (například C# nebo Visual Basic .NET). Volitelné `/eld` – direktiva Určuje, které můžete použít [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] k dotazu vůči vygenerovaného **datovou sadu.** Tato možnost se používá při `/d` také parametr. Další informace najdete v tématu [dotazování typové datové sady](../../../../../docs/framework/data/adonet/querying-typed-datasets.md). Volitelné `/n:` – direktiva informuje nástroj, který taky obor názvů pro generování **datovou sadu** názvem **XSDSchema.Namespace**. Výstup příkazu je XSDSchemaFileName.cs, které můžete zkompilovat a použít v aplikaci ADO.NET. Generovaný kód mohou být zkompilovány jako modul nebo knihovny.  
  
 Následující kód ukazuje syntaxi pro kompilace generovaného kódu jako knihovny pomocí kompilátor jazyka C# (csc.exe).  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 `/t:` – Direktiva informuje nástroj zkompilovat do knihovny a `/r:` direktivy zadejte závislé knihovny potřebné ke kompilaci. Výstup příkazu je XSDSchemaFileName.dll, který se dá předat do kompilátoru při kompilaci aplikace ADO.NET s `/r:` – direktiva.  
  
 Následující kód ukazuje syntaxi pro přístup k oboru názvů předaný XSD.exe v aplikaci ADO.NET.  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 Následující příklad kódu používá zadaný **datovou sadu** s názvem **CustomerDataSet** načíst seznam zákazníků z **Northwind** databáze. Po načtení dat pomocí **vyplnění** metody v příkladu prochází každého zákazníka a to v **zákazníci** tabulky pomocí zadaného objektu **CustomersRow** ( **DataRow**) objektu. To poskytuje přímý přístup k **CustomerID** sloupců, nikoli pomocí **DataColumnCollection**.  
  
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
  
 Následuje schématu XML pro tento příklad.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [Typové datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

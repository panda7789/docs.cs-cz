---
title: Odvozování relační struktury datové sady ze schématu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 549579fca0179994191987097c12b6085ee91756
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119688"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>Odvozování relační struktury datové sady ze schématu XML (XSD)
Tato část obsahuje přehled toho, jak relační schéma `DataSet` je sestaven z dokument schématu XML definice jazyk (XSD) schématu. Obecně platí, pro každou `complexType` podřízený prvek element schématu tabulky se vygeneruje v `DataSet`. Struktura tabulky se určuje podle definice komplexního typu. Tabulky vytvářejí `DataSet` pro nejvyšší úrovně elementy ve schématu. Ale tabulku je vytvořen pouze pro nejvyšší úroveň `complexType` element při `complexType` element je vnořit do jiného `complexType` element, ve kterém malá a velká ve vnořeném `complexType` element je namapována na `DataTable` v rámci `DataSet`.  
  
 Další informace o XSD, najdete v článku World Wide Web Consortium (W3C) [XML schématu část 0: Úvod do doporučení](https://www.w3.org/TR/xmlschema-0/), [XML schématu část 1: Struktury doporučení](https://www.w3.org/TR/xmlschema-1/)a [XML schématu část 2: Datové typy doporučení](https://www.w3.org/TR/xmlschema-2/).  
  
 Následující příklad ukazuje schématu XML kde `customers` je podřízený prvek `MyDataSet` element, který je **datovou sadu** elementu.  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element name="customers" >   
           <xs:complexType >  
             <xs:sequence>  
               <xs:element name="CustomerID" type="xs:integer"   
                            minOccurs="0" />  
               <xs:element name="CompanyName" type="xs:string"   
                            minOccurs="0" />  
               <xs:element name="Phone" type="xs:string" />  
             </xs:sequence>  
           </xs:complexType>  
          </xs:element>  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 V předchozím příkladu prvek `customers` je komplexní typ elementu. Proto je analyzován definice komplexní typ a proces mapování vytvoří v následující tabulce.  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 Typ dat každého sloupce v tabulce je odvozen od typu schématu XML odpovídající element nebo atribut.  
  
> [!NOTE]
>  Pokud element `customers` je jednoduchý datový typ schématu XML jako **celé číslo**, je vygenerována žádná tabulka. Tabulky vytvářejí pouze prvky nejvyšší úrovně, které jsou komplexní typy.  
  
 V následujícím schématu XML **schématu** element má dva podřízené elementy, `InStateCustomers` a `OutOfStateCustomers`.  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="InStateCustomers" type="customerType" />  
   <xs:element name="OutOfStateCustomers" type="customerType" />  
    <xs:complexType name="customerType" >  
  
     </xs:complexType>  
  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element ref="customers" />  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 Jak `InStateCustomers` a `OutOfStateCustomers` komplexního typu prvků jsou podřízené prvky (`customerType`). Proto vygeneruje proces mapování následujících dvou tabulkách identické v `DataSet`.  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mapování omezení schématu XML (XSD) k omezením datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Popisuje prvky schématu XML použitý k vytvoření jedinečné a cizího klíče omezení `DataSet`.  
  
 [Generování relací datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Popisuje prvky schématu XML použitý k vytvoření relace mezi sloupci tabulky v `DataSet`.  
  
 [Omezení schématu XML a relací](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 Popisuje, jak vztahy se vytvářejí implicitně, při použití prvky schématu XML k vytvoření omezení `DataSet`.  
  
## <a name="related-sections"></a>Související oddíly  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Popisuje, jak načíst a zachováte data v a relační struktury `DataSet` jako XML data.  
  
## <a name="see-also"></a>Viz také:

- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

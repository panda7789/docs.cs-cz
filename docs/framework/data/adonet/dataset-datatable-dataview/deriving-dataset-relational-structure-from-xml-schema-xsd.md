---
title: Odvozování relační struktury datové sady ze schématu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: d32b5cb86bc5a138f9a5f438629d8e231be4ba94
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151166"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>Odvozování relační struktury datové sady ze schématu XML (XSD)
Tato část obsahuje přehled o tom, jak `DataSet` je relační schéma a sestaveno z dokumentu schématu schématu schématu schématu schématu schématu schématu schématu XML. Obecně platí pro `complexType` každý podřízený prvek prvku schématu tabulka je `DataSet`generována v . Struktura tabulky je určena definicí komplexního typu. Tabulky jsou vytvořeny `DataSet` v pro prvky nejvyšší úrovně ve schématu. Tabulka je však vytvořena pouze pro `complexType` prvek `complexType` nejvyšší úrovně, když `complexType` je prvek vnořen uvnitř jiného prvku, v takovém případě je vnořený `complexType` prvek mapován na a `DataTable` v rámci . `DataSet`  
  
 Další informace o zařízení XSD naleznete v [části schématu XML 0: Primer Recommendation konsorcia Xml](https://www.w3.org/TR/xmlschema-0/)konsorcia World Wide Web Consortium (W3C) , část [schématu XML, část 1 schématu XML](https://www.w3.org/TR/xmlschema-1/)a část 2 [schématu XML: Doporučení datových typů](https://www.w3.org/TR/xmlschema-2/).  
  
 Následující příklad ukazuje schéma XML, kde `customers` je podřízený `MyDataSet` prvek prvku, což je element **DataSet.**  
  
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
  
 V předchozím příkladu je `customers` prvek komplexní majek. Proto je analýza definice komplexního typu a proces mapování vytvoří následující tabulku.  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Datový typ každého sloupce v tabulce je odvozen z typu schématu XML odpovídajícího zadaného prvku nebo atributu.  
  
> [!NOTE]
> Pokud je `customers` prvek jednoduchého datového typu schématu XML, **například celé číslo**, není generována žádná tabulka. Tabulky jsou vytvořeny pouze pro prvky nejvyšší úrovně, které jsou složité typy.  
  
 V následujícím schématu XML má element **Schéma** dva podřízené `InStateCustomers` elementy a `OutOfStateCustomers`.  
  
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
  
 Prvky `InStateCustomers` i `OutOfStateCustomers` podřízené prvky`customerType`jsou prvky komplexního typu ( ). Proces mapování proto generuje následující dvě identické `DataSet`tabulky v .  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mapování omezení schématu XML (XSD) k omezením datové sady](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Popisuje prvky schématu XML použité k vytvoření jedinečných omezení `DataSet`cizího klíče v rozhraní .  
  
 [Generování relací datové sady ze schématu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)  
 Popisuje prvky schématu XML použité k vytvoření vztahů `DataSet`mezi sloupci tabulky v rozhraní .  
  
 [Omezení schématu XML a relací](xml-schema-constraints-and-relationships.md)  
 Popisuje, jak jsou vztahy vytvořeny implicitně při použití elementů schématu XML k vytvoření omezení v aplikaci `DataSet`.  
  
## <a name="related-sections"></a>Související oddíly  
 [Použití XML v datové sadě](using-xml-in-a-dataset.md)  
 Popisuje, jak načíst a zachovat relační `DataSet` strukturu a data v datech xml.  
  
## <a name="see-also"></a>Viz také

- [Přehled ADO.NET](../ado-net-overview.md)

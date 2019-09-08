---
title: Odvozování relační struktury datové sady ze schématu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: d15aa02b41b9a34b00298aeb32d2e3998de8feba
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786336"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>Odvozování relační struktury datové sady ze schématu XML (XSD)
Tato část poskytuje přehled o tom, jak je relační schéma a `DataSet` sestaveno z dokumentu schématu XSD (XML Schema Definition Language). Obecně platí, že pro `complexType` každý podřízený element elementu schématu je tabulka generována `DataSet`v. Struktura tabulky je určena definicí komplexního typu. Tabulky jsou vytvořeny v `DataSet` prvku pro prvky nejvyšší úrovně ve schématu. Tabulka je však vytvořena pouze pro element `complexType` nejvyšší úrovně, je- `complexType` li element vnořen uvnitř jiného `complexType` prvku, v `DataTable` takovém případě je `DataSet`vnořený `complexType` prvek mapován na v rámci.  
  
 Další informace o XSD najdete v části schéma XML pro konsorcium World Wide Web (W3C [) – část 0: Doporučení](https://www.w3.org/TR/xmlschema-0/) pro[Úvod, část schématu XML 1: Doporučení](https://www.w3.org/TR/xmlschema-1/) ke[strukturám a část schématu XML 2: Doporučení](https://www.w3.org/TR/xmlschema-2/)pro DataTypes.  
  
 Následující příklad ukazuje schéma XML, kde `customers` je podřízený element `MyDataSet` elementu, který je element **DataSet** .  
  
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
  
 V předchozím příkladu je element `customers` prvkem komplexního typu. Proto se definice komplexního typu analyzuje a proces mapování vytvoří následující tabulku.  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 Datový typ každého sloupce v tabulce je odvozen od typu schématu XML odpovídajícího elementu nebo atributu.  
  
> [!NOTE]
> Pokud je prvek `customers` jednoduchého datového typu schématu XML, jako je například **celé číslo**, není vygenerována žádná tabulka. Tabulky jsou vytvořeny pouze pro prvky nejvyšší úrovně, které jsou komplexní typy.  
  
 V následujícím schématu XML má element **Schema** dva podřízené `InStateCustomers` prvky elementu a. `OutOfStateCustomers`  
  
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
  
 I podřízené prvky jsou elementy komplexního typu (`customerType`). `OutOfStateCustomers` `InStateCustomers` Proto proces mapování generuje následující dvě identické tabulky v `DataSet`.  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mapování omezení schématu XML (XSD) k omezením datové sady](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Popisuje prvky schématu XML, které se používají k vytvoření jedinečnosti a omezení cizího klíče v `DataSet`.  
  
 [Generování relací datové sady ze schématu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)  
 Popisuje prvky schématu XML, které slouží k vytvoření vztahů mezi sloupci tabulky v `DataSet`.  
  
 [Omezení schématu XML a relací](xml-schema-constraints-and-relationships.md)  
 Popisuje `DataSet`, jak jsou relace vytvořeny implicitně při použití elementů schématu XML k vytvoření omezení v.  
  
## <a name="related-sections"></a>Související oddíly  
 [Použití XML v datové sadě](using-xml-in-a-dataset.md)  
 Popisuje, jak načíst a zachovat relační strukturu a data ve `DataSet` formě dat XML.  
  
## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](../ado-net-overview.md)

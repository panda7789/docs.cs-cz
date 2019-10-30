---
title: Odvozování relační struktury datové sady ze schématu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: ef77030b4e847f91fea074b68e223ac622539048
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040103"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>Odvozování relační struktury datové sady ze schématu XML (XSD)
Tato část poskytuje přehled o tom, jak je relační schéma `DataSet` sestaveno z dokumentu schématu XSD (XML Schema Definition Language). Obecně platí, že pro každý `complexType` podřízený element elementu schématu je tabulka vygenerována v `DataSet`. Struktura tabulky je určena definicí komplexního typu. Tabulky jsou vytvořeny v `DataSet` pro prvky nejvyšší úrovně ve schématu. Tabulka je však vytvořena pouze pro `complexType` element nejvyšší úrovně, je-li `complexType` prvek vnořen v jiném elementu `complexType`, v takovém případě je vnořený `complexType` element namapován na `DataTable` v rámci `DataSet`.  
  
 Další informace o schématu XSD naleznete v části "konsorcium World Wide Web (W3C) [XML Schema Part 0: doporučení](https://www.w3.org/TR/xmlschema-0/), [část 1 schématu XML: struktury doporučení](https://www.w3.org/TR/xmlschema-1/)a [část 2 XML schématu: doporučení k datatypeům](https://www.w3.org/TR/xmlschema-2/).  
  
 Následující příklad ukazuje schéma XML, kde `customers` je podřízeným prvkem prvku `MyDataSet`, který je prvkem **datové sady** .  
  
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
  
 V předchozím příkladu je prvek `customers` prvek komplexního typu. Proto se definice komplexního typu analyzuje a proces mapování vytvoří následující tabulku.  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Datový typ každého sloupce v tabulce je odvozen od typu schématu XML odpovídajícího elementu nebo atributu.  
  
> [!NOTE]
> Pokud `customers` elementu je jednoduchý datový typ schématu XML, jako je například **Integer**, není vygenerována žádná tabulka. Tabulky jsou vytvořeny pouze pro prvky nejvyšší úrovně, které jsou komplexní typy.  
  
 V následujícím schématu XML má element **Schema** dva podřízené prvky elementu `InStateCustomers` a `OutOfStateCustomers`.  
  
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
  
 `InStateCustomers` i podřízené prvky `OutOfStateCustomers` jsou elementy komplexního typu (`customerType`). Proto proces mapování generuje následující dvě identické tabulky v `DataSet`.  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mapování omezení schématu XML (XSD) k omezením datové sady](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Popisuje prvky schématu XML, které slouží k vytváření omezení jedinečného a cizího klíče v `DataSet`.  
  
 [Generování relací datové sady ze schématu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)  
 Popisuje prvky schématu XML, které slouží k vytvoření vztahů mezi sloupci tabulky v `DataSet`.  
  
 [Omezení schématu XML a relací](xml-schema-constraints-and-relationships.md)  
 Popisuje, jak jsou relace vytvořeny implicitně při použití elementů schématu XML k vytvoření omezení v `DataSet`.  
  
## <a name="related-sections"></a>Související oddíly  
 [Použití XML v datové sadě](using-xml-in-a-dataset.md)  
 Popisuje, jak načíst a zachovat relační strukturu a data v `DataSet` jako data XML.  
  
## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](../ado-net-overview.md)

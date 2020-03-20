---
title: Generování relací datové sady ze schématu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: feb0be7f66bf0f407e54ef0830c13f0c4a8a6418
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151127"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>Generování relací datové sady ze schématu XML (XSD)
V <xref:System.Data.DataSet>aplikaci vytvoříte přidružení mezi dvěma nebo více sloupci vytvořením vztahu nadřazený podřízený. Existují tři způsoby, jak reprezentovat vztah **DataSet** v rámci schématu definice schématu XML (XSD):  
  
- Určete vnořené komplexní typy.  
  
- Použijte **anotaci msdata:Relationship.**  
  
- Zadejte **xs:keyref** bez anotace **msdata:ConstraintOnly.**  
  
## <a name="nested-complex-types"></a>Vnořené komplexní typy  
 Vnořené komplexní definice typu ve schématu označují vztahy nadřazený-podřízený prvků. Následující fragment schématu XML ukazuje, že **OrderDetail** je podřízený míchaný prvek **Order** elementu.  
  
```xml  
<xs:element name="Order">  
  <xs:complexType>  
     <xs:sequence>
       <xs:element name="OrderDetail" />  
           <xs:complexType>
           </xs:complexType>  
     </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Proces mapování schématu XML vytvoří tabulky v **datové sadě,** které odpovídají vnořené komplexní typy ve schématu. Vytvoří také další sloupce, které**-** se používají jako nadřazené podřízené sloupce pro generované tabulky. Všimněte si, že tyto nadřazené**-** podřízené sloupce určují vztahy, které nejsou stejné jako určení omezení primárního klíče nebo cizího klíče.  
  
## <a name="msdatarelationship-annotation"></a>msdata:Anotace vztahu  
 **Anotace msdata:Relationship** umožňuje explicitně určit vztahy nadřazený podřízený mezi prvky ve schématu, které nejsou vnořené. Následující příklad ukazuje strukturu **Relationship** elementu.  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"
msdata:parent=""
msdata:child=""
msdata:parentkey=""
msdata:childkey="" />  
```  
  
 Atributy anotace **msdata:Relationship** identifikují prvky, které jsou součástí vztahu nadřazený-podřízený, jakož i **parentkey** a **childkey** prvky a atributy zapojené do vztahu. Proces mapování používá tyto informace ke generování tabulek v **datové sadě** a k vytvoření relace primárního klíče a cizího klíče mezi těmito tabulkami.  
  
 Například následující fragment schématu určuje **Prvky Order** a **OrderDetail** na stejné úrovni (ne vnořené). Schéma určuje anotaci **msdata:Relationship,** která určuje vztah nadřazený-podřízený mezi těmito dvěma prvky. V tomto případě musí být explicitní vztah určen pomocí anotace **msdata:Relationship.**  
  
```xml  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetail">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
       <xs:element name="Order">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrdDetailRelation"  
          msdata:parent="Order"  
          msdata:child="OrderDetail"
          msdata:parentkey="OrderNumber"  
          msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
```  
  
 Proces mapování používá element **Vztah** k vytvoření vztahu mezi nadřazeným a podřízeným vztahem mezi **sloupcem OrderNumber** v tabulce **Pořadí** a sloupcem **OrderNo** v tabulce **OrderDetail** v **sadě DataSet**. Proces mapování určuje pouze vztah; automaticky neurčuje žádná omezení hodnot v těchto sloupcích, stejně jako omezení primárního klíče/cizího klíče v relačních databázích.  
  
### <a name="in-this-section"></a>V tomto oddílu  
 [Mapování implicitních relací mezi elementy ve vnořeném schématu](map-implicit-relations-between-nested-schema-elements.md)  
 Popisuje omezení a vztahy, které jsou implicitně vytvořeny v **DataSet** při vnořené prvky jsou zjištěny ve schématu XML.  
  
 [Mapování relací zadaných pro vnořené elementy](map-relations-specified-for-nested-elements.md)  
 Popisuje, jak explicitně nastavit vztahy v **dataset** pro vnořené prvky ve schématu XML.  
  
 [Určení relací mezi elementy bez vnoření](specify-relations-between-elements-with-no-nesting.md)  
 Popisuje, jak vytvořit vztahy v **datové sadě** mezi prvky schématu XML, které nejsou vnořené.  
  
### <a name="related-sections"></a>Související oddíly  
 [Odvozování relační struktury datové sady ze schématu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Popisuje relační strukturu nebo schéma **datasady** vytvořené ze schématu jazyka definice schématu XML (XSD).  
  
 [Mapování omezení schématu XML (XSD) k omezením datové sady](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Popisuje prvky schématu XML použité k vytvoření jedinečných omezení cizího klíče v **datové sadě**.  
  
## <a name="see-also"></a>Viz také

- [Přehled ADO.NET](../ado-net-overview.md)

---
title: "Generování datovou sadu vztahů ze schématu XML (XSD)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 916b9ad24c2ae2334635760a520116b4c19df314
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>Generování datovou sadu vztahů ze schématu XML (XSD)
V <xref:System.Data.DataSet>, vytvoří přidružení mezi dvěma nebo více sloupců tak, že vytvoříte vztah nadřazený podřízený. Existují tři způsoby, jak představují **datovou sadu** vztahu v rámci schématu schématu XML definition language (XSD):  
  
-   Zadejte vnořené komplexní typy.  
  
-   Použití **msdata:Relationship** poznámky.  
  
-   Zadejte **xs:keyref** bez **msdata:ConstraintOnly** poznámky.  
  
## <a name="nested-complex-types"></a>Vnořené komplexní typy  
 Vnořené komplexní typ definice ve schématu označte vztahy nadřazených a podřízených elementů. Následující fragment kódu XML schéma ukazuje, že **OrderDetail** je podřízený element **pořadí** elementu.  
  
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
  
 Proces mapování schématu XML vytváří tabulky v **datovou sadu** , odpovídají vnořené komplexní typy ve schématu. Vytvoří také další sloupce, které se používají jako nadřazený**-**podřízené sloupce pro generovaný tabulky. Všimněte si, že tyto nadřazených**-**podřízené sloupce zadejte relace, který není stejný jako při zadání omezení primárního klíče a cizího klíče.  
  
## <a name="msdatarelationship-annotation"></a>MSDATA:Relationship – Poznámka  
 **Msdata:Relationship** poznámky umožňuje explicitně zadat vztahů nadřazenosti a podřízenosti mezi elementy ve schématu, které nejsou vnořené. Následující příklad ukazuje strukturu **vztah** elementu.  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 Atributy **msdata:Relationship** poznámky identifikovat elementy zahrnutých v relaci nadřazený podřízený, stejně jako **vlastnosti parentkey** a **childkey** elementy a atributy, které jsou součástí relace. Proces mapování používá tyto informace k vygenerování tabulky v **datovou sadu** a vytvořte primární klíč, cizí klíče relace mezi těmito tabulkami.  
  
 Například následující schéma fragment Určuje **pořadí** a **OrderDetail** prvků na stejné úrovni (nevnořené). Určuje schéma **msdata:Relationship** poznámky, která určuje relaci nadřazený podřízený mezi tyto dva prvky. V takovém případě explicitní relace musí být určen pomocí **msdata:Relationship** poznámky.  
  
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
  
 Proces mapování používá **vztah** elementu, který chcete vytvořit relaci nadřazený podřízený mezi **OrderNumber** sloupec v **pořadí** tabulky a **OrderNo** sloupec v **OrderDetail** tabulky v **datovou sadu**. Proces mapování určuje pouze relace; neurčuje automaticky žádná omezení na hodnoty v těchto sloupcích, stejně jako primární klíč, cizí klíče omezení relačních databází.  
  
### <a name="in-this-section"></a>V tomto oddílu  
 [Mapování implicitních relací mezi elementy ve vnořeném schématu](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 Popisuje omezení a vztahy, které jsou implicitně vytvořené v **datovou sadu** když dojde k vnořených elementů v schématu XML.  
  
 [Mapování relací zadaných pro vnořené elementy](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 Popisuje, jak nastavit explicitně vztahů v **datovou sadu** pro vnořené prvky ve schématu XML.  
  
 [Určení relací mezi elementy bez vnoření](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 Popisuje postup vytvoření vztahů v **datovou sadu** mezi elementy schématu XML, které nejsou vnořené.  
  
### <a name="related-sections"></a>Související oddíly  
 [Odvozování relační struktury datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Popisuje relační struktura nebo schéma z **datovou sadu** vytvořený ze schématu XML definition language (XSD) schématu.  
  
 [Mapování omezení schématu XML (XSD) k omezením datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Popisuje elementy schématu XML použitý k vytvoření jedinečné a cizí klíče omezení **datovou sadu**.  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

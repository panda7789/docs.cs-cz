---
title: Generování relací datové sady ze schématu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: 7c73dcec3d23b094436791af6649de83b9eacad9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43880033"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>Generování relací datové sady ze schématu XML (XSD)
V <xref:System.Data.DataSet>, formuláře přidružení mezi dvěma nebo více sloupců tak, že vytvoříte vztah nadřízenosti a podřízenosti. Existují tři způsoby, jak reprezentaci **datovou sadu** vztahu v rámci schématu schématu XML definice jazyk (XSD):  
  
-   Zadejte vnořené komplexní typy.  
  
-   Použití **msdata:Relationship** poznámky.  
  
-   Zadejte **xs:keyref** bez **msdata:ConstraintOnly** poznámky.  
  
## <a name="nested-complex-types"></a>Vnořené komplexní typy  
 Vnořené komplexní typ definice ve schématu označují vztahy nadřazenosti a podřízenosti prvků. Následující fragment XML schéma ukazuje, že **OrderDetail** je podřízený prvek **pořadí** elementu.  
  
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
  
 Proces mapování schématu XML vytvoří tabulky v **datovou sadu** , které odpovídají vnořené komplexní typy ve schématu. Vytvoří také další sloupce, které se používají jako nadřazený**-** podřízené sloupce pro generované tabulky. Všimněte si, že tyto nadřazené**-** podřízené sloupce zadejte relace, která není stejné jako zadání omezení primárního klíče a cizího klíče.  
  
## <a name="msdatarelationship-annotation"></a>MSDATA:Relationship poznámky  
 **Msdata:Relationship** anotace umožňuje explicitně určit vztahů nadřazenosti a podřízenosti mezi elementy ve schématu, které nejsou vnořené. Následující příklad ukazuje strukturu **vztah** elementu.  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 Atributy **msdata:Relationship** anotace identifikaci prvků, které jsou zahrnuté ve vztahu nadřazený podřízený, stejně jako **vlastnosti parentkey** a **childkey** elementy a atributy, které jsou součástí relace. Proces mapování používá tyto informace k vygenerování tabulek v **datovou sadu** a vytvořte primární klíč, cizí klíče vztah mezi těmito tabulkami.  
  
 Například následující fragment schéma určuje **pořadí** a **OrderDetail** elementů na stejné úrovni (ne vnořenou). Určuje schéma **msdata:Relationship** poznámky, které určuje vztah nadřízenosti a podřízenosti mezi těmito dvěma elementy. V takovém případě explicitního vztahu musí být zadán pomocí **msdata:Relationship** poznámky.  
  
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
  
 Používá proces mapování **vztah** prvku k vytvoření vztahu nadřazený podřízený mezi **OrderNumber** sloupec **pořadí** tabulky a **OrderNo** sloupec v **OrderDetail** v tabulku **datovou sadu**. Proces mapování pouze určuje vztah; neurčuje automaticky jakákoliv omezení u hodnot v těchto sloupcích, stejně jako primární klíč nebo omezení cizího klíče v relační databáze.  
  
### <a name="in-this-section"></a>V tomto oddílu  
 [Mapování implicitních relací mezi elementy ve vnořeném schématu](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 Popisuje omezení a vztahy, které se implicitně vytvářejí v **datovou sadu** při výskytu vnořené elementy ve schématu XML.  
  
 [Mapování relací zadaných pro vnořené elementy](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 Popisuje, jak nastavit explicitně vztahy v **datovou sadu** pro vnořené prvky ve schématu XML.  
  
 [Určení relací mezi elementy bez vnoření](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 Popisuje, jak vytvořit vztahy v **datovou sadu** mezi prvky schématu XML, které nejsou vnořené.  
  
### <a name="related-sections"></a>Související oddíly  
 [Odvozování relační struktury datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Popisuje relační struktury nebo schématu, **datovou sadu** , který je vytvořen z jazyk (XSD) schématu definice schématu XML.  
  
 [Mapování omezení schématu XML (XSD) k omezením datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Popisuje prvky schématu XML použitý k vytvoření jedinečné a cizího klíče omezení **datovou sadu**.  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

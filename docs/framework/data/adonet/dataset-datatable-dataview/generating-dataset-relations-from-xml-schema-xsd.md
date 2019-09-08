---
title: Generování relací datové sady ze schématu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: d00f07ee3338941b7de1bb890f71cd3c2d120246
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784641"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>Generování relací datové sady ze schématu XML (XSD)
V a <xref:System.Data.DataSet>tvoří přidružení mezi dvěma nebo více sloupci vytvořením vztahu nadřízený-podřízený. Existují tři způsoby, jak znázornit relaci **datové sady** v rámci schématu XSD (XML Schema Definition Language):  
  
- Zadejte vnořené komplexní typy.  
  
- Použijte anotaci **msdata: Relationship** .  
  
- Určete **xs: keyref** bez anotace **msdata: ConstraintOnly** .  
  
## <a name="nested-complex-types"></a>Vnořené komplexní typy  
 Vnořené definice komplexního typu ve schématu označují vztahy nadřazenosti a podřízenosti prvků. Následující fragment schématu XML ukazuje, že **OrderDetail** je podřízeným prvkem elementu **Order** .  
  
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
  
 Proces mapování schématu XML vytvoří tabulky v **datové sadě** , které odpovídají vnořeným komplexním typům ve schématu. Vytvoří také další sloupce, které jsou používány jako nadřazené **-** podřízené sloupce pro vygenerované tabulky. Všimněte si, že **-** tyto nadřazené podřízené sloupce určují relace, které se neshodují s určením omezení primárního klíče nebo cizího klíče.  
  
## <a name="msdatarelationship-annotation"></a>msdata: Poznámka vztahu  
 Anotace **msdata: Relationship** umožňuje explicitně zadat vztahy nadřazenosti a podřízenosti mezi prvky ve schématu, které nejsou vnořené. Následující příklad ukazuje strukturu elementu **Relationship** .  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 Atributy **msdata:** anotace Relationship identifikují prvky zahrnuté v relaci nadřazený-podřízený a také elementy **vlastnosti ParentKey** a **ChildKey** a atributy, které jsou součástí relace. Proces mapování používá tyto informace ke generování tabulek v **datové sadě** a k vytvoření vztahu primárního klíče/cizího klíče mezi těmito tabulkami.  
  
 Například následující fragment schématu určuje **pořadí** a **OrderDetail** prvky na stejné úrovni (nevnořený). Schéma určuje anotaci **msdata: Relationship** , která určuje vztah nadřazenosti a podřízenosti mezi těmito dvěma prvky. V takovém případě je nutné zadat explicitní relaci pomocí poznámky **msdata: Relationship** .  
  
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
  
 Proces mapování používá element **Relationship** k vytvoření vztahu nadřízený-podřízený mezi sloupcem **OrderNumber** v tabulce **Order** a sloupcem **OrderNo** v tabulce **OrderDetail** v **datové sadě**. Proces mapování určuje pouze vztah; neurčuje automaticky žádná omezení pro hodnoty v těchto sloupcích, stejně jako omezení primárního klíče a cizího klíče v relačních databázích.  
  
### <a name="in-this-section"></a>V tomto oddílu  
 [Mapování implicitních relací mezi elementy ve vnořeném schématu](map-implicit-relations-between-nested-schema-elements.md)  
 Popisuje omezení a vztahy, které jsou implicitně vytvořeny v **datové sadě** , pokud jsou ve schématu XML zjištěny vnořené prvky.  
  
 [Mapování relací zadaných pro vnořené elementy](map-relations-specified-for-nested-elements.md)  
 Popisuje způsob explicitního nastavování vztahů v **datové sadě** pro vnořené prvky ve schématu XML.  
  
 [Určení relací mezi elementy bez vnoření](specify-relations-between-elements-with-no-nesting.md)  
 Popisuje, jak vytvořit relace v **datové sadě** mezi prvky schématu XML, které nejsou vnořené.  
  
### <a name="related-sections"></a>Související oddíly  
 [Odvozování relační struktury datové sady ze schématu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Popisuje relační strukturu neboli schéma pro **datovou sadu** , která je vytvořena ze schématu XSD (XML Schema Definition Language).  
  
 [Mapování omezení schématu XML (XSD) k omezením datové sady](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Popisuje prvky schématu XML, které slouží k vytváření omezení jedinečného a cizího klíče v **datové sadě**.  
  
## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](../ado-net-overview.md)

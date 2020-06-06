---
title: 'Postupy: Generování tříd a dokumentace ke schématu XML pomocí nástroje XML Schema Definition'
description: Naučte se používat nástroj definice schématu XML ke generování schématu XML, který popisuje třídu nebo generuje třídu definovanou schématem XML.
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 0e4e84ea7e11b2e7a00c852d4a2075747c71267e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "84288963"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a>Postupy: Generování tříd a dokumentace ke schématu XML pomocí nástroje XML Schema Definition
Nástroj definici schématu XML (Xsd.exe) slouží ke generování schématu XML, která popisuje třídu nebo ke generování třídy definované ve schématu XML. Následující postupy ukazují, jak provádět tyto operace.

Nástroj pro definici schématu XML (XSD. exe) obvykle najdete v následující cestě: \
_C: \\ Program Files (x86) \\ Microsoft SDK \\ Windows \\ {Version} \\ bin \\ netfx {Version} Tools\\_

### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a>Chcete-li generovat třídy, které odpovídají určité schéma  
  
1. Otevřete příkazový řádek.  
  
2. Předejte schématu XML jako argument nástroj definici schématu XML, který vytvoří sadu tříd, které budou přesně odpovídat schématu XML, například:  
  
    ```console  
    xsd mySchema.xsd  
    ```  
  
     Nástroj lze zpracovat pouze schémata, které odkazují na specifikaci World Wide Web Consortium XML ze dne 16. Jinými slovy obor názvů schématu XML musí být "", http://www.w3.org/2001/XMLSchema jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema" />  
    ```  
  
3. Upravte tříd pomocí metody, vlastnosti nebo pole, podle potřeby. Další informace o úpravách třídy s atributy naleznete v tématu [řízení serializace XML pomocí atributů](controlling-xml-serialization-using-attributes.md) a [atributů, které řídí serializaci kódovaných SOAP](attributes-that-control-encoded-soap-serialization.md).  
  
 Často je užitečné si prohlédnout schématu XML datový proud, který je generována, když jsou serializovat instance třídy (nebo třídy). Například může publikovat vaše schéma ostatním uživatelům, nebo vám může porovnat s schématu, ke které se snaží dosáhnout shody.  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a>Generovat dokument XML schématu ze sady tříd  
  
1. Zkompilujte třídu nebo třídy do knihovny DLL.  
  
2. Otevřete příkazový řádek.  
  
3. Předejte knihovny DLL jako argument Xsd.exe, například:  
  
    ```console  
    xsd MyFile.dll  
    ```  
  
     Schéma (nebo schémata), bude napsán, počínaje název "schema0.xsd".  
  
## <a name="see-also"></a>Viz také

- <xref:System.Data.DataSet>
- [Nástroj definice schématu XML a serializace XML](the-xml-schema-definition-tool-and-xml-serialization.md)
- [Představení serializace XML](introducing-xml-serialization.md)
- [Nástroj definice schématu XML (XSD. exe)](xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Postupy: Serializace objektu](how-to-serialize-an-object.md)
- [Postupy: Deserializace objektu](how-to-deserialize-an-object.md)

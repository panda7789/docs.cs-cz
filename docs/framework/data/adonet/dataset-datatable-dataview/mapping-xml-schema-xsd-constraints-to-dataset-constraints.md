---
title: Mapování omezení XML schématu (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: c9cd97535a0165b82f0823c1f17f621491d4255c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677473"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapování omezení XML schématu (XSD) k omezením datové sady
Schéma XML definice jazyk (XSD) umožňuje zadat pro prvky a atributy, které definuje omezení. Při mapování schématu XML na relační schéma v <xref:System.Data.DataSet>, omezení schématu XML se mapují na odpovídající omezení relačních tabulek a sloupců v rámci **datovou sadu**.  
  
 Tato část pojednává o mapování následující omezení schématu XML:  
  
-   Omezení jedinečnosti zadat pomocí **jedinečný** elementu.  
  
-   Omezení pro klíč zadaný pomocí **klíč** elementu.  
  
-   Omezení keyref zadat pomocí **keyref** elementu.  
  
 Pomocí omezení na elementu nebo atributu zadejte určitá omezení na hodnoty elementu v žádné instanci dokumentu. Například klíče omezení na **CustomerID** podřízený prvek **zákazníka** element ve schématu znamená, že hodnoty **CustomerID** musí být podřízený element Jedinečný v žádné instanci dokumentu, a že nejsou povoleny hodnoty null.  
  
 Omezení je taky možné specifikovat mezi elementy a atributy v dokumentu, aby bylo možné navázat relaci v rámci dokumentu. Key ani keyref omezení se používají ve schématu zadat omezení v rámci dokumentu, výsledkem je vztah mezi dokumentu elementů a atributů.  
  
 Proces mapování převede odpovídající omezení u tabulky vytvořené v rámci těchto omezení schématu **datovou sadu**.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mapování jedinečných omezení schématu XML (XSD) k omezením datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Popisuje prvky schématu XML použitý k vytvoření jedinečné omezení **datovou sadu**.  
  
 [Mapování klíčových omezení schématu XML (XSD) k omezením datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Popisuje prvky schématu XML použitý k vytvoření omezení klíče (jedinečná omezení kde nejsou povoleny hodnoty null) **datovou sadu**.  
  
 [Mapování klíčových referenčních omezení schématu XML (XSD) k omezením datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Popisuje prvky schématu XML použitý k vytvoření keyref omezení (cizí klíč) **datovou sadu**.  
  
## <a name="related-sections"></a>Související oddíly  
 [Odvozování relační struktury datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Popisuje relační struktury nebo schématu, **datovou sadu** , který je vytvořen ze schématu XSD.  
  
 [Generování relací datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Popisuje prvky schématu XML použitý k vytvoření relace mezi sloupci tabulky v **datovou sadu**.  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

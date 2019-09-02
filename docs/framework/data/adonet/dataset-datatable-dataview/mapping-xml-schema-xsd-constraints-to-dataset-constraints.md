---
title: Mapování omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: b0082b534b8df10ac5277cf2f5aa5b2d2e40c11b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204630"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapování omezení schématu XML (XSD) k omezením datové sady
Jazyk definice schématu XML (XSD) umožňuje určení omezení pro prvky a atributy, které definuje. Při mapování schématu XML na relační schéma v <xref:System.Data.DataSet>, jsou omezení schématu XML mapována na odpovídající relační omezení pro tabulky a sloupce v rámci **datové sady**.  
  
 Tato část popisuje mapování následujících omezení schématu XML:  
  
- Omezení jedinečnosti zadané pomocí jedinečného prvku.  
  
- Omezení klíče zadané pomocí klíčového elementu.  
  
- Omezení keyref zadané pomocí elementu **keyref**  
  
 Pomocí omezení pro element nebo atribut zadáte určitá omezení pro hodnoty prvku v jakékoli instanci dokumentu. Například omezení klíče u podřízeného prvku **KódZákazníka** elementu Customer ve schématu označuje, že hodnoty podřízeného prvku **KódZákazníka** musí být jedinečné v jakékoli instanci dokumentu a že hodnoty null nejsou povoleny.  
  
 Omezení lze také zadat mezi elementy a atributy v dokumentu, aby bylo možné vytvořit relaci v rámci dokumentu. Omezení Key a keyref se používají ve schématu k určení omezení v rámci dokumentu, což má za následek relaci mezi prvky dokumentu a atributy.  
  
 Proces mapování převede Tato omezení schématu na vhodná omezení pro tabulky vytvořené v rámci **datové sady**.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mapování jedinečných omezení schématu XML (XSD) k omezením datové sady](map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Popisuje prvky schématu XML používané k vytváření jedinečných omezení v **datové sadě**.  
  
 [Mapování klíčových omezení schématu XML (XSD) k omezením datové sady](map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Popisuje prvky schématu XML, které se používají k vytvoření omezení klíče (jedinečná omezení, kde nejsou povoleny hodnoty null) v **datové sadě**.  
  
 [Mapování klíčových referenčních omezení schématu XML (XSD) k omezením datové sady](map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Popisuje prvky schématu XML používané k vytvoření omezení keyref (cizí klíč) v **datové sadě**.  
  
## <a name="related-sections"></a>Související oddíly  
 [Odvozování relační struktury datové sady ze schématu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Popisuje relační strukturu neboli schéma pro **datovou sadu** , která je vytvořena ze schématu XSD.  
  
 [Generování relací datové sady ze schématu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)  
 Popisuje prvky schématu XML, které slouží k vytvoření vztahů mezi sloupci tabulky v **datové sadě**.  
  
## <a name="see-also"></a>Viz také:

- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

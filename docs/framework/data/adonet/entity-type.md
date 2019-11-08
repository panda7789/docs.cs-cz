---
title: entity type
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: 1dafce5f7f95ba6f391c8742944f40a9afa7dcf8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737814"
---
# <a name="entity-type"></a>entity type
*Typ entity* je základní stavební blok pro popis struktury dat pomocí model EDM (Entity Data Model) (EDM). V koncepčním modelu představuje typ entity strukturu konceptů nejvyšší úrovně, jako jsou například zákazníci nebo objednávky. Typ entity je šablona pro instance typu entity. Každá šablona obsahuje následující informace:  
  
- Jedinečný název. (Povinné.)  
  
- [Klíč entity](entity-key.md) definovaný jednou nebo více vlastnostmi. (Povinné.)  
  
- Data ve formě [vlastností](property.md). (Volitelné.)  
  
- [Navigační vlastnosti](navigation-property.md) , které umožňují navigaci od jednoho [konce](association-end.md) [přidružení](association-type.md) k druhému konci. Volitelné  
  
 V aplikaci instance typu entity představuje konkrétní objekt (například konkrétního zákazníka nebo objednávky). Každá instance typu entity musí mít v [sadě entit](entity-set.md)jedinečný [klíč entity](entity-key.md) .  
  
 Dvě instance typu entity jsou považovány za rovné pouze v případě, že jsou stejného typu a hodnoty jejich klíčů entit jsou stejné.  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje koncepční model se třemi typy entit: `Book`, `Publisher`a `Author`:  
  
 ![Vzorový model se třemi typy entit](./media/entity-type/example-model-three-entity-types.gif)  
  
 Všimněte si, že vlastnosti každého typu entity, který tvoří klíč entity, jsou označeny řetězcem "(Key)".  
  
 [ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language). Následující CSDL definuje typ entity `Book` zobrazený v diagramu výše:  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)
- [facet](facet.md)

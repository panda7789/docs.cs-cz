---
title: association set end
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 48ba84d46e380462405551cc2d826d84368b351a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786928"
---
# <a name="association-set-end"></a>association set end
*Zakončení sady přidružení* identifikuje [typ entity](entity-type.md) a [sadu entit](entity-set.md) na konci [sady přidružení](association-set.md). Zakončení sady přidružení je definováno jako součást sady přidružení. sada přidružení musí mít zakončení přesně dvou sad přidružení.  
  
 Definice end sady přidružení obsahuje následující informace:  
  
- Jeden z typů entit zapojených do sady přidružení. Požadovanou  
  
- Sada entit pro typ entity zapojená do sady přidružení. Požadovanou  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje koncepční model se dvěma přidruženími: `WrittenBy` a. `PublishedBy`  
  
 ![Vzorový model se třemi typy entit](./media/association-set-end/example-model-three-entity-types.gif)  
  
 Následující diagram znázorňuje sadu přidružení (`PublishedBy`) a dvě sady entit (`Books` a `Publishers`) na základě koncepčního modelu uvedeného výše. Sada přidružení končí `Books` jako sady entit a `Publishers` . BI v `Books` sadě entit představuje instanci `Book` typu entity v době běhu. Podobně PJ představuje `Publisher` instanci `Publishers` v sadě entit. BiPj představuje instanci `PublishedBy` přidružení `PublishedBy` v sadě přidružení.  
  
 ![Snímek obrazovky, který zobrazuje příklad sady.](./media/association-set-end/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů DSL označované jako konceptuální schéma Definition Language ([CSDL](./ef/language-reference/csdl-specification.md)). Následující CSDL definuje kontejner entit s jednou sadou přidružení pro každé přidružení v diagramu výše. Všimněte si, že zakončení sady přidružení je definováno jako součást každé definice sady přidružení.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)

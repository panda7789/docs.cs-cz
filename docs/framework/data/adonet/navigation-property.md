---
title: Navigační vlastnost – ADO.NET
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: afb2043abf70fa92ea7cdf8d1e8246d5cdfdba74
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738384"
---
# <a name="navigation-property"></a>Navigační vlastnost

*Navigační vlastnost* je volitelnou vlastností u [typu entity](entity-type.md) , která umožňuje navigaci od jednoho [konce](association-end.md) [přidružení](association-type.md) k druhému konci. Na rozdíl od jiných [vlastností](property.md)navigační vlastnosti neobsahují data.

Definice navigační vlastnosti zahrnuje následující:

- Název. Požadovanou

- Přidružení, které naviguje. Požadovanou

- Konec přidružení, které naviguje. Požadovanou

Všimněte si, že navigační vlastnosti jsou volitelné na obou typech entit na konci přidružení. Definujete-li vlastnost navigace na jednom typu entity na konci přidružení, nemusíte definovat vlastnost navigace na typu entity na druhém konci přidružení.

Datový typ vlastnosti navigace je určen [násobností](association-end-multiplicity.md) jeho vzdáleného [zakončení přidružení](association-end.md). Předpokládejme například, že navigační vlastnost, `OrdersNavProp`, existuje v `Customer` typu entity a přechází mezi `Customer` a `Order`přidružení 1:1. Vzhledem k tomu, že vzdálené zakončení přidružení pro navigační vlastnost má násobnost mnoho (\*), je jeho datovým typem kolekce (z `Order`). Podobně platí, že pokud v `Order` typu entity `CustomerNavProp`existuje vlastnost navigace, její datový typ by byl `Customer`, protože násobnost vzdáleného elementu end je jedna (1).

## <a name="example"></a>Příklad

Následující diagram znázorňuje koncepční model se třemi typy entit: `Book`, `Publisher`a `Author`. Navigační vlastnosti, `Publisher` a `Authors`, jsou definovány pro typ entity Book. Navigační vlastnost `Books` je definována jak pro typ entity Vydavatel, tak pro typ entity `Author`.

 ![Diagram znázorňující koncepční model se třemi typy entit.](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

[ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language). Následující CSDL definuje typ entity `Book` zobrazený v diagramu výše:

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

Všimněte si, že atributy XML slouží ke sdělování informací nezbytných pro definování navigační vlastnosti: atribut `Name` obsahuje název vlastnosti `Relationship` obsahuje název přidaného přidružení a `FromRole` a `ToRole` obsahovat. konec přidružení.

## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)
- [Relace, navigační vlastnosti a cizí klíče](/ef/ef6/fundamentals/relationships)

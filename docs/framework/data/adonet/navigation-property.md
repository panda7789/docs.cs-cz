---
title: Navigační vlastnost – ADO.NET
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: b57ecf9329aa9ea8afc07507613c9e3961bfd0a9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836594"
---
# <a name="navigation-property"></a>Navigační vlastnost

A *navigační vlastnost* vlastnost je volitelná na [typ entity](entity-type.md) , který umožňuje navigace z jednoho [end](association-end.md) z [přidružení](association-type.md) do druhém konci. Na rozdíl od jiných [vlastnosti](property.md), navigačních vlastností není vázané na data.

Definice vlastnosti navigace zahrnuje následující položky:

- Název. (Povinné)

- Přidružení, na kterou se přejde. (Povinné)

- Elementy end přidružení, na kterou se přejde. (Povinné)

Všimněte si, že jsou volitelné na oba typy entit na konci asociace navigační vlastnosti. Pokud definujete navigační vlastnost jednoho typu entity na konci asociace, není nutné definovat vlastnost navigace typu entity na druhém konci přidružení.

Datový typ vlastnosti navigace závisí [násobnost](association-end-multiplicity.md) jeho vzdáleného [end přidružení](association-end.md). Předpokládejme například, vlastnost navigace, `OrdersNavProp`, existuje na `Customer` typu entity a přejde na více přidružení mezi `Customer` a `Order`. Protože ukončení vzdálené přidružení pro navigační vlastnost má násobnost mnoha (\*), jeho datový typ je kolekce (z `Order`). Podobně, pokud vlastnost navigace, `CustomerNavProp`, existuje na `Order` typ entity, jeho datový typ by `Customer`, protože vzdáleným koncem násobnost je jedna (1).

## <a name="example"></a>Příklad

Následující diagram znázorňuje Koncepční model s tři typy entit: `Book`, `Publisher`, a `Author`. Vlastnosti navigace `Publisher` a `Authors`, jsou definovány na typ entity adresáře. Navigační vlastnost `Books` je definována obě vydavatele typu entity a `Author` typ entity.

 ![Diagram znázorňující konceptuálního modelu s tři typy entit.](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

[ADO.NET Entity Framework](./ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](./ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů. Definuje následující CSDL `Book` typ entity, které jsou zobrazeny ve výše uvedeném diagramu:

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

Všimněte si, že atributy ve formátu XML se používají ke komunikaci informace potřebné k definování navigační vlastnost: Atribut `Name` obsahuje název vlastnosti, `Relationship` obsahuje název přidružení se odkazuje, a `FromRole` a `ToRole` obsahovat elementy end přidružení.

## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)
- [Relace, navigačních vlastností a cizí klíče](/ef/ef6/fundamentals/relationships)

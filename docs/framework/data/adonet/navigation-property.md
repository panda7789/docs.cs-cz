---
title: Navigační vlastnost
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: 09c0e5e5dbc7b2be89e044c4d111fdd65fada7c7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662176"
---
# <a name="navigation-property"></a>Navigační vlastnost
A *navigační vlastnost* vlastnost je volitelná na [typ entity](../../../../docs/framework/data/adonet/entity-type.md) , který umožňuje navigace z jednoho [end](../../../../docs/framework/data/adonet/association-end.md) z [přidružení](../../../../docs/framework/data/adonet/association-type.md) do druhém konci. Na rozdíl od jiných [vlastnosti](../../../../docs/framework/data/adonet/property.md), navigačních vlastností není vázané na data.  
  
 Definice vlastnosti navigace zahrnuje následující položky:  
  
-   Název. (Povinné)  
  
-   Přidružení, na kterou se přejde. (Povinné)  
  
-   Elementy end přidružení, na kterou se přejde. (Povinné)  
  
 Všimněte si, že jsou volitelné na oba typy entit na konci asociace navigační vlastnosti. Pokud definujete navigační vlastnost jednoho typu entity na konci asociace, není nutné definovat vlastnost navigace typu entity na druhém konci přidružení.  
  
 Datový typ vlastnosti navigace závisí [násobnost](../../../../docs/framework/data/adonet/association-end-multiplicity.md) jeho vzdáleného [end přidružení](../../../../docs/framework/data/adonet/association-end.md). Předpokládejme například, vlastnost navigace, `OrdersNavProp`, existuje na `Customer` typu entity a přejde na více přidružení mezi `Customer` a `Order`. Protože ukončení vzdálené přidružení pro navigační vlastnost má násobnost mnoho (*), je jeho datový typ kolekce (z `Order`). Podobně, pokud vlastnost navigace, `CustomerNavProp`, existuje na `Order` typ entity, jeho datový typ by `Customer`, protože vzdáleným koncem násobnost je jedna (1).  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model s tři typy entit: `Book`, `Publisher`, a `Author`. Vlastnosti navigace `Publisher` a `Authors`, jsou definovány na typ entity adresáře. Navigační vlastnost `Books` je definována obě vydavatele typu entity a `Author` typ entity.  
  
 ![Model s navigační vlastnosti](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů. Definuje následující CSDL `Book` typ entity, které jsou zobrazeny ve výše uvedeném diagramu:  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 Všimněte si, že atributy ve formátu XML se používají ke komunikaci informace potřebné k definování navigační vlastnost: Atribut `Name` obsahuje název vlastnosti, `Relationship` obsahuje název přidružení se odkazuje, a `FromRole` a `ToRole` obsahovat elementy end přidružení.  
  
## <a name="see-also"></a>Viz také:
- [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)

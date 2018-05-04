---
title: navigační vlastnost
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: 149aefe84c9d04fab1786b99c2ac8c5060bccd87
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="navigation-property"></a>navigační vlastnost
A *navigační vlastnost* je volitelná vlastnost na [typ entity](../../../../docs/framework/data/adonet/entity-type.md) umožňuje pro navigaci z jednoho [end](../../../../docs/framework/data/adonet/association-end.md) z [přidružení](../../../../docs/framework/data/adonet/association-type.md) na druhém konci. Na rozdíl od jiných [vlastnosti](../../../../docs/framework/data/adonet/property.md), navigačních vlastností nepřenášejí data.  
  
 Navigační vlastnost definice zahrnuje následující položky:  
  
-   Název. (Povinné)  
  
-   Přidružení, který se odkazuje. (Povinné)  
  
-   Elementy end přidružení, který se odkazuje. (Povinné)  
  
 Všimněte si, že jsou volitelné na oba typy entit na koncích přidružení navigační vlastnosti. Pokud definujete navigační vlastnost u jednoho typu entity na konci tohoto přidružení, nemáte definovat navigační vlastnost typu entity na druhém konci přidružení.  
  
 Datový typ vlastnosti navigace je dáno [násobnost](../../../../docs/framework/data/adonet/association-end-multiplicity.md) jeho vzdálené [end přidružení](../../../../docs/framework/data/adonet/association-end.md). Předpokládejme například, navigační vlastnost `OrdersNavProp`, existuje na `Customer` typu entity a přejde na více přidružení mezi `Customer` a `Order`. Protože end vzdáleného přidružení pro navigační vlastnost má násobnost mnoho (*), je jeho datový typ kolekce (z `Order`). Podobně, pokud navigační vlastnost `CustomerNavProp`, existuje na `Order` typ entity, bude jeho datového typu `Customer`, protože násobnost konce vzdálené je jedna (1).  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model se tři typy entit: `Book`, `Publisher`, a `Author`. Navigační vlastnosti `Publisher` a `Authors`, jsou definovány na typ entity adresáře. Navigační vlastnost `Books` je definována obě vydavatele typu entity a `Author` typ entity.  
  
 ![Modelu s navigační vlastnosti](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech. Definuje následující CSDL `Book` typ entity, které jsou uvedené v diagramu výše:  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 Všimněte si, že XML atributy se používají ke komunikaci informace potřebné k definování navigační vlastnost: atribut `Name` obsahuje název vlastnosti, `Relationship` obsahuje název tohoto přidružení se odkazuje, a `FromRole` a `ToRole` obsahovat konce přidružení.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)

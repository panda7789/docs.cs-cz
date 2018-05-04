---
title: end přidružení
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: 9d7bd6fa92a4337add18deafbeb5ad28fefcb749
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="association-end"></a>end přidružení
*End přidružení* identifikuje [typ entity](../../../../docs/framework/data/adonet/entity-type.md) na jednom konci [přidružení](../../../../docs/framework/data/adonet/association-type.md) a počet entit, zadejte instancí, které může existovat na tomto konci tohoto přidružení. Zakončení přidružení jsou definované jako součást přidružení; přidružení musí mít přesně dva elementy end přidružení. [Navigační vlastnosti](../../../../docs/framework/data/adonet/navigation-property.md) povolit pro navigaci z elementu end přidružení jeden na druhý.  
  
 Definici end přidružení obsahuje následující informace:  
  
-   Jeden z typů entity účastní přidružení. (Povinné)  
  
    > [!NOTE]
    >  Pro danou přidružení může být pro každý element end přidružení zadaný typ entity stejné. Tím se vytvoří vlastní přidružení.  
  
-   [Násobnost end přidružení](../../../../docs/framework/data/adonet/association-end-multiplicity.md) určující počet instancí typ entity, které mohou být na jednom konci přidružení. Násobnost end přidružení může mít hodnotu jedna (1), žádnou nebo jednu (0..1), nebo mnoho (*).  
  
-   Název elementu end přidružení. (Volitelné)  
  
-   Informace o operacích, které se provádí na konci přidružení, jako je například cascade na odstranění. (Volitelné)  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model se dvě přidružení: `PublishedBy` a `WrittenBy`. Přidružení končí pro `PublishedBy` jsou přidružení `Book` a `Publisher` typy entit. Násobnost `Publisher` koncový je jedna (1) a násobnosti atributu `Book` koncový je mnoho (*), označující, že vydavatel publikuje mnoho knihy a publikování knihy se jeden vydavatelem.  
  
 ![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 ADO.NET Entity Framework používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech. Definuje CSDL níže `PublishedBy` přidružení vidět v diagramu výše. Všimněte si, že jsou zadané typu, názvu a násobnost konce každé přidružení podle atributů XML ( `Type`, `Role`, a `Multiplicity` atributy v uvedeném pořadí). Volitelné informace o operace provedené na element end je zadaný v elementu XML ( `OnDelete` element). V takovém případě je-li vydavatel odstraněna, proto jsou všechny přidružené knih.  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)

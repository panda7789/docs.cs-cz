---
title: association end
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: 33cc2e10d9b72ef7f5f024905938c41fcc4a9755
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785044"
---
# <a name="association-end"></a>association end
*Zakončení přidružení* identifikuje [typ entity](entity-type.md) na jednom konci [přidružení](association-type.md) a počet instancí typu entity, které mohou existovat na konci přidružení. Zakončení přidružení jsou definována jako součást přidružení; přidružení musí mít přesně dvě zakončení přidružení. [Navigační vlastnosti](navigation-property.md) umožňují navigaci z jednoho zakončení přidružení k druhému.  
  
 Definice elementu end přidružení obsahuje následující informace:  
  
- Jeden z typů entit zapojených do přidružení. Požadovanou  
  
    > [!NOTE]
    > Pro dané přidružení může být typ entity zadaný pro každý konec přidružení stejný. Tím se vytvoří samo přidružení.  
  
- [Násobnost zakončení přidružení](association-end-multiplicity.md) , která označuje počet instancí typu entity, které mohou být na jednom konci přidružení. Násobnost zakončení přidružení může mít hodnotu jedna (1), 0 nebo 1 (0.. 1) nebo mnoho (\*).  
  
- Název zakončení přidružení. Volitelné  
  
- Informace o operacích, které jsou prováděny na konci přidružení, jako je například kaskáda při odstranění. Volitelné  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje koncepční model se dvěma přidruženími: `PublishedBy` a. `WrittenBy` Přidružení `PublishedBy` jsouzakončenápro`Publisher` přidružení jsou typy entit a.`Book` Násobnost elementu `Publisher` end je jedna (1) a násobnost elementu `Book` end je mnoho (\*), což znamená, že vydavatel zveřejňuje mnoho knih a kniha je publikována jedním vydavatelem.  
  
 ![Vzorový model se třemi typy entit](./media/association-end/example-model-three-entity-types.gif)  
  
 ADO.NET Entity Framework používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](./ef/language-reference/csdl-specification.md)(konceptuální schéma Definition Language). Následující CSDL definuje `PublishedBy` přidružení zobrazené v diagramu výše. Všimněte si, že typ, název a násobnost každého elementu end přidružení jsou určeny atributy XML (v `Type` `Role` `Multiplicity` uvedeném pořadí). Volitelné informace o operacích provedených na konci jsou uvedeny v elementu XML ( `OnDelete` element). V tomto případě platí, že pokud je Vydavatel odstraněn, jsou všechny přidružené knihy.  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)

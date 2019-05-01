---
title: entity set
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: 7fcaa2cb9bac02271940a712d4d044df25d7d4cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033953"
---
# <a name="entity-set"></a>entity set
*Sadu entit* je logický kontejner pro instance [typ entity](../../../../docs/framework/data/adonet/entity-type.md) a instance libovolného typu odvozeného z tohoto typu entity. (Informace o odvozených typech naleznete v tématu [modelu Entity Data Model: Dědičnost](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).) Vztah mezi typem entity a sady entit je obdobou vztah mezi řádek a tabulky v relační databázi: Jako řádek typ entity, který popisuje strukturu dat a jako tabulka, obsahuje sadu entit instance dané struktury. Sadu entit není konstrukce; modelování dat strukturu dat nepopisuje. Místo toho sadu entit poskytuje konstrukci pro prostředí hostování nebo úložiště (například do databáze SQL serveru nebo modul common language runtime) do instance typu entity skupiny tak, že je možné mapovat do úložiště dat.  
  
 Sadu entit je definována v rámci [kontejneru entity](../../../../docs/framework/data/adonet/entity-container.md), což je logické seskupení sady entit a [sad přidružení](../../../../docs/framework/data/adonet/association-set.md).  
  
 Pro instanci entity typu existovat v sadu entit musí být splněné následující podmínky:  
  
- Typ instance je buď stejná jako typ entity, na kterém je na základě sady entit nebo typ instance je podtypem typu entity.  
  
- [Klíč entity](../../../../docs/framework/data/adonet/entity-key.md) pro instanci je jedinečný v rámci sady entit.  
  
- Instance neexistuje v jiné sadě entit.  
  
    > [!NOTE]
    >  Více sad entit můžete definovat pomocí stejného typu entity, ale může existovat pouze instance typu danou entitu v sadě entit.  
  
 Není nutné definovat nastavení pro každý typ entity v konceptuálním modelu entity.  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model s tři typy entit: `Book`, `Publisher`, a `Author`.  
  
 ![Příklad modelu s tři typy entit](./media/entity-set/example-model-three-entity-types.gif)  
  
 Následující diagram znázorňuje dvě sady entit (`Books` a `Publishers`) a sada přidružení (`PublishedBy`) založené na konceptuální model, uvedené výše. BI v `Books` sadu entit představuje instanci `Book` typ entity v době běhu. Obdobně Pj představují `Publisher` instance v `Publishers` sady entit. BiPj představuje instanci `PublishedBy` přidružení v `PublishedBy` sada přidružení.  
  
 ![Snímek obrazovky zobrazující příklad sady.](./media/entity-set/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů. Následující CSDL definuje kontejneru entity s entitami nastavit pro každý typ entity v konceptuálním modelu uvedené výše. Všimněte si, že název a entita, zadejte pro každou sadu entit, jsou definovány pomocí atributů XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Je možné definovat více sad entit podle typu (MEST). Definuje kontejner služby entity se dvěma sadami entity pro následující CSDL `Book` typ entity:  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)

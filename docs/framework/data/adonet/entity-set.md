---
title: entity set
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: 5a2465801c270813dd7bca2144d05fa202571153
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738430"
---
# <a name="entity-set"></a>entity set
*Sada entit* je logický kontejner pro instance [typu entity](entity-type.md) a instance libovolného typu odvozeného z tohoto typu entity. (Informace o odvozených typech naleznete v tématu [model EDM (Entity Data Model): dědičnost](entity-data-model-inheritance.md).) Vztah mezi typem entity a sadou entit je podobný relaci mezi řádkem a tabulkou v relační databázi: jako řádek, typ entity popisuje datovou strukturu a, podobně jako tabulka, sada entit obsahuje instance dané struktury. Sada entit není konstrukcí modelování dat; nepopisuje strukturu dat. Místo toho sada entit poskytuje konstrukci pro prostředí hostování nebo úložiště (například modul CLR (Common Language Runtime) nebo databáze SQL Server) k seskupení instancí typů entit tak, aby bylo možné je namapovat na úložiště dat.  
  
 Sada entit je definována v rámci [kontejneru entit](entity-container.md), což je logické seskupení sad entit a [sad přidružení](association-set.md).  
  
 Aby v sadě entit existovala instance typu entity, musí být splněny následující podmínky:  
  
- Typ instance je buď stejný jako typ entity, na které je založena sada entit, nebo typ instance je podtypem typu entity.  
  
- [Klíč entity](entity-key.md) pro instanci je v sadě entit jedinečný.  
  
- Instance neexistuje v žádné jiné sadě entit.  
  
    > [!NOTE]
    > Pomocí stejného typu entity lze definovat více sad entit, ale instance daného typu entity může existovat pouze v jedné sadě entit.  
  
 Pro každý typ entity v koncepčním modelu nemusíte definovat sadu entit.  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje koncepční model se třemi typy entit: `Book`, `Publisher`a `Author`.  
  
 ![Vzorový model se třemi typy entit](./media/entity-set/example-model-three-entity-types.gif)  
  
 Následující diagram znázorňuje dvě sady entit (`Books` a `Publishers`) a sadu přidružení (`PublishedBy`) založenou na koncepčním modelu uvedeném výše. BI v `Books` sadě entit představuje instanci `Book` typu entity v době běhu. Podobně PJ představuje instanci `Publisher` v sadě entit `Publishers`. BiPj představuje instanci přidružení `PublishedBy` v sadě přidružení `PublishedBy`.  
  
 ![Snímek obrazovky, který zobrazuje příklad sady.](./media/entity-set/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language). Následující CSDL definuje kontejner entit s jednou sadou entit pro každý typ entity v koncepčním modelu uvedeném výše. Všimněte si, že název a typ entity pro každou sadu entit jsou definovány pomocí atributů XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Je možné definovat několik sad entit na typ (MEST). Následující CSDL definuje kontejner entit se dvěma sadami entit pro `Book` typ entity:  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)

---
title: association set
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: e279322f9e950cd4359db8c6dce39bfc46d188f6
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732378"
---
# <a name="association-set"></a>association set
*Sada přidružení* je logický kontejner pro instance [přidružení](association-type.md) stejného typu. Sada přidružení není konstrukcí modelování dat; To znamená, že nepopisuje strukturu dat nebo relací. Místo toho poskytuje sada přidružení konstrukci pro prostředí hostování nebo úložiště (například modul CLR (Common Language Runtime) nebo databáze SQL Server) k seskupení instancí přidružení, aby bylo možné je namapovat na úložiště dat.  
  
 Sada přidružení je definována v rámci [kontejneru entit](entity-container.md), což je logické seskupení [sad entit](entity-set.md) a sad přidružení.  
  
 Definice sady přidružení obsahuje následující informace:  
  
- Název sady přidružení. Požadovanou  
  
- Přidružení, které bude obsahovat instance. Požadovanou  
  
- [Končí dvě sady přidružení](association-set-end.md).  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje koncepční model se dvěma přidruženími: `PublishedBy`a `WrittenBy`. I když informace o sadách přidružení nejsou předány v diagramu, další diagram zobrazuje příklad sad přidružení a sad entit založených na tomto modelu.  
  
 ![Vzorový model se třemi typy entit](./media/association-set/example-model-three-entity-types.gif)  
  
 Následující příklad ukazuje sadu přidružení (`PublishedBy`) a dvě sady entit (`Books` a `Publishers`) na základě koncepčního modelu uvedeného výše. BI v `Books` sadě entit představuje instanci `Book` typu entity v době běhu. Podobně PJ představuje instanci `Publisher` v sadě entit `Publishers`. BiPj představuje instanci přidružení `PublishedBy` v sadě přidružení `PublishedBy`.  
  
 ![Snímek obrazovky, který zobrazuje příklad sady.](./media/association-set/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language). Následující CSDL definuje kontejner entit s jednou sadou přidružení pro každé přidružení v diagramu výše. Všimněte si, že název a přidružení pro každou sadu přidružení jsou definovány pomocí atributů XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Pro každé přidružení je možné definovat několik sad přidružení, pokud žádné dvě sady přidružení nesdílejí [zakončení sady přidružení](association-set-end.md). Následující CSDL definuje kontejner entit se dvěma sadami přidružení pro `WrittenBy` přidružení. Všimněte si, že pro `Book` a `Author` typů entit byly definovány více sad entit a že žádná sada přidružení nesdílí sadu přidružení end.  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)
- [foreign key property](foreign-key-property.md)

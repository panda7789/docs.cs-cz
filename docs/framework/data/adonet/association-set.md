---
title: association set
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: af9297d9c827b12ed8611e99930234511f7f661c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204481"
---
# <a name="association-set"></a>association set
*Sada přidružení* je logický kontejner [přidružení](../../../../docs/framework/data/adonet/association-type.md) instance stejného typu. Skupinu přidružení není konstrukce; modelování dat nepopisuje to znamená, že struktura dat nebo vztahy. Místo toho přidružení sady zajišťující konstrukci prostředí hostování nebo úložiště (například do databáze SQL serveru nebo modul common language runtime) do skupiny přidružení instance tak, že je možné mapovat do úložiště dat.  
  
 Skupinu přidružení je definována v rámci [kontejneru entity](../../../../docs/framework/data/adonet/entity-container.md), což je logické seskupení [sad entit](../../../../docs/framework/data/adonet/entity-set.md) a sad přidružení.  
  
 Definici pro skupinu přidružení obsahuje následující informace:  
  
-   Název sady přidružení. (Povinné)  
  
-   Přidružení, které bude obsahovat instancí. (Povinné)  
  
-   Dvě [přidružení nastavení zakončení](../../../../docs/framework/data/adonet/association-set-end.md).  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model se dvěma přidružení: `PublishedBy`, a `WrittenBy`. I když se informace o sadách přidružení se předávají v diagramu, následující diagram znázorňuje příklad sad přidružení a sady entit na základě tohoto modelu.  
  
 ![Příklad modelu s tři typy entit](./media/association-set/example-model-three-entity-types.gif)  
  
 Následující příklad ukazuje skupinu přidružení (`PublishedBy`) a dvě sady entit (`Books` a `Publishers`) založené na konceptuální model, uvedené výše. BI v `Books` sadu entit představuje instanci `Book` typ entity v době běhu. Obdobně Pj představuje `Publisher` instance v `Publishers` sady entit. BiPj představuje instanci `PublishedBy` přidružení v `PublishedBy` sada přidružení.  
  
 ![Snímek obrazovky zobrazující příklad sady.](./media/association-set/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů. Následující CSDL definuje kontejneru entity s jeden přidružení nastavení pro každé přidružení ve výše uvedeném diagramu. Všimněte si, že název a přidružení pro každé přidružení nastavení jsou definovány pomocí atributů XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Je možné definovat více sad přidružení za přidružení, pokud žádné sdílené složky nastaví dva přidružení [přidružení nastavit konec](../../../../docs/framework/data/adonet/association-set-end.md). Definuje kontejner služby entity se dvěma sadami přidružení pro následující CSDL `WrittenBy` přidružení. Všimněte si, že byla definovaná pro více sad entit `Book` a `Author` typy entit a nastavit žádné přidružení sdílené složky přidružení nastavit konec.  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
- [foreign key property](../../../../docs/framework/data/adonet/foreign-key-property.md)

---
title: sada entit
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 9d0cef0247c36f3c7819e37f8144635ebdbf610b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="entity-set"></a>sada entit
*Sady entit* je logický kontejner pro instance [typ entity](../../../../docs/framework/data/adonet/entity-type.md) a instancí jakéhokoli typu odvozeného z tohoto typu entity. (Informace o odvozené typy najdete v tématu [datového modelu Entity: dědičnosti](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).) Vztah mezi typem entity a sadu entit je podobná vztah mezi řádek a tabulku v relační databázi: řádek, jako je typ entity popisuje strukturu dat a jako tabulku, obsahuje sadu entit instance dané struktury. Sadu entit není dat modelování konstrukce; Struktura dat nepopisuje. Místo toho sadu entit poskytuje konstrukt pro hostování nebo úložiště prostředí (například databáze SQL serveru nebo modul common language runtime) k instancím typu entity skupiny tak, aby se můžete namapovat k úložišti dat.  
  
 Sadu entit je definována v rámci [kontejneru entit](../../../../docs/framework/data/adonet/entity-container.md), což je logické seskupení sad entit a [nastaví přidružení](../../../../docs/framework/data/adonet/association-set.md).  
  
 Instance typu entity existovat v sadu entit musí být splněné následující podmínky:  
  
-   Typ instance je buď stejný jako typ entity, na kterém je na základě sady entit nebo typ instance není podtypem typ entity.  
  
-   [Klíč entity](../../../../docs/framework/data/adonet/entity-key.md) pro instance je jedinečné v rámci sady entit.  
  
-   Instance neexistuje v jiné sadě entit.  
  
    > [!NOTE]
    >  Několik sad entit lze definovat pomocí stejného typu entity, ale může existovat pouze instance typu danou entitu v sadě jednu entitu.  
  
 Nemusíte definovat entitu ke každému typu entity v konceptuálním modelu.  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model se tři typy entit: `Book`, `Publisher`, a `Author`.  
  
 ![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Následující diagram znázorňuje dvě sady entit (`Books` a `Publishers`) a nastavená přidružení (`PublishedBy`) na základě konceptuálního modelu uvedené výše. BI v `Books` sady entit představuje instanci `Book` typ entity v době běhu. Podobně Pj představují `Publisher` instance v `Publishers` sady entit. BiPj představuje instanci `PublishedBy` přidružení v `PublishedBy` sadu přidružení.  
  
 ![Nastaví příklad](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech. Následující CSDL definuje jednu sadu entit pro každý typ entity v konceptuálním modelu výše uvedeném kontejner entity. Všimněte si, že název a entity zadejte pro každou sadu entit jsou definovány pomocí atributy XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Je možné definovat několik sad entit na typ (MEST). Následující CSDL definuje kontejner entity dvě sady entit pro `Book` typ entity:  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)

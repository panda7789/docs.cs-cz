---
title: "Sada přidružení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fa977f69951184629f4e9555f524f074a09ce96a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="association-set"></a>Sada přidružení
*Sadu přidružení* je logický kontejner pro [přidružení](../../../../docs/framework/data/adonet/association-type.md) instance stejného typu. Sadu přidružení není dat modelování konstrukce; nepopisuje tedy strukturu dat nebo vztahy. Místo toho sadu přidružení poskytuje konstrukt pro hostování nebo úložiště prostředí (například databáze SQL serveru nebo modul common language runtime) k instancím přidružení skupiny, které může být namapovaný na úložiště dat.  
  
 Sadu přidružení je definována v rámci [kontejneru entit](../../../../docs/framework/data/adonet/entity-container.md), což je logické seskupení [sad entit](../../../../docs/framework/data/adonet/entity-set.md) a nastaví přidružení.  
  
 Definice pro sadu přidružení obsahuje následující informace:  
  
-   Název sady přidružení. (Povinné)  
  
-   Přidružení, které bude obsahovat instancí. (Povinné)  
  
-   Dva [končí nastavená přidružení](../../../../docs/framework/data/adonet/association-set-end.md).  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model se dvě přidružení: `PublishedBy`, a `WrittenBy`. I když v diagramu není bude předávat informace o přidružení sady, další diagram ukazuje příklad sady přidružení a sad entit na základě tohoto modelu.  
  
 ![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Následující příklad ukazuje sadu přidružení (`PublishedBy`) a dvě sady entit (`Books` a `Publishers`) na základě konceptuálního modelu uvedené výše. BI v `Books` sady entit představuje instanci `Book` typ entity v době běhu. Podobně, představuje Pj `Publisher` instance v `Publishers` sady entit. BiPj představuje instanci `PublishedBy` přidružení v `PublishedBy` sadu přidružení.  
  
 ![Nastaví příklad](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech. Následující CSDL definuje jednu sadu pro každé přidružení v diagramu výše přidružení kontejner entity. Všimněte si, že název a přidružení pro každé přidružení nastavit jsou definovány pomocí atributy XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Je možné definovat několik sad přidružení na přidružení, stejně dlouho jako žádná sdílená složka sady dvě přidružení [nastavená přidružení end](../../../../docs/framework/data/adonet/association-set-end.md). Následující CSDL definuje kontejner entity dvě sady přidružení pro `WrittenBy` přidružení. Všimněte si, že se definovaly několik sad entit `Book` a `Author` typy entit a nastavit žádné přidružení sdílené složky přidružení nastavit end.  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [foreign key property](../../../../docs/framework/data/adonet/foreign-key-property.md)

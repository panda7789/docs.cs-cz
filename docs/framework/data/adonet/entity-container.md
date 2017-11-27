---
title: Kontejneru entit
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5ac4383e68aad49af1a65988d9993f6fa018b31a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="entity-container"></a>Kontejneru entit
*Kontejneru entit* je logické seskupení [sad entit](../../../../docs/framework/data/adonet/entity-set.md), [přidružení sady](../../../../docs/framework/data/adonet/association-set.md), a [funkce importy](../../../../docs/framework/data/adonet/model-declared-function.md).  
  
 Následující musí být splněné z kontejner entitu definovanou v konceptuálním modelu:  
  
-   Minimálně jednu entitu kontejneru musí být definován v každé konceptuálním modelu.  
  
-   Kontejneru entit musí mít jedinečný název v rámci každé konceptuálního modelu.  
  
 Kontejner entity můžete definovat sady entit nebo sady přidružení, které používají typy entit a přidružení definované v jedné nebo více oborů názvů. Další informace najdete v tématu [datového modelu Entity: obory názvů](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model se tři typy entit: `Book`, `Publisher`, a `Author`.  Podívejte se na další příklad další informace.  
  
 ![Ukázkový Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 I když diagram špatně přenáší informace o kontejneru entit, musíte definovat konceptuálního modelu kontejner entity. [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá DSL, kterému se říká jazyk definice konceptuálního schématu ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech. Následující CSDL definuje kontejner entity pro koncepční model zobrazený v diagramu výše. Všimněte si, že název kontejneru entit je definována v atribut XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Viz také  
 [Entity Data Model klíčové koncepty](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Datového modelu entity](../../../../docs/framework/data/adonet/entity-data-model.md)

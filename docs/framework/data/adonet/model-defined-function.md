---
title: "model definované funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8e311d6e9c67a30636bdeaea7982057605678684
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="model-defined-function"></a>model definované funkce
A *modelu definované funkce* je funkce, která je definována v konceptuálním modelu. Tělo funkce definované model je vyjádřen v [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), což umožňuje pro funkce, která má být vyjádřena nezávisle na pravidla nebo jazyky podporované v datovém zdroji.  
  
 Definice pro funkci definované model obsahuje následující informace:  
  
-   Název funkce. (Povinné)  
  
-   Typ vrácené hodnoty. (Volitelné)  
  
    > [!NOTE]
    >  Pokud není zadaný žádný návratový typ, je vrácené hodnoty void.  
  
-   Informace o parametrech. (Volitelné)  
  
-   [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) výraz, který definuje tělo funkce.  
  
 Všimněte si, že model definované funkce nepodporuje výstupní parametry. Toto omezení je na místě, aby funkce definované modelu může být složené.  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model se tři typy entit: `Book`, `Publisher`, a `Author`.  
  
 ![Modelu s datum publikování](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech. Následující CSDL definuje funkci v konceptuálním modelu, která vrátí počet let od instance `Book` byla publikována (v diagramu výše).  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a>Viz také  
 [Entity Data Model klíčové koncepty](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Datového modelu entity](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [Datového modelu entity: Primitivní datové typy](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)

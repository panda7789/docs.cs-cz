---
title: "Model Entity Data Model: dědičnosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 421a2bdbf2652880097fb1df3c9b63f38ac2bd10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="entity-data-model-inheritance"></a>Model Entity Data Model: dědičnosti
Entity Data Model (EDM) podporuje dědičnosti pro [typy entit](../../../../docs/framework/data/adonet/entity-type.md). Dědičnost v modelu EDM je podobná dědičnosti pro třídy v objektově orientované programovací jazyky. Jako pomocí třídy v objektově orientovaný jazyků v konceptuálním modelu můžete definovat typ entity ( *odvozeného typu*), dědí z jiného typu entity ( *základní typ*). Ale na rozdíl od třídy v objektově orientované programování v konceptuálním modelu odvozený typ vždy dědí všechny [vlastnosti](../../../../docs/framework/data/adonet/property.md) a [navigační vlastnosti](../../../../docs/framework/data/adonet/navigation-property.md) základního typu. Nejde přepsat zděděné vlastnosti v odvozeném typu.  
  
 Hierarchie dědičnosti, ve kterých odvozený typ dědí z jiné odvozený typ můžete vytvořit v konceptuálním modelu. Typ na nejvyšší úrovni hierarchie (jeden typ v hierarchii, která není typu odvozené) se nazývá *kořenový typ*. V hierarchii dědičnosti [klíč entity](../../../../docs/framework/data/adonet/entity-key.md) v kořenové typ musí být definován.  
  
 Hierarchie dědičnosti, ve kterých odvozený typ dědí z více než jeden typ nelze vytvořit. Například v konceptuálním modelu s `Book` typ entity, můžete definovat odvozené typy `FictionBook` a `NonFictionBook` každý dědit z `Book`. Však nelze definovat pak typ, který dědí z obou `FictionBook` a `NonFictionBook` typy.  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model s čtyři typy entit: `Book`, `FictionBook`, `Publisher`, a `Author`. `FictionBook` Typ entity je odvozený typ, která dědí z `Book` typ entity. `FictionBook` Typ dědí `ISBN (Key)`, `Title`, a `Revision` vlastnosti a definuje další vlastnost s názvem `Genre`.  
  
 ![Dědičnost](../../../../docs/framework/data/adonet/media/inheritanceexample.gif "InheritanceExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech. Následující CSDL definuje typ entity `FictionBook`, který dědí z `Book` typu (jako v diagramu výše):  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)

---
title: "Komplexní typ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6a7fbdace6403d2f1037beff8fe28d7c934d3174
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="complex-type"></a>Komplexní typ
A *komplexní typ* o šablonu pro definování vlastností formátovaných, strukturovaných na [typy entit](../../../../docs/framework/data/adonet/entity-type.md) nebo na jiné komplexní typy. Každá šablona obsahuje následující:  
  
-   Jedinečný název. (Povinné)  
  
    > [!NOTE]
    >  Název pro komplexní typ nemůže být stejný jako název typu entity v rámci stejného oboru názvů.  
  
-   Data ve formě jednoho nebo více [vlastnosti](../../../../docs/framework/data/adonet/property.md). (Volitelné).  
  
    > [!NOTE]
    >  Vlastnost komplexního typu, může být jiná komplexního typu.  
  
 Komplexní typ je podobná typ entity, pro komplexní typ přenášet datovou částí v podobě vlastnosti primitivní typ nebo jiné komplexní typy. Existují však některé hlavní rozdíly mezi typy entit a komplexní typy:  
  
-   Komplexní typy nemají identit a proto nemůže existovat nezávisle. Komplexní typy může existovat pouze jako vlastnosti na typy entit a jiné komplexní typy.  
  
-   Komplexní typy nemůže se podílet na [přidružení](../../../../docs/framework/data/adonet/association-type.md). Ani konec přidružení může být komplexního typu a proto [navigační vlastnosti](../../../../docs/framework/data/adonet/navigation-property.md) nelze definovat na komplexní typy.  
  
## <a name="example"></a>Příklad  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech. Následující CSDL definuje komplexní typ, adresu, s vlastnostmi primitivní typ `StreetAddress`, `City`, `StateOrProvince`, `Country`, a `PostalCode`.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Chcete-li definovat komplexní typ `Address` (nahoře) jako vlastnost na typ entity, je potřeba deklarovat vlastnost typu v definici typu entity. Následující CSDL deklaruje `Address` vlastnost jako komplexní typ. na typ entity (vydavatel):  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)

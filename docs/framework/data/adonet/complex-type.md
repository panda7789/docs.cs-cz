---
title: complex type
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: 9d63660c441192bbc9ecb48bb3a86030b46461cc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160807"
---
# <a name="complex-type"></a>complex type
A *komplexní typ* je šablonu pro definování bohatých a strukturované vlastnosti na [typy entit](../../../../docs/framework/data/adonet/entity-type.md) nebo jiné komplexní typy. Každá šablona obsahuje následující:  
  
-   Jedinečný název. (Povinné)  
  
    > [!NOTE]
    >  Název komplexního typu nemůže být stejný jako název typu entity v rámci stejného oboru názvů.  
  
-   Data ve formě jednoho nebo více [vlastnosti](../../../../docs/framework/data/adonet/property.md). (Volitelné).  
  
    > [!NOTE]
    >  Vlastnost komplexní typ může být jiného komplexního typu.  
  
 Komplexní typ je podobný typ entity, komplexní typ mohou obsahovat datové ve formě vlastnosti primitivní typ nebo jiné komplexní typy. Existují však některé hlavní rozdíly mezi typy entit a komplexní typy:  
  
-   Komplexní typy není identity a proto nemůže existovat nezávisle na sobě. Komplexní typy může existovat pouze jako vlastnosti na typy entit nebo jiné komplexní typy.  
  
-   Komplexní typy se nemůže podílet na [přidružení](../../../../docs/framework/data/adonet/association-type.md). Ani jedna end přidružení může být komplexní typ a proto [navigační vlastnosti](../../../../docs/framework/data/adonet/navigation-property.md) nelze zadat u komplexních typů.  
  
## <a name="example"></a>Příklad  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů. Komplexní typ, adresa, s vlastnostmi primitivní typ definuje následující CSDL `StreetAddress`, `City`, `StateOrProvince`, `Country`, a `PostalCode`.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Chcete-li definovat komplexní typ `Address` (výše) jako vlastnost v typu entity, je třeba deklarovat typ vlastnosti v definici typu entity. Deklaruje následující CSDL `Address` vlastnost jako komplexní typ na typ entity (vydavatel):  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)

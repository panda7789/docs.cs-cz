---
title: complex type
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: 0d9b8efd08cc0dfba5b26a70773b614b0d63d74f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786757"
---
# <a name="complex-type"></a>complex type
*Komplexní typ* je šablona pro definování bohatě strukturovaných vlastností na [typech entit](entity-type.md) nebo na jiných komplexních typech. Každá šablona obsahuje následující:  
  
- Jedinečný název. Požadovanou  
  
    > [!NOTE]
    > Název komplexního typu nemůže být stejný jako název typu entity v rámci stejného oboru názvů.  
  
- Data ve formě jedné nebo více [vlastností](property.md). (Volitelné.)  
  
    > [!NOTE]
    > Vlastnost komplexního typu může být jiný komplexní typ.  
  
 Komplexní typ je podobný jako typ entity v tom, že komplexní typ může mít datovou datovou část ve formě vlastností primitivního typu nebo jiných komplexních typů. Existují však některé klíčové rozdíly mezi komplexními typy a typy entit:  
  
- Komplexní typy nemají identity, a proto nemohou existovat nezávisle. Komplexní typy mohou existovat pouze jako vlastnosti u typů entit nebo jiných komplexních typů.  
  
- Komplexní typy se nemůžou účastnit [přidružení](association-type.md). Ani konec přidružení může být komplexní typ, a proto nelze definovat [vlastnosti navigace](navigation-property.md) pro komplexní typy.  
  
## <a name="example"></a>Příklad  
 [ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](./ef/language-reference/csdl-specification.md)(konceptuální schéma Definition Language). Následující CSDL definuje komplexní typ, adresu `StreetAddress`s vlastnostmi `City` `StateOrProvince` `Country`primitivního typu,,, a `PostalCode`.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Chcete-li definovat komplexní `Address` typ (výše) jako vlastnost typu entity, je nutné deklarovat typ vlastnosti v definici typu entity. Následující CSDL deklaruje `Address` vlastnost jako komplexní typ pro typ entity (Publisher):  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)

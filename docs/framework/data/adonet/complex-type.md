---
title: complex type
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: fac25ace69938e1245200e10285f4460ac216780
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948733"
---
# <a name="complex-type"></a>complex type
*Komplexní typ* je šablona pro definování bohatě strukturovaných vlastností na [typech entit](../../../../docs/framework/data/adonet/entity-type.md) nebo na jiných komplexních typech. Každá šablona obsahuje následující:  
  
- Jedinečný název. Požadovanou  
  
    > [!NOTE]
    > Název komplexního typu nemůže být stejný jako název typu entity v rámci stejného oboru názvů.  
  
- Data ve formě jedné nebo více [vlastností](../../../../docs/framework/data/adonet/property.md). (Volitelné.)  
  
    > [!NOTE]
    > Vlastnost komplexního typu může být jiný komplexní typ.  
  
 Komplexní typ je podobný jako typ entity v tom, že komplexní typ může mít datovou datovou část ve formě vlastností primitivního typu nebo jiných komplexních typů. Existují však některé klíčové rozdíly mezi komplexními typy a typy entit:  
  
- Komplexní typy nemají identity, a proto nemohou existovat nezávisle. Komplexní typy mohou existovat pouze jako vlastnosti u typů entit nebo jiných komplexních typů.  
  
- Komplexní typy se nemůžou účastnit [přidružení](../../../../docs/framework/data/adonet/association-type.md). Ani konec přidružení může být komplexní typ, a proto nelze definovat [vlastnosti navigace](../../../../docs/framework/data/adonet/navigation-property.md) pro komplexní typy.  
  
## <a name="example"></a>Příklad  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)(konceptuální schéma Definition Language). Následující CSDL definuje komplexní typ, adresu `StreetAddress`s vlastnostmi `City` `StateOrProvince` `Country`primitivního typu,,, a `PostalCode`.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Chcete-li definovat komplexní `Address` typ (výše) jako vlastnost typu entity, je nutné deklarovat typ vlastnosti v definici typu entity. Následující CSDL deklaruje `Address` vlastnost jako komplexní typ pro typ entity (Publisher):  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)

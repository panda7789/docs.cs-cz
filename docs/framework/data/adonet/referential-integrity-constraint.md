---
title: referential integrity constraint
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: ad35df7bcca62ffdbc3842b0817b22c5482a3d4d
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738371"
---
# <a name="referential-integrity-constraint"></a>referential integrity constraint
*Omezení referenční integrity* v model EDM (Entity Data Model) (EDM) se podobá omezení referenční integrity v relační databázi. Stejným způsobem, že sloupec (nebo sloupce) z tabulky databáze může odkazovat na primární klíč jiné tabulky, může [vlastnost](property.md) (nebo vlastnosti) [typu entity](entity-type.md) odkazovat na [klíč entity](entity-key.md) jiného typu entity. Odkazovaný typ entity se nazývá *hlavní konec* omezení. Typ entity, který odkazuje na hlavní konec, se nazývá *závislý konec* omezení.  
  
 Omezení referenční integrity je definováno jako součást [přidružení](association-type.md) mezi dvěma typy entit. Definice omezení referenční integrity určuje následující informace:  
  
- Hlavní konec omezení (Typ entity, jejíž klíč entity odkazuje na závislý konec.)  
  
- Klíč entity hlavního elementu end  
  
- Závislý konec omezení (Typ entity, která má vlastnost nebo vlastnosti odkazující na klíč entity hlavního elementu end.)  
  
- Odkazovaná vlastnost nebo vlastnosti závislého elementu end.  
  
 Účelem omezení referenční integrity v modelu EDM je zajistit, aby platná přidružení existovala vždy. Další informace najdete v tématu [vlastnost cizího klíče](foreign-key-property.md).  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje koncepční model se dvěma přidruženími: `WrittenBy` a `PublishedBy`. Typ entity `Book` má vlastnost, `PublisherId`, která odkazuje na klíč entity `Publisher` typu entity, když v přidružení `PublishedBy` definujete omezení referenční integrity.  
  
 ![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "Příklad modelu referenčního omezení")  
  
 [ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language). Následující CSDL definuje omezení referenční integrity u `PublishedBy` přidružení uvedeného v koncepčním modelu výše.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)

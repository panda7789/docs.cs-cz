---
title: referential integrity constraint
description: Seznamte se s omezeními referenční integrity v model EDM (Entity Data Model), která zajistí, aby platná přidružení existovala vždycky mezi typy entit.
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: 65c811b2a12a64870107ff771d5acc64e86f2c1f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286621"
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
 Následující diagram znázorňuje koncepční model se dvěma přidruženími: `WrittenBy` a `PublishedBy` . `Book`Typ entity má vlastnost, `PublisherId` která odkazuje na klíč entity `Publisher` typu entity při definování omezení referenční integrity u `PublishedBy` přidružení.  
  
 ![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "Příklad modelu referenčního omezení")  
  
 [ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language). Následující CSDL definuje omezení referenční integrity u `PublishedBy` přidružení uvedeného výše v koncepčním modelu.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Viz také

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)

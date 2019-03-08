---
title: omezení referenční integrity
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: 7d3304393ef4e97887d9b8afec94ed265e38eaf0
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679109"
---
# <a name="referential-integrity-constraint"></a>omezení referenční integrity
A *omezení referenční integrity* v modelu Entity Data Model (EDM) je podobná omezení referenční integrity v relační databázi. Stejným způsobem, že sloupec (nebo sloupce) z tabulky databáze může odkazovat na primární klíč druhé tabulky a [vlastnost](../../../../docs/framework/data/adonet/property.md) (nebo vlastnosti) ze [typ entity](../../../../docs/framework/data/adonet/entity-type.md) může odkazovat [klíč entity ](../../../../docs/framework/data/adonet/entity-key.md) jiného typu entity. Je volána typ entity, na který odkazuje *hlavní koncový* omezení. Typ entity, která odkazuje na konci instančního objektu je volána *závislé end* omezení.  
  
 Omezení referenční integrity je definován jako součást [přidružení](../../../../docs/framework/data/adonet/association-type.md) mezi dvěma typy entit. Definice pro omezující podmínku referenční integrity určuje následující informace:  
  
-   Hlavní konec omezení. (Typ entity závislé end odkazuje jehož klíč entity.)  
  
-   Klíč entity, která konci instančního objektu.  
  
-   Závislé konec omezení. (Typ entity, který má vlastnost nebo vlastnosti, které odkazují na klíč entity, která konci instančního objektu.)  
  
-   Odkazující vlastnost nebo vlastnosti elementu end závislé.  
  
 Účelem omezení referenční integrity v modelu EDM je zajistit, že platný přidružení vždy existují. Další informace najdete v tématu [vlastnost cizího klíče](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model se dvěma přidružení: `WrittenBy` a `PublishedBy`. `Book` Má vlastnost, typ entity `PublisherId`, která odkazuje na klíč entity, která `Publisher` typ entity při definování omezení referenční integrity na `PublishedBy` přidružení.  
  
 ![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "příklad modelu referenční omezení")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů. Následující CSDL definuje omezení referenční integrity na `PublishedBy` přidružení ukazuje koncepční model uvedený výše.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Viz také:
- [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)

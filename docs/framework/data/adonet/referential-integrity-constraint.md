---
title: omezení referenční integrity
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: a4d63e07da0c75b8a0369933fccfc0cc66fcc40b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="referential-integrity-constraint"></a>omezení referenční integrity
A *omezení referenční integrity* v Entity Data Model (EDM) je podobná omezení referenční integrity v relační databázi. Stejným způsobem, že sloupec (nebo sloupce) z tabulky databáze může odkazovat primární klíč jiné tabulky [vlastnost](../../../../docs/framework/data/adonet/property.md) (nebo vlastnosti) z [typ entity](../../../../docs/framework/data/adonet/entity-type.md) může odkazovat [klíč entity ](../../../../docs/framework/data/adonet/entity-key.md) jiného typu entity. Je volána typ entity, který se odkazuje *hlavní end* omezení. Typ entity, který odkazuje na hlavní end je volána *ukončení závislosti* omezení.  
  
 Omezení referenční integrity je definován jako součást [přidružení](../../../../docs/framework/data/adonet/association-type.md) mezi dvěma typy entit. Definice omezení referenční integrity určuje následující informace:  
  
-   Hlavní konec omezení. (Typ entity jejichž klíč entity odkazuje ukončení závislosti.)  
  
-   Klíč entity hlavní konce.  
  
-   Závislého konce omezení. (Typu entity, který má vlastnost nebo vlastnosti, které klíč entity hlavní konce.)  
  
-   Odkazující vlastnost nebo vlastnosti ukončení závislosti.  
  
 Účelem omezení referenční integrity v modelu EDM je zajistit, vždy existují platný přidružení. Další informace najdete v tématu [vlastností cizího klíče](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model se dvě přidružení: `WrittenBy` a `PublishedBy`. `Book` Typ entity má vlastnosti, `PublisherId`, klíč entity, který odkazuje `Publisher` typ entity, když definujete omezení referenční integrity na `PublishedBy` přidružení.  
  
 ![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech. Následující CSDL definuje omezení referenční integrity na `PublishedBy` přidružení zobrazí v konceptuálním modelu výše.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)

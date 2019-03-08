---
title: Vlastnost cizího klíče
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: 8680019f6f1a53233b5c49163f474cf33409b69b
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674468"
---
# <a name="foreign-key-property"></a>Vlastnost cizího klíče
A *vlastnost cizího klíče* v modelu Entity Data Model (EDM) je primitivního typu [vlastnost](../../../../docs/framework/data/adonet/property.md) (nebo sadu vlastností pro jednoduchý typ) na [typ entity](../../../../docs/framework/data/adonet/entity-type.md) obsahující [klíč entity](../../../../docs/framework/data/adonet/entity-key.md) jiného typu entity.  
  
 Vlastnost cizího klíče je obdobou sloupec cizího klíče v relační databázi. Stejným způsobem, že sloupce cizího klíče se používají v relační databázi k vytváření vztahů mezi řádků v tabulkách, vlastnosti cizího klíče v konceptuálním modelu se používají k navázání [přidružení](../../../../docs/framework/data/adonet/association-type.md) mezi typy entit. A [omezení referenční integrity](../../../../docs/framework/data/adonet/referential-integrity-constraint.md) se používá k definování přidružení mezi dvěma typy entit, pokud jeden z typů má vlastnost cizího klíče.  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model s tři typy entit: `Book`, `Publisher`, a `Author`. `Book` Má vlastnost, typ entity `PublisherId`, která odkazuje na klíč entity, která `Publisher` typ entity při definování omezení referenční integrity na `PublishedBy` přidružení.  
  
 ![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "příklad modelu referenční omezení")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů. Následující CSDL používá vlastnost cizího klíče `PublisherId` k definování omezení referenční integrity na `PublishedBy` přidružení zobrazí v konceptuálním modelu uvedené výše.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Viz také:
- [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)

---
title: foreign key property
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: a77f7479ce38cb34830377021157f312916baca4
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738405"
---
# <a name="foreign-key-property"></a>foreign key property
*Vlastnost cizího klíče* v model EDM (Entity Data Model) (EDM) je [vlastnost](property.md) primitivního typu (nebo sada vlastností primitivního typu) pro [typ entity](entity-type.md) , který obsahuje [klíč entity](entity-key.md) jiného typu entity.  
  
 Vlastnost cizího klíče je analogická jako sloupec cizího klíče v relační databázi. Stejným způsobem, jakým se používají sloupce cizího klíče v relační databázi k vytváření vztahů mezi řádky v tabulkách, se vlastnosti cizích klíčů v koncepčním modelu používají k navázání [přidružení](association-type.md) mezi typy entit. [Omezení referenční integrity](referential-integrity-constraint.md) slouží k definování přidružení mezi dvěma typy entit, pokud jeden z typů má vlastnost cizího klíče.  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje koncepční model se třemi typy entit: `Book`, `Publisher`a `Author`. Typ entity `Book` má vlastnost, `PublisherId`, která odkazuje na klíč entity `Publisher` typu entity, když v přidružení `PublishedBy` definujete omezení referenční integrity.  
  
 ![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Příklad modelu referenčního omezení")  
  
 [ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language). Následující CSDL používá vlastnost cizího klíče `PublisherId` k definování omezení referenční integrity v přidružení `PublishedBy` zobrazeném v koncepčním modelu uvedeném výše.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)

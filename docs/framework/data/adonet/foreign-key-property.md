---
title: foreign key property
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: e2f41c2db9aea26c7954a99ebf3f40b03e8df735
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795038"
---
# <a name="foreign-key-property"></a>foreign key property
*Vlastnost cizího klíče* v model EDM (Entity Data Model) (EDM) je [vlastnost](property.md) primitivního typu (nebo sada vlastností primitivního typu) pro [typ entity](entity-type.md) , který obsahuje [klíč entity](entity-key.md) jiného typu entity.  
  
 Vlastnost cizího klíče je analogická jako sloupec cizího klíče v relační databázi. Stejným způsobem, jakým se používají sloupce cizího klíče v relační databázi k vytváření vztahů mezi řádky v tabulkách, se vlastnosti cizích klíčů v koncepčním modelu používají k navázání [přidružení](association-type.md) mezi typy entit. [Omezení referenční integrity](referential-integrity-constraint.md) slouží k definování přidružení mezi dvěma typy entit, pokud jeden z typů má vlastnost cizího klíče.  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje koncepční model se třemi typy entit: `Book`, `Publisher` `Author`a. Typ entity má vlastnost, `PublisherId`která odkazuje `Publisher` na klíč entity typu entity při definování omezení referenční integrity u `PublishedBy` přidružení. `Book`  
  
 ![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Příklad modelu referenčního omezení")  
  
 [ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](./ef/language-reference/csdl-specification.md)(konceptuální schéma Definition Language). Následující CSDL používá vlastnost `PublisherId` cizího klíče k definování omezení referenční integrity `PublishedBy` u přidružení uvedeného v koncepčním modelu uvedeném výše.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)

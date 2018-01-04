---
title: "vlastností cizího klíče"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 91d06e50a2c64c649ff35352f5b4a41c7417efdf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="foreign-key-property"></a>vlastností cizího klíče
A *vlastností cizího klíče* v Entity Data Model (EDM) je primitivní typ [vlastnost](../../../../docs/framework/data/adonet/property.md) (nebo sadu vlastností primitivní typ) na [typ entity](../../../../docs/framework/data/adonet/entity-type.md) obsahující [klíč entity](../../../../docs/framework/data/adonet/entity-key.md) jiného typu entity.  
  
 Vlastností cizího klíče je podobná sloupec cizího klíče v relační databázi. Stejným způsobem, že sloupce cizího klíče v relační databázi slouží k vytváření vztahů mezi řádků v tabulkách, vlastnosti cizího klíče v konceptuálním modelu se použijí k vytvoření [přidružení](../../../../docs/framework/data/adonet/association-type.md) mezi typy entit. A [omezení referenční integrity](../../../../docs/framework/data/adonet/referential-integrity-constraint.md) se používá k definování přidružení mezi dvěma typy entit, pokud jeden z typů vlastností cizího klíče.  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje Koncepční model se tři typy entit: `Book`, `Publisher`, a `Author`. `Book` Typ entity má vlastnosti, `PublisherId`, klíč entity, který odkazuje `Publisher` typ entity, když definujete omezení referenční integrity na `PublishedBy` přidružení.  
  
 ![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech. Následující CSDL používá vlastností cizího klíče `PublisherId` definovat omezení referenční integrity na `PublishedBy` přidružení zobrazí v konceptuálním modelu uvedené výše.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)

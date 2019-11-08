---
title: 'Model EDM (Entity Data Model): dědičnost'
ms.date: 03/30/2017
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
ms.openlocfilehash: 4c4abc371000006d40ede3d904b0437f3f85e3e7
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738448"
---
# <a name="entity-data-model-inheritance"></a>Model EDM (Entity Data Model): dědičnost
Model EDM (Entity Data Model) (EDM) podporuje dědičnost pro [typy entit](entity-type.md). Dědičnost v EDM je podobná dědičnosti pro třídy v objektově orientovaném programovacím jazyce. Podobně jako u tříd v objektově orientovaném jazyce, v koncepčním modelu můžete definovat typ entity ( *odvozený typ*), který dědí z jiného typu entity ( *základní typ*). Nicméně na rozdíl od tříd v objektově orientovaném programování, v koncepčním modelu odvozený typ vždy zdědí všechny [vlastnosti](property.md) a [navigační vlastnosti](navigation-property.md) základního typu. Zděděné vlastnosti nelze přepsat v odvozeném typu.  
  
 V koncepčním modelu můžete vytvořit Hierarchie dědičnosti, ve kterých je odvozený typ děděn z jiného odvozeného typu. Typ v horní části hierarchie (jeden typ v hierarchii, který není odvozeným typem) se označuje jako *Kořenový typ*. V hierarchii dědičnosti musí být [klíč entity](entity-key.md) definován u kořenového typu.  
  
 Nelze vytvořit Hierarchie dědičnosti, ve kterých je odvozený typ děděn z více než jednoho typu. Například v koncepčním modelu s typem entity `Book` můžete definovat odvozené typy `FictionBook` a `NonFictionBook`, které jednotlivé dědí z `Book`. Nicméně nelze definovat typ, který dědí z typu `FictionBook` i `NonFictionBook`.  
  
## <a name="example"></a>Příklad  

Následující diagram znázorňuje koncepční model se čtyřmi typy entit: `Book`, `FictionBook`, `Publisher`a `Author`. Typ entity `FictionBook` je odvozený typ, který dědí z `Book` typu entity. Typ `FictionBook` dědí vlastnosti `ISBN (Key)`, `Title`a `Revision` a definuje další vlastnost s názvem `Genre`.  
  
 ![Diagram znázorňující koncepční model se čtyřmi typy entit.](./media/entity-data-model-inheritance/entity-type-inheritance.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language). Následující CSDL definuje typ entity, `FictionBook`, který dědí z typu `Book` (jako v diagramu výše):  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)

---
title: Model EDM (Entity Data Model) Dědičnost
ms.date: 03/30/2017
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
ms.openlocfilehash: 21dbdff63c07dbcdac8de7bf4b3a8e5d0ece7901
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784079"
---
# <a name="entity-data-model-inheritance"></a>Model EDM (Entity Data Model) Dědičnost
Model EDM (Entity Data Model) (EDM) podporuje dědičnost pro [typy entit](entity-type.md). Dědičnost v EDM je podobná dědičnosti pro třídy v objektově orientovaném programovacím jazyce. Podobně jako u tříd v objektově orientovaném jazyce, v koncepčním modelu můžete definovat typ entity ( *odvozený typ*), který dědí z jiného typu entity ( *základní typ*). Nicméně na rozdíl od tříd v objektově orientovaném programování, v koncepčním modelu odvozený typ vždy zdědí všechny [vlastnosti](property.md) a [navigační vlastnosti](navigation-property.md) základního typu. Zděděné vlastnosti nelze přepsat v odvozeném typu.  
  
 V koncepčním modelu můžete vytvořit Hierarchie dědičnosti, ve kterých je odvozený typ děděn z jiného odvozeného typu. Typ v horní části hierarchie (jeden typ v hierarchii, který není odvozeným typem) se označuje jako *Kořenový typ*. V hierarchii dědičnosti musí být [klíč entity](entity-key.md) definován u kořenového typu.  
  
 Nelze vytvořit Hierarchie dědičnosti, ve kterých je odvozený typ děděn z více než jednoho typu. `Book` Například v koncepčním modelu s typem entity můžete definovat odvozené typy `FictionBook` a `NonFictionBook` všechny z `Book`nich dědí. Nicméně nelze definovat typ, který dědí z obou `FictionBook` typů a. `NonFictionBook`  
  
## <a name="example"></a>Příklad  

Následující diagram znázorňuje koncepční model se čtyřmi typy entit `Book`:, `FictionBook`, `Publisher` `Author`a. Typ entity je odvozený typ, který dědí `Book` z typu entity. `FictionBook` `FictionBook` Typ `Genre`dědí vlastnosti ,`Title` a`Revision` a definuje další vlastnost s názvem. `ISBN (Key)`  
  
 ![Diagram znázorňující koncepční model se čtyřmi typy entit.](./media/entity-data-model-inheritance/entity-type-inheritance.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](./ef/language-reference/csdl-specification.md)(konceptuální schéma Definition Language). Následující CSDL definuje typ `FictionBook`entity,, který dědí `Book` z typu (jako v diagramu výše):  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)

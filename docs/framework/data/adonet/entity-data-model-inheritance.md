---
title: Model EDM (Entity Data Model) Dědičnost
ms.date: 03/30/2017
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
ms.openlocfilehash: 9f77f2ebb86ea050c124fbd1c6f2b30ed9e75a1c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083813"
---
# <a name="entity-data-model-inheritance"></a>Model EDM (Entity Data Model) Dědičnost
Entity Data Model (EDM) podporuje dědičnost [typy entit](../../../../docs/framework/data/adonet/entity-type.md). Dědičnost v modelu EDM je podobný dědičnosti tříd v objektově orientované programovací jazyky. Jako s třídami v objektově orientované jazyků v konceptuálním modelu můžete definovat typ entity ( *odvozeného typu*), která dědí z jiného typu entity ( *základní typ*). Ale na rozdíl od tříd v objektově orientované programování v konceptuálním modelu odvozený typ vždy zdědí všechny [vlastnosti](../../../../docs/framework/data/adonet/property.md) a [navigační vlastnosti](../../../../docs/framework/data/adonet/navigation-property.md) základního typu. Nelze přepsat zděděné vlastnosti v odvozeném typu.  
  
 V konceptuálním modelu můžete vytvořit hierarchie dědičnosti, ve kterých odvozený typ dědí z jiného odvozeného typu. Typ v horní části hierarchie (jeden typ v hierarchii, která není odvozeným typem) se nazývá *kořenový typ*. V hierarchii dědičnosti [klíč entity](../../../../docs/framework/data/adonet/entity-key.md) na kořenový typ musí být definován.  
  
 Hierarchie dědičnosti, ve kterých odvozený typ dědí z více než jeden typ nelze vytvořit. Například v konceptuálním modelu s `Book` typ entity, můžete definovat odvozené typy `FictionBook` a `NonFictionBook` každý dědit z `Book`. Však nelze definovat poté typ, který zdědí vlastnosti z obou `FictionBook` a `NonFictionBook` typy.  
  
## <a name="example"></a>Příklad  

Následující diagram znázorňuje Koncepční model, čtyři typy entit: `Book`, `FictionBook`, `Publisher`, a `Author`. `FictionBook` Entity typu je odvozený typ dědí `Book` typu entity. `FictionBook` Typ dědí `ISBN (Key)`, `Title`, a `Revision` vlastnosti a definuje další vlastnosti s názvem `Genre`.  
  
 ![Diagram zobrazující průběh konceptuální model, čtyři typy entit.](./media/entity-data-model-inheritance/entity-type-inheritance.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů. Následující CSDL definuje typ entity, `FictionBook`, které dědí z `Book` typu (stejně jako v diagramu výše):  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)

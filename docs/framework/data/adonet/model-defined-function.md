---
title: model-defined function
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 973d7ff9f7b76650782d62dcdcab60c8cedde18f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735574"
---
# <a name="model-defined-function"></a>model-defined function
*Funkce definovaná modelem* je funkce, která je definována v koncepčním modelu. Tělo funkce definované modelem je vyjádřeno v [Entity SQL](./ef/language-reference/entity-sql-language.md), což umožňuje, aby byla funkce vyjádřena nezávisle na pravidlech nebo jazycích podporovaných ve zdroji dat.  
  
 Definice funkce definované modelem obsahuje následující informace:  
  
- Název funkce. Požadovanou  
  
- Typ návratové hodnoty. Volitelné  
  
    > [!NOTE]
    > Pokud není zadán žádný návratový typ, návratová hodnota je void.  
  
- Informace o parametrech. Volitelné  
  
- Výraz [Entity SQL](./ef/language-reference/entity-sql-language.md) definující tělo funkce.  
  
 Všimněte si, že funkce definované modelem nepodporují výstupní parametry. Toto omezení je nastaveno tak, aby bylo možné sestavit funkce definované modelem.  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje koncepční model se třemi typy entit: `Book`, `Publisher`a `Author`.  
  
 ![Snímek obrazovky, který zobrazuje model s datem publikování](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language). Následující CSDL definuje funkci v koncepčním modelu, která vrací počet roků od chvíle, kdy byla publikována instance `Book` (v diagramu výše).  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)
- [Model EDM (Entity Data Model): Primitivní datové typy](entity-data-model-primitive-data-types.md)

---
title: model-defined function
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 05a44e86a118b649490cde849c8ca2c2bb0d2f15
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934524"
---
# <a name="model-defined-function"></a>model-defined function
*Funkce definovaná modelem* je funkce, která je definována v koncepčním modelu. Tělo funkce definované modelem je vyjádřeno v [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), což umožňuje, aby byla funkce vyjádřena nezávisle na pravidlech nebo jazycích podporovaných ve zdroji dat.  
  
 Definice funkce definované modelem obsahuje následující informace:  
  
- Název funkce. Požadovanou  
  
- Typ návratové hodnoty. Volitelné  
  
    > [!NOTE]
    > Pokud není zadán žádný návratový typ, návratová hodnota je void.  
  
- Informace o parametrech. Volitelné  
  
- Výraz [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) definující tělo funkce.  
  
 Všimněte si, že funkce definované modelem nepodporují výstupní parametry. Toto omezení je nastaveno tak, aby bylo možné sestavit funkce definované modelem.  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje koncepční model se třemi typy entit: `Book`, `Publisher` `Author`a.  
  
 ![Snímek obrazovky, který zobrazuje model s datem publikování](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)(konceptuální schéma Definition Language). Následující CSDL definuje funkci v koncepčním modelu, která vrací počet roků od okamžiku, kdy byla publikována instance `Book` (v diagramu výše).  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)
- [Model EDM (Entity Data Model): Primitivní datové typy](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)

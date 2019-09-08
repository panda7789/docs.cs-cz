---
title: model-declared function
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: cb2fca52604bd57f25469f5621c292a27638c76f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794795"
---
# <a name="model-declared-function"></a>model-declared function
*Modelem deklarovaná funkce* je funkce, která je deklarována v koncepčním modelu, ale není definována v tomto koncepčním modelu. Funkce může být definována v prostředí hostování nebo úložiště. Například funkce deklarovaná modelem může být mapována na funkci, která je definována v databázi, čímž vystavuje funkce na straně serveru v koncepčním modelu.  
  
 Deklarace funkce deklarované modelem obsahuje následující informace:  
  
- Název funkce Požadovanou  
  
- Typ návratové hodnoty. Volitelné  
  
    > [!NOTE]
    > Pokud není zadána žádná návratová hodnota, návratový typ je void.  
  
- Informace o parametrech, včetně názvu a typu parametru. Volitelné  
  
## <a name="example"></a>Příklad  
 [ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů jazyk specifický pro doménu (DSL), který se nazývá jazyk[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(konceptuální schéma Definition Language). V CSDL jedna implementace modelem deklarované funkce je importovaná funkce (pomocí [elementu FunctionImport](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)). Následující CSDL definuje kontejner entit s definicí importu funkce. Všimněte si, že návratový typ pro funkci je void, protože není zadaný žádný návratový typ.  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)

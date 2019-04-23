---
title: model-declared function
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: c9abf9a3340cd22ab5d654588b1d22e10b5c05fa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130543"
---
# <a name="model-declared-function"></a>model-declared function
A *modelu deklarované funkce* je funkce, která je deklarována v konceptuálním modelu, ale není definovaný v tomto koncepčního modelu. Funkce mohou být definovány v prostředí hostování nebo úložiště. Funkce deklarované modelu může například namapovat na funkce, která je definována v databázi tak vystavení funkce na straně serveru v konceptuálním modelu.  
  
 Deklarace funkce deklarované model obsahuje následující informace:  
  
-   Název funkce. (Povinné)  
  
-   Typ vrácené hodnoty. (Volitelné)  
  
    > [!NOTE]
    >  Pokud není zadána žádná návratová hodnota, je návratový typ void.  
  
-   Informace o parametrech, včetně názvu parametru a typu. (Volitelné)  
  
## <a name="example"></a>Příklad  
 [ADO.NET Entity Framework](./ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) k definování konceptuálních modelů. V CSDL, je jedna implementace funkce deklarované modelu importovanou funkci (pomocí [FunctionImport element](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)). Následující CSDL definuje kontejneru entity s definicí funkce importu. Všimněte si, že návratový typ pro funkci je neplatný, protože není zadán žádný návratový typ.  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)

---
title: funkce deklarované modelu
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: 5db7d49fd4b839cef47db8086b4ef39ce4dc6aea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725139"
---
# <a name="model-declared-function"></a>funkce deklarované modelu
A *modelu deklarované funkce* je funkce, která je deklarována v konceptuálním modelu, ale není definovaný v tomto koncepčního modelu. Funkce mohou být definovány v prostředí hostování nebo úložiště. Funkce deklarované modelu může například namapovat na funkce, která je definována v databázi tak vystavení funkce na straně serveru v konceptuálním modelu.  
  
 Deklarace funkce deklarované model obsahuje následující informace:  
  
-   Název funkce. (Povinné)  
  
-   Typ vrácené hodnoty. (Volitelné)  
  
    > [!NOTE]
    >  Pokud není zadána žádná návratová hodnota, je návratový typ void.  
  
-   Informace o parametrech, včetně názvu parametru a typu. (Volitelné)  
  
## <a name="example"></a>Příklad  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá jazyka specifického pro doménu (DSL) volá Konceptuální schéma definici jazyka ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelů. V CSDL, je jedna implementace modelu deklarovaná funkce [funkce import](https://msdn.microsoft.com/library/125704ae-56c7-4233-80b7-389a10f3a65d). Následující CSDL definuje kontejneru entity s definicí funkce importu. Všimněte si, že návratový typ pro funkci je neplatný, protože není zadán žádný návratový typ.  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a>Viz také:
- [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)

---
title: entity container
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: 95740fb9d8b357a4fa160af6fdafb139711283cd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795253"
---
# <a name="entity-container"></a>entity container
*Kontejner entit* je logické seskupení [sad entit](entity-set.md), [sad přidružení](association-set.md)a [importů funkcí](model-declared-function.md).  
  
 Následující hodnota musí být true kontejneru entity definovaného v koncepčním modelu:  
  
- V každém koncepčním modelu musí být definován alespoň jeden kontejner entit.  
  
- Kontejner entity musí mít jedinečný název v rámci každého koncepčního modelu.  
  
 Kontejner entit může definovat sady entit nebo sady přidružení, které používají typy entit nebo přidružení definované v jednom nebo více oborech názvů. Další informace najdete v tématu [model EDM (Entity Data Model): Obory názvů](entity-data-model-namespaces.md).  
  
## <a name="example"></a>Příklad  
 Následující diagram znázorňuje koncepční model se třemi typy entit: `Book`, `Publisher` `Author`a.  Další informace najdete v dalším příkladu.  
  
 ![Vzorový model se třemi typy entit](./media/entity-container/example-model-three-entity-types.gif)  
  
 I když diagram nevyjadřuje informace o kontejneru entit, koncepční model musí definovat kontejner entit. [ADO.NET Entity Framework](./ef/index.md) používá pro definování konceptuálních modelů DSL označované jako konceptuální schéma Definition Language ([CSDL](./ef/language-reference/csdl-specification.md)). Následující CSDL definuje kontejner entit pro koncepční model zobrazený v diagramu výše. Všimněte si, že název kontejneru entity je definován v atributu XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)
- [Model EDM (Entity Data Model)](entity-data-model.md)

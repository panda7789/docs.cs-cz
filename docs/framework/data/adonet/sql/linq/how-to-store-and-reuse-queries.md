---
title: 'Postupy: Uložení a opakované použití dotazů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a012bd79-1809-45e3-adea-0229532396cc
ms.openlocfilehash: f8400b214bc9ba3a28eeec05f6171953b42bc6f5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938748"
---
# <a name="how-to-store-and-reuse-queries"></a>Postupy: Uložení a opakované použití dotazů
V případě, že máte aplikaci, která spouští strukturální podobné dotazy mnohokrát, můžete často zvýšit výkon kompilováním dotazu jednou a jeho spuštěním několikrát s různými parametry. Aplikace může například potřebovat načíst všechny zákazníky, kteří jsou v určitém městě, kde město je určeno za běhu uživatelem ve formuláři. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje použití zkompilovaných *dotazů* pro tento účel.  
  
> [!NOTE]
> Tento vzor použití představuje nejběžnější použití kompilovaných dotazů. Další přístupy jsou možné. Například zkompilované dotazy mohou být uloženy jako statické členy v částečné třídě, která rozšiřuje kód generovaný návrhářem.  
  
## <a name="example"></a>Příklad  
 V mnoha scénářích možná budete chtít znovu použít dotazy napříč hranicemi vlákna. V takových případech je ukládání kompilovaných dotazů do statických proměnných obzvláště efektivní. Následující příklad kódu předpokládá `Queries` třídu navrženou pro ukládání kompilovaných dotazů a předpokládá třídu Northwind, která představuje silného typu. <xref:System.Data.Linq.DataContext>  
  
 [!code-csharp[DLinqQuerying#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#6)]
 [!code-vb[DLinqQuerying#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#6)]  
  
 [!code-csharp[DLinqQuerying#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#7)]
 [!code-vb[DLinqQuerying#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#7)]  
  
## <a name="example"></a>Příklad  
 Aktuálně nemůžete ukládat (v statických proměnných) dotazy, které vracejí *anonymní typ*, protože typ nemá žádný název, který by měl poskytnout jako obecný argument. Následující příklad ukazuje, jak lze problém obejít vytvořením typu, který může představovat výsledek, a poté jej použít jako obecný argument.  
  
 [!code-csharp[DLinqQuerying#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#8)]
 [!code-vb[DLinqQuerying#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#8)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.Linq.CompiledQuery>
- [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Dotazování na databázi](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)

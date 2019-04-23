---
title: 'Postupy: Vytvoření domény aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff85f5737babb73d87f4918ca0f4981263f7dadc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166748"
---
# <a name="how-to-create-an-application-domain"></a>Postupy: Vytvoření domény aplikace
Hostitel common language runtime automaticky vytvoří aplikační domény v případě potřeby. Můžete však vytvořit vlastní domény aplikace a načíst do nich tato sestavení, které chcete spravovat sami. Můžete také vytvořit aplikační domény, ze kterých je kód spuštěn.  
  
 Vytvořit novou doménu aplikace pomocí jedné z přetížené **CreateDomain** metody v <xref:System.AppDomain?displayProperty=nameWithType> třídy. Můžete pojmenujte doménu aplikace a na něj odkazovat s tímto názvem.  
  
 Následující příklad vytvoří novou doménu aplikace, přiřadí název `MyDomain`a potom vypíše název domény hostitele a nově vytvořený podřízené domény aplikace do konzoly.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Programování pomocí domén aplikace](application-domains.md#programming-with-application-domains)
- [Používání domén aplikací](../../../docs/framework/app-domains/use.md)

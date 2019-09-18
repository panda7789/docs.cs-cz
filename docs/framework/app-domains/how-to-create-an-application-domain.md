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
ms.openlocfilehash: 7f42f85adf3e9b0874df6c0360bea25b07facc0d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053149"
---
# <a name="how-to-create-an-application-domain"></a>Postupy: Vytvoření domény aplikace
Hostitel společného jazykového modulu runtime vytváří domény aplikace automaticky v případě potřeby. Můžete však vytvořit vlastní domény aplikace a načíst je do těchto sestavení, která chcete spravovat osobně. Můžete také vytvořit domény aplikace, ze kterých můžete spustit kód.  
  
 Novou doménu aplikace vytvoříte pomocí jedné z přetížených metod **CreateDomain –** ve <xref:System.AppDomain?displayProperty=nameWithType> třídě. Doméně aplikace můžete přidělit název a odkazovat na ni tímto názvem.  
  
 Následující příklad vytvoří novou doménu aplikace, přiřadí jí název `MyDomain`a potom vypíše název domény hostitele a nově vytvořenou podřízenou doménu aplikace do konzoly.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Programování s aplikačními doménami](application-domains.md#programming-with-application-domains)
- [Používání domén aplikací](use.md)

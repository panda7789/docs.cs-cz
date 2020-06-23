---
title: 'Postupy: Vytvoření domény aplikace'
description: Přečtěte si, jak vytvořit doménu aplikace v rozhraní .NET. Můžete vytvořit doménu aplikace pro načtení sestavení pro správu osobně nebo vytvořit kód pro spuštění kódu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
ms.openlocfilehash: 8e44e682f64854dbc0181b26f6ed3fa2905b7814
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104810"
---
# <a name="how-to-create-an-application-domain"></a>Postupy: Vytvoření domény aplikace
Hostitel společného jazykového modulu runtime vytváří domény aplikace automaticky v případě potřeby. Můžete však vytvořit vlastní domény aplikace a načíst je do těchto sestavení, která chcete spravovat osobně. Můžete také vytvořit domény aplikace, ze kterých můžete spustit kód.  
  
 Novou doménu aplikace vytvoříte pomocí jedné z přetížených metod **CreateDomain –** ve <xref:System.AppDomain?displayProperty=nameWithType> třídě. Doméně aplikace můžete přidělit název a odkazovat na ni tímto názvem.  
  
 Následující příklad vytvoří novou doménu aplikace, přiřadí jí název `MyDomain` a potom vypíše název domény hostitele a nově vytvořenou podřízenou doménu aplikace do konzoly.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také

- [Programování s aplikačními doménami](application-domains.md#programming-with-application-domains)
- [Používání domén aplikací](use.md)

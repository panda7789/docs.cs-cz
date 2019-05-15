---
title: 'Postupy: Používání časových pásem v aritmetice kalendářních a časových údajů'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], adding and subtracting
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d504aa9ad7d6e4084192a2434ac408e8fa7a041
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588537"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a>Postupy: Používání časových pásem v aritmetice kalendářních a časových údajů

Obvykle při provádění datum a čas aritmetické pomocí <xref:System.DateTime> nebo <xref:System.DateTimeOffset> hodnot, výsledek neodráží všechna pravidla úpravy časového pásma. To platí i v případě, časovém pásmu z hodnoty data a času je jasně údaje (například když <xref:System.DateTime.Kind%2A> je nastavena na <xref:System.DateTimeKind.Local>). Toto téma ukazuje, jak provádět aritmetické operace na hodnoty data a času, které patří do určitého časového pásma. Výsledky aritmetické operace bude odrážet pravidla úpravy časového pásma.

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a>Použít pravidla úpravy aritmetika data a času

1. Implementujte některé metody, které úzce párování hodnoty data a času s časovým pásmem, do které patří. Například definice struktury, která obsahuje datum a čas a její časové pásmo. Následující příklad používá tento přístup k propojení <xref:System.DateTime> hodnotu s časovým pásmem.

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. Převod času na koordinovaný univerzální čas (UTC) pomocí volání buď <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> metoda nebo <xref:System.TimeZoneInfo.ConvertTime%2A> metody.

3. Proveďte aritmetickou operaci na čas UTC.

4. Převést čas od času UTC na časové pásmo přidružené původní čas voláním <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metody.

## <a name="example"></a>Příklad

Následující příklad přidá dvě hodiny a 30 minut do 9. března 2008 v 1:30 hod Střední (běžný čas). Časové pásmo přechodu na letní čas dojde později, 30 minut ve 2:00:00 9. března, 2008. Protože příklad následující čtyři kroky uvedené v předchozí části, správně hlásí ve výsledné dobu 5:00:00. 9. března, 2008.

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

Obě <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty nejsou přidruženy k libovolné časové pásmo, do kterého může patřit. Pokud chcete provést tak, aby automaticky použije pravidla úpravy časového pásma aritmetika data a času, musí být časové pásmo, do které žádné datum a čas, hodnotu patří okamžitě identifikovatelné. To znamená, že datum a čas a její přidružené časového pásma musí být úzce spojeny. Existuje několik způsobů, jak to provést, mezi které patří následující:

* Předpokládejme, že, která se použijí všechny časy v aplikaci patří konkrétní časové pásmo. I když v některých případech je vhodné, tento přístup nabízí omezené flexibilitu a přenositelnost může být omezená.

* Definice typu, který úzce spojuje datum a čas s časovým pásmem jeho přidružené zahrnutím i jako pole typu. Tento přístup se používá v příkladu kódu, který definuje strukturu ukládat data a času a časového pásma ve dvou polích člena.

Příklad ukazuje, jak k provádění aritmetických operací na <xref:System.DateTime> hodnoty tak, aby na výsledek jsou použita pravidla úpravy časového pásma. Ale <xref:System.DateTimeOffset> hodnoty můžete použít stejně snadno. Následující příklad ukazuje, jak může kód v původním příkladu je adaptovat k použití <xref:System.DateTimeOffset> místo <xref:System.DateTime> hodnoty.

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

Všimněte si, že pokud je toto přidání je jednoduše provedeno na <xref:System.DateTimeOffset> hodnoty bez nejprve převodu na čas UTC, výsledek odráží správného bodu v čase, ale její posun toto nereflektuje určeného časového pásma.

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

* Že <xref:System> obor názvů je importovat s `using` – příkaz (vyžadováno za kód jazyka C#).

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Provádění aritmetických operací s daty a časy](../../../docs/standard/datetime/performing-arithmetic-operations.md)

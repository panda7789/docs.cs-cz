---
title: 'Postupy: používání časových pásem datum a čas aritmetické'
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
ms.openlocfilehash: 9f9d326750cdef96be1aa6055d46b4ac08ec7a0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a>Postupy: používání časových pásem datum a čas aritmetické

Normálně, když provést datum a čas aritmetické pomocí <xref:System.DateTime> nebo <xref:System.DateTimeOffset> hodnoty, výsledek nezohledňuje všechna pravidla pro úpravu časové pásmo. To platí i v případě, na časové pásmo hodnoty data a času je jasně identifikovatelné (například když <xref:System.DateTime.Kind%2A> je nastavena na <xref:System.DateTimeKind.Local>). Toto téma ukazuje, jak provádět aritmetické operace na hodnoty data a času, které patří do určitého časového pásma. Výsledky aritmetické operace bude odrážet pravidla úpravy časového pásma.

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a>Chcete-li použít pravidla úpravy datum a čas aritmetické

1. Implementujte některé metody úzce spojovacích hodnota data a času s časovým pásmem, do které patří. Například deklarujte strukturu, která obsahuje datum a čas hodnota a její časové pásmo. Následující příklad používá tento přístup k propojení <xref:System.DateTime> hodnotu s časovým pásmem.

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. Převést čas koordinovaný světový čas (UTC) voláním buď <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> metoda nebo <xref:System.TimeZoneInfo.ConvertTime%2A> metoda.

3. Provádění aritmetických operací na čas UTC.

4. Převést čas od času UTC na původní čas přidružené časové pásmo voláním <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metoda.

## <a name="example"></a>Příklad

Následující příklad přidá dvě hodiny a 30 minut do 9. března 2008 v 1:30 hodin Centrální běžný čas. Časové pásmo přechodu na letní čas dojde později, 30 minut ve 2:00 9. března 2008. Vzhledem k tomu, že v příkladu zahrnuje čtyři kroky uvedené v předchozí části, správně hlásí výsledný čas jako 05:00. 9. března 2008.

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

Obě <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty nejsou přidruženy k žádné časové pásmo, ke kterému můžou patřit. Pokud chcete provést datum a čas aritmetické způsobem, který automaticky použije pravidla úpravy časového pásma, musí být časové pásmo, které žádné datum a čas patří hodnota okamžitě identifikovatelné. To znamená, že datum a čas a jeho přidružené časové pásmo musí být úzce párované. Existuje několik způsobů, jak to provést, které zahrnují následující:

* Předpokládejme, že všechny časy použité v aplikaci patří do určitého časového pásma. I když je vhodné v některých případech, tento postup nabízí omezenou flexibilitu a případně i omezenou přenositelnost.

* Zadejte typ, který spojuje úzce datum a čas s jeho přidružené časové pásmo zahrnutím i pole typu. Tento postup se používá v příkladu kódu, který definuje strukturu pro uložení datum a čas a časové pásmo ve dvou polích člen.

Příklad ukazuje, jak provádět aritmetické operace na <xref:System.DateTime> hodnoty tak, aby na výsledek použita pravidla úpravy časového pásma. Ale <xref:System.DateTimeOffset> hodnoty lze použít stejným způsobem. Následující příklad ilustruje, jak může být přizpůsobena použít kód v původní ukázce <xref:System.DateTimeOffset> místo <xref:System.DateTime> hodnoty.

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

Všimněte si, že Pokud Přidání provádí jednoduše na <xref:System.DateTimeOffset> hodnotu bez první převodu na čas UTC, výsledek odráží konkrétní bod v čase, ale její posun toto nereflektuje určené časového pásma.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Tento příklad vyžaduje:

* Aby byl přidán odkaz na System.Core.dll do projektu.

* Zda <xref:System> importovat obor názvů s `using` (povinné v kódu jazyka C#).

## <a name="see-also"></a>Viz také

[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[provádění aritmetických operací s daty a časy](../../../docs/standard/datetime/performing-arithmetic-operations.md)

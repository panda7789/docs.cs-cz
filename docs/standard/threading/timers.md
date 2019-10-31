---
title: Časovače
description: Zjistěte, jaké časovače rozhraní .NET se mají použít ve vícevláknovém prostředí.
ms.date: 07/03/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
author: pkulikov
ms.openlocfilehash: d7d1fa13b02fe7425fa9b4cb81ba20297a23fe4b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128953"
---
# <a name="timers"></a>Časovače

.NET poskytuje dva časovače pro použití v prostředí s více vlákny:

- <xref:System.Threading.Timer?displayProperty=nameWithType>, která spouští jednu metodu zpětného volání v <xref:System.Threading.ThreadPool> vlákně v pravidelných intervalech.
- <xref:System.Timers.Timer?displayProperty=nameWithType>, který ve výchozím nastavení vyvolá událost v <xref:System.Threading.ThreadPool> vlákně v pravidelných intervalech.

> [!NOTE]
> Některé implementace rozhraní .NET můžou zahrnovat další časovače:
>
> - <xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: model Windows Forms komponenta, která aktivuje událost v pravidelných intervalech. Komponenta nemá žádné uživatelské rozhraní a je určena pro použití v prostředí s jedním vláknem.  
> - <xref:System.Web.UI.Timer?displayProperty=nameWithType>: komponenta ASP.NET, která provádí asynchronní nebo synchronní zpětné volání webové stránky v pravidelných intervalech.
> - <xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: časovač, který je integrovaný do fronty <xref:System.Windows.Threading.Dispatcher>, která se zpracovává v zadaném časovém intervalu a v zadané prioritě.

## <a name="the-systemthreadingtimer-class"></a>Třída System. Threading. Timer

Třída <xref:System.Threading.Timer?displayProperty=nameWithType> umožňuje nepřetržitě volat delegáta v zadaných časových intervalech. Tuto třídu můžete použít také k naplánování jednoho volání delegáta v zadaném časovém intervalu. Delegát je spuštěn ve vlákně <xref:System.Threading.ThreadPool>.

Při vytváření objektu <xref:System.Threading.Timer?displayProperty=nameWithType> zadáte delegáta <xref:System.Threading.TimerCallback>, který definuje metodu zpětného volání, objekt volitelného stavu, který je předán zpětnému volání, čas zpoždění před prvním voláním zpětného volání a časový interval mezi vyvolání zpětného volání. Chcete-li zrušit probíhající časovač, zavolejte metodu <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType>.

Následující příklad vytvoří časovač, který volá poskytnutého delegáta poprvé po jedné sekundě (1000 milisekund) a pak je zavolá každé dvě sekundy. Objekt State v příkladu slouží ke zjištění, kolikrát je volán delegát. Časovač se zastaví, pokud byl delegát volán nejméně desetkrát.

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

Další informace a příklady naleznete v tématu <xref:System.Threading.Timer?displayProperty=nameWithType>.

## <a name="the-systemtimerstimer-class"></a>Třída System. Timers. Timer

Další časovač, který lze použít v prostředí s více vlákny, je <xref:System.Timers.Timer?displayProperty=nameWithType>, že ve výchozím nastavení vyvolá událost ve <xref:System.Threading.ThreadPool> vlákně.

Při vytváření objektu <xref:System.Timers.Timer?displayProperty=nameWithType> můžete zadat časový interval, ve kterém se má vyvolat událost <xref:System.Timers.Timer.Elapsed>. Vlastnost <xref:System.Timers.Timer.Enabled%2A> použijte k označení, zda má časovač vyvolat událost <xref:System.Timers.Timer.Elapsed>. Pokud potřebujete událost <xref:System.Timers.Timer.Elapsed> vyvolat pouze jednou po uplynutí zadaného intervalu, nastavte <xref:System.Timers.Timer.AutoReset%2A> na `false`. Výchozí hodnota vlastnosti <xref:System.Timers.Timer.AutoReset%2A> je `true`, což znamená, že se událost <xref:System.Timers.Timer.Elapsed> generuje pravidelně v intervalu definovaném vlastností <xref:System.Timers.Timer.Interval%2A>.

Další informace a příklady naleznete v tématu <xref:System.Timers.Timer?displayProperty=nameWithType>.
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [Funkce a objekty dělení na vlákna](threading-objects-and-features.md)

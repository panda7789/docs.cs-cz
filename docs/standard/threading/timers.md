---
title: Časovače
description: Zjistěte, co se mají používat časovače rozhraní .NET v prostředí s více vlákny.
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73128953"
---
# <a name="timers"></a>Časovače

Rozhraní .NET poskytuje dva časovače pro použití v prostředí s více vlákny:

- <xref:System.Threading.Timer?displayProperty=nameWithType>, který v pravidelných intervalech <xref:System.Threading.ThreadPool> provede jednu metodu zpětného volání ve vlákně.
- <xref:System.Timers.Timer?displayProperty=nameWithType>, který ve výchozím nastavení <xref:System.Threading.ThreadPool> vyvolá událost ve vlákně v pravidelných intervalech.

> [!NOTE]
> Některé implementace rozhraní .NET mohou obsahovat další časovače:
>
> - <xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: součást Windows Forms, která v pravidelných intervalech aktivuje událost. Komponenta nemá žádné uživatelské rozhraní a je určena pro použití v prostředí s jedním podprocesem.  
> - <xref:System.Web.UI.Timer?displayProperty=nameWithType>: součást ASP.NET, která v pravidelných intervalech provádí asynchronní nebo synchronní postbacky webových stránek.
> - <xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: časovač, který je <xref:System.Windows.Threading.Dispatcher> integrován do fronty, který je zpracován v určeném časovém intervalu a se zadanou prioritou.

## <a name="the-systemthreadingtimer-class"></a>Třída System.Threading.Timer

Třída <xref:System.Threading.Timer?displayProperty=nameWithType> umožňuje průběžně volat delegáta v určených časových intervalech. Tuto třídu můžete také použít k naplánování jednoho volání delegátovi v zadaném časovém intervalu. Delegát je spuštěn ve <xref:System.Threading.ThreadPool> vlákně.

Při vytváření <xref:System.Threading.Timer?displayProperty=nameWithType> objektu určíte <xref:System.Threading.TimerCallback> delegáta, který definuje metodu zpětného volání, volitelný objekt stavu, který je předán zpětnému volání, dobu zpoždění před prvním vyvoláním zpětného volání a časový interval mezi vyvoláním zpětného volání. Chcete-li zrušit čekající <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> časovač, zavolejte metodu.

Následující příklad vytvoří časovač, který volá zadaný delegát poprvé po jedné sekundě (1000 milisekund) a pak jej volá každé dvě sekundy. Objekt stavu v příkladu se používá ke spočítání, kolikrát je volána delegáta. Časovač je zastaven, pokud delegát byl volán alespoň 10 krát.

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

Další informace a příklady <xref:System.Threading.Timer?displayProperty=nameWithType>naleznete v tématu .

## <a name="the-systemtimerstimer-class"></a>Třída System.Timers.Timer

Další časovač, který lze použít v <xref:System.Timers.Timer?displayProperty=nameWithType> prostředí s více vlákny <xref:System.Threading.ThreadPool> je, že ve výchozím nastavení vyvolá událost ve vlákně.

Při vytváření <xref:System.Timers.Timer?displayProperty=nameWithType> objektu můžete určit časový interval, ve <xref:System.Timers.Timer.Elapsed> kterém chcete vyvolat událost. Pomocí <xref:System.Timers.Timer.Enabled%2A> vlastnosti označte, zda <xref:System.Timers.Timer.Elapsed> časovač má vyvolat událost. Pokud potřebujete <xref:System.Timers.Timer.Elapsed> událost, která má být vyvolána pouze jednou po <xref:System.Timers.Timer.AutoReset%2A> `false`uplynutí zadaného intervalu, nastavte na . Výchozí <xref:System.Timers.Timer.AutoReset%2A> hodnota vlastnosti `true`je , což <xref:System.Timers.Timer.Elapsed> znamená, že událost je <xref:System.Timers.Timer.Interval%2A> vyvolána pravidelně v intervalu definovaném vlastností.

Další informace a příklady <xref:System.Timers.Timer?displayProperty=nameWithType>naleznete v tématu .
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [Objekty a prvky zřetězení](threading-objects-and-features.md)

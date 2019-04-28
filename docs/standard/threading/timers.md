---
title: Časovače
description: Zjistěte, jaké časovače .NET pro použití v prostředí s více vlákny.
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
ms.author: ronpet
ms.openlocfilehash: 644ccf5951e9d2556fc697d2fd763f026fd0ebdb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672559"
---
# <a name="timers"></a>Časovače

.NET poskytuje dvě časovače pro použití v prostředí s více vlákny:

- <xref:System.Threading.Timer?displayProperty=nameWithType>, která spustí metodu zpětného volání jednoho na <xref:System.Threading.ThreadPool> vlákna v pravidelných intervalech.
- <xref:System.Timers.Timer?displayProperty=nameWithType>, který ve výchozím nastavení vyvolá událost, na <xref:System.Threading.ThreadPool> vlákna v pravidelných intervalech.

> [!NOTE]
> Některé implementace .NET mohou zahrnovat další časovače:
>
> - <xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: komponenty Windows Forms, který se aktivuje událost v pravidelných intervalech. Komponenta nemá žádné uživatelské rozhraní a je určená pro použití v prostředí s jedním vláknem.  
> - <xref:System.Web.UI.Timer?displayProperty=nameWithType>: komponentu ASP.NET, která provede zpětné volání synchronní nebo asynchronní webové stránky v pravidelných intervalech.
> - <xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: časovač, který je integrován do <xref:System.Windows.Threading.Dispatcher> fronty, která je zpracována v zadaném intervalu, času a na zadanou prioritou.

## <a name="the-systemthreadingtimer-class"></a>Třída System.Threading.Timer

<xref:System.Threading.Timer?displayProperty=nameWithType> Třída umožňuje nepřetržitě volání delegáta v zadaných časových intervalech. Tato třída také můžete použít k naplánování jedním voláním metody delegáta v zadaném časovém intervalu. Delegát se spouští podle <xref:System.Threading.ThreadPool> vlákna.

Při vytváření <xref:System.Threading.Timer?displayProperty=nameWithType> objektu, zadáte <xref:System.Threading.TimerCallback> delegáta, který definuje metodu zpětného volání, volitelné stavu objektu, který je předán do zpětného volání, dobu zpoždění před prvním vyvoláním služby zpětného volání a časový interval mezi vyvoláními zpětného volání. Chcete-li zrušit čekajícího časovače, zavolejte <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> metody.

Následující příklad vytvoří časovač, který volá uvedený delegát poprvé po jedné sekundě (1000 milisekund) a nazve je každé dvě sekundy. Stav objektu v příkladu se používá ke zjištění počtu volání delegáta se nazývá. Časovač je zastaven, když je delegát byla volána alespoň 10krát.

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

Další informace a příklady najdete v tématu <xref:System.Threading.Timer?displayProperty=nameWithType>.

## <a name="the-systemtimerstimer-class"></a>Třída System.Timers.Timer

Další časovač, který lze použít v prostředí s více vlákny je <xref:System.Timers.Timer?displayProperty=nameWithType> ve výchozím nastavení vyvolá událost, na <xref:System.Threading.ThreadPool> vlákna.

Když vytvoříte <xref:System.Timers.Timer?displayProperty=nameWithType> objektu, můžete zadat časový interval, ve který se má použít <xref:System.Timers.Timer.Elapsed> událostí. Použití <xref:System.Timers.Timer.Enabled%2A> vlastnost umožňující označit, pokud by měla vyvolat časovač <xref:System.Timers.Timer.Elapsed> událostí. Pokud potřebujete <xref:System.Timers.Timer.Elapsed> událost vyvolána pouze jednou po uplynutí zadaného intervalu, nastavte <xref:System.Timers.Timer.AutoReset%2A> k `false`. Výchozí hodnota <xref:System.Timers.Timer.AutoReset%2A> vlastnost je `true`, to znamená, že <xref:System.Timers.Timer.Elapsed> událost se vyvolá, pravidelně v intervalu určeném v <xref:System.Timers.Timer.Interval%2A> vlastnost.

Další informace a příklady najdete v tématu <xref:System.Timers.Timer?displayProperty=nameWithType>.
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [Funkce a objekty dělení na vlákna](threading-objects-and-features.md)

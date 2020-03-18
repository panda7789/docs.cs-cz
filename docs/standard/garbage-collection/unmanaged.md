---
title: Vymazání nespravovaných prostředků
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Close method
- Dispose method
- garbage collector
- garbage collection, unmanaged resources
- cleanup operations
- explicit cleanups
- unmanaged resource cleanup
- Finalize method
ms.assetid: a17b0066-71c2-4ba4-9822-8e19332fc213
ms.openlocfilehash: e05cfb949ee3f206f212ca7015f3ff4c22cd2a12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73423040"
---
# <a name="cleaning-up-unmanaged-resources"></a>Vymazání nespravovaných prostředků

U většiny objektů, které vaše aplikace vytvoří, se můžete spolehnout na . NET je uvolňování pro zpracování správy paměti. Pokud však vytváříte objekty, které zahrnují nespravované prostředky, musíte tyto prostředky explicitně uvolnit, pokud je v rámci aplikace již nepoužíváte. Nejběžnějšími typy nespravovaných prostředků jsou objekty, které obalují prostředky operačního systému, jako jsou soubory, okna, síťová připojení nebo připojení databáze. Přestože je systém uvolňování paměti schopen sledovat dobu platnosti objektu, který zapouzdřuje nespravovaný prostředek, nemá specifické znalosti o tom, jak spravovaný prostředek uvolnit a vyčistit.

Pokud vaše typy používají nespravované prostředky, měli byste provést následující úkony:

- Implementovat [dispose vzor](implementing-dispose.md). To vyžaduje, abyste <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> poskytli implementaci, která povolí deterministické uvolnění nespravovaných prostředků. Příjemce vašeho typu <xref:System.IDisposable.Dispose%2A> volá, když objekt (a prostředky, které používá) již není potřeba. Metoda <xref:System.IDisposable.Dispose%2A> okamžitě uvolní nespravované prostředky.

- Zajistěte, aby vaše nespravované prostředky byly uvolněny v případě, že spotřebitel vašeho typu zapomene volat <xref:System.IDisposable.Dispose%2A>. Toto lze provést dvěma způsoby:

  - Použijte bezpečný popisovač, který zajistí obtékání nespravovaných prostředků. Toto je doporučený postup. Bezpečné popisovače jsou odvozeny z <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> třídy a zahrnují robustní <xref:System.Object.Finalize%2A> metodu. Při použití bezpečného popisovače jednoduše <xref:System.IDisposable> implementovat rozhraní a <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> volání metody <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> bezpečného popisovače v implementaci. Finalizační metoda bezpečného popisovače je volána <xref:System.IDisposable.Dispose%2A> automaticky systémem uvolňování paměti, pokud není volána jeho metoda.

    —nebo—

  - Přepsat metodu. <xref:System.Object.Finalize%2A?displayProperty=nameWithType> Finalizace umožňuje nedeterministické uvolnění nespravovaných prostředků, když <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> příjemce typu nedokáže volat k jejich deterministicky dispose. Vzhledem k tomu, že finalizace objektu může být složitá operace náchylná k chybám, doporučujeme namísto poskytování vlastní finalizační metody použít bezpečný popisovač.

Spotřebitelé vašeho typu pak <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> můžete volat implementaci přímo do volné paměti používané nespravované prostředky. Při správné implementaci <xref:System.IDisposable.Dispose%2A> metody, buď <xref:System.Object.Finalize%2A> vaše metoda bezpečného popisovače <xref:System.Object.Finalize%2A?displayProperty=nameWithType> nebo vlastní přepsání metody se stane <xref:System.IDisposable.Dispose%2A> ochrannou pro vyčištění prostředků v případě, že metoda není volána.

## <a name="in-this-section"></a>V tomto oddílu

[Implementace metody Dispose](../../../docs/standard/garbage-collection/implementing-dispose.md) Popisuje, jak implementovat [dispose vzor](implementing-dispose.md) pro uvolnění nespravovaných prostředků.

[Použití objektů, které implementují IDisposable](../../../docs/standard/garbage-collection/using-objects.md) Popisuje, jak spotřebitelé typu zajistit, že jeho <xref:System.IDisposable.Dispose%2A> implementace je volána. Doporučujeme k tomu `using` použít příkaz `Using` C# nebo příkaz jazyka Visual Basic.

## <a name="reference"></a>Referenční informace

<xref:System.IDisposable?displayProperty=nameWithType>\
Definuje metodu <xref:System.IDisposable.Dispose%2A> pro uvolnění nespravovaných prostředků.

<xref:System.Object.Finalize%2A?displayProperty=nameWithType>\
Poskytuje pro dokončení objektu, pokud nespravované <xref:System.IDisposable.Dispose%2A> prostředky nejsou uvolněny metodou.

<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>\
Potlačí finalizaci. Tato metoda je obvykle volána z `Dispose` metody, která zabraňuje spuštění finalizační metody.

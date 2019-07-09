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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6be45a3d03d8cff580653260081a20d518448237
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662736"
---
# <a name="cleaning-up-unmanaged-resources"></a>Vymazání nespravovaných prostředků

U většiny objektů, které vaše aplikace vytvoří můžete se spolehnout na. NET pro uvolňování paměti správy paměti. Pokud však vytváříte objekty, které zahrnují nespravované prostředky, musíte tyto prostředky explicitně uvolnit, pokud je v rámci aplikace již nepoužíváte. Nejběžnějšími typy nespravovaných prostředků jsou objekty, které obalují prostředky operačního systému, jako jsou soubory, okna, síťová připojení nebo připojení databáze. Přestože je systém uvolňování paměti schopen sledovat dobu platnosti objektu, který zapouzdřuje nespravovaný prostředek, nemá specifické znalosti o tom, jak spravovaný prostředek uvolnit a vyčistit.

Pokud vaše typy používají nespravované prostředky, měli byste provést následující úkony:

- Implementace [vzor dispose](../../../docs/standard/design-guidelines/dispose-pattern.md). To vyžaduje, že jste zadali <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace umožňující deterministické uvolnění nespravovaných prostředků. Příjemce vašeho typu volání <xref:System.IDisposable.Dispose%2A> když objekt (a jimi používané prostředky) je už nepotřebujete. <xref:System.IDisposable.Dispose%2A> Metoda okamžitě uvolní nespravované prostředky.

- Zadejte pro vaše nespravovaných prostředků v případě, že příjemce vašeho typu zapomene zavolat <xref:System.IDisposable.Dispose%2A>. Toto lze provést dvěma způsoby:

  - Použijte bezpečný popisovač, který zajistí obtékání nespravovaných prostředků. Toto je doporučený postup. Bezpečné popisovače jsou odvozeny z <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> třídy a zahrnují robustní <xref:System.Object.Finalize%2A> metody. Pokud použijete bezpečný popisovač, stačí pouze implementovat <xref:System.IDisposable> rozhraní a volat bezpečný popisovač <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> metoda ve vaší <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace. Finalizační metoda bezpečného popisovače je volána automaticky metodou systému uvolňování paměti pokud jeho <xref:System.IDisposable.Dispose%2A> metoda není volána.

    —nebo—

  - Přepsat <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody. Finalizace umožňuje nedeterministické uvolnění nespravovaných prostředků, pokud příjemce typu selže při volání <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> a deterministicky neprovede. Vzhledem k tomu, že finalizace objektu může být složitá operace náchylná k chybám, doporučujeme namísto poskytování vlastní finalizační metody použít bezpečný popisovač.

Mohou příjemci typu provést zavoláním vaše <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> provádění uvolnění paměti využívané nespravovanými prostředky. Při správné implementaci <xref:System.IDisposable.Dispose%2A> metoda, buď bezpečný popisovač <xref:System.Object.Finalize%2A> metody nebo vaše vlastní přepsání metody <xref:System.Object.Finalize%2A?displayProperty=nameWithType> zabezpečení pro vyčištění prostředků v případě, že <xref:System.IDisposable.Dispose%2A> metoda není volána.

## <a name="in-this-section"></a>V tomto oddílu

[Implementace metody Dispose](../../../docs/standard/garbage-collection/implementing-dispose.md) popisuje, jak implementovat [vzor dispose](../../../docs/standard/design-guidelines/dispose-pattern.md) pro uvolnění nespravovaných prostředků.

[Použití objektů, které implementují rozhraní IDisposable](../../../docs/standard/garbage-collection/using-objects.md) popisuje, jak mohou příjemci typu zajistit, aby jeho <xref:System.IDisposable.Dispose%2A> volána implementace. Doporučujeme použít C# `using` příkazu nebo Visual Basic `Using` příkaz provedete to tak.

## <a name="reference"></a>Odkaz

<xref:System.IDisposable?displayProperty=nameWithType>\
Definuje <xref:System.IDisposable.Dispose%2A> metodu pro uvolnění nespravovaných prostředků.

<xref:System.Object.Finalize%2A?displayProperty=nameWithType>\
Zajišťuje finalizaci objektu, pokud nedojde k uvolnění nespravovaných prostředků podle <xref:System.IDisposable.Dispose%2A> metody.

<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>\
Potlačí finalizaci. Tato metoda je obvykle volána z `Dispose` metoda zabránit spuštění finalizační metody.

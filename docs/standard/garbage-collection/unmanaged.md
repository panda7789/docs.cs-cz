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
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423040"
---
# <a name="cleaning-up-unmanaged-resources"></a>Vymazání nespravovaných prostředků

Pro většinu objektů, které vaše aplikace vytvoří, můžete spoléhat na. Systém uvolňování paměti sítě pro zpracování správy paměti. Pokud však vytváříte objekty, které zahrnují nespravované prostředky, musíte tyto prostředky explicitně uvolnit, pokud je v rámci aplikace již nepoužíváte. Nejběžnějšími typy nespravovaných prostředků jsou objekty, které obalují prostředky operačního systému, jako jsou soubory, okna, síťová připojení nebo připojení databáze. Přestože je systém uvolňování paměti schopen sledovat dobu platnosti objektu, který zapouzdřuje nespravovaný prostředek, nemá specifické znalosti o tom, jak spravovaný prostředek uvolnit a vyčistit.

Pokud vaše typy používají nespravované prostředky, měli byste provést následující úkony:

- Implementujte [vzor Dispose](implementing-dispose.md). K tomu je potřeba, abyste zajistili <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementaci, která umožňuje deterministické vydání nespravovaných prostředků. Příjemce vašeho typu volá <xref:System.IDisposable.Dispose%2A>, když objekt (a prostředky, které používá) už není potřeba. Metoda <xref:System.IDisposable.Dispose%2A> hned uvolní nespravované prostředky.

- Poskytněte nespravované prostředky, které mají být vydány v případě, že příjemce vašeho typu zapomene volat <xref:System.IDisposable.Dispose%2A>. Toto lze provést dvěma způsoby:

  - Použijte bezpečný popisovač, který zajistí obtékání nespravovaných prostředků. Toto je doporučený postup. Bezpečné popisovače jsou odvozeny z třídy <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> a obsahují robustní <xref:System.Object.Finalize%2A> metodu. Pokud používáte bezpečný popisovač, jednoduše implementujete rozhraní <xref:System.IDisposable> a ve své implementaci <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> zavoláte metodu <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> bezpečného popisovače. Finalizační metoda bezpečného popisovače je volána automaticky systémem uvolňování paměti, pokud jeho <xref:System.IDisposable.Dispose%2A> metoda není volána.

    —nebo—

  - Přepsat metodu <xref:System.Object.Finalize%2A?displayProperty=nameWithType>. Finalizace umožňuje nedeterministické vydání nespravovaných prostředků, když příjemce typu nevolá <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> k jejich uvolnění. Vzhledem k tomu, že finalizace objektu může být složitá operace náchylná k chybám, doporučujeme namísto poskytování vlastní finalizační metody použít bezpečný popisovač.

Příjemci vašeho typu pak mohou volat vaši <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementaci přímo do volné paměti používané nespravovanými prostředky. Při správné implementaci <xref:System.IDisposable.Dispose%2A> metody, buď metoda bezpečného popisovač <xref:System.Object.Finalize%2A> nebo vaše vlastní přepsání metody <xref:System.Object.Finalize%2A?displayProperty=nameWithType>, se změní na zabezpečení pro vyčištění prostředků v případě, že metoda <xref:System.IDisposable.Dispose%2A> není volána.

## <a name="in-this-section"></a>V tomto oddílu

[Implementace metody Dispose](../../../docs/standard/garbage-collection/implementing-dispose.md) Popisuje, jak implementovat [vzor Dispose](implementing-dispose.md) pro uvolnění nespravovaných prostředků.

[Použití objektů, které implementují IDisposable](../../../docs/standard/garbage-collection/using-objects.md) Popisuje způsob, jakým uživatelé typu zajišťují, aby byla volána jeho <xref:System.IDisposable.Dispose%2A> implementace. K tomu doporučujeme použít C# příkaz `using` nebo příkaz Visual Basic `Using`.

## <a name="reference"></a>Odkaz

<xref:System.IDisposable?displayProperty=nameWithType>\
Definuje metodu <xref:System.IDisposable.Dispose%2A> pro uvolňování nespravovaných prostředků.

<xref:System.Object.Finalize%2A?displayProperty=nameWithType>\
Poskytuje finalizaci objektů, pokud metoda <xref:System.IDisposable.Dispose%2A> neuvolní nespravované prostředky.

<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>\
Potlačí finalizaci. Tato metoda je obvykle volána z metody `Dispose`, aby zabránila spuštění finalizační metody.

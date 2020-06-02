---
title: Čištění nespravovaných prostředků
ms.date: 05/13/2020
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
ms.openlocfilehash: aeb39f32c97424646b85b26ed9c4ed0e350d196b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287607"
---
# <a name="cleaning-up-unmanaged-resources"></a>Čištění nespravovaných prostředků

Pro většinu objektů, které vaše aplikace vytvoří, můžete spoléhat na [systém uvolňování paměti .NET](index.md) pro zpracování správy paměti. Když však vytváříte objekty, které obsahují nespravované prostředky, je nutné tyto prostředky explicitně uvolnit po jejich použití. Nejběžnějšími typy nespravovaných prostředků jsou objekty, které zabalí prostředky operačního systému, jako jsou soubory, Windows, síťová připojení nebo databázová připojení. Přestože je systém uvolňování paměti schopen sledovat dobu platnosti objektu, který zapouzdřuje nespravovaný prostředek, nemá specifické znalosti o tom, jak spravovaný prostředek uvolnit a vyčistit.

Pokud vaše typy používají nespravované prostředky, měli byste provést následující úkony:

- Implementujte [vzor Dispose](implementing-dispose.md). K tomu je potřeba poskytnout implementaci, která umožňuje <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> deterministické vydání nespravovaných prostředků. Příjemce volání typu <xref:System.IDisposable.Dispose%2A> v případě, že objekt (a prostředky, které používá) již není potřeba. <xref:System.IDisposable.Dispose%2A>Metoda okamžitě uvolní nespravované prostředky.

- V případě, že příjemce vašeho typu zapomene zavolat <xref:System.IDisposable.Dispose%2A> , poskytněte možnost uvolnění nespravovaných prostředků. Toto lze provést dvěma způsoby:

  - Použijte bezpečný popisovač, který zajistí obtékání nespravovaných prostředků. Toto je doporučený postup. Bezpečné popisovače jsou odvozeny z <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> abstraktní třídy a obsahují robustní <xref:System.Object.Finalize%2A> metodu. Pokud používáte bezpečný popisovač, jednoduše implementujete <xref:System.IDisposable> rozhraní a zavoláte metodu bezpečného popisovače <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> v <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementaci. Finalizační metoda bezpečného popisovače je volána automaticky systémem uvolňování paměti, pokud není <xref:System.IDisposable.Dispose%2A> volána jeho metoda.

    –**nebo**–

  - Přepsat <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metodu. Finalizace umožňuje nedeterministické vydání nespravovaných prostředků, když příjemce typu nevolá, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> aby bylo možné je vyřadit z něj deterministické. Definujte [finalizační](../../csharp/programming-guide/classes-and-structs/destructors.md) metodu přepsáním <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody.

  > [!WARNING]
  > Avšak vzhledem k tomu, že finalizace objektu může být složitá a operace náchylná k chybám, doporučujeme místo poskytování vlastního finalizační metody použít bezpečný popisovač.

Příjemci vašeho typu můžou následně zavolat vaši <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementaci přímo na volnou paměť využívanou nespravovanými prostředky. Při správné implementaci metody se <xref:System.IDisposable.Dispose%2A> buď metoda bezpečného popisovače <xref:System.Object.Finalize%2A> nebo vaše vlastní přepsání <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody změní na zabezpečení pro vyčištění prostředků v případě, že <xref:System.IDisposable.Dispose%2A> metoda není volána.

## <a name="in-this-section"></a>V této části

[Implementace metody Dispose](implementing-dispose.md) popisuje, jak implementovat vzor Dispose pro uvolnění nespravovaných prostředků.

[Použití objektů, které `IDisposable` implementují](using-objects.md) Popisuje, jak uživatelé typu zajišťují, že <xref:System.IDisposable.Dispose%2A> je volána jeho implementace. `using`K tomu doporučujeme použít příkaz C# (nebo Visual Basic `Using` ).

## <a name="reference"></a>Odkaz

| Typ/člen | Popis |
|--|--|
| <xref:System.IDisposable?displayProperty=nameWithType> | Definuje <xref:System.IDisposable.Dispose%2A> metodu pro uvolnění nespravovaných prostředků. |
| <xref:System.Object.Finalize%2A?displayProperty=nameWithType> | Poskytuje finalizaci objektu, pokud není nespravované prostředky uvolněny <xref:System.IDisposable.Dispose%2A> metodou. |
| <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> | Potlačí finalizaci. Tato metoda je obvykle volána z `Dispose` metody, aby zabránila spuštění finalizační metody. |

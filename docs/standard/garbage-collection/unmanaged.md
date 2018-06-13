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
ms.openlocfilehash: 5e32d2d4424d05b95af1eda400974da3293b8499
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575931"
---
# <a name="cleaning-up-unmanaged-resources"></a>Vymazání nespravovaných prostředků
Pro většinu objektů, které vytváří vaše aplikace můžete spolehnout na. NET na systém uvolňování paměti pro zpracování Správa paměti. Pokud však vytváříte objekty, které zahrnují nespravované prostředky, musíte tyto prostředky explicitně uvolnit, pokud je v rámci aplikace již nepoužíváte. Nejběžnějšími typy nespravovaných prostředků jsou objekty, které obalují prostředky operačního systému, jako jsou soubory, okna, síťová připojení nebo připojení databáze. Přestože je systém uvolňování paměti schopen sledovat dobu platnosti objektu, který zapouzdřuje nespravovaný prostředek, nemá specifické znalosti o tom, jak spravovaný prostředek uvolnit a vyčistit.  
  
 Pokud vaše typy používají nespravované prostředky, měli byste provést následující úkony:  
  
-   Implementace [dispose vzor](../../../docs/standard/design-guidelines/dispose-pattern.md). To vyžaduje, aby poskytovaly <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace povolit deterministický verzi nespravovaných prostředků. Příjemce voláními typ <xref:System.IDisposable.Dispose%2A> při objektu (a prostředky používá) již není potřeba. <xref:System.IDisposable.Dispose%2A> Metoda okamžitě uvolní nespravované prostředky.  
  
-   Poskytují pro nespravované prostředky k uvolnění v případě, že příjemce vašeho typu zapomene volat <xref:System.IDisposable.Dispose%2A>. Toto lze provést dvěma způsoby:  
  
    -   Použijte bezpečný popisovač, který zajistí obtékání nespravovaných prostředků. Toto je doporučený postup. Bezpečné obslužné rutiny, které jsou odvozeny od <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> třídy a zahrnout robustní <xref:System.Object.Finalize%2A> metoda. Použijete-li bezpečné popisovač, jednoduše implementovat <xref:System.IDisposable> rozhraní a volání bezpečného popisovač <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> metoda ve vaší <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace. Finalizační metodu bezpečné popisovač se nazývá automaticky modulem garbage collector v případě jeho <xref:System.IDisposable.Dispose%2A> metoda není volána.  
  
         —nebo—  
  
    -   Přepsání <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metoda. Finalizace umožňuje Nedeterministický verzi nespravovaných prostředků, když dojde k volání selhání příjemce a typ <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> k uvolnění těchto nepodmíněně. Vzhledem k tomu, že finalizace objektu může být složitá operace náchylná k chybám, doporučujeme namísto poskytování vlastní finalizační metody použít bezpečný popisovač.  
  
 Potom můžete volat příjemci vašeho typu vaší <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace přímo na uvolnění paměti, které nespravovaných prostředků. Při správně implementaci <xref:System.IDisposable.Dispose%2A> metoda, buď bezpečné popisovač <xref:System.Object.Finalize%2A> metoda nebo vlastní přepsání <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metoda bude chránit vyčištění prostředků v případě, že <xref:System.IDisposable.Dispose%2A> metoda není volána.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Implementace metody Dispose](../../../docs/standard/garbage-collection/implementing-dispose.md)  
 Popisuje, jak implementovat [dispose vzor](../../../docs/standard/design-guidelines/dispose-pattern.md) pro uvolnění nespravovaných prostředků.  
  
 [Použití objektů implementujících rozhraní IDisposable](../../../docs/standard/garbage-collection/using-objects.md)  
 Popisuje, jak uživatelé typu zajistěte, aby jeho <xref:System.IDisposable.Dispose%2A> implementace je volána. Doporučujeme používat jazyka C# `using` příkaz nebo Visual Basic `Using` příkaz k tomu.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.IDisposable?displayProperty=nameWithType>  
 Definuje <xref:System.IDisposable.Dispose%2A> metodu pro uvolnění nespravovaných prostředků.  
  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 Poskytuje pro dokončení objektu, pokud nejsou vydal nespravované prostředky <xref:System.IDisposable.Dispose%2A> metoda.  
  
 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>  
 Potlačí finalizaci. Tato metoda je volána infrastruktura z `Dispose` metodu finalizační metody zabránit ve spouštění.

---
title: "Slabé odkazy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 906c23caa7065486bb094ad2475ed9e7e24b3d9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="weak-references"></a>Slabé odkazy
Uvolňování paměti nelze shromažďovat objekt používá jiná aplikace při kódu aplikace dosáhnout tento objekt. Aplikace se říká obsahují silné odkaz na objekt.  
  
 Slabé odkazy umožňuje uvolňování ke shromažďování objekt zároveň umožňuje aplikaci získat přístup k objektu. Slabé odkazy je platný pouze během neurčitém množství času, dokud nebude objekt shromažďuje, když neexistuje žádné silné odkazy. Pokud použijete slabé odkaz, aplikace můžete získat stále silné odkaz na objekt, který zabraňuje v jeho nejsou shromažďována. Však není vždy riziko, že uvolňování paměti získá k objektu nejprve předtím, než se obnovila silné odkaz.  
  
 Slabé odkazy jsou užitečné pro objekty, které používají velké množství paměti, ale můžete je znovu vytvořit snadno Pokud jsou převzaty systémem uvolňování paměti.  
  
 Předpokládejme, že je stromové zobrazení v aplikaci Windows Forms zobrazí komplexní hierarchické výběr možností pro uživatele. Základní dat je velká, udržování stromu v paměti je v případě, když uživatel se zabývá něco jiného v aplikaci.  
  
 Když uživatel přepíná rychle do jiné části aplikace, můžete použít <xref:System.WeakReference> třída vytvořit slabé odkaz na stromu a zrušení silné všechny odkazy. Když uživatel přejde zpět do stromu, aplikace se pokusí získat silné odkaz na stromu a v případě úspěšného zabraňuje rekonstrukce stromu.  
  
 Když Pokud chcete stanovit slabé odkaz s objektem, vytvoříte <xref:System.WeakReference> pomocí instance objektu sledovat. Pak můžete nastavit <xref:System.WeakReference.Target%2A> vlastnost, která má tento objekt a sadu původní odkaz na objekt, který má `null`. Příklad kódu, najdete v článku <xref:System.WeakReference> v knihovně tříd.  
  
## <a name="short-and-long-weak-references"></a>Krátký a dlouhý slabé odkazy  
 Můžete vytvořit odkaz na krátké slabé nebo dlouho slabé odkazy:  
  
-   krátký  
  
     Cíl krátký slabé odkaz se změní na `null` když je objekt uvolněn systémem uvolňování paměti. Odkaz na slabé je sám spravovaného objektu a mohou podléhat uvolňování paměti stejně jako ostatní spravovaného objektu.  Odkaz na krátké slabé je pro výchozí konstruktor <xref:System.WeakReference>.  
  
-   dlouhá  
  
     Dlouho slabé odkaz se uchovávají objektu <xref:System.Object.Finalize%2A> byla volána metoda. To umožňuje objekt, který má být znovu vytvořen, ale pořád nepředvídatelným stav objektu. Chcete-li použít dlouho odkaz, zadejte `true` v <xref:System.WeakReference> konstruktor.  
  
     Pokud nemá typ objektu <xref:System.Object.Finalize%2A> používá funkci krátké Slabý odkaz metoda, a je slabé odkaz platný pouze dokud cíle jsou shromažďovány, kterému může dojít, kdykoli později finalizační metodu je spustit.  
  
 Vytvořit odkaz na silné a znovu použít objekt přetypovat <xref:System.WeakReference.Target%2A> vlastnost <xref:System.WeakReference> na typ objektu. Pokud <xref:System.WeakReference.Target%2A> vlastnost vrátí `null`objektu byla shromážděných jinak, můžete nadále používat objekt, protože aplikace je znovu získali silné odkaz na jeho.  
  
## <a name="guidelines-for-using-weak-references"></a>Pokyny k používání slabé odkazy  
 Použijte dlouho slabé odkazy pouze v případě potřeby, protože stav objektu nepředvídatelným po dokončení.  
  
 Nepoužívejte slabé odkazy na objekty malé, protože ukazatel samotné může být jako velké nebo větší.  
  
 Nepoužívejte slabé odkazy jako automatické řešení problémů správu paměti. Místo toho vytvořte efektivní zásady ukládání do mezipaměti pro zpracování objektů vaší aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)

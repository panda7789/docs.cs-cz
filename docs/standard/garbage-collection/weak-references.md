---
title: Slabé odkazy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65492beb888da1986f456d3fd000fc02f340f3c4
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121100"
---
# <a name="weak-references"></a>Slabé odkazy
Systému uvolňování paměti nelze shromáždit objektu používá aplikace, zatímco kód aplikace může dosáhnout tohoto objektu. Aplikace se říká, že mají silného odkazu na objekt.  
  
 Slabý odkaz umožňuje uvolňování paměti shromažďovat objekt zároveň umožní aplikaci přístup k objektu. Slabý odkaz je platný pouze během neurčitý množství času, dokud nebude objekt shromažďuje, když neexistují žádné odkazy na silné. Při použití nestálý odkaz, aplikace může stále získat silného odkazu na objekt, který zabrání shromažďování. Existuje ale vždy riziko, že systému uvolňování paměti získá objektu nejprve předtím, než se obnoví silného odkazu.  
  
 Slabé odkazy jsou užitečné pro objekty, které použít velké množství paměti, ale můžete vytvořit snadno, pokud jsou převzaty systémem uvolňování paměti.  
  
 Předpokládejme, že stromové zobrazení v aplikaci Windows Forms zobrazí komplexní hierarchické poskytoval možnosti pro uživatele. Podkladová data moc velká, uchovávání stromu v paměti je v případě, když je uživatel péči o něco jiného v aplikaci.  
  
 Když uživatel přejde do jiné části aplikace okamžitě, můžete použít <xref:System.WeakReference> třídy k vytvoření nestálý odkaz do stromové struktury a odstranit všechny odkazy silného. Když uživatel přejde zpět do stromu, aplikace se pokusí získat silného odkazu na stromové struktuře a, v případě úspěchu se vyhnete rekonstrukce stromu.  
  
 Chcete-li vytvořit nestálý odkaz s objektem, vytvoříte <xref:System.WeakReference> ke sledování pomocí instance objektu. Pak můžete nastavit <xref:System.WeakReference.Target%2A> nastavte na tento objekt a nastavte původní odkaz na objekt, který má `null`. Příklad kódu naleznete v tématu <xref:System.WeakReference> v knihovně tříd.  
  
## <a name="short-and-long-weak-references"></a>Krátký a dlouhý slabé odkazy  
 Můžete vytvořit krátké nestálý odkaz nebo long nestálý odkaz:  
  
-   krátké  
  
     Cíl krátké nestálý odkaz stane `null` při objektu je uvolněn systémem uvolňování paměti. Slabý odkaz je samotný objekt spravovaný a je časovač uvolněn z paměti stejně jako jakýkoli jiný spravovaný objekt.  Krátký nestálý odkaz je výchozí konstruktor pro <xref:System.WeakReference>.  
  
-   Long  
  
     Dlouho nestálý odkaz se uchovávají po objektu <xref:System.Object.Finalize%2A> byla volána metoda. To umožňuje objekt, který chcete znovu vytvořit, ale zůstane stav objektu nepředvídatelné. Použít odkaz na dlouhé, zadejte `true` v <xref:System.WeakReference> konstruktoru.  
  
     Pokud nemá typ objektu <xref:System.Object.Finalize%2A> použije metoda, krátký nestálý odkaz funkce a nestálý odkaz je platný pouze dokud cíle jsou shromažďovány, kterému může dojít kdykoliv po finalizační metodu je spustit.  
  
 Vytvořit silného odkazu a znovu použít objekt přetypujte <xref:System.WeakReference.Target%2A> vlastnost <xref:System.WeakReference> typu objektu. Pokud <xref:System.WeakReference.Target%2A> vrátí vlastnost `null`, byl tento objekt shromážděných; jinak vrátí hodnotu, můžete pokračovat pomocí objektu, protože aplikace má znovu získali silného odkazu na ni.  
  
## <a name="guidelines-for-using-weak-references"></a>Pokyny k používání slabé odkazy  
 Použijte dlouho slabé odkazy pouze v případě, že je nutné, protože stav objektu se po dokončení nepředvídatelné.  
  
 Nepoužívejte slabé odkazy na malé objekty, protože ukazatel sám může být tak velká, nebo větší.  
  
 Nepoužívejte slabé odkazy jako automatické řešení pro správu problémů s pamětí. Místo toho vyvíjejte platné zásady ukládání do mezipaměti pro zpracování objektů vaší aplikace.  
  
## <a name="see-also"></a>Viz také:

- [Uvolňování paměti](../../../docs/standard/garbage-collection/index.md)

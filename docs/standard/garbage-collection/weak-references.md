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
ms.openlocfilehash: 120777ca3c26b1634bd2143863547cfa4ea5deac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141329"
---
# <a name="weak-references"></a>Slabé odkazy
Systém uvolňování paměti nemůže shromažďovat objekt, který používá aplikace, zatímco kód aplikace může dosáhnout tohoto objektu. Aplikace je řekl, aby silný odkaz na objekt.  
  
 Slabý odkaz umožňuje uvolňování paměti shromažďovat objekt při zachování stále umožňuje aplikaci přístup k objektu. Slabý odkaz je platný pouze během neurčité množství času, dokud objekt je shromažďována, pokud neexistují žádné silné odkazy. Při použití slabé odkaz, aplikace stále získat silný odkaz na objekt, který zabraňuje jeho shromažďování. Existuje však vždy riziko, že systém uvolňování paměti se dostane k objektu nejprve před obnovením silného odkazu.  
  
 Slabé odkazy jsou užitečné pro objekty, které používají velké množství paměti, ale lze je snadno znovu vytvořit, pokud jsou uvolněny systémem uvolňování paměti.  
  
 Předpokládejme, že stromové zobrazení v aplikaci Windows Forms zobrazí uživateli komplexní hierarchický výběr možností. Pokud podkladová data je velký, udržování stromu v paměti je neefektivní, když uživatel je zapojen s něčím jiným v aplikaci.  
  
 Když uživatel přepne do jiné části aplikace, <xref:System.WeakReference> můžete použít třídu k vytvoření slabé odkaz na strom a zničit všechny silné odkazy. Když uživatel přepne zpět do stromu, aplikace se pokusí získat silný odkaz na strom a v případě úspěchu se vyhne rekonstrukci stromu.  
  
 Chcete-li vytvořit slabý odkaz s <xref:System.WeakReference> objektem, vytvořte pomocí instance objektu, který má být sledován. Potom nastavte <xref:System.WeakReference.Target%2A> vlastnost na tento objekt a nastavte původní `null`odkaz na objekt . Příklad kódu naleznete <xref:System.WeakReference> v knihovně tříd.  
  
## <a name="short-and-long-weak-references"></a>Krátké a dlouhé slabé odkazy  
 Můžete vytvořit krátký slabý odkaz nebo dlouhý slabý odkaz:  
  
- Krátké  
  
     Cíl krátký slabý odkaz `null` se stane, když je objekt uvolněn uvolnění paměti. Slabý odkaz je sám o sobě spravovaný objekt a je předmětem uvolňování paměti stejně jako jakýkoli jiný spravovaný objekt.  Krátký slabý odkaz je konstruktor <xref:System.WeakReference>bez parametrů pro .  
  
- Dlouhé  
  
     Dlouhý slabý odkaz je zachován a <xref:System.Object.Finalize%2A> metoda objektu byla volána. To umožňuje objekt znovu vytvořit, ale stav objektu zůstává nepředvídatelné. Chcete-li použít dlouhý `true` odkaz, zadejte v konstruktoru. <xref:System.WeakReference>  
  
     Pokud typ objektu nemá metodu, <xref:System.Object.Finalize%2A> použije se funkce krátké hojné referenční funkce a slabý odkaz je platný pouze do shromáždění cíle, ke kterému může dojít kdykoli po spuštění finalizační metody.  
  
 Chcete-li vytvořit silný odkaz a použít <xref:System.WeakReference.Target%2A> objekt <xref:System.WeakReference> znovu, přetypování vlastnost a na typ objektu. Pokud <xref:System.WeakReference.Target%2A> vlastnost `null`vrátí , objekt byl shromážděn; v opačném případě můžete pokračovat v používání objektu, protože aplikace získala silný odkaz na něj.  
  
## <a name="guidelines-for-using-weak-references"></a>Pokyny pro použití slabých odkazů  
 Dlouhé slabé odkazy používejte pouze v případě potřeby, protože stav objektu je po dokončení nepředvídatelný.  
  
 Nepoužívejte slabé odkazy na malé objekty, protože samotný ukazatel může být stejně velký nebo větší.  
  
 Nepoužívejte slabé odkazy jako automatické řešení problémů se správou paměti. Místo toho vytvořte zásady ukládání do mezipaměti pro zpracování objektů aplikace.  
  
## <a name="see-also"></a>Viz také

- [Kolekce paměti](../../../docs/standard/garbage-collection/index.md)

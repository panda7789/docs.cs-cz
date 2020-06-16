---
title: Slabé odkazy
description: Přečtěte si o slabých odkazech, které umožňují systému uvolňování paměti .NET shromažďovat objekt, zatímco aplikace stále umožňuje přístup k objektu.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
ms.openlocfilehash: 1c18b4fa979058893e0683620ec6cff8e7b15b9b
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768180"
---
# <a name="weak-references"></a>Slabé odkazy
Systém uvolňování paměti nemůže shromáždit objekt, který je používán aplikací, zatímco kód aplikace může dosáhnout tohoto objektu. Aplikace je označována jako, že má silný odkaz na objekt.  
  
 Slabý odkaz umožňuje, aby systém uvolňování paměti shromáždil objekt, zatímco aplikace stále umožňuje přístup k objektu. Slabý odkaz je platný pouze během neurčitého množství času, dokud není objekt shromážděn, když neexistují žádné silné odkazy. Když použijete slabý odkaz, aplikace může stále získat silný odkaz na objekt, který brání jeho shromažďování. Nicméně vždy hrozí riziko, že systém uvolňování paměti získá nejprve před tím, než se silný odkaz znovu vytvoří.  
  
 Slabé odkazy jsou užitečné pro objekty, které využívají hodně paměti, ale je možné je znovu vytvořit, pokud jsou uvolněny uvolňováním paměti.  
  
 Předpokládejme, že se stromové zobrazení v aplikaci model Windows Forms zobrazí uživateli komplexní hierarchická volba možností. Pokud je podkladová data velká, udržování stromu paměti je neefektivní, pokud je uživatel zapojen do aplikace v nějakém jiném.  
  
 Když uživatel přepne jinam do jiné části aplikace, můžete použít <xref:System.WeakReference> třídu k vytvoření slabého odkazu stromu a zničení všech silných odkazů. Když uživatel přepne zpět do stromu, aplikace se pokusí získat silný odkaz na strom a v případě úspěchu se vyhne opětovné konstrukci stromu.  
  
 Chcete-li vytvořit slabý odkaz na objekt, vytvoříte <xref:System.WeakReference> pomocí instance objektu, který chcete sledovat. Potom nastavíte <xref:System.WeakReference.Target%2A> vlastnost na tento objekt a nastavíte původní odkaz na objekt `null` . Příklad kódu naleznete <xref:System.WeakReference> v tématu v knihovně tříd.  
  
## <a name="short-and-long-weak-references"></a>Krátké a dlouhé slabé odkazy  
 Můžete vytvořit krátký slabý odkaz nebo dlouhý slabý odkaz:  
  
- Dostatečná  
  
     Cíl krátkého slabého odkazu se aktivuje, `null` když se objekt uvolní uvolňováním paměti. Slabý odkaz je sám o sobě spravovaným objektem a podléhá uvolňování paměti stejně jako jakýkoli jiný spravovaný objekt.  Krátký slabý odkaz je konstruktor bez parametrů pro <xref:System.WeakReference> .  
  
- Dlouhou  
  
     Po volání metody objektu se zachová dlouhý slabý odkaz <xref:System.Object.Finalize%2A> . To umožňuje, aby byl objekt znovu vytvořen, ale stav objektu zůstane nepředvídatelné. Chcete-li použít dlouhý odkaz, zadejte `true` v <xref:System.WeakReference> konstruktoru.  
  
     Pokud typ objektu nemá <xref:System.Object.Finalize%2A> metodu, je použita krátká slabá odkazová funkce a slabý odkaz je platný pouze do okamžiku, kdy je cíl shromážděn, což může nastat kdykoli po spuštění finalizační metody.  
  
 Chcete-li vytvořit silný odkaz a znovu použít objekt, přetypujte <xref:System.WeakReference.Target%2A> vlastnost na <xref:System.WeakReference> typ objektu. Pokud se <xref:System.WeakReference.Target%2A> vlastnost vrátí `null` , objekt byl shromážděn. v opačném případě můžete objekt nadále používat, protože aplikace znovu získala na něj silný odkaz.  
  
## <a name="guidelines-for-using-weak-references"></a>Pokyny pro používání slabých odkazů  
 Používejte dlouhé slabé odkazy pouze v případě, že je to nutné, protože stav objektu je po dokončení nepředvídatelné.  
  
 Nepoužívejte slabé odkazy na malé objekty, protože ukazatel sám může být velký nebo větší.  
  
 Nepoužívejte slabé odkazy jako automatické řešení problémů se správou paměti. Místo toho vytvořte účinné zásady ukládání do mezipaměti pro zpracování objektů aplikace.  
  
## <a name="see-also"></a>Viz také

- [Uvolňování paměti](index.md)

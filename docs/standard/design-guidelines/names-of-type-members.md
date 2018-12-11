---
title: Názvy členů typu
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
author: KrzysztofCwalina
ms.openlocfilehash: 264627f49a3d2a083f8f46f23f71e8b34d042c8e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127573"
---
# <a name="names-of-type-members"></a>Názvy členů typu
Typy jsou tvořeny členů: metody, vlastnosti, události, konstruktory a pole. Pokyny pro vytváření názvů členů typů v následujících částech.  
  
## <a name="names-of-methods"></a>Názvy metod  
 Protože metody jsou prostředky opatření, pokyny pro návrh vyžadují, aby názvy metod akce nebo operace frází. Také následující toto pravidlo slouží k odlišení názvy metod z vlastnost a zadejte názvy, které jsou věty podstatné jméno nebo přídavného jména.  
  
 **✓ DO** poskytují názvy metod, které jsou, nebo příkaz frází.  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a>Názvy vlastností  
 Na rozdíl od jiných členů vlastnosti by se měly provádět podstatné jméno fráze nebo tvary přídavných jmen názvy. Důvodem je skutečnost, že vlastnost odkazuje na data, a název vlastnosti, která odráží. PascalCasing se vždy používá pro názvy vlastností.  
  
 **✓ DO** název vlastnosti pomocí podstatné jméno, podstatné jméno fráze nebo přídavného jména.  
  
 **X DO NOT** mít vlastnosti, které odpovídají názvu metody "Get" jako v následujícím příkladu:  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 Tento model obvykle indikuje vlastnost by měla být skutečně metodu.  
  
 **✓ DO** název vlastnosti kolekce s množném čísle věta popisující položek v kolekci namísto použití singulární frázi "Seznam" nebo "Kolekce."  
  
 **✓ DO** název logické vlastnosti s nevyjádřil fráze (`CanSeek` místo `CantSeek`). Volitelně můžete také před logické vlastnosti pomocí "Je", "můžete" nebo "Má" pouze, pokud přidá hodnotu.  
  
 **✓ CONSIDER** poskytuje vlastnost se stejným názvem jako jeho typu.  
  
 Například následující vlastnost správně získá a nastaví hodnotu výčtu s názvem `Color`, takže název vlastnosti `Color`:  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a>Názvy událostí  
 Události odkazují na určitou akci, buď ten, který se děje, nebo aplikace, došlo k chybě. Proto stejně jako u metod, událostí jsou pojmenované s příkazy a čas příkaz slouží k určení doby, kdy je vyvolána událost.  
  
 **✓ DO** název události operaci nebo operace frází.  
  
 Mezi příklady patří `Clicked`, `Painting`, `DroppedDown`, a tak dále.  
  
 **✓ DO** pojmenovat události s koncept před a po ní, pomocí k dispozici a rodu minulosti.  
  
 Například by byla volána zavřít událost, která je aktivována před zavřením okna `Closing`, a ten, který je aktivována po zavření okna by byla volána `Closed`.  
  
 **X DO NOT** použijte "Before" nebo "After" předpony nebo postfixes udávajících před a po událostech. Použití, které jsou k dispozici a minulosti rodu, jak bylo právě popsáno.  
  
 **✓ DO** název s příponou "EventHandler" obslužné rutiny události (delegáty používané jako typy událostí), jak je znázorněno v následujícím příkladu:  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 **✓ DO** použití dvou parametrů s názvem `sender` a `e` v obslužných rutinách událostí.  
  
 Parametr odesílatele představuje objekt, který vyvolal událost. Parametr odesílatele je obvykle typu `object`i v případě, že je možné využívat více určitého typu.  
  
 **✓ DO** pojmenujte událost třídy argument s příponou "EventArgs".  
  
## <a name="names-of-fields"></a>Názvy polí  
 Pokyny pro pojmenování pole platí pro statické veřejné a chráněné položky. Interní a privátní pole nejsou pokryty všemi pokyny a pole veřejné nebo chráněné instance nejsou povoleny [pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md).  
  
 **✓ DO** použít PascalCasing v názvech polí.  
  
 **✓ DO** pojmenovat pole pomocí podstatné jméno, podstatné jméno fráze nebo přídavného jména.  
  
 **X DO NOT** použijte předponu pro názvy polí.  
  
 Nepoužívejte například "g_" nebo "s_" k označení statická pole.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
- [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)

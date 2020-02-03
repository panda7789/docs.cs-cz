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
ms.openlocfilehash: 81c837bd045992043208a59f6ee16803c1d6eb3c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744179"
---
# <a name="names-of-type-members"></a>Názvy členů typu
Typy jsou tvořeny členy: metody, vlastnosti, události, konstruktory a pole. Následující části popisují pokyny pro pojmenování členů typu.

## <a name="names-of-methods"></a>Názvy metod
 Vzhledem k tomu, že metody jsou způsoby provádění akce, pokyny pro návrh vyžadují, aby názvy metod byly příkazy nebo příkazy. Podle těchto pokynů také slouží k odlišení názvů metod od názvů vlastností a typů, což jsou podstatná jména nebo fráze.

 ✔️ Zadejte názvy metod, které jsou slovesy nebo fráze příkazů.

```csharp
public class String {
    public int CompareTo(...);
    public string[] Split(...);
    public string Trim();
}
```

## <a name="names-of-properties"></a>Názvy vlastností
 Na rozdíl od jiných členů je třeba předávat vlastnosti na jméno nebo název přídavného jména. Důvodem je, že vlastnost odkazuje na data a název vlastnosti odráží. PascalCasing se vždycky používá pro názvy vlastností.

 ✔️ pojmenovat vlastnosti s použitím podstatného jména, fráze podstatného jména nebo přídavného jména.

 ❌ nemají vlastnosti, které se shodují s názvem metody Get, jako v následujícím příkladu:

 `public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`

 Tento model obvykle označuje, že by vlastnost měla být ve skutečnosti metodou.

 ✔️ DO vlastností kolekce name pomocí množném fráze popisující položky v kolekci namísto použití fráze v jednotném čísle, za kterou následuje seznam nebo kolekce.

 ✔️ Pojmenujte logické vlastnosti s použitím kladné fráze (`CanSeek` namísto `CantSeek`). Volitelně můžete také zadat předponu logických vlastností pomocí "is", "Can" nebo "má", ale pouze tam, kde přidá hodnotu.

 ✔️ Zvažte vlastnost, která má stejný název jako jeho typ.

 Například následující vlastnost správně získá a nastaví hodnotu výčtu s názvem `Color`, takže vlastnost má název `Color`:

```csharp
public enum Color {...}
public class Control {
    public Color Color { get {...} set {...} }
}
```

## <a name="names-of-events"></a>Názvy událostí
 Události vždy odkazují na určitou akci, která se děje, nebo na jednu z nich. Proto jako u metod jsou události pojmenovány s příkazy a k označení času vyvolání události se používá příkaz vhodné.

 ✔️ události s názvem pomocí příkazu nebo fráze.

 Příklady zahrnují `Clicked`, `Painting`, `DroppedDown`a tak dále.

 ✔️ Přidávejte názvy událostí s konceptem před a po, a to pomocí současného a minulého časů.

 Například událost zavření, která je aktivována před zavřením okna, by byla volána `Closing`a ta, která je aktivována po zavření okna, by byla volána `Closed`.

 ❌ nepoužívat předpony a přípony "Before" nebo "After" k označení před a po událostech. Použijte přítomné a dřívější časů, jak je popsáno výše.

 ✔️ obslužné rutiny událostí názvů (Delegáti používané jako typy událostí) s příponou EventHandler, jak je znázorněno v následujícím příkladu:

 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`

 ✔️ použít dva parametry s názvem `sender` a `e` v obslužných rutinách událostí.

 Parametr Sender reprezentuje objekt, který vyvolal událost. Parametr sender je obvykle typu `object`, a to i v případě, že je možné využít konkrétnější typ.

 ✔️ třídy argumentu události názvu s příponou EventArgs.

## <a name="names-of-fields"></a>Názvy polí
 Pokyny pro pojmenovávání polí se vztahují na statická veřejná a chráněná pole. Do interních a privátních polí se nevztahují pokyny a v [pokynech návrhu členů](../../../docs/standard/design-guidelines/member.md)nejsou povolena pole veřejné nebo chráněné instance.

 ✔️ používat PascalCasing v názvech polí.

 ✔️ pole DO pole název s použitím podstatného jména, věty nebo jména.

 ❌ nepoužívejte předponu pro názvy polí.

 Například nepoužívejte "g_" nebo "s_" k označení statických polí.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)

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
ms.openlocfilehash: a9cd531100057fbad4884a20e6e7db6ef94e7956
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709215"
---
# <a name="names-of-type-members"></a>Názvy členů typu
Typy jsou tvořeny členy: metody, vlastnosti, události, konstruktory a pole. Následující části popisují pokyny pro pojmenování členů typu.  
  
## <a name="names-of-methods"></a>Názvy metod  
 Vzhledem k tomu, že metody jsou způsoby provádění akce, pokyny pro návrh vyžadují, aby názvy metod byly příkazy nebo příkazy. Podle těchto pokynů také slouží k odlišení názvů metod od názvů vlastností a typů, což jsou podstatná jména nebo fráze.  
  
 **✓ DO** poskytují názvy metod, které jsou, nebo příkaz frází.  
  
```csharp  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a>Názvy vlastností  
 Na rozdíl od jiných členů je třeba předávat vlastnosti na jméno nebo název přídavného jména. Důvodem je, že vlastnost odkazuje na data a název vlastnosti odráží. PascalCasing se vždycky používá pro názvy vlastností.  
  
 **✓ DO** název vlastnosti pomocí podstatné jméno, podstatné jméno fráze nebo přídavného jména.  
  
 **X DO NOT** mít vlastnosti, které odpovídají názvu metody "Get" jako v následujícím příkladu:  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 Tento model obvykle označuje, že by vlastnost měla být ve skutečnosti metodou.  
  
 **✓ Do** vlastností shromažďování názvů pomocí množném fráze, která popisuje položky v kolekci namísto použití fráze v jednotném čísle následovaných "list" nebo "Collection".  
  
 **✓ DO** název logické vlastnosti s nevyjádřil fráze (`CanSeek` místo `CantSeek`). Volitelně můžete také zadat předponu logických vlastností pomocí "is", "Can" nebo "má", ale pouze tam, kde přidá hodnotu.  
  
 **✓ CONSIDER** poskytuje vlastnost se stejným názvem jako jeho typu.  
  
 Například následující vlastnost správně získá a nastaví hodnotu výčtu s názvem `Color`, takže vlastnost má název `Color`:  
  
```csharp  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a>Názvy událostí  
 Události vždy odkazují na určitou akci, která se děje, nebo na jednu z nich. Proto jako u metod jsou události pojmenovány s příkazy a k označení času vyvolání události se používá příkaz vhodné.  
  
 **✓ DO** název události operaci nebo operace frází.  
  
 Příklady zahrnují `Clicked`, `Painting`, `DroppedDown`a tak dále.  
  
 **✓ DO** pojmenovat události s koncept před a po ní, pomocí k dispozici a rodu minulosti.  
  
 Například událost zavření, která je aktivována před zavřením okna, by byla volána `Closing`a ta, která je aktivována po zavření okna, by byla volána `Closed`.  
  
 **X DO NOT** použijte "Before" nebo "After" předpony nebo postfixes udávajících před a po událostech. Použijte přítomné a dřívější časů, jak je popsáno výše.  
  
 **✓ DO** název s příponou "EventHandler" obslužné rutiny události (delegáty používané jako typy událostí), jak je znázorněno v následujícím příkladu:  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 **✓ DO** použití dvou parametrů s názvem `sender` a `e` v obslužných rutinách událostí.  
  
 Parametr Sender reprezentuje objekt, který vyvolal událost. Parametr sender je obvykle typu `object`, a to i v případě, že je možné využít konkrétnější typ.  
  
 **✓ DO** pojmenujte událost třídy argument s příponou "EventArgs".  
  
## <a name="names-of-fields"></a>Názvy polí  
 Pokyny pro pojmenovávání polí se vztahují na statická veřejná a chráněná pole. Do interních a privátních polí se nevztahují pokyny a v [pokynech návrhu členů](../../../docs/standard/design-guidelines/member.md)nejsou povolena pole veřejné nebo chráněné instance.  
  
 **✓ DO** použít PascalCasing v názvech polí.  
  
 **✓ DO** pojmenovat pole pomocí podstatné jméno, podstatné jméno fráze nebo přídavného jména.  
  
 **X DO NOT** použijte předponu pro názvy polí.  
  
 Například nepoužívejte "g_" nebo "s_" k označení statických polí.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)

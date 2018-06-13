---
title: Názvy členy typu
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25fe93b63c518f54ee72300f26dfcb3f3ad21d76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575346"
---
# <a name="names-of-type-members"></a>Názvy členy typu
Typy jsou vytvářeny členů: metody, vlastnosti, události, konstruktory a pole. Následující části popisují pokyny pro pojmenování členy typu.  
  
## <a name="names-of-methods"></a>Názvy metod  
 Vzhledem k tomu, že jsou metody způsob akce, pokynů pro návrh vyžadují, aby metoda názvy příkazy nebo akce frází. Toto platí také následující slouží k rozlišení názvů metoda z vlastnost a zadejte názvy, které jsou podstatné jméno a přídavných jmen frází.  
  
 **PROVEĎTE ✓** zadejte název metody, které jsou, nebo příkaz frází.  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a>Názvy vlastností  
 Na rozdíl od jiných členů by měly mít vlastnosti frázi podstatné jméno nebo tvary přídavných jmen názvy. Je to způsobeno odkazuje vlastnost k datům a název vlastnosti, která odráží. PascalCasing se vždy používá pro názvy vlastností.  
  
 **PROVEĎTE ✓** název vlastnosti pomocí podstatné jméno, heslo podstatné jméno nebo přídavných jmen.  
  
 **X nesmí** mít vlastnosti, které odpovídají názvu metody "Get" jako v následujícím příkladu:  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 Tento vzor obvykle označuje vlastnost by měla být skutečně metodu.  
  
 **PROVEĎTE ✓** název vlastnosti v kolekci s množném čísle frázi popisující položky v kolekci místo použití singulární frázi následuje "seznam" nebo "Kolekce."  
  
 **PROVEĎTE ✓** název logické vlastnosti s kladných frázi (`CanSeek` místo `CantSeek`). Volitelně můžete také předpony logická hodnota vlastnosti s "Je", "můžete" nebo "Má" ale pouze tam, kde se přidá hodnotu.  
  
 **✓ ZVAŽTE** poskytnutí stejný název jako typ vlastnosti.  
  
 Například následující vlastnost správně získá a nastaví hodnotu výčtu s názvem `Color`, takže je název vlastnosti `Color`:  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a>Názvy událostí  
 Události se vždy odkazují na některé akce, a to buď jednu, která je situaci nebo ten, který došlo k chybě. Stejně jako u metody, proto události jsou pojmenované s příkazy a slovesného příkaz času slouží k označení doby, kdy je vyvolána událost.  
  
 **PROVEĎTE ✓** název události s operaci nebo frázi operaci.  
  
 Mezi příklady patří `Clicked`, `Painting`, `DroppedDown`a tak dále.  
  
 **PROVEĎTE ✓** zadejte název události s koncept před a po, pomocí přítomen a časů v minulosti.  
  
 Například by názvem zavřít událost, která je vyvolána před zavřením okna `Closing`, a ten, který je vyvolána po zavření okna by se volat `Closed`.  
  
 **X nesmí** použijte "Před" nebo "Po" předpony nebo postfixes k označení před a po události. Použití přítomen a časy minulosti jako právě popsané.  
  
 **PROVEĎTE ✓** název obslužné rutiny událostí (delegáti používat jako typy událostí) s příponou "Obslužná rutina události", jak je znázorněno v následujícím příkladu:  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 **PROVEĎTE ✓** použít dva parametry s názvem `sender` a `e` v obslužné rutiny událostí.  
  
 Parametr odesílatele představuje objekt, který vyvolá událost. Parametr odesílatele je obvykle typu `object`i v případě, že je možné využívat více konkrétního typu.  
  
 **PROVEĎTE ✓** název události třídy argument s příponou "EventArgs".  
  
## <a name="names-of-fields"></a>Názvy polí  
 Pole názvy pokyny se vztahují k statických polí veřejné a chráněné. Interní a privátní pole nejsou předmětem pokyny a veřejné nebo chráněné instance pole nejsou povoleny [pokynů pro návrh člen](../../../docs/standard/design-guidelines/member.md).  
  
 **PROVEĎTE ✓** použít PascalCasing v názvech polí.  
  
 **PROVEĎTE ✓** název pole pomocí podstatné jméno, heslo podstatné jméno nebo přídavných jmen.  
  
 **X nesmí** použijte předponu pro názvy polí.  
  
 Nepoužívejte například "g_" nebo "s_" k označení statických polí.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)

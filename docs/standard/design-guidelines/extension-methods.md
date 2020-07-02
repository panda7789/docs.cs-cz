---
title: Metody rozšíření
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
ms.openlocfilehash: 55e6a816bbec401fdb061a3394635378b2f37424
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621597"
---
# <a name="extension-methods"></a>Metody rozšíření
Rozšiřující metody jsou funkce jazyka, která umožňuje volání statických metod pomocí syntaxe volání metody instance. Tyto metody musí mít alespoň jeden parametr, který představuje instanci, na které je metoda provozována.

 Třída, která definuje takové metody rozšíření, je označována jako třída "sponzor" a musí být deklarována jako statická. Chcete-li použít rozšiřující metody, musí jedna importovat obor názvů definující třídu sponzor.

 ❌Vyhněte se frivolously definování rozšiřujících metod, zejména u typů, které nevlastníte.

 Pokud vlastníte zdrojový kód typu, zvažte místo toho použití regulárních metod instance. Pokud nevlastníte a chcete přidat metodu, buďte velmi opatrní. Liberalizace použití rozšiřujících metod má potenciál nepotřebných rozhraní API typů, která nebyla navržena pro tyto metody.

 ✔️ Zvažte použití rozšiřujících metod v některém z následujících scénářů:

- Pro poskytování pomocných funkcí, které jsou relevantní pro každou implementaci rozhraní, pokud se tyto funkce dají zapsat v rámci základního rozhraní. Důvodem je skutečnost, že konkrétní implementace nemohou být jinak přiřazeny rozhraním. Například `LINQ to Objects` operátory jsou implementovány jako metody rozšíření pro všechny <xref:System.Collections.Generic.IEnumerable%601> typy. Všechny implementace tak `IEnumerable<>` budou automaticky povoleny LINQ.

- Když metoda instance by zavedla závislost na některém typu, ale taková závislost by mohla přerušit pravidla správy závislostí. Například závislost z <xref:System.String> na <xref:System.Uri?displayProperty=nameWithType> je pravděpodobně nežádoucí, takže `String.ToUri()` návratová metoda instance `System.Uri` by představovala špatný návrh z perspektivy správy závislostí. Návratová metoda statického rozšíření `Uri.ToUri(this string str)` `System.Uri` by byla mnohem lepším návrhem.

 ❌Vyhněte se definování metod rozšíření na <xref:System.Object?displayProperty=nameWithType> .

 Uživatelé jazyka VB nebudou moci volat takové metody pro odkazy na objekty pomocí syntaxe metody rozšíření. VB nepodporuje volání takových metod, protože v jazyce VB, který deklaruje odkaz jako objekt vynucuje, aby všechna volání metod byla v tomto případě pozdní vazbou (skutečný člen nazvaný je určen za běhu), zatímco vazby na metody rozšíření jsou určeny v době kompilace (s časnou vazbou).

 Všimněte si, že se pravidla vztahují na jiné jazyky, kde se nachází stejné chování vazby, nebo kde nejsou podporované rozšiřující metody.

 ❌Neumísťujte rozšiřující metody do stejného oboru názvů jako rozšířený typ, pokud se nejedná o přidání metod do rozhraní nebo pro správu závislostí.

 ❌Vyhněte se definování dvou nebo více rozšiřujících metod se stejnou signaturou, a to i v případě, že se nacházejí v různých oborech názvů.

 ✔️ Zvažte definování metod rozšíření ve stejném oboru názvů jako rozšířený typ, pokud je typ rozhraní a pokud mají být metody rozšíření použity ve většině nebo ve všech případech.

 ❌Nedefinujte metody rozšíření implementující funkci v oborech názvů obvykle přidružených k jiným funkcím. Místo toho je definujte v oboru názvů přidruženém k funkci, ke které patří.

 ❌Vyhněte se obecným názvům oborů názvů vyhrazených pro metody rozšíření (např. "rozšíření"). Místo toho použijte popisný název (například "Routing").

 *Částečně &copy; 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také:

- [Pokyny pro návrh členů](member.md)
- [Pokyny k návrhu architektury](index.md)

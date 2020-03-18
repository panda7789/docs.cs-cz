---
title: Názvy tříd, struktur a rozhraní
ms.date: 10/22/2008
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
ms.openlocfilehash: 2c528348c0e84037a80df9797c56f03b51c73adc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400594"
---
# <a name="names-of-classes-structs-and-interfaces"></a>Názvy tříd, struktur a rozhraní
Následující pokyny pro pojmenování platí pro obecné pojmenování typu.

 ✔️ do name třídy a struktury s návěsy nebo fráze užitkových jmen, pomocí PascalCasing.

 Tím se odlišují názvy typů od metod, které jsou pojmenovány s lovesnými frázemi.

 ✔️ do název rozhraní s přídavnými jmény, nebo občas s přídavnými jmény nebo fráze z rozmene.

 Fráze se zápojem a beznosná označení by měla být používána zřídka a mohou označovat, že typ by měl být abstraktní třídou, nikoli rozhraním.

 ❌Nedávejte názvy tříd předponu (např.

 ✔️ ZVAŽTe ukončení názvu odvozených tříd názvem základní třídy.

 To je velmi čitelné a vysvětluje vztah jasně. Některé příklady tohoto v `ArgumentOutOfRangeException`kódu jsou: , `Exception`což `SerializableAttribute`je druh , `Attribute`a , což je druh . Při uplatňování těchto pokynů je však důležité použít přiměřený úsudek; například `Button` třída je druh `Control` události, `Control` i když se nezobrazí v jeho názvu.

 ✔️ názvy předpony rozhraní DO s písmenem I, což znamená, že typ je rozhraní.

 Například `IComponent` (popisné jméno), `ICustomAttributeProvider` (fráze nosného `IPersistable` jména) a (přídavné jméno) jsou vhodné názvy rozhraní. Stejně jako u jiných názvů typů se vyhněte zkratkám.

 ✔️ do ujistěte se, že názvy se liší pouze předponou "I" na název rozhraní při definování dvojice třídy rozhraní, kde třída je standardní implementace rozhraní.

## <a name="names-of-generic-type-parameters"></a>Názvy parametrů obecného typu
 Obecné typy byly přidány do rozhraní .NET Framework 2.0. Tato funkce zavedla nový druh identifikátoru nazývaný *parametr typu*.

 ✔️ do název obecný typ parametry s popisnými názvy, pokud jednopísmenný název je zcela samovysvětlující a popisný název by nepřidanou hodnotu.

 ✔️ ZVAŽTe použití `T` jako název parametru typu pro typy s jedním parametrem typu s jedním písmenem.

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 ✔️ názvy parametrů popisného typu `T`předpony DO s programem .

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 ✔️ ZVAŽTe označení omezení umístěných na parametr typu v názvu parametru.

 Například parametr omezen na `ISession` může být `TSession`volána .

## <a name="names-of-common-types"></a>Názvy běžných typů
 ✔️ do postupujte podle pokynů popsaných v následující tabulce při pojmenování typů odvozených z nebo provádění některých typů rozhraní .NET Framework.

|Základní typ|Pokyny pro odvozené/implementující typ|
|---------------|------------------------------------------|
|`System.Attribute`|✔️ DO přidat příponu "Atribut" do názvů vlastních tříd atributů.|
|`System.Delegate`|✔️ DO přidat příponu "EventHandler" do názvů delegátů, které se používají v událostech.<br /><br /> ✔️ DO přidat příponu "Zpětné volání" na názvy delegátů než ty, které se používají jako obslužné rutiny událostí.<br /><br /> ❌NEPŘIdávejte příponu "Delegát" delegátovi.|
|`System.EventArgs`|✔️ DO přidat příponu "EventArgs."|
|`System.Enum`|❌NEODvozujte z této třídy; místo toho použijte klíčové slovo podporované vaším jazykem; například v c#, `enum` použijte klíčové slovo.<br /><br /> ❌Nepřidávejte příponu "Enum" nebo "Flag".|
|`System.Exception`|✔️ DO přidat příponu "Výjimka".|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|✔️ do přidat příponu "Slovník." Všimněte `IDictionary` si, že je konkrétní typ kolekce, ale tento pokyn má přednost před obecnější kolekce pokyny, které následuje.|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|✔️ do přidat příponu "Kolekce".|
|`System.IO.Stream`|✔️ do přidat příponu "Stream.".|
|`CodeAccessPermission IPermission`|✔️ do přidat příponu "Oprávnění".|

## <a name="naming-enumerations"></a>Pojmenování výčtů
 Názvy typů výčtu (také nazývané výčty) obecně by se měly řídit standardními pravidly pojmenování typu (PascalCasing atd.). Existují však další pokyny, které platí konkrétně pro výčty.

 ✔️ DO použít název jednotného čísla typu pro výčet, pokud jeho hodnoty jsou bitová pole.

 ✔️ DO použít název typu množného čísla pro výčet s bitovými poli jako hodnoty, nazývané také výčty příznaků.

 ❌Nepoužívejte příponu "Enum" v názvech typů výčtu.

 ❌Nepoužívejte přípony "Příznak" nebo "Příznaky" v názvech typu enum.

 ❌Nepoužívejte předponu na názvy hodnot výčtu (např. "ad" pro výčty ADO, "rtf" pro výčty rtf atd.).

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno se svolením Pearson Education, Inc. z [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)

---
title: Názvy tříd, struktur a rozhraní
description: Použijte tyto pokyny pro pojmenovávání tříd, struktur a rozhraní jako součást pokynů pro navrhování knihoven, které rozšíří a pracují s knihovnami .NET.
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
ms.openlocfilehash: b9de9329cc8e1bfc47a46523c7119bb3b2c244d8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290211"
---
# <a name="names-of-classes-structs-and-interfaces"></a>Názvy tříd, struktur a rozhraní
Pokyny pro pojmenování, které následují, se týkají obecného typu pojmenování.

 pomocí PascalCasing ✔️ DO tříd názvů a struktur s podstatnými jmény nebo frázemi podstatných jmen.

 To odlišuje názvy typů od metod, které jsou pojmenovány pomocí příkazového fráze.

 ✔️ DO názvových rozhraní přidávejte fráze adjektiva nebo občas s podstatnými jmény nebo frázemi podstatných jmen.

 Podstatná jména a fráze substantivum by se měly používat zřídka a můžou indikovat, že typ by měl být abstraktní třída, a ne rozhraní.

 ❌Neposkytněte název třídy předponu (např. "C").

 ✔️ Zvažte ukončení názvu odvozených tříd s názvem základní třídy.

 To je velmi čitelné a jasně vysvětluje vztah. Některé příklady tohoto kódu v kódu jsou: `ArgumentOutOfRangeException` , což je typ `Exception` a `SerializableAttribute` , což je druh `Attribute` . Je ale důležité použít rozumné rozhodnutí při použití této směrnice. `Button`Třída je například druh `Control` události, i když `Control` se nezobrazuje v názvu.

 ✔️ PROVEDE předpony názvů rozhraní s písmenem I, aby označoval, že typ je rozhraní.

 Například `IComponent` (popisný substantivum), `ICustomAttributeProvider` (fráze substantivum) a `IPersistable` (adjektivum) jsou vhodné názvy rozhraní. Stejně jako u jiných typů názvů Vyhněte zkratce.

 ✔️ Zajistěte, aby se názvy lišily pouze předponou "I" v názvu rozhraní při definování dvojice třídy – rozhraní, kde je třída standardní implementací rozhraní.

## <a name="names-of-generic-type-parameters"></a>Názvy parametrů obecného typu
 K .NET Framework 2,0 byly přidány obecné typy. Funkce představila nový typ identifikátoru nazvaný *parametr typu*.

 ✔️ pojmenovat parametry obecného typu s popisnými názvy, pokud není název s jedním písmenem zcela zřejmý a popisný název by nepřidal hodnotu.

 ✔️ ZVÁŽIT použití `T` jako názvu parametru typu pro typy s jedním parametrem typu s jedním písmenem.

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 ✔️ DĚLAT předpony názvů parametrů popisného typu s `T` .

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 ✔️ Zvažte označení omezení, která jsou uvedena v parametru typu v názvu parametru.

 Například parametr omezený na `ISession` může být volán `TSession` .

## <a name="names-of-common-types"></a>Názvy běžných typů
 ✔️ postupujte podle pokynů popsaných v následující tabulce, když pojmenováváte typy odvozené z nebo implementují určité .NET Framework typy.

|Základní typ|Základní pravidlo pro odvození/implementaci typu|
|---------------|------------------------------------------|
|`System.Attribute`|✔️ Přidejte příponu "Attribute" do názvů vlastních tříd atributů.|
|`System.Delegate`|✔️ přidat příponu EventHandler do názvů delegátů, kteří se používají v událostech.<br /><br /> ✔️ přidat příponu "zpětného volání" do názvů jiných delegátů, než které byly použity jako obslužné rutiny událostí.<br /><br /> ❌Nepřidejte příponu Delegate do delegáta.|
|`System.EventArgs`|✔️ přidat příponu EventArgs.|
|`System.Enum`|❌Neodvozovat z této třídy; místo toho použijte klíčové slovo podporované vaším jazykem. například v jazyce C# použijte `enum` klíčové slovo.<br /><br /> ❌Nepřidávat příponu "enum" nebo "Flag".|
|`System.Exception`|✔️ přidat příponu "Exception".|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|✔️ přidat příponu "Dictionary". Všimněte si, že `IDictionary` se jedná o konkrétní typ kolekce, ale tyto obecné zásady mají přednost před obecnější pokyny k kolekcím.|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|✔️ přidat příponu "Collection".|
|`System.IO.Stream`|✔️ přidat příponu "Stream".|
|`CodeAccessPermission IPermission`|✔️ přidat příponu "oprávnění".|

## <a name="naming-enumerations"></a>Vytváření názvů výčtů
 Názvy výčtových typů (označovaných také jako výčty) by obecně měly splňovat standardní pravidla pro pojmenovávání typů (PascalCasing atd.). Existují však další pokyny, které platí konkrétně pro výčty.

 ✔️ použít název typu jednotného čísla pro výčet, pokud jeho hodnoty nejsou bitové pole.

 ✔️ použít název typu plural pro výčet s bitovými poli jako hodnoty, označované také jako příznaky Enum.

 ❌V názvech typu výčtu nepoužívejte příponu Enum.

 ❌V názvech typu výčtu nepoužívejte přípony příznak ani Flags.

 ❌Nepoužívejte předponu u názvů hodnot výčtu (např. "AD" pro výčty objektů ADO, "RTF" pro výčty formátovaného textu atd.).

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny k návrhu architektury](index.md)
- [Pokyny pro pojmenování](naming-guidelines.md)

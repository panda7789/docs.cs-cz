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
author: KrzysztofCwalina
ms.openlocfilehash: 2ecd708ccb8eb91270e8ef9c174b8d7e599a2629
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353720"
---
# <a name="names-of-classes-structs-and-interfaces"></a>Názvy tříd, struktur a rozhraní
Pokyny pro pojmenování, které následují, se týkají obecného typu pojmenování.  
  
 **✓ DO** název třídy a struktury s podstatná jména či fráze podstatné jméno, pomocí PascalCasing.  
  
 To odlišuje názvy typů od metod, které jsou pojmenovány pomocí příkazového fráze.  
  
 **✓ DO** název rozhraní tvary přídavných jmen fráze nebo příležitostně s podstatná jména či fráze podstatné jméno.  
  
 Podstatná jména a fráze substantivum by se měly používat zřídka a můžou indikovat, že typ by měl být abstraktní třída, a ne rozhraní.  
  
 **X DO NOT** poskytnout názvy tříd předpona (například "C").  
  
 **✓ CONSIDER** ukončení název odvozené třídy s názvem základní třídy.  
  
 To je velmi čitelné a jasně vysvětluje vztah. Některé příklady tohoto kódu jsou: `ArgumentOutOfRangeException`, což je druh `Exception`a `SerializableAttribute`, což je typ `Attribute`. Je ale důležité použít rozumné rozhodnutí při použití této směrnice. Například třída `Button` je druh události `Control`, i když `Control` se nezobrazuje v názvu.  
  
 **✓ DO** předponu rozhraní názvy písmenem I, že je typ rozhraní.  
  
 Například `IComponent` (popisný substantivum), `ICustomAttributeProvider` (fráze substantivum) a `IPersistable` (adjektivum) jsou vhodné názvy rozhraní. Stejně jako u jiných typů názvů Vyhněte zkratce.  
  
 **✓ DO** Ujistěte se, že názvy liší pouze pomocí "I" předpony na název rozhraní při definování pár třída – rozhraní, kde třída je standardní implementace rozhraní.  
  
## <a name="names-of-generic-type-parameters"></a>Názvy parametrů obecného typu  
 K .NET Framework 2,0 byly přidány obecné typy. Funkce představila nový typ identifikátoru nazvaný *parametr typu*.  
  
 **✓ DO** název parametry obecného typu pomocí popisných názvů, pokud je název jednoho písmeno úplně není potřeba vysvětlovat a popisný název nebude přidejte hodnotu.  
  
 **✓ CONSIDER** pomocí `T` jako název typu parametru pro typy s jeden parametr typu jedním písmenem.  
  
```csharp  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **✓ DO** předpony typ popisné názvy parametrů s `T`.  
  
```csharp  
public interface ISessionChannel<TSession> where TSession : ISession {  
    TSession Session { get; }  
}  
```  
  
 **✓ CONSIDER** označující omezení vztahujících se na parametr typu názvu parametru.  
  
 Například parametr omezený na `ISession` může být volán `TSession`.  
  
## <a name="names-of-common-types"></a>Názvy běžných typů  
 **✓ DO** postupujte podle pokynů popsaných v následující tabulce, při pojmenování typy odvozené od nebo implementaci určitých typů rozhraní .NET Framework.  
  
|Základní typ|Základní pravidlo pro odvození/implementaci typu|  
|---------------|------------------------------------------|  
|`System.Attribute`|**✓ DO** přidat příponu "Atribut" názvy vlastních atributů tříd.|  
|`System.Delegate`|**✓ DO** přidat příponu "Obslužná rutina události" na názvy delegáti, které se používají v události.<br /><br /> **✓ DO** přidat příponu "Zpětné volání" pro názvy delegátů kromě těch, které používá jako obslužné rutiny událostí.<br /><br /> **X DO NOT** přidat příponu "Delegáta" s delegátem.|  
|`System.EventArgs`|**✓ DO** přidat příponu "EventArgs."|  
|`System.Enum`|**X DO NOT** odvozovat z této třídy; použijte – klíčové slovo jazyka nepodporuje místo toho, například v jazyce C#, použít `enum` – klíčové slovo.<br /><br /> **X DO NOT** přidat příponu "Výčtu" nebo "Příznak."|  
|`System.Exception`|**✓ DO** přidat příponu "Výjimky."|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**✓ DO** přidat příponu "Slovník." Všimněte si, že `IDictionary` je konkrétní typ kolekce, ale tyto zásady mají přednost před obecnější pokyny ke kolekcím.|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**✓ DO** přidat příponu "Kolekce."|  
|`System.IO.Stream`|**✓ DO** přidat příponu "Stream."|  
|`CodeAccessPermission IPermission`|**✓ DO** přidat příponu "Oprávnění."|  
  
## <a name="naming-enumerations"></a>Vytváření názvů výčtů  
 Názvy výčtových typů (označovaných také jako výčty) by obecně měly splňovat standardní pravidla pro pojmenovávání typů (PascalCasing atd.). Existují však další pokyny, které platí konkrétně pro výčty.  
  
 **✓ DO** použijte název singulární typ výčtu pouze v případě jeho hodnoty jsou bitová pole.  
  
 **✓ DO** použijte název množném čísle typ výčtu s bitových polí jako hodnoty, označované taky jako příznaky výčtu.  
  
 **X DO NOT** používají příponu "Výčtu" v názvech typ výčtu.  
  
 **X DO NOT** použijte "Příznak" nebo "Příznaky" přípony ve výčtu zadejte názvy.  
  
 **X DO NOT** použijte předponu na názvy hodnot výčtu (například "ad" pro výčty ADO.), "rtf" pro výčty RTF atd.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)

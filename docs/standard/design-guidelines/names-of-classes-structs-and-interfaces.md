---
title: Názvy tříd, struktur a rozhraní
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f60a2283c01d0dc2665dafaa99ea52000aa3bc47
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552280"
---
# <a name="names-of-classes-structs-and-interfaces"></a>Názvy tříd, struktur a rozhraní
Pokyny pro pojmenování, které následují platí pro pojmenování obecného typu.  
  
 **✓ DO** název třídy a struktury s podstatná jména či fráze podstatné jméno, pomocí PascalCasing.  
  
 Názvy typů to odlišuje od metody, které jsou pojmenovány příkaz Možnosti.  
  
 **✓ DO** název rozhraní tvary přídavných jmen fráze nebo příležitostně s podstatná jména či fráze podstatné jméno.  
  
 Podstatná jména a frází podstatné jméno by měl používat jen zřídka a může znamenat, že typ musí být abstraktní třída a není rozhraní.  
  
 **X DO NOT** poskytnout názvy tříd předpona (například "C").  
  
 **✓ CONSIDER** ukončení název odvozené třídy s názvem základní třídy.  
  
 To je velmi čitelný a jasně vysvětluje relace. Tady je několik příkladů tohoto kódu: `ArgumentOutOfRangeException`, což je typ z `Exception`, a `SerializableAttribute`, což je typ z `Attribute`. Je však potřeba použít přiměřené rozhodnutí při uplatňování toto pravidlo; například `Button` třída je typ z `Control` události, i když `Control` nezobrazí ve svém názvu.  
  
 **✓ DO** předponu rozhraní názvy písmenem I, že je typ rozhraní.  
  
 Například `IComponent` (popisná podstatná) `ICustomAttributeProvider` (podstatné jméno fráze), a `IPersistable` (přídavného jména) jsou názvy odpovídající rozhraní. Stejně jako jiné názvy typů se vyhněte zkratky.  
  
 **✓ DO** Ujistěte se, že názvy liší pouze pomocí "I" předpony na název rozhraní při definování pár třída – rozhraní, kde třída je standardní implementace rozhraní.  
  
## <a name="names-of-generic-type-parameters"></a>Názvy parametrů obecného typu  
 Obecné typy byly přidány do rozhraní .NET Framework 2.0. Funkce zavedená nová druh identifikátor s názvem *parametr typu*.  
  
 **✓ DO** název parametry obecného typu pomocí popisných názvů, pokud je název jednoho písmeno úplně není potřeba vysvětlovat a popisný název nebude přidejte hodnotu.  
  
 **✓ CONSIDER** pomocí `T` jako název typu parametru pro typy s jeden parametr typu jedním písmenem.  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **✓ DO** předpony typ popisné názvy parametrů s `T`.  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession {  
    TSession Session { get; }  
}  
```  
  
 **✓ CONSIDER** označující omezení vztahujících se na parametr typu názvu parametru.  
  
 Například s omezením parametru `ISession` může být volána `TSession`.  
  
## <a name="names-of-common-types"></a>Názvy běžných typů  
 **✓ DO** postupujte podle pokynů popsaných v následující tabulce, při pojmenování typy odvozené od nebo implementaci určitých typů rozhraní .NET Framework.  
  
|Základní typ|Pravidlo typu odvozené/implementace|  
|---------------|------------------------------------------|  
|`System.Attribute`|**✓ DO** přidat příponu "Atribut" názvy vlastních atributů tříd.|  
|`System.Delegate`|**✓ DO** přidat příponu "Obslužná rutina události" na názvy delegáti, které se používají v události.<br /><br /> **✓ DO** přidat příponu "Zpětné volání" pro názvy delegátů kromě těch, které používá jako obslužné rutiny událostí.<br /><br /> **X DO NOT** přidat příponu "Delegáta" s delegátem.|  
|`System.EventArgs`|**✓ DO** přidat příponu "EventArgs."|  
|`System.Enum`|**X DO NOT** odvozovat z této třídy; použijte – klíčové slovo jazyka nepodporuje místo toho, například v jazyce C#, použít `enum` – klíčové slovo.<br /><br /> **X DO NOT** přidat příponu "Výčtu" nebo "Příznak."|  
|`System.Exception`|**✓ DO** přidat příponu "Výjimky."|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**✓ DO** přidat příponu "Slovník." Všimněte si, že `IDictionary` je určitý typ kolekce, ale toto pravidlo má přednost před více obecných pokynů kolekce, který následuje.|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**✓ DO** přidat příponu "Kolekce."|  
|`System.IO.Stream`|**✓ DO** přidat příponu "Stream."|  
|`CodeAccessPermission IPermission`|**✓ DO** přidat příponu "Oprávnění."|  
  
## <a name="naming-enumerations"></a>Názvy výčtů  
 Názvy typů výčtu (také nazývané výčtů) obecně by měla dodržovat standardní pojmenování typ pravidla (PascalCasing atd.). Existují však další pokyny, které platí konkrétně pro výčty.  
  
 **✓ DO** použijte název singulární typ výčtu pouze v případě jeho hodnoty jsou bitová pole.  
  
 **✓ DO** použijte název množném čísle typ výčtu s bitových polí jako hodnoty, označované taky jako příznaky výčtu.  
  
 **X DO NOT** používají příponu "Výčtu" v názvech typ výčtu.  
  
 **X DO NOT** použijte "Příznak" nebo "Příznaky" přípony ve výčtu zadejte názvy.  
  
 **X DO NOT** použijte předponu na názvy hodnot výčtu (například "ad" pro výčty ADO.), "rtf" pro výčty RTF atd.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)

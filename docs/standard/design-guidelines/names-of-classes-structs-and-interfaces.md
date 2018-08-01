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
ms.openlocfilehash: a1841fbfcb76d5b56681b63ec4b39e9a7418707f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576139"
---
# <a name="names-of-classes-structs-and-interfaces"></a>Názvy tříd, struktur a rozhraní
Pojmenování pokyny, které platí pro pojmenování obecného typu.  
  
 **✓ DO** název třídy a struktury s podstatná jména či fráze podstatné jméno, pomocí PascalCasing.  
  
 Názvy typů to odlišuje od metody, které jsou s názvem s frází operaci.  
  
 **✓ DO** název rozhraní tvary přídavných jmen fráze nebo příležitostně s podstatná jména či fráze podstatné jméno.  
  
 Podstatná jména a podstatné jméno frází by měl používat jen zřídka a může znamenat, že typ by měl být abstraktní třída a není rozhraní.  
  
 **X DO NOT** poskytnout názvy tříd předpona (například "C").  
  
 **✓ CONSIDER** ukončení název odvozené třídy s názvem základní třídy.  
  
 To je velmi čitelná a jasně vysvětluje relace. Některé příklady v kódu: `ArgumentOutOfRangeException`, což je typ z `Exception`, a `SerializableAttribute`, což je typ z `Attribute`. Je ale důležité použít přiměřené rozhodnutí v použití obecných zásad; například `Button` třída je typ z `Control` události, i když `Control` nezobrazí v jeho názvu.  
  
 **✓ DO** předponu rozhraní názvy písmenem I, že je typ rozhraní.  
  
 Například `IComponent` (popisná podstatná jména), `ICustomAttributeProvider` (podstatné jméno frázi), a `IPersistable` (přídavných jmen) jsou vhodné rozhraní názvy. Stejně jako u jiných názvy typů vyhněte zkratky.  
  
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
public interface ISessionChannel<TSession> where TSession : ISession{  
    TSession Session { get; }  
}  
```  
  
 **✓ CONSIDER** označující omezení vztahujících se na parametr typu názvu parametru.  
  
 Například parametr omezená na `ISession` může být například `TSession`.  
  
## <a name="names-of-common-types"></a>Názvy běžné typy  
 **✓ DO** postupujte podle pokynů popsaných v následující tabulce, při pojmenování typy odvozené od nebo implementaci určitých typů rozhraní .NET Framework.  
  
|Základní typ|Odvozené implementace typu obecné zásady|  
|---------------|------------------------------------------|  
|`System.Attribute`|**✓ DO** přidat příponu "Atribut" názvy vlastních atributů tříd.|  
|`System.Delegate`|**✓ DO** přidat příponu "Obslužná rutina události" na názvy delegáti, které se používají v události.<br /><br /> **✓ DO** přidat příponu "Zpětné volání" pro názvy delegátů kromě těch, které používá jako obslužné rutiny událostí.<br /><br /> **X DO NOT** přidat příponu "Delegáta" s delegátem.|  
|`System.EventArgs`|**✓ DO** přidat příponu "EventArgs."|  
|`System.Enum`|**X DO NOT** odvozovat z této třídy; použijte – klíčové slovo jazyka nepodporuje místo toho, například v jazyce C#, použít `enum` – klíčové slovo.<br /><br /> **X DO NOT** přidat příponu "Výčtu" nebo "Příznak."|  
|`System.Exception`|**✓ DO** přidat příponu "Výjimky."|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**✓ DO** přidat příponu "Slovník." Všimněte si, že `IDictionary` je určitý typ kolekce, ale tyto obecné zásady má přednost před více obecných pokynů kolekce, který následuje dále.|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**✓ DO** přidat příponu "Kolekce."|  
|`System.IO.Stream`|**✓ DO** přidat příponu "Stream."|  
|`CodeAccessPermission IPermission`|**✓ DO** přidat příponu "Oprávnění."|  
  
## <a name="naming-enumerations"></a>Pojmenování výčty  
 Názvy výčtové typy (také nazývané výčty) obecně by mělo vycházet standardní pojmenování typ pravidla (PascalCasing atd.). Existují však další pokyny, které platí konkrétně pro výčty.  
  
 **✓ DO** použijte název singulární typ výčtu pouze v případě jeho hodnoty jsou bitová pole.  
  
 **✓ DO** použijte název množném čísle typ výčtu s bitových polí jako hodnoty, označované taky jako příznaky výčtu.  
  
 **X DO NOT** používají příponu "Výčtu" v názvech typ výčtu.  
  
 **X DO NOT** použijte "Příznak" nebo "Příznaky" přípony ve výčtu zadejte názvy.  
  
 **X DO NOT** použijte předponu na názvy hodnot výčtu (například "ad" pro výčty ADO.), "rtf" pro výčty RTF atd.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)

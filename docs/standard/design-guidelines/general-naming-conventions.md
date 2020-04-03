---
title: Obecné konvence pojmenování
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
ms.openlocfilehash: ef4a8f571a67477739bbc59d3103ba78dea47177
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635923"
---
# <a name="general-naming-conventions"></a>Obecné konvence pojmenování

Tato část popisuje obecné konvence pojmenování, které se vztahují k výběru slov, pokyny pro použití zkratek a zkratky a doporučení, jak se vyhnout použití názvů specifických pro jazyk.

## <a name="word-choice"></a>Volba slova
 ✔️ DO vybrat snadno čitelné názvy identifikátorů.

 Například vlastnost s `HorizontalAlignment` názvem je čitelnější `AlignmentHorizontal`pro angličtinu než .

 ✔️ do prospěch čitelnost před stručnost.

 Název `CanScrollHorizontally` vlastnosti je `ScrollableX` lepší než (obskurní odkaz na osu X).

 ❌NEPOUŽÍVEJTE podtržítka, pomlčky ani žádné jiné nealfanumerické znaky.

 ❌NEPOUŽÍVEJTE maďarský zápis.

 ❌Vyhněte se použití identifikátorů, které jsou v konfliktu s klíčovými slovy široce používaných programovacích jazyků.

 Podle pravidla 4 specifikace common language (CLS) musí všechny kompatibilní jazyky poskytovat mechanismus, který umožňuje přístup k pojmenovaným položkám, které používají klíčové slovo tohoto jazyka jako identifikátor. C#, například používá znak @ jako mechanismus escape v tomto případě. Je však stále vhodné vyhnout se běžným klíčovým slovům, protože je mnohem obtížnější použít metodu s řídicí sekvencí než bez ní.

## <a name="using-abbreviations-and-acronyms"></a>Použití zkratek a zkratek
 ❌NEPOUŽÍVEJTE zkratky nebo kontrakce jako součást názvů identifikátorů.

 Například použijte `GetWindow` spíše `GetWin`než .

 ❌Nepoužívejte žádné zkratky, které nejsou široce přijímané, a to i v případě, že jsou, pouze v případě potřeby.

## <a name="avoiding-language-specific-names"></a>Jak se vyhnout názvům specifickým pro jazyk
 ✔️ DO používat sémanticky zajímavé názvy spíše než jazyk-specifické klíčová slova pro názvy typů.

 Například `GetLength` je lepší název `GetInt`než .

 ✔️ DO použít obecný název typu CLR, nikoli název specifický pro jazyk, ve výjimečných případech, kdy identifikátor nemá žádný sémantický význam nad rámec svého typu.

 Například metoda převodu <xref:System.Int64> by měla `ToInt64`být `ToLong` pojmenována , nikoli (protože <xref:System.Int64> je název `long`CLR pro alias specifický pro C#). V následující tabulce je uvedeno několik základních datových typů používajících názvy typů CLR (stejně jako odpovídající názvy typů pro c#, visual basic a c++).

|C#|Visual Basic|C++|CLR|
|---------|------------------|-----------|---------|
|**Sbyte**|**Sbyte**|**char**|**Sbyte**|
|**Bajt**|**Byte**|**unsigned char**|**Byte**|
|**short**|**Krátké**|**short**|**Int16**|
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|
|**int**|**Celé číslo**|**int**|**Int32**|
|**uint**|**UInt32**|**unsigned int**|**UInt32**|
|**long**|**Dlouhé**|**__int64**|**Int64**|
|**ulong**|**UInt64**|**nepodepsané __int64**|**UInt64**|
|**float**|**Single**|**float**|**Single**|
|**double**|**Dvojité**|**double**|**Dvojité**|
|**bool**|**Logická hodnota**|**bool**|**Logická hodnota**|
|**char**|**Char**|**wchar_t**|**Char**|
|**Řetězec**|**Řetězec**|**Řetězec**|**Řetězec**|
|**Objekt**|**Objekt**|**Objekt**|**Objekt**|

 ✔️ DO používat běžný název, například `value` nebo `item`, spíše než opakování názvu typu, ve výjimečných případech, kdy identifikátor nemá žádný sémantický význam a typ parametru není důležité.

## <a name="naming-new-versions-of-existing-apis"></a>Pojmenování nových verzí existujících api
 ✔️ do použít název podobný staré rozhraní API při vytváření nových verzí existující rozhraní API.

 To pomáhá zvýraznit vztah mezi api.

 ✔️ do raději přidání přípony spíše než předponu k označení nové verze existující rozhraní API.

 To pomůže při zjišťování při procházení dokumentace nebo při použití technologie IntelliSense. Stará verze rozhraní API bude uspořádána v blízkosti nových rozhraní API, protože většina prohlížečů a technologie IntelliSense zobrazuje identifikátory v abecedním pořadí.

 ✔️ zvažte použití zcela nového, ale smysluplného identifikátoru, namísto přidání přípony nebo předpony.

 ✔️ do použít číselnou příponu k označení nové verze existující rozhraní API, zejména v případě, že existující název rozhraní API je jediný název, který dává smysl (tj. pokud je průmyslový standard) a pokud přidání jakékoli smysluplné přípony (nebo změna názvu) není vhodnou volbou.

 ❌Nepoužívejte příponu "Ex" (nebo podobné) identifikátor odlišit od starší verze stejného rozhraní API.

 ✔️ do použít příponu "64" při zavádění verzí api, které pracují na 64bitové celé číslo (dlouhé celé číslo) namísto 32bitové celé číslo. Tento přístup je třeba provést pouze v případě, že existuje existující 32bitové rozhraní API; nedělejte to pro zcela nová api pouze s 64bitovou verzí.

 *Části &copy; 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno se svolením Pearson Education, Inc. z [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)
- [Konvence pojmenování rozhraní .NET pro editorConfig](/visualstudio/ide/editorconfig-naming-conventions)

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
ms.openlocfilehash: c90987fd28d5157cfb7f7eea4680b5ab4be1a200
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290951"
---
# <a name="general-naming-conventions"></a>Obecné konvence pojmenování

Tato část popisuje obecné konvence vytváření názvů, které se týkají volby Wordu, pokyny k používání zkratky a zkratek a doporučení, jak se vyhnout použití názvů specifických pro jazyk.

## <a name="word-choice"></a>Volba Wordu
 ✔️ zvolit snadno čitelné názvy identifikátorů.

 Například vlastnost s názvem `HorizontalAlignment` je více než v angličtině čitelné `AlignmentHorizontal` .

 ✔️ upřednostnit čitelnost přes zkrácení.

 Název vlastnosti `CanScrollHorizontally` je lepší než `ScrollableX` (skryje odkaz na osu X).

 ❌Nepoužívejte podtržítka, spojovníky nebo žádné jiné nealfanumerické znaky.

 ❌Nepoužívejte maďarské notace.

 ❌Vyhněte se použití identifikátorů, které jsou v konfliktu s klíčovými slovy široce používaných programovacích jazyků.

 V souladu s pravidlem 4 specifikace CLS (Common Language Specification) musí všechny vyhovující jazyky poskytovat mechanismus, který umožňuje přístup k pojmenovaným položkám, které používají klíčové slovo tohoto jazyka jako identifikátor. Jazyk C# například v tomto případě používá jako řídicí mechanismus znak @ Sign. Je však stále vhodné se vyhnout běžným klíčovým slovům, protože je mnohem obtížnější použít metodu s řídicí sekvencí, než je ta bez ní.

## <a name="using-abbreviations-and-acronyms"></a>Používání zkratek a zkratek
 ❌Nepoužívejte zkratky ani smluvní strany jako součást názvů identifikátorů.

 Použijte například `GetWindow` místo `GetWin` .

 ❌Nepoužívejte žádné zkratky, které nejsou běžně přijímány, a to i v případě potřeby.

## <a name="avoiding-language-specific-names"></a>Vyloučení názvů specifických pro jazyk
 ✔️ použít sémanticky zajímavé názvy namísto klíčových slov specifických pro jednotlivé jazyky pro názvy typů.

 Například `GetLength` je lepší název než `GetInt` .

 ✔️ použít název obecného typu CLR, nikoli název specifický pro jazyk, ve výjimečných případech, kdy identifikátor nemá sémantický význam mimo jeho typ.

 Například metoda převodu na hodnotu <xref:System.Int64> by měla být pojmenována `ToInt64` , not `ToLong` (protože <xref:System.Int64> je název CLR pro alias specifický pro jazyk C# `long` ). Následující tabulka uvádí několik základních datových typů pomocí názvů typů CLR (a také odpovídajících názvů typů pro C#, Visual Basic a C++).

|C#|Visual Basic|C++|CLR|
|---------|------------------|-----------|---------|
|**SByte**|**SByte**|**char**|**SByte**|
|**bytové**|**Bytové**|**unsigned char**|**Bytové**|
|**short**|**Dostatečná**|**short**|**Int16**|
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|
|**int**|**Čísla**|**int**|**Int32**|
|**uint**|**UInt32**|**unsigned int**|**UInt32**|
|**long**|**Dlouhou**|**__int64**|**Int64**|
|**ulong**|**UInt64**|**Nepodepsaný __int64**|**UInt64**|
|**Plovák**|**Single**|**Plovák**|**Single**|
|**double**|**Klepat**|**double**|**Klepat**|
|**bool**|**Logická hodnota**|**bool**|**Logická hodnota**|
|**char**|**Char**|**wchar_t**|**Char**|
|**řetězec**|**Řetězec**|**Řetězec**|**Řetězec**|
|**odkazy objektů**|**Předmětů**|**Předmětů**|**Předmětů**|

 ✔️ použít běžný název, například `value` nebo `item` , namísto opakování názvu typu, ve výjimečných případech, kdy identifikátor nemá sémantický význam a typ parametru není důležitý.

## <a name="naming-new-versions-of-existing-apis"></a>Pojmenovávání nových verzí stávajících rozhraní API
 Při vytváření nových verzí existujícího rozhraní API se ✔️ použít název podobný tomuto starému rozhraní API.

 Tato možnost pomáhá zdůraznit vztah mezi rozhraními API.

 ✔️ raději přidat příponu místo předpony, která označuje novou verzi existujícího rozhraní API.

 To vám pomůže se zjišťováním při procházení dokumentace nebo pomocí technologie IntelliSense. Stará verze rozhraní API bude uspořádána blízko nových rozhraní API, protože většina prohlížečů a IntelliSense zobrazuje identifikátory v abecedním pořadí.

 ✔️ Zvažte použití zcela nového, ale smysluplného identifikátoru namísto přidání přípony nebo předpony.

 ✔️ použít číselnou příponu k označení nové verze existujícího rozhraní API, zejména pokud je stávající název rozhraní API jediným názvem, který dává smysl (tj. Pokud jde o průmyslový standard), a pokud přidání jakékoli smysluplné přípony (nebo změny názvu) nepředstavuje vhodnou možnost.

 ❌Nepoužívejte příponu "ex" (nebo podobnou) pro identifikátor k odlišení od dřívější verze stejného rozhraní API.

 ✔️ použít příponu "64" při představení verzí rozhraní API, které pracují na 64 celočíselném čísle (dlouhé celé číslo) namísto hodnoty 32-bit integer. Tento přístup je potřeba vzít jenom v případě, že existující rozhraní API pro 32 existuje. Neprovádějte ji pro nové rozhraní API pro novou značku s pouze 64 verzí.

 *Částečně &copy; 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny k návrhu architektury](index.md)
- [Pokyny k pojmenování](naming-guidelines.md)
- [Konvence vytváření názvů .NET pro EditorConfig](/visualstudio/ide/editorconfig-naming-conventions)

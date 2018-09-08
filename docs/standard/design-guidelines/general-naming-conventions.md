---
title: Obecné zásady vytváření názvů
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd3defd969b5f26fb95e7feca9c3d533e67272b1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44209496"
---
# <a name="general-naming-conventions"></a>Obecné zásady vytváření názvů
Tato část popisuje obecné zásady vytváření názvů, které se týkají podle vlastní volby slov, pokyny na pomocí zkratky a zkratky a doporučení o tom, abyste se vyhnuli použití názvů specifických pro jazyk.  
  
## <a name="word-choice"></a>Volba aplikace Word  
 **✓ DO** zvolte snadno čitelné identifikátor názvy.  
  
 Například vlastnost s názvem `HorizontalAlignment` je angličtina čitelnější než `AlignmentHorizontal`.  
  
 **✓ DO** upřednostnit čitelnost přes jako stručný výtah.  
  
 Název vlastnosti `CanScrollHorizontally` je obecně lepší než `ScrollableX` (skrytého odkaz na ose x).  
  
 **X DO NOT** použít podtržítka, pomlčky nebo jiné nealfanumerické znaky.  
  
 **X DO NOT** použijte Maďarská zápis.  
  
 **X AVOID** pomocí identifikátorů, které je v konfliktu s slov široce používá programovací jazyky.  
  
 Podle pravidla 4 z specifikace CLS (Common Language) musí všechny kompatibilní s jazyky poskytují mechanismus, který umožňuje přístup k pojmenované položky, které používají – klíčové slovo volbou jazyka jako identifikátor. Jazyk C#, například používá jako mechanismus v tomto případě řídicí znak @. Je však stále vhodné vyhnout běžných klíčových slov, protože je mnohem obtížnější použít metodu s řídicí sekvence než jedna bez ní.  
  
## <a name="using-abbreviations-and-acronyms"></a>Použití zkratky a zkratky  
 **X DO NOT** použít zkratky nebo staženiny jako součást identifikátoru názvy.  
  
 Například použít `GetWindow` spíše než `GetWin`.  
  
 **X DO NOT** žádné režim, které nejsou široce používaný a to i v případě, že jsou pouze v případě, že je nutné použít.  
  
## <a name="avoiding-language-specific-names"></a>Jak se vyhnout názvů specifických pro jazyk  
 **✓ DO** používá sémanticky zajímavé názvy namísto klíčová slova specifická pro jazyk pro názvy typů.  
  
 Například `GetLength` je název lepší než `GetInt`.  
  
 **✓ DO** použít obecný název typu CLR, nikoli název konkrétní jazyk, ve výjimečných případech, pokud identifikátor nemá význam sémantického nad rámec jeho typu.  
  
 Například metoda převodu na <xref:System.Int64> by měly být pojmenovány `ToInt64`, nikoli `ToLong` (protože <xref:System.Int64> je název CLR pro jazyk C#-konkrétní alias `long`). Následující tabulka představuje několik základních datových typů pomocí názvy typů modulu CLR (stejně jako odpovídající názvy typů pro C#, Visual Basic a C++).  
  
|C#|Visual Basic|C++|CLR|  
|---------|------------------|-----------|---------|  
|**sbyte**|**SByte –**|**char**|**SByte –**|  
|**byte**|**Bajtů**|**unsigned char**|**Bajtů**|  
|**short**|**krátké**|**short**|**Int16**|  
|**ushort**|**UInt16**|**short bez znaménka**|**UInt16**|  
|**int**|**celé číslo**|**int**|**Datový typ Int32**|  
|**uint**|**UInt32**|**unsigned int**|**UInt32**|  
|**long**|**Long**|**__int64**|**Int64**|  
|**ulong**|**UInt64**|**unsigned __int64**|**UInt64**|  
|**float**|**Jeden**|**float**|**Jeden**|  
|**double**|**Double**|**double**|**Double**|  
|**bool**|**Datový typ Boolean**|**bool**|**Datový typ Boolean**|  
|**char**|**Char**|**wchar_t**|**Char**|  
|**string**|**řetězec**|**řetězec**|**řetězec**|  
|**object**|**objekt**|**objekt**|**objekt**|  
  
 **✓ DO** použít běžný název, například `value` nebo `item`, místo opakování název typu ve výjimečných případech, pokud identifikátor nemá žádný význam sémantického a typ parametru není důležité.  
  
## <a name="naming-new-versions-of-existing-apis"></a>Pojmenování nové verze stávajících rozhraní API  
 **✓ DO** použijte název podobná staré rozhraní API, při vytváření nové verze existujícího rozhraní API.  
  
 To pomáhá zvýraznit vztahy mezi rozhraním API.  
  
 **✓ DO** přednost přidání příponu místo předpony označující novou verzi existujícího rozhraní API.  
  
 To vám pomůže zjišťování při procházení dokumentaci, nebo pomocí technologie IntelliSense. Stará verze rozhraní API uspořádání blízko nová rozhraní API, protože většina prohlížečů a technologie IntelliSense zobrazí identifikátory v abecedním pořadí.  
  
 **✓ CONSIDER** pomocí identifikátor úplně nový, ale smysluplný místo přidávání příponu nebo předponu.  
  
 **✓ DO** používá číselnou příponou se k označení novou verzi existujícího rozhraní API, zvlášť pokud existující název rozhraní API je pouze název, který dává smysl (tj. Pokud je oborový standard) a Pokud Přidání všechny smysluplný přípony (nebo změna názvu) není aplikace možnost ropriate.  
  
 **X DO NOT** "Ex" (nebo podobná) používat příponu pro identifikátor ho odlišuje od dřívější verzi rozhraní API stejné.  
  
 **✓ DO** používají "64" příponu zaváděné verze rozhraní API, která pracovat 64bitové celé číslo (dlouhých celých čísel) namísto 32bitové celé číslo. Budete muset provést tento postup, pokud existuje stávající rozhraní API 32-bit; Neprovádějte to pro úplně nová rozhraní API s 64bitovou verzi.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
- [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)

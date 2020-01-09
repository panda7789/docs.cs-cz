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
ms.openlocfilehash: d1b01fac7368ffeceb554c6f12aecb8f8760fa1d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709332"
---
# <a name="general-naming-conventions"></a>Obecné konvence pojmenování
Tato část popisuje obecné konvence vytváření názvů, které se týkají volby Wordu, pokyny k používání zkratky a zkratek a doporučení, jak se vyhnout použití názvů specifických pro jazyk.  
  
## <a name="word-choice"></a>Volba Wordu  
 **✓ DO** zvolte snadno čitelné identifikátor názvy.  
  
 Například vlastnost s názvem `HorizontalAlignment` je více než `AlignmentHorizontal`čitelná pro angličtinu.  
  
 **✓ DO** upřednostnit čitelnost přes jako stručný výtah.  
  
 Název vlastnosti `CanScrollHorizontally` je lepší než `ScrollableX` (překrytí odkazem na osu X).  
  
 **X DO NOT** použít podtržítka, pomlčky nebo jiné nealfanumerické znaky.  
  
 **X DO NOT** použijte Maďarská zápis.  
  
 **X AVOID** pomocí identifikátorů, které je v konfliktu s slov široce používá programovací jazyky.  
  
 V souladu s pravidlem 4 specifikace CLS (Common Language Specification) musí všechny vyhovující jazyky poskytovat mechanismus, který umožňuje přístup k pojmenovaným položkám, které používají klíčové slovo tohoto jazyka jako identifikátor. C#například používá @ Sign jako řídicí mechanismus v tomto případě. Je však stále vhodné se vyhnout běžným klíčovým slovům, protože je mnohem obtížnější použít metodu s řídicí sekvencí, než je ta bez ní.  
  
## <a name="using-abbreviations-and-acronyms"></a>Používání zkratek a zkratek  
 **X DO NOT** použít zkratky nebo staženiny jako součást identifikátoru názvy.  
  
 Použijte například `GetWindow` místo `GetWin`.  
  
 **X DO NOT** žádné režim, které nejsou široce používaný a to i v případě, že jsou pouze v případě, že je nutné použít.  
  
## <a name="avoiding-language-specific-names"></a>Vyloučení názvů specifických pro jazyk  
 **✓ DO** používá sémanticky zajímavé názvy namísto klíčová slova specifická pro jazyk pro názvy typů.  
  
 `GetLength` je například lepší název než `GetInt`.  
  
 **✓ DO** použít obecný název typu CLR, nikoli název konkrétní jazyk, ve výjimečných případech, pokud identifikátor nemá význam sémantického nad rámec jeho typu.  
  
 Například metoda převodu na <xref:System.Int64> by měla být pojmenována `ToInt64`, nikoli `ToLong` (protože <xref:System.Int64> je název CLR pro alias specifický C#pro `long`). Následující tabulka uvádí několik základních datových typů pomocí názvů typů CLR (a také odpovídajících názvů typů pro C#, Visual Basic a C++).  
  
|C#|Visual Basic|C++|CLR|  
|---------|------------------|-----------|---------|  
|**sbyte**|**SByte**|**char**|**SByte**|  
|**byte**|**Bytové**|**znak bez znaménka**|**Bytové**|  
|**short**|**Dostatečná**|**short**|**Int16**|  
|**ushort**|**UInt16**|**krátký unsigned**|**UInt16**|  
|**int**|**Celé číslo**|**int**|**Int32**|  
|**uint**|**UInt32**|**unsigned int**|**UInt32**|  
|**long**|**Dlouhou**|**__int64**|**Int64**|  
|**ulong**|**UInt64**|**Nepodepsaný __int64**|**UInt64**|  
|**float**|**Konkrétní**|**float**|**Konkrétní**|  
|**double**|**Klepat**|**double**|**Klepat**|  
|**bool**|**Datový typ Boolean**|**bool**|**Datový typ Boolean**|  
|**char**|**Char**|**wchar_t**|**Char**|  
|**string**|**Řetězec**|**Řetězec**|**Řetězec**|  
|**object**|**objekt**|**objekt**|**objekt**|  
  
 **✓ DO** použít běžný název, například `value` nebo `item`, místo opakování název typu ve výjimečných případech, pokud identifikátor nemá žádný význam sémantického a typ parametru není důležité.  
  
## <a name="naming-new-versions-of-existing-apis"></a>Pojmenovávání nových verzí stávajících rozhraní API  
 **✓ DO** použijte název podobná staré rozhraní API, při vytváření nové verze existujícího rozhraní API.  
  
 Tato možnost pomáhá zdůraznit vztah mezi rozhraními API.  
  
 **✓ DO** přednost přidání příponu místo předpony označující novou verzi existujícího rozhraní API.  
  
 To vám pomůže se zjišťováním při procházení dokumentace nebo pomocí technologie IntelliSense. Stará verze rozhraní API bude uspořádána blízko nových rozhraní API, protože většina prohlížečů a IntelliSense zobrazuje identifikátory v abecedním pořadí.  
  
 **✓ CONSIDER** pomocí identifikátor úplně nový, ale smysluplný místo přidávání příponu nebo předponu.  
  
 **✓ DO** používá číselnou příponou se k označení novou verzi existujícího rozhraní API, zvlášť pokud existující název rozhraní API je pouze název, který dává smysl (tj. Pokud je oborový standard) a Pokud Přidání všechny smysluplný přípony (nebo změna názvu) není aplikace možnost ropriate.  
  
 **X DO NOT** "Ex" (nebo podobná) používat příponu pro identifikátor ho odlišuje od dřívější verzi rozhraní API stejné.  
  
 **✓ DO** používají "64" příponu zaváděné verze rozhraní API, která pracovat 64bitové celé číslo (dlouhých celých čísel) namísto 32bitové celé číslo. Tento přístup je potřeba vzít jenom v případě, že existující rozhraní API pro 32 existuje. Neprovádějte ji pro nové rozhraní API pro novou značku s pouze 64 verzí.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)

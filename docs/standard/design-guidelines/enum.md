---
title: Návrh výčtu
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
author: KrzysztofCwalina
ms.openlocfilehash: 429f2e3821ff12ff4fc51b73c102ee3799d0228d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148129"
---
# <a name="enum-design"></a>Návrh výčtu
Výčty jsou zvláštní druh typu hodnoty. Existují dva typy výčtů: jednoduchý, výčty a příznak výčty.  
  
 Jednoduché výčty představují malé uzavřených sad možností. Běžným příkladem jednoduché výčtu je sada barev.  
  
 Příznak výčty jsou navrženy pro podporu bitové operace s hodnotami výčtu. Běžným příkladem výčet příznaků je seznam možností.  
  
 **✓ DO** pomocí výčet parametry, vlastnosti, silného typu a návratové hodnoty, které představují sadu hodnot.  
  
 **✓ DO** upřednostnit pomocí výčet místo statické konstanty.  
  
 **X DO NOT** používat výčet pro otevřené sady (například verzi operačního systému, názvy přátel, atd.).  
  
 **X DO NOT** poskytují vyhrazené výčet hodnot, které jsou určené pro budoucí použití.  
  
 V pozdější fázi můžete vždy jednoduše přidejte hodnoty pro existující výčet. Zobrazit [přidání hodnoty výčty](#add_value) podrobné informace o přidání hodnot do výčty. Vyhrazené hodnoty stačí znečištění směrovány správu sadu skutečných hodnot a vede k chybám uživatelů.  
  
 **X AVOID** veřejně vystavení výčty pomocí pouze jednu hodnotu.  
  
 Běžnou praxí pro zajištění budoucí rozšíření rozhraní API jazyka C je přidání vyhrazené parametry podpisy metod. Tyto parametry vyhrazené může být vyjádřený jako výčty pomocí jedno výchozí hodnotu. To by neměl být spravovaných rozhraní API. Metoda přetížení umožňuje přidávání parametrů v budoucích vezích se.  
  
 **X DO NOT** zahrnout sentinel hodnoty výčty.  
  
 I když jsou někdy užitečné pro vývojáře rozhraní framework, sentinel hodnoty jsou matoucí pro uživatele tohoto rozhraní. Používají se ke sledování stavu je jedna z hodnot výčtu spíše než ze sady reprezentována výčtového typu.  
  
 **✓ DO** zadejte hodnotu nula na jednoduchý výčty.  
  
 Zvažte možnost volání hodnotu něco jako "None". Pokud taková hodnota není vhodná pro tento konkrétní výčet, měla být přiřazena základní hodnotou nula nejběžnější výchozí hodnota pro výčet.  
  
 **✓ CONSIDER** pomocí <xref:System.Int32> (výchozí ve většině programovacích jazycích) jako nadřazený typ enum Pokud žádné z následujících:  
  
-   Výčet je výčet příznaků a máte více než 32 příznaky, nebo chcete mít více v budoucnu.  
  
-   Základní typ musí být jiná než <xref:System.Int32> jednodušší spolupráce s nespravovaným kódem očekává jinou velikost výčty.  
  
-   Výsledkem by bylo menší základní typ značné úspory v prostoru. Pokud očekáváte, že výčtu použije hlavně jako argument pro tok řízení, velikost provede malý rozdíl. Úspora velikosti může být významné pokud:  
  
    -   Očekáváte, že se použije jako pole instance velmi často struktury nebo třídy výčtu.  
  
    -   Očekáváte, že uživatelům vytvořit velké pole nebo kolekce výčet instancí.  
  
    -   Očekáváte velký počet instancí výčtového typu se musí serializovat.  
  
 Pro použití v paměti, mějte na paměti, že spravované objekty budou vždy `DWORD`-zarovnané, tak efektivně potřebujete více výčty nebo jiných malých struktury v instanci se zabalit menší výčet s aby rozdíl, protože velikost celkový počet instancí je vždy má zaokrouhlí `DWORD`.  
  
 **✓ DO** název příznak výčty pomocí množném čísle podstatná jména či fráze podstatné jméno a jednoduchý výčty pomocí singulární podstatná jména či fráze podstatné jméno.  
  
 **X DO NOT** rozšířit <xref:System.Enum?displayProperty=nameWithType> přímo.  
  
 <xref:System.Enum?displayProperty=nameWithType> je speciální typ používá modul CLR k vytvoření uživatelem definované výčty. Většina programovacích jazyků poskytují programový element, který poskytuje přístup k této funkci. Například v jazyce C# `enum` – klíčové slovo se používá k definování výčtu.  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a>Navrhování příznak výčty  
 **✓ DO** použít <xref:System.FlagsAttribute?displayProperty=nameWithType> na příznak výčty. Tento atribut nevztahují na jednoduché výčty.  
  
 **✓ DO** použít zajišťuje dva pro hodnoty výčtu příznak, mohou být volně kombinovány pomocí bitové operace OR.  
  
 **✓ CONSIDER** poskytování hodnot speciální výčtu pro běžně používá kombinace příznaků.  
  
 Bitové operace jsou rozšířené koncept a by neměla být zapotřebí pro jednoduché úlohy. <xref:System.IO.FileAccess.ReadWrite> je příkladem zvláštní hodnota.  
  
 **X AVOID** vytváření výčtů příznak, kde jsou neplatné určité kombinace hodnot.  
  
 **X AVOID** pomocí příznak hodnoty výčtu nula, pokud hodnota představuje "všechny příznaky jsou vymazány" a je správně podle další obecné zásady s názvem.  
  
 **✓ DO** název nulové hodnoty příznak výčtů `None`. Příznak výčtu musí hodnota vždy znamená "všechny příznaky jsou vymazány."  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a>Přínos pro výčty  
 Je velmi běžné ke zjištění, že budete muset přidat hodnoty výčtu, poté, co jste už už vydali. Je potenciální problémy s kompatibilitou aplikací po je nově přidaná hodnota vrácená z existujícího rozhraní API, protože špatně vytvořené aplikace nemusí správně zpracovávat nové hodnoty.  
  
 **✓ CONSIDER** přidání hodnot do výčty navzdory riziko malé kompatibility.  
  
 Pokud máte reálná data o nekompatibility aplikací způsobené dodatky na výčet, zvažte přidání nového rozhraní API, který vrací hodnoty novém i starém a vyřazení staré rozhraní API, které by měly pokračovat ve vrací pouze původní hodnoty. Tím se zajistí, že zůstane svoje stávající aplikace kompatibilní.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)  
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)

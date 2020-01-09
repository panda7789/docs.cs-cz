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
ms.openlocfilehash: 130e9b4e7f8d7076d1dc3f21f51dc07a68799bbe
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709449"
---
# <a name="enum-design"></a>Návrh výčtu

Výčty jsou speciálním druhem hodnotového typu. Existují dva druhy výčtů: jednoduché výčty a výčty příznaku.

Jednoduché výčty reprezentují malé uzavřené sady možností. Běžným příkladem jednoduchého výčtu je sada barev.

Výčty příznaků jsou navržené tak, aby podporovaly bitové operace s hodnotami výčtu. Běžným příkladem výčtu příznaků je seznam možností.

**✓ DO** pomocí výčet parametry, vlastnosti, silného typu a návratové hodnoty, které představují sadu hodnot.

**✓ DO** upřednostnit pomocí výčet místo statické konstanty.

**X DO NOT** používat výčet pro otevřené sady (například verzi operačního systému, názvy přátel, atd.).

**X DO NOT** poskytují vyhrazené výčet hodnot, které jsou určené pro budoucí použití.

V pozdější fázi můžete kdykoli jednoduše přidat hodnoty do stávajícího výčtu. Další podrobnosti o přidávání hodnot do výčtů naleznete v tématu [Přidání hodnot do výčtů](#add_value) . Rezervované hodnoty jenom zneznečišťující sadu skutečných hodnot a mají za následek chyby uživatelů.

**X AVOID** veřejně vystavení výčty pomocí pouze jednu hodnotu.

Běžný postup pro zajištění budoucí rozšiřitelnosti rozhraní API jazyka C je přidání rezervovaných parametrů k podpisům metod. Tyto vyhrazené parametry lze vyjádřit jako výčty s jednou výchozí hodnotou. To by nemělo být provedeno ve spravovaných rozhraních API. Přetížení metody umožňuje přidávání parametrů v budoucích verzích.

**X DO NOT** zahrnout sentinel hodnoty výčty.

I když jsou někdy užitečné pro vývojáře architektury, hodnoty Sentinel jsou pro uživatele rozhraní matoucí. Používají se ke sledování stavu výčtu, nikoli k jedné z hodnot ze sady reprezentované výčtem.

**✓ DO** zadejte hodnotu nula na jednoduchý výčty.

Zvažte volání hodnoty jako "none". Pokud taková hodnota není vhodná pro tento konkrétní výčet, měla by být většině běžných výchozích hodnot výčtu přiřazena základní hodnota nula.

**✓ CONSIDER** pomocí <xref:System.Int32> (výchozí ve většině programovacích jazycích) jako nadřazený typ enum Pokud žádné z následujících:

- Výčtový typ je výčet příznaků a máte více než 32 příznaků nebo v budoucnu očekávat větší hodnotu.

- Podkladový typ musí být jiný než <xref:System.Int32> pro snazší interoperabilitu s nespravovaným kódem očekává v různých velikostech výčty.

- Menší nadřízený typ by způsobil značnou úsporu místa. Pokud očekáváte, že se má výčet použít hlavně jako argument pro tok řízení, velikost bude mít malý rozdíl. Úspora velikosti může být významná v těchto případech:

  - Očekáváte, že se výčet použije jako pole ve velmi často se instanci struktury nebo třídy.

  - Očekáváte, že uživatelé budou vytvářet velká pole nebo kolekce instancí výčtu.

  - Očekáváte, že se má serializovat velký počet instancí výčtu.

V případě využití v paměti si uvědomte, že spravované objekty jsou vždycky `DWORD`zarovnané, takže v instanci efektivně potřebujete víc výčtů nebo jiných malých struktur, aby bylo možné vytvořit rozdíl, protože celková velikost instance se vždycky zaokrouhluje na `DWORD`.

**✓ DO** název příznak výčty pomocí množném čísle podstatná jména či fráze podstatné jméno a jednoduchý výčty pomocí singulární podstatná jména či fráze podstatné jméno.

**X DO NOT** rozšířit <xref:System.Enum?displayProperty=nameWithType> přímo.

<xref:System.Enum?displayProperty=nameWithType> je speciální typ používaný modulem CLR k vytváření výčtů definovaných uživatelem. Většina programovacích jazyků poskytuje programovací prvek, který vám dává přístup k této funkci. Například v C# klíčovém slově `enum` slouží k definování výčtu.

<a name="design"></a>

### <a name="designing-flag-enums"></a>Navrhování výčtů příznaků

**✓ DO** použít <xref:System.FlagsAttribute?displayProperty=nameWithType> na příznak výčty. Nepoužívejte tento atribut pro jednoduché výčty.

**✓ DO** použít zajišťuje dva pro hodnoty výčtu příznak, mohou být volně kombinovány pomocí bitové operace OR.

**✓ CONSIDER** poskytování hodnot speciální výčtu pro běžně používá kombinace příznaků.

Bitové operace jsou pokročilým konceptem a neměly by se vyžadovat pro jednoduché úlohy. <xref:System.IO.FileAccess.ReadWrite> je příkladem takové speciální hodnoty.

**X AVOID** vytváření výčtů příznak, kde jsou neplatné určité kombinace hodnot.

**X AVOID** pomocí příznak hodnoty výčtu nula, pokud hodnota představuje "všechny příznaky jsou vymazány" a je správně podle další obecné zásady s názvem.

**✓ DO** název nulové hodnoty příznak výčtů `None`. U výčtu příznaků hodnota musí vždy znamenat "všechny příznaky jsou vymazány".

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a>Přidání hodnoty do výčtů

Je velmi běžné zjistit, že je třeba přidat hodnoty do výčtu po jeho odeslání. Při vrácení nově přidané hodnoty z existujícího rozhraní API dojde k potenciálnímu problému s kompatibilitou aplikací, protože špatně zapsané aplikace nemusí správně zpracovat novou hodnotu.

**✓ CONSIDER** přidání hodnot do výčty navzdory riziko malé kompatibility.

Pokud máte skutečná data týkající se nekompatibility aplikací způsobená přídavky výčtu, zvažte přidání nového rozhraní API, které vrátí nové a staré hodnoty, a vyřadí staré rozhraní API, které by mělo pokračovat v vracení pouze starých hodnot. Tím zajistíte, že vaše existující aplikace budou kompatibilní.

*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)

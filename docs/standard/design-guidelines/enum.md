---
title: Návrh výčtu
description: Návrh pro výčty, které jsou zvláštním druhem hodnotového typu. Jednoduché výčty uchovávají malé, uzavřené sady možností. Výčty označení podporují bitové operace s hodnotami výčtu.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
ms.openlocfilehash: 40a9faf53dc8a03674cd59074244c15cd304bdd2
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768534"
---
# <a name="enum-design"></a>Návrh výčtu

Výčty jsou speciálním druhem hodnotového typu. Existují dva druhy výčtů: jednoduché výčty a výčty příznaku.

Jednoduché výčty reprezentují malé uzavřené sady možností. Běžným příkladem jednoduchého výčtu je sada barev.

Výčty příznaků jsou navržené tak, aby podporovaly bitové operace s hodnotami výčtu. Běžným příkladem výčtu příznaků je seznam možností.

✔️ použít výčet pro silné typy parametrů, vlastnosti a návratové hodnoty, které reprezentují sady hodnot.

✔️ preferovat pomocí výčtu místo statických konstant.

❌Nepoužívejte výčet pro otevřené sady (například verzi operačního systému, názvy vašich přátel atd.).

❌Neposkytněte hodnoty rezervovaných výčtů, které jsou určeny pro budoucí použití.

V pozdější fázi můžete kdykoli jednoduše přidat hodnoty do stávajícího výčtu. Další podrobnosti o přidávání hodnot do výčtů naleznete v tématu [Přidání hodnot do výčtů](#add_value) . Rezervované hodnoty jenom zneznečišťující sadu skutečných hodnot a mají za následek chyby uživatelů.

❌Vyhněte se veřejně vystavování výčtů pouze s jednou hodnotou.

Běžný postup pro zajištění budoucí rozšiřitelnosti rozhraní API jazyka C je přidání rezervovaných parametrů k podpisům metod. Tyto vyhrazené parametry lze vyjádřit jako výčty s jednou výchozí hodnotou. To by nemělo být provedeno ve spravovaných rozhraních API. Přetížení metody umožňuje přidávání parametrů v budoucích verzích.

❌Nezahrnujte hodnoty Sentinel do výčtů.

I když jsou někdy užitečné pro vývojáře architektury, hodnoty Sentinel jsou pro uživatele rozhraní matoucí. Používají se ke sledování stavu výčtu, nikoli k jedné z hodnot ze sady reprezentované výčtem.

✔️ pro jednoduché výčty zadejte hodnotu nula.

Zvažte volání hodnoty jako "none". Pokud taková hodnota není vhodná pro tento konkrétní výčet, měla by být většině běžných výchozích hodnot výčtu přiřazena základní hodnota nula.

✔️ Zvažte použití <xref:System.Int32> (výchozí ve většině programovacích jazyků) jako podkladový typ výčtu, pokud není splněna některá z následujících podmínek:

- Výčtový typ je výčet příznaků a máte více než 32 příznaků nebo v budoucnu očekávat větší hodnotu.

- Podkladový typ musí být jiný než <xref:System.Int32> pro snazší interoperabilitu s nespravovaným kódem, který očekává různé velikosti výčtů.

- Menší nadřízený typ by způsobil značnou úsporu místa. Pokud očekáváte, že se má výčet použít hlavně jako argument pro tok řízení, velikost bude mít malý rozdíl. Úspora velikosti může být významná v těchto případech:

  - Očekáváte, že se výčet použije jako pole ve velmi často se instanci struktury nebo třídy.

  - Očekáváte, že uživatelé budou vytvářet velká pole nebo kolekce instancí výčtu.

  - Očekáváte, že se má serializovat velký počet instancí výčtu.

V případě využití paměti je třeba si uvědomit, že jsou spravované objekty vždycky `DWORD` zarovnané, takže budete v instanci efektivně potřebovat více výčtů nebo jiných malých struktur, aby bylo možné provést rozdíl, protože celková velikost instance se vždycky zaokrouhluje na `DWORD` .

✔️ DO názvů označovat výčty s podstatnými jmény v množném číslech nebo frázemi podstatných jmen a jednoduchými výčty s podstatnými jmény a větami

❌Nešíří se <xref:System.Enum?displayProperty=nameWithType> přímo.

<xref:System.Enum?displayProperty=nameWithType>je speciální typ používaný modulem CLR k vytváření výčtů definovaných uživatelem. Většina programovacích jazyků poskytuje programovací prvek, který vám dává přístup k této funkci. Například v jazyce C# se `enum` klíčové slovo používá k definování výčtu.

<a name="design"></a>

### <a name="designing-flag-enums"></a>Navrhování výčtů příznaků

✔️ použít <xref:System.FlagsAttribute?displayProperty=nameWithType> pro označení výčty. Nepoužívejte tento atribut pro jednoduché výčty.

✔️ pro hodnoty výčtu příznaků použít mocniny dvou, aby bylo možné volně kombinovat pomocí bitové operace OR.

✔️ Zvažte poskytování speciálních hodnot výčtu pro běžně používané kombinace příznaků.

Bitové operace jsou pokročilým konceptem a neměly by se vyžadovat pro jednoduché úlohy. <xref:System.IO.FileAccess.ReadWrite>je příkladem takové speciální hodnoty.

❌Vyhněte se vytváření výčtů příznaků, kde jsou určité kombinace hodnot neplatné.

❌Vyhněte se použití hodnot výčtu příznak nula, pokud hodnota nepředstavuje "všechny příznaky jsou vymazány" a je pojmenována správně, jak je předepsáno v další části.

✔️ pojmenovat nulovou hodnotu výčtů příznaků `None` . U výčtu příznaků hodnota musí vždy znamenat "všechny příznaky jsou vymazány".

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a>Přidání hodnoty do výčtů

Je velmi běžné zjistit, že je třeba přidat hodnoty do výčtu po jeho odeslání. Při vrácení nově přidané hodnoty z existujícího rozhraní API dojde k potenciálnímu problému s kompatibilitou aplikací, protože špatně zapsané aplikace nemusí správně zpracovat novou hodnotu.

✔️ Zvažte přidání hodnot do výčtů bez ohledu na malé riziko kompatibility.

Pokud máte skutečná data týkající se nekompatibility aplikací způsobená přídavky výčtu, zvažte přidání nového rozhraní API, které vrátí nové a staré hodnoty, a vyřadí staré rozhraní API, které by mělo pokračovat v vracení pouze starých hodnot. Tím zajistíte, že vaše existující aplikace budou kompatibilní.

*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny pro návrh typů](type.md)
- [Pokyny k návrhu architektury](index.md)

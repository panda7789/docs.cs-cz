---
title: Návrh s typy odkazů s možnou hodnotou null
description: Tento rozšířený kurz poskytuje úvod do typů odkazů s možnou hodnotou null. Naučíte se vyjádřit záměr návrhu, když referenční hodnoty mohou být nulové, a mít kompilátor vynucovat, když nemohou být null.
ms.date: 02/19/2019
ms.technology: csharp-null-safety
ms.custom: mvc
ms.openlocfilehash: b00050c1d151b95e330f94eb9393a4031e47d5a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240064"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a>Kurz: Vyjádřete svůj záměr návrhu jasněji s typy odkazů s možnou a nulovou hodnotou.

C# 8.0 zavádí [typy odkazů s možnou hodnotou null](../nullable-references.md), které doplňují typy odkazů stejným způsobem, jakým jsou typy hodnot typu hodnot s možnou hodnotou null. Deklarujete proměnnou jako **typ odkazu s možnou hodnotou null** připojením typu a. `?` Například `string?` představuje hodnotu `string`nullable . Tyto nové typy můžete použít k jasněji vyjádřit záměr návrhu: některé proměnné *musí mít vždy hodnotu*, jiné *mohou chybět hodnotu*.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> - Začleňte do svých návrhů typy odkazů s možnou hodnotou null a nenulovatelné
> - Povolte kontroly typu odkazu s možnou hodnotou null v celém kódu.
> - Napište kód, kde kompilátor vynucuje tato rozhodnutí o návrhu.
> - Použití referenční funkce s možnou hodnotou null ve vlastních návrzích

## <a name="prerequisites"></a>Požadavky

Budete muset nastavit počítač pro spuštění .NET Core, včetně kompilátoru C# 8.0. Kompilátor Jazyka C# 8.0 je k dispozici v [sadě Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)nebo [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

Tento kurz předpokládá, že jste obeznámeni s C# a .NET, včetně Visual Studio nebo .NET Core CLI.

## <a name="incorporate-nullable-reference-types-into-your-designs"></a>Začleňte do svých návrhů typy odkazů s možnou hodnotou null

V tomto kurzu vytvoříte knihovnu, která modeluje spuštění průzkumu. Kód používá typy odkazů s možnou hodnotou null a typy odkazů s nulovou hodnotou, které představují koncepty reálného světa. Otázky průzkumu nemůže být nikdy null. Respondent by raději neodpověděl na otázku. Odpovědi mohou být `null` v tomto případě.

Kód, který budete psát pro tuto ukázku vyjadřuje tento záměr a kompilátor vynucuje tento záměr.

## <a name="create-the-application-and-enable-nullable-reference-types"></a>Vytvoření aplikace a povolení typů odkazů s možnou hodnotou null

Vytvořte novou konzolovou aplikaci v sadě `dotnet new console`Visual Studio nebo z příkazového řádku pomocí aplikace . Pojmenujte `NullableIntroduction`aplikaci . Po vytvoření aplikace budete muset určit, že celý projekt se zkompiluje v povoleném **kontextu poznámky s možnou hodnotou null**. Otevřete soubor *.csproj* `Nullable` a přidejte prvek do `PropertyGroup` prvku. Nastavte její hodnotu na `enable`. Musíte se přihlásit do funkce **typu odkazu s možnou hodnotou null,** a to i v projektech jazyka C# 8.0. Je to proto, že jakmile je funkce zapnuta, existující deklarace referenčních proměnných se stanou **typy odkazů s možnou hodnotou null**. I když toto rozhodnutí pomůže najít problémy, kde existující kód nemusí mít správné kontroly null, nemusí přesně odrážet původní záměr návrhu:

```xml
<Nullable>enable</Nullable>
```

### <a name="design-the-types-for-the-application"></a>Navrhněte typy pro aplikaci

Tato aplikace průzkumu vyžaduje vytvoření několika tříd:

- Třída, která modeluje seznam otázek.
- Třída, která modeluje seznam osob kontaktovaných pro průzkum.
- Třída, která modeluje odpovědi od osoby, která provedla průzkum.

Tyto typy budou používat nullable a nenulelné typy odkazů vyjádřit, které členy jsou požadovány a které členy jsou volitelné. Typy odkazů s možnou hodnotou Null jasně sdělují záměr návrhu:

- Otázky, které jsou součástí průzkumu, nemohou být nikdy nulové: Nemá smysl klást prázdnou otázku.
- Respondenti nemohou být nikdy null. Budete chtít sledovat lidi, které jste kontaktovali, dokonce i respondenty, kteří se odmítli zúčastnit.
- Odpověď na otázku může být null. Respondenti mohou odmítnout odpovědět na některé nebo všechny otázky.

Pokud jste naprogramovali v c#, můžete být tak zvyklí na referenční typy, které umožňují `null` hodnoty, které jste možná vynechali další příležitosti k deklarování instancí s možnou hodnotou null:

- Kolekce otázek by měla být nenulovatelná.
- Kolekce respondentů by měla být nenulovatelná.

Při psaní kódu uvidíte, že typ odkazu s možnou nemožnou hodnotou null jako <xref:System.NullReferenceException>výchozí pro odkazy zabraňuje běžným chybám, které by mohly vést k s. Jedna lekce z tohoto kurzu je, že jste se rozhodli `null`o tom, které proměnné by mohly nebo nemohly být . Jazyk neposkytl syntaxi pro vyjádření těchto rozhodnutí. Teď už ano.

Aplikace, kterou vytvoříte, provede následující kroky:

1. Vytvoří průzkum a přidá k němu otázky.
1. Vytvoří pseudonáhodnou sadu respondentů pro průzkum.
1. Kontaktuje respondenty, dokud velikost dokončeného průzkumu nedosáhne čísla cíle.
1. Zapíše důležité statistiky o odpovědích na průzkum.

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a>Sestavení průzkumu s typy s možnou hodnotou null a nenulovatelné

První kód, který napíšete, vytvoří průzkum. Budete psát třídy pro modelování otázky průzkumu a spuštění průzkumu. Průzkum má tři typy otázek, které se vyznačují formátem odpovědi: Ano/Ne odpovědi, počet odpovědí a textové odpovědi. Vytvořte `public SurveyQuestion` třídu:

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

Kompilátor interpretuje každou deklaraci proměnné typu odkazu jako typ odkazu **s hodnotou neshodnou hodnotu null** pro kód v povoleném kontextu poznámky s možnou hodnotou null. První upozornění zobrazíte přidáním vlastností textu otázky a typu otázky, jak je znázorněno v následujícím kódu:

```csharp
namespace NullableIntroduction
{
    public enum QuestionType
    {
        YesNo,
        Number,
        Text
    }

    public class SurveyQuestion
    {
        public string QuestionText { get; }
        public QuestionType TypeOfQuestion { get; }
    }
}
```

Protože jste se neinicializovali `QuestionText`, kompilátor vydá upozornění, že vlastnost, kterou nelze utvarovat jako nenulovatelná, nebyla inicializována. Váš návrh vyžaduje, aby text otázky byl nenulový, takže přidáte konstruktor pro jeho inicializaci a také hodnotu. `QuestionType` Definice dokončené třídy vypadá takto:

[!code-csharp[DefineQuestion](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

Přidání konstruktoru odebere upozornění. Argument konstruktoru je také typ odkazu s možnou hodnotou null, takže kompilátor nevydává žádná upozornění.

Dále vytvořte `public` třídu s názvem `SurveyRun`. Tato třída obsahuje `SurveyQuestion` seznam objektů a metod pro přidání otázek do průzkumu, jak je znázorněno v následujícím kódu:

```csharp
using System.Collections.Generic;

namespace NullableIntroduction
{
    public class SurveyRun
    {
        private List<SurveyQuestion> surveyQuestions = new List<SurveyQuestion>();

        public void AddQuestion(QuestionType type, string question) =>
            AddQuestion(new SurveyQuestion(type, question));
        public void AddQuestion(SurveyQuestion surveyQuestion) => surveyQuestions.Add(surveyQuestion);
    }
}
```

Stejně jako dříve je nutné inicializovat objekt seznamu na hodnotu bez null nebo kompilátor vydá upozornění. Neexistují žádné kontroly null v `AddQuestion` druhé přetížení, protože nejsou potřeba: Jste deklarovali, že proměnná je nenulovatelný. Jeho hodnota nemůže `null`být .

Přepněte do *Program.cs* v editoru `Main` a nahraďte obsah následujících řádků kódu:

[!code-csharp[AddQuestions](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

Vzhledem k tomu, že celý projekt je v povoleném kontextu `null` poznámky s možnou hodnotou null, zobrazí se upozornění při předání libovolné metody, která očekává typ odkazu s možnou hodnotou null. Zkuste to přidáním následujícího řádku do `Main`:

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a>Vytváření respondentů a získání odpovědí na průzkum

Dále napište kód, který generuje odpovědi na průzkum. Tento proces zahrnuje několik malých úkolů:

1. Vytvořte metodu, která generuje objekty respondentu. Tito představují lidi, kteří byli požádáni o vyplnění průzkumu.
1. Vytvořte logiku, která simuluje kladení otázek respondentovi a shromažďování odpovědí nebo konstatování, že respondent neodpověděl.
1. Opakujte, dokud na průzkum neodpoví dostatek respondentů.

Budete potřebovat třídu, která bude reprezentovat odpověď na průzkum, takže ji přidejte nyní. Povolte podporu, jejíž hodnotu lze uznat jako null. Přidejte `Id` vlastnost a konstruktor, který ji inicializuje, jak je znázorněno v následujícím kódu:

```csharp
namespace NullableIntroduction
{
    public class SurveyResponse
    {
        public int Id { get; }

        public SurveyResponse(int id) => Id = id;
    }
}
```

Dále přidejte `static` metodu pro vytvoření nových účastníků generováním náhodného ID:

[!code-csharp[GenerateRespondents](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

Hlavní odpovědností této třídy je generovat odpovědi pro účastníka na otázky v průzkumu. Tato odpovědnost má několik kroků:

1. Požádejte o účast v průzkumu. Pokud osoba nesouhlasí, vrátí chybějící (nebo nulovou) odpověď.
1. Zeptejte se na každou otázku a zaznamenejte odpověď. Každá odpověď může také chybět (nebo null).

Přidejte do třídy `SurveyResponse` následující kód:

[!code-csharp[AnswerSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

Úložiště pro odpovědi průzkumu `Dictionary<int, string>?`je , označující, že může být null. Používáte novou funkci jazyka k deklarování záměru návrhu, a to jak kompilátoru, tak komukoli, kdo váš kód čte později. Pokud jste někdy `surveyResponses` dereference bez `null` kontroly hodnoty jako první, dostanete upozornění kompilátoru. Nedostanete upozornění v metodě, `AnswerSurvey` protože kompilátor `surveyResponses` může určit, že proměnná byla nastavena na hodnotu nenulovou výše.

Použití `null` pro chybějící odpovědi zvýrazní klíčový bod pro práci s typy odkazů `null` s možnou hodnotou null: vaším cílem není odebrat všechny hodnoty z programu. Spíše vaším cílem je zajistit, aby kód, který píšete vyjadřuje záměr vašeho návrhu. Chybějící hodnoty jsou nezbytné koncept vyjádřit ve vašem kódu. Hodnota `null` je jasný způsob, jak vyjádřit tyto chybějící hodnoty. Pokus o `null` odebrání všech hodnot vede pouze k definování jiného způsobu vyjádření těchto chybějících hodnot bez `null`.

Dále musíte napsat metodu `PerformSurvey` ve `SurveyRun` třídě. Do `SurveyRun` třídy přidejte následující kód:

[!code-csharp[PerformSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

Zde opět vaše volba nullable `List<SurveyResponse>?` označuje odpověď může být null. To znamená, že průzkum ještě nebyl poskytnut žádnému respondentovi. Všimněte si, že respondenti jsou přidány, dokud dostatek souhlasu.

Posledním krokem ke spuštění průzkumu je přidání volání k provedení `Main` průzkumu na konci metody:

[!code-csharp[RunSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a>Prozkoumat odpovědi na průzkum

Posledním krokem je zobrazení výsledků průzkumu. Přidáte kód do mnoha tříd, které jste napsali. Tento kód ukazuje hodnotu rozlišování nullable a non-nullable reference typy. Začněte přidáním následujících dvou členů `SurveyResponse` s výrazem do třídy:

[!code-csharp[ReportResponses](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

Protože `surveyResponses` je typ odkazu s možnou hodnotou null, jsou nezbytné kontroly null před zrušením odkazování. Metoda `Answer` vrátí řetězec s možnou hodnotou null, takže musíme pokrýt případ chybějící odpovědi pomocí operátoru null-coalescing.

Dále přidejte tyto tři členy s `SurveyRun` výrazem do třídy:

[!code-csharp[ReportResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

Člen `AllParticipants` musí vzít v `respondents` úvahu, že proměnná může být null, ale vrácená hodnota nemůže být null. Pokud změníte tento výraz `??` odebráním a prázdnou sekvenci, která `null` následuje, kompilátor vás upozorní, že metoda může vrátit a její návratový podpis vrátí typ s hodnotou null.

Nakonec přidejte následující smyčku `Main` v dolní části metody:

[!code-csharp[DisplaySurveyResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

Nepotřebujete žádné `null` kontroly v tomto kódu, protože jste navrhli základní rozhraní tak, aby všechny vrátit nenulové typy odkazů.

## <a name="get-the-code"></a>Získání kódu

Můžete získat kód pro hotový kurz z našeho úložiště [vzorků](https://github.com/dotnet/samples) ve složce [csharp/NullableIntroduction.](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction)

Experimentujte změnou deklarací typu mezi typy odkazů s možnou hodnotou null a nenulovatelné. Podívejte se, jak to generuje různá upozornění, abyste `null`náhodou nedereferencili .

## <a name="next-steps"></a>Další kroky

Další informace o migraci existující aplikace pro použití typů odkazů s možnou hodnotou null:
> [!div class="nextstepaction"]
> [Upgrade aplikace na použití typů odkazů s možnou hodnotou null](upgrade-to-nullable-references.md)

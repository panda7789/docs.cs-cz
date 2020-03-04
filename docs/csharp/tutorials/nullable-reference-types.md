---
title: Návrh s použitím typů odkazů s možnou hodnotou null
description: Tento rozšířený kurz poskytuje Úvod k odkazům s možnou hodnotou null. Naučíte se vyjádřit svůj návrh na to, kdy mohou být referenční hodnoty null, a nechat vynutit kompilátor, pokud nesmí mít hodnotu null.
ms.date: 02/19/2019
ms.technology: csharp-null-safety
ms.custom: mvc
ms.openlocfilehash: b00050c1d151b95e330f94eb9393a4031e47d5a8
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240064"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a>Kurz: Seznámení s typem s možnou hodnotou null a odkazy, které neumožňují hodnotu null, je jasné.

C#8,0 zavádí [typy odkazů s možnou hodnotou null](../nullable-references.md), které doplňují odkazy na typy hodnot, které připlňují hodnoty typu s možnou hodnotou null. Deklarujete proměnnou, která bude představovat **typ odkazu s možnou hodnotou null** připojením `?` k typu. `string?` například představuje `string`s možnou hodnotou null. Tyto nové typy můžete použít k přehlednějšímu vyjádření záměru návrhu: některé proměnné *musí mít vždy hodnotu*, jiné *mohou chybět hodnoty*.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> - Zahrnutí typů s možnou hodnotou null a odkazů, které neumožňují hodnotu null, do návrhů
> - Povolí kontrolu typu odkazu s možnou hodnotou null v celém kódu.
> - Napsat kód, kde kompilátor vynutil tato rozhodnutí o návrhu.
> - Použití funkce odkazu s možnou hodnotou null ve vlastních návrzích

## <a name="prerequisites"></a>Předpoklady

Musíte nastavit počítač tak, aby běžel .NET Core, včetně kompilátoru C# 8,0. Kompilátor C# 8,0 je k dispozici v rámci sady [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)nebo [.NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

V tomto kurzu se předpokládá, že C# máte zkušenosti s platformou a .NET, včetně sady Visual Studio nebo .NET Core CLI.

## <a name="incorporate-nullable-reference-types-into-your-designs"></a>Zahrnutí typů odkazů s možnou hodnotou null do vašich návrhů

V tomto kurzu vytvoříte knihovnu, ve které modely spouštějí průzkum. Kód používá odkaz s možnou hodnotou null a odkaz, který nepovoluje hodnotu null, aby představoval koncepty reálného světa. Otázky průzkumu nemohou nikdy mít hodnotu null. Respondent může chtít odpovědět na otázku. V tomto případě mohou být odpovědi `null`.

Kód, který zapíšete pro tuto ukázku, tento záměr vyjádří a kompilátor vynutilí tento záměr.

## <a name="create-the-application-and-enable-nullable-reference-types"></a>Vytvoření aplikace a povolení typů odkazů s možnou hodnotou null

Vytvořte novou konzolovou aplikaci buď v aplikaci Visual Studio, nebo z příkazového řádku pomocí `dotnet new console`. Pojmenujte aplikaci `NullableIntroduction`. Po vytvoření aplikace budete muset určit, že se celý projekt zkompiluje v povoleném **kontextu anotace s možnou hodnotou null**. Otevřete soubor *. csproj* a přidejte `Nullable` element do prvku `PropertyGroup`. Nastavte její hodnotu na `enable`. Je nutné, abyste se přihlásili k funkci **typů odkazů s možnou hodnotou null** , i v C# projektech 8,0. To je proto, že když je funkce zapnutá, existující deklarace referenčních proměnných se stanou odkazy, které neumožňují **hodnotu null**. I když toto rozhodnutí pomůže najít problémy, kdy existující kód nemusí mít správné kontroly hodnoty null, nemusí přesně odrážet původní záměr návrhu:

```xml
<Nullable>enable</Nullable>
```

### <a name="design-the-types-for-the-application"></a>Návrh typů pro aplikaci

Tato aplikace průzkumu vyžaduje vytvoření řady tříd:

- Třída, která modeluje seznam otázek.
- Třída, která modeluje seznam lidí, kteří se na průzkum kontaktovali.
- Třída, která modeluje odpovědi od osoby, která provedla průzkum.

Tyto typy využívají odkaz s možnou hodnotou null a neumožňující použití odkazů, aby vyjádřili, které členy jsou požadovány a které členy jsou nepovinné. Typy odkazů s možnou hodnotou null oznamují, že záměr návrhu je jasný:

- Otázky, které jsou součástí průzkumu, nemůžou mít nikdy hodnotu null: nezáleží na tom, aby se dotazoval na prázdnou otázku.
- Respondenti nikdy nemohou mít hodnotu null. Budete chtít sledovat lidi, ke kterým jste kontaktovali, dokonce i respondenti, kteří se odmítli zúčastnit.
- Každá odpověď na otázku může mít hodnotu null. Respondenti mohou odmítnout odpověď na některé nebo všechny otázky.

Pokud jste pracovali v C#nástroji, možná jste zvyklí na odkazování na typy, které umožňují `null` hodnoty, které jste pravděpodobně vynechali při deklaraci instancí, které neumožňují hodnotu null:

- Kolekce dotazů by neměla mít hodnotu null.
- Kolekce respondentů by neměla mít hodnotu null.

Při psaní kódu uvidíte, že typ odkazu, který neumožňuje hodnotu null jako výchozí pro odkazy, zabraňuje běžným chybám, které by mohly vést k <xref:System.NullReferenceException>s. Jednou z lekcí tohoto kurzu je, že jste provedli rozhodnutí o tom, které proměnné by mohly nebo nemohly být `null`. Jazyk neposkytl syntaxi pro vyjádření těchto rozhodnutí. Teď to dělá.

Aplikace, kterou budete sestavovat, provede následující kroky:

1. Vytvoří průzkum a přidá do něj dotazy.
1. Vytvoří pseudo náhodnou sadu respondentů pro průzkum.
1. Kontaktuje respondenty, dokud velikost dokončeného průzkumu nedosáhne cílového čísla.
1. Zapisuje důležité statistiky odpovědí na průzkum.

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a>Sestavit průzkum s povolenými typy s možnou hodnotou null a bez hodnot null

První kód, který budete psát, vytvoří průzkum. Budete psát třídy pro modelování otázky průzkumu a spuštění průzkumu. Váš průzkum má tři typy dotazů, které jsou odlišené podle formátu odpovědi: ano/ne odpovědi, počet odpovědí a text odpovědi. Vytvořit třídu `public SurveyQuestion`:

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

Kompilátor interpretuje každou deklaraci proměnné typu odkazu jako typ odkazu, **který nepovoluje hodnotu null** , pro kód v aktivovaném kontextu anotace s možnou hodnotou null. Můžete se podívat na vaše první upozornění přidáním vlastností textu otázky a typu otázky, jak je znázorněno v následujícím kódu:

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

Vzhledem k tomu, že jste neinicializoval `QuestionText`, vyvolá kompilátor upozornění, že nedošlo k inicializaci vlastnosti, která není null. Váš návrh vyžaduje, aby text otázky nebyl null, takže přidáte konstruktor, který ho inicializuje, a také hodnotu `QuestionType`. Hotová definice třídy vypadá jako následující kód:

[!code-csharp[DefineQuestion](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

Přidáním konstruktoru se odstraní upozornění. Argument konstruktoru je také typ odkazu, který neumožňuje hodnotu null, takže kompilátor nevydá žádná upozornění.

Dále vytvořte třídu `public` s názvem `SurveyRun`. Tato třída obsahuje seznam `SurveyQuestion` objektů a metod pro přidání otázek do průzkumu, jak je znázorněno v následujícím kódu:

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

Stejně jako předtím je nutné inicializovat objekt seznamu na hodnotu, která není null, nebo kompilátor vydá upozornění. V druhém přetížení `AddQuestion` neexistují žádné kontroly null, protože nejsou potřeba: deklaraci této proměnné nemůžete mít hodnotu null. Její hodnotu nelze `null`.

V editoru přepněte na *program.cs* a nahraďte obsah `Main` následujícími řádky kódu:

[!code-csharp[AddQuestions](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

Vzhledem k tomu, že celý projekt je v povoleném kontextu anotace s možnou hodnotou null, zobrazí se upozornění při předání `null` jakékoli metodě, která očekává typ odkazu, který není null. Zkuste to přidáním následujícího řádku do `Main`:

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a>Vytváření respondentů a získávání odpovědí na průzkum

Potom napíšete kód, který generuje odpovědi na průzkum. Tento proces zahrnuje několik malých úloh:

1. Sestavte metodu, která generuje objekty respondentů. Tyto reprezentace označují, že lidé požádali o vyplnění průzkumu.
1. Logika sestavení pro simulaci dotazů na respondenty a shromažďování odpovědí nebo zaznamenání, že respondent neodpověděl.
1. Opakujte, dokud na průzkum neodpoví dostatek respondentů.

Budete potřebovat třídu, která bude reprezentovat odpověď průzkumu, takže ji přidejte. Povolí podporu s možnou hodnotou null. Přidejte vlastnost `Id` a konstruktor, který ji inicializuje, jak je znázorněno v následujícím kódu:

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

Dále přidejte metodu `static` pro vytvoření nových účastníků vygenerováním náhodného ID:

[!code-csharp[GenerateRespondents](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

Hlavní zodpovědností této třídy je vygenerování odpovědí pro účastníka na otázky v průzkumu. Tato zodpovědnost zahrnuje několik kroků:

1. Zeptejte se na účast v průzkumu. Pokud uživatel nesouhlasí, vrátí odpověď chybějící (nebo null).
1. Položte každou otázku a zaznamenejte odpověď. Každá odpověď může také chybět (nebo mít hodnotu null).

Do své `SurveyResponse` třídy přidejte následující kód:

[!code-csharp[AnswerSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

Úložiště pro odpovědi na průzkum je `Dictionary<int, string>?`, což značí, že může mít hodnotu null. Používáte novou funkci jazyka k deklaraci záměru návrhu, jak pro kompilátor, tak pro každého, kdo váš kód čte, později. Pokud jste někdy ododkazovali `surveyResponses` bez kontroly `null` hodnoty, zobrazí se upozornění kompilátoru. V metodě `AnswerSurvey` nezískáte upozornění, protože kompilátor může určit, že proměnná `surveyResponses` byla nastavena na hodnotu jinou než null.

Použití `null` pro chybějící odpovědi zvýrazní klíčové body pro práci s typy odkazů s možnou hodnotou null: vaším cílem není odebrat všechny `null` hodnoty z programu. Místo toho je vaším cílem zajistit, aby kód, který píšete, vyjadřoval záměr vašeho návrhu. Chybějící hodnoty jsou nezbytným konceptem, který by bylo možné vyjádřit do kódu. Hodnota `null` je jasný způsob, jak vyjádřit chybějící hodnoty. Pokus o odebrání všech hodnot `null` vede jenom k definování nějaký jiný způsob, jak tyto chybějící hodnoty vyjádřit bez `null`.

Dále je nutné zapsat metodu `PerformSurvey` do `SurveyRun` třídy. Do `SurveyRun` třídy přidejte následující kód:

[!code-csharp[PerformSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

Tady můžete znovu vybrat `List<SurveyResponse>?` s možnou hodnotou null a odpověď může mít hodnotu null. To indikuje, že průzkum ještě není předaný žádným respondentům. Všimněte si, že se přidávají respondenti, dokud nepřijdete o dostatek.

Posledním krokem ke spuštění průzkumu je přidání volání pro provedení průzkumu na konci `Main` metody:

[!code-csharp[RunSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a>Kontrola odpovědí na průzkum

Posledním krokem je zobrazení výsledků průzkumu. Přidáte kód do mnoha tříd, které jste napsali. Tento kód ukazuje hodnotu rozlišující typy s možnou hodnotou null a odkazy, které neumožňují hodnotu null. Začněte přidáním následujících dvou členů výrazu-těle do třídy `SurveyResponse`:

[!code-csharp[ReportResponses](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

Vzhledem k tomu, že `surveyResponses` je typ odkazu s možnou hodnotou null, jsou před odkazování na ni nutné kontroly hodnoty null. Metoda `Answer` vrací řetězec, který nemůže mít hodnotu null, takže musíme pokrýt případ chybějící odpovědi pomocí operátoru pro sjednocení null.

Dále přidejte tyto tři členy Expression-těle do třídy `SurveyRun`:

[!code-csharp[ReportResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

Člen `AllParticipants` musí vzít v úvahu, že proměnná `respondents` může mít hodnotu null, ale návratová hodnota nemůže být null. Pokud tento výraz změníte odebráním `??` a prázdné sekvence, která následuje, kompilátor vás upozorní, že metoda může vracet `null` a její návratový podpis vrátí typ, který nemůže mít hodnotu null.

Nakonec přidejte následující smyčku do dolní části `Main` metody:

[!code-csharp[DisplaySurveyResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

V tomto kódu nepotřebujete žádné `null` kontroly, protože jste navrhli základní rozhraní tak, aby všechny vracely typy odkazů, které neumožňují hodnotu null.

## <a name="get-the-code"></a>Získání kódu

Kód pro dokončený kurz můžete získat z našeho úložiště [ukázek](https://github.com/dotnet/samples) ve složce [CSharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) .

Experimenty změnou deklarace typů mezi typy s možnou hodnotou null a odkazem, které neumožňují hodnotu null. Podívejte se, jak to generuje různá upozornění, abyste měli jistotu, že nebudete omylem odkázat na `null`.

## <a name="next-steps"></a>Další kroky

Další informace migracem existující aplikace na použití typů odkazů s možnou hodnotou null:
> [!div class="nextstepaction"]
> [Upgrade aplikace na použití typů odkazů s možnou hodnotou null](upgrade-to-nullable-references.md)

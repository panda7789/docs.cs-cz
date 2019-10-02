---
title: Návrh s použitím typů odkazů s možnou hodnotou null
description: Tento rozšířený kurz poskytuje Úvod k odkazům s možnou hodnotou null. Naučíte se vyjádřit svůj návrh na to, kdy mohou být referenční hodnoty null, a nechat vynutit kompilátor, pokud nesmí mít hodnotu null.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 8b7c512a2f6bd67b07d8e344ad126026048be172
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736743"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a>Kurz: Seznámení s typem s možnou hodnotou null a odkazy, které neumožňují hodnotu null, je jasné.

C#8 zavádí **typy odkazů s možnou hodnotou null**, které připlňují odkazové typy stejným způsobem jako typy hodnot s možnou hodnotou null. Deklarujete proměnnou, která bude představovat **typ odkazu s možnou hodnotou null** připojením `?` k typu. Například `string?` představuje hodnotu null `string`. Tyto nové typy můžete použít k přehlednějšímu vyjádření záměru návrhu: některé proměnné *musí mít vždy hodnotu*, jiné *mohou chybět hodnoty*.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> - Zahrnutí typů s možnou hodnotou null a odkazů, které neumožňují hodnotu null, do návrhů
> - Povolí kontrolu typu odkazu s možnou hodnotou null v celém kódu.
> - Napsat kód, kde kompilátor vynutil tato rozhodnutí o návrhu.
> - Použití funkce odkazu s možnou hodnotou null ve vlastních návrzích

## <a name="prerequisites"></a>Předpoklady

Musíte nastavit počítač tak, aby běžel .NET Core, včetně kompilátoru C# 8,0. Kompilátor C# 8 beta je k dispozici v rámci sady [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)nebo [.NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

V tomto kurzu se předpokládá, že C# máte zkušenosti s platformou a .NET, včetně sady Visual Studio nebo .NET Core CLI.

## <a name="incorporate-nullable-reference-types-into-your-designs"></a>Zahrnutí typů odkazů s možnou hodnotou null do vašich návrhů

V tomto kurzu vytvoříte knihovnu, ve které modely spouštějí průzkum. Kód používá odkaz s možnou hodnotou null a odkaz, který nepovoluje hodnotu null, aby představoval koncepty reálného světa. Otázky průzkumu nemohou nikdy mít hodnotu null. Respondent může chtít odpovědět na otázku. V tomto případě mohou být odpovědi null.

Kód, který zapíšete pro tuto ukázku, tento záměr vyjádří a kompilátor vynutilí tento záměr.

## <a name="create-the-application-and-enable-nullable-reference-types"></a>Vytvoření aplikace a povolení typů odkazů s možnou hodnotou null

Vytvořte novou konzolovou aplikaci buď v aplikaci Visual Studio, nebo z příkazového řádku pomocí `dotnet new console`. Pojmenujte aplikaci `NullableIntroduction`. Po vytvoření aplikace budete muset povolit C# 8 beta funkcí. Otevřete soubor `csproj` a přidejte prvek `LangVersion` do prvku `PropertyGroup`. Je nutné, abyste se přihlásili k funkci **typů odkazů s možnou hodnotou null** i v C# 8 projektech. To je proto, že když je funkce zapnutá, existující deklarace referenčních proměnných se stanou odkazy, které neumožňují **hodnotu null**. I když toto rozhodnutí pomůže najít problémy, kdy existující kód nemusí mít správné kontroly hodnoty null, nemusí přesně odpovídat původnímu záměru návrhu. Funkci zapnete tak, že nastavíte `Nullable` elementu na `enable`:

```xml
<LangVersion>8.0</LangVersion>
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

Pokud jste napracovali v C#nástroji, možná jste zvyklí na odkazování na typy, které povolují hodnoty null, které jste pravděpodobně vynechali při deklaraci instancí, které neumožňují hodnotu null:

- Kolekce dotazů by neměla mít hodnotu null.
- Kolekce respondentů by neměla mít hodnotu null.

Při psaní kódu uvidíte, že typ odkazu, který neumožňuje hodnotu null, jako výchozí pro odkazy, zabraňuje běžným chybám, které by mohly vést k nulovým referenčním výjimkám. Jednou z lekcí tohoto kurzu je, že jste provedli rozhodnutí o tom, které proměnné by mohly nebo nemohly být null. Jazyk neposkytl syntaxi pro vyjádření těchto rozhodnutí. Teď to dělá.

Aplikace, kterou budete sestavovat, provede následující kroky:

1. Vytvořte průzkum a přidejte do něj otázky.
1. Vytvořte pseudo náhodnou sadu respondentů pro průzkum.
1. Kontaktujte respondenty, dokud velikost dokončeného průzkumu nedosáhne cílového čísla.
1. Napište důležité statistiky pro odpovědi na dotazníky.

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a>Sestavit průzkum s povolenými typy s možnou hodnotou null a bez hodnot null

První kód, který budete psát, vytvoří průzkum. Budete psát třídy pro modelování otázky průzkumu a spuštění průzkumu. Váš průzkum má tři typy dotazů, které jsou odlišené podle formátu odpovědi: ano/ne odpovědi, počet odpovědí a text odpovědi. Vytvořte třídu `public` `SurveyQuestion`:

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

Kompilátor interpretuje každou deklaraci proměnné typu odkazu jako typ odkazu, **který nepovoluje hodnotu null** , pro kód v povoleném kontextu s povolenou hodnotou null. Můžete se podívat na vaše první upozornění přidáním vlastností textu otázky a typu otázky, jak je znázorněno v následujícím kódu:

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

Vzhledem k tomu, že jste neinicializoval `QuestionText`, vyvolá kompilátor upozornění, že není inicializována vlastnost, která není null. Váš návrh vyžaduje, aby text otázky nebyl null, takže přidáte konstruktor, který ho inicializuje, a také hodnotu `QuestionType`. Hotová definice třídy vypadá jako následující kód:

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

Přidáním konstruktoru se odstraní upozornění. Argument konstruktoru je také typ odkazu, který neumožňuje hodnotu null, takže kompilátor nevydá žádná upozornění.

Dále vytvořte třídu `public` s názvem `SurveyRun`. Tato třída obsahuje seznam objektů a metod `SurveyQuestion` pro přidání otázek do průzkumu, jak je znázorněno v následujícím kódu:

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

Stejně jako předtím je nutné inicializovat objekt seznamu na hodnotu, která není null, nebo kompilátor vydá upozornění. V druhém přetížení `AddQuestion` nejsou žádné kontroly null, protože nejsou potřeba: deklaraci této proměnné nemůžete mít hodnotu null. Hodnota nemůže být `null`.

V editoru přepněte na `Program.cs` a nahraďte obsah `Main` následujícími řádky kódu:

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

Vzhledem k tomu, že celý projekt je v povoleném kontextu s povolenou hodnotou null, zobrazí se upozornění při předání `null` do jakékoli metody, která očekává typ odkazu, který neumožňuje hodnotu null. Zkuste to přidáním následujícího řádku do `Main`:

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

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

Hlavní zodpovědností této třídy je vygenerování odpovědí pro účastníka na otázky v průzkumu. Tato zodpovědnost zahrnuje několik kroků:

1. Zeptejte se na účast v průzkumu. Pokud uživatel nesouhlasí, vrátí odpověď chybějící (nebo null).
1. Položte každou otázku a zaznamenejte odpověď. Každá odpověď může také chybět (nebo mít hodnotu null).

Do třídy `SurveyResponse` přidejte následující kód:

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

Úložiště pro odpovědi na průzkum je `Dictionary<int, string>?`, což znamená, že může mít hodnotu null. Používáte novou funkci jazyka k deklaraci záměru návrhu, jak pro kompilátor, tak pro každého, kdo váš kód čte, později. Pokud někdy zrušíte odkaz `surveyResponses` bez prvotní kontroly hodnoty null, zobrazí se upozornění kompilátoru. Nezobrazuje se upozornění v metodě @no__t 0, protože kompilátor může určit, že proměnná `surveyResponses` byla nastavena na hodnotu jinou než null.

Použití `null` pro chybějící odpovědi zvýrazní klíčové body pro práci s typy odkazů s možnou hodnotou null: vaším cílem není odebrat všechny hodnoty `null` z programu. Místo toho je vaším cílem zajistit, aby kód, který píšete, vyjadřoval záměr vašeho návrhu. Chybějící hodnoty jsou nezbytným konceptem, který by bylo možné vyjádřit do kódu. Hodnota `null` představuje jasný způsob, jak vyjádřit chybějící hodnoty. Pokus o odebrání všech hodnot `null` vede pouze k definování jiného způsobu, jak tyto chybějící hodnoty vyjádřit bez `null`.

Dále je nutné zapsat metodu `PerformSurvey` ve třídě `SurveyRun`. Do třídy `SurveyRun` přidejte následující kód:

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

Tady můžete znovu vybrat @no__t s možnou hodnotou null-0, což znamená, že odpověď může být null. To indikuje, že průzkum ještě není předaný žádným respondentům. Všimněte si, že se přidávají respondenti, dokud nepřijdete o dostatek.

Posledním krokem ke spuštění průzkumu je přidání volání pro provedení průzkumu na konci metody `Main`:

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a>Kontrola odpovědí na průzkum

Posledním krokem je zobrazení výsledků průzkumu. Přidáte kód do mnoha tříd, které jste napsali. Tento kód ukazuje hodnotu rozlišující typy s možnou hodnotou null a odkazy, které neumožňují hodnotu null. Začněte přidáním následujících dvou členů výrazu-těle do třídy `SurveyResponse`:

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

Vzhledem k tomu, že `surveyResponses` je odkazový typ, který nepovoluje hodnotu null, nejsou před odkazování na odkazování nutné žádné kontroly. Metoda `Answer` vrátí řetězec bez hodnoty null, takže vyberte přetížení `GetValueOrDefault`, které pro výchozí hodnotu převezme druhý argument.

Dále přidejte tyto tři členy Expression-těle do třídy `SurveyRun`:

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

Člen `AllParticipants` musí vzít v úvahu, že proměnná `respondents` může mít hodnotu null, ale návratová hodnota nemůže být null. Pokud tento výraz změníte odebráním `??` a prázdné sekvence, která následuje, kompilátor vás upozorní, že metoda může vracet hodnotu `null` a její návratový podpis vrátí typ, který nelze připouštějící hodnotu null.

Nakonec přidejte následující smyčku na konec metody `Main`:

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

V tomto kódu nepotřebujete žádné kontroly `null`, protože jste navrhli základní rozhraní tak, aby všechny vracely typy odkazů, které neumožňují hodnotu null.

## <a name="get-the-code"></a>Získat kód

Kód pro dokončený kurz můžete získat z našeho úložiště [ukázek](https://github.com/dotnet/samples) ve složce [CSharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) .

Experimenty změnou deklarace typů mezi typy s možnou hodnotou null a odkazem, které neumožňují hodnotu null. Podívejte se, jak to generuje různá upozornění, abyste se ujistili, že nechtěně neodkazuje na `null`.

## <a name="next-steps"></a>Další kroky

Další informace migracem existující aplikace na použití typů odkazů s možnou hodnotou null:
> [!div class="nextstepaction"]
> [Upgrade aplikace na použití typů odkazů s možnou hodnotou null](upgrade-to-nullable-references.md)

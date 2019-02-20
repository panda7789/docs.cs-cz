---
title: Návrh s typy s možnou hodnotou Null odkazů
description: V tomto kurzu pokročilé obsahuje úvod do typy s možnou hodnotou Null odkazů. Se dozvíte, jak vyjádřit svůj návrh úmyslem při může mít hodnotu null referenční hodnoty a nechat kompilátor vynucovat, když nemohou být null.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 1c0df9b129e9c434eb3b5e6e50144013c2c0462e
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442097"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a>Kurz: Máte v úmyslu návrhu Express jasněji s typy s možnou hodnotou Null a Null reference

C#8 zavádí **typy s možnou hodnotou Null odkazů**, kterou doplněk referenční typy stejným způsobem jako typy s možnou hodnotou doplňují typy hodnot. Deklarujete proměnnou **typ s možnou hodnotou Null odkazu** připojením `?` typu. Například `string?` představuje s povolenou hodnotou Null `string`. Pro větší přehlednost express máte v úmyslu návrhu můžete použít tyto nové typy: Některé proměnné *musí mít vždy hodnotu*, ostatní *pravděpodobně chybí hodnota*.

V tomto kurzu se dozvíte jak:

> [!div class="checklist"]
> * Typy s možnou hodnotou Null a Null reference začlenit do vašich návrhů
> * Povolení kontroly typů s povolenou hodnotou Null reference v rámci vašeho kódu.
> * Psaní kódu, kde kompilátor vynucuje tato rozhodnutí o návrhu.
> * Použití s možnou hodnotou Null odkaz funkce v vlastní návrhy

## <a name="prerequisites"></a>Požadavky

Budete muset nastavit počítač pro spuštění .NET Core, včetně C# 8.0 beta verze kompilátoru. C# 8 beta verze kompilátoru je k dispozici s [Visual Studio 2019 preview 2](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+preview), nebo [.NET Core 3.0 ve verzi preview 2](https://dotnet.microsoft.com/download/dotnet-core/3.0).

Tento kurz předpokládá, že jste obeznámeni s C# a .NET, včetně sady Visual Studio nebo rozhraní příkazového řádku .NET Core.

## <a name="incorporate-nullable-reference-types-into-your-designs"></a>Typy s možnou hodnotou Null odkazů začlenit do vašich návrhů

V tomto kurzu vytvoříte knihovnu, která modeluje spouštění průzkumu. Kód používá k reprezentaci koncepty skutečné typy s možnou hodnotou Null odkazů a typy neumožňující hodnotu odkazu. Dotazy zjišťování může mít nikdy hodnotu null. Respondenta pravděpodobně nechcete odpověď na otázku. V tomto případě může mít hodnotu null odpovědi.

Kód, který napíšete pro tuto ukázku vyjadřuje tohoto záměru a kompilátor vynucuje tohoto záměru.

## <a name="create-the-application-and-enable-nullable-reference-types"></a>Vytvoření aplikace a povolení typy s možnou hodnotou Null odkazů

Vytvořte novou konzolovou aplikaci v sadě Visual Studio nebo z příkazového řádku pomocí `dotnet new console`. Pojmenujte aplikaci `NullableIntroduction`. Po vytvoření aplikace, budete muset povolit C# 8 beta verze funkce. Otevřít `csproj` a přidejte `LangVersion` elementu `PropertyGroup` elementu. Třeba pokud se rozhodnete do **typy s možnou hodnotou Null odkazů** funkce, dokonce i v C# 8 projekty. Důvodem je, že když je tato funkce zapnutá, budou existující deklarace proměnných odkazu **typy neumožňující hodnotu odkazu**. Když toto rozhodnutí se vám umožní najít problémy, kde stávající kód nemusí mít správné zjednodušená kontrola hodnot null, se nemusí přesně odrážet váš původním záměr návrhu. Zapnout funkci tak, že nastavíte `NullableContextOptions` elementu `enable`:

```xml
<LangVersion>8.0</LangVersion>
<NullableContextOptions>enable</NullableContextOptions>
```

> [!NOTE]
> Když C# (ne v režimu náhledu), se uvolní 8 `NullableContextOptions` element přidá nové šablony projektu. Dokud to neuděláte budete muset přidat ručně.


### <a name="design-the-types-for-the-application"></a>Navrhování typů pro aplikaci

Tato aplikace průzkumu vyžaduje vytvoření počet tříd:

- Třída, která modeluje seznam dotazů.
- Třída, která modeluje seznam osob kontaktovat průzkum.
- Třída, která modeluje odpovědi od osoby, která trvala zjišťování.

Tyto typy způsobí, že použití s možnou hodnotou Null a typy neumožňující hodnotu odkazu vyjádřit členy, které jsou požadovány a členy, které jsou volitelné. Typy s možnou hodnotou Null odkazů komunikovat, který jasně návrh záměr:

- Otázky, které jsou součástí zjišťování může mít nikdy hodnotu null: Nemá smysl pro prázdný dotaz.
- Respondentů může mít nikdy hodnotu null. Budete chtít sledovat lidé, se kterými vás kontaktovat, dokonce i respondentů, které odmítl se zúčastnit.
- Každá odpověď na dotaz může mít hodnotu null. Odpovědi na některé nebo všechny otázky můžete odmítnout respondentů.

Pokud jste naprogramovat v C#, může být proto zvyklí na referenční typy, které umožňují hodnoty null, které jste si asi nevšimli představují další příležitosti k deklarování Null instancemi:

- Kolekci otázek by měl mít hodnotu Null.
- Kolekce respondentů by měl mít hodnotu Null.

Při psaní kódu, uvidíte, že typ odkazu null jako výchozí pro odkazy se vyhnete běžných chyb, které by mohly vést k výjimkám odkaz s hodnotou null. Lekce jeden z tohoto kurzu je, že jste provedli rozhodnutí o tom, které proměnné může nebo nemůže mít hodnotu null. Jazyk neposkytl syntaxe express tato rozhodnutí. Nyní dělá.

Aplikace, kterou vytvoříte, bude proveďte následující kroky:

1. Vytvořit průzkum a přidejte do ní dotazy.
1. Vytvoření sady pseudonáhodné respondentů průzkum.
1. Kontaktujte respondentů, dokud velikost dokončené průzkumu dosáhne cíle číslo.
1. Vypsat důležitých statistik o odpovědi průzkumu.

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a>Vytvářejte zjišťování s typy s možnou hodnotou Null a Null

První kód, který napíšete vytvoří zjišťování. Napíšete třídy modelu otázky průzkumu a zjišťování spustit. Vaším dotazníkem má tři typy dotazů, formát odpovědi liší: Ano/Ne odpovědi číslo odpovědi a text odpovědi. Vytvoření `public` `SurveyQuestion` třídy:

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

Kompilátor interpretuje každý odkaz na typ deklarace proměnné jako **Null** odkazovat na typ pro kód v rámci s možnou hodnotou Null povolené. První upozornění můžete zobrazit tak, že přidáte vlastnosti text otázky a typ otázku, jak je znázorněno v následujícím kódu:

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

Protože nebyla inicializována `QuestionText`, kompilátor vyvolá upozornění, že vlastnost se zakázanou nebyla inicializována. Vyžaduje otázku text, který má být jiná než null, proto přidejte konstruktor k inicializaci jeho návrhu a `QuestionType` hodnotu. V definici hotové třídy bude vypadat jako v následujícím kódu:

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

Přidáním konstruktoru odebere upozornění. Argument konstruktoru je také typu Null odkaz, takže kompilátor nebude vydat upozornění.

Dále vytvořte `public` třídu s názvem `SurveyRun`. Tato třída obsahuje seznam `SurveyQuestion` objekty a metody pro přidání otázky průzkumu, jak je znázorněno v následujícím kódu:

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

Stejně jako dříve je nutné inicializovat objektem seznamu k nenulovou hodnotu nebo kompilátor vyvolá upozornění. Neexistují žádné kontroly hodnoty null v druhé přetížení metody `AddQuestion` vzhledem k tomu, že podle potřeby: Deklarujete tuto proměnnou k umožňovat hodnotu Null. Jeho hodnota nemůže být `null`.

Přepnout na `Program.cs` ve svém editoru a nahraďte obsah `Main` s následujícími řádky kódu:

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

Protože celý projekt je v kontextu s možnou hodnotou Null povolené, zobrazí se upozornění při předání `null` na jakoukoli metodu, očekává se typ neumožňující hodnotu odkazu. Vyzkoušet tak, že přidáte následující řádek, který `Main`:

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a>Vytvoření respondentů a získejte odpovědi na průzkum

Dále napište kód, který generuje odpovědi na tento průzkum. Tento proces zahrnuje několik malé úlohy:

1. Vytvořte metodu, která vytváří objekty respondentů. Představují položené odborníky vyplnit tento průzkum.
1. Vytvořte logiku pro simulaci kladení otázek respondentům a shromažďování odpovědi nebo poznamenat, že jste nenašli odpověď respondent.
1. Opakujte, dokud dostatek respondentů získejte odpovědi na tento průzkum.

Budete potřebovat třídy představují odpověď na průzkum, takže nyní přidat. Povolte podporu s možnou hodnotou Null. Přidat `Id` vlastnost a konstruktor, který inicializuje ji, jak je znázorněno v následujícím kódu:

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

V dalším kroku přidejte `static` metodu pro vytvoření nové účastníky vygenerováním náhodné ID:

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

Hlavní zodpovědností této třídy je generují odpovědi účastníka na otázky v průzkumu. Tuto odpovědnost zahrnuje několik kroků:

1. Požádejte o účast na průzkumu. Pokud není souhlas uživatele, vrátí odpověď chybí (nebo null).
1. Každý dotaz a odpověď si poznamenejte. Každou odpověď může být také chybí (nebo null).

Přidejte následující kód, který vaše `SurveyResponse` třídy:

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

Úložiště pro zjišťování odpovědi je `Dictionary<int, string>?`, která udává, že může mít hodnotu null. Chcete-li deklarovat vaším záměrem návrhu, kompilátoru a každému, kdo čte kód později používáte novou funkci jazyka. Pokud jste někdy přistoupit přes ukazatel `surveyResponses` bez provedení kontroly nejprve na hodnotu null, zobrazí se upozornění kompilátoru. Vám upozornění `AnswerSurvey` metoda protože kompilátor může určit, `surveyResponses` proměnné byl nastaven na nenulovou hodnotu výše.

Pomocí `null` pro odpovědi chybí zvýrazní zásadním aspektem pro práci s typy s možnou hodnotou Null reference: vaším cílem není odebrat všechny `null` hodnoty z vaší aplikace. Vaším cílem je místo, ujistěte se, že kód, který napíšete vyjadřují záměr návrhu. Chybějící hodnoty jsou nezbytné koncept vyjádřit v kódu. `null` Hodnotu vymazat způsob, jak vyjádřit tyto chybějící hodnoty. Chcete-li odebrat všechny `null` hodnoty pouze vede k definování některé další způsob, jak vyjádřit tyto chybějící hodnoty bez `null`.

Dále je třeba napsat `PerformSurvey` metodu `SurveyRun` třídy. Přidejte následující kód `SurveyRun` třídy:

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

Znovu sem, podle vašeho výběru s povolenou hodnotou Null `List<SurveyResponse>?` označuje odpověď může mít hodnotu null. Označuje, že tento průzkum ještě bylo přiděleno žádné respondentů ještě. Všimněte si, že jsou přidávány respondentů, dokud dostatek vyjádřili souhlas.

Posledním krokem ke spuštění zjišťování je přidat volání k provedení zjišťování na konci `Main` metody:

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a>Zkontrolujte odpovědi v průzkumu

Posledním krokem je zobrazit výsledky zjišťování. Přidáte kód pro většinu tříd, které jste zadali. Tento kód ukazuje, jakou hodnotu rozlišování typy odkazů s možnou hodnotou Null a Null. Začněte přidáním následujících dvou s výrazem v těle členy `SurveyResponse` třídy:

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

Protože `surveyResponses` je typem odkazu Null před zrušením odkazu nevzniká žádné kontroly. `Answer` Metoda vrátí řetězec null, proto zvolte přetížení `GetValueOrDefault` , který přijímá jako druhý argument pro výchozí hodnotu.

V dalším kroku přidejte tyto tři členy s výrazem v těle k `SurveyRun` třídy:

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

`AllParticipants` Člen musí vzít v úvahu, který `respondents` proměnná může mít hodnotu null, ale vrácená hodnota nemůže mít hodnotu null. Pokud změníte tento výraz tak, že odeberete `??` a prázdné sekvenci, který následuje, kompilátor vás upozorní, metoda může vrátit `null` a jeho návratový signatura vrátí hodnotu Null typu.

Nakonec přidejte následující smyčku v dolní části `Main` metody:

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

Není potřeba vybírat žádnou `null` kontroluje v tomto kódu, protože základní rozhraní jste navrhli tak, aby všechny návratové typy neumožňující hodnotu odkazu.

## <a name="get-the-code"></a>Získat kód

Můžete získat kód pro dokončení kurzu z našich [ukázky](https://github.com/dotnet/samples) úložiště v [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) složky.

Experimentujte změnou deklarace typů mezi typy s možnou hodnotou Null a Null odkazů. Naleznete v tématu Jak, který generuje upozornění jinou zajistit Nepřistupujte omylem `null`.

## <a name="next-steps"></a>Další kroky

Další informace a migrujte existující aplikace pro použití typů s povolenou hodnotou Null odkazu:
> [!div class="nextstepaction"]
> [Upgrade aplikace pro použití s možnou hodnotou Null odkazové typy](upgrade-to-nullable-references.md)

---
title: Návrh s typy s možnou hodnotou Null odkazů
description: V tomto kurzu pokročilé obsahuje úvod do typy s možnou hodnotou Null odkazů. Se dozvíte, jak vyjádřit svůj návrh úmyslem při může mít hodnotu null referenční hodnoty a nechat kompilátor vynucovat, když nemohou být null.
ms.date: 12/03/2018
ms.custom: mvc
ms.openlocfilehash: eec0c54c041db98595202ab982494df6ae3f743c
ms.sourcegitcommit: e39d93d358974b9ed4541cedf4e25c0101015c3c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2019
ms.locfileid: "55204766"
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

Budete muset nastavit počítač pro spuštění .NET Core, včetně C# 8.0 beta verze kompilátoru. C# 8 beta verze kompilátoru je k dispozici s [Visual Studio 2019 ve verzi preview 1](https://visualstudio.microsoft.com/vs/preview/), nebo [.NET Core 3.0 ve verzi preview 1](https://dotnet.microsoft.com/download/dotnet-core/3.0).

Tento kurz předpokládá, že jste obeznámeni s C# a .NET, včetně sady Visual Studio nebo rozhraní příkazového řádku .NET Core.

## <a name="incorporate-nullable-reference-types-into-your-designs"></a>Typy s možnou hodnotou Null odkazů začlenit do vašich návrhů

V tomto kurzu vytvoříte knihovnu, která modeluje spouštění průzkumu. Kód používá k reprezentaci koncepty skutečné typy s možnou hodnotou Null odkazů a typy neumožňující hodnotu odkazu. Dotazy zjišťování může mít nikdy hodnotu null. Respondenta pravděpodobně nechcete odpověď na otázku. V tomto případě může mít hodnotu null odpovědi.

Kód, který napíšete pro tuto ukázku vyjadřuje tohoto záměru a kompilátor vynucuje tohoto záměru.

## <a name="create-the-application-and-enable-nullable-reference-types"></a>Vytvoření aplikace a povolení typy s možnou hodnotou Null odkazů

Vytvořte novou konzolovou aplikaci v sadě Visual Studio nebo z příkazového řádku pomocí `dotnet new console`. Pojmenujte aplikaci `NullableIntroduction`. Po vytvoření aplikace, budete muset povolit C# 8 beta verze funkce. Otevřít `csproj` a přidejte `LangVersion` elementu `PropertyGroup` element:

```xml
<LangVersion>8.0</LangVersion>
```

Alternativně můžete použít vlastnosti projektu sady Visual Studio povolit C# 8. V Průzkumníku řešení klikněte pravým tlačítkem na uzel projektu, vyberte **vlastnosti**. Vyberte **sestavení** kartu a klikněte na tlačítko **Upřesnit...** . V rozevírací nabídce pro jazykovou verzi, vyberte  **C# 8.0 (beta verze)**.

Třeba pokud se rozhodnete do **typy s možnou hodnotou Null odkazů** funkce, dokonce i v C# 8 projekty. Důvodem je, že když je tato funkce zapnutá, budou existující deklarace proměnných odkazu **typy neumožňující hodnotu odkazu**. Když toto rozhodnutí se vám umožní najít problémy, kde stávající kód nemusí mít správné zjednodušená kontrola hodnot null, se nemusí přesně odrážet váš původním záměr návrhu. Zapnout funkci pomocí nové direktivy pragma:

```csharp
#nullable enable
```

Předchozí – Direktiva pragma můžete přidat libovolné místo ve zdrojovém souboru a je zapnutá funkce typ s možnou hodnotou Null odkaz z tohoto bodu. Direktivy pragma podporuje také `disable` argument pro funkci vypnout.

Můžete také zapnout **typy s možnou hodnotou Null odkazů** pro celý projekt tak, že přidáte následující element souboru .csproj, třeba hned za `LangVersion` element, který povolené C# 8.0:

```xml
<NullableReferenceTypes>true</NullableReferenceTypes>
```

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

První kód, který napíšete vytvoří zjišťování. Napíšete třídy modelu otázky průzkumu a zjišťování spustit. Vaším dotazníkem má tři typy dotazů, formát odpovědi liší: Ano/Ne odpovědi číslo odpovědi a text odpovědi. Vytvoření `public` `SurveyQuestion` třídy. Zahrnout `#nullable enable` – Direktiva pragma ihned po `using` příkazy:

```csharp
#nullable enable
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

Přidání `#nullable enable` – Direktiva pragma znamená, že kompilátor interpretuje každý odkaz na typ deklarace proměnné jako **Null** typ odkazu. První upozornění můžete zobrazit tak, že přidáte vlastnosti text otázky a typ otázku, jak je znázorněno v následujícím kódu:

```csharp
#nullable enable
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

Dále vytvořte `public` třídu s názvem `SurveyRun`. Zahrnout `#nullable enable` následující direktivy pragma `using` příkazy. Tato třída obsahuje seznam `SurveyQuestion` objekty a metody pro přidání otázky průzkumu, jak je znázorněno v následujícím kódu:

```csharp
using System.Collections.Generic;

#nullable enable
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

Bez `#nullable enable` – Direktiva pragma se v horní části souboru, kompilátor nebude vyvolávat tato upozornění při předání `null` jako text `AddQuestion` argument. To opravit přidáním `#nullable enable` následující `using` příkazu. Vyzkoušet tak, že přidáte následující řádek, který `Main`:

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a>Vytvoření respondentů a získejte odpovědi na průzkum

Dále napište kód, který generuje odpovědi na tento průzkum. To zahrnuje několik malé úlohy:

1. Vytvořte metodu, která vytváří objekty respondentů. Představují položené odborníky vyplnit tento průzkum.
1. Vytvořte logiku pro simulaci kladení otázek respondentům a shromažďování odpovědi nebo poznamenat, že jste nenašli odpověď respondent.
1. Opakujte, dokud dostatek respondentů získejte odpovědi na tento průzkum.

Budete potřebovat třídy představují odpověď na průzkum, takže nyní přidat. Povolte podporu s možnou hodnotou Null. Přidat `Id` vlastnost a konstruktor, který inicializuje ji, jak je znázorněno v následujícím kódu:

```csharp
#nullable enable
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

Další informace najdete přehled typů s povolenou hodnotou Null reference...
> [!div class="nextstepaction"]
> [Přehled odkazy s možnou hodnotou Null](../nullable-references.md)

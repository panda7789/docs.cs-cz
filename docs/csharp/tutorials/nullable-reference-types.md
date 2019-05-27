---
title: Návrh s typy s možnou hodnotou Null odkazů
description: V tomto kurzu pokročilé obsahuje úvod do typy s možnou hodnotou Null odkazů. Se dozvíte, jak vyjádřit svůj návrh úmyslem při může mít hodnotu null referenční hodnoty a nechat kompilátor vynucovat, když nemohou být null.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: cd73a73554514c2b7c70c78ba24038ee8d543266
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/24/2019
ms.locfileid: "66195826"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="cab89-104">Kurz: Máte v úmyslu návrhu Express jasněji s typy s možnou hodnotou Null a Null reference</span><span class="sxs-lookup"><span data-stu-id="cab89-104">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>

<span data-ttu-id="cab89-105">C#8 zavádí **typy s možnou hodnotou Null odkazů**, kterou doplněk referenční typy stejným způsobem jako typy s možnou hodnotou doplňují typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="cab89-105">C# 8 introduces **nullable reference types**, which complement reference types the same way nullable value types complement value types.</span></span> <span data-ttu-id="cab89-106">Deklarujete proměnnou **typ s možnou hodnotou Null odkazu** připojením `?` typu.</span><span class="sxs-lookup"><span data-stu-id="cab89-106">You declare a variable to be a **nullable reference type** by appending a `?` to the type.</span></span> <span data-ttu-id="cab89-107">Například `string?` představuje s povolenou hodnotou Null `string`.</span><span class="sxs-lookup"><span data-stu-id="cab89-107">For example, `string?` represents a nullable `string`.</span></span> <span data-ttu-id="cab89-108">Pro větší přehlednost express máte v úmyslu návrhu můžete použít tyto nové typy: Některé proměnné *musí mít vždy hodnotu*, ostatní *pravděpodobně chybí hodnota*.</span><span class="sxs-lookup"><span data-stu-id="cab89-108">You can use these new types to more clearly express your design intent: some variables *must always have a value*, others *may be missing a value*.</span></span>

<span data-ttu-id="cab89-109">V tomto kurzu se dozvíte jak:</span><span class="sxs-lookup"><span data-stu-id="cab89-109">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="cab89-110">Typy s možnou hodnotou Null a Null reference začlenit do vašich návrhů</span><span class="sxs-lookup"><span data-stu-id="cab89-110">Incorporate nullable and non-nullable reference types into your designs</span></span>
> * <span data-ttu-id="cab89-111">Povolení kontroly typů s povolenou hodnotou Null reference v rámci vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="cab89-111">Enable nullable reference type checks throughout your code.</span></span>
> * <span data-ttu-id="cab89-112">Psaní kódu, kde kompilátor vynucuje tato rozhodnutí o návrhu.</span><span class="sxs-lookup"><span data-stu-id="cab89-112">Write code where the compiler enforces those design decisions.</span></span>
> * <span data-ttu-id="cab89-113">Použití s možnou hodnotou Null odkaz funkce v vlastní návrhy</span><span class="sxs-lookup"><span data-stu-id="cab89-113">Use the nullable reference feature in your own designs</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cab89-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cab89-114">Prerequisites</span></span>

<span data-ttu-id="cab89-115">Budete muset nastavit počítač pro spuštění .NET Core, včetně C# 8.0 beta verze kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="cab89-115">You'll need to set up your machine to run .NET Core, including the C# 8.0 beta compiler.</span></span> <span data-ttu-id="cab89-116">C# 8 beta verze kompilátoru je k dispozici s [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), nebo si prohlédnout nejnovější [ve verzi preview rozhraní .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="cab89-116">The C# 8 beta compiler is available with [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or the latest [.NET Core 3.0 preview](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="cab89-117">Tento kurz předpokládá, že jste obeznámeni s C# a .NET, včetně sady Visual Studio nebo rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cab89-117">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="incorporate-nullable-reference-types-into-your-designs"></a><span data-ttu-id="cab89-118">Typy s možnou hodnotou Null odkazů začlenit do vašich návrhů</span><span class="sxs-lookup"><span data-stu-id="cab89-118">Incorporate nullable reference types into your designs</span></span>

<span data-ttu-id="cab89-119">V tomto kurzu vytvoříte knihovnu, která modeluje spouštění průzkumu.</span><span class="sxs-lookup"><span data-stu-id="cab89-119">In this tutorial, you'll build a library that models running a survey.</span></span> <span data-ttu-id="cab89-120">Kód používá k reprezentaci koncepty skutečné typy s možnou hodnotou Null odkazů a typy neumožňující hodnotu odkazu.</span><span class="sxs-lookup"><span data-stu-id="cab89-120">The code uses both nullable reference types and non-nullable reference types to represent the real-world concepts.</span></span> <span data-ttu-id="cab89-121">Dotazy zjišťování může mít nikdy hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="cab89-121">The survey questions can never be null.</span></span> <span data-ttu-id="cab89-122">Respondenta pravděpodobně nechcete odpověď na otázku.</span><span class="sxs-lookup"><span data-stu-id="cab89-122">A respondent might prefer not to answer a question.</span></span> <span data-ttu-id="cab89-123">V tomto případě může mít hodnotu null odpovědi.</span><span class="sxs-lookup"><span data-stu-id="cab89-123">The responses might be null in this case.</span></span>

<span data-ttu-id="cab89-124">Kód, který napíšete pro tuto ukázku vyjadřuje tohoto záměru a kompilátor vynucuje tohoto záměru.</span><span class="sxs-lookup"><span data-stu-id="cab89-124">The code you'll write for this sample expresses that intent, and the compiler enforces that intent.</span></span>

## <a name="create-the-application-and-enable-nullable-reference-types"></a><span data-ttu-id="cab89-125">Vytvoření aplikace a povolení typy s možnou hodnotou Null odkazů</span><span class="sxs-lookup"><span data-stu-id="cab89-125">Create the application and enable nullable reference types</span></span>

<span data-ttu-id="cab89-126">Vytvořte novou konzolovou aplikaci v sadě Visual Studio nebo z příkazového řádku pomocí `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="cab89-126">Create a new console application either in Visual Studio or from the command line using `dotnet new console`.</span></span> <span data-ttu-id="cab89-127">Pojmenujte aplikaci `NullableIntroduction`.</span><span class="sxs-lookup"><span data-stu-id="cab89-127">Name the application `NullableIntroduction`.</span></span> <span data-ttu-id="cab89-128">Po vytvoření aplikace, budete muset povolit C# 8 beta verze funkce.</span><span class="sxs-lookup"><span data-stu-id="cab89-128">Once you've created the application, you'll need to enable C# 8 beta features.</span></span> <span data-ttu-id="cab89-129">Otevřít `csproj` a přidejte `LangVersion` elementu `PropertyGroup` elementu.</span><span class="sxs-lookup"><span data-stu-id="cab89-129">Open the `csproj` file and add a `LangVersion` element to the `PropertyGroup` element.</span></span> <span data-ttu-id="cab89-130">Třeba pokud se rozhodnete do **typy s možnou hodnotou Null odkazů** funkce, dokonce i v C# 8 projekty.</span><span class="sxs-lookup"><span data-stu-id="cab89-130">You must opt into the **nullable reference types** feature, even in C# 8 projects.</span></span> <span data-ttu-id="cab89-131">Důvodem je, že když je tato funkce zapnutá, budou existující deklarace proměnných odkazu **typy neumožňující hodnotu odkazu**.</span><span class="sxs-lookup"><span data-stu-id="cab89-131">That's because once the feature is turned on, existing reference variable declarations become **non-nullable reference types**.</span></span> <span data-ttu-id="cab89-132">Když toto rozhodnutí se vám umožní najít problémy, kde stávající kód nemusí mít správné zjednodušená kontrola hodnot null, se nemusí přesně odrážet váš původním záměr návrhu.</span><span class="sxs-lookup"><span data-stu-id="cab89-132">While that decision will help find issues where existing code may not have proper null-checks, it may not accurately reflect your original design intent.</span></span> <span data-ttu-id="cab89-133">Zapnout funkci tak, že nastavíte `Nullable` elementu `enable`:</span><span class="sxs-lookup"><span data-stu-id="cab89-133">You turn on the feature by setting the `Nullable` element to `enable`:</span></span>

```xml
<LangVersion>8.0</LangVersion>
<Nullable>enable</Nullable>
```

> [!IMPORTANT]
> <span data-ttu-id="cab89-134">`Nullable` Element se dříve nazýval `NullableContextOptions`.</span><span class="sxs-lookup"><span data-stu-id="cab89-134">The `Nullable` element was previously named `NullableContextOptions`.</span></span> <span data-ttu-id="cab89-135">Přejmenování se dodává se sadou Visual Studio. 2019, 16.2 p1.</span><span class="sxs-lookup"><span data-stu-id="cab89-135">The rename ships with Visual Studio 2019, 16.2-p1.</span></span> <span data-ttu-id="cab89-136">Tato změna nemá žádné 3.0.100-preview5-011568 .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="cab89-136">The .NET Core SDK 3.0.100-preview5-011568 does not have this change.</span></span> <span data-ttu-id="cab89-137">Pokud používáte rozhraní příkazového řádku .NET Core, budete muset použít `NullableContextOptions` až do další ve verzi preview je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="cab89-137">If you are using the .NET Core CLI, you'll need to use `NullableContextOptions` until the next preview is available.</span></span>

> [!NOTE]
> <span data-ttu-id="cab89-138">Když C# (ne v režimu náhledu), se uvolní 8 `Nullable` element přidá nové šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="cab89-138">When C# 8 is released (not in preview mode), the `Nullable` element will be added by new project templates.</span></span> <span data-ttu-id="cab89-139">Dokud to neuděláte budete muset přidat ručně.</span><span class="sxs-lookup"><span data-stu-id="cab89-139">Until then, you'll need to add it manually.</span></span>

### <a name="design-the-types-for-the-application"></a><span data-ttu-id="cab89-140">Navrhování typů pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="cab89-140">Design the types for the application</span></span>

<span data-ttu-id="cab89-141">Tato aplikace průzkumu vyžaduje vytvoření počet tříd:</span><span class="sxs-lookup"><span data-stu-id="cab89-141">This survey application requires creating a number of classes:</span></span>

- <span data-ttu-id="cab89-142">Třída, která modeluje seznam dotazů.</span><span class="sxs-lookup"><span data-stu-id="cab89-142">A class that models the list of questions.</span></span>
- <span data-ttu-id="cab89-143">Třída, která modeluje seznam osob kontaktovat průzkum.</span><span class="sxs-lookup"><span data-stu-id="cab89-143">A class that models a list of people contacted for the survey.</span></span>
- <span data-ttu-id="cab89-144">Třída, která modeluje odpovědi od osoby, která trvala zjišťování.</span><span class="sxs-lookup"><span data-stu-id="cab89-144">A class that models the answers from a person that took the survey.</span></span>

<span data-ttu-id="cab89-145">Tyto typy způsobí, že použití s možnou hodnotou Null a typy neumožňující hodnotu odkazu vyjádřit členy, které jsou požadovány a členy, které jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="cab89-145">These types will make use of both nullable and non-nullable reference types to express which members are required and which members are optional.</span></span> <span data-ttu-id="cab89-146">Typy s možnou hodnotou Null odkazů komunikovat, který jasně návrh záměr:</span><span class="sxs-lookup"><span data-stu-id="cab89-146">Nullable reference types communicate that design intent clearly:</span></span>

- <span data-ttu-id="cab89-147">Otázky, které jsou součástí zjišťování může mít nikdy hodnotu null: Nemá smysl pro prázdný dotaz.</span><span class="sxs-lookup"><span data-stu-id="cab89-147">The questions that are part of the survey can never be null: It makes no sense to ask an empty question.</span></span>
- <span data-ttu-id="cab89-148">Respondentů může mít nikdy hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="cab89-148">The respondents can never be null.</span></span> <span data-ttu-id="cab89-149">Budete chtít sledovat lidé, se kterými vás kontaktovat, dokonce i respondentů, které odmítl se zúčastnit.</span><span class="sxs-lookup"><span data-stu-id="cab89-149">You'll want to track people you contacted, even respondents that declined to participate.</span></span>
- <span data-ttu-id="cab89-150">Každá odpověď na dotaz může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="cab89-150">Any response to a question may be null.</span></span> <span data-ttu-id="cab89-151">Odpovědi na některé nebo všechny otázky můžete odmítnout respondentů.</span><span class="sxs-lookup"><span data-stu-id="cab89-151">Respondents can decline to answer some or all questions.</span></span>

<span data-ttu-id="cab89-152">Pokud jste naprogramovat v C#, může být proto zvyklí na referenční typy, které umožňují hodnoty null, které jste si asi nevšimli představují další příležitosti k deklarování Null instancemi:</span><span class="sxs-lookup"><span data-stu-id="cab89-152">If you've programmed in C#, you may be so accustomed to reference types that allow null values that you may have missed other opportunities to declare non-nullable instances:</span></span>

- <span data-ttu-id="cab89-153">Kolekci otázek by měl mít hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="cab89-153">The collection of questions should be non-nullable.</span></span>
- <span data-ttu-id="cab89-154">Kolekce respondentů by měl mít hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="cab89-154">The collection of respondents should be non-nullable.</span></span>

<span data-ttu-id="cab89-155">Při psaní kódu, uvidíte, že typ odkazu null jako výchozí pro odkazy se vyhnete běžných chyb, které by mohly vést k výjimkám odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="cab89-155">As you write the code, you'll see that a non-nullable reference type as the default for references avoids common mistakes that could lead to null reference exceptions.</span></span> <span data-ttu-id="cab89-156">Lekce jeden z tohoto kurzu je, že jste provedli rozhodnutí o tom, které proměnné může nebo nemůže mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="cab89-156">One lesson from this tutorial is that you made decisions about which variables could or could not be null.</span></span> <span data-ttu-id="cab89-157">Jazyk neposkytl syntaxe express tato rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="cab89-157">The language didn't provide syntax to express those decisions.</span></span> <span data-ttu-id="cab89-158">Nyní dělá.</span><span class="sxs-lookup"><span data-stu-id="cab89-158">Now it does.</span></span>

<span data-ttu-id="cab89-159">Aplikace, kterou vytvoříte, bude proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="cab89-159">The app you'll build will do the following steps:</span></span>

1. <span data-ttu-id="cab89-160">Vytvořit průzkum a přidejte do ní dotazy.</span><span class="sxs-lookup"><span data-stu-id="cab89-160">Create a survey and add questions to it.</span></span>
1. <span data-ttu-id="cab89-161">Vytvoření sady pseudonáhodné respondentů průzkum.</span><span class="sxs-lookup"><span data-stu-id="cab89-161">Create a pseudo-random set of respondents for the survey.</span></span>
1. <span data-ttu-id="cab89-162">Kontaktujte respondentů, dokud velikost dokončené průzkumu dosáhne cíle číslo.</span><span class="sxs-lookup"><span data-stu-id="cab89-162">Contact respondents until the completed survey size reaches the goal number.</span></span>
1. <span data-ttu-id="cab89-163">Vypsat důležitých statistik o odpovědi průzkumu.</span><span class="sxs-lookup"><span data-stu-id="cab89-163">Write out important statistics on the survey responses.</span></span>

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a><span data-ttu-id="cab89-164">Vytvářejte zjišťování s typy s možnou hodnotou Null a Null</span><span class="sxs-lookup"><span data-stu-id="cab89-164">Build the survey with nullable and non-nullable types</span></span>

<span data-ttu-id="cab89-165">První kód, který napíšete vytvoří zjišťování.</span><span class="sxs-lookup"><span data-stu-id="cab89-165">The first code you'll write creates the survey.</span></span> <span data-ttu-id="cab89-166">Napíšete třídy modelu otázky průzkumu a zjišťování spustit.</span><span class="sxs-lookup"><span data-stu-id="cab89-166">You'll write classes to model a survey question and a survey run.</span></span> <span data-ttu-id="cab89-167">Vaším dotazníkem má tři typy dotazů, formát odpovědi liší: Ano/Ne odpovědi číslo odpovědi a text odpovědi.</span><span class="sxs-lookup"><span data-stu-id="cab89-167">Your survey has three types of questions, distinguished by the format of the answer: Yes/No answers, number answers, and text answers.</span></span> <span data-ttu-id="cab89-168">Vytvoření `public` `SurveyQuestion` třídy:</span><span class="sxs-lookup"><span data-stu-id="cab89-168">Create a `public` `SurveyQuestion` class:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

<span data-ttu-id="cab89-169">Kompilátor interpretuje každý odkaz na typ deklarace proměnné jako **Null** odkazovat na typ pro kód v rámci s možnou hodnotou Null povolené.</span><span class="sxs-lookup"><span data-stu-id="cab89-169">The compiler interprets every reference type variable declaration as a **non-nullable** reference type for code in a nullable enabled context.</span></span> <span data-ttu-id="cab89-170">První upozornění můžete zobrazit tak, že přidáte vlastnosti text otázky a typ otázku, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="cab89-170">You can see your first warning by adding properties for the question text and the type of question, as shown in the following code:</span></span>

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

<span data-ttu-id="cab89-171">Protože nebyla inicializována `QuestionText`, kompilátor vyvolá upozornění, že vlastnost se zakázanou nebyla inicializována.</span><span class="sxs-lookup"><span data-stu-id="cab89-171">Because you haven't initialized `QuestionText`, the compiler issues a warning that a non-nullable property hasn't been initialized.</span></span> <span data-ttu-id="cab89-172">Vyžaduje otázku text, který má být jiná než null, proto přidejte konstruktor k inicializaci jeho návrhu a `QuestionType` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cab89-172">Your design requires the question text to be non-null, so you add a constructor to initialize it and the `QuestionType` value as well.</span></span> <span data-ttu-id="cab89-173">V definici hotové třídy bude vypadat jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="cab89-173">The finished class definition looks like the following code:</span></span>

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

<span data-ttu-id="cab89-174">Přidáním konstruktoru odebere upozornění.</span><span class="sxs-lookup"><span data-stu-id="cab89-174">Adding the constructor removes the warning.</span></span> <span data-ttu-id="cab89-175">Argument konstruktoru je také typu Null odkaz, takže kompilátor nebude vydat upozornění.</span><span class="sxs-lookup"><span data-stu-id="cab89-175">The constructor argument is also a non-nullable reference type, so the compiler doesn't issue any warnings.</span></span>

<span data-ttu-id="cab89-176">Dále vytvořte `public` třídu s názvem `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="cab89-176">Next, create a `public` class named `SurveyRun`.</span></span> <span data-ttu-id="cab89-177">Tato třída obsahuje seznam `SurveyQuestion` objekty a metody pro přidání otázky průzkumu, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="cab89-177">This class contains a list of `SurveyQuestion` objects and methods to add questions to the survey, as shown in the following code:</span></span>

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

<span data-ttu-id="cab89-178">Stejně jako dříve je nutné inicializovat objektem seznamu k nenulovou hodnotu nebo kompilátor vyvolá upozornění.</span><span class="sxs-lookup"><span data-stu-id="cab89-178">As before, you must initialize the list object to a non-null value or the compiler issues a warning.</span></span> <span data-ttu-id="cab89-179">Neexistují žádné kontroly hodnoty null v druhé přetížení metody `AddQuestion` vzhledem k tomu, že podle potřeby: Deklarujete tuto proměnnou k umožňovat hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="cab89-179">There are no null checks in the second overload of `AddQuestion` because they aren't needed: You've declared that variable to be non-nullable.</span></span> <span data-ttu-id="cab89-180">Jeho hodnota nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="cab89-180">Its value can't be `null`.</span></span>

<span data-ttu-id="cab89-181">Přepnout na `Program.cs` ve svém editoru a nahraďte obsah `Main` s následujícími řádky kódu:</span><span class="sxs-lookup"><span data-stu-id="cab89-181">Switch to `Program.cs` in your editor and replace the contents of `Main` with the following lines of code:</span></span>

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

<span data-ttu-id="cab89-182">Protože celý projekt je v kontextu s možnou hodnotou Null povolené, zobrazí se upozornění při předání `null` na jakoukoli metodu, očekává se typ neumožňující hodnotu odkazu.</span><span class="sxs-lookup"><span data-stu-id="cab89-182">Because the entire project is in a nullable enabled context, you'll get warnings when you pass `null` to any method expecting a non-nullable reference type.</span></span> <span data-ttu-id="cab89-183">Vyzkoušet tak, že přidáte následující řádek, který `Main`:</span><span class="sxs-lookup"><span data-stu-id="cab89-183">Try it by adding the following line to `Main`:</span></span>

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a><span data-ttu-id="cab89-184">Vytvoření respondentů a získejte odpovědi na průzkum</span><span class="sxs-lookup"><span data-stu-id="cab89-184">Create respondents and get answers to the survey</span></span>

<span data-ttu-id="cab89-185">Dále napište kód, který generuje odpovědi na tento průzkum.</span><span class="sxs-lookup"><span data-stu-id="cab89-185">Next, write the code that generates answers to the survey.</span></span> <span data-ttu-id="cab89-186">Tento proces zahrnuje několik malé úlohy:</span><span class="sxs-lookup"><span data-stu-id="cab89-186">This process involves several small tasks:</span></span>

1. <span data-ttu-id="cab89-187">Vytvořte metodu, která vytváří objekty respondentů.</span><span class="sxs-lookup"><span data-stu-id="cab89-187">Build a method that generates respondent objects.</span></span> <span data-ttu-id="cab89-188">Představují položené odborníky vyplnit tento průzkum.</span><span class="sxs-lookup"><span data-stu-id="cab89-188">These represent people asked to fill out the survey.</span></span>
1. <span data-ttu-id="cab89-189">Vytvořte logiku pro simulaci kladení otázek respondentům a shromažďování odpovědi nebo poznamenat, že jste nenašli odpověď respondent.</span><span class="sxs-lookup"><span data-stu-id="cab89-189">Build logic to simulate asking the questions to a respondent and collecting answers or noting that a respondent didn't answer.</span></span>
1. <span data-ttu-id="cab89-190">Opakujte, dokud dostatek respondentů získejte odpovědi na tento průzkum.</span><span class="sxs-lookup"><span data-stu-id="cab89-190">Repeat until enough respondents have answered the survey.</span></span>

<span data-ttu-id="cab89-191">Budete potřebovat třídy představují odpověď na průzkum, takže nyní přidat.</span><span class="sxs-lookup"><span data-stu-id="cab89-191">You'll need a class to represent a survey response, so add that now.</span></span> <span data-ttu-id="cab89-192">Povolte podporu s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="cab89-192">Enable nullable support.</span></span> <span data-ttu-id="cab89-193">Přidat `Id` vlastnost a konstruktor, který inicializuje ji, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="cab89-193">Add an `Id` property and a constructor that initializes it, as shown in the following code:</span></span>

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

<span data-ttu-id="cab89-194">V dalším kroku přidejte `static` metodu pro vytvoření nové účastníky vygenerováním náhodné ID:</span><span class="sxs-lookup"><span data-stu-id="cab89-194">Next, add a `static` method to create new participants by generating a random ID:</span></span>

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

<span data-ttu-id="cab89-195">Hlavní zodpovědností této třídy je generují odpovědi účastníka na otázky v průzkumu.</span><span class="sxs-lookup"><span data-stu-id="cab89-195">The main responsibility of this class is to generate the responses for a participant to the questions in the survey.</span></span> <span data-ttu-id="cab89-196">Tuto odpovědnost zahrnuje několik kroků:</span><span class="sxs-lookup"><span data-stu-id="cab89-196">This responsibility has a few steps:</span></span>

1. <span data-ttu-id="cab89-197">Požádejte o účast na průzkumu.</span><span class="sxs-lookup"><span data-stu-id="cab89-197">Ask for participation in the survey.</span></span> <span data-ttu-id="cab89-198">Pokud není souhlas uživatele, vrátí odpověď chybí (nebo null).</span><span class="sxs-lookup"><span data-stu-id="cab89-198">If the person doesn't consent, return a missing (or null) response.</span></span>
1. <span data-ttu-id="cab89-199">Každý dotaz a odpověď si poznamenejte.</span><span class="sxs-lookup"><span data-stu-id="cab89-199">Ask each question and record the answer.</span></span> <span data-ttu-id="cab89-200">Každou odpověď může být také chybí (nebo null).</span><span class="sxs-lookup"><span data-stu-id="cab89-200">Each answer may also be missing (or null).</span></span>

<span data-ttu-id="cab89-201">Přidejte následující kód, který vaše `SurveyResponse` třídy:</span><span class="sxs-lookup"><span data-stu-id="cab89-201">Add the following code to your `SurveyResponse` class:</span></span>

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

<span data-ttu-id="cab89-202">Úložiště pro zjišťování odpovědi je `Dictionary<int, string>?`, která udává, že může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="cab89-202">The storage for the survey answers is a `Dictionary<int, string>?`, indicating that it may be null.</span></span> <span data-ttu-id="cab89-203">Chcete-li deklarovat vaším záměrem návrhu, kompilátoru a každému, kdo čte kód později používáte novou funkci jazyka.</span><span class="sxs-lookup"><span data-stu-id="cab89-203">You're using the new language feature to declare your design intent, both to the compiler and to anyone reading your code later.</span></span> <span data-ttu-id="cab89-204">Pokud jste někdy přistoupit přes ukazatel `surveyResponses` bez provedení kontroly nejprve na hodnotu null, zobrazí se upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="cab89-204">If you ever dereference `surveyResponses` without checking for the null value first, you'll get a compiler warning.</span></span> <span data-ttu-id="cab89-205">Vám upozornění `AnswerSurvey` metoda protože kompilátor může určit, `surveyResponses` proměnné byl nastaven na nenulovou hodnotu výše.</span><span class="sxs-lookup"><span data-stu-id="cab89-205">You don't get a warning in the `AnswerSurvey` method because the compiler can determine the `surveyResponses` variable was set to a non-null value above.</span></span>

<span data-ttu-id="cab89-206">Pomocí `null` pro odpovědi chybí zvýrazní zásadním aspektem pro práci s typy s možnou hodnotou Null reference: vaším cílem není odebrat všechny `null` hodnoty z vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="cab89-206">Using `null` for missing answers highlights a key point for working with nullable reference types: your goal isn't to remove all `null` values from your program.</span></span> <span data-ttu-id="cab89-207">Vaším cílem je místo, ujistěte se, že kód, který napíšete vyjadřují záměr návrhu.</span><span class="sxs-lookup"><span data-stu-id="cab89-207">Rather, your goal is to ensure that the code you write expresses the intent of your design.</span></span> <span data-ttu-id="cab89-208">Chybějící hodnoty jsou nezbytné koncept vyjádřit v kódu.</span><span class="sxs-lookup"><span data-stu-id="cab89-208">Missing values are a necessary concept to express in your code.</span></span> <span data-ttu-id="cab89-209">`null` Hodnotu vymazat způsob, jak vyjádřit tyto chybějící hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cab89-209">The `null` value is a clear way to express those missing values.</span></span> <span data-ttu-id="cab89-210">Chcete-li odebrat všechny `null` hodnoty pouze vede k definování některé další způsob, jak vyjádřit tyto chybějící hodnoty bez `null`.</span><span class="sxs-lookup"><span data-stu-id="cab89-210">Trying to remove all `null` values only leads to defining some other way to express those missing values without `null`.</span></span>

<span data-ttu-id="cab89-211">Dále je třeba napsat `PerformSurvey` metodu `SurveyRun` třídy.</span><span class="sxs-lookup"><span data-stu-id="cab89-211">Next, you need to write the `PerformSurvey` method in the `SurveyRun` class.</span></span> <span data-ttu-id="cab89-212">Přidejte následující kód `SurveyRun` třídy:</span><span class="sxs-lookup"><span data-stu-id="cab89-212">Add the following code in the `SurveyRun` class:</span></span>

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

<span data-ttu-id="cab89-213">Znovu sem, podle vašeho výběru s povolenou hodnotou Null `List<SurveyResponse>?` označuje odpověď může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="cab89-213">Here again, your choice of a nullable `List<SurveyResponse>?` indicates the response may be null.</span></span> <span data-ttu-id="cab89-214">Označuje, že tento průzkum ještě bylo přiděleno žádné respondentů ještě.</span><span class="sxs-lookup"><span data-stu-id="cab89-214">That indicates the survey hasn't been given to any respondents yet.</span></span> <span data-ttu-id="cab89-215">Všimněte si, že jsou přidávány respondentů, dokud dostatek vyjádřili souhlas.</span><span class="sxs-lookup"><span data-stu-id="cab89-215">Notice that respondents are added until enough have consented.</span></span>

<span data-ttu-id="cab89-216">Posledním krokem ke spuštění zjišťování je přidat volání k provedení zjišťování na konci `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="cab89-216">The last step to run the survey is to add a call to perform the survey at the end of the `Main` method:</span></span>

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a><span data-ttu-id="cab89-217">Zkontrolujte odpovědi v průzkumu</span><span class="sxs-lookup"><span data-stu-id="cab89-217">Examine survey responses</span></span>

<span data-ttu-id="cab89-218">Posledním krokem je zobrazit výsledky zjišťování.</span><span class="sxs-lookup"><span data-stu-id="cab89-218">The last step is to display survey results.</span></span> <span data-ttu-id="cab89-219">Přidáte kód pro většinu tříd, které jste zadali.</span><span class="sxs-lookup"><span data-stu-id="cab89-219">You'll add code to many of the classes you've written.</span></span> <span data-ttu-id="cab89-220">Tento kód ukazuje, jakou hodnotu rozlišování typy odkazů s možnou hodnotou Null a Null.</span><span class="sxs-lookup"><span data-stu-id="cab89-220">This code demonstrates the value of distinguishing nullable and non-nullable reference types.</span></span> <span data-ttu-id="cab89-221">Začněte přidáním následujících dvou s výrazem v těle členy `SurveyResponse` třídy:</span><span class="sxs-lookup"><span data-stu-id="cab89-221">Start by adding the following two expression-bodied members to the `SurveyResponse` class:</span></span>

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

<span data-ttu-id="cab89-222">Protože `surveyResponses` je typem odkazu Null před zrušením odkazu nevzniká žádné kontroly.</span><span class="sxs-lookup"><span data-stu-id="cab89-222">Because `surveyResponses` is a non-nullable reference type, no checks are necessary before de-referencing it.</span></span> <span data-ttu-id="cab89-223">`Answer` Metoda vrátí řetězec null, proto zvolte přetížení `GetValueOrDefault` , který přijímá jako druhý argument pro výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cab89-223">The `Answer` method returns a non-nullable string, so choose the overload of `GetValueOrDefault` that takes a second argument for the default value.</span></span>

<span data-ttu-id="cab89-224">V dalším kroku přidejte tyto tři členy s výrazem v těle k `SurveyRun` třídy:</span><span class="sxs-lookup"><span data-stu-id="cab89-224">Next, add these three expression-bodied members to the `SurveyRun` class:</span></span>

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

<span data-ttu-id="cab89-225">`AllParticipants` Člen musí vzít v úvahu, který `respondents` proměnná může mít hodnotu null, ale vrácená hodnota nemůže mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="cab89-225">The `AllParticipants` member must take into account that the `respondents` variable might be null, but the return value can't be null.</span></span> <span data-ttu-id="cab89-226">Pokud změníte tento výraz tak, že odeberete `??` a prázdné sekvenci, který následuje, kompilátor vás upozorní, metoda může vrátit `null` a jeho návratový signatura vrátí hodnotu Null typu.</span><span class="sxs-lookup"><span data-stu-id="cab89-226">If you change that expression by removing the `??` and the empty sequence that follows, the compiler warns you the method might return `null` and its return signature returns a non-nullable type.</span></span>

<span data-ttu-id="cab89-227">Nakonec přidejte následující smyčku v dolní části `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="cab89-227">Finally, add the following loop at the bottom of the `Main` method:</span></span>

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

<span data-ttu-id="cab89-228">Není potřeba vybírat žádnou `null` kontroluje v tomto kódu, protože základní rozhraní jste navrhli tak, aby všechny návratové typy neumožňující hodnotu odkazu.</span><span class="sxs-lookup"><span data-stu-id="cab89-228">You don't need any `null` checks in this code because you've designed the underlying interfaces so that they all return non-nullable reference types.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="cab89-229">Získat kód</span><span class="sxs-lookup"><span data-stu-id="cab89-229">Get the code</span></span>

<span data-ttu-id="cab89-230">Můžete získat kód pro dokončení kurzu z našich [ukázky](https://github.com/dotnet/samples) úložiště v [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) složky.</span><span class="sxs-lookup"><span data-stu-id="cab89-230">You can get the code for the finished tutorial from our [samples](https://github.com/dotnet/samples) repository in the [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folder.</span></span>

<span data-ttu-id="cab89-231">Experimentujte změnou deklarace typů mezi typy s možnou hodnotou Null a Null odkazů.</span><span class="sxs-lookup"><span data-stu-id="cab89-231">Experiment by changing the type declarations between nullable and non-nullable reference types.</span></span> <span data-ttu-id="cab89-232">Naleznete v tématu Jak, který generuje upozornění jinou zajistit Nepřistupujte omylem `null`.</span><span class="sxs-lookup"><span data-stu-id="cab89-232">See how that generates different warnings to ensure you don't accidentally dereference a `null`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="cab89-233">Další kroky</span><span class="sxs-lookup"><span data-stu-id="cab89-233">Next steps</span></span>

<span data-ttu-id="cab89-234">Další informace a migrujte existující aplikace pro použití typů s povolenou hodnotou Null odkazu:</span><span class="sxs-lookup"><span data-stu-id="cab89-234">Learn more by migrating an existing application to use nullable reference types:</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="cab89-235">Upgrade aplikace pro použití s možnou hodnotou Null odkazové typy</span><span class="sxs-lookup"><span data-stu-id="cab89-235">Upgrade an application to use nullable reference types</span></span>](upgrade-to-nullable-references.md)

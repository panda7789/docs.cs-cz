---
title: Návrh s typy s možnou hodnotou Null odkazů
description: V tomto kurzu pokročilé obsahuje úvod do typy s možnou hodnotou Null odkazů. Se dozvíte, jak vyjádřit svůj návrh úmyslem při může mít hodnotu null referenční hodnoty a nechat kompilátor vynucovat, když nemohou být null.
ms.date: 12/03/2018
ms.custom: mvc
ms.openlocfilehash: 7e4cb423658287e5260770a680f189c227b9cd01
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53156492"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="d63a8-104">Kurz: Máte v úmyslu návrhu Express jasněji s typy s možnou hodnotou Null a Null reference</span><span class="sxs-lookup"><span data-stu-id="d63a8-104">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>

<span data-ttu-id="d63a8-105">C#8 zavádí **typy s možnou hodnotou Null odkazů**, kterou doplněk referenční typy stejným způsobem jako typy s možnou hodnotou doplňují typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="d63a8-105">C# 8 introduces **nullable reference types**, which complement reference types the same way nullable value types complement value types.</span></span> <span data-ttu-id="d63a8-106">Deklarujete proměnnou **typ s možnou hodnotou Null odkazu** připojením `?` typu.</span><span class="sxs-lookup"><span data-stu-id="d63a8-106">You declare a variable to be a **nullable reference type** by appending a `?` to the type.</span></span> <span data-ttu-id="d63a8-107">Například `string?` představuje s povolenou hodnotou Null `string`.</span><span class="sxs-lookup"><span data-stu-id="d63a8-107">For example, `string?` represents a nullable `string`.</span></span> <span data-ttu-id="d63a8-108">Pro větší přehlednost express máte v úmyslu návrhu můžete použít tyto nové typy: Některé proměnné *musí mít vždy hodnotu*, ostatní *pravděpodobně chybí hodnota*.</span><span class="sxs-lookup"><span data-stu-id="d63a8-108">You can use these new types to more clearly express your design intent: some variables *must always have a value*, others *may be missing a value*.</span></span>

<span data-ttu-id="d63a8-109">V tomto kurzu se dozvíte jak:</span><span class="sxs-lookup"><span data-stu-id="d63a8-109">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="d63a8-110">Typy s možnou hodnotou Null a Null reference začlenit do vašich návrhů</span><span class="sxs-lookup"><span data-stu-id="d63a8-110">Incorporate nullable and non-nullable reference types into your designs</span></span>
> * <span data-ttu-id="d63a8-111">Povolení kontroly typů s povolenou hodnotou Null reference v rámci vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="d63a8-111">Enable nullable reference type checks throughout your code.</span></span>
> * <span data-ttu-id="d63a8-112">Psaní kódu, kde kompilátor vynucuje tato rozhodnutí o návrhu.</span><span class="sxs-lookup"><span data-stu-id="d63a8-112">Write code where the compiler enforces those design decisions.</span></span>
> * <span data-ttu-id="d63a8-113">Použití s možnou hodnotou Null odkaz funkce v vlastní návrhy</span><span class="sxs-lookup"><span data-stu-id="d63a8-113">Use the nullable reference feature in your own designs</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d63a8-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d63a8-114">Prerequisites</span></span>

<span data-ttu-id="d63a8-115">Budete muset nastavit počítač pro spuštění .NET Core, včetně C# 8.0 beta verze kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="d63a8-115">You’ll need to set up your machine to run .NET Core, including the C# 8.0 beta compiler.</span></span> <span data-ttu-id="d63a8-116">C# 8 beta verze kompilátoru je k dispozici s [Visual Studio 2019 ve verzi preview 1](https://visualstudio.microsoft.com/vs/preview/), nebo [.NET Core 3.0 ve verzi preview 1](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="d63a8-116">The C# 8 beta compiler is available with [Visual Studio 2019 preview 1](https://visualstudio.microsoft.com/vs/preview/), or [.NET Core 3.0 preview 1](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="d63a8-117">Tento kurz předpokládá, že jste obeznámeni s C# a .NET, včetně sady Visual Studio nebo rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d63a8-117">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="incorporate-nullable-reference-types-into-your-designs"></a><span data-ttu-id="d63a8-118">Typy s možnou hodnotou Null odkazů začlenit do vašich návrhů</span><span class="sxs-lookup"><span data-stu-id="d63a8-118">Incorporate nullable reference types into your designs</span></span>

<span data-ttu-id="d63a8-119">V tomto kurzu vytvoříte knihovnu, která modeluje spouštění průzkumu.</span><span class="sxs-lookup"><span data-stu-id="d63a8-119">In this tutorial, you'll build a library that models running a survey.</span></span> <span data-ttu-id="d63a8-120">Kód používá k reprezentaci koncepty skutečné typy s možnou hodnotou Null odkazů a typy neumožňující hodnotu odkazu.</span><span class="sxs-lookup"><span data-stu-id="d63a8-120">The code uses both nullable reference types and non-nullable reference types to represent the real-world concepts.</span></span> <span data-ttu-id="d63a8-121">Dotazy zjišťování může mít nikdy hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="d63a8-121">The survey questions can never be null.</span></span> <span data-ttu-id="d63a8-122">Respondenta pravděpodobně nechcete odpověď na otázku.</span><span class="sxs-lookup"><span data-stu-id="d63a8-122">A respondent might prefer not to answer a question.</span></span> <span data-ttu-id="d63a8-123">V tomto případě může mít hodnotu null odpovědi.</span><span class="sxs-lookup"><span data-stu-id="d63a8-123">The responses might be null in this case.</span></span>

<span data-ttu-id="d63a8-124">Kód, který napíšete pro tuto ukázku vyjadřuje tohoto záměru a kompilátor vynucuje tohoto záměru.</span><span class="sxs-lookup"><span data-stu-id="d63a8-124">The code you'll write for this sample expresses that intent, and the compiler enforces that intent.</span></span>

## <a name="create-the-application-and-enable-nullable-reference-types"></a><span data-ttu-id="d63a8-125">Vytvoření aplikace a povolení typy s možnou hodnotou Null odkazů</span><span class="sxs-lookup"><span data-stu-id="d63a8-125">Create the application and enable nullable reference types</span></span>

<span data-ttu-id="d63a8-126">Vytvořte novou konzolovou aplikaci v sadě Visual Studio nebo z příkazového řádku pomocí `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="d63a8-126">Create a new console application either in Visual Studio or from the command line using `dotnet new console`.</span></span> <span data-ttu-id="d63a8-127">Pojmenujte aplikaci `NullableIntroduction`.</span><span class="sxs-lookup"><span data-stu-id="d63a8-127">Name the application `NullableIntroduction`.</span></span> <span data-ttu-id="d63a8-128">Po vytvoření aplikace, budete muset povolit C# 8 beta verze funkce.</span><span class="sxs-lookup"><span data-stu-id="d63a8-128">Once you've created the application, you'll need to enable C# 8 beta features.</span></span> <span data-ttu-id="d63a8-129">Otevřít `csproj` a přidejte `LangVersion` elementu `PropertyGroup` element:</span><span class="sxs-lookup"><span data-stu-id="d63a8-129">Open the `csproj` file, and add a `LangVersion` element to the `PropertyGroup` element:</span></span>

```xml
<LangVersion>8.0</LangVersion>
```

<span data-ttu-id="d63a8-130">Alternativně můžete použít vlastnosti projektu sady Visual Studio povolit C# 8.</span><span class="sxs-lookup"><span data-stu-id="d63a8-130">Alternatively, you can use the Visual Studio project properties to enable C# 8.</span></span> <span data-ttu-id="d63a8-131">V Průzkumníku řešení klikněte pravým tlačítkem na uzel projektu, vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d63a8-131">In Solution Explorer, right click on the project node, select **Properties**.</span></span> <span data-ttu-id="d63a8-132">Vyberte **sestavení** kartu a klikněte na tlačítko **Upřesnit...** . V rozevírací nabídce pro jazykovou verzi, vyberte  **C# 8.0 (beta verze)**.</span><span class="sxs-lookup"><span data-stu-id="d63a8-132">Then, select the **build** tab, and click **Advanced...**. In the dropdown for language version, select **C# 8.0 (beta)**.</span></span>

<span data-ttu-id="d63a8-133">Třeba pokud se rozhodnete do **typy s možnou hodnotou Null odkazů** funkce, dokonce i v C# 8 projekty.</span><span class="sxs-lookup"><span data-stu-id="d63a8-133">You must opt into the **nullable reference types** feature, even in C# 8 projects.</span></span> <span data-ttu-id="d63a8-134">Důvodem je, že když je tato funkce zapnutá, budou existující deklarace proměnných odkazu **typy neumožňující hodnotu odkazu**.</span><span class="sxs-lookup"><span data-stu-id="d63a8-134">That's because once the feature is turned on, existing reference variable declarations become **non-nullable reference types**.</span></span> <span data-ttu-id="d63a8-135">Když toto rozhodnutí se vám umožní najít problémy, kde stávající kód nemusí mít správné zjednodušená kontrola hodnot null, se nemusí přesně odrážet váš původním záměr návrhu.</span><span class="sxs-lookup"><span data-stu-id="d63a8-135">While that decision will help find issues where existing code may not have proper null-checks, it may not accurately reflect your original design intent.</span></span> <span data-ttu-id="d63a8-136">Zapnout funkci pomocí nové direktivy pragma:</span><span class="sxs-lookup"><span data-stu-id="d63a8-136">You turn on the feature with a new pragma:</span></span>

```csharp
#nullable enable
```

<span data-ttu-id="d63a8-137">Předchozí – Direktiva pragma můžete přidat libovolné místo ve zdrojovém souboru a je zapnutá funkce typ s možnou hodnotou Null odkaz z tohoto bodu.</span><span class="sxs-lookup"><span data-stu-id="d63a8-137">You can add the preceding pragma anywhere in a source file, and the nullable reference type feature is turned on from that point.</span></span> <span data-ttu-id="d63a8-138">Direktivy pragma podporuje také `disable` argument pro funkci vypnout.</span><span class="sxs-lookup"><span data-stu-id="d63a8-138">The pragma also supports the `disable` argument to turn off the feature.</span></span>

<span data-ttu-id="d63a8-139">Můžete také zapnout **typy s možnou hodnotou Null odkazů** pro celý projekt tak, že přidáte následující element souboru .csproj, třeba hned za `LangVersion` element, který povolené C# 8.0:</span><span class="sxs-lookup"><span data-stu-id="d63a8-139">You can also turn on **nullable reference types** for an entire project by adding the following element to your .csproj file, for example, immediately following the `LangVersion` element that enabled C# 8.0:</span></span>

```xml
<NullableReferenceTypes>true</NullableReferenceTypes>
```

### <a name="design-the-types-for-the-application"></a><span data-ttu-id="d63a8-140">Navrhování typů pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="d63a8-140">Design the types for the application</span></span>

<span data-ttu-id="d63a8-141">Tato aplikace průzkumu vyžaduje vytvoření počet tříd:</span><span class="sxs-lookup"><span data-stu-id="d63a8-141">This survey application requires creating a number of classes:</span></span>

- <span data-ttu-id="d63a8-142">Třída, která modeluje seznam dotazů.</span><span class="sxs-lookup"><span data-stu-id="d63a8-142">A class that models the list of questions.</span></span>
- <span data-ttu-id="d63a8-143">Třída, která modeluje seznam osob kontaktovat průzkum.</span><span class="sxs-lookup"><span data-stu-id="d63a8-143">A class that models a list of people contacted for the survey.</span></span>
- <span data-ttu-id="d63a8-144">Třída, která modeluje odpovědi od osoby, která trvala zjišťování.</span><span class="sxs-lookup"><span data-stu-id="d63a8-144">A class that models the answers from a person that took the survey.</span></span>

<span data-ttu-id="d63a8-145">Tyto typy způsobí, že použití s možnou hodnotou Null a typy neumožňující hodnotu odkazu vyjádřit členy, které jsou požadovány a členy, které jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="d63a8-145">These types will make use of both nullable and non-nullable reference types to express which members are required and which members are optional.</span></span> <span data-ttu-id="d63a8-146">Typy s možnou hodnotou Null odkazů komunikovat, který jasně návrh záměr:</span><span class="sxs-lookup"><span data-stu-id="d63a8-146">Nullable reference types communicate that design intent clearly:</span></span>

- <span data-ttu-id="d63a8-147">Otázky, které jsou součástí zjišťování může mít nikdy hodnotu null: Nemá smysl pro prázdný dotaz.</span><span class="sxs-lookup"><span data-stu-id="d63a8-147">The questions that are part of the survey can never be null: It makes no sense to ask an empty question.</span></span>
- <span data-ttu-id="d63a8-148">Respondentů může mít nikdy hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="d63a8-148">The respondents can never be null.</span></span> <span data-ttu-id="d63a8-149">Budete chtít sledovat lidé, se kterými vás kontaktovat, dokonce i respondentů, které odmítl se zúčastnit.</span><span class="sxs-lookup"><span data-stu-id="d63a8-149">You'll want to track people you contacted, even respondents that declined to participate.</span></span>
- <span data-ttu-id="d63a8-150">Každá odpověď na dotaz může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="d63a8-150">Any response to a question may be null.</span></span> <span data-ttu-id="d63a8-151">Odpovědi na některé nebo všechny otázky můžete odmítnout respondentů.</span><span class="sxs-lookup"><span data-stu-id="d63a8-151">Respondents can decline to answer some or all questions.</span></span>

<span data-ttu-id="d63a8-152">Pokud jste naprogramovat v C#, může být proto zvyklí na referenční typy, které umožňují hodnoty null, které jste si asi nevšimli představují další příležitosti k deklarování Null instancemi:</span><span class="sxs-lookup"><span data-stu-id="d63a8-152">If you've programmed in C#, you may be so accustomed to reference types that allow null values that you may have missed other opportunities to declare non-nullable instances:</span></span>

- <span data-ttu-id="d63a8-153">Kolekci otázek by měl mít hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="d63a8-153">The collection of questions should be non-nullable.</span></span>
- <span data-ttu-id="d63a8-154">Kolekce respondentů by měl mít hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="d63a8-154">The collection of respondents should be non-nullable.</span></span>

<span data-ttu-id="d63a8-155">Při psaní kódu, uvidíte, že typ odkazu null jako výchozí pro odkazy se vyhnete běžných chyb, které by mohly vést k výjimkám odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="d63a8-155">As you write the code, you'll see that a non-nullable reference type as the default for references avoids common mistakes that could lead to null reference exceptions.</span></span> <span data-ttu-id="d63a8-156">Lekce jeden z tohoto kurzu je, že jste provedli rozhodnutí o tom, které proměnné může nebo nemůže mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="d63a8-156">One lesson from this tutorial is that you made decisions about which variables could or could not be null.</span></span> <span data-ttu-id="d63a8-157">Jazyk neposkytl syntaxe express tato rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="d63a8-157">The language didn't provide syntax to express those decisions.</span></span> <span data-ttu-id="d63a8-158">Nyní dělá.</span><span class="sxs-lookup"><span data-stu-id="d63a8-158">Now it does.</span></span>

<span data-ttu-id="d63a8-159">Aplikace, kterou vytvoříte, bude proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="d63a8-159">The app you'll build will do the following steps:</span></span>

1. <span data-ttu-id="d63a8-160">Vytvořit průzkum a přidejte do ní dotazy.</span><span class="sxs-lookup"><span data-stu-id="d63a8-160">Create a survey and add questions to it.</span></span>
1. <span data-ttu-id="d63a8-161">Vytvoření sady pseudonáhodné respondentů průzkum.</span><span class="sxs-lookup"><span data-stu-id="d63a8-161">Create a pseudo-random set of respondents for the survey.</span></span>
1. <span data-ttu-id="d63a8-162">Kontaktujte respondentů, dokud velikost dokončené průzkumu dosáhne cíle číslo.</span><span class="sxs-lookup"><span data-stu-id="d63a8-162">Contact respondents until the completed survey size reaches the goal number.</span></span>
1. <span data-ttu-id="d63a8-163">Vypsat důležitých statistik o odpovědi průzkumu.</span><span class="sxs-lookup"><span data-stu-id="d63a8-163">Write out important statistics on the survey responses.</span></span>

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a><span data-ttu-id="d63a8-164">Vytvářejte zjišťování s typy s možnou hodnotou Null a Null</span><span class="sxs-lookup"><span data-stu-id="d63a8-164">Build the survey with nullable and non-nullable types</span></span>

<span data-ttu-id="d63a8-165">První kód, který napíšete vytvoří zjišťování.</span><span class="sxs-lookup"><span data-stu-id="d63a8-165">The first code you'll write creates the survey.</span></span> <span data-ttu-id="d63a8-166">Napíšete třídy modelu otázky průzkumu a zjišťování spustit.</span><span class="sxs-lookup"><span data-stu-id="d63a8-166">You'll write classes to model a survey question and a survey run.</span></span> <span data-ttu-id="d63a8-167">Vaším dotazníkem má tři typy dotazů, formát odpovědi liší: Ano/Ne odpovědi číslo odpovědi a text odpovědi.</span><span class="sxs-lookup"><span data-stu-id="d63a8-167">Your survey has three types of questions, distinguished by the format of the answer: Yes/No answers, number answers, and text answers.</span></span> <span data-ttu-id="d63a8-168">Vytvoření `public` `SurveyQuestion` třídy.</span><span class="sxs-lookup"><span data-stu-id="d63a8-168">Create a `public` `SurveyQuestion` class.</span></span> <span data-ttu-id="d63a8-169">Zahrnout `#nullable enable` – Direktiva pragma ihned po `using` příkazy:</span><span class="sxs-lookup"><span data-stu-id="d63a8-169">Include the `#nullable enable` pragma immediately after the `using` statements:</span></span>

```csharp
#nullable enable
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

<span data-ttu-id="d63a8-170">Přidání `#nullable enable` – Direktiva pragma znamená, že kompilátor interpretuje každý odkaz na typ deklarace proměnné jako **Null** typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="d63a8-170">Adding the `#nullable enable` pragma means the compiler interprets every reference type variable declaration as a **non-nullable** reference type.</span></span> <span data-ttu-id="d63a8-171">První upozornění můžete zobrazit tak, že přidáte vlastnosti text otázky a typ otázku, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="d63a8-171">You can see your first warning by adding properties for the question text and the type of question, as shown in the following code:</span></span>

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

<span data-ttu-id="d63a8-172">Protože nebyla inicializována `QuestionText`, kompilátor vyvolá upozornění, že vlastnost se zakázanou nebyla inicializována.</span><span class="sxs-lookup"><span data-stu-id="d63a8-172">Because you haven't initialized `QuestionText`, the compiler issues a warning that a non-nullable property hasn't been initialized.</span></span> <span data-ttu-id="d63a8-173">Vyžaduje otázku text, který má být jiná než null, proto přidejte konstruktor k inicializaci jeho návrhu a `QuestionType` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d63a8-173">Your design requires the question text to be non-null, so you add a constructor to initialize it and the `QuestionType` value as well.</span></span> <span data-ttu-id="d63a8-174">V definici hotové třídy bude vypadat jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="d63a8-174">The finished class definition looks like the following code:</span></span>

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

<span data-ttu-id="d63a8-175">Přidáním konstruktoru odebere upozornění.</span><span class="sxs-lookup"><span data-stu-id="d63a8-175">Adding the constructor removes the warning.</span></span> <span data-ttu-id="d63a8-176">Argument konstruktoru je také typu Null odkaz, takže kompilátor nebude vydat upozornění.</span><span class="sxs-lookup"><span data-stu-id="d63a8-176">The constructor argument is also a non-nullable reference type, so the compiler doesn't issue any warnings.</span></span>

<span data-ttu-id="d63a8-177">Dále vytvořte `public` třídu s názvem `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="d63a8-177">Next, create a `public` class named `SurveyRun`.</span></span> <span data-ttu-id="d63a8-178">Zahrnout `#nullable enable` následující direktivy pragma `using` příkazy.</span><span class="sxs-lookup"><span data-stu-id="d63a8-178">Include the `#nullable enable` pragma following the `using` statements.</span></span> <span data-ttu-id="d63a8-179">Tato třída obsahuje seznam `SurveyQuestion` objekty a metody pro přidání otázky průzkumu, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="d63a8-179">This class contains a list of `SurveyQuestion` objects and methods to add questions to the survey, as shown in the following code:</span></span>

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

<span data-ttu-id="d63a8-180">Stejně jako dříve je nutné inicializovat objektem seznamu k nenulovou hodnotu nebo kompilátor vyvolá upozornění.</span><span class="sxs-lookup"><span data-stu-id="d63a8-180">As before, you must initialize the list object to a non-null value or the compiler issues a warning.</span></span> <span data-ttu-id="d63a8-181">Neexistují žádné kontroly hodnoty null v druhé přetížení metody `AddQuestion` vzhledem k tomu, že podle potřeby: Deklarujete tuto proměnnou k umožňovat hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="d63a8-181">There are no null checks in the second overload of `AddQuestion` because they aren't needed: You've declared that variable to be non-nullable.</span></span> <span data-ttu-id="d63a8-182">Jeho hodnota nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="d63a8-182">Its value can't be `null`.</span></span>

<span data-ttu-id="d63a8-183">Přepnout na `Program.cs` ve svém editoru a nahraďte obsah `Main` s následujícími řádky kódu:</span><span class="sxs-lookup"><span data-stu-id="d63a8-183">Switch to `Program.cs` in your editor and replace the contents of `Main` with the following lines of code:</span></span>

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

<span data-ttu-id="d63a8-184">Bez `#nullable enable` – Direktiva pragma se v horní části souboru, kompilátor nebude vyvolávat tato upozornění při předání `null` jako text `AddQuestion` argument.</span><span class="sxs-lookup"><span data-stu-id="d63a8-184">Without the `#nullable enable` pragma at the top of the file, the compiler doesn't issue a warning when you pass `null` as the text for the `AddQuestion` argument.</span></span> <span data-ttu-id="d63a8-185">To opravit přidáním `#nullable enable` následující `using` příkazu.</span><span class="sxs-lookup"><span data-stu-id="d63a8-185">Fix that by adding `#nullable enable` following the `using` statement.</span></span> <span data-ttu-id="d63a8-186">Vyzkoušet tak, že přidáte následující řádek, který `Main`:</span><span class="sxs-lookup"><span data-stu-id="d63a8-186">Try it by adding the following line to `Main`:</span></span>

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a><span data-ttu-id="d63a8-187">Vytvoření respondentů a získejte odpovědi na průzkum</span><span class="sxs-lookup"><span data-stu-id="d63a8-187">Create respondents and get answers to the survey</span></span>

<span data-ttu-id="d63a8-188">Dále napište kód, který generuje odpovědi na tento průzkum.</span><span class="sxs-lookup"><span data-stu-id="d63a8-188">Next, write the code that generates answers to the survey.</span></span> <span data-ttu-id="d63a8-189">To zahrnuje několik malé úlohy:</span><span class="sxs-lookup"><span data-stu-id="d63a8-189">This involves several small tasks:</span></span>

1. <span data-ttu-id="d63a8-190">Vytvořte metodu, která vytváří objekty respondentů.</span><span class="sxs-lookup"><span data-stu-id="d63a8-190">Build a method that generates respondent objects.</span></span> <span data-ttu-id="d63a8-191">Představují položené odborníky vyplnit tento průzkum.</span><span class="sxs-lookup"><span data-stu-id="d63a8-191">These represent people asked to fill out the survey.</span></span>
1. <span data-ttu-id="d63a8-192">Vytvořte logiku pro simulaci kladení otázek respondentům a shromažďování odpovědi nebo poznamenat, že jste nenašli odpověď respondent.</span><span class="sxs-lookup"><span data-stu-id="d63a8-192">Build logic to simulate asking the questions to a respondent and collecting answers or noting that a respondent didn't answer.</span></span>
1. <span data-ttu-id="d63a8-193">Opakujte, dokud dostatek respondentů získejte odpovědi na tento průzkum.</span><span class="sxs-lookup"><span data-stu-id="d63a8-193">Repeat until enough respondents have answered the survey.</span></span>

<span data-ttu-id="d63a8-194">Budete potřebovat třídy představují odpověď na průzkum, takže nyní přidat.</span><span class="sxs-lookup"><span data-stu-id="d63a8-194">You'll need a class to represent a survey response, so add that now.</span></span> <span data-ttu-id="d63a8-195">Povolte podporu s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="d63a8-195">Enable nullable support.</span></span> <span data-ttu-id="d63a8-196">Přidat `Id` vlastnost a konstruktor, který inicializuje ji, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="d63a8-196">Add an `Id` property and a constructor that initializes it, as shown in the following code:</span></span>

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

<span data-ttu-id="d63a8-197">V dalším kroku přidejte `static` metodu pro vytvoření nové účastníky vygenerováním náhodné ID:</span><span class="sxs-lookup"><span data-stu-id="d63a8-197">Next, add a `static` method to create new participants by generating a random ID:</span></span>

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

<span data-ttu-id="d63a8-198">Hlavní zodpovědností této třídy je generují odpovědi účastníka na otázky v průzkumu.</span><span class="sxs-lookup"><span data-stu-id="d63a8-198">The main responsibility of this class is to generate the responses for a participant to the questions in the survey.</span></span> <span data-ttu-id="d63a8-199">Tuto odpovědnost zahrnuje několik kroků:</span><span class="sxs-lookup"><span data-stu-id="d63a8-199">This responsibility has a few steps:</span></span>

1. <span data-ttu-id="d63a8-200">Požádejte o účast na průzkumu.</span><span class="sxs-lookup"><span data-stu-id="d63a8-200">Ask for participation in the survey.</span></span> <span data-ttu-id="d63a8-201">Pokud není souhlas uživatele, vrátí odpověď chybí (nebo null).</span><span class="sxs-lookup"><span data-stu-id="d63a8-201">If the person doesn't consent, return a missing (or null) response.</span></span>
1. <span data-ttu-id="d63a8-202">Každý dotaz a odpověď si poznamenejte.</span><span class="sxs-lookup"><span data-stu-id="d63a8-202">Ask each question and record the answer.</span></span> <span data-ttu-id="d63a8-203">Každou odpověď může být také chybí (nebo null).</span><span class="sxs-lookup"><span data-stu-id="d63a8-203">Each answer may also be missing (or null).</span></span>

<span data-ttu-id="d63a8-204">Přidejte následující kód, který vaše `SurveyRespondent` třídy:</span><span class="sxs-lookup"><span data-stu-id="d63a8-204">Add the following code to your `SurveyRespondent` class:</span></span>

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

<span data-ttu-id="d63a8-205">Úložiště pro zjišťování odpovědi je `Dictionary<int, string>?`, která udává, že může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="d63a8-205">The storage for the survey answers is a `Dictionary<int, string>?`, indicating that it may be null.</span></span> <span data-ttu-id="d63a8-206">Chcete-li deklarovat vaším záměrem návrhu, kompilátoru a každému, kdo čte kód později používáte novou funkci jazyka.</span><span class="sxs-lookup"><span data-stu-id="d63a8-206">You're using the new language feature to declare your design intent, both to the compiler and to anyone reading your code later.</span></span> <span data-ttu-id="d63a8-207">Pokud jste někdy přistoupit přes ukazatel `surveyResponses` bez provedení kontroly nejprve na hodnotu null, zobrazí se upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="d63a8-207">If you ever dereference `surveyResponses` without checking for the null value first, you'll get a compiler warning.</span></span> <span data-ttu-id="d63a8-208">Vám upozornění `AnswerSurvey` metoda protože kompilátor může určit, `surveyResponses` proměnné byl nastaven na nenulovou hodnotu výše.</span><span class="sxs-lookup"><span data-stu-id="d63a8-208">You don't get a warning in the `AnswerSurvey` method because the compiler can determine the `surveyResponses` variable was set to a non-null value above.</span></span>

<span data-ttu-id="d63a8-209">Dále je třeba napsat `PerformSurvey` metodu `SurveyRun` třídy.</span><span class="sxs-lookup"><span data-stu-id="d63a8-209">Next, you need to write the `PerformSurvey` method in the `SurveyRun` class.</span></span> <span data-ttu-id="d63a8-210">Přidejte následující kód `SurveyRun` třídy:</span><span class="sxs-lookup"><span data-stu-id="d63a8-210">Add the following code in the `SurveyRun` class:</span></span>

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

<span data-ttu-id="d63a8-211">Znovu sem, podle vašeho výběru s povolenou hodnotou Null `List<SurveyResponse>?` označuje odpověď může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="d63a8-211">Here again, your choice of a nullable `List<SurveyResponse>?` indicates the response may be null.</span></span> <span data-ttu-id="d63a8-212">Označuje, že tento průzkum ještě bylo přiděleno žádné respondentů ještě.</span><span class="sxs-lookup"><span data-stu-id="d63a8-212">That indicates the survey hasn't been given to any respondents yet.</span></span> <span data-ttu-id="d63a8-213">Všimněte si, že jsou přidávány respondentů, dokud dostatek vyjádřili souhlas.</span><span class="sxs-lookup"><span data-stu-id="d63a8-213">Notice that respondents are added until enough have consented.</span></span>

<span data-ttu-id="d63a8-214">Posledním krokem ke spuštění zjišťování je přidat volání k provedení zjišťování na konci `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="d63a8-214">The last step to run the survey is to add a call to perform the survey at the end of the `Main` method:</span></span>

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a><span data-ttu-id="d63a8-215">Zkontrolujte odpovědi v průzkumu</span><span class="sxs-lookup"><span data-stu-id="d63a8-215">Examine survey responses</span></span>

<span data-ttu-id="d63a8-216">Posledním krokem je zobrazit výsledky zjišťování.</span><span class="sxs-lookup"><span data-stu-id="d63a8-216">The last step is to display survey results.</span></span> <span data-ttu-id="d63a8-217">Přidáte kód pro většinu tříd, které jste zadali.</span><span class="sxs-lookup"><span data-stu-id="d63a8-217">You'll add code to many of the classes you've written.</span></span> <span data-ttu-id="d63a8-218">Tento kód ukazuje, jakou hodnotu rozlišování typy odkazů s možnou hodnotou Null a Null.</span><span class="sxs-lookup"><span data-stu-id="d63a8-218">This code demonstrates the value of distinguishing nullable and non-nullable reference types.</span></span> <span data-ttu-id="d63a8-219">Začněte přidáním následujících dvou s výrazem v těle členy `SurveyResponse` třídy:</span><span class="sxs-lookup"><span data-stu-id="d63a8-219">Start by adding the following two expression-bodied members to the `SurveyResponse` class:</span></span>

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

<span data-ttu-id="d63a8-220">Protože `surveyResponses` se zakázanou odkaz, typ žádné kontroly jsou nezbytné před zrušením odkazu.</span><span class="sxs-lookup"><span data-stu-id="d63a8-220">Because `surveyResponses` is a non-nullable reference, type no checks are necessary before de-referencing it.</span></span> <span data-ttu-id="d63a8-221">`Answer` Metoda vrátí řetězec null, proto zvolte přetížení `GetValueOrDefault` , který přijímá jako druhý argument pro výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d63a8-221">The `Answer` method returns a non-nullable string, so choose the overload of `GetValueOrDefault` that takes a second argument for the default value.</span></span>

<span data-ttu-id="d63a8-222">V dalším kroku přidejte tyto tři členy s výrazem v těle k `SurveyRun` třídy:</span><span class="sxs-lookup"><span data-stu-id="d63a8-222">Next, add these three expression-bodied members to the `SurveyRun` class:</span></span>

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

<span data-ttu-id="d63a8-223">`AllParticipants` Člen musí vzít v úvahu, který `respondents` proměnná může mít hodnotu null, ale vrácená hodnota nemůže mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="d63a8-223">The `AllParticipants` member must take into account that the `respondents` variable might be null, but the return value can't be null.</span></span> <span data-ttu-id="d63a8-224">Pokud změníte tento výraz tak, že odeberete `??` a prázdné sekvenci, který následuje, kompilátor vás upozorní, metoda může vrátit `null` a jeho návratový signatura vrátí hodnotu Null typu.</span><span class="sxs-lookup"><span data-stu-id="d63a8-224">If you change that expression by removing the `??` and the empty sequence that follows, the compiler warns you the method might return `null` and its return signature returns a non-nullable type.</span></span>

<span data-ttu-id="d63a8-225">Nakonec přidejte následující smyčku v dolní části `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="d63a8-225">Finally, add the following loop at the bottom of the `Main` method:</span></span>

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

<span data-ttu-id="d63a8-226">Není potřeba vybírat žádnou `null` kontroluje v tomto kódu, protože základní rozhraní jste navrhli tak, aby všechny návratové typy neumožňující hodnotu odkazu.</span><span class="sxs-lookup"><span data-stu-id="d63a8-226">You don't need any `null` checks in this code because you've designed the underlying interfaces so that they all return non-nullable reference types.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="d63a8-227">Získat kód</span><span class="sxs-lookup"><span data-stu-id="d63a8-227">Get the code</span></span>

<span data-ttu-id="d63a8-228">Můžete získat kód pro dokončení kurzu z našich [ukázky](https://github.com/dotnet/samples) úložiště v [csharp/IntroToNullables](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) složky.</span><span class="sxs-lookup"><span data-stu-id="d63a8-228">You can get the code for the finished tutorial from our [samples](https://github.com/dotnet/samples) repository in the [csharp/IntroToNullables](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folder.</span></span>

<span data-ttu-id="d63a8-229">Experimentujte změnou deklarace typů mezi typy s možnou hodnotou Null a Null odkazů.</span><span class="sxs-lookup"><span data-stu-id="d63a8-229">Experiment by changing the type declarations between nullable and non-nullable reference types.</span></span> <span data-ttu-id="d63a8-230">Naleznete v tématu Jak, který generuje upozornění jinou zajistit Nepřistupujte omylem `null`.</span><span class="sxs-lookup"><span data-stu-id="d63a8-230">See how that generates different warnings to ensure you don't accidentally dereference a `null`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d63a8-231">Další kroky</span><span class="sxs-lookup"><span data-stu-id="d63a8-231">Next steps</span></span>

<span data-ttu-id="d63a8-232">Další informace najdete přehled typů s povolenou hodnotou Null reference...</span><span class="sxs-lookup"><span data-stu-id="d63a8-232">Learn more by reading an overview of nullable reference types..</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="d63a8-233">Přehled odkazy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="d63a8-233">An overview of nullable references</span></span>](../nullable-references.md)

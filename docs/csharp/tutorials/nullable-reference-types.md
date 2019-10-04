---
title: Návrh s použitím typů odkazů s možnou hodnotou null
description: Tento rozšířený kurz poskytuje Úvod k odkazům s možnou hodnotou null. Naučíte se vyjádřit svůj návrh na to, kdy mohou být referenční hodnoty null, a nechat vynutit kompilátor, pokud nesmí mít hodnotu null.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 5327a9babdf080a535e292cdcefba6da9d0a725b
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834072"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="83749-104">Kurz: Seznámení s typem s možnou hodnotou null a odkazy, které neumožňují hodnotu null, je jasné.</span><span class="sxs-lookup"><span data-stu-id="83749-104">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>

<span data-ttu-id="83749-105">C#8 zavádí **typy odkazů s možnou hodnotou null**, které připlňují odkazové typy stejným způsobem jako typy hodnot s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="83749-105">C# 8 introduces **nullable reference types**, which complement reference types the same way nullable value types complement value types.</span></span> <span data-ttu-id="83749-106">Deklarujete proměnnou, která bude představovat **typ odkazu s možnou hodnotou null** připojením `?` k typu.</span><span class="sxs-lookup"><span data-stu-id="83749-106">You declare a variable to be a **nullable reference type** by appending a `?` to the type.</span></span> <span data-ttu-id="83749-107">Například `string?` představuje hodnotu null `string`.</span><span class="sxs-lookup"><span data-stu-id="83749-107">For example, `string?` represents a nullable `string`.</span></span> <span data-ttu-id="83749-108">Tyto nové typy můžete použít k přehlednějšímu vyjádření záměru návrhu: některé proměnné *musí mít vždy hodnotu*, jiné *mohou chybět hodnoty*.</span><span class="sxs-lookup"><span data-stu-id="83749-108">You can use these new types to more clearly express your design intent: some variables *must always have a value*, others *may be missing a value*.</span></span>

<span data-ttu-id="83749-109">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="83749-109">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="83749-110">Zahrnutí typů s možnou hodnotou null a odkazů, které neumožňují hodnotu null, do návrhů</span><span class="sxs-lookup"><span data-stu-id="83749-110">Incorporate nullable and non-nullable reference types into your designs</span></span>
> - <span data-ttu-id="83749-111">Povolí kontrolu typu odkazu s možnou hodnotou null v celém kódu.</span><span class="sxs-lookup"><span data-stu-id="83749-111">Enable nullable reference type checks throughout your code.</span></span>
> - <span data-ttu-id="83749-112">Napsat kód, kde kompilátor vynutil tato rozhodnutí o návrhu.</span><span class="sxs-lookup"><span data-stu-id="83749-112">Write code where the compiler enforces those design decisions.</span></span>
> - <span data-ttu-id="83749-113">Použití funkce odkazu s možnou hodnotou null ve vlastních návrzích</span><span class="sxs-lookup"><span data-stu-id="83749-113">Use the nullable reference feature in your own designs</span></span>

## <a name="prerequisites"></a><span data-ttu-id="83749-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83749-114">Prerequisites</span></span>

<span data-ttu-id="83749-115">Musíte nastavit počítač tak, aby běžel .NET Core, včetně kompilátoru C# 8,0.</span><span class="sxs-lookup"><span data-stu-id="83749-115">You'll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="83749-116">Kompilátor C# 8 beta je k dispozici v rámci sady [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)nebo [.NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="83749-116">The C# 8 beta compiler is available with [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="83749-117">V tomto kurzu se předpokládá, že C# máte zkušenosti s platformou a .NET, včetně sady Visual Studio nebo .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="83749-117">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="incorporate-nullable-reference-types-into-your-designs"></a><span data-ttu-id="83749-118">Zahrnutí typů odkazů s možnou hodnotou null do vašich návrhů</span><span class="sxs-lookup"><span data-stu-id="83749-118">Incorporate nullable reference types into your designs</span></span>

<span data-ttu-id="83749-119">V tomto kurzu vytvoříte knihovnu, ve které modely spouštějí průzkum.</span><span class="sxs-lookup"><span data-stu-id="83749-119">In this tutorial, you'll build a library that models running a survey.</span></span> <span data-ttu-id="83749-120">Kód používá odkaz s možnou hodnotou null a odkaz, který nepovoluje hodnotu null, aby představoval koncepty reálného světa.</span><span class="sxs-lookup"><span data-stu-id="83749-120">The code uses both nullable reference types and non-nullable reference types to represent the real-world concepts.</span></span> <span data-ttu-id="83749-121">Otázky průzkumu nemohou nikdy mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="83749-121">The survey questions can never be null.</span></span> <span data-ttu-id="83749-122">Respondent může chtít odpovědět na otázku.</span><span class="sxs-lookup"><span data-stu-id="83749-122">A respondent might prefer not to answer a question.</span></span> <span data-ttu-id="83749-123">V tomto případě mohou být odpovědi null.</span><span class="sxs-lookup"><span data-stu-id="83749-123">The responses might be null in this case.</span></span>

<span data-ttu-id="83749-124">Kód, který zapíšete pro tuto ukázku, tento záměr vyjádří a kompilátor vynutilí tento záměr.</span><span class="sxs-lookup"><span data-stu-id="83749-124">The code you'll write for this sample expresses that intent, and the compiler enforces that intent.</span></span>

## <a name="create-the-application-and-enable-nullable-reference-types"></a><span data-ttu-id="83749-125">Vytvoření aplikace a povolení typů odkazů s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="83749-125">Create the application and enable nullable reference types</span></span>

<span data-ttu-id="83749-126">Vytvořte novou konzolovou aplikaci buď v aplikaci Visual Studio, nebo z příkazového řádku pomocí `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="83749-126">Create a new console application either in Visual Studio or from the command line using `dotnet new console`.</span></span> <span data-ttu-id="83749-127">Pojmenujte aplikaci `NullableIntroduction`.</span><span class="sxs-lookup"><span data-stu-id="83749-127">Name the application `NullableIntroduction`.</span></span> <span data-ttu-id="83749-128">Po vytvoření aplikace budete muset povolit C# 8 beta funkcí.</span><span class="sxs-lookup"><span data-stu-id="83749-128">Once you've created the application, you'll need to enable C# 8 beta features.</span></span> <span data-ttu-id="83749-129">Otevřete soubor `csproj` a přidejte prvek `LangVersion` do prvku `PropertyGroup`.</span><span class="sxs-lookup"><span data-stu-id="83749-129">Open the `csproj` file and add a `LangVersion` element to the `PropertyGroup` element.</span></span> <span data-ttu-id="83749-130">Je nutné, abyste se přihlásili k funkci **typů odkazů s možnou hodnotou null** i v C# 8 projektech.</span><span class="sxs-lookup"><span data-stu-id="83749-130">You must opt into the **nullable reference types** feature, even in C# 8 projects.</span></span> <span data-ttu-id="83749-131">To je proto, že když je funkce zapnutá, existující deklarace referenčních proměnných se stanou odkazy, které neumožňují **hodnotu null**.</span><span class="sxs-lookup"><span data-stu-id="83749-131">That's because once the feature is turned on, existing reference variable declarations become **non-nullable reference types**.</span></span> <span data-ttu-id="83749-132">I když toto rozhodnutí pomůže najít problémy, kdy existující kód nemusí mít správné kontroly hodnoty null, nemusí přesně odpovídat původnímu záměru návrhu.</span><span class="sxs-lookup"><span data-stu-id="83749-132">While that decision will help find issues where existing code may not have proper null-checks, it may not accurately reflect your original design intent.</span></span> <span data-ttu-id="83749-133">Funkci zapnete tak, že nastavíte `Nullable` elementu na `enable`:</span><span class="sxs-lookup"><span data-stu-id="83749-133">You turn on the feature by setting the `Nullable` element to `enable`:</span></span>

```xml
<LangVersion>8.0</LangVersion>
<Nullable>enable</Nullable>
```

### <a name="design-the-types-for-the-application"></a><span data-ttu-id="83749-134">Návrh typů pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="83749-134">Design the types for the application</span></span>

<span data-ttu-id="83749-135">Tato aplikace průzkumu vyžaduje vytvoření řady tříd:</span><span class="sxs-lookup"><span data-stu-id="83749-135">This survey application requires creating a number of classes:</span></span>

- <span data-ttu-id="83749-136">Třída, která modeluje seznam otázek.</span><span class="sxs-lookup"><span data-stu-id="83749-136">A class that models the list of questions.</span></span>
- <span data-ttu-id="83749-137">Třída, která modeluje seznam lidí, kteří se na průzkum kontaktovali.</span><span class="sxs-lookup"><span data-stu-id="83749-137">A class that models a list of people contacted for the survey.</span></span>
- <span data-ttu-id="83749-138">Třída, která modeluje odpovědi od osoby, která provedla průzkum.</span><span class="sxs-lookup"><span data-stu-id="83749-138">A class that models the answers from a person that took the survey.</span></span>

<span data-ttu-id="83749-139">Tyto typy využívají odkaz s možnou hodnotou null a neumožňující použití odkazů, aby vyjádřili, které členy jsou požadovány a které členy jsou nepovinné.</span><span class="sxs-lookup"><span data-stu-id="83749-139">These types will make use of both nullable and non-nullable reference types to express which members are required and which members are optional.</span></span> <span data-ttu-id="83749-140">Typy odkazů s možnou hodnotou null oznamují, že záměr návrhu je jasný:</span><span class="sxs-lookup"><span data-stu-id="83749-140">Nullable reference types communicate that design intent clearly:</span></span>

- <span data-ttu-id="83749-141">Otázky, které jsou součástí průzkumu, nemůžou mít nikdy hodnotu null: nezáleží na tom, aby se dotazoval na prázdnou otázku.</span><span class="sxs-lookup"><span data-stu-id="83749-141">The questions that are part of the survey can never be null: It makes no sense to ask an empty question.</span></span>
- <span data-ttu-id="83749-142">Respondenti nikdy nemohou mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="83749-142">The respondents can never be null.</span></span> <span data-ttu-id="83749-143">Budete chtít sledovat lidi, ke kterým jste kontaktovali, dokonce i respondenti, kteří se odmítli zúčastnit.</span><span class="sxs-lookup"><span data-stu-id="83749-143">You'll want to track people you contacted, even respondents that declined to participate.</span></span>
- <span data-ttu-id="83749-144">Každá odpověď na otázku může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="83749-144">Any response to a question may be null.</span></span> <span data-ttu-id="83749-145">Respondenti mohou odmítnout odpověď na některé nebo všechny otázky.</span><span class="sxs-lookup"><span data-stu-id="83749-145">Respondents can decline to answer some or all questions.</span></span>

<span data-ttu-id="83749-146">Pokud jste napracovali v C#nástroji, možná jste zvyklí na odkazování na typy, které povolují hodnoty null, které jste pravděpodobně vynechali při deklaraci instancí, které neumožňují hodnotu null:</span><span class="sxs-lookup"><span data-stu-id="83749-146">If you've programmed in C#, you may be so accustomed to reference types that allow null values that you may have missed other opportunities to declare non-nullable instances:</span></span>

- <span data-ttu-id="83749-147">Kolekce dotazů by neměla mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="83749-147">The collection of questions should be non-nullable.</span></span>
- <span data-ttu-id="83749-148">Kolekce respondentů by neměla mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="83749-148">The collection of respondents should be non-nullable.</span></span>

<span data-ttu-id="83749-149">Při psaní kódu uvidíte, že typ odkazu, který neumožňuje hodnotu null, jako výchozí pro odkazy, zabraňuje běžným chybám, které by mohly vést k nulovým referenčním výjimkám.</span><span class="sxs-lookup"><span data-stu-id="83749-149">As you write the code, you'll see that a non-nullable reference type as the default for references avoids common mistakes that could lead to null reference exceptions.</span></span> <span data-ttu-id="83749-150">Jednou z lekcí tohoto kurzu je, že jste provedli rozhodnutí o tom, které proměnné by mohly nebo nemohly být null.</span><span class="sxs-lookup"><span data-stu-id="83749-150">One lesson from this tutorial is that you made decisions about which variables could or could not be null.</span></span> <span data-ttu-id="83749-151">Jazyk neposkytl syntaxi pro vyjádření těchto rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="83749-151">The language didn't provide syntax to express those decisions.</span></span> <span data-ttu-id="83749-152">Teď to dělá.</span><span class="sxs-lookup"><span data-stu-id="83749-152">Now it does.</span></span>

<span data-ttu-id="83749-153">Aplikace, kterou budete sestavovat, provede následující kroky:</span><span class="sxs-lookup"><span data-stu-id="83749-153">The app you'll build will do the following steps:</span></span>

1. <span data-ttu-id="83749-154">Vytvořte průzkum a přidejte do něj otázky.</span><span class="sxs-lookup"><span data-stu-id="83749-154">Create a survey and add questions to it.</span></span>
1. <span data-ttu-id="83749-155">Vytvořte pseudo náhodnou sadu respondentů pro průzkum.</span><span class="sxs-lookup"><span data-stu-id="83749-155">Create a pseudo-random set of respondents for the survey.</span></span>
1. <span data-ttu-id="83749-156">Kontaktujte respondenty, dokud velikost dokončeného průzkumu nedosáhne cílového čísla.</span><span class="sxs-lookup"><span data-stu-id="83749-156">Contact respondents until the completed survey size reaches the goal number.</span></span>
1. <span data-ttu-id="83749-157">Napište důležité statistiky pro odpovědi na dotazníky.</span><span class="sxs-lookup"><span data-stu-id="83749-157">Write out important statistics on the survey responses.</span></span>

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a><span data-ttu-id="83749-158">Sestavit průzkum s povolenými typy s možnou hodnotou null a bez hodnot null</span><span class="sxs-lookup"><span data-stu-id="83749-158">Build the survey with nullable and non-nullable types</span></span>

<span data-ttu-id="83749-159">První kód, který budete psát, vytvoří průzkum.</span><span class="sxs-lookup"><span data-stu-id="83749-159">The first code you'll write creates the survey.</span></span> <span data-ttu-id="83749-160">Budete psát třídy pro modelování otázky průzkumu a spuštění průzkumu.</span><span class="sxs-lookup"><span data-stu-id="83749-160">You'll write classes to model a survey question and a survey run.</span></span> <span data-ttu-id="83749-161">Váš průzkum má tři typy dotazů, které jsou odlišené podle formátu odpovědi: ano/ne odpovědi, počet odpovědí a text odpovědi.</span><span class="sxs-lookup"><span data-stu-id="83749-161">Your survey has three types of questions, distinguished by the format of the answer: Yes/No answers, number answers, and text answers.</span></span> <span data-ttu-id="83749-162">Vytvořte třídu `public` `SurveyQuestion`:</span><span class="sxs-lookup"><span data-stu-id="83749-162">Create a `public` `SurveyQuestion` class:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

<span data-ttu-id="83749-163">Kompilátor interpretuje každou deklaraci proměnné typu odkazu jako typ odkazu, **který nepovoluje hodnotu null** , pro kód v povoleném kontextu s povolenou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="83749-163">The compiler interprets every reference type variable declaration as a **non-nullable** reference type for code in a nullable enabled context.</span></span> <span data-ttu-id="83749-164">Můžete se podívat na vaše první upozornění přidáním vlastností textu otázky a typu otázky, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="83749-164">You can see your first warning by adding properties for the question text and the type of question, as shown in the following code:</span></span>

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

<span data-ttu-id="83749-165">Vzhledem k tomu, že jste neinicializoval `QuestionText`, vyvolá kompilátor upozornění, že není inicializována vlastnost, která není null.</span><span class="sxs-lookup"><span data-stu-id="83749-165">Because you haven't initialized `QuestionText`, the compiler issues a warning that a non-nullable property hasn't been initialized.</span></span> <span data-ttu-id="83749-166">Váš návrh vyžaduje, aby text otázky nebyl null, takže přidáte konstruktor, který ho inicializuje, a také hodnotu `QuestionType`.</span><span class="sxs-lookup"><span data-stu-id="83749-166">Your design requires the question text to be non-null, so you add a constructor to initialize it and the `QuestionType` value as well.</span></span> <span data-ttu-id="83749-167">Hotová definice třídy vypadá jako následující kód:</span><span class="sxs-lookup"><span data-stu-id="83749-167">The finished class definition looks like the following code:</span></span>

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

<span data-ttu-id="83749-168">Přidáním konstruktoru se odstraní upozornění.</span><span class="sxs-lookup"><span data-stu-id="83749-168">Adding the constructor removes the warning.</span></span> <span data-ttu-id="83749-169">Argument konstruktoru je také typ odkazu, který neumožňuje hodnotu null, takže kompilátor nevydá žádná upozornění.</span><span class="sxs-lookup"><span data-stu-id="83749-169">The constructor argument is also a non-nullable reference type, so the compiler doesn't issue any warnings.</span></span>

<span data-ttu-id="83749-170">Dále vytvořte třídu `public` s názvem `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="83749-170">Next, create a `public` class named `SurveyRun`.</span></span> <span data-ttu-id="83749-171">Tato třída obsahuje seznam objektů a metod `SurveyQuestion` pro přidání otázek do průzkumu, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="83749-171">This class contains a list of `SurveyQuestion` objects and methods to add questions to the survey, as shown in the following code:</span></span>

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

<span data-ttu-id="83749-172">Stejně jako předtím je nutné inicializovat objekt seznamu na hodnotu, která není null, nebo kompilátor vydá upozornění.</span><span class="sxs-lookup"><span data-stu-id="83749-172">As before, you must initialize the list object to a non-null value or the compiler issues a warning.</span></span> <span data-ttu-id="83749-173">V druhém přetížení `AddQuestion` nejsou žádné kontroly null, protože nejsou potřeba: deklaraci této proměnné nemůžete mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="83749-173">There are no null checks in the second overload of `AddQuestion` because they aren't needed: You've declared that variable to be non-nullable.</span></span> <span data-ttu-id="83749-174">Hodnota nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="83749-174">Its value can't be `null`.</span></span>

<span data-ttu-id="83749-175">V editoru přepněte na `Program.cs` a nahraďte obsah `Main` následujícími řádky kódu:</span><span class="sxs-lookup"><span data-stu-id="83749-175">Switch to `Program.cs` in your editor and replace the contents of `Main` with the following lines of code:</span></span>

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

<span data-ttu-id="83749-176">Vzhledem k tomu, že celý projekt je v povoleném kontextu s povolenou hodnotou null, zobrazí se upozornění při předání `null` do jakékoli metody, která očekává typ odkazu, který neumožňuje hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="83749-176">Because the entire project is in a nullable enabled context, you'll get warnings when you pass `null` to any method expecting a non-nullable reference type.</span></span> <span data-ttu-id="83749-177">Zkuste to přidáním následujícího řádku do `Main`:</span><span class="sxs-lookup"><span data-stu-id="83749-177">Try it by adding the following line to `Main`:</span></span>

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a><span data-ttu-id="83749-178">Vytváření respondentů a získávání odpovědí na průzkum</span><span class="sxs-lookup"><span data-stu-id="83749-178">Create respondents and get answers to the survey</span></span>

<span data-ttu-id="83749-179">Potom napíšete kód, který generuje odpovědi na průzkum.</span><span class="sxs-lookup"><span data-stu-id="83749-179">Next, write the code that generates answers to the survey.</span></span> <span data-ttu-id="83749-180">Tento proces zahrnuje několik malých úloh:</span><span class="sxs-lookup"><span data-stu-id="83749-180">This process involves several small tasks:</span></span>

1. <span data-ttu-id="83749-181">Sestavte metodu, která generuje objekty respondentů.</span><span class="sxs-lookup"><span data-stu-id="83749-181">Build a method that generates respondent objects.</span></span> <span data-ttu-id="83749-182">Tyto reprezentace označují, že lidé požádali o vyplnění průzkumu.</span><span class="sxs-lookup"><span data-stu-id="83749-182">These represent people asked to fill out the survey.</span></span>
1. <span data-ttu-id="83749-183">Logika sestavení pro simulaci dotazů na respondenty a shromažďování odpovědí nebo zaznamenání, že respondent neodpověděl.</span><span class="sxs-lookup"><span data-stu-id="83749-183">Build logic to simulate asking the questions to a respondent and collecting answers or noting that a respondent didn't answer.</span></span>
1. <span data-ttu-id="83749-184">Opakujte, dokud na průzkum neodpoví dostatek respondentů.</span><span class="sxs-lookup"><span data-stu-id="83749-184">Repeat until enough respondents have answered the survey.</span></span>

<span data-ttu-id="83749-185">Budete potřebovat třídu, která bude reprezentovat odpověď průzkumu, takže ji přidejte.</span><span class="sxs-lookup"><span data-stu-id="83749-185">You'll need a class to represent a survey response, so add that now.</span></span> <span data-ttu-id="83749-186">Povolí podporu s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="83749-186">Enable nullable support.</span></span> <span data-ttu-id="83749-187">Přidejte vlastnost `Id` a konstruktor, který ji inicializuje, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="83749-187">Add an `Id` property and a constructor that initializes it, as shown in the following code:</span></span>

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

<span data-ttu-id="83749-188">Dále přidejte metodu `static` pro vytvoření nových účastníků vygenerováním náhodného ID:</span><span class="sxs-lookup"><span data-stu-id="83749-188">Next, add a `static` method to create new participants by generating a random ID:</span></span>

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

<span data-ttu-id="83749-189">Hlavní zodpovědností této třídy je vygenerování odpovědí pro účastníka na otázky v průzkumu.</span><span class="sxs-lookup"><span data-stu-id="83749-189">The main responsibility of this class is to generate the responses for a participant to the questions in the survey.</span></span> <span data-ttu-id="83749-190">Tato zodpovědnost zahrnuje několik kroků:</span><span class="sxs-lookup"><span data-stu-id="83749-190">This responsibility has a few steps:</span></span>

1. <span data-ttu-id="83749-191">Zeptejte se na účast v průzkumu.</span><span class="sxs-lookup"><span data-stu-id="83749-191">Ask for participation in the survey.</span></span> <span data-ttu-id="83749-192">Pokud uživatel nesouhlasí, vrátí odpověď chybějící (nebo null).</span><span class="sxs-lookup"><span data-stu-id="83749-192">If the person doesn't consent, return a missing (or null) response.</span></span>
1. <span data-ttu-id="83749-193">Položte každou otázku a zaznamenejte odpověď.</span><span class="sxs-lookup"><span data-stu-id="83749-193">Ask each question and record the answer.</span></span> <span data-ttu-id="83749-194">Každá odpověď může také chybět (nebo mít hodnotu null).</span><span class="sxs-lookup"><span data-stu-id="83749-194">Each answer may also be missing (or null).</span></span>

<span data-ttu-id="83749-195">Do třídy `SurveyResponse` přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="83749-195">Add the following code to your `SurveyResponse` class:</span></span>

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

<span data-ttu-id="83749-196">Úložiště pro odpovědi na průzkum je `Dictionary<int, string>?`, což znamená, že může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="83749-196">The storage for the survey answers is a `Dictionary<int, string>?`, indicating that it may be null.</span></span> <span data-ttu-id="83749-197">Používáte novou funkci jazyka k deklaraci záměru návrhu, jak pro kompilátor, tak pro každého, kdo váš kód čte, později.</span><span class="sxs-lookup"><span data-stu-id="83749-197">You're using the new language feature to declare your design intent, both to the compiler and to anyone reading your code later.</span></span> <span data-ttu-id="83749-198">Pokud někdy zrušíte odkaz `surveyResponses` bez prvotní kontroly hodnoty null, zobrazí se upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="83749-198">If you ever dereference `surveyResponses` without checking for the null value first, you'll get a compiler warning.</span></span> <span data-ttu-id="83749-199">Nezobrazuje se upozornění v metodě @no__t 0, protože kompilátor může určit, že proměnná `surveyResponses` byla nastavena na hodnotu jinou než null.</span><span class="sxs-lookup"><span data-stu-id="83749-199">You don't get a warning in the `AnswerSurvey` method because the compiler can determine the `surveyResponses` variable was set to a non-null value above.</span></span>

<span data-ttu-id="83749-200">Použití `null` pro chybějící odpovědi zvýrazní klíčové body pro práci s typy odkazů s možnou hodnotou null: vaším cílem není odebrat všechny hodnoty `null` z programu.</span><span class="sxs-lookup"><span data-stu-id="83749-200">Using `null` for missing answers highlights a key point for working with nullable reference types: your goal isn't to remove all `null` values from your program.</span></span> <span data-ttu-id="83749-201">Místo toho je vaším cílem zajistit, aby kód, který píšete, vyjadřoval záměr vašeho návrhu.</span><span class="sxs-lookup"><span data-stu-id="83749-201">Rather, your goal is to ensure that the code you write expresses the intent of your design.</span></span> <span data-ttu-id="83749-202">Chybějící hodnoty jsou nezbytným konceptem, který by bylo možné vyjádřit do kódu.</span><span class="sxs-lookup"><span data-stu-id="83749-202">Missing values are a necessary concept to express in your code.</span></span> <span data-ttu-id="83749-203">Hodnota `null` představuje jasný způsob, jak vyjádřit chybějící hodnoty.</span><span class="sxs-lookup"><span data-stu-id="83749-203">The `null` value is a clear way to express those missing values.</span></span> <span data-ttu-id="83749-204">Pokus o odebrání všech hodnot `null` vede pouze k definování jiného způsobu, jak tyto chybějící hodnoty vyjádřit bez `null`.</span><span class="sxs-lookup"><span data-stu-id="83749-204">Trying to remove all `null` values only leads to defining some other way to express those missing values without `null`.</span></span>

<span data-ttu-id="83749-205">Dále je nutné zapsat metodu `PerformSurvey` ve třídě `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="83749-205">Next, you need to write the `PerformSurvey` method in the `SurveyRun` class.</span></span> <span data-ttu-id="83749-206">Do třídy `SurveyRun` přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="83749-206">Add the following code in the `SurveyRun` class:</span></span>

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

<span data-ttu-id="83749-207">Tady můžete znovu vybrat @no__t s možnou hodnotou null-0, což znamená, že odpověď může být null.</span><span class="sxs-lookup"><span data-stu-id="83749-207">Here again, your choice of a nullable `List<SurveyResponse>?` indicates the response may be null.</span></span> <span data-ttu-id="83749-208">To indikuje, že průzkum ještě není předaný žádným respondentům.</span><span class="sxs-lookup"><span data-stu-id="83749-208">That indicates the survey hasn't been given to any respondents yet.</span></span> <span data-ttu-id="83749-209">Všimněte si, že se přidávají respondenti, dokud nepřijdete o dostatek.</span><span class="sxs-lookup"><span data-stu-id="83749-209">Notice that respondents are added until enough have consented.</span></span>

<span data-ttu-id="83749-210">Posledním krokem ke spuštění průzkumu je přidání volání pro provedení průzkumu na konci metody `Main`:</span><span class="sxs-lookup"><span data-stu-id="83749-210">The last step to run the survey is to add a call to perform the survey at the end of the `Main` method:</span></span>

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a><span data-ttu-id="83749-211">Kontrola odpovědí na průzkum</span><span class="sxs-lookup"><span data-stu-id="83749-211">Examine survey responses</span></span>

<span data-ttu-id="83749-212">Posledním krokem je zobrazení výsledků průzkumu.</span><span class="sxs-lookup"><span data-stu-id="83749-212">The last step is to display survey results.</span></span> <span data-ttu-id="83749-213">Přidáte kód do mnoha tříd, které jste napsali.</span><span class="sxs-lookup"><span data-stu-id="83749-213">You'll add code to many of the classes you've written.</span></span> <span data-ttu-id="83749-214">Tento kód ukazuje hodnotu rozlišující typy s možnou hodnotou null a odkazy, které neumožňují hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="83749-214">This code demonstrates the value of distinguishing nullable and non-nullable reference types.</span></span> <span data-ttu-id="83749-215">Začněte přidáním následujících dvou členů výrazu-těle do třídy `SurveyResponse`:</span><span class="sxs-lookup"><span data-stu-id="83749-215">Start by adding the following two expression-bodied members to the `SurveyResponse` class:</span></span>

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

<span data-ttu-id="83749-216">Vzhledem k tomu, že `surveyResponses` je typ odkazu s možnou hodnotou null, je nutné před zrušením odkazování zkontrolovat.</span><span class="sxs-lookup"><span data-stu-id="83749-216">Because `surveyResponses` is a nullable reference type null checks are necessary before de-referencing it.</span></span> <span data-ttu-id="83749-217">Metoda `Answer` vrací řetězec, který nemůže mít hodnotu null, takže musíme pokrýt případ chybějící odpovědi pomocí operátoru slučování null.</span><span class="sxs-lookup"><span data-stu-id="83749-217">The `Answer` method returns a non-nullable string, so we have to cover the case of a missing answer by using the null-coalescing operator.</span></span>

<span data-ttu-id="83749-218">Dále přidejte tyto tři členy Expression-těle do třídy `SurveyRun`:</span><span class="sxs-lookup"><span data-stu-id="83749-218">Next, add these three expression-bodied members to the `SurveyRun` class:</span></span>

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

<span data-ttu-id="83749-219">Člen `AllParticipants` musí vzít v úvahu, že proměnná `respondents` může mít hodnotu null, ale návratová hodnota nemůže být null.</span><span class="sxs-lookup"><span data-stu-id="83749-219">The `AllParticipants` member must take into account that the `respondents` variable might be null, but the return value can't be null.</span></span> <span data-ttu-id="83749-220">Pokud tento výraz změníte odebráním `??` a prázdné sekvence, která následuje, kompilátor vás upozorní, že metoda může vracet hodnotu `null` a její návratový podpis vrátí typ, který nelze připouštějící hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="83749-220">If you change that expression by removing the `??` and the empty sequence that follows, the compiler warns you the method might return `null` and its return signature returns a non-nullable type.</span></span>

<span data-ttu-id="83749-221">Nakonec přidejte následující smyčku na konec metody `Main`:</span><span class="sxs-lookup"><span data-stu-id="83749-221">Finally, add the following loop at the bottom of the `Main` method:</span></span>

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

<span data-ttu-id="83749-222">V tomto kódu nepotřebujete žádné kontroly `null`, protože jste navrhli základní rozhraní tak, aby všechny vracely typy odkazů, které neumožňují hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="83749-222">You don't need any `null` checks in this code because you've designed the underlying interfaces so that they all return non-nullable reference types.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="83749-223">Získat kód</span><span class="sxs-lookup"><span data-stu-id="83749-223">Get the code</span></span>

<span data-ttu-id="83749-224">Kód pro dokončený kurz můžete získat z našeho úložiště [ukázek](https://github.com/dotnet/samples) ve složce [CSharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) .</span><span class="sxs-lookup"><span data-stu-id="83749-224">You can get the code for the finished tutorial from our [samples](https://github.com/dotnet/samples) repository in the [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folder.</span></span>

<span data-ttu-id="83749-225">Experimenty změnou deklarace typů mezi typy s možnou hodnotou null a odkazem, které neumožňují hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="83749-225">Experiment by changing the type declarations between nullable and non-nullable reference types.</span></span> <span data-ttu-id="83749-226">Podívejte se, jak to generuje různá upozornění, abyste se ujistili, že nechtěně neodkazuje na `null`.</span><span class="sxs-lookup"><span data-stu-id="83749-226">See how that generates different warnings to ensure you don't accidentally dereference a `null`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="83749-227">Další kroky</span><span class="sxs-lookup"><span data-stu-id="83749-227">Next steps</span></span>

<span data-ttu-id="83749-228">Další informace migracem existující aplikace na použití typů odkazů s možnou hodnotou null:</span><span class="sxs-lookup"><span data-stu-id="83749-228">Learn more by migrating an existing application to use nullable reference types:</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="83749-229">Upgrade aplikace na použití typů odkazů s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="83749-229">Upgrade an application to use nullable reference types</span></span>](upgrade-to-nullable-references.md)

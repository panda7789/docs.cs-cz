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
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="88e89-104">Kurz: Vyjádřete svůj záměr návrhu jasněji s typy odkazů s možnou a nulovou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="88e89-104">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>

<span data-ttu-id="88e89-105">C# 8.0 zavádí [typy odkazů s možnou hodnotou null](../nullable-references.md), které doplňují typy odkazů stejným způsobem, jakým jsou typy hodnot typu hodnot s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="88e89-105">C# 8.0 introduces [nullable reference types](../nullable-references.md), which complement reference types the same way nullable value types complement value types.</span></span> <span data-ttu-id="88e89-106">Deklarujete proměnnou jako **typ odkazu s možnou hodnotou null** připojením typu a. `?`</span><span class="sxs-lookup"><span data-stu-id="88e89-106">You declare a variable to be a **nullable reference type** by appending a `?` to the type.</span></span> <span data-ttu-id="88e89-107">Například `string?` představuje hodnotu `string`nullable .</span><span class="sxs-lookup"><span data-stu-id="88e89-107">For example, `string?` represents a nullable `string`.</span></span> <span data-ttu-id="88e89-108">Tyto nové typy můžete použít k jasněji vyjádřit záměr návrhu: některé proměnné *musí mít vždy hodnotu*, jiné *mohou chybět hodnotu*.</span><span class="sxs-lookup"><span data-stu-id="88e89-108">You can use these new types to more clearly express your design intent: some variables *must always have a value*, others *may be missing a value*.</span></span>

<span data-ttu-id="88e89-109">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="88e89-109">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="88e89-110">Začleňte do svých návrhů typy odkazů s možnou hodnotou null a nenulovatelné</span><span class="sxs-lookup"><span data-stu-id="88e89-110">Incorporate nullable and non-nullable reference types into your designs</span></span>
> - <span data-ttu-id="88e89-111">Povolte kontroly typu odkazu s možnou hodnotou null v celém kódu.</span><span class="sxs-lookup"><span data-stu-id="88e89-111">Enable nullable reference type checks throughout your code.</span></span>
> - <span data-ttu-id="88e89-112">Napište kód, kde kompilátor vynucuje tato rozhodnutí o návrhu.</span><span class="sxs-lookup"><span data-stu-id="88e89-112">Write code where the compiler enforces those design decisions.</span></span>
> - <span data-ttu-id="88e89-113">Použití referenční funkce s možnou hodnotou null ve vlastních návrzích</span><span class="sxs-lookup"><span data-stu-id="88e89-113">Use the nullable reference feature in your own designs</span></span>

## <a name="prerequisites"></a><span data-ttu-id="88e89-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="88e89-114">Prerequisites</span></span>

<span data-ttu-id="88e89-115">Budete muset nastavit počítač pro spuštění .NET Core, včetně kompilátoru C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="88e89-115">You'll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="88e89-116">Kompilátor Jazyka C# 8.0 je k dispozici v [sadě Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)nebo [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="88e89-116">The C# 8.0 compiler is available with [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="88e89-117">Tento kurz předpokládá, že jste obeznámeni s C# a .NET, včetně Visual Studio nebo .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="88e89-117">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="incorporate-nullable-reference-types-into-your-designs"></a><span data-ttu-id="88e89-118">Začleňte do svých návrhů typy odkazů s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="88e89-118">Incorporate nullable reference types into your designs</span></span>

<span data-ttu-id="88e89-119">V tomto kurzu vytvoříte knihovnu, která modeluje spuštění průzkumu.</span><span class="sxs-lookup"><span data-stu-id="88e89-119">In this tutorial, you'll build a library that models running a survey.</span></span> <span data-ttu-id="88e89-120">Kód používá typy odkazů s možnou hodnotou null a typy odkazů s nulovou hodnotou, které představují koncepty reálného světa.</span><span class="sxs-lookup"><span data-stu-id="88e89-120">The code uses both nullable reference types and non-nullable reference types to represent the real-world concepts.</span></span> <span data-ttu-id="88e89-121">Otázky průzkumu nemůže být nikdy null.</span><span class="sxs-lookup"><span data-stu-id="88e89-121">The survey questions can never be null.</span></span> <span data-ttu-id="88e89-122">Respondent by raději neodpověděl na otázku.</span><span class="sxs-lookup"><span data-stu-id="88e89-122">A respondent might prefer not to answer a question.</span></span> <span data-ttu-id="88e89-123">Odpovědi mohou být `null` v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="88e89-123">The responses might be `null` in this case.</span></span>

<span data-ttu-id="88e89-124">Kód, který budete psát pro tuto ukázku vyjadřuje tento záměr a kompilátor vynucuje tento záměr.</span><span class="sxs-lookup"><span data-stu-id="88e89-124">The code you'll write for this sample expresses that intent, and the compiler enforces that intent.</span></span>

## <a name="create-the-application-and-enable-nullable-reference-types"></a><span data-ttu-id="88e89-125">Vytvoření aplikace a povolení typů odkazů s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="88e89-125">Create the application and enable nullable reference types</span></span>

<span data-ttu-id="88e89-126">Vytvořte novou konzolovou aplikaci v sadě `dotnet new console`Visual Studio nebo z příkazového řádku pomocí aplikace .</span><span class="sxs-lookup"><span data-stu-id="88e89-126">Create a new console application either in Visual Studio or from the command line using `dotnet new console`.</span></span> <span data-ttu-id="88e89-127">Pojmenujte `NullableIntroduction`aplikaci .</span><span class="sxs-lookup"><span data-stu-id="88e89-127">Name the application `NullableIntroduction`.</span></span> <span data-ttu-id="88e89-128">Po vytvoření aplikace budete muset určit, že celý projekt se zkompiluje v povoleném **kontextu poznámky s možnou hodnotou null**.</span><span class="sxs-lookup"><span data-stu-id="88e89-128">Once you've created the application, you'll need to specify that the entire project compiles in an enabled **nullable annotation context**.</span></span> <span data-ttu-id="88e89-129">Otevřete soubor *.csproj* `Nullable` a přidejte prvek do `PropertyGroup` prvku.</span><span class="sxs-lookup"><span data-stu-id="88e89-129">Open the *.csproj* file and add a `Nullable` element to the `PropertyGroup` element.</span></span> <span data-ttu-id="88e89-130">Nastavte její hodnotu na `enable`.</span><span class="sxs-lookup"><span data-stu-id="88e89-130">Set its value to `enable`.</span></span> <span data-ttu-id="88e89-131">Musíte se přihlásit do funkce **typu odkazu s možnou hodnotou null,** a to i v projektech jazyka C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="88e89-131">You must opt into the **nullable reference types** feature, even in C# 8.0 projects.</span></span> <span data-ttu-id="88e89-132">Je to proto, že jakmile je funkce zapnuta, existující deklarace referenčních proměnných se stanou **typy odkazů s možnou hodnotou null**.</span><span class="sxs-lookup"><span data-stu-id="88e89-132">That's because once the feature is turned on, existing reference variable declarations become **non-nullable reference types**.</span></span> <span data-ttu-id="88e89-133">I když toto rozhodnutí pomůže najít problémy, kde existující kód nemusí mít správné kontroly null, nemusí přesně odrážet původní záměr návrhu:</span><span class="sxs-lookup"><span data-stu-id="88e89-133">While that decision will help find issues where existing code may not have proper null-checks, it may not accurately reflect your original design intent:</span></span>

```xml
<Nullable>enable</Nullable>
```

### <a name="design-the-types-for-the-application"></a><span data-ttu-id="88e89-134">Navrhněte typy pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="88e89-134">Design the types for the application</span></span>

<span data-ttu-id="88e89-135">Tato aplikace průzkumu vyžaduje vytvoření několika tříd:</span><span class="sxs-lookup"><span data-stu-id="88e89-135">This survey application requires creating a number of classes:</span></span>

- <span data-ttu-id="88e89-136">Třída, která modeluje seznam otázek.</span><span class="sxs-lookup"><span data-stu-id="88e89-136">A class that models the list of questions.</span></span>
- <span data-ttu-id="88e89-137">Třída, která modeluje seznam osob kontaktovaných pro průzkum.</span><span class="sxs-lookup"><span data-stu-id="88e89-137">A class that models a list of people contacted for the survey.</span></span>
- <span data-ttu-id="88e89-138">Třída, která modeluje odpovědi od osoby, která provedla průzkum.</span><span class="sxs-lookup"><span data-stu-id="88e89-138">A class that models the answers from a person that took the survey.</span></span>

<span data-ttu-id="88e89-139">Tyto typy budou používat nullable a nenulelné typy odkazů vyjádřit, které členy jsou požadovány a které členy jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="88e89-139">These types will make use of both nullable and non-nullable reference types to express which members are required and which members are optional.</span></span> <span data-ttu-id="88e89-140">Typy odkazů s možnou hodnotou Null jasně sdělují záměr návrhu:</span><span class="sxs-lookup"><span data-stu-id="88e89-140">Nullable reference types communicate that design intent clearly:</span></span>

- <span data-ttu-id="88e89-141">Otázky, které jsou součástí průzkumu, nemohou být nikdy nulové: Nemá smysl klást prázdnou otázku.</span><span class="sxs-lookup"><span data-stu-id="88e89-141">The questions that are part of the survey can never be null: It makes no sense to ask an empty question.</span></span>
- <span data-ttu-id="88e89-142">Respondenti nemohou být nikdy null.</span><span class="sxs-lookup"><span data-stu-id="88e89-142">The respondents can never be null.</span></span> <span data-ttu-id="88e89-143">Budete chtít sledovat lidi, které jste kontaktovali, dokonce i respondenty, kteří se odmítli zúčastnit.</span><span class="sxs-lookup"><span data-stu-id="88e89-143">You'll want to track people you contacted, even respondents that declined to participate.</span></span>
- <span data-ttu-id="88e89-144">Odpověď na otázku může být null.</span><span class="sxs-lookup"><span data-stu-id="88e89-144">Any response to a question may be null.</span></span> <span data-ttu-id="88e89-145">Respondenti mohou odmítnout odpovědět na některé nebo všechny otázky.</span><span class="sxs-lookup"><span data-stu-id="88e89-145">Respondents can decline to answer some or all questions.</span></span>

<span data-ttu-id="88e89-146">Pokud jste naprogramovali v c#, můžete být tak zvyklí na referenční typy, které umožňují `null` hodnoty, které jste možná vynechali další příležitosti k deklarování instancí s možnou hodnotou null:</span><span class="sxs-lookup"><span data-stu-id="88e89-146">If you've programmed in C#, you may be so accustomed to reference types that allow `null` values that you may have missed other opportunities to declare non-nullable instances:</span></span>

- <span data-ttu-id="88e89-147">Kolekce otázek by měla být nenulovatelná.</span><span class="sxs-lookup"><span data-stu-id="88e89-147">The collection of questions should be non-nullable.</span></span>
- <span data-ttu-id="88e89-148">Kolekce respondentů by měla být nenulovatelná.</span><span class="sxs-lookup"><span data-stu-id="88e89-148">The collection of respondents should be non-nullable.</span></span>

<span data-ttu-id="88e89-149">Při psaní kódu uvidíte, že typ odkazu s možnou nemožnou hodnotou null jako <xref:System.NullReferenceException>výchozí pro odkazy zabraňuje běžným chybám, které by mohly vést k s.</span><span class="sxs-lookup"><span data-stu-id="88e89-149">As you write the code, you'll see that a non-nullable reference type as the default for references avoids common mistakes that could lead to <xref:System.NullReferenceException>s.</span></span> <span data-ttu-id="88e89-150">Jedna lekce z tohoto kurzu je, že jste se rozhodli `null`o tom, které proměnné by mohly nebo nemohly být .</span><span class="sxs-lookup"><span data-stu-id="88e89-150">One lesson from this tutorial is that you made decisions about which variables could or could not be `null`.</span></span> <span data-ttu-id="88e89-151">Jazyk neposkytl syntaxi pro vyjádření těchto rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="88e89-151">The language didn't provide syntax to express those decisions.</span></span> <span data-ttu-id="88e89-152">Teď už ano.</span><span class="sxs-lookup"><span data-stu-id="88e89-152">Now it does.</span></span>

<span data-ttu-id="88e89-153">Aplikace, kterou vytvoříte, provede následující kroky:</span><span class="sxs-lookup"><span data-stu-id="88e89-153">The app you'll build does the following steps:</span></span>

1. <span data-ttu-id="88e89-154">Vytvoří průzkum a přidá k němu otázky.</span><span class="sxs-lookup"><span data-stu-id="88e89-154">Creates a survey and adds questions to it.</span></span>
1. <span data-ttu-id="88e89-155">Vytvoří pseudonáhodnou sadu respondentů pro průzkum.</span><span class="sxs-lookup"><span data-stu-id="88e89-155">Creates a pseudo-random set of respondents for the survey.</span></span>
1. <span data-ttu-id="88e89-156">Kontaktuje respondenty, dokud velikost dokončeného průzkumu nedosáhne čísla cíle.</span><span class="sxs-lookup"><span data-stu-id="88e89-156">Contacts respondents until the completed survey size reaches the goal number.</span></span>
1. <span data-ttu-id="88e89-157">Zapíše důležité statistiky o odpovědích na průzkum.</span><span class="sxs-lookup"><span data-stu-id="88e89-157">Writes out important statistics on the survey responses.</span></span>

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a><span data-ttu-id="88e89-158">Sestavení průzkumu s typy s možnou hodnotou null a nenulovatelné</span><span class="sxs-lookup"><span data-stu-id="88e89-158">Build the survey with nullable and non-nullable types</span></span>

<span data-ttu-id="88e89-159">První kód, který napíšete, vytvoří průzkum.</span><span class="sxs-lookup"><span data-stu-id="88e89-159">The first code you'll write creates the survey.</span></span> <span data-ttu-id="88e89-160">Budete psát třídy pro modelování otázky průzkumu a spuštění průzkumu.</span><span class="sxs-lookup"><span data-stu-id="88e89-160">You'll write classes to model a survey question and a survey run.</span></span> <span data-ttu-id="88e89-161">Průzkum má tři typy otázek, které se vyznačují formátem odpovědi: Ano/Ne odpovědi, počet odpovědí a textové odpovědi.</span><span class="sxs-lookup"><span data-stu-id="88e89-161">Your survey has three types of questions, distinguished by the format of the answer: Yes/No answers, number answers, and text answers.</span></span> <span data-ttu-id="88e89-162">Vytvořte `public SurveyQuestion` třídu:</span><span class="sxs-lookup"><span data-stu-id="88e89-162">Create a `public SurveyQuestion` class:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

<span data-ttu-id="88e89-163">Kompilátor interpretuje každou deklaraci proměnné typu odkazu jako typ odkazu **s hodnotou neshodnou hodnotu null** pro kód v povoleném kontextu poznámky s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="88e89-163">The compiler interprets every reference type variable declaration as a **non-nullable** reference type for code in an enabled nullable annotation context.</span></span> <span data-ttu-id="88e89-164">První upozornění zobrazíte přidáním vlastností textu otázky a typu otázky, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="88e89-164">You can see your first warning by adding properties for the question text and the type of question, as shown in the following code:</span></span>

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

<span data-ttu-id="88e89-165">Protože jste se neinicializovali `QuestionText`, kompilátor vydá upozornění, že vlastnost, kterou nelze utvarovat jako nenulovatelná, nebyla inicializována.</span><span class="sxs-lookup"><span data-stu-id="88e89-165">Because you haven't initialized `QuestionText`, the compiler issues a warning that a non-nullable property hasn't been initialized.</span></span> <span data-ttu-id="88e89-166">Váš návrh vyžaduje, aby text otázky byl nenulový, takže přidáte konstruktor pro jeho inicializaci a také hodnotu. `QuestionType`</span><span class="sxs-lookup"><span data-stu-id="88e89-166">Your design requires the question text to be non-null, so you add a constructor to initialize it and the `QuestionType` value as well.</span></span> <span data-ttu-id="88e89-167">Definice dokončené třídy vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="88e89-167">The finished class definition looks like the following code:</span></span>

[!code-csharp[DefineQuestion](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

<span data-ttu-id="88e89-168">Přidání konstruktoru odebere upozornění.</span><span class="sxs-lookup"><span data-stu-id="88e89-168">Adding the constructor removes the warning.</span></span> <span data-ttu-id="88e89-169">Argument konstruktoru je také typ odkazu s možnou hodnotou null, takže kompilátor nevydává žádná upozornění.</span><span class="sxs-lookup"><span data-stu-id="88e89-169">The constructor argument is also a non-nullable reference type, so the compiler doesn't issue any warnings.</span></span>

<span data-ttu-id="88e89-170">Dále vytvořte `public` třídu s názvem `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="88e89-170">Next, create a `public` class named `SurveyRun`.</span></span> <span data-ttu-id="88e89-171">Tato třída obsahuje `SurveyQuestion` seznam objektů a metod pro přidání otázek do průzkumu, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="88e89-171">This class contains a list of `SurveyQuestion` objects and methods to add questions to the survey, as shown in the following code:</span></span>

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

<span data-ttu-id="88e89-172">Stejně jako dříve je nutné inicializovat objekt seznamu na hodnotu bez null nebo kompilátor vydá upozornění.</span><span class="sxs-lookup"><span data-stu-id="88e89-172">As before, you must initialize the list object to a non-null value or the compiler issues a warning.</span></span> <span data-ttu-id="88e89-173">Neexistují žádné kontroly null v `AddQuestion` druhé přetížení, protože nejsou potřeba: Jste deklarovali, že proměnná je nenulovatelný.</span><span class="sxs-lookup"><span data-stu-id="88e89-173">There are no null checks in the second overload of `AddQuestion` because they aren't needed: You've declared that variable to be non-nullable.</span></span> <span data-ttu-id="88e89-174">Jeho hodnota nemůže `null`být .</span><span class="sxs-lookup"><span data-stu-id="88e89-174">Its value can't be `null`.</span></span>

<span data-ttu-id="88e89-175">Přepněte do *Program.cs* v editoru `Main` a nahraďte obsah následujících řádků kódu:</span><span class="sxs-lookup"><span data-stu-id="88e89-175">Switch to *Program.cs* in your editor and replace the contents of `Main` with the following lines of code:</span></span>

[!code-csharp[AddQuestions](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

<span data-ttu-id="88e89-176">Vzhledem k tomu, že celý projekt je v povoleném kontextu `null` poznámky s možnou hodnotou null, zobrazí se upozornění při předání libovolné metody, která očekává typ odkazu s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="88e89-176">Because the entire project is in an enabled nullable annotation context, you'll get warnings when you pass `null` to any method expecting a non-nullable reference type.</span></span> <span data-ttu-id="88e89-177">Zkuste to přidáním následujícího řádku do `Main`:</span><span class="sxs-lookup"><span data-stu-id="88e89-177">Try it by adding the following line to `Main`:</span></span>

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a><span data-ttu-id="88e89-178">Vytváření respondentů a získání odpovědí na průzkum</span><span class="sxs-lookup"><span data-stu-id="88e89-178">Create respondents and get answers to the survey</span></span>

<span data-ttu-id="88e89-179">Dále napište kód, který generuje odpovědi na průzkum.</span><span class="sxs-lookup"><span data-stu-id="88e89-179">Next, write the code that generates answers to the survey.</span></span> <span data-ttu-id="88e89-180">Tento proces zahrnuje několik malých úkolů:</span><span class="sxs-lookup"><span data-stu-id="88e89-180">This process involves several small tasks:</span></span>

1. <span data-ttu-id="88e89-181">Vytvořte metodu, která generuje objekty respondentu.</span><span class="sxs-lookup"><span data-stu-id="88e89-181">Build a method that generates respondent objects.</span></span> <span data-ttu-id="88e89-182">Tito představují lidi, kteří byli požádáni o vyplnění průzkumu.</span><span class="sxs-lookup"><span data-stu-id="88e89-182">These represent people asked to fill out the survey.</span></span>
1. <span data-ttu-id="88e89-183">Vytvořte logiku, která simuluje kladení otázek respondentovi a shromažďování odpovědí nebo konstatování, že respondent neodpověděl.</span><span class="sxs-lookup"><span data-stu-id="88e89-183">Build logic to simulate asking the questions to a respondent and collecting answers or noting that a respondent didn't answer.</span></span>
1. <span data-ttu-id="88e89-184">Opakujte, dokud na průzkum neodpoví dostatek respondentů.</span><span class="sxs-lookup"><span data-stu-id="88e89-184">Repeat until enough respondents have answered the survey.</span></span>

<span data-ttu-id="88e89-185">Budete potřebovat třídu, která bude reprezentovat odpověď na průzkum, takže ji přidejte nyní.</span><span class="sxs-lookup"><span data-stu-id="88e89-185">You'll need a class to represent a survey response, so add that now.</span></span> <span data-ttu-id="88e89-186">Povolte podporu, jejíž hodnotu lze uznat jako null.</span><span class="sxs-lookup"><span data-stu-id="88e89-186">Enable nullable support.</span></span> <span data-ttu-id="88e89-187">Přidejte `Id` vlastnost a konstruktor, který ji inicializuje, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="88e89-187">Add an `Id` property and a constructor that initializes it, as shown in the following code:</span></span>

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

<span data-ttu-id="88e89-188">Dále přidejte `static` metodu pro vytvoření nových účastníků generováním náhodného ID:</span><span class="sxs-lookup"><span data-stu-id="88e89-188">Next, add a `static` method to create new participants by generating a random ID:</span></span>

[!code-csharp[GenerateRespondents](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

<span data-ttu-id="88e89-189">Hlavní odpovědností této třídy je generovat odpovědi pro účastníka na otázky v průzkumu.</span><span class="sxs-lookup"><span data-stu-id="88e89-189">The main responsibility of this class is to generate the responses for a participant to the questions in the survey.</span></span> <span data-ttu-id="88e89-190">Tato odpovědnost má několik kroků:</span><span class="sxs-lookup"><span data-stu-id="88e89-190">This responsibility has a few steps:</span></span>

1. <span data-ttu-id="88e89-191">Požádejte o účast v průzkumu.</span><span class="sxs-lookup"><span data-stu-id="88e89-191">Ask for participation in the survey.</span></span> <span data-ttu-id="88e89-192">Pokud osoba nesouhlasí, vrátí chybějící (nebo nulovou) odpověď.</span><span class="sxs-lookup"><span data-stu-id="88e89-192">If the person doesn't consent, return a missing (or null) response.</span></span>
1. <span data-ttu-id="88e89-193">Zeptejte se na každou otázku a zaznamenejte odpověď.</span><span class="sxs-lookup"><span data-stu-id="88e89-193">Ask each question and record the answer.</span></span> <span data-ttu-id="88e89-194">Každá odpověď může také chybět (nebo null).</span><span class="sxs-lookup"><span data-stu-id="88e89-194">Each answer may also be missing (or null).</span></span>

<span data-ttu-id="88e89-195">Přidejte do třídy `SurveyResponse` následující kód:</span><span class="sxs-lookup"><span data-stu-id="88e89-195">Add the following code to your `SurveyResponse` class:</span></span>

[!code-csharp[AnswerSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

<span data-ttu-id="88e89-196">Úložiště pro odpovědi průzkumu `Dictionary<int, string>?`je , označující, že může být null.</span><span class="sxs-lookup"><span data-stu-id="88e89-196">The storage for the survey answers is a `Dictionary<int, string>?`, indicating that it may be null.</span></span> <span data-ttu-id="88e89-197">Používáte novou funkci jazyka k deklarování záměru návrhu, a to jak kompilátoru, tak komukoli, kdo váš kód čte později.</span><span class="sxs-lookup"><span data-stu-id="88e89-197">You're using the new language feature to declare your design intent, both to the compiler and to anyone reading your code later.</span></span> <span data-ttu-id="88e89-198">Pokud jste někdy `surveyResponses` dereference bez `null` kontroly hodnoty jako první, dostanete upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="88e89-198">If you ever dereference `surveyResponses` without checking for the `null` value first, you'll get a compiler warning.</span></span> <span data-ttu-id="88e89-199">Nedostanete upozornění v metodě, `AnswerSurvey` protože kompilátor `surveyResponses` může určit, že proměnná byla nastavena na hodnotu nenulovou výše.</span><span class="sxs-lookup"><span data-stu-id="88e89-199">You don't get a warning in the `AnswerSurvey` method because the compiler can determine the `surveyResponses` variable was set to a non-null value above.</span></span>

<span data-ttu-id="88e89-200">Použití `null` pro chybějící odpovědi zvýrazní klíčový bod pro práci s typy odkazů `null` s možnou hodnotou null: vaším cílem není odebrat všechny hodnoty z programu.</span><span class="sxs-lookup"><span data-stu-id="88e89-200">Using `null` for missing answers highlights a key point for working with nullable reference types: your goal isn't to remove all `null` values from your program.</span></span> <span data-ttu-id="88e89-201">Spíše vaším cílem je zajistit, aby kód, který píšete vyjadřuje záměr vašeho návrhu.</span><span class="sxs-lookup"><span data-stu-id="88e89-201">Rather, your goal is to ensure that the code you write expresses the intent of your design.</span></span> <span data-ttu-id="88e89-202">Chybějící hodnoty jsou nezbytné koncept vyjádřit ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="88e89-202">Missing values are a necessary concept to express in your code.</span></span> <span data-ttu-id="88e89-203">Hodnota `null` je jasný způsob, jak vyjádřit tyto chybějící hodnoty.</span><span class="sxs-lookup"><span data-stu-id="88e89-203">The `null` value is a clear way to express those missing values.</span></span> <span data-ttu-id="88e89-204">Pokus o `null` odebrání všech hodnot vede pouze k definování jiného způsobu vyjádření těchto chybějících hodnot bez `null`.</span><span class="sxs-lookup"><span data-stu-id="88e89-204">Trying to remove all `null` values only leads to defining some other way to express those missing values without `null`.</span></span>

<span data-ttu-id="88e89-205">Dále musíte napsat metodu `PerformSurvey` ve `SurveyRun` třídě.</span><span class="sxs-lookup"><span data-stu-id="88e89-205">Next, you need to write the `PerformSurvey` method in the `SurveyRun` class.</span></span> <span data-ttu-id="88e89-206">Do `SurveyRun` třídy přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="88e89-206">Add the following code in the `SurveyRun` class:</span></span>

[!code-csharp[PerformSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

<span data-ttu-id="88e89-207">Zde opět vaše volba nullable `List<SurveyResponse>?` označuje odpověď může být null.</span><span class="sxs-lookup"><span data-stu-id="88e89-207">Here again, your choice of a nullable `List<SurveyResponse>?` indicates the response may be null.</span></span> <span data-ttu-id="88e89-208">To znamená, že průzkum ještě nebyl poskytnut žádnému respondentovi.</span><span class="sxs-lookup"><span data-stu-id="88e89-208">That indicates the survey hasn't been given to any respondents yet.</span></span> <span data-ttu-id="88e89-209">Všimněte si, že respondenti jsou přidány, dokud dostatek souhlasu.</span><span class="sxs-lookup"><span data-stu-id="88e89-209">Notice that respondents are added until enough have consented.</span></span>

<span data-ttu-id="88e89-210">Posledním krokem ke spuštění průzkumu je přidání volání k provedení `Main` průzkumu na konci metody:</span><span class="sxs-lookup"><span data-stu-id="88e89-210">The last step to run the survey is to add a call to perform the survey at the end of the `Main` method:</span></span>

[!code-csharp[RunSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a><span data-ttu-id="88e89-211">Prozkoumat odpovědi na průzkum</span><span class="sxs-lookup"><span data-stu-id="88e89-211">Examine survey responses</span></span>

<span data-ttu-id="88e89-212">Posledním krokem je zobrazení výsledků průzkumu.</span><span class="sxs-lookup"><span data-stu-id="88e89-212">The last step is to display survey results.</span></span> <span data-ttu-id="88e89-213">Přidáte kód do mnoha tříd, které jste napsali.</span><span class="sxs-lookup"><span data-stu-id="88e89-213">You'll add code to many of the classes you've written.</span></span> <span data-ttu-id="88e89-214">Tento kód ukazuje hodnotu rozlišování nullable a non-nullable reference typy.</span><span class="sxs-lookup"><span data-stu-id="88e89-214">This code demonstrates the value of distinguishing nullable and non-nullable reference types.</span></span> <span data-ttu-id="88e89-215">Začněte přidáním následujících dvou členů `SurveyResponse` s výrazem do třídy:</span><span class="sxs-lookup"><span data-stu-id="88e89-215">Start by adding the following two expression-bodied members to the `SurveyResponse` class:</span></span>

[!code-csharp[ReportResponses](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

<span data-ttu-id="88e89-216">Protože `surveyResponses` je typ odkazu s možnou hodnotou null, jsou nezbytné kontroly null před zrušením odkazování.</span><span class="sxs-lookup"><span data-stu-id="88e89-216">Because `surveyResponses` is a nullable reference type, null checks are necessary before de-referencing it.</span></span> <span data-ttu-id="88e89-217">Metoda `Answer` vrátí řetězec s možnou hodnotou null, takže musíme pokrýt případ chybějící odpovědi pomocí operátoru null-coalescing.</span><span class="sxs-lookup"><span data-stu-id="88e89-217">The `Answer` method returns a non-nullable string, so we have to cover the case of a missing answer by using the null-coalescing operator.</span></span>

<span data-ttu-id="88e89-218">Dále přidejte tyto tři členy s `SurveyRun` výrazem do třídy:</span><span class="sxs-lookup"><span data-stu-id="88e89-218">Next, add these three expression-bodied members to the `SurveyRun` class:</span></span>

[!code-csharp[ReportResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

<span data-ttu-id="88e89-219">Člen `AllParticipants` musí vzít v `respondents` úvahu, že proměnná může být null, ale vrácená hodnota nemůže být null.</span><span class="sxs-lookup"><span data-stu-id="88e89-219">The `AllParticipants` member must take into account that the `respondents` variable might be null, but the return value can't be null.</span></span> <span data-ttu-id="88e89-220">Pokud změníte tento výraz `??` odebráním a prázdnou sekvenci, která `null` následuje, kompilátor vás upozorní, že metoda může vrátit a její návratový podpis vrátí typ s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="88e89-220">If you change that expression by removing the `??` and the empty sequence that follows, the compiler warns you the method might return `null` and its return signature returns a non-nullable type.</span></span>

<span data-ttu-id="88e89-221">Nakonec přidejte následující smyčku `Main` v dolní části metody:</span><span class="sxs-lookup"><span data-stu-id="88e89-221">Finally, add the following loop at the bottom of the `Main` method:</span></span>

[!code-csharp[DisplaySurveyResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

<span data-ttu-id="88e89-222">Nepotřebujete žádné `null` kontroly v tomto kódu, protože jste navrhli základní rozhraní tak, aby všechny vrátit nenulové typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="88e89-222">You don't need any `null` checks in this code because you've designed the underlying interfaces so that they all return non-nullable reference types.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="88e89-223">Získání kódu</span><span class="sxs-lookup"><span data-stu-id="88e89-223">Get the code</span></span>

<span data-ttu-id="88e89-224">Můžete získat kód pro hotový kurz z našeho úložiště [vzorků](https://github.com/dotnet/samples) ve složce [csharp/NullableIntroduction.](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction)</span><span class="sxs-lookup"><span data-stu-id="88e89-224">You can get the code for the finished tutorial from our [samples](https://github.com/dotnet/samples) repository in the [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folder.</span></span>

<span data-ttu-id="88e89-225">Experimentujte změnou deklarací typu mezi typy odkazů s možnou hodnotou null a nenulovatelné.</span><span class="sxs-lookup"><span data-stu-id="88e89-225">Experiment by changing the type declarations between nullable and non-nullable reference types.</span></span> <span data-ttu-id="88e89-226">Podívejte se, jak to generuje různá upozornění, abyste `null`náhodou nedereferencili .</span><span class="sxs-lookup"><span data-stu-id="88e89-226">See how that generates different warnings to ensure you don't accidentally dereference a `null`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="88e89-227">Další kroky</span><span class="sxs-lookup"><span data-stu-id="88e89-227">Next steps</span></span>

<span data-ttu-id="88e89-228">Další informace o migraci existující aplikace pro použití typů odkazů s možnou hodnotou null:</span><span class="sxs-lookup"><span data-stu-id="88e89-228">Learn more by migrating an existing application to use nullable reference types:</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="88e89-229">Upgrade aplikace na použití typů odkazů s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="88e89-229">Upgrade an application to use nullable reference types</span></span>](upgrade-to-nullable-references.md)

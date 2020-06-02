---
title: Testování .NET Standard knihovny tříd pomocí .NET Core v Visual Studio Code
description: Vytvoří projekt testu jednotek pro knihovnu tříd .NET Core. Ověřte, zda knihovna tříd .NET Core pracuje správně s testy jednotek.
ms.date: 05/29/2020
ms.openlocfilehash: be227453bd441028cc6ce348c00fad944140238f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292187"
---
# <a name="tutorial-test-a-net-standard-library-with-net-core-in-visual-studio-code"></a><span data-ttu-id="fc833-104">Kurz: testování knihovny .NET Standard pomocí .NET Core v Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="fc833-104">Tutorial: Test a .NET Standard library with .NET Core in Visual Studio Code</span></span>

<span data-ttu-id="fc833-105">V tomto kurzu se dozvíte, jak automatizovat testování částí přidáním testovacího projektu do řešení.</span><span class="sxs-lookup"><span data-stu-id="fc833-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fc833-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc833-106">Prerequisites</span></span>

- <span data-ttu-id="fc833-107">Tento kurz spolupracuje s řešením, které vytvoříte v části [Vytvoření knihovny .NET Standard v Visual Studio Code](library-with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="fc833-107">This tutorial works with the solution that you create in [Create a .NET Standard library in Visual Studio Code](library-with-visual-studio-code.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="fc833-108">Vytvoření projektu testování částí</span><span class="sxs-lookup"><span data-stu-id="fc833-108">Create a unit test project</span></span>

1. <span data-ttu-id="fc833-109">Otevřete Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="fc833-109">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="fc833-110">Otevřete `ClassLibraryProjects` řešení, které jste vytvořili v části [vytvoření knihovny .NET Standard v aplikaci Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="fc833-110">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md).</span></span>

1. <span data-ttu-id="fc833-111">Vytvořte projekt testu jednotek s názvem "StringLibraryTest".</span><span class="sxs-lookup"><span data-stu-id="fc833-111">Create a unit test project named "StringLibraryTest".</span></span>

   ```dotnetcli
   dotnet new mstest -o StringLibraryTest
   ```

   <span data-ttu-id="fc833-112">Šablona projektu vytvoří soubor UnitTest1.cs s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="fc833-112">The project template creates a UnitTest1.cs file with the following code:</span></span>

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestMethod1()
           {
           }
       }
   }
   ```

   <span data-ttu-id="fc833-113">Zdrojový kód vytvořený šablonou testu jednotky provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="fc833-113">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="fc833-114">Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> obor názvů, který obsahuje typy používané pro testování částí.</span><span class="sxs-lookup"><span data-stu-id="fc833-114">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="fc833-115">Aplikuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atribut na `UnitTest1` třídu.</span><span class="sxs-lookup"><span data-stu-id="fc833-115">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="fc833-116">Použije <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atribut k definování `TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="fc833-116">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1`.</span></span>

   <span data-ttu-id="fc833-117">Každá metoda označená pomocí [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) v testovací třídě s označením [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) je provedena automaticky při spuštění testu jednotky.</span><span class="sxs-lookup"><span data-stu-id="fc833-117">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

   > [!NOTE]
   > <span data-ttu-id="fc833-118">MSTest je jedna ze tří testovacích rozhraní, ze kterých si můžete vybrat.</span><span class="sxs-lookup"><span data-stu-id="fc833-118">MSTest is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="fc833-119">Ostatní jsou xUnit a nUnit.</span><span class="sxs-lookup"><span data-stu-id="fc833-119">The others are xUnit and nUnit.</span></span>

1. <span data-ttu-id="fc833-120">Přidejte testovací projekt do řešení.</span><span class="sxs-lookup"><span data-stu-id="fc833-120">Add the test project to the solution.</span></span>

   ```dotnetcli
   dotnet sln add StringLibraryTest/StringLibraryTest.csproj
   ```

1. <span data-ttu-id="fc833-121">Vytvořte odkaz na projekt knihovny tříd spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="fc833-121">Create a project reference to the class library project by running the following command:</span></span>

   ```dotnetcli
   dotnet add StringLibraryTest/StringLibraryTest.csproj reference StringLibrary/StringLibrary.csproj
   ```

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="fc833-122">Přidat a spustit metody testování částí</span><span class="sxs-lookup"><span data-stu-id="fc833-122">Add and run unit test methods</span></span>

<span data-ttu-id="fc833-123">Když aplikace Visual Studio spustí test jednotky, provede každou metodu, která je označena <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atributem ve třídě, která je označena <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="fc833-123">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="fc833-124">Testovací metoda končí při nalezení prvního selhání nebo po úspěšném dokončení všech testů obsažených v metodě.</span><span class="sxs-lookup"><span data-stu-id="fc833-124">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="fc833-125">Nejběžnější testy volají členy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> třídy.</span><span class="sxs-lookup"><span data-stu-id="fc833-125">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="fc833-126">Mnoho metod Assert zahrnuje nejméně dva parametry, jeden z nich je očekávaný výsledek testu a druhý z nich je skutečný výsledek testu.</span><span class="sxs-lookup"><span data-stu-id="fc833-126">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="fc833-127">`Assert`V následující tabulce jsou uvedeny některé často volané metody třídy:</span><span class="sxs-lookup"><span data-stu-id="fc833-127">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="fc833-128">Metody Assert</span><span class="sxs-lookup"><span data-stu-id="fc833-128">Assert methods</span></span>     | <span data-ttu-id="fc833-129">Funkce</span><span class="sxs-lookup"><span data-stu-id="fc833-129">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="fc833-130">Ověřuje, zda jsou dvě hodnoty nebo objekty stejné.</span><span class="sxs-lookup"><span data-stu-id="fc833-130">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="fc833-131">Vyhodnocení se nezdařila, pokud se hodnoty nebo objekty neshodují.</span><span class="sxs-lookup"><span data-stu-id="fc833-131">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="fc833-132">Ověřuje, že dvě proměnné objektu odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="fc833-132">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="fc833-133">Pokud proměnné odkazují na různé objekty, vyhodnocení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="fc833-133">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="fc833-134">Ověřuje, jestli je podmínka `false` .</span><span class="sxs-lookup"><span data-stu-id="fc833-134">Verifies that a condition is `false`.</span></span> <span data-ttu-id="fc833-135">Pokud je podmínka, vyhodnocení se nezdařilo `true` .</span><span class="sxs-lookup"><span data-stu-id="fc833-135">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="fc833-136">Ověřuje, že objekt není `null` .</span><span class="sxs-lookup"><span data-stu-id="fc833-136">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="fc833-137">Pokud je objekt, vyhodnocení se nezdařilo `null` .</span><span class="sxs-lookup"><span data-stu-id="fc833-137">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="fc833-138">Můžete také použít <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> metodu v testovací metodě k označení typu výjimky, kterou očekává, že má být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="fc833-138">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="fc833-139">Test se nezdařil, pokud není vyvolána zadaná výjimka.</span><span class="sxs-lookup"><span data-stu-id="fc833-139">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="fc833-140">Při testování `StringLibrary.StartsWithUpper` metody je třeba zadat počet řetězců, které začínají velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="fc833-140">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="fc833-141">Očekáváte, že se metoda vrátí `true` v těchto případech, takže můžete volat <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="fc833-141">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fc833-142">Podobně je vhodné zadat počet řetězců, které začínají jinou výjimkou znaku velkého písmene.</span><span class="sxs-lookup"><span data-stu-id="fc833-142">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="fc833-143">Očekáváte, že se metoda vrátí `false` v těchto případech, takže můžete volat <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="fc833-143">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="fc833-144">Vzhledem k tomu, že vaše metoda knihovny zpracovává řetězce, je také vhodné se ujistit, že úspěšně zpracovává [prázdný řetězec ( `String.Empty` )](xref:System.String.Empty) a a `null` řetězec.</span><span class="sxs-lookup"><span data-stu-id="fc833-144">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty) and a and a `null` string.</span></span> <span data-ttu-id="fc833-145">Prázdný řetězec je jeden, který nemá žádné znaky a jehož hodnota <xref:System.String.Length> je 0.</span><span class="sxs-lookup"><span data-stu-id="fc833-145">An empty string is one that has no characters and whose <xref:System.String.Length> is 0.</span></span> <span data-ttu-id="fc833-146">`null`Řetězec je ten, který se neinicializoval.</span><span class="sxs-lookup"><span data-stu-id="fc833-146">A `null` string is one that hasn't been initialized.</span></span> <span data-ttu-id="fc833-147">Můžete zavolat `StartsWithUpper` přímo jako statickou metodu a předat jeden <xref:System.String> argument.</span><span class="sxs-lookup"><span data-stu-id="fc833-147">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="fc833-148">Nebo můžete zavolat `StartsWithUpper` jako metodu rozšíření pro `string` proměnnou přiřazenou k `null` .</span><span class="sxs-lookup"><span data-stu-id="fc833-148">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="fc833-149">Budete definovat tři metody, z nichž každá volá <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metodu opakovaně pro každý prvek v poli řetězců.</span><span class="sxs-lookup"><span data-stu-id="fc833-149">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="fc833-150">Vzhledem k tomu, že testovací metoda selže, jakmile najde první selhání, zavoláte přetížení metody, které vám umožní předat řetězec, který označuje hodnotu řetězce použitou ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="fc833-150">Because the test method fails as soon as it finds the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="fc833-151">Postup vytvoření testovacích metod:</span><span class="sxs-lookup"><span data-stu-id="fc833-151">To create the test methods:</span></span>

1. <span data-ttu-id="fc833-152">Otevřete *StringLibraryTest/UnitTest1. cs* a nahraďte celý kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="fc833-152">Open *StringLibraryTest/UnitTest1.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   <span data-ttu-id="fc833-153">Test velkých písmen v `TestStartsWithUpper` metodě obsahuje řecké velké písmeno alfa (u + 0391) a velké písmeno cyrilice em (u + 041C).</span><span class="sxs-lookup"><span data-stu-id="fc833-153">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="fc833-154">Test malých písmen v `TestDoesNotStartWithUpper` metodě obsahuje řecké malé písmeno alfa (U + 03B1) a malé písmeno g (u + 0433).</span><span class="sxs-lookup"><span data-stu-id="fc833-154">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="fc833-155">Uložte provedené změny.</span><span class="sxs-lookup"><span data-stu-id="fc833-155">Save your changes.</span></span>

1. <span data-ttu-id="fc833-156">Spusťte testy:</span><span class="sxs-lookup"><span data-stu-id="fc833-156">Run the tests:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   <span data-ttu-id="fc833-157">Výstup terminálu ukazuje, že všechny testy byly úspěšné.</span><span class="sxs-lookup"><span data-stu-id="fc833-157">The terminal output shows that all tests passed.</span></span>

   ```
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.

   Test Run Successful.
   Total tests: 3
        Passed: 3
   Total time: 5.1116 Seconds
   ```

## <a name="handle-test-failures"></a><span data-ttu-id="fc833-158">Zpracování selhání testu</span><span class="sxs-lookup"><span data-stu-id="fc833-158">Handle test failures</span></span>

<span data-ttu-id="fc833-159">Pokud pracujete s vývojem řízeným testováním (TDD), napíšete nejprve testy a při jejich prvním spuštění dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="fc833-159">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="fc833-160">Potom do aplikace přidáte kód, který provede test úspěšně.</span><span class="sxs-lookup"><span data-stu-id="fc833-160">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="fc833-161">V tomto případě jste po zápisu kódu aplikace, který ověřuje, vytvořili test, takže jste neviděli test neúspěšný.</span><span class="sxs-lookup"><span data-stu-id="fc833-161">In this case, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="fc833-162">Chcete-li ověřit, že test selže, pokud očekáváte, že selže, přidejte do vstupu testu neplatnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fc833-162">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="fc833-163">Upravte `words` pole v `TestDoesNotStartWithUpper` metodě tak, aby obsahovalo řetězec "Error" (chyba).</span><span class="sxs-lookup"><span data-stu-id="fc833-163">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. <span data-ttu-id="fc833-164">Spusťte testy:</span><span class="sxs-lookup"><span data-stu-id="fc833-164">Run the tests:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   <span data-ttu-id="fc833-165">Výstup terminálu ukazuje, že jeden test se nezdařil, a obsahuje chybovou zprávu pro neúspěšný test.</span><span class="sxs-lookup"><span data-stu-id="fc833-165">The terminal output shows that one test fails, and it provides an error message for the failed test.</span></span>

   ```
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.
     X TestDoesNotStartWithUpper [283ms]
     Error Message:
      Assert.IsFalse failed. Expected for 'Error': false; Actual: True
     Stack Trace:
     at StringLibraryTest.UnitTest1.TestDoesNotStartWithUpper()
       in C:\Projects\ClassLibraryProjects\StringLibraryTest\UnitTest1.cs:line 33

   Test Run Failed.
   Total tests: 3
        Passed: 2
        Failed: 1
   Total time: 1.7825 Seconds
   ```

1. <span data-ttu-id="fc833-166">Vraťte změny, které jste provedli v kroku 1, a odeberte řetězec "Error" (chyba).</span><span class="sxs-lookup"><span data-stu-id="fc833-166">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="fc833-167">Spusťte test znovu a testy proběhnou znovu.</span><span class="sxs-lookup"><span data-stu-id="fc833-167">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="fc833-168">Testování verze pro vydání knihovny</span><span class="sxs-lookup"><span data-stu-id="fc833-168">Test the Release version of the library</span></span>

<span data-ttu-id="fc833-169">Nyní, když testy prošly všechny při spuštění ladicí verze knihovny, spusťte testy dodatečně k sestavení vydání knihovny.</span><span class="sxs-lookup"><span data-stu-id="fc833-169">Now that the tests have all passed when running the Debug version of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="fc833-170">Několik faktorů, včetně optimalizací kompilátoru, může někdy způsobit různé chování mezi sestaveními ladění a vydání.</span><span class="sxs-lookup"><span data-stu-id="fc833-170">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

1. <span data-ttu-id="fc833-171">Spusťte testy s konfigurací sestavení vydaných verzí:</span><span class="sxs-lookup"><span data-stu-id="fc833-171">Run the tests with the Release build configuration:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj --configuration Release
   ```

   <span data-ttu-id="fc833-172">Testy jsou passované.</span><span class="sxs-lookup"><span data-stu-id="fc833-172">The tests pass.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="fc833-173">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="fc833-173">Additional resources</span></span>

- [<span data-ttu-id="fc833-174">Testování částí v .NET Core a .NET Standard</span><span class="sxs-lookup"><span data-stu-id="fc833-174">Unit testing in .NET Core and .NET Standard</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="fc833-175">Další kroky</span><span class="sxs-lookup"><span data-stu-id="fc833-175">Next steps</span></span>

<span data-ttu-id="fc833-176">V tomto kurzu testujete jednotku knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="fc833-176">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="fc833-177">Knihovnu můžete zpřístupnit ostatním tím, že ji publikujete do [NuGet](https://nuget.org) jako balíček.</span><span class="sxs-lookup"><span data-stu-id="fc833-177">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="fc833-178">Pokud se chcete dozvědět, jak postupovat, postupujte podle kurzu NuGet:</span><span class="sxs-lookup"><span data-stu-id="fc833-178">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fc833-179">Vytvoření a publikování balíčku pomocí rozhraní příkazového řádku dotnet</span><span class="sxs-lookup"><span data-stu-id="fc833-179">Create and publish a package using the dotnet CLI</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

<span data-ttu-id="fc833-180">Pokud knihovnu publikujete jako balíček NuGet, můžou ji nainstalovat a používat i ostatní.</span><span class="sxs-lookup"><span data-stu-id="fc833-180">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="fc833-181">Pokud se chcete dozvědět, jak postupovat, postupujte podle kurzu NuGet:</span><span class="sxs-lookup"><span data-stu-id="fc833-181">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fc833-182">Instalace a použití balíčku pomocí rozhraní příkazového řádku dotnet</span><span class="sxs-lookup"><span data-stu-id="fc833-182">Install and use a package using the dotnet CLI</span></span>](/nuget/quickstart/install-and-use-a-package-using-the-dotnet-cli)

<span data-ttu-id="fc833-183">Knihovna nemusí být distribuována jako balíček.</span><span class="sxs-lookup"><span data-stu-id="fc833-183">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="fc833-184">Dá se seskupit pomocí konzolové aplikace, která ho používá.</span><span class="sxs-lookup"><span data-stu-id="fc833-184">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="fc833-185">Informace o tom, jak publikovat konzolovou aplikaci, najdete v předchozím kurzu v této sérii:</span><span class="sxs-lookup"><span data-stu-id="fc833-185">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fc833-186">Publikování konzolové aplikace .NET Core pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="fc833-186">Publish a .NET Core console application with Visual Studio Code</span></span>](publishing-with-visual-studio-code.md)

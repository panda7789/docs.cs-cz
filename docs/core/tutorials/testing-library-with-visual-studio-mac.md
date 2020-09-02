---
title: Otestování .NET Standard knihovny tříd pomocí .NET Core s využitím Visual Studio pro Mac
description: Vytvoří projekt testu jednotek pro knihovnu tříd .NET Core. Ověřte, zda knihovna tříd .NET Core pracuje správně s testy jednotek.
ms.date: 06/08/2020
ms.openlocfilehash: d3c8a5e01d16047949e977f3af6a429970d996d0
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359217"
---
# <a name="test-a-net-standard-class-library-with-net-core-using-visual-studio"></a><span data-ttu-id="b6427-104">Testování knihovny tříd .NET Standard pomocí .NET Core pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b6427-104">Test a .NET Standard class library with .NET Core using Visual Studio</span></span>

<span data-ttu-id="b6427-105">V tomto kurzu se dozvíte, jak automatizovat testování částí přidáním testovacího projektu do řešení.</span><span class="sxs-lookup"><span data-stu-id="b6427-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b6427-106">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="b6427-106">Prerequisites</span></span>

- <span data-ttu-id="b6427-107">Tento kurz spolupracuje s řešením, které vytvoříte v části [Vytvoření knihovny .NET Standard pomocí Visual Studio pro Mac](library-with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="b6427-107">This tutorial works with the solution that you create in [Create a .NET Standard library using Visual Studio for Mac](library-with-visual-studio-mac.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="b6427-108">Vytvoření projektu testování částí</span><span class="sxs-lookup"><span data-stu-id="b6427-108">Create a unit test project</span></span>

<span data-ttu-id="b6427-109">Testy jednotek poskytují automatizované softwarové testování během vývoje a publikování.</span><span class="sxs-lookup"><span data-stu-id="b6427-109">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="b6427-110">[MSTest](https://github.com/Microsoft/testfx-docs) je jedna ze tří testovacích rozhraní, ze kterých si můžete vybrat.</span><span class="sxs-lookup"><span data-stu-id="b6427-110">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="b6427-111">Ostatní jsou [xUnit](https://xunit.net/) a [nUnit](https://nunit.org/).</span><span class="sxs-lookup"><span data-stu-id="b6427-111">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="b6427-112">Spusťte Visual Studio pro Mac.</span><span class="sxs-lookup"><span data-stu-id="b6427-112">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="b6427-113">Otevřete `ClassLibraryProjects` řešení, které jste vytvořili v části [vytvoření knihovny .NET Standard pomocí Visual Studio pro Mac](library-with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="b6427-113">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library using Visual Studio for Mac](library-with-visual-studio-mac.md).</span></span>

1. <span data-ttu-id="b6427-114">Na panelu **řešení** <kbd>klikněte na</kbd> `ClassLibraryProjects` řešení a vyberte **Přidat**  >  **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="b6427-114">In the **Solution** pad, <kbd>ctrl</kbd>-click the `ClassLibraryProjects` solution and select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="b6427-115">V dialogovém okně **Nový projekt** vyberte možnost **testy** z uzlu **web a konzola** .</span><span class="sxs-lookup"><span data-stu-id="b6427-115">In the **New Project** dialog, select **Tests** from the **Web and Console** node.</span></span> <span data-ttu-id="b6427-116">Vyberte **projekt MSTest** a potom klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="b6427-116">Select the **MSTest Project** followed by **Next**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-project.png" alt-text="Visual Studio – nový projekt – dialogové okno pro vytvoření testovacího projektu":::

1. <span data-ttu-id="b6427-118">Vyberte **.NET Core 3,1**.</span><span class="sxs-lookup"><span data-stu-id="b6427-118">Select **.NET Core 3.1**.</span></span> <span data-ttu-id="b6427-119">Pojmenujte nový projekt "StringLibraryTest" a vyberte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="b6427-119">Name the new project "StringLibraryTest" and select **Create**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-new-project-name.png" alt-text="Visual Studio Mac – dialog nového projektu zadání názvu projektu":::

   <span data-ttu-id="b6427-121">Visual Studio vytvoří soubor třídy s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="b6427-121">Visual Studio creates a class file with the following code:</span></span>

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

   <span data-ttu-id="b6427-122">Zdrojový kód vytvořený šablonou testu jednotky provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="b6427-122">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="b6427-123">Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> obor názvů, který obsahuje typy používané pro testování částí.</span><span class="sxs-lookup"><span data-stu-id="b6427-123">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="b6427-124">Aplikuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atribut na `UnitTest1` třídu.</span><span class="sxs-lookup"><span data-stu-id="b6427-124">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="b6427-125">Aplikuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atribut na `TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="b6427-125">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to `TestMethod1`.</span></span>

   <span data-ttu-id="b6427-126">Každá metoda označená pomocí [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) v testovací třídě s označením [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) je provedena automaticky při spuštění testu jednotky.</span><span class="sxs-lookup"><span data-stu-id="b6427-126">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="b6427-127">Přidat odkaz na projekt</span><span class="sxs-lookup"><span data-stu-id="b6427-127">Add a project reference</span></span>

<span data-ttu-id="b6427-128">Aby projekt testu spolupracoval s `StringLibrary` třídou, přidejte odkaz na `StringLibrary` projekt.</span><span class="sxs-lookup"><span data-stu-id="b6427-128">For the test project to work with the `StringLibrary` class, add a reference to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="b6427-129">Na panelu **řešení** klikněte v části **StringLibraryTest**na **závislosti** <kbd>CTRL</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b6427-129">In the **Solution** pad, <kbd>ctrl</kbd>-click **Dependencies** under **StringLibraryTest**.</span></span> <span data-ttu-id="b6427-130">V místní nabídce vyberte **Přidat odkaz** .</span><span class="sxs-lookup"><span data-stu-id="b6427-130">Select **Add Reference** from the context menu.</span></span>

1. <span data-ttu-id="b6427-131">V dialogovém okně **odkazy** vyberte projekt **StringLibrary** .</span><span class="sxs-lookup"><span data-stu-id="b6427-131">In the **References** dialog, select the **StringLibrary** project.</span></span> <span data-ttu-id="b6427-132">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="b6427-132">Select **OK**.</span></span>

      :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-edit-references.png" alt-text="Dialogové okno Visual Studio Mac Edit References":::

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="b6427-134">Přidat a spustit metody testování částí</span><span class="sxs-lookup"><span data-stu-id="b6427-134">Add and run unit test methods</span></span>

<span data-ttu-id="b6427-135">Když aplikace Visual Studio spustí test jednotky, provede každou metodu, která je označena <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atributem ve třídě, která je označena  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="b6427-135">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="b6427-136">Testovací metoda končí při nalezení prvního selhání nebo po úspěšném dokončení všech testů obsažených v metodě.</span><span class="sxs-lookup"><span data-stu-id="b6427-136">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="b6427-137">Nejběžnější testy volají členy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> třídy.</span><span class="sxs-lookup"><span data-stu-id="b6427-137">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="b6427-138">Mnoho metod Assert zahrnuje nejméně dva parametry, jeden z nich je očekávaný výsledek testu a druhý z nich je skutečný výsledek testu.</span><span class="sxs-lookup"><span data-stu-id="b6427-138">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="b6427-139">`Assert`V následující tabulce jsou uvedeny některé často volané metody třídy:</span><span class="sxs-lookup"><span data-stu-id="b6427-139">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="b6427-140">Metody Assert</span><span class="sxs-lookup"><span data-stu-id="b6427-140">Assert methods</span></span>     | <span data-ttu-id="b6427-141">Funkce</span><span class="sxs-lookup"><span data-stu-id="b6427-141">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="b6427-142">Ověřuje, zda jsou dvě hodnoty nebo objekty stejné.</span><span class="sxs-lookup"><span data-stu-id="b6427-142">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="b6427-143">Vyhodnocení se nezdařila, pokud se hodnoty nebo objekty neshodují.</span><span class="sxs-lookup"><span data-stu-id="b6427-143">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="b6427-144">Ověřuje, že dvě proměnné objektu odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="b6427-144">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="b6427-145">Pokud proměnné odkazují na různé objekty, vyhodnocení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="b6427-145">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="b6427-146">Ověřuje, jestli je podmínka `false` .</span><span class="sxs-lookup"><span data-stu-id="b6427-146">Verifies that a condition is `false`.</span></span> <span data-ttu-id="b6427-147">Pokud je podmínka, vyhodnocení se nezdařilo `true` .</span><span class="sxs-lookup"><span data-stu-id="b6427-147">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="b6427-148">Ověřuje, že objekt není `null` .</span><span class="sxs-lookup"><span data-stu-id="b6427-148">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="b6427-149">Pokud je objekt, vyhodnocení se nezdařilo `null` .</span><span class="sxs-lookup"><span data-stu-id="b6427-149">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="b6427-150">Můžete také použít <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> metodu v testovací metodě k označení typu výjimky, kterou očekává, že má být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="b6427-150">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="b6427-151">Test se nezdařil, pokud není vyvolána zadaná výjimka.</span><span class="sxs-lookup"><span data-stu-id="b6427-151">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="b6427-152">Při testování `StringLibrary.StartsWithUpper` metody je třeba zadat počet řetězců, které začínají velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="b6427-152">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="b6427-153">Očekáváte, že se metoda vrátí `true` v těchto případech, takže můžete volat <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="b6427-153">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b6427-154">Podobně je vhodné zadat počet řetězců, které začínají jinou výjimkou znaku velkého písmene.</span><span class="sxs-lookup"><span data-stu-id="b6427-154">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="b6427-155">Očekáváte, že se metoda vrátí `false` v těchto případech, takže můžete volat <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="b6427-155">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="b6427-156">Vzhledem k tomu, že vaše metoda knihovny zpracovává řetězce, je také vhodné se ujistit, že úspěšně zpracovává [prázdný řetězec ( `String.Empty` )](xref:System.String.Empty), platný řetězec, který neobsahuje žádné znaky a jehož <xref:System.String.Length> hodnota je 0, a `null` řetězec, který nebyl inicializován.</span><span class="sxs-lookup"><span data-stu-id="b6427-156">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="b6427-157">Můžete zavolat `StartsWithUpper` přímo jako statickou metodu a předat jeden <xref:System.String> argument.</span><span class="sxs-lookup"><span data-stu-id="b6427-157">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="b6427-158">Nebo můžete zavolat `StartsWithUpper` jako metodu rozšíření pro `string` proměnnou přiřazenou k `null` .</span><span class="sxs-lookup"><span data-stu-id="b6427-158">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="b6427-159">Budete definovat tři metody, z nichž každá volá <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metodu pro každý prvek v poli řetězců.</span><span class="sxs-lookup"><span data-stu-id="b6427-159">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="b6427-160">Zavoláte přetížení metody, které vám umožní zadat chybovou zprávu, která se zobrazí v případě selhání testu.</span><span class="sxs-lookup"><span data-stu-id="b6427-160">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="b6427-161">Zpráva identifikuje řetězec, který způsobil chybu.</span><span class="sxs-lookup"><span data-stu-id="b6427-161">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="b6427-162">Postup vytvoření testovacích metod:</span><span class="sxs-lookup"><span data-stu-id="b6427-162">To create the test methods:</span></span>

1. <span data-ttu-id="b6427-163">Otevřete soubor *UnitTest1.cs* a nahraďte kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="b6427-163">Open the *UnitTest1.cs* file and replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   <span data-ttu-id="b6427-164">Test velkých písmen v `TestStartsWithUpper` metodě obsahuje řecké velké písmeno alfa (u + 0391) a velké písmeno cyrilice em (u + 041C).</span><span class="sxs-lookup"><span data-stu-id="b6427-164">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="b6427-165">Test malých písmen v `TestDoesNotStartWithUpper` metodě obsahuje řecké malé písmeno alfa (U + 03B1) a malé písmeno g (u + 0433).</span><span class="sxs-lookup"><span data-stu-id="b6427-165">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="b6427-166">V řádku nabídek vyberte **soubor**  >  **Uložit jako**.</span><span class="sxs-lookup"><span data-stu-id="b6427-166">On the menu bar, select **File** > **Save As**.</span></span> <span data-ttu-id="b6427-167">V dialogovém okně se ujistěte, že je **kódování** nastaveno na **kódování Unicode (UTF-8)**.</span><span class="sxs-lookup"><span data-stu-id="b6427-167">In the dialog, make sure that **Encoding** is set to **Unicode (UTF-8)**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/save-file-as-dialog.png" alt-text="Visual Studio uložit soubor jako dialog":::

1. <span data-ttu-id="b6427-169">Až se zobrazí dotaz, jestli chcete nahradit existující soubor, vyberte **nahradit**.</span><span class="sxs-lookup"><span data-stu-id="b6427-169">When you're asked if you want to replace the existing file, select **Replace**.</span></span>

   <span data-ttu-id="b6427-170">Pokud neuložíte zdrojový kód jako soubor s kódováním UTF8, Visual Studio ho může uložit jako soubor ASCII.</span><span class="sxs-lookup"><span data-stu-id="b6427-170">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="b6427-171">Pokud k tomu dojde, modul runtime nebude přesně kódovat znaky UTF8 mimo rozsah ASCII a výsledky testu nebudou správné.</span><span class="sxs-lookup"><span data-stu-id="b6427-171">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="b6427-172">Otevřete panel **testování částí** na pravé straně obrazovky.</span><span class="sxs-lookup"><span data-stu-id="b6427-172">Open the **Unit Tests** panel on the right side of the screen.</span></span> <span data-ttu-id="b6427-173">V nabídce vyberte **Zobrazit**  >  **testy** .</span><span class="sxs-lookup"><span data-stu-id="b6427-173">Select **View** > **Tests** from the menu.</span></span>

1. <span data-ttu-id="b6427-174">Kliknutím na ikonu **Dock (ukotvit** ) ponechejte panel otevřený.</span><span class="sxs-lookup"><span data-stu-id="b6427-174">Click the **Dock** icon to keep the panel open.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-dock-icon.png" alt-text="Ikona ukotvení panelu Visual Studio pro Mac testování částí":::

1. <span data-ttu-id="b6427-176">Klikněte na tlačítko **Spustit vše** .</span><span class="sxs-lookup"><span data-stu-id="b6427-176">Click the **Run All** button.</span></span>

   <span data-ttu-id="b6427-177">Všechny testy jsou passované.</span><span class="sxs-lookup"><span data-stu-id="b6427-177">All tests pass.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-pass.png" alt-text="Visual Studio pro Mac očekávanou zkušební průchody":::

## <a name="handle-test-failures"></a><span data-ttu-id="b6427-179">Zpracování selhání testu</span><span class="sxs-lookup"><span data-stu-id="b6427-179">Handle test failures</span></span>

<span data-ttu-id="b6427-180">Pokud pracujete s vývojem řízeným testováním (TDD), napíšete nejprve testy a při jejich prvním spuštění dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="b6427-180">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="b6427-181">Potom do aplikace přidáte kód, který provede test úspěšně.</span><span class="sxs-lookup"><span data-stu-id="b6427-181">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="b6427-182">Pro tento kurz jste vytvořili test po zápisu kódu aplikace, který ověřuje, takže jste neviděli test neúspěšný.</span><span class="sxs-lookup"><span data-stu-id="b6427-182">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="b6427-183">Chcete-li ověřit, že test selže, pokud očekáváte, že selže, přidejte do vstupu testu neplatnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b6427-183">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="b6427-184">Upravte `words` pole v `TestDoesNotStartWithUpper` metodě tak, aby obsahovalo řetězec "Error" (chyba).</span><span class="sxs-lookup"><span data-stu-id="b6427-184">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="b6427-185">Nemusíte soubor ukládat, protože Visual Studio automaticky ukládá otevřené soubory, když je řešení sestaveno pro spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="b6427-185">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. <span data-ttu-id="b6427-186">Spusťte testy znovu.</span><span class="sxs-lookup"><span data-stu-id="b6427-186">Run the tests again.</span></span>

   <span data-ttu-id="b6427-187">Tentokrát okno **Průzkumník testů** indikuje, že dva testy byly úspěšné a jedna se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="b6427-187">This time, the **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/failed-test-window.png" alt-text="Okno Průzkumníka testů s neúspěšnými testy":::

1. <span data-ttu-id="b6427-189"><kbd>stiskněte klávesu CTRL</kbd>a klikněte na neúspěšný test `TestDoesNotStartWithUpper` a v místní nabídce vyberte možnost **Zobrazit panel výsledků** .</span><span class="sxs-lookup"><span data-stu-id="b6427-189"><kbd>ctrl</kbd>-click the failed test, `TestDoesNotStartWithUpper`, and select **Show Results Pad** from the context menu.</span></span>

   <span data-ttu-id="b6427-190">Na panelu **výsledků** se zobrazí zpráva vytvořená kontrolním výrazem: Assert. NEPRAVDA.</span><span class="sxs-lookup"><span data-stu-id="b6427-190">The **Results** pad displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="b6427-191">Očekávané pro ' error ': false; skutečnost: true ".</span><span class="sxs-lookup"><span data-stu-id="b6427-191">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="b6427-192">Z důvodu chyby nejsou v poli Po otestování "Error" žádné řetězce.</span><span class="sxs-lookup"><span data-stu-id="b6427-192">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-failure.png" alt-text="Okno Průzkumníka testů znázorňující chybu kontrolního výrazu NEPRAVDA":::

1. <span data-ttu-id="b6427-194">Odeberte řetězec "Error", který jste přidali v kroku 1.</span><span class="sxs-lookup"><span data-stu-id="b6427-194">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="b6427-195">Spusťte test znovu a testy proběhnou znovu.</span><span class="sxs-lookup"><span data-stu-id="b6427-195">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="b6427-196">Testování verze pro vydání knihovny</span><span class="sxs-lookup"><span data-stu-id="b6427-196">Test the Release version of the library</span></span>

<span data-ttu-id="b6427-197">Nyní, když testy úspěšně prošly při spuštění sestavení ladění knihovny, spusťte testy dodatečně k sestavení vydání knihovny.</span><span class="sxs-lookup"><span data-stu-id="b6427-197">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="b6427-198">Několik faktorů, včetně optimalizací kompilátoru, může někdy způsobit různé chování mezi sestaveními ladění a vydání.</span><span class="sxs-lookup"><span data-stu-id="b6427-198">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="b6427-199">Testování sestavení pro vydání:</span><span class="sxs-lookup"><span data-stu-id="b6427-199">To test the Release build:</span></span>

1. <span data-ttu-id="b6427-200">Na panelu nástrojů sady Visual Studio změňte konfiguraci sestavení z **ladit** na **release**.</span><span class="sxs-lookup"><span data-stu-id="b6427-200">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="Panel nástrojů sady Visual Studio s zvýrazněným sestavením pro vydání":::

1. <span data-ttu-id="b6427-202">Na panelu **řešení** klikněte v nabídce <kbd>CTRL</kbd>na projekt **StringLibrary** a vyberte **sestavení** z místní nabídky pro rekompilaci knihovny.</span><span class="sxs-lookup"><span data-stu-id="b6427-202">In the **Solution** pad, <kbd>ctrl</kbd>-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/build-library-context-menu.png" alt-text="Místní nabídka StringLibrary s příkazem Build":::

1. <span data-ttu-id="b6427-204">Znovu spusťte testy jednotek.</span><span class="sxs-lookup"><span data-stu-id="b6427-204">Run the unit tests again.</span></span>

   <span data-ttu-id="b6427-205">Testy jsou passované.</span><span class="sxs-lookup"><span data-stu-id="b6427-205">The tests pass.</span></span>

## <a name="debug-tests"></a><span data-ttu-id="b6427-206">Ladit testy</span><span class="sxs-lookup"><span data-stu-id="b6427-206">Debug tests</span></span>

<span data-ttu-id="b6427-207">Můžete použít stejný postup jako v [kurzu: ladění konzolové aplikace .NET Core pomocí Visual Studio pro Mac](debugging-with-visual-studio-mac.md) pro ladění kódu pomocí projektu testování částí.</span><span class="sxs-lookup"><span data-stu-id="b6427-207">You can use the same process shown in [Tutorial: Debug a .NET Core console application using Visual Studio for Mac](debugging-with-visual-studio-mac.md) to debug code using your unit test project.</span></span> <span data-ttu-id="b6427-208">Místo spuštění projektu <kbd>aplikace pro</kbd>selektory klikněte v místní nabídce na projekt **StringLibraryTests** a vyberte **Spustit ladění projektu** .</span><span class="sxs-lookup"><span data-stu-id="b6427-208">Instead of starting the ShowCase app project, <kbd>ctrl</kbd>-click the **StringLibraryTests** project, and select **Start Debugging Project** from the context menu.</span></span> <span data-ttu-id="b6427-209">Visual Studio spustí testovací projekt pomocí připojeného ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="b6427-209">Visual Studio starts the test project with the debugger attached.</span></span> <span data-ttu-id="b6427-210">Spuštění se zastaví na všech zarážekch, které jste přidali do testovacího projektu, nebo na podkladový kód knihovny.</span><span class="sxs-lookup"><span data-stu-id="b6427-210">Execution will stop at any breakpoint you've added to the test project or the underlying library code.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="b6427-211">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="b6427-211">Additional resources</span></span>

* [<span data-ttu-id="b6427-212">Testování částí v .NET Core a .NET Standard</span><span class="sxs-lookup"><span data-stu-id="b6427-212">Unit testing in .NET Core and .NET Standard</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="b6427-213">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b6427-213">Next steps</span></span>

<span data-ttu-id="b6427-214">V tomto kurzu testujete jednotku knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="b6427-214">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="b6427-215">Knihovnu můžete zpřístupnit ostatním tím, že ji publikujete do [NuGet](https://nuget.org) jako balíček.</span><span class="sxs-lookup"><span data-stu-id="b6427-215">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="b6427-216">Pokud se chcete dozvědět, jak postupovat, postupujte podle kurzu NuGet:</span><span class="sxs-lookup"><span data-stu-id="b6427-216">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b6427-217">Vytvoření a publikování balíčku (rozhraní příkazového řádku dotnet)</span><span class="sxs-lookup"><span data-stu-id="b6427-217">Create and publish a package (dotnet CLI)</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

<span data-ttu-id="b6427-218">Pokud knihovnu publikujete jako balíček NuGet, můžou ji nainstalovat a používat i ostatní.</span><span class="sxs-lookup"><span data-stu-id="b6427-218">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="b6427-219">Pokud se chcete dozvědět, jak postupovat, postupujte podle kurzu NuGet:</span><span class="sxs-lookup"><span data-stu-id="b6427-219">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b6427-220">Instalace a použití balíčku v Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="b6427-220">Install and use a package in Visual Studio for Mac</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

<span data-ttu-id="b6427-221">Knihovna nemusí být distribuována jako balíček.</span><span class="sxs-lookup"><span data-stu-id="b6427-221">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="b6427-222">Dá se seskupit pomocí konzolové aplikace, která ho používá.</span><span class="sxs-lookup"><span data-stu-id="b6427-222">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="b6427-223">Informace o tom, jak publikovat konzolovou aplikaci, najdete v předchozím kurzu v této sérii:</span><span class="sxs-lookup"><span data-stu-id="b6427-223">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b6427-224">Publikování konzolové aplikace .NET Core pomocí Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="b6427-224">Publish a .NET Core console application using Visual Studio for Mac</span></span>](publishing-with-visual-studio-mac.md)

---
title: Testování knihovny tříd .NET Standard pomocí .NET Core pomocí sady Visual Studio
description: Vytvoří projekt testu jednotek pro knihovnu tříd .NET Core. Ověřte, zda knihovna tříd .NET Core pracuje správně s testy jednotek.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: f20b089fd22794d5aaeff34502e960fe41a565e1
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2020
ms.locfileid: "84700966"
---
# <a name="tutorial-test-a-net-standard-class-library-with-net-core-using-visual-studio"></a><span data-ttu-id="73624-104">Kurz: testování .NET Standard knihovny tříd pomocí .NET Core pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="73624-104">Tutorial: Test a .NET Standard class library with .NET Core using Visual Studio</span></span>

<span data-ttu-id="73624-105">V tomto kurzu se dozvíte, jak automatizovat testování částí přidáním testovacího projektu do řešení.</span><span class="sxs-lookup"><span data-stu-id="73624-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="73624-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73624-106">Prerequisites</span></span>

- <span data-ttu-id="73624-107">Tento kurz spolupracuje s řešením, které vytvoříte v části [Vytvoření knihovny .NET Standard v sadě Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="73624-107">This tutorial works with the solution that you create in [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="73624-108">Vytvoření projektu testování částí</span><span class="sxs-lookup"><span data-stu-id="73624-108">Create a unit test project</span></span>

<span data-ttu-id="73624-109">Testy jednotek poskytují automatizované softwarové testování během vývoje a publikování.</span><span class="sxs-lookup"><span data-stu-id="73624-109">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="73624-110">[MSTest](https://github.com/Microsoft/testfx-docs) je jedna ze tří testovacích rozhraní, ze kterých si můžete vybrat.</span><span class="sxs-lookup"><span data-stu-id="73624-110">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="73624-111">Ostatní jsou [xUnit](https://xunit.net/) a [nUnit](https://nunit.org/).</span><span class="sxs-lookup"><span data-stu-id="73624-111">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="73624-112">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="73624-112">Start Visual Studio.</span></span>

1. <span data-ttu-id="73624-113">Otevřete `ClassLibraryProjects` řešení, které jste vytvořili v části [vytvoření knihovny .NET Standard v aplikaci Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="73624-113">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md).</span></span>

1. <span data-ttu-id="73624-114">Přidejte do řešení nový projekt testování částí s názvem "StringLibraryTest".</span><span class="sxs-lookup"><span data-stu-id="73624-114">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="73624-115">V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat**  >  **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="73624-115">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="73624-116">Na stránce **Přidat nový projekt** zadejte do vyhledávacího pole **MSTest** .</span><span class="sxs-lookup"><span data-stu-id="73624-116">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="73624-117">V seznamu jazyk vyberte **C#** nebo **Visual Basic** a pak vyberte **všechny platformy** ze seznamu platforem.</span><span class="sxs-lookup"><span data-stu-id="73624-117">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="73624-118">Zvolte šablonu **projekt testů MSTest (.NET Core)** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="73624-118">Choose the **MSTest Test Project (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="73624-119">Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **StringLibraryTest** .</span><span class="sxs-lookup"><span data-stu-id="73624-119">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="73624-120">Potom zvolte **Create** (Vytvořit).</span><span class="sxs-lookup"><span data-stu-id="73624-120">Then choose **Create**.</span></span>

1. <span data-ttu-id="73624-121">Visual Studio vytvoří projekt a otevře soubor třídy v okně Code (kód) s následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="73624-121">Visual Studio creates the project and opens the class file in the code window with the following code.</span></span> <span data-ttu-id="73624-122">Pokud jazyk, který chcete použít, není zobrazen, změňte selektor jazyka v horní části stránky.</span><span class="sxs-lookup"><span data-stu-id="73624-122">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

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

   ```vb
   Imports Microsoft.VisualStudio.TestTools.UnitTesting

   Namespace StringLibraryTest
       <TestClass>
       Public Class UnitTest1
           <TestMethod>
           Sub TestSub()

           End Sub
       End Class
   End Namespace
   ```

   <span data-ttu-id="73624-123">Zdrojový kód vytvořený šablonou testu jednotky provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="73624-123">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="73624-124">Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> obor názvů, který obsahuje typy používané pro testování částí.</span><span class="sxs-lookup"><span data-stu-id="73624-124">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="73624-125">Aplikuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atribut na `UnitTest1` třídu.</span><span class="sxs-lookup"><span data-stu-id="73624-125">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="73624-126">Použije <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atribut pro definování `TestMethod1` v jazyce C# nebo `TestSub` v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="73624-126">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic.</span></span>

   <span data-ttu-id="73624-127">Každá metoda označená pomocí [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) v testovací třídě s označením [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) je provedena automaticky při spuštění testu jednotky.</span><span class="sxs-lookup"><span data-stu-id="73624-127">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="73624-128">Přidat odkaz na projekt</span><span class="sxs-lookup"><span data-stu-id="73624-128">Add a project reference</span></span>

<span data-ttu-id="73624-129">Aby projekt testu spolupracoval s `StringLibrary` třídou, přidejte odkaz do projektu **StringLibraryTest** do `StringLibrary` projektu.</span><span class="sxs-lookup"><span data-stu-id="73624-129">For the test project to work with the `StringLibrary` class, add a reference in the **StringLibraryTest** project to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="73624-130">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **závislosti** projektu **StringLibraryTest** a v místní nabídce vyberte **Přidat odkaz na projekt** .</span><span class="sxs-lookup"><span data-stu-id="73624-130">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Project Reference** from the context menu.</span></span>

1. <span data-ttu-id="73624-131">V dialogovém okně **Správce odkazů** rozbalte uzel **projekty** a zaškrtněte políčko vedle položky **StringLibrary**.</span><span class="sxs-lookup"><span data-stu-id="73624-131">In the **Reference Manager** dialog, expand the **Projects** node, and select the box next to **StringLibrary**.</span></span> <span data-ttu-id="73624-132">Přidání odkazu na `StringLibrary` sestavení umožňuje kompilátoru najít metody **StringLibrary** při kompilování projektu **StringLibraryTest** .</span><span class="sxs-lookup"><span data-stu-id="73624-132">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods while compiling the **StringLibraryTest** project.</span></span>

1. <span data-ttu-id="73624-133">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="73624-133">Select **OK**.</span></span>

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="73624-134">Přidat a spustit metody testování částí</span><span class="sxs-lookup"><span data-stu-id="73624-134">Add and run unit test methods</span></span>

<span data-ttu-id="73624-135">Když aplikace Visual Studio spustí test jednotky, provede každou metodu, která je označena <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atributem ve třídě, která je označena <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="73624-135">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="73624-136">Testovací metoda končí při nalezení prvního selhání nebo po úspěšném dokončení všech testů obsažených v metodě.</span><span class="sxs-lookup"><span data-stu-id="73624-136">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="73624-137">Nejběžnější testy volají členy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> třídy.</span><span class="sxs-lookup"><span data-stu-id="73624-137">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="73624-138">Mnoho metod Assert zahrnuje nejméně dva parametry, jeden z nich je očekávaný výsledek testu a druhý z nich je skutečný výsledek testu.</span><span class="sxs-lookup"><span data-stu-id="73624-138">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="73624-139">`Assert`V následující tabulce jsou uvedeny některé často volané metody třídy:</span><span class="sxs-lookup"><span data-stu-id="73624-139">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="73624-140">Metody Assert</span><span class="sxs-lookup"><span data-stu-id="73624-140">Assert methods</span></span>     | <span data-ttu-id="73624-141">Funkce</span><span class="sxs-lookup"><span data-stu-id="73624-141">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="73624-142">Ověřuje, zda jsou dvě hodnoty nebo objekty stejné.</span><span class="sxs-lookup"><span data-stu-id="73624-142">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="73624-143">Vyhodnocení se nezdařila, pokud se hodnoty nebo objekty neshodují.</span><span class="sxs-lookup"><span data-stu-id="73624-143">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="73624-144">Ověřuje, že dvě proměnné objektu odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="73624-144">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="73624-145">Pokud proměnné odkazují na různé objekty, vyhodnocení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="73624-145">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="73624-146">Ověřuje, jestli je podmínka `false` .</span><span class="sxs-lookup"><span data-stu-id="73624-146">Verifies that a condition is `false`.</span></span> <span data-ttu-id="73624-147">Pokud je podmínka, vyhodnocení se nezdařilo `true` .</span><span class="sxs-lookup"><span data-stu-id="73624-147">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="73624-148">Ověřuje, že objekt není `null` .</span><span class="sxs-lookup"><span data-stu-id="73624-148">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="73624-149">Pokud je objekt, vyhodnocení se nezdařilo `null` .</span><span class="sxs-lookup"><span data-stu-id="73624-149">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="73624-150">Můžete také použít <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> metodu v testovací metodě k označení typu výjimky, kterou očekává, že má být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="73624-150">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="73624-151">Test se nezdařil, pokud není vyvolána zadaná výjimka.</span><span class="sxs-lookup"><span data-stu-id="73624-151">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="73624-152">Při testování `StringLibrary.StartsWithUpper` metody je třeba zadat počet řetězců, které začínají velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="73624-152">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="73624-153">Očekáváte, že se metoda vrátí `true` v těchto případech, takže můžete volat <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="73624-153">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="73624-154">Podobně je vhodné zadat počet řetězců, které začínají jinou výjimkou znaku velkého písmene.</span><span class="sxs-lookup"><span data-stu-id="73624-154">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="73624-155">Očekáváte, že se metoda vrátí `false` v těchto případech, takže můžete volat <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="73624-155">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="73624-156">Vzhledem k tomu, že vaše metoda knihovny zpracovává řetězce, je také vhodné se ujistit, že úspěšně zpracovává [prázdný řetězec ( `String.Empty` )](xref:System.String.Empty), platný řetězec, který neobsahuje žádné znaky a jehož <xref:System.String.Length> hodnota je 0, a `null` řetězec, který nebyl inicializován.</span><span class="sxs-lookup"><span data-stu-id="73624-156">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="73624-157">Můžete zavolat `StartsWithUpper` přímo jako statickou metodu a předat jeden <xref:System.String> argument.</span><span class="sxs-lookup"><span data-stu-id="73624-157">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="73624-158">Nebo můžete zavolat `StartsWithUpper` jako metodu rozšíření pro `string` proměnnou přiřazenou k `null` .</span><span class="sxs-lookup"><span data-stu-id="73624-158">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="73624-159">Budete definovat tři metody, z nichž každá volá <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metodu pro každý prvek v poli řetězců.</span><span class="sxs-lookup"><span data-stu-id="73624-159">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="73624-160">Zavoláte přetížení metody, které vám umožní zadat chybovou zprávu, která se zobrazí v případě selhání testu.</span><span class="sxs-lookup"><span data-stu-id="73624-160">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="73624-161">Zpráva identifikuje řetězec, který způsobil chybu.</span><span class="sxs-lookup"><span data-stu-id="73624-161">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="73624-162">Postup vytvoření testovacích metod:</span><span class="sxs-lookup"><span data-stu-id="73624-162">To create the test methods:</span></span>

1. <span data-ttu-id="73624-163">V okně kódu *UnitTest1.cs* nebo *UnitTest1. vb* nahraďte kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="73624-163">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibraryTest/UnitTest1.vb":::

   <span data-ttu-id="73624-164">Test velkých písmen v `TestStartsWithUpper` metodě obsahuje řecké velké písmeno alfa (u + 0391) a velké písmeno cyrilice em (u + 041C).</span><span class="sxs-lookup"><span data-stu-id="73624-164">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="73624-165">Test malých písmen v `TestDoesNotStartWithUpper` metodě obsahuje řecké malé písmeno alfa (U + 03B1) a malé písmeno g (u + 0433).</span><span class="sxs-lookup"><span data-stu-id="73624-165">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="73624-166">Na panelu nabídek vyberte **soubor**  >  **Uložit UnitTest1.cs jako** nebo **soubor**  >  **Uložit UnitTest1. vb jako**.</span><span class="sxs-lookup"><span data-stu-id="73624-166">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="73624-167">V dialogovém okně **Uložit soubor jako** vyberte šipku vedle tlačítka **Uložit** a vyberte **Uložit s kódováním**.</span><span class="sxs-lookup"><span data-stu-id="73624-167">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="73624-168">![Visual Studio uložit soubor jako dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="73624-168">![Visual Studio Save File As dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span></span>

1. <span data-ttu-id="73624-169">Kliknutím na tlačítko **Ano** v dialogovém okně **Potvrdit uložení jako** soubor uložte.</span><span class="sxs-lookup"><span data-stu-id="73624-169">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="73624-170">V dialogovém okně **Upřesnit možnosti uložení** vyberte v rozevíracím seznamu **kódování** znakovou **sadu Unicode (UTF-8 s podpisem 65001)** a vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="73624-170">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="73624-171">![Dialogové okno Upřesnit možnosti uložení v aplikaci Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)</span><span class="sxs-lookup"><span data-stu-id="73624-171">![Visual Studio Advanced Save Options dialog](./media/testing-library-with-visual-studio/advanced-save-options.png)</span></span>

   <span data-ttu-id="73624-172">Pokud neuložíte zdrojový kód jako soubor s kódováním UTF8, Visual Studio ho může uložit jako soubor ASCII.</span><span class="sxs-lookup"><span data-stu-id="73624-172">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="73624-173">Pokud k tomu dojde, modul runtime nebude přesně kódovat znaky UTF8 mimo rozsah ASCII a výsledky testu nebudou správné.</span><span class="sxs-lookup"><span data-stu-id="73624-173">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="73624-174">Na panelu nabídek vyberte možnost **test**  >  **Spustit všechny testy**.</span><span class="sxs-lookup"><span data-stu-id="73624-174">On the menu bar, select **Test** > **Run All Tests**.</span></span> <span data-ttu-id="73624-175">Pokud okno **Průzkumník testů** není otevřené, otevřete ho výběrem **test**  >  **Test Explorer**.</span><span class="sxs-lookup"><span data-stu-id="73624-175">If the **Test Explorer** window doesn't open, open it by choosing **Test** > **Test Explorer**.</span></span> <span data-ttu-id="73624-176">Tři testy jsou uvedeny v části **prošlé testy** a v části **Souhrn** se zobrazí výsledek testovacího běhu.</span><span class="sxs-lookup"><span data-stu-id="73624-176">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="73624-177">![Okno Průzkumníka testů s předáváním testů](./media/testing-library-with-visual-studio/test-explorer-window.png)</span><span class="sxs-lookup"><span data-stu-id="73624-177">![Test Explorer window with passing tests](./media/testing-library-with-visual-studio/test-explorer-window.png)</span></span>

## <a name="handle-test-failures"></a><span data-ttu-id="73624-178">Zpracování selhání testu</span><span class="sxs-lookup"><span data-stu-id="73624-178">Handle test failures</span></span>

<span data-ttu-id="73624-179">Pokud pracujete s vývojem řízeným testováním (TDD), napíšete nejprve testy a při jejich prvním spuštění dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="73624-179">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="73624-180">Potom do aplikace přidáte kód, který provede test úspěšně.</span><span class="sxs-lookup"><span data-stu-id="73624-180">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="73624-181">Pro tento kurz jste vytvořili test po zápisu kódu aplikace, který ověřuje, takže jste neviděli test neúspěšný.</span><span class="sxs-lookup"><span data-stu-id="73624-181">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="73624-182">Chcete-li ověřit, že test selže, pokud očekáváte, že selže, přidejte do vstupu testu neplatnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="73624-182">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="73624-183">Upravte `words` pole v `TestDoesNotStartWithUpper` metodě tak, aby obsahovalo řetězec "Error" (chyba).</span><span class="sxs-lookup"><span data-stu-id="73624-183">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="73624-184">Nemusíte soubor ukládat, protože Visual Studio automaticky ukládá otevřené soubory, když je řešení sestaveno pro spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="73624-184">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="73624-185">Spusťte test výběrem možnosti **test**  >  **Spustit všechny testy** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="73624-185">Run the test by selecting **Test** > **Run All Tests** from the menu bar.</span></span> <span data-ttu-id="73624-186">Okno **Průzkumník testů** indikuje, že dva testy byly úspěšné a jedna se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="73624-186">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="73624-187">![Okno Průzkumníka testů s neúspěšnými testy](./media/testing-library-with-visual-studio/failed-test-window.png)</span><span class="sxs-lookup"><span data-stu-id="73624-187">![Test Explorer window with failing tests](./media/testing-library-with-visual-studio/failed-test-window.png)</span></span>

1. <span data-ttu-id="73624-188">Vyberte neúspěšný test `TestDoesNotStartWith` .</span><span class="sxs-lookup"><span data-stu-id="73624-188">Select the failed test, `TestDoesNotStartWith`.</span></span>

   <span data-ttu-id="73624-189">V okně **Průzkumník testů** se zobrazí zpráva vytvořená kontrolním výrazem: Assert. NEPRAVDA.</span><span class="sxs-lookup"><span data-stu-id="73624-189">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="73624-190">Očekávané pro ' error ': false; skutečnost: true ".</span><span class="sxs-lookup"><span data-stu-id="73624-190">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="73624-191">Z důvodu chyby nejsou v poli Po otestování "Error" žádné řetězce.</span><span class="sxs-lookup"><span data-stu-id="73624-191">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="73624-192">![Okno Průzkumníka testů znázorňující chybu kontrolního výrazu NEPRAVDA](./media/testing-library-with-visual-studio/failed-test-detail.png)</span><span class="sxs-lookup"><span data-stu-id="73624-192">![Test Explorer window showing the IsFalse assertion failure](./media/testing-library-with-visual-studio/failed-test-detail.png)</span></span>

1. <span data-ttu-id="73624-193">Odeberte řetězec "Error", který jste přidali v kroku 1.</span><span class="sxs-lookup"><span data-stu-id="73624-193">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="73624-194">Spusťte test znovu a testy proběhnou znovu.</span><span class="sxs-lookup"><span data-stu-id="73624-194">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="73624-195">Testování verze pro vydání knihovny</span><span class="sxs-lookup"><span data-stu-id="73624-195">Test the Release version of the library</span></span>

<span data-ttu-id="73624-196">Nyní, když testy úspěšně prošly při spuštění sestavení ladění knihovny, spusťte testy dodatečně k sestavení vydání knihovny.</span><span class="sxs-lookup"><span data-stu-id="73624-196">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="73624-197">Několik faktorů, včetně optimalizací kompilátoru, může někdy způsobit různé chování mezi sestaveními ladění a vydání.</span><span class="sxs-lookup"><span data-stu-id="73624-197">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="73624-198">Testování sestavení pro vydání:</span><span class="sxs-lookup"><span data-stu-id="73624-198">To test the Release build:</span></span>

1. <span data-ttu-id="73624-199">Na panelu nástrojů sady Visual Studio změňte konfiguraci sestavení z **ladit** na **release**.</span><span class="sxs-lookup"><span data-stu-id="73624-199">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="73624-200">![Panel nástrojů sady Visual Studio s zvýrazněným sestavením pro vydání](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span><span class="sxs-lookup"><span data-stu-id="73624-200">![Visual Studio toolbar with release build highlighted](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span></span>

1. <span data-ttu-id="73624-201">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **StringLibrary** a vyberte **sestavení** z místní nabídky pro rekompilaci knihovny.</span><span class="sxs-lookup"><span data-stu-id="73624-201">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="73624-202">![Místní nabídka StringLibrary s příkazem Build](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="73624-202">![StringLibrary context menu with build command](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span></span>

1. <span data-ttu-id="73624-203">Spusťte testy jednotek výběrem možnosti **test spustit**  >  **všechny testy** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="73624-203">Run the unit tests by choosing **Test Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="73624-204">Testy jsou passované.</span><span class="sxs-lookup"><span data-stu-id="73624-204">The tests pass.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="73624-205">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="73624-205">Additional resources</span></span>

* [<span data-ttu-id="73624-206">Základy testování částí – Visual Studio</span><span class="sxs-lookup"><span data-stu-id="73624-206">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)
* [<span data-ttu-id="73624-207">Testování částí v .NET Core a .NET Standard</span><span class="sxs-lookup"><span data-stu-id="73624-207">Unit testing in .NET Core and .NET Standard</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="73624-208">Další kroky</span><span class="sxs-lookup"><span data-stu-id="73624-208">Next steps</span></span>

<span data-ttu-id="73624-209">V tomto kurzu testujete jednotku knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="73624-209">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="73624-210">Knihovnu můžete zpřístupnit ostatním tím, že ji publikujete do [NuGet](https://nuget.org) jako balíček.</span><span class="sxs-lookup"><span data-stu-id="73624-210">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="73624-211">Pokud se chcete dozvědět, jak postupovat, postupujte podle kurzu NuGet:</span><span class="sxs-lookup"><span data-stu-id="73624-211">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="73624-212">Vytvoření a publikování balíčku NuGet pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="73624-212">Create and publish a NuGet package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio?tabs=netcore-cli)

<span data-ttu-id="73624-213">Pokud knihovnu publikujete jako balíček NuGet, můžou ji nainstalovat a používat i ostatní.</span><span class="sxs-lookup"><span data-stu-id="73624-213">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="73624-214">Pokud se chcete dozvědět, jak postupovat, postupujte podle kurzu NuGet:</span><span class="sxs-lookup"><span data-stu-id="73624-214">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="73624-215">Instalace a použití balíčku v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="73624-215">Install and use a package in Visual Studio</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

<span data-ttu-id="73624-216">Knihovna nemusí být distribuována jako balíček.</span><span class="sxs-lookup"><span data-stu-id="73624-216">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="73624-217">Dá se seskupit pomocí konzolové aplikace, která ho používá.</span><span class="sxs-lookup"><span data-stu-id="73624-217">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="73624-218">Informace o tom, jak publikovat konzolovou aplikaci, najdete v předchozím kurzu v této sérii:</span><span class="sxs-lookup"><span data-stu-id="73624-218">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="73624-219">Publikování konzolové aplikace .NET Core pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="73624-219">Publish a .NET Core console application with Visual Studio</span></span>](publishing-with-visual-studio.md)

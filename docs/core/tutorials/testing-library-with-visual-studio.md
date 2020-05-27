---
title: Testování .NET Standard knihovny tříd pomocí .NET Core v aplikaci Visual Studio
description: Vytvořte projekt testu jednotek pro knihovnu tříd .NET Core. Ověřte, že vaše knihovna tříd .NET Core pracuje správně s testy jednotek.
ms.date: 05/21/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 79b680022484bb9222b66c3df76bdd5a06de8117
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005008"
---
# <a name="tutorial-test-a-net-standard-library-with-net-core-in-visual-studio"></a><span data-ttu-id="124f0-104">Kurz: testování knihovny .NET Standard pomocí .NET Core v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="124f0-104">Tutorial: Test a .NET Standard library with .NET Core in Visual Studio</span></span>

<span data-ttu-id="124f0-105">V tomto kurzu se dozvíte, jak automatizovat testování částí přidáním testovacího projektu do řešení.</span><span class="sxs-lookup"><span data-stu-id="124f0-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="124f0-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="124f0-106">Prerequisites</span></span>

- <span data-ttu-id="124f0-107">Tento kurz spolupracuje s řešením, které vytvoříte v části [Vytvoření knihovny .NET Standard v sadě Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="124f0-107">This tutorial works with the solution that you create in [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="124f0-108">Vytvoření projektu testování částí</span><span class="sxs-lookup"><span data-stu-id="124f0-108">Create a unit test project</span></span>

1. <span data-ttu-id="124f0-109">Otevřete `ClassLibraryProjects` řešení, které jste vytvořili v části [vytvoření knihovny .NET Standard v aplikaci Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="124f0-109">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md).</span></span>

1. <span data-ttu-id="124f0-110">Přidejte do řešení nový projekt testování částí s názvem "StringLibraryTest".</span><span class="sxs-lookup"><span data-stu-id="124f0-110">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="124f0-111">V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat**  >  **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="124f0-111">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="124f0-112">Na stránce **Přidat nový projekt** zadejte do vyhledávacího pole **MSTest** .</span><span class="sxs-lookup"><span data-stu-id="124f0-112">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="124f0-113">V seznamu jazyk vyberte **C#** nebo **Visual Basic** a pak vyberte **všechny platformy** ze seznamu platforem.</span><span class="sxs-lookup"><span data-stu-id="124f0-113">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="124f0-114">Zvolte šablonu **projekt testů MSTest (.NET Core)** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="124f0-114">Choose the **MSTest Test Project (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="124f0-115">Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **StringLibraryTest** .</span><span class="sxs-lookup"><span data-stu-id="124f0-115">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="124f0-116">Potom zvolte **Create** (Vytvořit).</span><span class="sxs-lookup"><span data-stu-id="124f0-116">Then choose **Create**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="124f0-117">MSTest je jedna ze tří testovacích rozhraní, ze kterých si můžete vybrat.</span><span class="sxs-lookup"><span data-stu-id="124f0-117">MSTest is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="124f0-118">Ostatní jsou xUnit a nUnit.</span><span class="sxs-lookup"><span data-stu-id="124f0-118">The others are xUnit and nUnit.</span></span>

1. <span data-ttu-id="124f0-119">Visual Studio vytvoří projekt a otevře soubor třídy v okně Code (kód) s následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="124f0-119">Visual Studio creates the project and opens the class file in the code window with the following code.</span></span> <span data-ttu-id="124f0-120">Pokud jazyk, který chcete použít, není zobrazen, změňte selektor jazyka v horní části stránky.</span><span class="sxs-lookup"><span data-stu-id="124f0-120">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

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

   <span data-ttu-id="124f0-121">Zdrojový kód vytvořený šablonou testu jednotky provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="124f0-121">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="124f0-122">Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> obor názvů, který obsahuje typy používané pro testování částí.</span><span class="sxs-lookup"><span data-stu-id="124f0-122">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="124f0-123">Aplikuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atribut na `UnitTest1` třídu.</span><span class="sxs-lookup"><span data-stu-id="124f0-123">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="124f0-124">Použije <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atribut pro definování `TestMethod1` v jazyce C# nebo `TestSub` v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="124f0-124">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic.</span></span>

   <span data-ttu-id="124f0-125">Každá metoda označená pomocí [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) v testovací třídě s označením [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) je provedena automaticky při spuštění testu jednotky.</span><span class="sxs-lookup"><span data-stu-id="124f0-125">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

1. <span data-ttu-id="124f0-126">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **závislosti** projektu **StringLibraryTest** a v místní nabídce vyberte **Přidat odkaz na projekt** .</span><span class="sxs-lookup"><span data-stu-id="124f0-126">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Project Reference** from the context menu.</span></span>

1. <span data-ttu-id="124f0-127">V dialogovém okně **Správce odkazů** rozbalte uzel **projekty** a zaškrtněte políčko vedle položky **StringLibrary**.</span><span class="sxs-lookup"><span data-stu-id="124f0-127">In the **Reference Manager** dialog, expand the **Projects** node, and select the box next to **StringLibrary**.</span></span> <span data-ttu-id="124f0-128">Přidání odkazu na `StringLibrary` sestavení umožňuje kompilátoru najít metody **StringLibrary** při kompilování projektu **StringLibraryTest** .</span><span class="sxs-lookup"><span data-stu-id="124f0-128">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods while compiling the **StringLibraryTest** project.</span></span>

1. <span data-ttu-id="124f0-129">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="124f0-129">Select **OK**.</span></span>

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="124f0-130">Přidat a spustit metody testování částí</span><span class="sxs-lookup"><span data-stu-id="124f0-130">Add and run unit test methods</span></span>

<span data-ttu-id="124f0-131">Když aplikace Visual Studio spustí test jednotky, provede každou metodu, která je označena <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atributem ve třídě, která je označena <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="124f0-131">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="124f0-132">Testovací metoda končí při nalezení prvního selhání nebo po úspěšném dokončení všech testů obsažených v metodě.</span><span class="sxs-lookup"><span data-stu-id="124f0-132">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="124f0-133">Nejběžnější testy volají členy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> třídy.</span><span class="sxs-lookup"><span data-stu-id="124f0-133">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="124f0-134">Mnoho metod Assert zahrnuje nejméně dva parametry, jeden z nich je očekávaný výsledek testu a druhý z nich je skutečný výsledek testu.</span><span class="sxs-lookup"><span data-stu-id="124f0-134">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="124f0-135">`Assert`V následující tabulce jsou uvedeny některé často volané metody třídy:</span><span class="sxs-lookup"><span data-stu-id="124f0-135">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="124f0-136">Metody Assert</span><span class="sxs-lookup"><span data-stu-id="124f0-136">Assert methods</span></span>     | <span data-ttu-id="124f0-137">Funkce</span><span class="sxs-lookup"><span data-stu-id="124f0-137">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="124f0-138">Ověřuje, zda jsou dvě hodnoty nebo objekty stejné.</span><span class="sxs-lookup"><span data-stu-id="124f0-138">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="124f0-139">Vyhodnocení se nezdařila, pokud se hodnoty nebo objekty neshodují.</span><span class="sxs-lookup"><span data-stu-id="124f0-139">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="124f0-140">Ověřuje, že dvě proměnné objektu odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="124f0-140">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="124f0-141">Pokud proměnné odkazují na různé objekty, vyhodnocení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="124f0-141">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="124f0-142">Ověřuje, jestli je podmínka `false` .</span><span class="sxs-lookup"><span data-stu-id="124f0-142">Verifies that a condition is `false`.</span></span> <span data-ttu-id="124f0-143">Pokud je podmínka, vyhodnocení se nezdařilo `true` .</span><span class="sxs-lookup"><span data-stu-id="124f0-143">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="124f0-144">Ověřuje, že objekt není `null` .</span><span class="sxs-lookup"><span data-stu-id="124f0-144">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="124f0-145">Pokud je objekt, vyhodnocení se nezdařilo `null` .</span><span class="sxs-lookup"><span data-stu-id="124f0-145">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="124f0-146">Můžete také použít <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> metodu v testovací metodě k označení typu výjimky, kterou očekává, že má být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="124f0-146">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="124f0-147">Test se nezdařil, pokud není vyvolána zadaná výjimka.</span><span class="sxs-lookup"><span data-stu-id="124f0-147">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="124f0-148">Při testování `StringLibrary.StartsWithUpper` metody je třeba zadat počet řetězců, které začínají velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="124f0-148">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="124f0-149">Očekáváte, že se metoda vrátí `true` v těchto případech, takže můžete volat <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="124f0-149">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="124f0-150">Podobně je vhodné zadat počet řetězců, které začínají jinou výjimkou znaku velkého písmene.</span><span class="sxs-lookup"><span data-stu-id="124f0-150">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="124f0-151">Očekáváte, že se metoda vrátí `false` v těchto případech, takže můžete volat <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="124f0-151">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="124f0-152">Vzhledem k tomu, že vaše metoda knihovny zpracovává řetězce, je také vhodné se ujistit, že úspěšně zpracovává [prázdný řetězec ( `String.Empty` )](xref:System.String.Empty), platný řetězec, který neobsahuje žádné znaky a jehož <xref:System.String.Length> hodnota je 0, a `null` řetězec, který nebyl inicializován.</span><span class="sxs-lookup"><span data-stu-id="124f0-152">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="124f0-153">Pokud `StartsWithUpper` je volána jako metoda rozšíření v <xref:System.String> instanci, nelze předat `null` řetězec.</span><span class="sxs-lookup"><span data-stu-id="124f0-153">If `StartsWithUpper` is called as an extension method on a <xref:System.String> instance, it can't be passed a `null` string.</span></span> <span data-ttu-id="124f0-154">Můžete ji však také volat přímo jako statickou metodu a předat jeden <xref:System.String> argument.</span><span class="sxs-lookup"><span data-stu-id="124f0-154">However, you can also call it directly as a static method and pass a single <xref:System.String> argument.</span></span>

<span data-ttu-id="124f0-155">Budete definovat tři metody, z nichž každá volá <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metodu opakovaně pro každý prvek v poli řetězců.</span><span class="sxs-lookup"><span data-stu-id="124f0-155">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="124f0-156">Vzhledem k tomu, že testovací metoda selže, jakmile najde první selhání, zavoláte přetížení metody, které vám umožní předat řetězec, který označuje hodnotu řetězce použitou ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="124f0-156">Because the test method fails as soon as it finds the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="124f0-157">Postup vytvoření testovacích metod:</span><span class="sxs-lookup"><span data-stu-id="124f0-157">To create the test methods:</span></span>

1. <span data-ttu-id="124f0-158">V okně kódu *UnitTest1.cs* nebo *UnitTest1. vb* nahraďte kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="124f0-158">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   <span data-ttu-id="124f0-159">Test velkých písmen v `TestStartsWithUpper` metodě obsahuje řecké velké písmeno alfa (u + 0391) a velké písmeno cyrilice em (u + 041C).</span><span class="sxs-lookup"><span data-stu-id="124f0-159">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="124f0-160">Test malých písmen v `TestDoesNotStartWithUpper` metodě obsahuje řecké malé písmeno alfa (U + 03B1) a malé písmeno g (u + 0433).</span><span class="sxs-lookup"><span data-stu-id="124f0-160">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="124f0-161">Na panelu nabídek vyberte **soubor**  >  **Uložit UnitTest1.cs jako** nebo **soubor**  >  **Uložit UnitTest1. vb jako**.</span><span class="sxs-lookup"><span data-stu-id="124f0-161">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="124f0-162">V dialogovém okně **Uložit soubor jako** vyberte šipku vedle tlačítka **Uložit** a vyberte **Uložit s kódováním**.</span><span class="sxs-lookup"><span data-stu-id="124f0-162">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="124f0-163">![Visual Studio uložit soubor jako dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="124f0-163">![Visual Studio Save File As dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span></span>

1. <span data-ttu-id="124f0-164">Kliknutím na tlačítko **Ano** v dialogovém okně **Potvrdit uložení jako** soubor uložte.</span><span class="sxs-lookup"><span data-stu-id="124f0-164">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="124f0-165">V dialogovém okně **Upřesnit možnosti uložení** vyberte v rozevíracím seznamu **kódování** znakovou **sadu Unicode (UTF-8 s podpisem 65001)** a vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="124f0-165">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="124f0-166">![Dialogové okno Upřesnit možnosti uložení v aplikaci Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)</span><span class="sxs-lookup"><span data-stu-id="124f0-166">![Visual Studio Advanced Save Options dialog](./media/testing-library-with-visual-studio/advanced-save-options.png)</span></span>

   <span data-ttu-id="124f0-167">Pokud neuložíte zdrojový kód jako soubor s kódováním UTF8, Visual Studio ho může uložit jako soubor ASCII.</span><span class="sxs-lookup"><span data-stu-id="124f0-167">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="124f0-168">Pokud k tomu dojde, modul runtime nebude přesně kódovat znaky UTF8 mimo rozsah ASCII a výsledky testu nebudou správné.</span><span class="sxs-lookup"><span data-stu-id="124f0-168">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="124f0-169">Na panelu nabídek vyberte možnost **test**  >  **Spustit všechny testy**.</span><span class="sxs-lookup"><span data-stu-id="124f0-169">On the menu bar, select **Test** > **Run All Tests**.</span></span> <span data-ttu-id="124f0-170">Pokud okno **Průzkumník testů** není otevřené, otevřete ho výběrem **test**  >  **Test Explorer**.</span><span class="sxs-lookup"><span data-stu-id="124f0-170">If the **Test Explorer** window doesn't open, open it by choosing **Test** > **Test Explorer**.</span></span> <span data-ttu-id="124f0-171">Tři testy jsou uvedeny v části **prošlé testy** a v části **Souhrn** se zobrazí výsledek testovacího běhu.</span><span class="sxs-lookup"><span data-stu-id="124f0-171">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="124f0-172">![Okno Průzkumníka testů s předáváním testů](./media/testing-library-with-visual-studio/test-explorer-window.png)</span><span class="sxs-lookup"><span data-stu-id="124f0-172">![Test Explorer window with passing tests](./media/testing-library-with-visual-studio/test-explorer-window.png)</span></span>

## <a name="handle-test-failures"></a><span data-ttu-id="124f0-173">Zpracování selhání testu</span><span class="sxs-lookup"><span data-stu-id="124f0-173">Handle test failures</span></span>

<span data-ttu-id="124f0-174">V testovacím běhu došlo k žádným chybám, ale mírně ho změňte, aby jedna z testovacích metod nebyla úspěšná:</span><span class="sxs-lookup"><span data-stu-id="124f0-174">Your test run had no failures, but change it slightly so that one of the test methods fails:</span></span>

1. <span data-ttu-id="124f0-175">Upravte `words` pole v `TestDoesNotStartWithUpper` metodě tak, aby obsahovalo řetězec "Error" (chyba).</span><span class="sxs-lookup"><span data-stu-id="124f0-175">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="124f0-176">Nemusíte soubor ukládat, protože Visual Studio automaticky ukládá otevřené soubory, když je řešení sestaveno pro spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="124f0-176">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="124f0-177">Spusťte test výběrem možnosti **test**  >  **Spustit všechny testy** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="124f0-177">Run the test by selecting **Test** > **Run All Tests** from the menu bar.</span></span> <span data-ttu-id="124f0-178">Okno **Průzkumník testů** indikuje, že dva testy byly úspěšné a jedna se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="124f0-178">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="124f0-179">![Okno Průzkumníka testů s neúspěšnými testy](./media/testing-library-with-visual-studio/failed-test-window.png)</span><span class="sxs-lookup"><span data-stu-id="124f0-179">![Test Explorer window with failing tests](./media/testing-library-with-visual-studio/failed-test-window.png)</span></span>

1. <span data-ttu-id="124f0-180">Vyberte neúspěšný test `TestDoesNotStartWith` .</span><span class="sxs-lookup"><span data-stu-id="124f0-180">Select the failed test, `TestDoesNotStartWith`.</span></span> <span data-ttu-id="124f0-181">V okně **Průzkumník testů** se zobrazí zpráva vytvořená kontrolním výrazem: Assert. NEPRAVDA.</span><span class="sxs-lookup"><span data-stu-id="124f0-181">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="124f0-182">Očekávané pro ' error ': false; skutečnost: true ".</span><span class="sxs-lookup"><span data-stu-id="124f0-182">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="124f0-183">Z důvodu chyby nebyly testovány všechny řetězce v poli po "Error".</span><span class="sxs-lookup"><span data-stu-id="124f0-183">Because of the failure, all strings in the array after "Error" weren't tested.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="124f0-184">![Okno Průzkumníka testů znázorňující chybu kontrolního výrazu NEPRAVDA](./media/testing-library-with-visual-studio/failed-test-detail.png)</span><span class="sxs-lookup"><span data-stu-id="124f0-184">![Test Explorer window showing the IsFalse assertion failure](./media/testing-library-with-visual-studio/failed-test-detail.png)</span></span>

1. <span data-ttu-id="124f0-185">Vraťte změny, které jste provedli v kroku 1, a odeberte řetězec "Error" (chyba).</span><span class="sxs-lookup"><span data-stu-id="124f0-185">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="124f0-186">Spusťte test znovu a testy proběhnou znovu.</span><span class="sxs-lookup"><span data-stu-id="124f0-186">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="124f0-187">Testování verze pro vydání knihovny</span><span class="sxs-lookup"><span data-stu-id="124f0-187">Test the Release version of the library</span></span>

<span data-ttu-id="124f0-188">Nyní, když testy prošly všechny při spuštění ladicí verze knihovny, spusťte testy dodatečně k sestavení vydání knihovny.</span><span class="sxs-lookup"><span data-stu-id="124f0-188">Now that the tests have all passed when running the Debug version of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="124f0-189">Několik faktorů, včetně optimalizací kompilátoru, může někdy způsobit různé chování mezi sestaveními ladění a vydání.</span><span class="sxs-lookup"><span data-stu-id="124f0-189">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="124f0-190">Testování sestavení pro vydání:</span><span class="sxs-lookup"><span data-stu-id="124f0-190">To test the Release build:</span></span>

1. <span data-ttu-id="124f0-191">Na panelu nástrojů sady Visual Studio změňte konfiguraci sestavení z **ladit** na **release**.</span><span class="sxs-lookup"><span data-stu-id="124f0-191">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="124f0-192">![Panel nástrojů sady Visual Studio s zvýrazněným sestavením pro vydání](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span><span class="sxs-lookup"><span data-stu-id="124f0-192">![Visual Studio toolbar with release build highlighted](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span></span>

1. <span data-ttu-id="124f0-193">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **StringLibrary** a vyberte **sestavení** z místní nabídky pro rekompilaci knihovny.</span><span class="sxs-lookup"><span data-stu-id="124f0-193">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="124f0-194">![Místní nabídka StringLibrary s příkazem Build](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="124f0-194">![StringLibrary context menu with build command](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span></span>

1. <span data-ttu-id="124f0-195">Spusťte testy jednotek výběrem možnosti **test spustit**  >  **všechny testy** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="124f0-195">Run the unit tests by choosing **Test Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="124f0-196">Testy jsou passované.</span><span class="sxs-lookup"><span data-stu-id="124f0-196">The tests pass.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="124f0-197">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="124f0-197">Additional resources</span></span>

- [<span data-ttu-id="124f0-198">Základy testování částí – Visual Studio</span><span class="sxs-lookup"><span data-stu-id="124f0-198">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)

## <a name="next-steps"></a><span data-ttu-id="124f0-199">Další kroky</span><span class="sxs-lookup"><span data-stu-id="124f0-199">Next steps</span></span>

<span data-ttu-id="124f0-200">V tomto kurzu testujete jednotku knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="124f0-200">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="124f0-201">Knihovnu můžete zpřístupnit ostatním tím, že ji publikujete do [NuGet](https://nuget.org) jako balíček.</span><span class="sxs-lookup"><span data-stu-id="124f0-201">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="124f0-202">Pokud se chcete dozvědět, jak postupovat, postupujte podle kurzu NuGet:</span><span class="sxs-lookup"><span data-stu-id="124f0-202">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="124f0-203">Vytvoření a publikování balíčku NuGet pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="124f0-203">Create and publish a NuGet package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio?tabs=netcore-cli)

<span data-ttu-id="124f0-204">Pokud knihovnu publikujete jako balíček NuGet, můžou ji nainstalovat a používat i ostatní.</span><span class="sxs-lookup"><span data-stu-id="124f0-204">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="124f0-205">Pokud se chcete dozvědět, jak postupovat, postupujte podle kurzu NuGet:</span><span class="sxs-lookup"><span data-stu-id="124f0-205">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="124f0-206">Instalace a použití balíčku v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="124f0-206">Install and use a package in Visual Studio</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

<span data-ttu-id="124f0-207">Knihovna nemusí být distribuována jako balíček.</span><span class="sxs-lookup"><span data-stu-id="124f0-207">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="124f0-208">Dá se seskupit pomocí konzolové aplikace, která ho používá.</span><span class="sxs-lookup"><span data-stu-id="124f0-208">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="124f0-209">Informace o tom, jak publikovat konzolovou aplikaci, najdete v předchozím kurzu v této sérii:</span><span class="sxs-lookup"><span data-stu-id="124f0-209">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="124f0-210">Publikování konzolové aplikace .NET Core pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="124f0-210">Publish a .NET Core console application with Visual Studio</span></span>](publishing-with-visual-studio.md)

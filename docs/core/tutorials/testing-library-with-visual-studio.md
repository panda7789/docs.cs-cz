---
title: Testování knihovny tříd .NET Standard s jádrem .NET v sadě Visual Studio
description: Vytvořte projekt testování částí pro knihovnu tříd .NET Core. Ověřte, zda knihovna tříd .NET Core funguje správně s testy částí.
ms.date: 12/24/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 307261088f5c7c69c0e69fbd6b99940c04842eec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156618"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a><span data-ttu-id="194f1-104">Testování knihovny .NET Standard s jádrem .NET v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="194f1-104">Test a .NET Standard library with .NET Core in Visual Studio</span></span>

<span data-ttu-id="194f1-105">V [části Sestavení knihovny .NET Standard v sadě Visual Studio](library-with-visual-studio.md)jste <xref:System.String> vytvořili jednoduchou knihovnu tříd, která do třídy přidá metodu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="194f1-105">In [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md), you created a simple class library that adds an extension method to the <xref:System.String> class.</span></span> <span data-ttu-id="194f1-106">Nyní vytvoříte test částí a ujistěte se, že funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="194f1-106">Now, you'll create a unit test to make sure that it works as expected.</span></span> <span data-ttu-id="194f1-107">Přidáte projekt testování částí do řešení, které jste vytvořili v předchozím článku.</span><span class="sxs-lookup"><span data-stu-id="194f1-107">You'll add your unit test project to the solution you created in the previous article.</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="194f1-108">Vytvoření projektu testování částí</span><span class="sxs-lookup"><span data-stu-id="194f1-108">Create a unit test project</span></span>

<span data-ttu-id="194f1-109">Chcete-li vytvořit projekt testování částí, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="194f1-109">To create the unit test project, do the following:</span></span>

1. <span data-ttu-id="194f1-110">Otevřete `ClassLibraryProjects` řešení, které jste vytvořili v článku [Sestavení a standardní knihovny .NET v sadě Visual Studio.](library-with-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="194f1-110">Open the `ClassLibraryProjects` solution you created in the [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md) article.</span></span>

1. <span data-ttu-id="194f1-111">Přidejte do řešení nový projekt testování částí s názvem "StringLibraryTest".</span><span class="sxs-lookup"><span data-stu-id="194f1-111">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="194f1-112">Klikněte pravým tlačítkem myši na řešení v **Průzkumníku řešení** a vyberte **Přidat** > **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="194f1-112">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="194f1-113">Na stránce **Přidat nový projekt** zadejte do vyhledávacího pole **mstest.**</span><span class="sxs-lookup"><span data-stu-id="194f1-113">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="194f1-114">V seznamu Jazyk zvolte **C#** nebo **Visual Basic** a pak ze seznamu Platforma zvolte **Všechny platformy.**</span><span class="sxs-lookup"><span data-stu-id="194f1-114">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="194f1-115">Zvolte šablonu **Testovací projekt MsTest (.NET Core)** a pak zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="194f1-115">Choose the **MsTest Test Project (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="194f1-116">Na stránce **Konfigurovat nový projekt** zadejte **StringLibraryTest** do pole **Název projektu.**</span><span class="sxs-lookup"><span data-stu-id="194f1-116">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="194f1-117">Potom zvolte **Create** (Vytvořit).</span><span class="sxs-lookup"><span data-stu-id="194f1-117">Then choose **Create**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="194f1-118">Kromě MSTest, můžete také vytvořit xUnit a nUnit testovací projekty pro .NET Core v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="194f1-118">In addition to an MSTest, you can also create xUnit and nUnit test projects for .NET Core in Visual Studio.</span></span>

1. <span data-ttu-id="194f1-119">Visual Studio vytvoří projekt a otevře soubor třídy v okně kódu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="194f1-119">Visual Studio creates the project and opens the class file in the code window with the following code:</span></span>

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

   <span data-ttu-id="194f1-120">Zdrojový kód vytvořený šablonou testování částí provádí následující akce:</span><span class="sxs-lookup"><span data-stu-id="194f1-120">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="194f1-121">Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> obor názvů, který obsahuje typy používané pro testování částí.</span><span class="sxs-lookup"><span data-stu-id="194f1-121">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>

   - <span data-ttu-id="194f1-122">Použije [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) atribut třídy. `UnitTest1`</span><span class="sxs-lookup"><span data-stu-id="194f1-122">It applies the [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) attribute to the `UnitTest1` class.</span></span> <span data-ttu-id="194f1-123">Každá testovací metoda v testovací třídě označená atributem [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) je automaticky provedena při spuštění testu jednotky.</span><span class="sxs-lookup"><span data-stu-id="194f1-123">Each test method in a test class tagged with the [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) attribute is executed automatically when the unit test is run.</span></span>

   - <span data-ttu-id="194f1-124">Použije [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) atribut definovat `TestMethod1` v jazyce `TestSub` C# nebo v jazyce Visual Basic jako testovací metoda pro automatické spuštění při spuštění testu jednotky.</span><span class="sxs-lookup"><span data-stu-id="194f1-124">It applies the [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic as a test method for automatic execution when the unit test is run.</span></span>

1. <span data-ttu-id="194f1-125">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel **Závislosti** projektu **StringLibraryTest** a z kontextové nabídky vyberte **přidat odkaz.**</span><span class="sxs-lookup"><span data-stu-id="194f1-125">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Reference** from the context menu.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="194f1-126">![Místní nabídka závislostí StringLibraryTest](./media/testing-library-with-visual-studio/add-reference-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="194f1-126">![Context menu of StringLibraryTest dependencies](./media/testing-library-with-visual-studio/add-reference-context-menu.png)</span></span>

1. <span data-ttu-id="194f1-127">V dialogovém okně **Správce odkazů** rozbalte uzel **Projekty** a zaškrtněte políčko vedle **položky StringLibrary**.</span><span class="sxs-lookup"><span data-stu-id="194f1-127">In the **Reference Manager** dialog, expand the **Projects** node and check the box next to **StringLibrary**.</span></span> <span data-ttu-id="194f1-128">Přidání odkazu na `StringLibrary` sestavení umožňuje kompilátoru najít metody **StringLibrary.**</span><span class="sxs-lookup"><span data-stu-id="194f1-128">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods.</span></span> <span data-ttu-id="194f1-129">Vyberte tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="194f1-129">Select the **OK** button.</span></span> <span data-ttu-id="194f1-130">Do projektu knihovny tříd je `StringLibrary`přidán odkaz .</span><span class="sxs-lookup"><span data-stu-id="194f1-130">A reference is added to your class library project, `StringLibrary`.</span></span>

   ![Dialogové okno Správce odkazů v sadě Visual Studio](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="194f1-132">Přidání a spuštění testovacích metod jednotek</span><span class="sxs-lookup"><span data-stu-id="194f1-132">Add and run unit test methods</span></span>

<span data-ttu-id="194f1-133">Při spuštění testu částí Visual Studio provede každou metodu, která je označena <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atributem <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> ve třídě testování částí, třídy, na které je atribut použit.</span><span class="sxs-lookup"><span data-stu-id="194f1-133">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a unit test class, the class to which the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute is applied.</span></span> <span data-ttu-id="194f1-134">Testovací metoda končí, když je nalezena první selhání nebo všechny testy obsažené v metodě byly úspěšné.</span><span class="sxs-lookup"><span data-stu-id="194f1-134">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="194f1-135">Nejběžnější testy volání členů <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> třídy.</span><span class="sxs-lookup"><span data-stu-id="194f1-135">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="194f1-136">Mnoho metod assert zahrnuje alespoň dva parametry, z nichž jeden je očekávaný výsledek testu a druhý je skutečný výsledek testu.</span><span class="sxs-lookup"><span data-stu-id="194f1-136">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="194f1-137">Některé z `Assert` nejčastěji nazývaných metod třídy jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="194f1-137">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="194f1-138">Metody uplatnění</span><span class="sxs-lookup"><span data-stu-id="194f1-138">Assert methods</span></span>     | <span data-ttu-id="194f1-139">Funkce</span><span class="sxs-lookup"><span data-stu-id="194f1-139">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="194f1-140">Ověří, že dvě hodnoty nebo objekty jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="194f1-140">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="194f1-141">Vyhodnocení se nezdaří, pokud hodnoty nebo objekty nejsou stejné.</span><span class="sxs-lookup"><span data-stu-id="194f1-141">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="194f1-142">Ověří, že dvě proměnné objektu odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="194f1-142">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="194f1-143">Assert se nezdaří, pokud proměnné odkazují na různé objekty.</span><span class="sxs-lookup"><span data-stu-id="194f1-143">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="194f1-144">Ověří, zda je `false`podmínka .</span><span class="sxs-lookup"><span data-stu-id="194f1-144">Verifies that a condition is `false`.</span></span> <span data-ttu-id="194f1-145">Nepodmíněný výraz se `true`nezdaří, pokud je podmínka .</span><span class="sxs-lookup"><span data-stu-id="194f1-145">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="194f1-146">Ověří, zda objekt není `null`.</span><span class="sxs-lookup"><span data-stu-id="194f1-146">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="194f1-147">Assert se nezdaří, `null`pokud je objekt .</span><span class="sxs-lookup"><span data-stu-id="194f1-147">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="194f1-148">Metodu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> můžete také použít v testovací metodě k označení typu výjimky, kterou se očekává vyvolání.</span><span class="sxs-lookup"><span data-stu-id="194f1-148">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="194f1-149">Test se nezdaří, pokud není vyvolána zadaná výjimka.</span><span class="sxs-lookup"><span data-stu-id="194f1-149">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="194f1-150">Při testování `StringLibrary.StartsWithUpper` metody chcete poskytnout počet řetězců, které začínají velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="194f1-150">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="194f1-151">Očekáváte, že `true` metoda vrátit v těchto případech, takže můžete volat metodu. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A></span><span class="sxs-lookup"><span data-stu-id="194f1-151">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> method.</span></span> <span data-ttu-id="194f1-152">Podobně chcete poskytnout počet řetězců, které začínají něčím jiným než velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="194f1-152">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="194f1-153">Očekáváte, že `false` metoda vrátit v těchto případech, takže můžete volat metodu. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A></span><span class="sxs-lookup"><span data-stu-id="194f1-153">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> method.</span></span>

<span data-ttu-id="194f1-154">Vzhledem k tomu, že metoda knihovny zpracovává řetězce, chcete se také ujistit, že úspěšně zpracovává [prázdný řetězec (`String.Empty`)](xref:System.String.Empty), platný řetězec, který nemá žádné znaky a jehož <xref:System.String.Length> je 0 a `null` řetězec, který nebyl inicializován.</span><span class="sxs-lookup"><span data-stu-id="194f1-154">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="194f1-155">Pokud `StartsWithUpper` je volána jako <xref:System.String> metoda rozšíření na instanci, nelze předat `null` řetězec.</span><span class="sxs-lookup"><span data-stu-id="194f1-155">If `StartsWithUpper` is called as an extension method on a <xref:System.String> instance, it can't be passed a `null` string.</span></span> <span data-ttu-id="194f1-156">Můžete jej však také volat přímo jako statickou metodu a předat jeden <xref:System.String> argument.</span><span class="sxs-lookup"><span data-stu-id="194f1-156">However, you can also call it directly as a static method and pass a single <xref:System.String> argument.</span></span>

<span data-ttu-id="194f1-157">Definujete tři metody, z nichž <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> každá volá metodu opakovaně pro každý prvek v řetězcovém poli.</span><span class="sxs-lookup"><span data-stu-id="194f1-157">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="194f1-158">Vzhledem k tomu, že testovací metoda selže, jakmile najde první selhání, zavoláte přetížení metody, která umožňuje předat řetězec, který označuje hodnotu řetězce použitou ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="194f1-158">Because the test method fails as soon as it finds the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="194f1-159">Chcete-li vytvořit zkušební metody:</span><span class="sxs-lookup"><span data-stu-id="194f1-159">To create the test methods:</span></span>

1. <span data-ttu-id="194f1-160">V okně kódu *UnitTest1.cs* nebo *UnitTest1.vb* nahraďte kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="194f1-160">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   <span data-ttu-id="194f1-161">Test velkých písmen v `TestStartsWithUpper` metodě zahrnuje řecké velké písmeno alfa (U + 0391) a velké písmeno cyrilice EM (U + 041C).</span><span class="sxs-lookup"><span data-stu-id="194f1-161">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="194f1-162">Test malých písmen v `TestDoesNotStartWithUpper` metodě zahrnuje řecké malé písmeno alfa (U + 03B1) a cyrilice malé písmeno ghe (U + 0433).</span><span class="sxs-lookup"><span data-stu-id="194f1-162">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="194f1-163">Na řádku nabídek vyberte **Soubor** > **Uložit UnitTest1.cs jako** nebo **Soubor** > **Uložit UnitTest1.vb jako**.</span><span class="sxs-lookup"><span data-stu-id="194f1-163">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="194f1-164">V dialogovém okně **Uložit soubor jako** vyberte šipku vedle tlačítka **Uložit** a vyberte Uložit **pomocí kódování**.</span><span class="sxs-lookup"><span data-stu-id="194f1-164">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="194f1-165">![Dialogové okno Uložit soubor jako v sadě Visual Studio](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="194f1-165">![Visual Studio Save File As dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span></span>

1. <span data-ttu-id="194f1-166">V dialogovém okně **Potvrdit uložení jako** vyberte tlačítko **Ano** pro uložení souboru.</span><span class="sxs-lookup"><span data-stu-id="194f1-166">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="194f1-167">V dialogovém okně **Upřesnit možnosti uložení** vyberte v rozevíracím seznamu **Kódování** **položku Unicode (UTF-8 s podpisem) – znaková stránka 65001** a vyberte **ok**.</span><span class="sxs-lookup"><span data-stu-id="194f1-167">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="194f1-168">![Dialogové okno Upřesnit možnosti ukládání sady Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)</span><span class="sxs-lookup"><span data-stu-id="194f1-168">![Visual Studio Advanced Save Options dialog](./media/testing-library-with-visual-studio/advanced-save-options.png)</span></span>

   <span data-ttu-id="194f1-169">Pokud se vám nepodaří uložit zdrojový kód jako soubor kódovaný UTF8, Visual Studio jej může uložit jako soubor ASCII.</span><span class="sxs-lookup"><span data-stu-id="194f1-169">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="194f1-170">Když se to stane, runtime není přesně dekódovat znaky UTF8 mimo rozsah ASCII a výsledky testu nebude správné.</span><span class="sxs-lookup"><span data-stu-id="194f1-170">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="194f1-171">Na řádku nabídek vyberte **Testovat** > **spustit** > **všechny testy**.</span><span class="sxs-lookup"><span data-stu-id="194f1-171">On the menu bar, select **Test** > **Run** > **All Tests**.</span></span> <span data-ttu-id="194f1-172">Otevře se okno **Průzkumníka testů** a zobrazí se, že testy byly úspěšně spuštěny.</span><span class="sxs-lookup"><span data-stu-id="194f1-172">The **Test Explorer** window opens and shows that the tests ran successfully.</span></span> <span data-ttu-id="194f1-173">Tři testy jsou uvedeny v části **Předané testy** a **část Souhrn** hlásí výsledek testu.</span><span class="sxs-lookup"><span data-stu-id="194f1-173">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="194f1-174">![Okno Průzkumníka testů s absolvováním testů](./media/testing-library-with-visual-studio/test-explorer-window.png)</span><span class="sxs-lookup"><span data-stu-id="194f1-174">![Test Explorer window with passing tests](./media/testing-library-with-visual-studio/test-explorer-window.png)</span></span>

## <a name="handle-test-failures"></a><span data-ttu-id="194f1-175">Zpracování selhání testu</span><span class="sxs-lookup"><span data-stu-id="194f1-175">Handle test failures</span></span>

<span data-ttu-id="194f1-176">Spuštění testu nemělo žádné chyby, ale mírně jej změňte tak, aby jedna z testovacích metod selhala:</span><span class="sxs-lookup"><span data-stu-id="194f1-176">Your test run had no failures, but change it slightly so that one of the test methods fails:</span></span>

1. <span data-ttu-id="194f1-177">Upravte `words` pole `TestDoesNotStartWithUpper` v metodě tak, aby obsahovalo řetězec "Chyba".</span><span class="sxs-lookup"><span data-stu-id="194f1-177">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="194f1-178">Soubor není nutné ukládat, protože visual studio automaticky ukládá otevřené soubory, když je řešení vytvořeno pro spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="194f1-178">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="194f1-179">Spusťte test výběrem **možnosti** > **Spustit** > všechny**testy** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="194f1-179">Run the test by selecting **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="194f1-180">Okno **Průzkumník testů** označuje, že dva testy byly úspěšné a jeden neúspěšný.</span><span class="sxs-lookup"><span data-stu-id="194f1-180">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="194f1-181">![Okno Průzkumníka testů s neúspěšnými testy](./media/testing-library-with-visual-studio/failed-test-window.png)</span><span class="sxs-lookup"><span data-stu-id="194f1-181">![Test Explorer window with failing tests](./media/testing-library-with-visual-studio/failed-test-window.png)</span></span>

1. <span data-ttu-id="194f1-182">Vyberte neúspěšný `TestDoesNotStartWith`test .</span><span class="sxs-lookup"><span data-stu-id="194f1-182">Select the failed test, `TestDoesNotStartWith`.</span></span> <span data-ttu-id="194f1-183">Okno **Průzkumník testů** zobrazí zprávu vytvořenou assert: "Assert.IsFalse se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="194f1-183">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="194f1-184">Očekáváno pro 'Chyba': false; aktuální: True".</span><span class="sxs-lookup"><span data-stu-id="194f1-184">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="194f1-185">Z důvodu selhání nebyly testovány všechny řetězce v poli po "Chyba".</span><span class="sxs-lookup"><span data-stu-id="194f1-185">Because of the failure, all strings in the array after "Error" weren't tested.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="194f1-186">![Okno Průzkumníka testů zobrazující selhání kontrolního výrazu IsFalse](./media/testing-library-with-visual-studio/failed-test-detail.png)</span><span class="sxs-lookup"><span data-stu-id="194f1-186">![Test Explorer window showing the IsFalse assertion failure](./media/testing-library-with-visual-studio/failed-test-detail.png)</span></span>

1. <span data-ttu-id="194f1-187">Vrátit zpět změny provedené v kroku 1 a odebrat řetězec "Chyba".</span><span class="sxs-lookup"><span data-stu-id="194f1-187">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="194f1-188">Znovu spusťte test a testy budou projít.</span><span class="sxs-lookup"><span data-stu-id="194f1-188">Rerun the test and the tests will pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="194f1-189">Otestujte verzi knihovny</span><span class="sxs-lookup"><span data-stu-id="194f1-189">Test the Release version of the library</span></span>

<span data-ttu-id="194f1-190">Byly jste spuštění testů proti ladění verze knihovny.</span><span class="sxs-lookup"><span data-stu-id="194f1-190">You've been running your tests against the Debug version of the library.</span></span> <span data-ttu-id="194f1-191">Nyní, když všechny testy byly všechny předány a jste dostatečně otestovali knihovnu, měli byste spustit testy další čas proti vydání sestavení knihovny.</span><span class="sxs-lookup"><span data-stu-id="194f1-191">Now that your tests have all passed and you've adequately tested your library, you should run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="194f1-192">Řada faktorů, včetně optimalizace kompilátoru, může někdy způsobit různé chování mezi ladění a vydání sestavení.</span><span class="sxs-lookup"><span data-stu-id="194f1-192">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="194f1-193">Chcete-li otestovat sestavení verze:</span><span class="sxs-lookup"><span data-stu-id="194f1-193">To test the Release build:</span></span>

1. <span data-ttu-id="194f1-194">Na panelu nástrojů sady Visual Studio změňte konfiguraci sestavení z **Ladění** na **Release**.</span><span class="sxs-lookup"><span data-stu-id="194f1-194">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="194f1-195">![Panel nástrojů Sady Visual Studio se zvýrazněným sestavením verze](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span><span class="sxs-lookup"><span data-stu-id="194f1-195">![Visual Studio toolbar with release build highlighted](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span></span>

1. <span data-ttu-id="194f1-196">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **StringLibrary** a z kontextové nabídky vyberte **Build** a knihovnu znovu zkompilujte.</span><span class="sxs-lookup"><span data-stu-id="194f1-196">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="194f1-197">![Kontextová nabídka StringLibrary s příkazem sestavení](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="194f1-197">![StringLibrary context menu with build command](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span></span>

1. <span data-ttu-id="194f1-198">Spusťte testy částí výběrem **možnosti** > **Spustit** > všechny**testy** z panelu nabídek.</span><span class="sxs-lookup"><span data-stu-id="194f1-198">Run the unit tests by choosing **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="194f1-199">Testy projdou.</span><span class="sxs-lookup"><span data-stu-id="194f1-199">The tests pass.</span></span>

<span data-ttu-id="194f1-200">Nyní, když jste dokončili testování knihovny, dalším krokem je zpřístupnit ji volajícím.</span><span class="sxs-lookup"><span data-stu-id="194f1-200">Now that you've finished testing your library, the next step is to make it available to callers.</span></span> <span data-ttu-id="194f1-201">Můžete jej svázat s jednou nebo více aplikacemi, nebo ji můžete distribuovat jako balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="194f1-201">You can bundle it with one or more applications, or you can distribute it as a NuGet package.</span></span> <span data-ttu-id="194f1-202">Další informace naleznete [v tématu Náročné knihovna standardních tříd .NET](consuming-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="194f1-202">For more information, see [Consuming a .NET Standard Class Library](consuming-library-with-visual-studio.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="194f1-203">Viz také</span><span class="sxs-lookup"><span data-stu-id="194f1-203">See also</span></span>

- [<span data-ttu-id="194f1-204">Základy testování částí - Visual Studio</span><span class="sxs-lookup"><span data-stu-id="194f1-204">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)

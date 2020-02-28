---
title: Testování .NET Standard knihovny tříd pomocí .NET Core v aplikaci Visual Studio
description: Vytvořte projekt testu jednotek pro knihovnu tříd .NET Core. Ověřte, že vaše knihovna tříd .NET Core pracuje správně s testy jednotek.
ms.date: 12/24/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 307261088f5c7c69c0e69fbd6b99940c04842eec
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156618"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a><span data-ttu-id="5209f-104">Testování knihovny .NET Standard pomocí .NET Core v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5209f-104">Test a .NET Standard library with .NET Core in Visual Studio</span></span>

<span data-ttu-id="5209f-105">V [sestavení knihovny .NET Standard v aplikaci Visual Studio](library-with-visual-studio.md)jste vytvořili jednoduchou knihovnu tříd, která přidá metodu rozšíření do <xref:System.String> třídy.</span><span class="sxs-lookup"><span data-stu-id="5209f-105">In [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md), you created a simple class library that adds an extension method to the <xref:System.String> class.</span></span> <span data-ttu-id="5209f-106">Nyní vytvoříte test jednotky, abyste se ujistili, že funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="5209f-106">Now, you'll create a unit test to make sure that it works as expected.</span></span> <span data-ttu-id="5209f-107">Projekt testování částí přidáte do řešení, které jste vytvořili v předchozím článku.</span><span class="sxs-lookup"><span data-stu-id="5209f-107">You'll add your unit test project to the solution you created in the previous article.</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="5209f-108">Vytvoření projektu testů jednotek</span><span class="sxs-lookup"><span data-stu-id="5209f-108">Create a unit test project</span></span>

<span data-ttu-id="5209f-109">Chcete-li vytvořit projekt testování částí, postupujte následovně:</span><span class="sxs-lookup"><span data-stu-id="5209f-109">To create the unit test project, do the following:</span></span>

1. <span data-ttu-id="5209f-110">Otevřete řešení `ClassLibraryProjects`, které jste vytvořili v článku [Vytvoření knihovny .NET Standard v aplikaci Visual Studio](library-with-visual-studio.md) .</span><span class="sxs-lookup"><span data-stu-id="5209f-110">Open the `ClassLibraryProjects` solution you created in the [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md) article.</span></span>

1. <span data-ttu-id="5209f-111">Přidejte do řešení nový projekt testování částí s názvem "StringLibraryTest".</span><span class="sxs-lookup"><span data-stu-id="5209f-111">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="5209f-112">V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat** > **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="5209f-112">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="5209f-113">Na stránce **Přidat nový projekt** zadejte do vyhledávacího pole **MSTest** .</span><span class="sxs-lookup"><span data-stu-id="5209f-113">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="5209f-114">V **C#** seznamu jazyků vyberte nebo **Visual Basic** a pak vyberte **všechny platformy** ze seznamu platforem.</span><span class="sxs-lookup"><span data-stu-id="5209f-114">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="5209f-115">Zvolte šablonu **projekt testů MSTest (.NET Core)** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="5209f-115">Choose the **MsTest Test Project (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="5209f-116">Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **StringLibraryTest** .</span><span class="sxs-lookup"><span data-stu-id="5209f-116">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="5209f-117">Potom zvolte **Create** (Vytvořit).</span><span class="sxs-lookup"><span data-stu-id="5209f-117">Then choose **Create**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="5209f-118">Kromě MSTest můžete také vytvořit xUnit a nUnit testovací projekty pro .NET Core v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5209f-118">In addition to an MSTest, you can also create xUnit and nUnit test projects for .NET Core in Visual Studio.</span></span>

1. <span data-ttu-id="5209f-119">Visual Studio vytvoří projekt a otevře soubor třídy v okně Code (kód) s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="5209f-119">Visual Studio creates the project and opens the class file in the code window with the following code:</span></span>

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

   <span data-ttu-id="5209f-120">Zdrojový kód vytvořený šablonou testu jednotky provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="5209f-120">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="5209f-121">Importuje obor názvů <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, který obsahuje typy používané pro testování částí.</span><span class="sxs-lookup"><span data-stu-id="5209f-121">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>

   - <span data-ttu-id="5209f-122">Aplikuje atribut [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) na třídu `UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="5209f-122">It applies the [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) attribute to the `UnitTest1` class.</span></span> <span data-ttu-id="5209f-123">Každá testovací metoda v testovací třídě, která je označena atributem [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) , je provedena automaticky při spuštění testu jednotky.</span><span class="sxs-lookup"><span data-stu-id="5209f-123">Each test method in a test class tagged with the [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) attribute is executed automatically when the unit test is run.</span></span>

   - <span data-ttu-id="5209f-124">Použije atribut [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) k definování `TestMethod1` v C# nebo `TestSub` v Visual Basic jako testovací metodu pro automatické provedení při spuštění testu jednotek.</span><span class="sxs-lookup"><span data-stu-id="5209f-124">It applies the [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic as a test method for automatic execution when the unit test is run.</span></span>

1. <span data-ttu-id="5209f-125">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **závislosti** projektu **StringLibraryTest** a vyberte možnost **Přidat odkaz** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="5209f-125">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Reference** from the context menu.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="5209f-126">![kontextová nabídka závislostí StringLibraryTest](./media/testing-library-with-visual-studio/add-reference-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="5209f-126">![Context menu of StringLibraryTest dependencies](./media/testing-library-with-visual-studio/add-reference-context-menu.png)</span></span>

1. <span data-ttu-id="5209f-127">V dialogovém okně **Správce odkazů** rozbalte uzel **projekty** a zaškrtněte políčko vedle položky **StringLibrary**.</span><span class="sxs-lookup"><span data-stu-id="5209f-127">In the **Reference Manager** dialog, expand the **Projects** node and check the box next to **StringLibrary**.</span></span> <span data-ttu-id="5209f-128">Přidání odkazu na sestavení `StringLibrary` umožňuje kompilátoru najít metody **StringLibrary** .</span><span class="sxs-lookup"><span data-stu-id="5209f-128">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods.</span></span> <span data-ttu-id="5209f-129">Vyberte tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="5209f-129">Select the **OK** button.</span></span> <span data-ttu-id="5209f-130">Do projektu knihovny tříd se přidá odkaz, `StringLibrary`.</span><span class="sxs-lookup"><span data-stu-id="5209f-130">A reference is added to your class library project, `StringLibrary`.</span></span>

   ![Dialogové okno Správce odkazů v aplikaci Visual Studio](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="5209f-132">Přidat a spustit metody testování částí</span><span class="sxs-lookup"><span data-stu-id="5209f-132">Add and run unit test methods</span></span>

<span data-ttu-id="5209f-133">Když aplikace Visual Studio spustí test jednotky, provede každou metodu, která je označena atributem <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> ve třídě testu jednotek, třída, na kterou je atribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> použit.</span><span class="sxs-lookup"><span data-stu-id="5209f-133">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a unit test class, the class to which the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute is applied.</span></span> <span data-ttu-id="5209f-134">Testovací metoda končí při nalezení prvního selhání nebo po úspěšném dokončení všech testů obsažených v metodě.</span><span class="sxs-lookup"><span data-stu-id="5209f-134">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="5209f-135">Nejběžnější testy volají členy třídy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>.</span><span class="sxs-lookup"><span data-stu-id="5209f-135">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="5209f-136">Mnoho metod Assert zahrnuje nejméně dva parametry, jeden z nich je očekávaný výsledek testu a druhý z nich je skutečný výsledek testu.</span><span class="sxs-lookup"><span data-stu-id="5209f-136">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="5209f-137">Některé často volané metody třídy `Assert` jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="5209f-137">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="5209f-138">Metody Assert</span><span class="sxs-lookup"><span data-stu-id="5209f-138">Assert methods</span></span>     | <span data-ttu-id="5209f-139">Funkce</span><span class="sxs-lookup"><span data-stu-id="5209f-139">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="5209f-140">Ověřuje, zda jsou dvě hodnoty nebo objekty stejné.</span><span class="sxs-lookup"><span data-stu-id="5209f-140">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="5209f-141">Vyhodnocení se nezdařila, pokud se hodnoty nebo objekty neshodují.</span><span class="sxs-lookup"><span data-stu-id="5209f-141">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="5209f-142">Ověřuje, že dvě proměnné objektu odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="5209f-142">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="5209f-143">Pokud proměnné odkazují na různé objekty, vyhodnocení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="5209f-143">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="5209f-144">Ověřuje, že je `false`podmínka.</span><span class="sxs-lookup"><span data-stu-id="5209f-144">Verifies that a condition is `false`.</span></span> <span data-ttu-id="5209f-145">Pokud je podmínka `true`, vyhodnocení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="5209f-145">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="5209f-146">Ověřuje, že objekt není `null`.</span><span class="sxs-lookup"><span data-stu-id="5209f-146">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="5209f-147">Pokud je objekt `null`, vyhodnocení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="5209f-147">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="5209f-148">Můžete také použít metodu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> v testovací metodě k označení typu výjimky, kterou očekává, že má být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="5209f-148">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="5209f-149">Test se nezdařil, pokud není vyvolána zadaná výjimka.</span><span class="sxs-lookup"><span data-stu-id="5209f-149">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="5209f-150">Při testování metody `StringLibrary.StartsWithUpper` chcete zadat počet řetězců, které začínají velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="5209f-150">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="5209f-151">Očekáváte, že metoda vrátí `true` v těchto případech, takže můžete volat metodu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A>.</span><span class="sxs-lookup"><span data-stu-id="5209f-151">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> method.</span></span> <span data-ttu-id="5209f-152">Podobně je vhodné zadat počet řetězců, které začínají jinou výjimkou znaku velkého písmene.</span><span class="sxs-lookup"><span data-stu-id="5209f-152">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="5209f-153">Očekáváte, že metoda vrátí `false` v těchto případech, takže můžete volat metodu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A>.</span><span class="sxs-lookup"><span data-stu-id="5209f-153">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> method.</span></span>

<span data-ttu-id="5209f-154">Vzhledem k tomu, že vaše metoda knihovny zpracovává řetězce, je také vhodné se ujistit, že úspěšně zpracovává [prázdný řetězec (`String.Empty`)](xref:System.String.Empty), platný řetězec, který neobsahuje žádné znaky a jehož <xref:System.String.Length> je 0, a `null` řetězec, který nebyl inicializován.</span><span class="sxs-lookup"><span data-stu-id="5209f-154">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="5209f-155">Pokud je `StartsWithUpper` volána jako metoda rozšíření v instanci <xref:System.String>, nelze předat `null` řetězec.</span><span class="sxs-lookup"><span data-stu-id="5209f-155">If `StartsWithUpper` is called as an extension method on a <xref:System.String> instance, it can't be passed a `null` string.</span></span> <span data-ttu-id="5209f-156">Můžete ji však také volat přímo jako statickou metodu a předat jeden <xref:System.String> argument.</span><span class="sxs-lookup"><span data-stu-id="5209f-156">However, you can also call it directly as a static method and pass a single <xref:System.String> argument.</span></span>

<span data-ttu-id="5209f-157">Budete definovat tři metody, každý z nich volá metodu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> opakovaně pro každý prvek v poli řetězců.</span><span class="sxs-lookup"><span data-stu-id="5209f-157">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="5209f-158">Vzhledem k tomu, že testovací metoda selže, jakmile najde první selhání, zavoláte přetížení metody, které vám umožní předat řetězec, který označuje hodnotu řetězce použitou ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="5209f-158">Because the test method fails as soon as it finds the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="5209f-159">Postup vytvoření testovacích metod:</span><span class="sxs-lookup"><span data-stu-id="5209f-159">To create the test methods:</span></span>

1. <span data-ttu-id="5209f-160">V okně kódu *UnitTest1.cs* nebo *UnitTest1. vb* nahraďte kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="5209f-160">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   <span data-ttu-id="5209f-161">Test velkých písmen v metodě `TestStartsWithUpper` obsahuje řecké velké písmeno alfa (U + 0391) a velké písmeno cyrilice EM (U + 041C).</span><span class="sxs-lookup"><span data-stu-id="5209f-161">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="5209f-162">Test malých písmen v metodě `TestDoesNotStartWithUpper` obsahuje řecké malé písmeno alfa (U + 03B1) a malé písmeno g (u + 0433) v cyrilici.</span><span class="sxs-lookup"><span data-stu-id="5209f-162">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="5209f-163">V řádku nabídek vyberte **soubor** > **Uložit UnitTest1.cs jako** nebo **soubor** > **Uložit UnitTest1. vb jako**.</span><span class="sxs-lookup"><span data-stu-id="5209f-163">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="5209f-164">V dialogovém okně **Uložit soubor jako** vyberte šipku vedle tlačítka **Uložit** a vyberte **Uložit s kódováním**.</span><span class="sxs-lookup"><span data-stu-id="5209f-164">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="5209f-165">![Visual Studio uložit soubor jako dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="5209f-165">![Visual Studio Save File As dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span></span>

1. <span data-ttu-id="5209f-166">Kliknutím na tlačítko **Ano** v dialogovém okně **Potvrdit uložení jako** soubor uložte.</span><span class="sxs-lookup"><span data-stu-id="5209f-166">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="5209f-167">V dialogovém okně **Upřesnit možnosti uložení** vyberte v rozevíracím seznamu **kódování** znakovou **sadu Unicode (UTF-8 s podpisem 65001)** a vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="5209f-167">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="5209f-168">Dialogové okno ![Upřesnit možnosti uložení v aplikaci Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)</span><span class="sxs-lookup"><span data-stu-id="5209f-168">![Visual Studio Advanced Save Options dialog](./media/testing-library-with-visual-studio/advanced-save-options.png)</span></span>

   <span data-ttu-id="5209f-169">Pokud neuložíte zdrojový kód jako soubor s kódováním UTF8, Visual Studio ho může uložit jako soubor ASCII.</span><span class="sxs-lookup"><span data-stu-id="5209f-169">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="5209f-170">Pokud k tomu dojde, modul runtime nebude přesně kódovat znaky UTF8 mimo rozsah ASCII a výsledky testu nebudou správné.</span><span class="sxs-lookup"><span data-stu-id="5209f-170">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="5209f-171">Na panelu nabídek vyberte možnost **Test** > **Spustit** > **všechny testy**.</span><span class="sxs-lookup"><span data-stu-id="5209f-171">On the menu bar, select **Test** > **Run** > **All Tests**.</span></span> <span data-ttu-id="5209f-172">Otevře se okno **Průzkumník testů** , ve kterém se zobrazí, že testy proběhly úspěšně.</span><span class="sxs-lookup"><span data-stu-id="5209f-172">The **Test Explorer** window opens and shows that the tests ran successfully.</span></span> <span data-ttu-id="5209f-173">Tři testy jsou uvedeny v části **prošlé testy** a v části **Souhrn** se zobrazí výsledek testovacího běhu.</span><span class="sxs-lookup"><span data-stu-id="5209f-173">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="5209f-174">![okno Průzkumníka testů s předáváním testů](./media/testing-library-with-visual-studio/test-explorer-window.png)</span><span class="sxs-lookup"><span data-stu-id="5209f-174">![Test Explorer window with passing tests](./media/testing-library-with-visual-studio/test-explorer-window.png)</span></span>

## <a name="handle-test-failures"></a><span data-ttu-id="5209f-175">Zpracování selhání testu</span><span class="sxs-lookup"><span data-stu-id="5209f-175">Handle test failures</span></span>

<span data-ttu-id="5209f-176">V testovacím běhu došlo k žádným chybám, ale mírně ho změňte, aby jedna z testovacích metod nebyla úspěšná:</span><span class="sxs-lookup"><span data-stu-id="5209f-176">Your test run had no failures, but change it slightly so that one of the test methods fails:</span></span>

1. <span data-ttu-id="5209f-177">Upravte pole `words` v metodě `TestDoesNotStartWithUpper` tak, aby obsahovala řetězec "Error" (chyba).</span><span class="sxs-lookup"><span data-stu-id="5209f-177">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="5209f-178">Nemusíte soubor ukládat, protože Visual Studio automaticky ukládá otevřené soubory, když je řešení sestaveno pro spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="5209f-178">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="5209f-179">Spusťte test výběrem možnosti **test** > **Spustit** > **všechny testy** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="5209f-179">Run the test by selecting **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="5209f-180">Okno **Průzkumník testů** indikuje, že dva testy byly úspěšné a jedna se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="5209f-180">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="5209f-181">![okno Průzkumníka testů s neúspěšnými testy](./media/testing-library-with-visual-studio/failed-test-window.png)</span><span class="sxs-lookup"><span data-stu-id="5209f-181">![Test Explorer window with failing tests](./media/testing-library-with-visual-studio/failed-test-window.png)</span></span>

1. <span data-ttu-id="5209f-182">Vyberte neúspěšný test `TestDoesNotStartWith`.</span><span class="sxs-lookup"><span data-stu-id="5209f-182">Select the failed test, `TestDoesNotStartWith`.</span></span> <span data-ttu-id="5209f-183">V okně **Průzkumník testů** se zobrazí zpráva vytvořená kontrolním výrazem: Assert. NEPRAVDA.</span><span class="sxs-lookup"><span data-stu-id="5209f-183">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="5209f-184">Očekávané pro ' error ': false; skutečnost: true ".</span><span class="sxs-lookup"><span data-stu-id="5209f-184">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="5209f-185">Z důvodu chyby nebyly testovány všechny řetězce v poli po "Error".</span><span class="sxs-lookup"><span data-stu-id="5209f-185">Because of the failure, all strings in the array after "Error" weren't tested.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="5209f-186">![okno Průzkumníka testů znázorňující selhání kontrolního výrazu s hodnotou false](./media/testing-library-with-visual-studio/failed-test-detail.png)</span><span class="sxs-lookup"><span data-stu-id="5209f-186">![Test Explorer window showing the IsFalse assertion failure](./media/testing-library-with-visual-studio/failed-test-detail.png)</span></span>

1. <span data-ttu-id="5209f-187">Vraťte změny, které jste provedli v kroku 1, a odeberte řetězec "Error" (chyba).</span><span class="sxs-lookup"><span data-stu-id="5209f-187">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="5209f-188">Spusťte test znovu a testy se budou předávat.</span><span class="sxs-lookup"><span data-stu-id="5209f-188">Rerun the test and the tests will pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="5209f-189">Testování verze pro vydání knihovny</span><span class="sxs-lookup"><span data-stu-id="5209f-189">Test the Release version of the library</span></span>

<span data-ttu-id="5209f-190">Spustili jste testy pro ladicí verzi knihovny.</span><span class="sxs-lookup"><span data-stu-id="5209f-190">You've been running your tests against the Debug version of the library.</span></span> <span data-ttu-id="5209f-191">Nyní, když testy úspěšně prošly a jste dostatečně otestovali knihovnu, měli byste spustit testy dodatečně na sestavení vydaných verzí knihovny.</span><span class="sxs-lookup"><span data-stu-id="5209f-191">Now that your tests have all passed and you've adequately tested your library, you should run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="5209f-192">Několik faktorů, včetně optimalizací kompilátoru, může někdy způsobit různé chování mezi sestaveními ladění a vydání.</span><span class="sxs-lookup"><span data-stu-id="5209f-192">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="5209f-193">Testování sestavení pro vydání:</span><span class="sxs-lookup"><span data-stu-id="5209f-193">To test the Release build:</span></span>

1. <span data-ttu-id="5209f-194">Na panelu nástrojů sady Visual Studio změňte konfiguraci sestavení z **ladit** na **release**.</span><span class="sxs-lookup"><span data-stu-id="5209f-194">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="5209f-195">panel nástrojů ![sady Visual Studio s zvýrazněnou verzí buildu](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span><span class="sxs-lookup"><span data-stu-id="5209f-195">![Visual Studio toolbar with release build highlighted](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span></span>

1. <span data-ttu-id="5209f-196">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **StringLibrary** a vyberte **sestavení** z místní nabídky pro rekompilaci knihovny.</span><span class="sxs-lookup"><span data-stu-id="5209f-196">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="5209f-197">místní nabídka ![StringLibrary pomocí příkazu Build](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="5209f-197">![StringLibrary context menu with build command](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span></span>

1. <span data-ttu-id="5209f-198">Spusťte testy jednotek výběrem možnosti **Test** > **Spustit** > **všechny testy** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="5209f-198">Run the unit tests by choosing **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="5209f-199">Testy jsou passované.</span><span class="sxs-lookup"><span data-stu-id="5209f-199">The tests pass.</span></span>

<span data-ttu-id="5209f-200">Teď, když jste dokončili testování knihovny, je dalším krokem zpřístupnění volajícím.</span><span class="sxs-lookup"><span data-stu-id="5209f-200">Now that you've finished testing your library, the next step is to make it available to callers.</span></span> <span data-ttu-id="5209f-201">Můžete ho seskupit s jednou nebo více aplikacemi nebo ho můžete distribuovat jako balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="5209f-201">You can bundle it with one or more applications, or you can distribute it as a NuGet package.</span></span> <span data-ttu-id="5209f-202">Další informace naleznete v tématu [spotřebovávání knihovny tříd .NET Standard](consuming-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="5209f-202">For more information, see [Consuming a .NET Standard Class Library](consuming-library-with-visual-studio.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5209f-203">Viz také</span><span class="sxs-lookup"><span data-stu-id="5209f-203">See also</span></span>

- [<span data-ttu-id="5209f-204">Základy testování částí – Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5209f-204">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)

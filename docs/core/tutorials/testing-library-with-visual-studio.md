---
title: Testování .NET Standard knihovny tříd pomocí .NET Core v aplikaci Visual Studio 2017
description: Vytvořte projekt testu jednotek pro knihovnu tříd .NET Core. Ověřte, že vaše knihovna tříd .NET Core pracuje správně s testy jednotek.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: e8a0d28919d4d26e69fb5a5f926b0e96270a2407
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925892"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio-2017"></a><span data-ttu-id="e827b-104">Testování knihovny .NET Standard pomocí platformy .NET Core v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="e827b-104">Test a .NET Standard library with .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="e827b-105">V [sestavách knihovny .NET standard C# s a .NET Core v aplikaci Visual Studio 2017](library-with-visual-studio.md) nebo [sestavení knihovny .NET Standard pomocí Visual Basic a .NET core v aplikaci Visual Studio 2017](vb-library-with-visual-studio.md)jste vytvořili jednoduchou knihovnu tříd, která přidá metodu rozšíření do <xref:System.String> třída.</span><span class="sxs-lookup"><span data-stu-id="e827b-105">In [Build a .NET Standard library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md) or [Build a .NET Standard library with Visual Basic and .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md), you created a simple class library that adds an extension method to the <xref:System.String> class.</span></span> <span data-ttu-id="e827b-106">Nyní vytvoříte test jednotky, abyste se ujistili, že funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="e827b-106">Now, you'll create a unit test to make sure that it works as expected.</span></span> <span data-ttu-id="e827b-107">Projekt testování částí přidáte do řešení, které jste vytvořili v předchozím článku.</span><span class="sxs-lookup"><span data-stu-id="e827b-107">You'll add your unit test project to the solution you created in the previous article.</span></span>

## <a name="creating-a-unit-test-project"></a><span data-ttu-id="e827b-108">Vytvoření projektu testu jednotek</span><span class="sxs-lookup"><span data-stu-id="e827b-108">Creating a unit test project</span></span>

<span data-ttu-id="e827b-109">Chcete-li vytvořit projekt testování částí, postupujte následovně:</span><span class="sxs-lookup"><span data-stu-id="e827b-109">To create the unit test project, do the following:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="e827b-110">C#</span><span class="sxs-lookup"><span data-stu-id="e827b-110">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="e827b-111">V **Průzkumník řešení**otevřete kontextovou nabídku uzlu řešení **ClassLibraryProjects** a vyberte **Přidat** > **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="e827b-111">In **Solution Explorer**, open the context menu for the **ClassLibraryProjects** solution node and select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="e827b-112">V dialogovém okně **Přidat nový projekt** vyberte uzel **vizuálu C#**  .</span><span class="sxs-lookup"><span data-stu-id="e827b-112">In the **Add New Project** dialog, select the **Visual C#** node.</span></span> <span data-ttu-id="e827b-113">Pak vyberte uzel **.NET Core** následovaný šablonou projektu **MSTest test (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="e827b-113">Then select the **.NET Core** node followed by the **MSTest Test Project (.NET Core)** project template.</span></span> <span data-ttu-id="e827b-114">Do textového pole **název** zadejte "StringLibraryTest" jako název projektu.</span><span class="sxs-lookup"><span data-stu-id="e827b-114">In the **Name** text box, enter "StringLibraryTest" as the name of the project.</span></span> <span data-ttu-id="e827b-115">Vyberte **OK** a vytvořte tak projekt testování částí.</span><span class="sxs-lookup"><span data-stu-id="e827b-115">Select **OK** to create the unit test project.</span></span>

   ![Dialogové okno Přidat nový projekt s zobrazeným projektem testu jednotek –C#](./media/testing-library-with-visual-studio/create-new-test-project.png)

   > [!NOTE]  
   > <span data-ttu-id="e827b-117">Kromě testovacího projektu MSTest můžete také pomocí sady Visual Studio vytvořit projekt testů xUnit pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e827b-117">In addition to an MSTest Test project, you can also use Visual Studio to create an xUnit test project for .NET Core.</span></span>

1. <span data-ttu-id="e827b-118">Visual Studio vytvoří projekt a otevře soubor *UnitTest1.cs* v okně Code (kód).</span><span class="sxs-lookup"><span data-stu-id="e827b-118">Visual Studio creates the project and opens the *UnitTest1.cs* file in the code window.</span></span>

   ![Okno Visual Studio Code pro třídu projektu testování částí a metodu –C#](./media/testing-library-with-visual-studio/unit-test-editor-window.png)

   <span data-ttu-id="e827b-120">Zdrojový kód vytvořený šablonou testu jednotky provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="e827b-120">The source code created by the unit test template does the following:</span></span>

   * <span data-ttu-id="e827b-121">Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> obor názvů, který obsahuje typy používané pro testování částí.</span><span class="sxs-lookup"><span data-stu-id="e827b-121">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>

   * <span data-ttu-id="e827b-122">Aplikuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atribut `UnitTest1` na třídu.</span><span class="sxs-lookup"><span data-stu-id="e827b-122">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span> <span data-ttu-id="e827b-123">Každá testovací metoda v testovací třídě, která je označena\] atributem TestMethod, \[je provedena automaticky při spuštění testu jednotky.</span><span class="sxs-lookup"><span data-stu-id="e827b-123">Each test method in a test class tagged with the \[TestMethod\] attribute is executed automatically when the unit test is run.</span></span>

   * <span data-ttu-id="e827b-124">Použije <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atribut pro definování `TestMethod1` jako testovací metodu pro automatické provádění při spuštění testu jednotky.</span><span class="sxs-lookup"><span data-stu-id="e827b-124">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1` as a test method for automatic execution when the unit test is run.</span></span>

1. <span data-ttu-id="e827b-125">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **závislosti** projektu **StringLibraryTest** a vyberte možnost **Přidat odkaz** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="e827b-125">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Reference** from the context menu.</span></span>

   ![Kontextová nabídka závislostí StringLibraryTest-C#](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="e827b-127">V dialogovém okně **Správce odkazů** rozbalte uzel **projekty** a zaškrtněte políčko vedle položky **StringLibrary**.</span><span class="sxs-lookup"><span data-stu-id="e827b-127">In the **Reference Manager** dialog, expand the **Projects** node and check the box next to **StringLibrary**.</span></span> <span data-ttu-id="e827b-128">Přidání odkazu na `StringLibrary` sestavení umožňuje kompilátoru najít metody **StringLibrary** .</span><span class="sxs-lookup"><span data-stu-id="e827b-128">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods.</span></span> <span data-ttu-id="e827b-129">Vyberte tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="e827b-129">Select the **OK** button.</span></span> <span data-ttu-id="e827b-130">Tím se přidá odkaz na váš projekt knihovny tříd, `StringLibrary`.</span><span class="sxs-lookup"><span data-stu-id="e827b-130">This adds a reference to your class library project, `StringLibrary`.</span></span>

   ![Dialogová okna pro přidání odkazu na projekt v aplikaci Visual Studio](./media/testing-library-with-visual-studio/project-reference-manager.png)

# <a name="visual-basictabvb"></a>[<span data-ttu-id="e827b-132">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e827b-132">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="e827b-133">V **Průzkumník řešení**otevřete kontextovou nabídku uzlu řešení **ClassLibraryProjects** a vyberte **Přidat** > **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="e827b-133">In **Solution Explorer**, open the context menu for the **ClassLibraryProjects** solution node and select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="e827b-134">V dialogovém okně **Přidat nový projekt** vyberte uzel **Visual Basic** .</span><span class="sxs-lookup"><span data-stu-id="e827b-134">In the **Add New Project** dialog, select the **Visual Basic** node.</span></span> <span data-ttu-id="e827b-135">Pak vyberte uzel **.NET Core** následovaný šablonou projektu **MSTest test (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="e827b-135">Then select the **.NET Core** node followed by the **MSTest Test Project (.NET Core)** project template.</span></span> <span data-ttu-id="e827b-136">Do textového pole **název** zadejte "StringLibraryTest" jako název projektu.</span><span class="sxs-lookup"><span data-stu-id="e827b-136">In the **Name** text box, enter "StringLibraryTest" as the name of the project.</span></span> <span data-ttu-id="e827b-137">Vyberte **OK** a vytvořte tak projekt testování částí.</span><span class="sxs-lookup"><span data-stu-id="e827b-137">Select **OK** to create the unit test project.</span></span>

   ![Dialogové okno Přidat nový projekt s zobrazeným projektem testu jednotek – Visual Basic](./media/testing-library-with-visual-studio/vb-create-new-test-project.png)

   > [!NOTE]  
   > <span data-ttu-id="e827b-139">Kromě testovacího projektu MSTest můžete také pomocí sady Visual Studio vytvořit projekt testů xUnit pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e827b-139">In addition to an MSTest Test project, you can also use Visual Studio to create an xUnit test project for .NET Core.</span></span>

1. <span data-ttu-id="e827b-140">Visual Studio vytvoří projekt a otevře soubor *UnitTest1. vb* v okně Code (kód).</span><span class="sxs-lookup"><span data-stu-id="e827b-140">Visual Studio creates the project and opens the *UnitTest1.vb* file in the code window.</span></span>

   ![Okno Visual Studio Code pro třídu projektu testování částí a metodu-Visual Basic](./media/testing-library-with-visual-studio/vb-unit-test-editor-window.png)

   <span data-ttu-id="e827b-142">Zdrojový kód vytvořený šablonou testu jednotky provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="e827b-142">The source code created by the unit test template does the following:</span></span>

   * <span data-ttu-id="e827b-143">Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> obor názvů, který obsahuje typy používané pro testování částí.</span><span class="sxs-lookup"><span data-stu-id="e827b-143">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>

   * <span data-ttu-id="e827b-144">Aplikuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>atribut) `UnitTest1` na třídu.</span><span class="sxs-lookup"><span data-stu-id="e827b-144">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>) attribute to the `UnitTest1` class.</span></span> <span data-ttu-id="e827b-145">Každá testovací metoda v testovací třídě, která je označena atributem, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> je provedena automaticky při spuštění testu jednotky.</span><span class="sxs-lookup"><span data-stu-id="e827b-145">Each test method in a test class tagged with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute is executed automatically when the unit test is run.</span></span>

   * <span data-ttu-id="e827b-146">Použije <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atribut pro definování `TestMethod1` jako testovací metodu pro automatické provádění při spuštění testu jednotky.</span><span class="sxs-lookup"><span data-stu-id="e827b-146">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1` as a test method for automatic execution when the unit test is run.</span></span>

1. <span data-ttu-id="e827b-147">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **závislosti** projektu **StringLibraryTest** a vyberte možnost **Přidat odkaz** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="e827b-147">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Reference** from the context menu.</span></span>

   ![Kontextová nabídka závislostí StringLibraryTest](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="e827b-149">V dialogovém okně **Správce odkazů** rozbalte uzel **projekty** a zaškrtněte políčko vedle položky **StringLibrary**.</span><span class="sxs-lookup"><span data-stu-id="e827b-149">In the **Reference Manager** dialog, expand the **Projects** node and check the box next to **StringLibrary**.</span></span> <span data-ttu-id="e827b-150">Přidání odkazu na `StringLibrary` sestavení umožňuje kompilátoru najít metody **StringLibrary** .</span><span class="sxs-lookup"><span data-stu-id="e827b-150">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods.</span></span> <span data-ttu-id="e827b-151">Vyberte tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="e827b-151">Select the **OK** button.</span></span> <span data-ttu-id="e827b-152">Tím se přidá odkaz na váš projekt knihovny tříd, `StringLibrary`.</span><span class="sxs-lookup"><span data-stu-id="e827b-152">This adds a reference to your class library project, `StringLibrary`.</span></span>

   ![Dialogová okna pro přidání odkazu na projekt v aplikaci Visual Studio – Visual Basic](./media/testing-library-with-visual-studio/project-reference-manager.png)

---

## <a name="adding-and-running-unit-test-methods"></a><span data-ttu-id="e827b-154">Přidávání a spouštění metod testování částí</span><span class="sxs-lookup"><span data-stu-id="e827b-154">Adding and running unit test methods</span></span>

<span data-ttu-id="e827b-155">Když aplikace Visual Studio spustí test jednotky, provede každou metodu označenou <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atributem ve třídě testu jednotek, třída, na <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> kterou je atribut použit.</span><span class="sxs-lookup"><span data-stu-id="e827b-155">When Visual Studio runs a unit test, it executes each method marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a unit test class, the class to which the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute is applied.</span></span> <span data-ttu-id="e827b-156">Testovací metoda končí, když dojde k první chybě nebo když všechny testy obsažené v metodě byly úspěšné.</span><span class="sxs-lookup"><span data-stu-id="e827b-156">A test method ends when the first failure is encountered or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="e827b-157">Nejběžnější testy volají členy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> třídy.</span><span class="sxs-lookup"><span data-stu-id="e827b-157">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="e827b-158">Mnoho metod Assert zahrnuje nejméně dva parametry, jeden z nich je očekávaný výsledek testu a druhý z nich je skutečný výsledek testu.</span><span class="sxs-lookup"><span data-stu-id="e827b-158">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="e827b-159">Některé z nejčastěji volaných metod jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="e827b-159">Some of its most frequently called methods are shown in the table below.</span></span>

<span data-ttu-id="e827b-160">Metody Assert</span><span class="sxs-lookup"><span data-stu-id="e827b-160">Assert methods</span></span> | <span data-ttu-id="e827b-161">Funkce</span><span class="sxs-lookup"><span data-stu-id="e827b-161">Function</span></span>
--- | ---
`Assert.AreEqual` | <span data-ttu-id="e827b-162">Ověřuje, zda jsou dvě hodnoty nebo objekty stejné.</span><span class="sxs-lookup"><span data-stu-id="e827b-162">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="e827b-163">Pokud hodnoty nebo objekty nejsou stejné, vyhodnocení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="e827b-163">The assert fails if the values or objects are not equal.</span></span>
`Assert.AreSame` | <span data-ttu-id="e827b-164">Ověřuje, že dvě proměnné objektu odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="e827b-164">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="e827b-165">Pokud proměnné odkazují na různé objekty, vyhodnocení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="e827b-165">The assert fails if the variables refer to different objects.</span></span>
`Assert.IsFalse` | <span data-ttu-id="e827b-166">Ověřuje, jestli je `false`podmínka.</span><span class="sxs-lookup"><span data-stu-id="e827b-166">Verifies that a condition is `false`.</span></span> <span data-ttu-id="e827b-167">Pokud je `true`podmínka, vyhodnocení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="e827b-167">The assert fails if the condition is `true`.</span></span>
`Assert.IsNotNull` | <span data-ttu-id="e827b-168">Ověřuje, že objekt `null`není.</span><span class="sxs-lookup"><span data-stu-id="e827b-168">Verifies that an object is not `null`.</span></span> <span data-ttu-id="e827b-169">Pokud je `null`objekt, vyhodnocení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="e827b-169">The assert fails if the object is `null`.</span></span>

<span data-ttu-id="e827b-170">Můžete také použít <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> atribut na testovací metodu.</span><span class="sxs-lookup"><span data-stu-id="e827b-170">You can also apply the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> attribute to a test method.</span></span> <span data-ttu-id="e827b-171">Označuje typ výjimky. očekává se, že testovací metoda bude vyvolána.</span><span class="sxs-lookup"><span data-stu-id="e827b-171">It indicates the type of exception a test method is expected to throw.</span></span> <span data-ttu-id="e827b-172">Test se nezdařil, pokud není vyvolána zadaná výjimka.</span><span class="sxs-lookup"><span data-stu-id="e827b-172">The test fails if the specified exception is not thrown.</span></span>

<span data-ttu-id="e827b-173">Při testování `StringLibrary.StartsWithUpper` metody je třeba zadat počet řetězců, které začínají velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="e827b-173">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="e827b-174">Očekáváte, že se metoda `true` vrátí v těchto případech, takže můžete <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> volat metodu.</span><span class="sxs-lookup"><span data-stu-id="e827b-174">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> method.</span></span> <span data-ttu-id="e827b-175">Podobně je vhodné zadat počet řetězců, které začínají jinou výjimkou znaku velkého písmene.</span><span class="sxs-lookup"><span data-stu-id="e827b-175">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="e827b-176">Očekáváte, že se metoda `false` vrátí v těchto případech, takže můžete <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> volat metodu.</span><span class="sxs-lookup"><span data-stu-id="e827b-176">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> method.</span></span>

<span data-ttu-id="e827b-177">Vzhledem k tomu, že vaše metoda knihovny zpracovává řetězce, je také vhodné se ujistit, že úspěšně zpracovává [prázdný`String.Empty`řetězec ()](xref:System.String.Empty), platný řetězec, který neobsahuje žádné znaky <xref:System.String.Length> a jehož hodnota je 0 `null` , a řetězec, který nebyl inicializované.</span><span class="sxs-lookup"><span data-stu-id="e827b-177">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that has not been initialized.</span></span> <span data-ttu-id="e827b-178">Pokud `StartsWithUpper` je volána jako metoda rozšíření <xref:System.String> v instanci, nelze předat `null` řetězec.</span><span class="sxs-lookup"><span data-stu-id="e827b-178">If `StartsWithUpper` is called as an extension method on a <xref:System.String> instance, it cannot be passed a `null` string.</span></span> <span data-ttu-id="e827b-179">Můžete ji však také volat přímo jako statickou metodu a předat jeden <xref:System.String> argument.</span><span class="sxs-lookup"><span data-stu-id="e827b-179">However, you can also call it directly as a static method and pass a single <xref:System.String> argument.</span></span>

<span data-ttu-id="e827b-180">Budete definovat tři metody, z nichž každá volá svou <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metodu opakovaně pro každý prvek v poli řetězců.</span><span class="sxs-lookup"><span data-stu-id="e827b-180">You'll define three methods, each of which calls its <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="e827b-181">Vzhledem k tomu, že testovací metoda selže, jakmile dojde k první chybě, zavoláte přetížení metody, které vám umožní předat řetězec, který označuje hodnotu řetězce použitou ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="e827b-181">Because the test method fails as soon as it encounters the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="e827b-182">Postup vytvoření testovacích metod:</span><span class="sxs-lookup"><span data-stu-id="e827b-182">To create the test methods:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="e827b-183">C#</span><span class="sxs-lookup"><span data-stu-id="e827b-183">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="e827b-184">V okně *UnitTest1.cs* kód nahraďte kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="e827b-184">In the *UnitTest1.cs* code window, replace the code with the following code:</span></span>

   [!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]

   <span data-ttu-id="e827b-185">Všimněte si, že váš test velkých písmen v `TestStartsWithUpper` metodě obsahuje řecké velké písmeno alfa (u + 0391) a velké písmeno cyrilice em (u + 041C) a test malých písmen `TestDoesNotStartWithUpper` v metodě zahrnuje řecký malý znak. Alpha (U + 03B1) a malé písmeno g (U + 0433).</span><span class="sxs-lookup"><span data-stu-id="e827b-185">Note that your test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C), and the test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="e827b-186">Na řádku nabídek vyberte **soubor** > **Uložit UnitTest1.cs jako**.</span><span class="sxs-lookup"><span data-stu-id="e827b-186">On the menu bar, select **File** > **Save UnitTest1.cs As**.</span></span> <span data-ttu-id="e827b-187">V dialogovém okně **Uložit soubor jako** vyberte šipku vedle tlačítka **Uložit** a vyberte **Uložit s kódováním**.</span><span class="sxs-lookup"><span data-stu-id="e827b-187">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   ![Visual Studio uložit soubor jako dialog – dialogové oknoC#](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

# <a name="visual-basictabvb"></a>[<span data-ttu-id="e827b-189">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e827b-189">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="e827b-190">V okně kódu *UnitTest1. vb* nahraďte kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="e827b-190">In the *UnitTest1.vb* code window, replace the code with the following code:</span></span>

    [!CODE-vb[Test#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   <span data-ttu-id="e827b-191">Všimněte si, že váš test velkých písmen v `TestStartsWithUpper` metodě obsahuje řecké velké písmeno alfa (u + 0391) a velké písmeno cyrilice em (u + 041C) a test malých písmen `TestDoesNotStartWithUpper` v metodě zahrnuje řecký malý znak. Alpha (U + 03B1) a malé písmeno g (U + 0433).</span><span class="sxs-lookup"><span data-stu-id="e827b-191">Note that your test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C), and the test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="e827b-192">Na panelu nabídek vyberte **soubor** > **Uložit UnitTest1. vb jako**.</span><span class="sxs-lookup"><span data-stu-id="e827b-192">On the menu bar, select **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="e827b-193">V dialogovém okně **Uložit soubor jako** vyberte šipku vedle tlačítka **Uložit** a vyberte **Uložit s kódováním**.</span><span class="sxs-lookup"><span data-stu-id="e827b-193">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   ![Visual Studio uložit soubor jako dialog – Visual Basic](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

---

1. <span data-ttu-id="e827b-195">Kliknutím na tlačítko **Ano** v dialogovém okně **Potvrdit uložení jako** soubor uložte.</span><span class="sxs-lookup"><span data-stu-id="e827b-195">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="e827b-196">V dialogovém okně **Upřesnit možnosti uložení** vyberte v rozevíracím seznamu **kódování** znakovou **sadu Unicode (UTF-8 s podpisem 65001)** a vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="e827b-196">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   ![Dialogové okno Upřesnit možnosti uložení v aplikaci Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)

   <span data-ttu-id="e827b-198">Pokud neuložíte zdrojový kód jako soubor s kódováním UTF8, Visual Studio ho může uložit jako soubor ASCII.</span><span class="sxs-lookup"><span data-stu-id="e827b-198">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="e827b-199">Pokud k tomu dojde, modul runtime nebude přesně kódovat znaky UTF8 mimo rozsah ASCII a výsledky testu nebudou přesné.</span><span class="sxs-lookup"><span data-stu-id="e827b-199">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be accurate.</span></span>

1. <span data-ttu-id="e827b-200">Na panelu nabídek vyberte možnost **test** > **Spustit** > **všechny testy**.</span><span class="sxs-lookup"><span data-stu-id="e827b-200">On the menu bar, select **Test** > **Run** > **All Tests**.</span></span> <span data-ttu-id="e827b-201">Otevře se okno **Průzkumník testů** , ve kterém se zobrazí, že testy proběhly úspěšně.</span><span class="sxs-lookup"><span data-stu-id="e827b-201">The **Test Explorer** window opens and shows that the tests ran successfully.</span></span> <span data-ttu-id="e827b-202">Tři testy jsou uvedeny v části **prošlé testy** a v části **Souhrn** se zobrazí výsledek testovacího běhu.</span><span class="sxs-lookup"><span data-stu-id="e827b-202">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   ![Okno Průzkumníka testů s předáváním testů](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handling-test-failures"></a><span data-ttu-id="e827b-204">Zpracování selhání testu</span><span class="sxs-lookup"><span data-stu-id="e827b-204">Handling test failures</span></span>

<span data-ttu-id="e827b-205">V testovacím běhu došlo k žádným chybám, ale mírně ho změňte, aby jedna z testovacích metod nebyla úspěšná:</span><span class="sxs-lookup"><span data-stu-id="e827b-205">Your test run had no failures, but change it slightly so that one of the test methods fails:</span></span>

1. <span data-ttu-id="e827b-206">`words` Upravte pole`TestDoesNotStartWithUpper` v metodě tak, aby obsahovalo řetězec "Error" (chyba).</span><span class="sxs-lookup"><span data-stu-id="e827b-206">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="e827b-207">Nemusíte soubor ukládat, protože Visual Studio automaticky ukládá otevřené soubory, když je řešení sestaveno pro spouštění testů.</span><span class="sxs-lookup"><span data-stu-id="e827b-207">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="e827b-208">Spusťte test výběrem možnosti **test** > **Spustit** > **všechny testy** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="e827b-208">Run the test by selecting **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="e827b-209">Okno **Průzkumník testů** indikuje, že dva testy byly úspěšné a jedna se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="e827b-209">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   ![Okno Průzkumníka testů s neúspěšnými testy](./media/testing-library-with-visual-studio/failed-test-window.png)

1. <span data-ttu-id="e827b-211">V části **nezdařené testy** vyberte neúspěšný test, `TestDoesNotStartWith`.</span><span class="sxs-lookup"><span data-stu-id="e827b-211">In the **Failed Tests** section, select the failed test, `TestDoesNotStartWith`.</span></span> <span data-ttu-id="e827b-212">V okně **Průzkumník testů** se zobrazí zpráva vytvořená pomocí kontrolního výrazu: Výraz Assert. NEPRAVDA se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="e827b-212">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="e827b-213">Očekávané pro ' error ': false; provedené True ".</span><span class="sxs-lookup"><span data-stu-id="e827b-213">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="e827b-214">Z důvodu chyby nebyly testovány všechny řetězce v poli za "Error".</span><span class="sxs-lookup"><span data-stu-id="e827b-214">Because of the failure, all strings in the array after "Error" were not tested.</span></span>

   ![Okno Průzkumníka testů, které zobrazuje nepravdivé selhání kontrolního výrazu](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. <span data-ttu-id="e827b-216">Vraťte změny, které jste provedli v kroku 1, a odeberte řetězec "Error" (chyba).</span><span class="sxs-lookup"><span data-stu-id="e827b-216">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="e827b-217">Spusťte test znovu a testy se budou předávat.</span><span class="sxs-lookup"><span data-stu-id="e827b-217">Rerun the test and the tests will pass.</span></span>

## <a name="testing-the-release-version-of-the-library"></a><span data-ttu-id="e827b-218">Testování verze pro vydání knihovny</span><span class="sxs-lookup"><span data-stu-id="e827b-218">Testing the Release version of the library</span></span>

<span data-ttu-id="e827b-219">Spustili jste testy pro ladicí verzi knihovny.</span><span class="sxs-lookup"><span data-stu-id="e827b-219">You've been running your tests against the Debug version of the library.</span></span> <span data-ttu-id="e827b-220">Nyní, když testy úspěšně prošly a jste dostatečně otestovali knihovnu, měli byste spustit testy dodatečně na sestavení vydaných verzí knihovny.</span><span class="sxs-lookup"><span data-stu-id="e827b-220">Now that your tests have all passed and you've adequately tested your library, you should run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="e827b-221">Několik faktorů, včetně optimalizací kompilátoru, může někdy způsobit různé chování mezi sestaveními ladění a vydání.</span><span class="sxs-lookup"><span data-stu-id="e827b-221">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="e827b-222">Testování sestavení pro vydání:</span><span class="sxs-lookup"><span data-stu-id="e827b-222">To test the Release build:</span></span>

1. <span data-ttu-id="e827b-223">Na panelu nástrojů sady Visual Studio změňte konfiguraci sestavení z **ladit** na **release**.</span><span class="sxs-lookup"><span data-stu-id="e827b-223">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   ![Panel nástrojů sady Visual Studio s zvýrazněným sestavením pro vydání](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="e827b-225">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **StringLibrary** a vyberte **sestavení** z místní nabídky pro rekompilaci knihovny.</span><span class="sxs-lookup"><span data-stu-id="e827b-225">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   ![Místní nabídka StringLibrary s příkazem Build](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. <span data-ttu-id="e827b-227">Spusťte testy jednotek výběrem možnosti **test** > **Spustit** > **všechny testy** z řádku nabídek.</span><span class="sxs-lookup"><span data-stu-id="e827b-227">Run the unit tests by choosing **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="e827b-228">Testy jsou passované.</span><span class="sxs-lookup"><span data-stu-id="e827b-228">The tests pass.</span></span>

<span data-ttu-id="e827b-229">Teď, když jste dokončili testování knihovny, je dalším krokem zpřístupnění volajícím.</span><span class="sxs-lookup"><span data-stu-id="e827b-229">Now that you've finished testing your library, the next step is to make it available to callers.</span></span> <span data-ttu-id="e827b-230">Můžete ho seskupit s jednou nebo více aplikacemi nebo ho můžete distribuovat jako balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="e827b-230">You can bundle it with one or more applications, or you can distribute it as a NuGet package.</span></span> <span data-ttu-id="e827b-231">Další informace naleznete v tématu [spotřebovávání knihovny tříd .NET Standard](./consuming-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="e827b-231">For more information, see [Consuming a .NET Standard Class Library](./consuming-library-with-visual-studio.md).</span></span>

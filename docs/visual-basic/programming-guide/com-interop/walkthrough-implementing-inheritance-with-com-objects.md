---
title: 'Návod: Implementace dědičnosti s objekty modelu COM (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: a1c1b7c247d3277c6614a4774395650c4c069c2f
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929995"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="c74a1-102">Návod: Implementace dědičnosti s objekty modelu COM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c74a1-102">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>
<span data-ttu-id="c74a1-103">Lze odvodit třídy jazyka Visual Basic z `Public` třídy v objektech COM, včetně těch, které jsou vytvořeny v dřívějších verzích jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c74a1-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of Visual Basic.</span></span> <span data-ttu-id="c74a1-104">Vlastnosti a metody třídy dědí od objektů COM může přepsat nebo přetížené stejně jako vlastnosti a metody jiné základní třídy lze přepsat nebo přetížené.</span><span class="sxs-lookup"><span data-stu-id="c74a1-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="c74a1-105">Dědičnost z objektů COM je užitečné, pokud máte existující knihovny tříd, které nechcete, aby se musela kompilovat.</span><span class="sxs-lookup"><span data-stu-id="c74a1-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>  
  
 <span data-ttu-id="c74a1-106">Následující postup ukazuje, jak pomocí jazyka Visual Basic 6.0 můžete vytvořit objekt modelu COM, který obsahuje třídu a pak použít jako základní třídu.</span><span class="sxs-lookup"><span data-stu-id="c74a1-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="c74a1-107">K vytvoření objektu COM, který se používá v tomto názorném postupu</span><span class="sxs-lookup"><span data-stu-id="c74a1-107">To build the COM object that is used in this walkthrough</span></span>  
  
1.  <span data-ttu-id="c74a1-108">V jazyce Visual Basic 6.0 otevřete nový projekt knihovny DLL ActiveX.</span><span class="sxs-lookup"><span data-stu-id="c74a1-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="c74a1-109">Projekt s názvem `Project1` se vytvoří.</span><span class="sxs-lookup"><span data-stu-id="c74a1-109">A project named `Project1` is created.</span></span> <span data-ttu-id="c74a1-110">Obsahuje třídu s názvem `Class1`.</span><span class="sxs-lookup"><span data-stu-id="c74a1-110">It has a class named `Class1`.</span></span>  
  
2.  <span data-ttu-id="c74a1-111">V **Project Exploreru**, klikněte pravým tlačítkem na **Project1**a potom klikněte na tlačítko **Project1 vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="c74a1-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="c74a1-112">**Vlastnosti projektu** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="c74a1-112">The **Project Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="c74a1-113">Na **Obecné** karty **vlastnosti projektu** dialogové okno pole, změňte název projektu tak, že zadáte `ComObject1` v **název projektu** pole.</span><span class="sxs-lookup"><span data-stu-id="c74a1-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>  
  
4.  <span data-ttu-id="c74a1-114">V **Project Exploreru**, klikněte pravým tlačítkem na `Class1`a potom klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="c74a1-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="c74a1-115">**Vlastnosti** se zobrazí okno pro třídu.</span><span class="sxs-lookup"><span data-stu-id="c74a1-115">The **Properties** window for the class is displayed.</span></span>  
  
5.  <span data-ttu-id="c74a1-116">Změnit `Name` vlastnost `MathFunctions`.</span><span class="sxs-lookup"><span data-stu-id="c74a1-116">Change the `Name` property to `MathFunctions`.</span></span>  
  
6.  <span data-ttu-id="c74a1-117">V **Project Exploreru**, klikněte pravým tlačítkem na `MathFunctions`a potom klikněte na tlačítko **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="c74a1-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="c74a1-118">**Editor kódu** se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="c74a1-118">The **Code Editor** is displayed.</span></span>  
  
7.  <span data-ttu-id="c74a1-119">Přidáte místní proměnnou pro uchování hodnoty vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="c74a1-119">Add a local variable to hold the property value:</span></span>  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  <span data-ttu-id="c74a1-120">Přidat vlastnost `Let` a vlastnost `Get` procedury vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="c74a1-120">Add Property `Let` and Property `Get` property procedures:</span></span>  
  
    ```  
    Public Property Let Prop1(ByVal vData As Integer)  
       'Used when assigning a value to the property.  
       mvarProp1 = vData  
    End Property  
    Public Property Get Prop1() As Integer  
       'Used when retrieving a property's value.  
       Prop1 = mvarProp1  
    End Property  
    ```  
  
9. <span data-ttu-id="c74a1-121">Přidání funkce:</span><span class="sxs-lookup"><span data-stu-id="c74a1-121">Add a function:</span></span>  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. <span data-ttu-id="c74a1-122">Vytvoření a registrace objektu COM kliknutím **zkontrolujte ComObject1.dll** na **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="c74a1-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c74a1-123">I když můžete také zveřejnit třídy vytvořené pomocí jazyka Visual Basic jako objekt modelu COM, není objekt modelu COM true a nelze použít v tomto názorném postupu.</span><span class="sxs-lookup"><span data-stu-id="c74a1-123">Although you can also expose a class created with Visual Basic as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="c74a1-124">Podrobnosti najdete v tématu [interoperabilita modelů COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="c74a1-124">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="interop-assemblies"></a><span data-ttu-id="c74a1-125">Sestavení vzájemné spolupráce</span><span class="sxs-lookup"><span data-stu-id="c74a1-125">Interop Assemblies</span></span>  
 <span data-ttu-id="c74a1-126">V následujícím postupu vytvoříte definiční sestavení, která funguje jako most mezi nespravovaný kód (například objekt modelu COM) a spravovaný kód, který používá Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c74a1-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code Visual Studio uses.</span></span> <span data-ttu-id="c74a1-127">Sestavení vzájemné spolupráce, který vytvoří jazyka Visual Basic zpracovává řadu podrobnosti o práci s objekty COM, například *zařazování spolupráce*, proces balení parametry a návratové hodnoty do ekvivalentní datové typy při přechodu a od objektů COM.</span><span class="sxs-lookup"><span data-stu-id="c74a1-127">The interop assembly that Visual Basic creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="c74a1-128">Odkaz v aplikaci Visual Basic odkazuje na sestavení vzájemné spolupráce, nikoli skutečný objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="c74a1-128">The reference in the Visual Basic application points to the interop assembly, not the actual COM object.</span></span>  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="c74a1-129">Objekt modelu COM pomocí jazyka Visual Basic 2005 a novějších verzích</span><span class="sxs-lookup"><span data-stu-id="c74a1-129">To use a COM object with Visual Basic 2005 and later versions</span></span>  
  
1.  <span data-ttu-id="c74a1-130">Otevřete nový projekt aplikace Windows jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c74a1-130">Open a new Visual Basic Windows Application project.</span></span>  
  
2.  <span data-ttu-id="c74a1-131">Na **projektu** nabídky, klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="c74a1-131">On the **Project** menu, click **Add Reference**.</span></span>  
  
     <span data-ttu-id="c74a1-132">**Přidat odkaz** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="c74a1-132">The **Add Reference** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="c74a1-133">Na **COM** kartu, dvakrát klikněte na panel `ComObject1` v **název komponenty** seznamu a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="c74a1-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>  
  
4.  <span data-ttu-id="c74a1-134">Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="c74a1-134">On the **Project** menu, click **Add New Item**.</span></span>  
  
     <span data-ttu-id="c74a1-135">**Přidat novou položku** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="c74a1-135">The **Add New Item** dialog box is displayed.</span></span>  
  
5.  <span data-ttu-id="c74a1-136">V **šablony** podokně klikněte na tlačítko **třídy**.</span><span class="sxs-lookup"><span data-stu-id="c74a1-136">In the **Templates** pane, click **Class**.</span></span>  
  
     <span data-ttu-id="c74a1-137">Výchozí název souboru `Class1.vb`, zobrazí se v **název** pole.</span><span class="sxs-lookup"><span data-stu-id="c74a1-137">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="c74a1-138">Toto pole MathClass.vb a kliknutím na tlačítko Změnit **přidat**.</span><span class="sxs-lookup"><span data-stu-id="c74a1-138">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="c74a1-139">Tím se vytvoří třídu s názvem `MathClass`a zobrazí jeho kód.</span><span class="sxs-lookup"><span data-stu-id="c74a1-139">This creates a class named `MathClass`, and displays its code.</span></span>  
  
6.  <span data-ttu-id="c74a1-140">Přidejte následující kód k hornímu okraji `MathClass` dědit ze třídy modelu COM.</span><span class="sxs-lookup"><span data-stu-id="c74a1-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>  
  
     [!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]  
  
7.  <span data-ttu-id="c74a1-141">Přetížení veřejnou metodu základní třídy přidáním následujícího kódu `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="c74a1-141">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>  
  
     [!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]  
  
8.  <span data-ttu-id="c74a1-142">Zděděné třídy rozšířit přidáním následujícího kódu `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="c74a1-142">Extend the inherited class by adding the following code to `MathClass`:</span></span>  
  
     [!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]  
  
 <span data-ttu-id="c74a1-143">Nová třída dědí vlastnosti ze základní třídy objektu COM, přetížení metody a definuje novou metodu rozšíření třídy.</span><span class="sxs-lookup"><span data-stu-id="c74a1-143">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>  
  
#### <a name="to-test-the-inherited-class"></a><span data-ttu-id="c74a1-144">Chcete-li testovat zděděné třídy</span><span class="sxs-lookup"><span data-stu-id="c74a1-144">To test the inherited class</span></span>  
  
1.  <span data-ttu-id="c74a1-145">Přidání tlačítka do formuláře při spuštění a pak dvojím kliknutím ho zobrazte jeho kód.</span><span class="sxs-lookup"><span data-stu-id="c74a1-145">Add a button to your startup form, and then double-click it to view its code.</span></span>  
  
2.  <span data-ttu-id="c74a1-146">Na tlačítku `Click` procedury Obslužná rutina události, přidejte následující kód k vytvoření instance `MathClass` a volání přetížené metody:</span><span class="sxs-lookup"><span data-stu-id="c74a1-146">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>  
  
     [!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]  
  
3.  <span data-ttu-id="c74a1-147">Stisknutím klávesy F5 spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="c74a1-147">Run the project by pressing F5.</span></span>  
  
 <span data-ttu-id="c74a1-148">Když kliknete na tlačítko na formuláři `AddNumbers` metoda nejdříve volána s `Short` datového typu čísla, a Visual Basic zvolí vhodné metody ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="c74a1-148">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and Visual Basic chooses the appropriate method from the base class.</span></span> <span data-ttu-id="c74a1-149">Druhé volání `AddNumbers` směřuje na přetížení metody z `MathClass`.</span><span class="sxs-lookup"><span data-stu-id="c74a1-149">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="c74a1-150">Třetí volání volání `SubtractNumbers` metodu, která rozšiřuje třídu.</span><span class="sxs-lookup"><span data-stu-id="c74a1-150">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="c74a1-151">Nastavte vlastnost v základní třídě a hodnota se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="c74a1-151">The property in the base class is set, and the value is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c74a1-152">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c74a1-152">Next Steps</span></span>  
 <span data-ttu-id="c74a1-153">Mohli jste si všimnout, který přetížené `AddNumbers` funkce zřejmě má stejný datový typ jako metody zděděné ze základní třídy objektu COM.</span><span class="sxs-lookup"><span data-stu-id="c74a1-153">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="c74a1-154">Důvodem je, že argumentů a parametrů metody základní třídy jsou definovány jako 16bitová celá čísla v jazyce Visual Basic 6.0, ale jsou vystaveny jako 16bitová celá čísla typu `Short` v pozdějších verzích jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c74a1-154">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="c74a1-155">Nové funkce přijímá 32bitová celá čísla a přetížení funkce základní třídy.</span><span class="sxs-lookup"><span data-stu-id="c74a1-155">The new function accepts 32-bit integers, and overloads the base class function.</span></span>  
  
 <span data-ttu-id="c74a1-156">Při práci s objekty COM, ujistěte se, abyste ověřili velikost a datové typy parametrů.</span><span class="sxs-lookup"><span data-stu-id="c74a1-156">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="c74a1-157">Například při použití objektu COM, který přijímá objekt kolekce jazyka Visual Basic 6.0 jako argument, nelze zadat kolekci z novější verze sady Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c74a1-157">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>  
  
 <span data-ttu-id="c74a1-158">Vlastností a metod zděděných z tříd modelu COM, lze přepsat, což znamená, že je možné deklarovat lokální vlastnost nebo metoda, která se nahradí vlastnost nebo metoda zděděné ze základní třídy modelu COM.</span><span class="sxs-lookup"><span data-stu-id="c74a1-158">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="c74a1-159">Pravidla pro přepsání zděděné vlastnosti modelu COM jsou podobné pravidlům pro přepsání další vlastnosti a metody s následujícími výjimkami:</span><span class="sxs-lookup"><span data-stu-id="c74a1-159">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>  
  
-   <span data-ttu-id="c74a1-160">Pokud přepíšete všechny vlastnosti nebo metody, které dědí z třídy modelu COM, je nutné přepsat všechny ostatní zděděné vlastnosti a metody.</span><span class="sxs-lookup"><span data-stu-id="c74a1-160">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>  
  
-   <span data-ttu-id="c74a1-161">Vlastnosti, které používají `ByRef` parametry nelze přepsat.</span><span class="sxs-lookup"><span data-stu-id="c74a1-161">Properties that use `ByRef` parameters cannot be overridden.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c74a1-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="c74a1-162">See Also</span></span>  
 [<span data-ttu-id="c74a1-163">Interoperabilita modelů COM v aplikacích .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c74a1-163">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [<span data-ttu-id="c74a1-164">Příkaz Inherits</span><span class="sxs-lookup"><span data-stu-id="c74a1-164">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="c74a1-165">Datový typ Short</span><span class="sxs-lookup"><span data-stu-id="c74a1-165">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)

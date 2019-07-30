---
title: 'Návod: Implementace dědičnosti s objekty modelu COM (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: f632df919417c04701727be3e99eb2bf3f6ff1f7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627045"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="e782d-102">Návod: Implementace dědičnosti s objekty modelu COM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e782d-102">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>

<span data-ttu-id="e782d-103">Třídy Visual Basic můžete odvodit ze `Public` tříd v objektech com, a to i těch, které byly vytvořeny v dřívějších verzích Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e782d-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of Visual Basic.</span></span> <span data-ttu-id="e782d-104">Vlastnosti a metody tříd zděděných z objektů COM mohou být přepsány nebo přetíženy stejně jako vlastnosti a metody jakékoli jiné základní třídy mohou být přepsány nebo přetíženy.</span><span class="sxs-lookup"><span data-stu-id="e782d-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="e782d-105">Dědičnost z objektů modelu COM je užitečná v případě, že máte existující knihovnu tříd, kterou nechcete znovu kompilovat.</span><span class="sxs-lookup"><span data-stu-id="e782d-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>

<span data-ttu-id="e782d-106">Následující postup ukazuje, jak použít Visual Basic 6,0 k vytvoření objektu modelu COM, který obsahuje třídu, a jeho následné použití jako základní třídy.</span><span class="sxs-lookup"><span data-stu-id="e782d-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="e782d-107">Vytvoření objektu COM, který je použit v tomto návodu</span><span class="sxs-lookup"><span data-stu-id="e782d-107">To build the COM object that is used in this walkthrough</span></span>

1. <span data-ttu-id="e782d-108">V Visual Basic 6,0 otevřete nový projekt knihovny DLL ActiveX.</span><span class="sxs-lookup"><span data-stu-id="e782d-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="e782d-109">Vytvoří se projekt `Project1` s názvem.</span><span class="sxs-lookup"><span data-stu-id="e782d-109">A project named `Project1` is created.</span></span> <span data-ttu-id="e782d-110">Obsahuje třídu s názvem `Class1`.</span><span class="sxs-lookup"><span data-stu-id="e782d-110">It has a class named `Class1`.</span></span>

2. <span data-ttu-id="e782d-111">V **Průzkumníku projektu**klikněte pravým tlačítkem na **Project1**a pak klikněte na **vlastnosti Project1**.</span><span class="sxs-lookup"><span data-stu-id="e782d-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="e782d-112">Zobrazí se dialogové okno **Vlastnosti projektu** .</span><span class="sxs-lookup"><span data-stu-id="e782d-112">The **Project Properties** dialog box is displayed.</span></span>

3. <span data-ttu-id="e782d-113">Na kartě **Obecné** v dialogovém okně **Vlastnosti projektu** změňte název projektu zadáním `ComObject1` do pole **název projektu** .</span><span class="sxs-lookup"><span data-stu-id="e782d-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>

4. <span data-ttu-id="e782d-114">V **Průzkumníku projektu**klikněte pravým tlačítkem myši `Class1`a pak klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="e782d-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="e782d-115">Zobrazí se okno **vlastnosti** třídy.</span><span class="sxs-lookup"><span data-stu-id="e782d-115">The **Properties** window for the class is displayed.</span></span>

5. <span data-ttu-id="e782d-116">Změňte vlastnost na `MathFunctions`. `Name`</span><span class="sxs-lookup"><span data-stu-id="e782d-116">Change the `Name` property to `MathFunctions`.</span></span>

6. <span data-ttu-id="e782d-117">V **Průzkumníku projektu**klikněte pravým tlačítkem myši `MathFunctions`a pak klikněte na **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="e782d-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="e782d-118">Zobrazí se **Editor kódu** .</span><span class="sxs-lookup"><span data-stu-id="e782d-118">The **Code Editor** is displayed.</span></span>

7. <span data-ttu-id="e782d-119">Přidejte místní proměnnou pro uchování hodnoty vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="e782d-119">Add a local variable to hold the property value:</span></span>

    ```vb
    ' Local variable to hold property value
    Private mvarProp1 As Integer
    ```

8. <span data-ttu-id="e782d-120">Přidat procedury `Let` vlastností vlastností `Get` a vlastností:</span><span class="sxs-lookup"><span data-stu-id="e782d-120">Add Property `Let` and Property `Get` property procedures:</span></span>

    ```vb
    Public Property Let Prop1(ByVal vData As Integer)
       'Used when assigning a value to the property.
       mvarProp1 = vData
    End Property
    Public Property Get Prop1() As Integer
       'Used when retrieving a property's value.
       Prop1 = mvarProp1
    End Property
    ```

9. <span data-ttu-id="e782d-121">Přidejte funkci:</span><span class="sxs-lookup"><span data-stu-id="e782d-121">Add a function:</span></span>

    ```vb
    Function AddNumbers(
       ByVal SomeNumber As Integer,
       ByVal AnotherNumber As Integer) As Integer

       AddNumbers = SomeNumber + AnotherNumber
    End Function
    ```

10. <span data-ttu-id="e782d-122">Vytvořte a zaregistrujte objekt COM kliknutím na příkaz **vytvořit ComObject1. dll** v nabídce **soubor** .</span><span class="sxs-lookup"><span data-stu-id="e782d-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e782d-123">I když můžete vystavit třídu vytvořenou pomocí Visual Basic jako objekt modelu COM, nejedná se o skutečný objekt COM a nelze ji použít v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="e782d-123">Although you can also expose a class created with Visual Basic as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="e782d-124">Podrobnosti najdete v tématu [interoperabilita modelu COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="e782d-124">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>

## <a name="interop-assemblies"></a><span data-ttu-id="e782d-125">Definiční sestavení</span><span class="sxs-lookup"><span data-stu-id="e782d-125">Interop Assemblies</span></span>

<span data-ttu-id="e782d-126">V následujícím postupu vytvoříte definiční sestavení, které funguje jako most mezi nespravovaným kódem (například objektem COM) a spravovaným kódem, který používá Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e782d-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code Visual Studio uses.</span></span> <span data-ttu-id="e782d-127">Definiční sestavení, které Visual Basic vytvoří, zpracovává mnoho podrobností o práci s objekty COM, jako je například *Interop Marshaling*, proces balení parametrů a návratové hodnoty do ekvivalentních datových typů při přesunu do a z objektů com.</span><span class="sxs-lookup"><span data-stu-id="e782d-127">The interop assembly that Visual Basic creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="e782d-128">Odkaz v aplikaci Visual Basic odkazuje na definiční sestavení, nikoli na samotný objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="e782d-128">The reference in the Visual Basic application points to the interop assembly, not the actual COM object.</span></span>

#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="e782d-129">Použití objektu COM s Visual Basic 2005 a novějšími verzemi</span><span class="sxs-lookup"><span data-stu-id="e782d-129">To use a COM object with Visual Basic 2005 and later versions</span></span>

1. <span data-ttu-id="e782d-130">Otevřete nový Visual Basic projekt aplikace systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e782d-130">Open a new Visual Basic Windows Application project.</span></span>

2. <span data-ttu-id="e782d-131">V nabídce **projekt** klikněte na příkaz **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="e782d-131">On the **Project** menu, click **Add Reference**.</span></span>

     <span data-ttu-id="e782d-132">**Přidat odkaz** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e782d-132">The **Add Reference** dialog box is displayed.</span></span>

3. <span data-ttu-id="e782d-133">Na kartě **com** poklikejte na `ComObject1` seznam **název součásti** a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="e782d-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>

4. <span data-ttu-id="e782d-134">V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="e782d-134">On the **Project** menu, click **Add New Item**.</span></span>

     <span data-ttu-id="e782d-135">**Přidat novou položku** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e782d-135">The **Add New Item** dialog box is displayed.</span></span>

5. <span data-ttu-id="e782d-136">V podokně **šablony** klikněte na **Třída**.</span><span class="sxs-lookup"><span data-stu-id="e782d-136">In the **Templates** pane, click **Class**.</span></span>

     <span data-ttu-id="e782d-137">Výchozí název `Class1.vb`souboru se zobrazí v poli **název** .</span><span class="sxs-lookup"><span data-stu-id="e782d-137">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="e782d-138">Změňte toto pole na MathClass. vb a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="e782d-138">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="e782d-139">Tím se vytvoří třída s `MathClass`názvem a zobrazí se její kód.</span><span class="sxs-lookup"><span data-stu-id="e782d-139">This creates a class named `MathClass`, and displays its code.</span></span>

6. <span data-ttu-id="e782d-140">Přidejte následující kód na začátek `MathClass` k dědění z třídy com.</span><span class="sxs-lookup"><span data-stu-id="e782d-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>

     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]

7. <span data-ttu-id="e782d-141">Přetížení veřejné metody základní třídy přidáním následujícího kódu do `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="e782d-141">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>

     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]

8. <span data-ttu-id="e782d-142">Rozšíří zděděnou třídu přidáním následujícího kódu do `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="e782d-142">Extend the inherited class by adding the following code to `MathClass`:</span></span>

     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]

<span data-ttu-id="e782d-143">Nová třída zdědí vlastnosti základní třídy v objektu COM, přetěžuje metodu a definuje novou metodu pro rozšiřování třídy.</span><span class="sxs-lookup"><span data-stu-id="e782d-143">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>

#### <a name="to-test-the-inherited-class"></a><span data-ttu-id="e782d-144">Testování zděděné třídy</span><span class="sxs-lookup"><span data-stu-id="e782d-144">To test the inherited class</span></span>

1. <span data-ttu-id="e782d-145">Přidejte tlačítko do formuláře po spuštění a pak dvakrát klikněte na něj, aby se zobrazil jeho kód.</span><span class="sxs-lookup"><span data-stu-id="e782d-145">Add a button to your startup form, and then double-click it to view its code.</span></span>

2. <span data-ttu-id="e782d-146">V proceduře obslužné rutiny `Click` události tlačítka přidejte následující kód pro vytvoření `MathClass` instance a volání přetížených metod:</span><span class="sxs-lookup"><span data-stu-id="e782d-146">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>

     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]

3. <span data-ttu-id="e782d-147">Spusťte projekt stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="e782d-147">Run the project by pressing F5.</span></span>

<span data-ttu-id="e782d-148">Po kliknutí na tlačítko ve formuláři `AddNumbers` je metoda nejprve volána s `Short` čísly datového typu a Visual Basic zvolí vhodnou metodu ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="e782d-148">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and Visual Basic chooses the appropriate method from the base class.</span></span> <span data-ttu-id="e782d-149">Druhé volání na `AddNumbers` je přesměrováno na metodu přetížení z `MathClass`.</span><span class="sxs-lookup"><span data-stu-id="e782d-149">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="e782d-150">Třetí volání volá `SubtractNumbers` metodu, která rozšiřuje třídu.</span><span class="sxs-lookup"><span data-stu-id="e782d-150">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="e782d-151">Vlastnost v základní třídě je nastavena a zobrazí se hodnota.</span><span class="sxs-lookup"><span data-stu-id="e782d-151">The property in the base class is set, and the value is displayed.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e782d-152">Další kroky</span><span class="sxs-lookup"><span data-stu-id="e782d-152">Next Steps</span></span>

<span data-ttu-id="e782d-153">Možná jste si všimli, že přetížená `AddNumbers` funkce má stejný datový typ jako metoda zděděná od základní třídy objektu com.</span><span class="sxs-lookup"><span data-stu-id="e782d-153">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="e782d-154">Důvodem je, že argumenty a parametry metody základní třídy jsou definovány jako 16bitová celá čísla v Visual Basic 6,0, ale jsou vystavena jako 16bitové celé číslo typu `Short` v pozdějších verzích Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e782d-154">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="e782d-155">Nová funkce přijímá 32 celých čísel a přetěžuje funkci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="e782d-155">The new function accepts 32-bit integers, and overloads the base class function.</span></span>

<span data-ttu-id="e782d-156">Při práci s objekty modelu COM ověřte, zda je nutné ověřit velikost a datové typy parametrů.</span><span class="sxs-lookup"><span data-stu-id="e782d-156">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="e782d-157">Například při použití objektu COM, který přijímá objekt kolekce Visual Basic 6,0 jako argument, nelze poskytnout kolekci z novější verze Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e782d-157">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>

<span data-ttu-id="e782d-158">Vlastnosti a metody zděděné z tříd modelu COM lze přepsat, což znamená, že lze deklarovat místní vlastnost nebo metodu, která nahrazuje vlastnost nebo metodu zděděnou ze základní třídy COM.</span><span class="sxs-lookup"><span data-stu-id="e782d-158">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="e782d-159">Pravidla pro přepsání zděděných vlastností modelu COM jsou podobná pravidlům pro přepsání dalších vlastností a metod s následujícími výjimkami:</span><span class="sxs-lookup"><span data-stu-id="e782d-159">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>

- <span data-ttu-id="e782d-160">Pokud přepíšete jakoukoliv vlastnost nebo metodu děděnou z třídy modelu COM, je nutné přepsat všechny ostatní zděděné vlastnosti a metody.</span><span class="sxs-lookup"><span data-stu-id="e782d-160">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>

- <span data-ttu-id="e782d-161">Vlastnosti, které `ByRef` používají parametry, nelze přepsat.</span><span class="sxs-lookup"><span data-stu-id="e782d-161">Properties that use `ByRef` parameters cannot be overridden.</span></span>

## <a name="see-also"></a><span data-ttu-id="e782d-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e782d-162">See also</span></span>

- [<span data-ttu-id="e782d-163">Interoperabilita modelů COM v aplikacích .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e782d-163">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="e782d-164">Příkaz Inherits</span><span class="sxs-lookup"><span data-stu-id="e782d-164">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="e782d-165">Datový typ Short</span><span class="sxs-lookup"><span data-stu-id="e782d-165">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)

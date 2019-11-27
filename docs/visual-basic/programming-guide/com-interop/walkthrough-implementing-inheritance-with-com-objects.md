---
title: 'Návod: Implementace dědičnosti s objekty modelu COM'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: 209e1005b9f944bf4883e8406031fb17d4d60df1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347984"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="1d7c8-102">Návod: Implementace dědičnosti s objekty modelu COM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d7c8-102">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>

<span data-ttu-id="1d7c8-103">Můžete odvodit Visual Basic třídy z tříd `Public` v objektech COM, i ty, které byly vytvořeny v dřívějších verzích Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of Visual Basic.</span></span> <span data-ttu-id="1d7c8-104">Vlastnosti a metody tříd zděděných z objektů COM mohou být přepsány nebo přetíženy stejně jako vlastnosti a metody jakékoli jiné základní třídy mohou být přepsány nebo přetíženy.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="1d7c8-105">Dědičnost z objektů modelu COM je užitečná v případě, že máte existující knihovnu tříd, kterou nechcete znovu kompilovat.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>

<span data-ttu-id="1d7c8-106">Následující postup ukazuje, jak použít Visual Basic 6,0 k vytvoření objektu modelu COM, který obsahuje třídu, a jeho následné použití jako základní třídy.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="1d7c8-107">Vytvoření objektu COM, který je použit v tomto návodu</span><span class="sxs-lookup"><span data-stu-id="1d7c8-107">To build the COM object that is used in this walkthrough</span></span>

1. <span data-ttu-id="1d7c8-108">V Visual Basic 6,0 otevřete nový projekt knihovny DLL ActiveX.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="1d7c8-109">Vytvoří se projekt s názvem `Project1`.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-109">A project named `Project1` is created.</span></span> <span data-ttu-id="1d7c8-110">Má třídu s názvem `Class1`.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-110">It has a class named `Class1`.</span></span>

2. <span data-ttu-id="1d7c8-111">V **Průzkumníku projektu**klikněte pravým tlačítkem na **Project1**a pak klikněte na **vlastnosti Project1**.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="1d7c8-112">Zobrazí se dialogové okno **Vlastnosti projektu** .</span><span class="sxs-lookup"><span data-stu-id="1d7c8-112">The **Project Properties** dialog box is displayed.</span></span>

3. <span data-ttu-id="1d7c8-113">Na kartě **Obecné** v dialogovém okně **Vlastnosti projektu** změňte název projektu zadáním `ComObject1` do pole **název projektu** .</span><span class="sxs-lookup"><span data-stu-id="1d7c8-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>

4. <span data-ttu-id="1d7c8-114">V **Průzkumníku projektu**klikněte pravým tlačítkem na `Class1`a pak klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="1d7c8-115">Zobrazí se okno **vlastnosti** třídy.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-115">The **Properties** window for the class is displayed.</span></span>

5. <span data-ttu-id="1d7c8-116">Změňte vlastnost `Name` na `MathFunctions`.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-116">Change the `Name` property to `MathFunctions`.</span></span>

6. <span data-ttu-id="1d7c8-117">V **Průzkumníku projektu**klikněte pravým tlačítkem na `MathFunctions`a pak klikněte na **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="1d7c8-118">Zobrazí se **Editor kódu** .</span><span class="sxs-lookup"><span data-stu-id="1d7c8-118">The **Code Editor** is displayed.</span></span>

7. <span data-ttu-id="1d7c8-119">Přidejte místní proměnnou pro uchování hodnoty vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="1d7c8-119">Add a local variable to hold the property value:</span></span>

    ```vb
    ' Local variable to hold property value
    Private mvarProp1 As Integer
    ```

8. <span data-ttu-id="1d7c8-120">Přidat procedury vlastností `Let` a vlastnost `Get` vlastností:</span><span class="sxs-lookup"><span data-stu-id="1d7c8-120">Add Property `Let` and Property `Get` property procedures:</span></span>

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

9. <span data-ttu-id="1d7c8-121">Přidejte funkci:</span><span class="sxs-lookup"><span data-stu-id="1d7c8-121">Add a function:</span></span>

    ```vb
    Function AddNumbers(
       ByVal SomeNumber As Integer,
       ByVal AnotherNumber As Integer) As Integer

       AddNumbers = SomeNumber + AnotherNumber
    End Function
    ```

10. <span data-ttu-id="1d7c8-122">Vytvořte a zaregistrujte objekt COM kliknutím na příkaz **vytvořit ComObject1. dll** v nabídce **soubor** .</span><span class="sxs-lookup"><span data-stu-id="1d7c8-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1d7c8-123">I když můžete vystavit třídu vytvořenou pomocí Visual Basic jako objekt modelu COM, nejedná se o skutečný objekt COM a nelze ji použít v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-123">Although you can also expose a class created with Visual Basic as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="1d7c8-124">Podrobnosti najdete v tématu [interoperabilita modelu COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="1d7c8-124">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>

## <a name="interop-assemblies"></a><span data-ttu-id="1d7c8-125">Definiční sestavení</span><span class="sxs-lookup"><span data-stu-id="1d7c8-125">Interop Assemblies</span></span>

<span data-ttu-id="1d7c8-126">V následujícím postupu vytvoříte definiční sestavení, které funguje jako most mezi nespravovaným kódem (například objektem COM) a spravovaným kódem, který používá Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code Visual Studio uses.</span></span> <span data-ttu-id="1d7c8-127">Definiční sestavení, které Visual Basic vytvoří, zpracovává mnoho podrobností o práci s objekty COM, jako je například *Interop Marshaling*, proces balení parametrů a návratové hodnoty do ekvivalentních datových typů při přesunu do a z objektů com.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-127">The interop assembly that Visual Basic creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="1d7c8-128">Odkaz v aplikaci Visual Basic odkazuje na definiční sestavení, nikoli na samotný objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-128">The reference in the Visual Basic application points to the interop assembly, not the actual COM object.</span></span>

### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="1d7c8-129">Použití objektu COM s Visual Basic 2005 a novějšími verzemi</span><span class="sxs-lookup"><span data-stu-id="1d7c8-129">To use a COM object with Visual Basic 2005 and later versions</span></span>

1. <span data-ttu-id="1d7c8-130">Otevřete nový Visual Basic projekt aplikace systému Windows.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-130">Open a new Visual Basic Windows Application project.</span></span>

2. <span data-ttu-id="1d7c8-131">V nabídce **projekt** klikněte na příkaz **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-131">On the **Project** menu, click **Add Reference**.</span></span>

     <span data-ttu-id="1d7c8-132">Zobrazí se dialogové okno **Přidat odkaz** .</span><span class="sxs-lookup"><span data-stu-id="1d7c8-132">The **Add Reference** dialog box is displayed.</span></span>

3. <span data-ttu-id="1d7c8-133">Na kartě **com** poklikejte na `ComObject1` v seznamu **název součásti** a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>

4. <span data-ttu-id="1d7c8-134">V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-134">On the **Project** menu, click **Add New Item**.</span></span>

     <span data-ttu-id="1d7c8-135">Zobrazí se dialogové okno **Přidat novou položku** .</span><span class="sxs-lookup"><span data-stu-id="1d7c8-135">The **Add New Item** dialog box is displayed.</span></span>

5. <span data-ttu-id="1d7c8-136">V podokně **šablony** klikněte na **Třída**.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-136">In the **Templates** pane, click **Class**.</span></span>

     <span data-ttu-id="1d7c8-137">V poli **název** se zobrazí výchozí název souboru `Class1.vb`.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-137">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="1d7c8-138">Změňte toto pole na MathClass. vb a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-138">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="1d7c8-139">Tím se vytvoří třída s názvem `MathClass`a zobrazí se její kód.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-139">This creates a class named `MathClass`, and displays its code.</span></span>

6. <span data-ttu-id="1d7c8-140">Přidejte následující kód na začátek `MathClass` k dědění z třídy COM.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>

     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]

7. <span data-ttu-id="1d7c8-141">Přetížení veřejné metody základní třídy přidáním následujícího kódu do `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="1d7c8-141">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>

     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]

8. <span data-ttu-id="1d7c8-142">Rozšíří zděděnou třídu přidáním následujícího kódu do `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="1d7c8-142">Extend the inherited class by adding the following code to `MathClass`:</span></span>

     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]

<span data-ttu-id="1d7c8-143">Nová třída zdědí vlastnosti základní třídy v objektu COM, přetěžuje metodu a definuje novou metodu pro rozšiřování třídy.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-143">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>

### <a name="to-test-the-inherited-class"></a><span data-ttu-id="1d7c8-144">Testování zděděné třídy</span><span class="sxs-lookup"><span data-stu-id="1d7c8-144">To test the inherited class</span></span>

1. <span data-ttu-id="1d7c8-145">Přidejte tlačítko do formuláře po spuštění a pak dvakrát klikněte na něj, aby se zobrazil jeho kód.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-145">Add a button to your startup form, and then double-click it to view its code.</span></span>

2. <span data-ttu-id="1d7c8-146">V proceduře obslužné rutiny události `Click` tlačítka přidejte následující kód k vytvoření instance `MathClass` a volání přetížených metod:</span><span class="sxs-lookup"><span data-stu-id="1d7c8-146">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>

     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]

3. <span data-ttu-id="1d7c8-147">Spusťte projekt stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-147">Run the project by pressing F5.</span></span>

<span data-ttu-id="1d7c8-148">Když kliknete na tlačítko ve formuláři, metoda `AddNumbers` je nejprve volána s `Short`mi čísly datových typů a Visual Basic zvolí odpovídající metodu ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-148">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and Visual Basic chooses the appropriate method from the base class.</span></span> <span data-ttu-id="1d7c8-149">Druhé volání `AddNumbers` je směrováno na metodu přetížení z `MathClass`.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-149">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="1d7c8-150">Třetí volání volá metodu `SubtractNumbers`, která rozšiřuje třídu.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-150">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="1d7c8-151">Vlastnost v základní třídě je nastavena a zobrazí se hodnota.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-151">The property in the base class is set, and the value is displayed.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1d7c8-152">Další kroky</span><span class="sxs-lookup"><span data-stu-id="1d7c8-152">Next Steps</span></span>

<span data-ttu-id="1d7c8-153">Možná jste si všimli, že přetížená funkce `AddNumbers` pravděpodobně má stejný datový typ jako metoda zděděná od základní třídy objektu COM.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-153">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="1d7c8-154">Důvodem je, že argumenty a parametry metody základní třídy jsou definovány jako 16bitová celá čísla v Visual Basic 6,0, ale jsou vystavena jako 16bitové celé číslo typu `Short` v pozdějších verzích Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-154">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="1d7c8-155">Nová funkce přijímá 32 celých čísel a přetěžuje funkci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-155">The new function accepts 32-bit integers, and overloads the base class function.</span></span>

<span data-ttu-id="1d7c8-156">Při práci s objekty modelu COM ověřte, zda je nutné ověřit velikost a datové typy parametrů.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-156">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="1d7c8-157">Například při použití objektu COM, který přijímá objekt kolekce Visual Basic 6,0 jako argument, nelze poskytnout kolekci z novější verze Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-157">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>

<span data-ttu-id="1d7c8-158">Vlastnosti a metody zděděné z tříd modelu COM lze přepsat, což znamená, že lze deklarovat místní vlastnost nebo metodu, která nahrazuje vlastnost nebo metodu zděděnou ze základní třídy COM.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-158">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="1d7c8-159">Pravidla pro přepsání zděděných vlastností modelu COM jsou podobná pravidlům pro přepsání dalších vlastností a metod s následujícími výjimkami:</span><span class="sxs-lookup"><span data-stu-id="1d7c8-159">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>

- <span data-ttu-id="1d7c8-160">Pokud přepíšete jakoukoliv vlastnost nebo metodu děděnou z třídy modelu COM, je nutné přepsat všechny ostatní zděděné vlastnosti a metody.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-160">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>

- <span data-ttu-id="1d7c8-161">Vlastnosti, které používají `ByRef` parametry, nelze přepsat.</span><span class="sxs-lookup"><span data-stu-id="1d7c8-161">Properties that use `ByRef` parameters cannot be overridden.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d7c8-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d7c8-162">See also</span></span>

- [<span data-ttu-id="1d7c8-163">Interoperabilita modelů COM v aplikacích .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1d7c8-163">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="1d7c8-164">Příkaz Inherits</span><span class="sxs-lookup"><span data-stu-id="1d7c8-164">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="1d7c8-165">Datový typ Short</span><span class="sxs-lookup"><span data-stu-id="1d7c8-165">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)

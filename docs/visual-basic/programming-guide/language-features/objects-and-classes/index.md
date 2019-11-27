---
title: Objekty a třídy
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: d45aca8b137f56cf058b63b9286504259c0005eb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346702"
---
# <a name="objects-and-classes-in-visual-basic"></a><span data-ttu-id="d7408-102">Objekty a třídy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d7408-102">Objects and classes in Visual Basic</span></span>

<span data-ttu-id="d7408-103">*Objekt* je kombinací kódu a dat, která lze považovat za jednotku.</span><span class="sxs-lookup"><span data-stu-id="d7408-103">An *object* is a combination of code and data that can be treated as a unit.</span></span> <span data-ttu-id="d7408-104">Objekt může být částí aplikace, například ovládacím prvkem nebo formulářem.</span><span class="sxs-lookup"><span data-stu-id="d7408-104">An object can be a piece of an application, like a control or a form.</span></span> <span data-ttu-id="d7408-105">Celá aplikace může být také objekt.</span><span class="sxs-lookup"><span data-stu-id="d7408-105">An entire application can also be an object.</span></span>

<span data-ttu-id="d7408-106">Při vytváření aplikace v Visual Basic stále pracujete s objekty.</span><span class="sxs-lookup"><span data-stu-id="d7408-106">When you create an application in Visual Basic, you constantly work with objects.</span></span> <span data-ttu-id="d7408-107">Můžete použít objekty poskytované Visual Basic, jako jsou ovládací prvky, formuláře a objekty pro přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="d7408-107">You can use objects provided by Visual Basic, such as controls, forms, and data access objects.</span></span> <span data-ttu-id="d7408-108">Můžete také použít objekty z jiných aplikací v rámci aplikace Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d7408-108">You can also use objects from other applications within your Visual Basic application.</span></span> <span data-ttu-id="d7408-109">Můžete dokonce vytvořit vlastní objekty a definovat další vlastnosti a metody pro ně.</span><span class="sxs-lookup"><span data-stu-id="d7408-109">You can even create your own objects and define additional properties and methods for them.</span></span> <span data-ttu-id="d7408-110">Objekty fungují jako Prefabrikované stavební bloky pro programy – umožňují napsat kód jen jednou a opakovaně ho používat.</span><span class="sxs-lookup"><span data-stu-id="d7408-110">Objects act like prefabricated building blocks for programs — they let you write a piece of code once and reuse it over and over.</span></span>

<span data-ttu-id="d7408-111">V tomto tématu jsou podrobněji popsány objekty.</span><span class="sxs-lookup"><span data-stu-id="d7408-111">This topic discusses objects in detail.</span></span>

## <a name="objects-and-classes"></a><span data-ttu-id="d7408-112">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="d7408-112">Objects and classes</span></span>

<span data-ttu-id="d7408-113">Každý objekt v Visual Basic je definován *třídou*.</span><span class="sxs-lookup"><span data-stu-id="d7408-113">Each object in Visual Basic is defined by a *class*.</span></span> <span data-ttu-id="d7408-114">Třída popisuje proměnné, vlastnosti, procedury a události objektu.</span><span class="sxs-lookup"><span data-stu-id="d7408-114">A class describes the variables, properties, procedures, and events of an object.</span></span> <span data-ttu-id="d7408-115">Objekty jsou instance třídy; Po definování třídy můžete vytvořit tolik objektů, kolik potřebujete.</span><span class="sxs-lookup"><span data-stu-id="d7408-115">Objects are instances of classes; you can create as many objects you need once you have defined a class.</span></span>

<span data-ttu-id="d7408-116">Pro pochopení vztahu mezi objektem a jeho třídou si můžete představit ořezávání souborů cookie a soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="d7408-116">To understand the relationship between an object and its class, think of cookie cutters and cookies.</span></span> <span data-ttu-id="d7408-117">Ořezávání souborů cookie je třída.</span><span class="sxs-lookup"><span data-stu-id="d7408-117">The cookie cutter is the class.</span></span> <span data-ttu-id="d7408-118">Definuje charakteristiky jednotlivých souborů cookie, například velikost a tvar.</span><span class="sxs-lookup"><span data-stu-id="d7408-118">It defines the characteristics of each cookie, for example size and shape.</span></span> <span data-ttu-id="d7408-119">Třída se používá k vytvoření objektů.</span><span class="sxs-lookup"><span data-stu-id="d7408-119">The class is used to create objects.</span></span> <span data-ttu-id="d7408-120">Objekty jsou soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="d7408-120">The objects are the cookies.</span></span>

<span data-ttu-id="d7408-121">Objekt je nutné vytvořit před tím, než budete moci získat přístup k jeho členům.</span><span class="sxs-lookup"><span data-stu-id="d7408-121">You must create an object before you can access its members.</span></span>

### <a name="to-create-an-object-from-a-class"></a><span data-ttu-id="d7408-122">Vytvoření objektu z třídy</span><span class="sxs-lookup"><span data-stu-id="d7408-122">To create an object from a class</span></span>

1. <span data-ttu-id="d7408-123">Určete, ze které třídy chcete vytvořit objekt.</span><span class="sxs-lookup"><span data-stu-id="d7408-123">Determine from which class you want to create an object.</span></span>

2. <span data-ttu-id="d7408-124">Zápis [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) pro vytvoření proměnné, ke které můžete přiřadit instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="d7408-124">Write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to create a variable to which you can assign a class instance.</span></span> <span data-ttu-id="d7408-125">Proměnná by měla být typu požadované třídy.</span><span class="sxs-lookup"><span data-stu-id="d7408-125">The variable should be of the type of the desired class.</span></span>

   ```vb
   Dim nextCustomer As customer
   ```

3. <span data-ttu-id="d7408-126">Přidejte klíčové slovo [New operator](../../../../visual-basic/language-reference/operators/new-operator.md) pro inicializaci proměnné na novou instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="d7408-126">Add the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword to initialize the variable to a new instance of the class.</span></span>

   ```vb
   Dim nextCustomer As New customer
   ```

4. <span data-ttu-id="d7408-127">Nyní můžete přistupovat ke členům třídy přes proměnnou objektu.</span><span class="sxs-lookup"><span data-stu-id="d7408-127">You can now access the members of the class through the object variable.</span></span>

   ```vb
   nextCustomer.accountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> <span data-ttu-id="d7408-128">Kdykoli je to možné, měli byste deklarovat proměnnou, která má být typu třídy, který chcete přiřadit.</span><span class="sxs-lookup"><span data-stu-id="d7408-128">Whenever possible, you should declare the variable to be of the class type you intend to assign to it.</span></span> <span data-ttu-id="d7408-129">Tato metoda se nazývá *časná vazba*.</span><span class="sxs-lookup"><span data-stu-id="d7408-129">This is called *early binding*.</span></span> <span data-ttu-id="d7408-130">Pokud neznáte typ třídy v době kompilace, můžete vyvolat *pozdní vazbu* tím, že deklarujete proměnnou, která má být [datového typu objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="d7408-130">If you don't know the class type at compile time, you can invoke *late binding* by declaring the variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="d7408-131">Pozdní vazba ale může snížit výkon a omezit přístup k členům objektu run-time.</span><span class="sxs-lookup"><span data-stu-id="d7408-131">However, late binding can make performance slower and limit access to the run-time object's members.</span></span> <span data-ttu-id="d7408-132">Další informace naleznete v tématu [deklarace objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="d7408-132">For more information, see [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).</span></span>

### <a name="multiple-instances"></a><span data-ttu-id="d7408-133">Více instancí</span><span class="sxs-lookup"><span data-stu-id="d7408-133">Multiple instances</span></span>

<span data-ttu-id="d7408-134">Objekty nově vytvořené z třídy jsou často identické.</span><span class="sxs-lookup"><span data-stu-id="d7408-134">Objects newly created from a class are often identical to each other.</span></span> <span data-ttu-id="d7408-135">Jakmile však existují jako jednotlivé objekty, jejich proměnné a vlastnosti lze změnit nezávisle na ostatních instancích.</span><span class="sxs-lookup"><span data-stu-id="d7408-135">Once they exist as individual objects, however, their variables and properties can be changed independently of the other instances.</span></span> <span data-ttu-id="d7408-136">Například pokud přidáte tři zaškrtávací políčka do formuláře, každé zaškrtávací políčko objekt je instancí třídy <xref:System.Windows.Forms.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="d7408-136">For example, if you add three check boxes to a form, each check box object is an instance of the <xref:System.Windows.Forms.CheckBox> class.</span></span> <span data-ttu-id="d7408-137">Jednotlivé <xref:System.Windows.Forms.CheckBox> objekty sdílejí společnou sadu vlastností a schopností (vlastnosti, proměnné, procedury a události) definované třídou.</span><span class="sxs-lookup"><span data-stu-id="d7408-137">The individual <xref:System.Windows.Forms.CheckBox> objects share a common set of characteristics and capabilities (properties, variables, procedures, and events) defined by the class.</span></span> <span data-ttu-id="d7408-138">Každý má však vlastní název, může být samostatně povolen a zakázán a může být umístěn v jiném umístění ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="d7408-138">However, each has its own name, can be separately enabled and disabled, and can be placed in a different location on the form.</span></span>

## <a name="object-members"></a><span data-ttu-id="d7408-139">Členy objektu</span><span class="sxs-lookup"><span data-stu-id="d7408-139">Object members</span></span>

<span data-ttu-id="d7408-140">Objekt je prvek aplikace, který představuje *instanci* třídy.</span><span class="sxs-lookup"><span data-stu-id="d7408-140">An object is an element of an application, representing an *instance* of a class.</span></span> <span data-ttu-id="d7408-141">Pole, vlastnosti, metody a události jsou stavebními bloky objektů a tvoří jejich *členy*.</span><span class="sxs-lookup"><span data-stu-id="d7408-141">Fields, properties, methods, and events are the building blocks of objects and constitute their *members*.</span></span>

### <a name="member-access"></a><span data-ttu-id="d7408-142">Přístup ke členu</span><span class="sxs-lookup"><span data-stu-id="d7408-142">Member Access</span></span>

<span data-ttu-id="d7408-143">Ke členu objektu přistupujete zadáním, v pořadí, názvu proměnné objektu, tečkou (`.`) a názvem člena.</span><span class="sxs-lookup"><span data-stu-id="d7408-143">You access a member of an object by specifying, in order, the name of the object variable, a period (`.`), and the name of the member.</span></span> <span data-ttu-id="d7408-144">Následující příklad nastaví vlastnost <xref:System.Windows.Forms.Control.Text%2A> objektu <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="d7408-144">The following example sets the <xref:System.Windows.Forms.Control.Text%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a><span data-ttu-id="d7408-145">Seznam členů IntelliSense</span><span class="sxs-lookup"><span data-stu-id="d7408-145">IntelliSense listing of members</span></span>

<span data-ttu-id="d7408-146">IntelliSense Vypíše členy třídy při vyvolání možnosti seznamu členů, například při zadání tečky (`.`) jako operátoru přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="d7408-146">IntelliSense lists members of a class when you invoke its List Members option, for example when you type a period (`.`) as a member-access operator.</span></span> <span data-ttu-id="d7408-147">Zadáte-li období za názvem proměnné deklarované jako instance této třídy, technologie IntelliSense Vypíše všechny členy instance a žádné sdílené členy.</span><span class="sxs-lookup"><span data-stu-id="d7408-147">If you type the period following the name of a variable declared as an instance of that class, IntelliSense lists all the instance members and none of the shared members.</span></span> <span data-ttu-id="d7408-148">Zadáte-li období za samotný název třídy, IntelliSense zobrazí seznam všech sdílených členů a žádné členy instance.</span><span class="sxs-lookup"><span data-stu-id="d7408-148">If you type the period following the class name itself, IntelliSense lists all the shared members and none of the instance members.</span></span> <span data-ttu-id="d7408-149">Další informace najdete v tématu [použití technologie IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="d7408-149">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>

### <a name="fields-and-properties"></a><span data-ttu-id="d7408-150">Pole a vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d7408-150">Fields and properties</span></span>

<span data-ttu-id="d7408-151">*Pole* a *vlastnosti* reprezentují informace uložené v objektu.</span><span class="sxs-lookup"><span data-stu-id="d7408-151">*Fields* and *properties* represent information stored in an object.</span></span> <span data-ttu-id="d7408-152">Hodnoty s příkazy přiřazení se načítají a nastavují stejným způsobem jako při načítání a nastavení místních proměnných v proceduře.</span><span class="sxs-lookup"><span data-stu-id="d7408-152">You retrieve and set their values with assignment statements the same way you retrieve and set local variables in a procedure.</span></span> <span data-ttu-id="d7408-153">Následující příklad načte vlastnost <xref:System.Windows.Forms.Control.Width%2A> a nastaví vlastnost <xref:System.Windows.Forms.Control.ForeColor%2A> objektu <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="d7408-153">The following example retrieves the <xref:System.Windows.Forms.Control.Width%2A> property and sets the <xref:System.Windows.Forms.Control.ForeColor%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

<span data-ttu-id="d7408-154">Všimněte si, že pole se také nazývá *členská proměnná*.</span><span class="sxs-lookup"><span data-stu-id="d7408-154">Note that a field is also called a *member variable*.</span></span>

<span data-ttu-id="d7408-155">Procedury vlastností použijte v těchto případech:</span><span class="sxs-lookup"><span data-stu-id="d7408-155">Use property procedures when:</span></span>

- <span data-ttu-id="d7408-156">Musíte určit, kdy a jak má být hodnota nastavena nebo načtena.</span><span class="sxs-lookup"><span data-stu-id="d7408-156">You need to control when and how a value is set or retrieved.</span></span>

- <span data-ttu-id="d7408-157">Vlastnost má dobře definovanou sadu hodnot, které je třeba ověřit.</span><span class="sxs-lookup"><span data-stu-id="d7408-157">The property has a well-defined set of values that need to be validated.</span></span>

- <span data-ttu-id="d7408-158">Nastavením hodnoty dojde k některému znatelnému změně stavu objektu, jako je například vlastnost `IsVisible`.</span><span class="sxs-lookup"><span data-stu-id="d7408-158">Setting the value causes some perceptible change in the object's state, such as an `IsVisible` property.</span></span>

- <span data-ttu-id="d7408-159">Nastavení vlastnosti způsobí změny jiných interních proměnných nebo hodnot jiných vlastností.</span><span class="sxs-lookup"><span data-stu-id="d7408-159">Setting the property causes changes to other internal variables or to the values of other properties.</span></span>

- <span data-ttu-id="d7408-160">Aby bylo možné nastavit nebo načíst vlastnost, je nutné provést sadu kroků.</span><span class="sxs-lookup"><span data-stu-id="d7408-160">A set of steps must be performed before the property can be set or retrieved.</span></span>

<span data-ttu-id="d7408-161">Pole použijte, když:</span><span class="sxs-lookup"><span data-stu-id="d7408-161">Use fields when:</span></span>

- <span data-ttu-id="d7408-162">Hodnota je typu ověřování při samostatném ověřování.</span><span class="sxs-lookup"><span data-stu-id="d7408-162">The value is of a self-validating type.</span></span> <span data-ttu-id="d7408-163">Například chyba nebo automatický převod dat nastane, pokud je jiná hodnota než `True` nebo `False` přiřazena k proměnné `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="d7408-163">For example, an error or automatic data conversion occurs if a value other than `True` or `False` is assigned to a `Boolean` variable.</span></span>

- <span data-ttu-id="d7408-164">Platná je libovolná hodnota rozsahu podporovaná datovým typem.</span><span class="sxs-lookup"><span data-stu-id="d7408-164">Any value in the range supported by the data type is valid.</span></span> <span data-ttu-id="d7408-165">To platí pro mnoho vlastností typu `Single` nebo `Double`.</span><span class="sxs-lookup"><span data-stu-id="d7408-165">This is true of many properties of type `Single` or `Double`.</span></span>

- <span data-ttu-id="d7408-166">Vlastnost je `String` datový typ a neexistuje žádné omezení velikosti nebo hodnoty řetězce.</span><span class="sxs-lookup"><span data-stu-id="d7408-166">The property is a `String` data type, and there is no constraint on the size or value of the string.</span></span>

- <span data-ttu-id="d7408-167">Další informace naleznete v tématu [procedury vlastností](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d7408-167">For more information, see [Property Procedures](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span></span>

### <a name="methods"></a><span data-ttu-id="d7408-168">Metody</span><span class="sxs-lookup"><span data-stu-id="d7408-168">Methods</span></span>

<span data-ttu-id="d7408-169">*Metoda* je akce, kterou může objekt provádět.</span><span class="sxs-lookup"><span data-stu-id="d7408-169">A *method* is an action that an object can perform.</span></span> <span data-ttu-id="d7408-170"><xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> je například metoda objektu <xref:System.Windows.Forms.ComboBox>, která přidá novou položku do pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="d7408-170">For example, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> is a method of the <xref:System.Windows.Forms.ComboBox> object that adds a new entry to a combo box.</span></span>

<span data-ttu-id="d7408-171">Následující příklad ukazuje metodu <xref:System.Windows.Forms.Timer.Start%2A> objektu <xref:System.Windows.Forms.Timer>.</span><span class="sxs-lookup"><span data-stu-id="d7408-171">The following example demonstrates the <xref:System.Windows.Forms.Timer.Start%2A> method of a <xref:System.Windows.Forms.Timer> object.</span></span>

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

<span data-ttu-id="d7408-172">Všimněte si, že metoda je jednoduše *procedurou* , která je vystavena objektem.</span><span class="sxs-lookup"><span data-stu-id="d7408-172">Note that a method is simply a *procedure* that is exposed by an object.</span></span>

<span data-ttu-id="d7408-173">Další informace najdete v tématu [postupy](../../../../visual-basic/programming-guide/language-features/procedures/index.md).</span><span class="sxs-lookup"><span data-stu-id="d7408-173">For more information, see [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md).</span></span>

### <a name="events"></a><span data-ttu-id="d7408-174">Události</span><span class="sxs-lookup"><span data-stu-id="d7408-174">Events</span></span>

<span data-ttu-id="d7408-175">Událost je akce rozpoznaná objektem, jako je kliknutí myší nebo stisknutí klávesy, a pro kterou můžete napsat kód, který bude reagovat.</span><span class="sxs-lookup"><span data-stu-id="d7408-175">An event is an action recognized by an object, such as clicking the mouse or pressing a key, and for which you can write code to respond.</span></span> <span data-ttu-id="d7408-176">Události mohou vzniknout v důsledku akce uživatele nebo kódu programu nebo mohou být způsobeny systémem.</span><span class="sxs-lookup"><span data-stu-id="d7408-176">Events can occur as a result of a user action or program code, or they can be caused by the system.</span></span> <span data-ttu-id="d7408-177">Kód, který signalizuje událost, se říká k *vyvolání* události a kód, který na něj reaguje, je označován za účelem jeho *zpracování* .</span><span class="sxs-lookup"><span data-stu-id="d7408-177">Code that signals an event is said to *raise* the event, and code that responds to it is said to *handle* it.</span></span>

<span data-ttu-id="d7408-178">Můžete také vyvíjet vlastní události, které mají být vyvolány objekty a zpracovávány jinými objekty.</span><span class="sxs-lookup"><span data-stu-id="d7408-178">You can also develop your own custom events to be raised by your objects and handled by other objects.</span></span> <span data-ttu-id="d7408-179">Další informace najdete v tématu [události](../../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="d7408-179">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>

### <a name="instance-members-and-shared-members"></a><span data-ttu-id="d7408-180">Členové instance a sdílené členy</span><span class="sxs-lookup"><span data-stu-id="d7408-180">Instance members and shared members</span></span>

<span data-ttu-id="d7408-181">Při vytváření objektu z třídy je výsledkem instance této třídy.</span><span class="sxs-lookup"><span data-stu-id="d7408-181">When you create an object from a class, the result is an instance of that class.</span></span> <span data-ttu-id="d7408-182">Členy, které nejsou deklarovány se [sdíleným](../../../../visual-basic/language-reference/modifiers/shared.md) klíčovým slovem, jsou *členy instance*, které patří výhradně do této konkrétní instance.</span><span class="sxs-lookup"><span data-stu-id="d7408-182">Members that are not declared with the [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) keyword are *instance members*, which belong strictly to that particular instance.</span></span> <span data-ttu-id="d7408-183">Člen instance v jedné instanci je nezávislý na stejném členu v jiné instanci stejné třídy.</span><span class="sxs-lookup"><span data-stu-id="d7408-183">An instance member in one instance is independent of the same member in another instance of the same class.</span></span> <span data-ttu-id="d7408-184">Členská proměnná instance může mít například různé hodnoty v různých instancích.</span><span class="sxs-lookup"><span data-stu-id="d7408-184">An instance member variable, for example, can have different values in different instances.</span></span>

<span data-ttu-id="d7408-185">Členy deklarované s klíčovým slovem `Shared` jsou *sdílené členy*, které patří do třídy jako celek a nikoli do žádné konkrétní instance.</span><span class="sxs-lookup"><span data-stu-id="d7408-185">Members declared with the `Shared` keyword are *shared members*, which belong to the class as a whole and not to any particular instance.</span></span> <span data-ttu-id="d7408-186">Sdílený člen existuje pouze jednou, bez ohledu na to, kolik instancí své třídy vytvoříte, nebo dokonce i v případě, že nevytvoříte žádné instance.</span><span class="sxs-lookup"><span data-stu-id="d7408-186">A shared member exists only once, no matter how many instances of its class you create, or even if you create no instances.</span></span> <span data-ttu-id="d7408-187">Sdílená členská proměnná, například má pouze jednu hodnotu, která je k dispozici pro veškerý kód, který má přístup ke třídě.</span><span class="sxs-lookup"><span data-stu-id="d7408-187">A shared member variable, for example, has only one value, which is available to all code that can access the class.</span></span>

#### <a name="accessing-nonshared-members"></a><span data-ttu-id="d7408-188">Přístup k nesdíleným členům</span><span class="sxs-lookup"><span data-stu-id="d7408-188">Accessing nonshared members</span></span>

##### <a name="to-access-a-nonshared-member-of-an-object"></a><span data-ttu-id="d7408-189">Přístup k nesdílenému členu objektu</span><span class="sxs-lookup"><span data-stu-id="d7408-189">To access a nonshared member of an object</span></span>

1. <span data-ttu-id="d7408-190">Ujistěte se, že objekt byl vytvořen z jeho třídy a přiřazený k proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="d7408-190">Make sure the object has been created from its class and assigned to an object variable.</span></span>

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. <span data-ttu-id="d7408-191">V příkazu, který přistupuje ke členu, postupujte podle názvu proměnné objektu s *operátorem přístupu členů* (`.`) a potom názvem člena.</span><span class="sxs-lookup"><span data-stu-id="d7408-191">In the statement that accesses the member, follow the object variable name with the *member-access operator* (`.`) and then the member name.</span></span>

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a><span data-ttu-id="d7408-192">Přístup ke sdíleným členům</span><span class="sxs-lookup"><span data-stu-id="d7408-192">Accessing shared members</span></span>

##### <a name="to-access-a-shared-member-of-an-object"></a><span data-ttu-id="d7408-193">Přístup ke sdílenému členu objektu</span><span class="sxs-lookup"><span data-stu-id="d7408-193">To access a shared member of an object</span></span>

- <span data-ttu-id="d7408-194">Dodržujte název třídy s *operátorem přístupu členů* (`.`) a potom názvem člena.</span><span class="sxs-lookup"><span data-stu-id="d7408-194">Follow the class name with the *member-access operator* (`.`) and then the member name.</span></span> <span data-ttu-id="d7408-195">Vždy byste měli přistupovat k `Shared`mu členu objektu přímo prostřednictvím názvu třídy.</span><span class="sxs-lookup"><span data-stu-id="d7408-195">You should always access a `Shared` member of the object directly through the class name.</span></span>

   ```vb
   MsgBox("This computer is called " & Environment.MachineName)
   ```

- <span data-ttu-id="d7408-196">Pokud jste již vytvořili objekt ze třídy, můžete alternativně přistupovat k `Shared`mu členu prostřednictvím proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="d7408-196">If you have already created an object from the class, you can alternatively access a `Shared` member through the object's variable.</span></span>

### <a name="differences-between-classes-and-modules"></a><span data-ttu-id="d7408-197">Rozdíly mezi třídami a moduly</span><span class="sxs-lookup"><span data-stu-id="d7408-197">Differences between classes and modules</span></span>

<span data-ttu-id="d7408-198">Hlavním rozdílem mezi třídami a moduly je, že třídy mohou být vytvořeny jako objekty, zatímco standardní moduly nemůžou.</span><span class="sxs-lookup"><span data-stu-id="d7408-198">The main difference between classes and modules is that classes can be instantiated as objects while standard modules cannot.</span></span> <span data-ttu-id="d7408-199">Vzhledem k tomu, že existuje pouze jedna kopie dat standardního modulu, když jedna část programu změní veřejnou proměnnou ve standardním modulu, jakákoli jiná část programu získá stejnou hodnotu, pokud následně přečte tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="d7408-199">Because there is only one copy of a standard module's data, when one part of your program changes a public variable in a standard module, any other part of the program gets the same value if it then reads that variable.</span></span> <span data-ttu-id="d7408-200">Naproti tomu data objektu existují samostatně pro každý objekt s vytvořenou instancí.</span><span class="sxs-lookup"><span data-stu-id="d7408-200">In contrast, object data exists separately for each instantiated object.</span></span> <span data-ttu-id="d7408-201">Dalším rozdílem je, že na rozdíl od standardních modulů můžou třídy implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d7408-201">Another difference is that unlike standard modules, classes can implement interfaces.</span></span>

> [!NOTE]
> <span data-ttu-id="d7408-202">Pokud je modifikátor `Shared` použit pro člena třídy, je přidružen k samotné třídě namísto konkrétní instance třídy.</span><span class="sxs-lookup"><span data-stu-id="d7408-202">When the `Shared` modifier is applied to a class member, it is associated with the class itself instead of a particular instance of the class.</span></span> <span data-ttu-id="d7408-203">Ke členu se má získat přímý odkaz pomocí názvu třídy, stejně jako k nim přistupovali členové modulu.</span><span class="sxs-lookup"><span data-stu-id="d7408-203">The member is accessed directly by using the class name, the same way module members are accessed.</span></span>

<span data-ttu-id="d7408-204">Třídy a moduly používají pro své členy také různé obory.</span><span class="sxs-lookup"><span data-stu-id="d7408-204">Classes and modules also use different scopes for their members.</span></span> <span data-ttu-id="d7408-205">Členy definované v rámci třídy jsou vymezeny v rámci konkrétní instance třídy a existují pouze za dobu života objektu.</span><span class="sxs-lookup"><span data-stu-id="d7408-205">Members defined within a class are scoped within a specific instance of the class and exist only for the lifetime of the object.</span></span> <span data-ttu-id="d7408-206">Chcete-li získat přístup ke členům třídy z vnějšku třídy, je nutné použít plně kvalifikované názvy ve formátu *objektu*. *Člen*.</span><span class="sxs-lookup"><span data-stu-id="d7408-206">To access class members from outside a class, you must use fully qualified names in the format of *Object*.*Member*.</span></span>

<span data-ttu-id="d7408-207">Na druhé straně členové deklarované v rámci modulu jsou ve výchozím nastavení veřejně přístupné a lze k němu přistupovat jakýmkoli kódem, který má přístup k modulu.</span><span class="sxs-lookup"><span data-stu-id="d7408-207">On the other hand, members declared within a module are publicly accessible by default, and can be accessed by any code that can access the module.</span></span> <span data-ttu-id="d7408-208">To znamená, že proměnné ve standardním modulu jsou efektivní globální proměnné, protože jsou viditelné z libovolného místa v projektu a existují po dobu života programu.</span><span class="sxs-lookup"><span data-stu-id="d7408-208">This means that variables in a standard module are effectively global variables because they are visible from anywhere in your project, and they exist for the life of the program.</span></span>

## <a name="reusing-classes-and-objects"></a><span data-ttu-id="d7408-209">Znovu použití tříd a objektů</span><span class="sxs-lookup"><span data-stu-id="d7408-209">Reusing classes and objects</span></span>

<span data-ttu-id="d7408-210">Objekty umožňují deklarovat proměnné a procedury jednou a pak je znovu použít, kdykoli je to potřeba.</span><span class="sxs-lookup"><span data-stu-id="d7408-210">Objects let you declare variables and procedures once and then reuse them whenever needed.</span></span> <span data-ttu-id="d7408-211">Například pokud chcete přidat kontrolu pravopisu do aplikace, můžete definovat všechny proměnné a funkce podpory, které poskytují funkce kontroly pravopisu.</span><span class="sxs-lookup"><span data-stu-id="d7408-211">For example, if you want to add a spelling checker to an application you could define all the variables and support functions to provide spell-checking functionality.</span></span> <span data-ttu-id="d7408-212">Pokud vytvoříte kontrolu pravopisu jako třídu, můžete ji následně znovu použít v jiných aplikacích přidáním odkazu na zkompilované sestavení.</span><span class="sxs-lookup"><span data-stu-id="d7408-212">If you create your spelling checker as a class, you can then reuse it in other applications by adding a reference to the compiled assembly.</span></span> <span data-ttu-id="d7408-213">Ještě lepší je, že budete moct Uložit nějakou práci pomocí třídy pro kontrolu pravopisu, kterou už vyvinul někdo jiný.</span><span class="sxs-lookup"><span data-stu-id="d7408-213">Better yet, you may be able to save yourself some work by using a spelling checker class that someone else has already developed.</span></span>

<span data-ttu-id="d7408-214">.NET Framework poskytuje mnoho příkladů součástí, které jsou k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="d7408-214">The .NET Framework provides many examples of components that are available for use.</span></span> <span data-ttu-id="d7408-215">Následující příklad používá třídu <xref:System.TimeZone> v oboru názvů <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="d7408-215">The following example uses the <xref:System.TimeZone> class in the <xref:System> namespace.</span></span> <span data-ttu-id="d7408-216"><xref:System.TimeZone> poskytuje členy, které umožňují načíst informace o časovém pásmu aktuálního počítačového systému.</span><span class="sxs-lookup"><span data-stu-id="d7408-216"><xref:System.TimeZone> provides members that allow you to retrieve information about the time zone of the current computer system.</span></span>

```vb
Public Sub examineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    MsgBox(s)
End Sub
```

<span data-ttu-id="d7408-217">V předchozím příkladu příkaz v prvním [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) deklaruje proměnnou objektu typu <xref:System.TimeZone> a přiřadí jí objekt <xref:System.TimeZone> vrácený vlastností <xref:System.TimeZone.CurrentTimeZone%2A>.</span><span class="sxs-lookup"><span data-stu-id="d7408-217">In the preceding example, the first [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declares an object variable of type <xref:System.TimeZone> and assigns to it a <xref:System.TimeZone> object returned by the <xref:System.TimeZone.CurrentTimeZone%2A> property.</span></span>

## <a name="relationships-among-objects"></a><span data-ttu-id="d7408-218">Vztahy mezi objekty</span><span class="sxs-lookup"><span data-stu-id="d7408-218">Relationships among objects</span></span>

<span data-ttu-id="d7408-219">Objekty mohou být vzájemně propojené několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="d7408-219">Objects can be related to each other in several ways.</span></span> <span data-ttu-id="d7408-220">Hlavní typy vztahů jsou *hierarchické* a *omezení*.</span><span class="sxs-lookup"><span data-stu-id="d7408-220">The principal kinds of relationship are *hierarchical* and *containment*.</span></span>

### <a name="hierarchical-relationship"></a><span data-ttu-id="d7408-221">Hierarchický vztah</span><span class="sxs-lookup"><span data-stu-id="d7408-221">Hierarchical relationship</span></span>

<span data-ttu-id="d7408-222">Pokud třídy jsou odvozeny z více základních tříd, říká se, že mají *hierarchický vztah*.</span><span class="sxs-lookup"><span data-stu-id="d7408-222">When classes are derived from more fundamental classes, they are said to have a *hierarchical relationship*.</span></span> <span data-ttu-id="d7408-223">Hierarchie tříd jsou užitečné, pokud popisují položky, které jsou podtypu obecnější třídy.</span><span class="sxs-lookup"><span data-stu-id="d7408-223">Class hierarchies are useful when describing items that are a subtype of a more general class.</span></span>

<span data-ttu-id="d7408-224">V následujícím příkladu Předpokládejme, že chcete definovat zvláštní druh <xref:System.Windows.Forms.Button>, který funguje jako normální <xref:System.Windows.Forms.Button>, ale také zpřístupňuje metodu, která vrátí barvy popředí a pozadí.</span><span class="sxs-lookup"><span data-stu-id="d7408-224">In the following example, suppose you want to define a special kind of <xref:System.Windows.Forms.Button> that acts like a normal <xref:System.Windows.Forms.Button> but also exposes a method that reverses the foreground and background colors.</span></span>

#### <a name="to-define-a-class-is-derived-from-an-already-existing-class"></a><span data-ttu-id="d7408-225">Definování třídy je odvozeno z již existující třídy</span><span class="sxs-lookup"><span data-stu-id="d7408-225">To define a class is derived from an already existing class</span></span>

1. <span data-ttu-id="d7408-226">Použijte [příkaz třídy](../../../../visual-basic/language-reference/statements/class-statement.md) k definování třídy, ze které chcete vytvořit objekt, který potřebujete.</span><span class="sxs-lookup"><span data-stu-id="d7408-226">Use a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md) to define a class from which to create the object you need.</span></span>

   ```vb
   Public Class reversibleButton
   ```

   <span data-ttu-id="d7408-227">Ujistěte se, že příkaz `End Class` dodržuje poslední řádek kódu ve vaší třídě.</span><span class="sxs-lookup"><span data-stu-id="d7408-227">Be sure an `End Class` statement follows the last line of code in your class.</span></span> <span data-ttu-id="d7408-228">Ve výchozím nastavení integrované vývojové prostředí (IDE) automaticky vygeneruje `End Class` při zadání příkazu `Class`.</span><span class="sxs-lookup"><span data-stu-id="d7408-228">By default, the integrated development environment (IDE) automatically generates an `End Class` when you enter a `Class` statement.</span></span>

2. <span data-ttu-id="d7408-229">Použijte příkaz `Class` okamžitě s [příkazem Inherits](../../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d7408-229">Follow the `Class` statement immediately with an [Inherits Statement](../../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span> <span data-ttu-id="d7408-230">Zadejte třídu, ze které je odvozena nová třída.</span><span class="sxs-lookup"><span data-stu-id="d7408-230">Specify the class from which your new class derives.</span></span>

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   <span data-ttu-id="d7408-231">Vaše nová třída zdědí všechny členy definované základní třídou.</span><span class="sxs-lookup"><span data-stu-id="d7408-231">Your new class inherits all the members defined by the base class.</span></span>

3. <span data-ttu-id="d7408-232">Přidejte kód pro další členy, které vaše odvozená třída zveřejňuje.</span><span class="sxs-lookup"><span data-stu-id="d7408-232">Add the code for the additional members your derived class exposes.</span></span> <span data-ttu-id="d7408-233">Například můžete přidat metodu `reverseColors` a vaše odvozená třída může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="d7408-233">For example, you might add a `reverseColors` method, and your derived class might look as follows:</span></span>

   ```vb
   Public Class reversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub reverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   <span data-ttu-id="d7408-234">Vytvoříte-li objekt z třídy `reversibleButton`, může přistupovat ke všem členům třídy <xref:System.Windows.Forms.Button> a také k metodě `reverseColors` a dalším novým členům, které definujete v `reversibleButton`.</span><span class="sxs-lookup"><span data-stu-id="d7408-234">If you create an object from the `reversibleButton` class, it can access all the members of the <xref:System.Windows.Forms.Button> class, as well as the `reverseColors` method and any other new members you define on `reversibleButton`.</span></span>

<span data-ttu-id="d7408-235">Odvozené třídy dědí členy ze třídy, na které jsou založeny, což umožňuje v hierarchii tříd přidat složitost během průběhu.</span><span class="sxs-lookup"><span data-stu-id="d7408-235">Derived classes inherit members from the class they are based on, allowing you to add complexity as you progress in a class hierarchy.</span></span> <span data-ttu-id="d7408-236">Další informace najdete v tématu [základy dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="d7408-236">For more information, see [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>

### <a name="compiling-the-code"></a><span data-ttu-id="d7408-237">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="d7408-237">Compiling the code</span></span>

<span data-ttu-id="d7408-238">Ujistěte se, že kompilátor má přístup ke třídě, ze které hodláte odvodit novou třídu.</span><span class="sxs-lookup"><span data-stu-id="d7408-238">Be sure the compiler can access the class from which you intend to derive your new class.</span></span> <span data-ttu-id="d7408-239">To může znamenat, že plně kvalifikované jeho jméno, jako v předchozím příkladu, nebo určení jeho oboru názvů v [příkazu Imports (obor názvů a typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="d7408-239">This might mean fully qualifying its name, as in the preceding example, or identifying its namespace in an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="d7408-240">Pokud je třída v jiném projektu, může být nutné přidat odkaz na tento projekt.</span><span class="sxs-lookup"><span data-stu-id="d7408-240">If the class is in a different project, you might need to add a reference to that project.</span></span> <span data-ttu-id="d7408-241">Další informace naleznete v tématu [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project).</span><span class="sxs-lookup"><span data-stu-id="d7408-241">For more information, see [Managing references in a project](/visualstudio/ide/managing-references-in-a-project).</span></span>

### <a name="containment-relationship"></a><span data-ttu-id="d7408-242">Vztah členství ve skupině</span><span class="sxs-lookup"><span data-stu-id="d7408-242">Containment relationship</span></span>

<span data-ttu-id="d7408-243">Jiný způsob, jakým mohou být objekty v relaci, je *vztah zahrnutí*.</span><span class="sxs-lookup"><span data-stu-id="d7408-243">Another way that objects can be related is a *containment relationship*.</span></span> <span data-ttu-id="d7408-244">Objekty kontejneru logicky zapouzdřují jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="d7408-244">Container objects logically encapsulate other objects.</span></span> <span data-ttu-id="d7408-245">Například objekt <xref:System.OperatingSystem> logicky obsahuje objekt <xref:System.Version>, který se vrátí prostřednictvím jeho vlastnosti <xref:System.OperatingSystem.Version%2A>.</span><span class="sxs-lookup"><span data-stu-id="d7408-245">For example, the <xref:System.OperatingSystem> object logically contains a <xref:System.Version> object, which it returns through its <xref:System.OperatingSystem.Version%2A> property.</span></span> <span data-ttu-id="d7408-246">Všimněte si, že objekt kontejneru fyzicky neobsahuje žádný jiný objekt.</span><span class="sxs-lookup"><span data-stu-id="d7408-246">Note that the container object does not physically contain any other object.</span></span>

#### <a name="collections"></a><span data-ttu-id="d7408-247">Kolekce</span><span class="sxs-lookup"><span data-stu-id="d7408-247">Collections</span></span>

<span data-ttu-id="d7408-248">Jeden konkrétní typ zahrnutí objektu je reprezentován *kolekcemi*.</span><span class="sxs-lookup"><span data-stu-id="d7408-248">One particular type of object containment is represented by *collections*.</span></span> <span data-ttu-id="d7408-249">Kolekce jsou skupiny podobných objektů, které lze vyčíslit.</span><span class="sxs-lookup"><span data-stu-id="d7408-249">Collections are groups of similar objects that can be enumerated.</span></span> <span data-ttu-id="d7408-250">Visual Basic podporuje specifickou syntaxi [pro každý... Další příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) , který umožňuje iterovat položky kolekce.</span><span class="sxs-lookup"><span data-stu-id="d7408-250">Visual Basic supports a specific syntax in the [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) that allows you to iterate through the items of a collection.</span></span> <span data-ttu-id="d7408-251">Kromě toho kolekce často umožňují použít <xref:Microsoft.VisualBasic.Collection.Item%2A> k načtení prvků podle jejich indexu nebo jejich přidružení k jedinečnému řetězci.</span><span class="sxs-lookup"><span data-stu-id="d7408-251">Additionally, collections often allow you to use an <xref:Microsoft.VisualBasic.Collection.Item%2A> to retrieve elements by their index or by associating them with a unique string.</span></span> <span data-ttu-id="d7408-252">Kolekce lze snadněji používat než pole, protože umožňují přidávat nebo odebírat položky bez použití indexů.</span><span class="sxs-lookup"><span data-stu-id="d7408-252">Collections can be easier to use than arrays because they allow you to add or remove items without using indexes.</span></span> <span data-ttu-id="d7408-253">Z důvodu jejich snadného použití se kolekce často používají k ukládání formulářů a ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="d7408-253">Because of their ease of use, collections are often used to store forms and controls.</span></span>

## <a name="related-topics"></a><span data-ttu-id="d7408-254">Příbuzná témata</span><span class="sxs-lookup"><span data-stu-id="d7408-254">Related topics</span></span>

<span data-ttu-id="d7408-255">[Návod: definování tříd](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)</span><span class="sxs-lookup"><span data-stu-id="d7408-255">[Walkthrough: Defining Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)</span></span>\
<span data-ttu-id="d7408-256">Poskytuje podrobný popis postupu vytvoření třídy.</span><span class="sxs-lookup"><span data-stu-id="d7408-256">Provides a step-by-step description of how to create a class.</span></span>

<span data-ttu-id="d7408-257">[Přetížené vlastnosti a metody](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)</span><span class="sxs-lookup"><span data-stu-id="d7408-257">[Overloaded Properties and Methods](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)</span></span>\
<span data-ttu-id="d7408-258">Vlastnosti a metody přetečení</span><span class="sxs-lookup"><span data-stu-id="d7408-258">Overloaded Properties and Methods</span></span>

<span data-ttu-id="d7408-259">[Základy dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)</span><span class="sxs-lookup"><span data-stu-id="d7408-259">[Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)</span></span>\
<span data-ttu-id="d7408-260">Pokrývá modifikátory dědičnosti, přepsání metod a vlastností, MyClass a MyBase.</span><span class="sxs-lookup"><span data-stu-id="d7408-260">Covers inheritance modifiers, overriding methods and properties, MyClass, and MyBase.</span></span>

<span data-ttu-id="d7408-261">[Doba života objektu: vytváření a zničení objektů](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)</span><span class="sxs-lookup"><span data-stu-id="d7408-261">[Object Lifetime: How Objects Are Created and Destroyed](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)</span></span>\
<span data-ttu-id="d7408-262">Popisuje vytváření a odstraňování instancí třídy.</span><span class="sxs-lookup"><span data-stu-id="d7408-262">Discusses creating and disposing of class instances.</span></span>

<span data-ttu-id="d7408-263">[Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="d7408-263">[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)</span></span>\
<span data-ttu-id="d7408-264">V této části najdete popis postupu vytvoření a použití anonymních typů, které umožňují vytvářet objekty bez psaní definice třídy pro datový typ.</span><span class="sxs-lookup"><span data-stu-id="d7408-264">Describes how to create and use anonymous types, which allow you to create objects without writing a class definition for the data type.</span></span>

<span data-ttu-id="d7408-265">[Inicializátory objektů: pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="d7408-265">[Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)</span></span>\
<span data-ttu-id="d7408-266">Popisuje Inicializátory objektů, které se používají k vytváření instancí pojmenovaných a anonymních typů pomocí jednoho výrazu.</span><span class="sxs-lookup"><span data-stu-id="d7408-266">Discusses object initializers, which are used to create instances of named and anonymous types by using a single expression.</span></span>

<span data-ttu-id="d7408-267">[Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span><span class="sxs-lookup"><span data-stu-id="d7408-267">[How to: Infer Property Names and Types in Anonymous Type Declarations](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span></span>\
<span data-ttu-id="d7408-268">Vysvětluje, jak odvodit názvy vlastností a typy v deklaracích anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="d7408-268">Explains how to infer property names and types in anonymous type declarations.</span></span> <span data-ttu-id="d7408-269">Poskytuje příklady úspěšného a neúspěšného odvození.</span><span class="sxs-lookup"><span data-stu-id="d7408-269">Provides examples of successful and unsuccessful inference.</span></span>

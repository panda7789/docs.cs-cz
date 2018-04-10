---
title: Objekty a třídy v jazyce Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be5e0156b4cacc39e1613e06fe3c138838b02700
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="objects-and-classes-in-visual-basic"></a><span data-ttu-id="7bbf9-102">Objekty a třídy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7bbf9-102">Objects and classes in Visual Basic</span></span>
<span data-ttu-id="7bbf9-103">*Objekt* je kombinací kód a data, která lze považovat za jednotku.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-103">An *object* is a combination of code and data that can be treated as a unit.</span></span> <span data-ttu-id="7bbf9-104">Objekt může být část aplikace, jako je ovládacího prvku nebo formuláře.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-104">An object can be a piece of an application, like a control or a form.</span></span> <span data-ttu-id="7bbf9-105">Celá aplikace může být také objekt.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-105">An entire application can also be an object.</span></span>

<span data-ttu-id="7bbf9-106">Když vytvoříte aplikaci v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], neustále práce s objekty.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-106">When you create an application in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], you constantly work with objects.</span></span> <span data-ttu-id="7bbf9-107">Můžete použít objekty poskytované [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], jako jsou například ovládací prvky, formulářů a dat přístup k objektům.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-107">You can use objects provided by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], such as controls, forms, and data access objects.</span></span> <span data-ttu-id="7bbf9-108">Můžete taky objektů z jiných aplikací v rámci vaší [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-108">You can also use objects from other applications within your [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] application.</span></span> <span data-ttu-id="7bbf9-109">Můžete dokonce vytvořit vlastní objekty a definovat další vlastnosti a metody pro ně.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-109">You can even create your own objects and define additional properties and methods for them.</span></span> <span data-ttu-id="7bbf9-110">Objekty fungovat stejně jako prefabrikované stavební bloky pro programy – umožňují můžete napsat kód jednou a znovu použít opakovaně.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-110">Objects act like prefabricated building blocks for programs — they let you write a piece of code once and reuse it over and over.</span></span>  
  
<span data-ttu-id="7bbf9-111">Toto téma popisuje objekty podrobně.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-111">This topic discusses objects in detail.</span></span>  

## <a name="objects-and-classes"></a><span data-ttu-id="7bbf9-112">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="7bbf9-112">Objects and classes</span></span>
<span data-ttu-id="7bbf9-113">Každý objekt v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] je definované *třída*.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-113">Each object in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] is defined by a *class*.</span></span> <span data-ttu-id="7bbf9-114">Třída popisuje proměnné, vlastnosti, postupy a události objektu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-114">A class describes the variables, properties, procedures, and events of an object.</span></span> <span data-ttu-id="7bbf9-115">Objekty jsou instance třídy; můžete vytvořit libovolný počet objektů, které potřebujete, jakmile definujete třídu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-115">Objects are instances of classes; you can create as many objects you need once you have defined a class.</span></span>

<span data-ttu-id="7bbf9-116">Vztah mezi objektem a její třída pochopit, vezměte v úvahu řezačky souboru cookie a soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-116">To understand the relationship between an object and its class, think of cookie cutters and cookies.</span></span> <span data-ttu-id="7bbf9-117">Ořezávání soubor cookie je třída.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-117">The cookie cutter is the class.</span></span> <span data-ttu-id="7bbf9-118">Definuje vlastnosti každého souboru cookie, například velikost a tvar.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-118">It defines the characteristics of each cookie, for example size and shape.</span></span> <span data-ttu-id="7bbf9-119">Třída slouží k vytváření objektů.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-119">The class is used to create objects.</span></span> <span data-ttu-id="7bbf9-120">Objekty jsou soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-120">The objects are the cookies.</span></span>

<span data-ttu-id="7bbf9-121">Objekt je nutné vytvořit před přístupem k její členy.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-121">You must create an object before you can access its members.</span></span>  

#### <a name="to-create-an-object-from-a-class"></a><span data-ttu-id="7bbf9-122">Chcete-li vytvořit objekt ze třídy</span><span class="sxs-lookup"><span data-stu-id="7bbf9-122">To create an object from a class</span></span>

1. <span data-ttu-id="7bbf9-123">Určete, ze které třídy, kterou chcete vytvořit objekt.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-123">Determine from which class you want to create an object.</span></span>  

2. <span data-ttu-id="7bbf9-124">Zápis [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md) vytvoření proměnné, do které můžete přiřadit instance třídy.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-124">Write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to create a variable to which you can assign a class instance.</span></span> <span data-ttu-id="7bbf9-125">Proměnná by měla být typ požadovanou třídu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-125">The variable should be of the type of the desired class.</span></span>

   ```vb
   Dim nextCustomer As customer
   ```

3. <span data-ttu-id="7bbf9-126">Přidat [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md) – klíčové slovo můžete inicializovat do nové instance třídy.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-126">Add the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword to initialize the variable to a new instance of the class.</span></span>

   ```vb
   Dim nextCustomer As New customer
   ```

4. <span data-ttu-id="7bbf9-127">Můžete teď přístup ke členům třídy prostřednictvím proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-127">You can now access the members of the class through the object variable.</span></span>  

   ```vb
   nextCustomer.accountNumber = lastAccountNumber + 1  
   ```

> [!NOTE]
>  <span data-ttu-id="7bbf9-128">Kdykoli je to možné, by měly deklarovat proměnnou být typu třídy, kterou chcete přiřadit k němu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-128">Whenever possible, you should declare the variable to be of the class type you intend to assign to it.</span></span> <span data-ttu-id="7bbf9-129">To se označuje jako *časné vazby*.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-129">This is called *early binding*.</span></span> <span data-ttu-id="7bbf9-130">Pokud neznáte třídu, zadejte v době kompilace, můžete vyvolat *pozdní vazby* deklarováním proměnné se [Object – datový typ](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="7bbf9-130">If you don't know the class type at compile time, you can invoke *late binding* by declaring the variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="7bbf9-131">Ale pozdní vazby můžete provádět pomalejší výkon a omezení přístupu ke členům běhového objektu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-131">However, late binding can make performance slower and limit access to the run-time object's members.</span></span> <span data-ttu-id="7bbf9-132">Další informace najdete v tématu [deklarace proměnné objektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="7bbf9-132">For more information, see [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).</span></span>

### <a name="multiple-instances"></a><span data-ttu-id="7bbf9-133">Více instancí</span><span class="sxs-lookup"><span data-stu-id="7bbf9-133">Multiple instances</span></span>
<span data-ttu-id="7bbf9-134">Objekty nově vytvořený z třídy jsou často identické navzájem.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-134">Objects newly created from a class are often identical to each other.</span></span> <span data-ttu-id="7bbf9-135">Jakmile existují jako jednotlivé objekty, ale jejich proměnné a vlastnosti lze změnit nezávisle na ostatních instancí.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-135">Once they exist as individual objects, however, their variables and properties can be changed independently of the other instances.</span></span> <span data-ttu-id="7bbf9-136">Například pokud přidáte tři políčka na formulář, každý objekt zaškrtávací políčko je instance <xref:System.Windows.Forms.CheckBox> třídy.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-136">For example, if you add three check boxes to a form, each check box object is an instance of the <xref:System.Windows.Forms.CheckBox> class.</span></span> <span data-ttu-id="7bbf9-137">Jednotlivých <xref:System.Windows.Forms.CheckBox> objekty sdílejí společnou sadu vlastností a funkcí (vlastnosti, proměnné, postupy a události) definované v třídě.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-137">The individual <xref:System.Windows.Forms.CheckBox> objects share a common set of characteristics and capabilities (properties, variables, procedures, and events) defined by the class.</span></span> <span data-ttu-id="7bbf9-138">Však každý má vlastní název, lze samostatně povolit a zakázat a mohou být umístěny v jiném umístění ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-138">However, each has its own name, can be separately enabled and disabled, and can be placed in a different location on the form.</span></span>

## <a name="object-members"></a><span data-ttu-id="7bbf9-139">Členové objektu</span><span class="sxs-lookup"><span data-stu-id="7bbf9-139">Object members</span></span>
<span data-ttu-id="7bbf9-140">Element aplikace, je objekt reprezentující *instance* třídy.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-140">An object is an element of an application, representing an *instance* of a class.</span></span> <span data-ttu-id="7bbf9-141">Pole, vlastnosti, metod a události představují stavební kameny objektů a tvoří jejich *členy*.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-141">Fields, properties, methods, and events are the building blocks of objects and constitute their *members*.</span></span>

### <a name="member-access"></a><span data-ttu-id="7bbf9-142">Přístup ke členu</span><span class="sxs-lookup"><span data-stu-id="7bbf9-142">Member Access</span></span>
<span data-ttu-id="7bbf9-143">Přístup ke členu objektu zadáním v pořadí, název proměnné objektu období (`.`) a název člena.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-143">You access a member of an object by specifying, in order, the name of the object variable, a period (`.`), and the name of the member.</span></span> <span data-ttu-id="7bbf9-144">Následující příklad nastavuje <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.Label> objektu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-144">The following example sets the <xref:System.Windows.Forms.Control.Text%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a><span data-ttu-id="7bbf9-145">IntelliSense seznam členů</span><span class="sxs-lookup"><span data-stu-id="7bbf9-145">IntelliSense listing of members</span></span>
<span data-ttu-id="7bbf9-146">IntelliSense zobrazí seznam členy třídy při vyvolání své volby vypsat členy, například když zadáte období (`.`) jako operátor přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-146">IntelliSense lists members of a class when you invoke its List Members option, for example when you type a period (`.`) as a member-access operator.</span></span> <span data-ttu-id="7bbf9-147">Pokud zadáte název proměnné deklarovány jako instance této třídy tečku, IntelliSense zobrazí seznam všech členů instance a žádná sdíleného člena.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-147">If you type the period following the name of a variable declared as an instance of that class, IntelliSense lists all the instance members and none of the shared members.</span></span> <span data-ttu-id="7bbf9-148">Pokud zadáte období následující samotný název třídy, IntelliSense zobrazí seznam všech sdíleného člena a žádný z členů instance.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-148">If you type the period following the class name itself, IntelliSense lists all the shared members and none of the instance members.</span></span> <span data-ttu-id="7bbf9-149">Další informace najdete v tématu [pomocí IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="7bbf9-149">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>

### <a name="fields-and-properties"></a><span data-ttu-id="7bbf9-150">Pole a vlastnosti</span><span class="sxs-lookup"><span data-stu-id="7bbf9-150">Fields and properties</span></span>
<span data-ttu-id="7bbf9-151">*Pole* a *vlastnosti* představují informace uložené v objektu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-151">*Fields* and *properties* represent information stored in an object.</span></span> <span data-ttu-id="7bbf9-152">Načtení a nastavení jejich hodnot s příkazy přiřazení stejným způsobem jako načíst a nastavit místní proměnné v postupu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-152">You retrieve and set their values with assignment statements the same way you retrieve and set local variables in a procedure.</span></span> <span data-ttu-id="7bbf9-153">Následující příklad načte <xref:System.Windows.Forms.Control.Width%2A> vlastnost a nastaví <xref:System.Windows.Forms.Control.ForeColor%2A> vlastnost <xref:System.Windows.Forms.Label> objektu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-153">The following example retrieves the <xref:System.Windows.Forms.Control.Width%2A> property and sets the <xref:System.Windows.Forms.Control.ForeColor%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

<span data-ttu-id="7bbf9-154">Všimněte si, že pole je také označován *členské proměnné*.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-154">Note that a field is also called a *member variable*.</span></span>
  
<span data-ttu-id="7bbf9-155">Použijte vlastnost postupy při:</span><span class="sxs-lookup"><span data-stu-id="7bbf9-155">Use property procedures when:</span></span>

- <span data-ttu-id="7bbf9-156">Potřebujete řídit, kdy a jak je nastavit nebo načíst hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-156">You need to control when and how a value is set or retrieved.</span></span>

- <span data-ttu-id="7bbf9-157">Tato vlastnost nemá jasně definované sady hodnot, které je potřeba ověřit.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-157">The property has a well-defined set of values that need to be validated.</span></span>

- <span data-ttu-id="7bbf9-158">Nastavení hodnoty způsobí, že některé postřehnutelné změny ve stavu objektu, například `IsVisible` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-158">Setting the value causes some perceptible change in the object's state, such as an `IsVisible` property.</span></span>

- <span data-ttu-id="7bbf9-159">Nastavení vlastnosti způsobí, že změny na ostatní interní proměnné nebo na hodnotách jiných vlastností.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-159">Setting the property causes changes to other internal variables or to the values of other properties.</span></span>

- <span data-ttu-id="7bbf9-160">Sadu kroky je potřeba provést před vlastnost nelze nastavit ani načíst.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-160">A set of steps must be performed before the property can be set or retrieved.</span></span>

<span data-ttu-id="7bbf9-161">Použití polí, když:</span><span class="sxs-lookup"><span data-stu-id="7bbf9-161">Use fields when:</span></span>  

- <span data-ttu-id="7bbf9-162">Hodnota je typu samoobslužné ověřování.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-162">The value is of a self-validating type.</span></span> <span data-ttu-id="7bbf9-163">Například Chyba nebo převod automatické dat v případě jinou hodnotu než `True` nebo `False` je přiřazena k `Boolean` proměnné.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-163">For example, an error or automatic data conversion occurs if a value other than `True` or `False` is assigned to a `Boolean` variable.</span></span>

- <span data-ttu-id="7bbf9-164">Libovolná hodnota v rozsahu nepodporuje datový typ je platný.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-164">Any value in the range supported by the data type is valid.</span></span> <span data-ttu-id="7bbf9-165">To platí pro mnoho vlastností typu `Single` nebo `Double`.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-165">This is true of many properties of type `Single` or `Double`.</span></span>

- <span data-ttu-id="7bbf9-166">Vlastnost je `String` datový typ, a neexistuje žádné omezení velikosti nebo hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-166">The property is a `String` data type, and there is no constraint on the size or value of the string.</span></span>

- <span data-ttu-id="7bbf9-167">Další informace najdete v tématu [procedury vlastností](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="7bbf9-167">For more information, see [Property Procedures](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span></span>

### <a name="methods"></a><span data-ttu-id="7bbf9-168">Metody</span><span class="sxs-lookup"><span data-stu-id="7bbf9-168">Methods</span></span>
<span data-ttu-id="7bbf9-169">A *metoda* je akce, která může provádět objekt.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-169">A *method* is an action that an object can perform.</span></span> <span data-ttu-id="7bbf9-170">Například <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> je metoda <xref:System.Windows.Forms.ComboBox> objekt, který přidá novou položku do pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-170">For example, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> is a method of the <xref:System.Windows.Forms.ComboBox> object that adds a new entry to a combo box.</span></span>

<span data-ttu-id="7bbf9-171">Následující příklad ukazuje <xref:System.Windows.Forms.Timer.Start%2A> metodu <xref:System.Windows.Forms.Timer> objektu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-171">The following example demonstrates the <xref:System.Windows.Forms.Timer.Start%2A> method of a <xref:System.Windows.Forms.Timer> object.</span></span>

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

<span data-ttu-id="7bbf9-172">Všimněte si, že je metoda jednoduše *postup* který je zveřejněný prostřednictvím objektu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-172">Note that a method is simply a *procedure* that is exposed by an object.</span></span>

<span data-ttu-id="7bbf9-173">Další informace najdete v tématu [postupy](../../../../visual-basic/programming-guide/language-features/procedures/index.md).</span><span class="sxs-lookup"><span data-stu-id="7bbf9-173">For more information, see [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md).</span></span>

### <a name="events"></a><span data-ttu-id="7bbf9-174">Události</span><span class="sxs-lookup"><span data-stu-id="7bbf9-174">Events</span></span>
<span data-ttu-id="7bbf9-175">Událost je akce rozpoznáno objekt, jako je například kliknutí myši nebo stisknutí klávesy, a pro které můžete psát kód reagovat.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-175">An event is an action recognized by an object, such as clicking the mouse or pressing a key, and for which you can write code to respond.</span></span> <span data-ttu-id="7bbf9-176">Události může dojít v důsledku akce uživatele nebo kódu programu, nebo může být způsobeno systému.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-176">Events can occur as a result of a user action or program code, or they can be caused by the system.</span></span> <span data-ttu-id="7bbf9-177">Kód, který signály událost říká, že je *vyvolat* událostí a kód, který reaguje na něj říká, že je *zpracování* ho.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-177">Code that signals an event is said to *raise* the event, and code that responds to it is said to *handle* it.</span></span>

<span data-ttu-id="7bbf9-178">Také lze vytvářet vlastní události vyvolané vašich objektů a zpracovávat jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-178">You can also develop your own custom events to be raised by your objects and handled by other objects.</span></span> <span data-ttu-id="7bbf9-179">Další informace najdete v tématu [události](../../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="7bbf9-179">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>

### <a name="instance-members-and-shared-members"></a><span data-ttu-id="7bbf9-180">Členy instance a sdílení členové</span><span class="sxs-lookup"><span data-stu-id="7bbf9-180">Instance members and shared members</span></span>
<span data-ttu-id="7bbf9-181">Když vytvoříte objekt ze třídy, výsledkem je instance této třídy.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-181">When you create an object from a class, the result is an instance of that class.</span></span> <span data-ttu-id="7bbf9-182">Členové, kteří nejsou deklarovat s [sdílené](../../../../visual-basic/language-reference/modifiers/shared.md) – klíčové slovo jsou *instance členy*, které patří výhradně na tuto konkrétní instanci.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-182">Members that are not declared with the [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) keyword are *instance members*, which belong strictly to that particular instance.</span></span> <span data-ttu-id="7bbf9-183">Člen instance v jedné instance je nezávislá stejného člena v jiná instance stejné třídy.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-183">An instance member in one instance is independent of the same member in another instance of the same class.</span></span> <span data-ttu-id="7bbf9-184">Členské proměnné instance, například může mít různé hodnoty v různých instancí.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-184">An instance member variable, for example, can have different values in different instances.</span></span>

<span data-ttu-id="7bbf9-185">Členy deklarovat s `Shared` – klíčové slovo jsou *sdílené členy*, který patří k třídě jako celek, ne na jakékoli určité instance.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-185">Members declared with the `Shared` keyword are *shared members*, which belong to the class as a whole and not to any particular instance.</span></span> <span data-ttu-id="7bbf9-186">Sdíleného člena existuje pouze po, bez ohledu na to, kolik instancí třídy jeho vytvoření nebo i v případě, že vytvoříte žádné instance.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-186">A shared member exists only once, no matter how many instances of its class you create, or even if you create no instances.</span></span> <span data-ttu-id="7bbf9-187">Proměnnou sdíleného člena, například obsahuje pouze jednu hodnotu, která je k dispozici pro všechny kód, který může přistupovat k třídě.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-187">A shared member variable, for example, has only one value, which is available to all code that can access the class.</span></span>

#### <a name="accessing-nonshared-members"></a><span data-ttu-id="7bbf9-188">Přístup ke členům sdíleném</span><span class="sxs-lookup"><span data-stu-id="7bbf9-188">Accessing nonshared members</span></span>  

###### <a name="to-access-a-nonshared-member-of-an-object"></a><span data-ttu-id="7bbf9-189">O přístup člena sdíleném objektu</span><span class="sxs-lookup"><span data-stu-id="7bbf9-189">To access a nonshared member of an object</span></span>

1. <span data-ttu-id="7bbf9-190">Zajistěte, aby bylo vytvořeno ze své třídy objektu a přiřazené proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-190">Make sure the object has been created from its class and assigned to an object variable.</span></span>

   ```vb
   Dim secondForm As New System.Windows.Forms.Form  
   ```  

2. <span data-ttu-id="7bbf9-191">V příkazu, který přistupuje k člen, postupujte podle názvu proměnné objektu s *přístup ke členu operátor* (`.`) a potom název člena.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-191">In the statement that accesses the member, follow the object variable name with the *member-access operator* (`.`) and then the member name.</span></span>

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a><span data-ttu-id="7bbf9-192">Přístup k sdílení členové</span><span class="sxs-lookup"><span data-stu-id="7bbf9-192">Accessing shared members</span></span>

###### <a name="to-access-a-shared-member-of-an-object"></a><span data-ttu-id="7bbf9-193">Přístup sdíleného člena objektu</span><span class="sxs-lookup"><span data-stu-id="7bbf9-193">To access a shared member of an object</span></span>

- <span data-ttu-id="7bbf9-194">Postupujte podle názvu třídy s *přístup ke členu operátor* (`.`) a potom název člena.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-194">Follow the class name with the *member-access operator* (`.`) and then the member name.</span></span> <span data-ttu-id="7bbf9-195">Byste měli vždy přistupovat `Shared` členem objektu přímo prostřednictvím název třídy.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-195">You should always access a `Shared` member of the object directly through the class name.</span></span>

   ```vb
   MsgBox("This computer is called " & Environment.MachineName)  
   ```

- <span data-ttu-id="7bbf9-196">Pokud jste již vytvořili objekt ze třídy, případně se dostanete `Shared` člen prostřednictvím proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-196">If you have already created an object from the class, you can alternatively access a `Shared` member through the object's variable.</span></span>

### <a name="differences-between-classes-and-modules"></a><span data-ttu-id="7bbf9-197">Rozdíly mezi třídami a modulů</span><span class="sxs-lookup"><span data-stu-id="7bbf9-197">Differences between classes and modules</span></span>
<span data-ttu-id="7bbf9-198">Hlavní rozdíl mezi třídami a moduly je, že třídy se dá vytvořit instance jako objekty při nelze standardní moduly.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-198">The main difference between classes and modules is that classes can be instantiated as objects while standard modules cannot.</span></span> <span data-ttu-id="7bbf9-199">A proto pouze jedna kopie dat standardní modul, kdy se jeden součástí vašeho programu změní veřejné proměnné ve standardním modulu jiných součástí program získá stejnou hodnotu, pokud je pak přečte tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-199">Because there is only one copy of a standard module's data, when one part of your program changes a public variable in a standard module, any other part of the program gets the same value if it then reads that variable.</span></span> <span data-ttu-id="7bbf9-200">Naproti tomu data objektu existuje samostatně pro každou instancí objektu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-200">In contrast, object data exists separately for each instantiated object.</span></span> <span data-ttu-id="7bbf9-201">Další rozdíl je, že na rozdíl od standardní moduly třídy mohou implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-201">Another difference is that unlike standard modules, classes can implement interfaces.</span></span>

> [!NOTE]
> <span data-ttu-id="7bbf9-202">Když `Shared` modifikátor umožňuje člena třídy, je přidružen vlastní místo konkrétní instanci třídy třídy.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-202">When the `Shared` modifier is applied to a class member, it is associated with the class itself instead of a particular instance of the class.</span></span> <span data-ttu-id="7bbf9-203">Člen je přistupovat přímo pomocí názvu třídy, stejné členy modulu způsob, jak se k nim přistupuje.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-203">The member is accessed directly by using the class name, the same way module members are accessed.</span></span>

<span data-ttu-id="7bbf9-204">Třídy a moduly také použít různé obory pro jejich členové.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-204">Classes and modules also use different scopes for their members.</span></span> <span data-ttu-id="7bbf9-205">Členové, které jsou definované v rámci třídy jsou určené v rámci konkrétní instanci třídy a existovat jenom pro doba života objektu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-205">Members defined within a class are scoped within a specific instance of the class and exist only for the lifetime of the object.</span></span> <span data-ttu-id="7bbf9-206">Přístup ke členům třídy z mimo třídu, musíte použít plně kvalifikované názvy ve formátu *objekt*. *Člen*.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-206">To access class members from outside a class, you must use fully qualified names in the format of *Object*.*Member*.</span></span>

<span data-ttu-id="7bbf9-207">Na druhé straně členové deklarované v rámci modul jsou veřejně dostupné ve výchozím nastavení a je přístupný kód, který můžete získat přístup k modulu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-207">On the other hand, members declared within a module are publicly accessible by default, and can be accessed by any code that can access the module.</span></span> <span data-ttu-id="7bbf9-208">To znamená, že proměnné ve standardním modulu jsou efektivně globální proměnné, protože jsou viditelné z libovolné místo ve vašem projektu a existují po celou dobu životnosti program.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-208">This means that variables in a standard module are effectively global variables because they are visible from anywhere in your project, and they exist for the life of the program.</span></span>

## <a name="reusing-classes-and-objects"></a><span data-ttu-id="7bbf9-209">Opětovné použití tříd a objektů</span><span class="sxs-lookup"><span data-stu-id="7bbf9-209">Reusing classes and objects</span></span>  
<span data-ttu-id="7bbf9-210">Objekty umožňují deklarace proměnných a postupy jednou a pak je vždy v případě potřeby znovu použijte.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-210">Objects let you declare variables and procedures once and then reuse them whenever needed.</span></span> <span data-ttu-id="7bbf9-211">Například pokud chcete přidat nástroj pro kontrolu pravopisu do aplikace můžete definovat všechny proměnné a podporovat funkce nakonfigurovánu pravopisu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-211">For example, if you want to add a spelling checker to an application you could define all the variables and support functions to provide spell-checking functionality.</span></span> <span data-ttu-id="7bbf9-212">Pokud vytvoříte vaše kontrola pravopisu jako třída, můžete je znovu ji v ostatních aplikacích přidáním odkazu na zkompilované sestavení.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-212">If you create your spelling checker as a class, you can then reuse it in other applications by adding a reference to the compiled assembly.</span></span> <span data-ttu-id="7bbf9-213">Ještě lepší nebudete moct uložit sami některé pracovní pomocí kontrola pravopisu třídu, která někdo jiný již vyvinula</span><span class="sxs-lookup"><span data-stu-id="7bbf9-213">Better yet, you may be able to save yourself some work by using a spelling checker class that someone else has already developed.</span></span>

<span data-ttu-id="7bbf9-214">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Obsahuje mnoho příklady součásti, které jsou k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-214">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provides many examples of components that are available for use.</span></span> <span data-ttu-id="7bbf9-215">Následující příklad používá <xref:System.TimeZone> třídy v <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-215">The following example uses the <xref:System.TimeZone> class in the <xref:System> namespace.</span></span> <span data-ttu-id="7bbf9-216"><xref:System.TimeZone>poskytuje členy, které vám umožní načíst informace o časovém pásmu aktuální počítačového systému.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-216"><xref:System.TimeZone> provides members that allow you to retrieve information about the time zone of the current computer system.</span></span>

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

<span data-ttu-id="7bbf9-217">V předchozím příkladu první [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md) deklaruje proměnné objektu typu <xref:System.TimeZone> a přiřadí ji <xref:System.TimeZone> objekt vrácený <xref:System.TimeZone.CurrentTimeZone%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-217">In the preceding example, the first [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declares an object variable of type <xref:System.TimeZone> and assigns to it a <xref:System.TimeZone> object returned by the <xref:System.TimeZone.CurrentTimeZone%2A> property.</span></span>

## <a name="relationships-among-objects"></a><span data-ttu-id="7bbf9-218">Vztahy mezi objekty</span><span class="sxs-lookup"><span data-stu-id="7bbf9-218">Relationships among objects</span></span>  
<span data-ttu-id="7bbf9-219">Objekty může souviset s navzájem několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-219">Objects can be related to each other in several ways.</span></span> <span data-ttu-id="7bbf9-220">Hlavní typy vztahů jsou *hierarchické* a *členství ve skupině*.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-220">The principal kinds of relationship are *hierarchical* and *containment*.</span></span>

### <a name="hierarchical-relationship"></a><span data-ttu-id="7bbf9-221">Hierarchický vztah</span><span class="sxs-lookup"><span data-stu-id="7bbf9-221">Hierarchical relationship</span></span>
<span data-ttu-id="7bbf9-222">Když jsou třídy odvozené z více základní třídy, se nazývá mít *hierarchický vztah*.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-222">When classes are derived from more fundamental classes, they are said to have a *hierarchical relationship*.</span></span> <span data-ttu-id="7bbf9-223">Hierarchie tříd jsou užitečné při popisu položky, které jsou podtypem další obecné třídy.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-223">Class hierarchies are useful when describing items that are a subtype of a more general class.</span></span>

<span data-ttu-id="7bbf9-224">V následujícím příkladu předpokládejme, že chcete definovat speciální typ <xref:System.Windows.Forms.Button> , funguje jako normální <xref:System.Windows.Forms.Button> , ale také zpřístupní metodu, která obrátí barvy popředí a na pozadí.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-224">In the following example, suppose you want to define a special kind of <xref:System.Windows.Forms.Button> that acts like a normal <xref:System.Windows.Forms.Button> but also exposes a method that reverses the foreground and background colors.</span></span>

##### <a name="to-define-a-class-is-derived-from-an-already-existing-class"></a><span data-ttu-id="7bbf9-225">Chcete-li definovat třídu je odvozený od již existující třídy</span><span class="sxs-lookup"><span data-stu-id="7bbf9-225">To define a class is derived from an already existing class</span></span>

1. <span data-ttu-id="7bbf9-226">Použití [Class – příkaz](../../../../visual-basic/language-reference/statements/class-statement.md) do definice třídy, ze které chcete vytvořit objekt potřebujete.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-226">Use a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md) to define a class from which to create the object you need.</span></span>

   ```vb
   Public Class reversibleButton
   ```

   <span data-ttu-id="7bbf9-227">Ujistěte se, `End Class` příkaz následuje poslední řádek kódu v třídě.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-227">Be sure an `End Class` statement follows the last line of code in your class.</span></span> <span data-ttu-id="7bbf9-228">Ve výchozím nastavení, budou automaticky vygeneruje integrované vývojové prostředí (IDE) `End Class` při zadávání `Class` příkaz.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-228">By default, the integrated development environment (IDE) automatically generates an `End Class` when you enter a `Class` statement.</span></span>

2. <span data-ttu-id="7bbf9-229">Postupujte podle `Class` příkaz okamžitě s [dědí příkaz](../../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7bbf9-229">Follow the `Class` statement immediately with an [Inherits Statement](../../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span> <span data-ttu-id="7bbf9-230">Zadejte třídu, ze kterého se nová třída odvozena.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-230">Specify the class from which your new class derives.</span></span>  
  
   ```vb
   Inherits System.Windows.Forms.Button
   ```

  <span data-ttu-id="7bbf9-231">Nové třídy dědí všechny členy, které jsou definované v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-231">Your new class inherits all the members defined by the base class.</span></span>

3. <span data-ttu-id="7bbf9-232">Přidáte kód pro další členy vaší zpřístupňuje odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-232">Add the code for the additional members your derived class exposes.</span></span> <span data-ttu-id="7bbf9-233">Například může přidat `reverseColors` metoda a odvozená třída může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="7bbf9-233">For example, you might add a `reverseColors` method, and your derived class might look as follows:</span></span>

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

   <span data-ttu-id="7bbf9-234">Pokud vytvoříte objekt z `reversibleButton` třídy, že přístup všech členů <xref:System.Windows.Forms.Button> třída, a taky `reverseColors` metoda a nové členy můžete definovat na `reversibleButton`.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-234">If you create an object from the `reversibleButton` class, it can access all the members of the <xref:System.Windows.Forms.Button> class, as well as the `reverseColors` method and any other new members you define on `reversibleButton`.</span></span>

<span data-ttu-id="7bbf9-235">Odvozené třídy dědí z třídy, které jsou založené na, že se můžete k přidání složitosti jako o průběhu v hierarchii – třída členů.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-235">Derived classes inherit members from the class they are based on, allowing you to add complexity as you progress in a class hierarchy.</span></span> <span data-ttu-id="7bbf9-236">Další informace najdete v tématu [základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="7bbf9-236">For more information, see [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>

#### <a name="compiling-the-code"></a><span data-ttu-id="7bbf9-237">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7bbf9-237">Compiling the code</span></span>
<span data-ttu-id="7bbf9-238">Ujistěte se, že kompilátor můžete přístup ke třídě, ze kterého chcete odvozena novou třídu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-238">Be sure the compiler can access the class from which you intend to derive your new class.</span></span> <span data-ttu-id="7bbf9-239">To může znamenat plně kvalifikující jeho název, jako v předchozím příkladu nebo identifikace jeho oboru názvů v [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="7bbf9-239">This might mean fully qualifying its name, as in the preceding example, or identifying its namespace in an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="7bbf9-240">Pokud třída je v na jiný projekt, možná budete muset přidat odkaz na tento projekt.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-240">If the class is in a different project, you might need to add a reference to that project.</span></span> <span data-ttu-id="7bbf9-241">Další informace najdete v tématu [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project).</span><span class="sxs-lookup"><span data-stu-id="7bbf9-241">For more information, see [Managing references in a project](/visualstudio/ide/managing-references-in-a-project).</span></span>

### <a name="containment-relationship"></a><span data-ttu-id="7bbf9-242">Vztah členství ve skupině</span><span class="sxs-lookup"><span data-stu-id="7bbf9-242">Containment relationship</span></span>
<span data-ttu-id="7bbf9-243">Dalším způsobem může souviset objekty je *vztah členství ve skupině*.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-243">Another way that objects can be related is a *containment relationship*.</span></span> <span data-ttu-id="7bbf9-244">Kontejnerové objekty zapouzdřují logicky jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-244">Container objects logically encapsulate other objects.</span></span> <span data-ttu-id="7bbf9-245">Například <xref:System.OperatingSystem> objekt logicky obsahuje <xref:System.Version> objekt, který vrátí prostřednictvím jeho <xref:System.OperatingSystem.Version%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-245">For example, the <xref:System.OperatingSystem> object logically contains a <xref:System.Version> object, which it returns through its <xref:System.OperatingSystem.Version%2A> property.</span></span> <span data-ttu-id="7bbf9-246">Všimněte si, že objekt kontejneru fyzicky neobsahuje jakýkoliv jiný objekt.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-246">Note that the container object does not physically contain any other object.</span></span>

#### <a name="collections"></a><span data-ttu-id="7bbf9-247">Kolekce</span><span class="sxs-lookup"><span data-stu-id="7bbf9-247">Collections</span></span>
<span data-ttu-id="7bbf9-248">Jeden konkrétní typ omezení objektu je reprezentována *kolekce*.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-248">One particular type of object containment is represented by *collections*.</span></span> <span data-ttu-id="7bbf9-249">Kolekce jsou podobné objekty, které jsou uvedené skupiny.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-249">Collections are groups of similar objects that can be enumerated.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="7bbf9-250">podporuje specifickou syntaxi v [For Each... Další příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) , které umožňuje iteraci v rámci položky kolekce.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-250"> supports a specific syntax in the [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) that allows you to iterate through the items of a collection.</span></span> <span data-ttu-id="7bbf9-251">Kromě toho kolekce často umožňují používat <xref:Microsoft.VisualBasic.Collection.Item%2A> načíst elementy pomocí jejich indexu nebo je možné přidružit do jedinečného řetězce.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-251">Additionally, collections often allow you to use an <xref:Microsoft.VisualBasic.Collection.Item%2A> to retrieve elements by their index or by associating them with a unique string.</span></span> <span data-ttu-id="7bbf9-252">Kolekce může být jednodušší než pole vzhledem k tomu, že umožňují přidat nebo odebrat položky bez použití indexy.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-252">Collections can be easier to use than arrays because they allow you to add or remove items without using indexes.</span></span> <span data-ttu-id="7bbf9-253">Kvůli jejich snadné použití se kolekce často používají k ukládání formuláře a ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-253">Because of their ease of use, collections are often used to store forms and controls.</span></span>

## <a name="related-topics"></a><span data-ttu-id="7bbf9-254">Související témata</span><span class="sxs-lookup"><span data-stu-id="7bbf9-254">Related topics</span></span>  
 [<span data-ttu-id="7bbf9-255">Návod: Definování tříd</span><span class="sxs-lookup"><span data-stu-id="7bbf9-255">Walkthrough: Defining Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)  
 <span data-ttu-id="7bbf9-256">Poskytuje podrobný popis toho, jak vytvořit třídu.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-256">Provides a step-by-step description of how to create a class.</span></span>  

 [<span data-ttu-id="7bbf9-257">Vlastnosti a metody přetečení</span><span class="sxs-lookup"><span data-stu-id="7bbf9-257">Overloaded Properties and Methods</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)  
 <span data-ttu-id="7bbf9-258">Vlastnosti a metody přetečení</span><span class="sxs-lookup"><span data-stu-id="7bbf9-258">Overloaded Properties and Methods</span></span>  

 [<span data-ttu-id="7bbf9-259">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="7bbf9-259">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 <span data-ttu-id="7bbf9-260">Popisuje modifikátory dědičnosti, přepsání metody a vlastnosti, MyBase a MyClass.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-260">Covers inheritance modifiers, overriding methods and properties, MyClass, and MyBase.</span></span>  

 [<span data-ttu-id="7bbf9-261">Doba života objektu: Objekty vytváření a zničení</span><span class="sxs-lookup"><span data-stu-id="7bbf9-261">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 <span data-ttu-id="7bbf9-262">Popisuje vytvoření a uvolnění instancí třídy.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-262">Discusses creating and disposing of class instances.</span></span>  

 [<span data-ttu-id="7bbf9-263">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="7bbf9-263">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 <span data-ttu-id="7bbf9-264">Popisuje, jak vytvořit a použít anonymní typy, které umožňují vytvářet objekty bez nutnosti psaní definice třídy pro datový typ.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-264">Describes how to create and use anonymous types, which allow you to create objects without writing a class definition for the data type.</span></span>  

 [<span data-ttu-id="7bbf9-265">Inicializátory objektů: Pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="7bbf9-265">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 <span data-ttu-id="7bbf9-266">Popisuje inicializátory objektů, které se používají k vytvoření instance pojmenované a anonymní typy pomocí jeden výraz.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-266">Discusses object initializers, which are used to create instances of named and anonymous types by using a single expression.</span></span>  

 [<span data-ttu-id="7bbf9-267">Postupy: odvození názvů a typů v deklaracích anonymního typu vlastností</span><span class="sxs-lookup"><span data-stu-id="7bbf9-267">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 <span data-ttu-id="7bbf9-268">Vysvětluje, jak odvození názvů a typů v deklaracích anonymního typu vlastností.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-268">Explains how to infer property names and types in anonymous type declarations.</span></span> <span data-ttu-id="7bbf9-269">Obsahuje příklady odvození úspěšné a neúspěšné.</span><span class="sxs-lookup"><span data-stu-id="7bbf9-269">Provides examples of successful and unsuccessful inference.</span></span>

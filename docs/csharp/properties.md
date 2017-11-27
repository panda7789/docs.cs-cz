---
title: Vlastnosti
description: "Další informace o C# vlastnosti, které obsahují funkce pro ověření, počítaný hodnoty, opožděné vyhodnocení, a vlastnost změnit oznámení."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 04/03/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 6950d25a-bba1-4744-b7c7-a3cc90438c55
ms.openlocfilehash: 1ffacd52df89a955ebfa72dc58836211c7a58640
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2017
---
# <a name="properties"></a><span data-ttu-id="144c6-104">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="144c6-104">Properties</span></span>

<span data-ttu-id="144c6-105">Vlastnosti jsou prvotřídní občanů v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="144c6-105">Properties are first class citizens in C#.</span></span> <span data-ttu-id="144c6-106">Jazyk definuje syntaxi, která umožňuje vývojářům psát kód, který přesně vyjadřoval jejich záměr návrhu.</span><span class="sxs-lookup"><span data-stu-id="144c6-106">The language defines syntax that enables developers to write code that accurately expresses their design intent.</span></span>

<span data-ttu-id="144c6-107">Vlastnosti chovat jako pole, když k nim.</span><span class="sxs-lookup"><span data-stu-id="144c6-107">Properties behave like fields when they are accessed.</span></span>
<span data-ttu-id="144c6-108">Na rozdíl od pole, ale vlastnosti jsou u přistupující objekty, které definují příkazy spustit, když je vlastnost získat přístup nebo přiřazená implementován.</span><span class="sxs-lookup"><span data-stu-id="144c6-108">However, unlike fields, properties are implemented with accessors that define the statements executed when a property is accessed or assigned.</span></span>

## <a name="property-syntax"></a><span data-ttu-id="144c6-109">Syntaxe vlastností</span><span class="sxs-lookup"><span data-stu-id="144c6-109">Property Syntax</span></span>

<span data-ttu-id="144c6-110">Syntaxe vlastností v představuje přirozené rozšíření na pole.</span><span class="sxs-lookup"><span data-stu-id="144c6-110">The syntax for properties is a natural extension to fields.</span></span> <span data-ttu-id="144c6-111">Pole definuje umístění úložiště:</span><span class="sxs-lookup"><span data-stu-id="144c6-111">A field defines a storage location:</span></span>

```csharp
public class Person
{
    public string FirstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="144c6-112">Obsahuje deklarace pro definici vlastnosti `get` a `set` přistupujícího objektu, který načítá a přiřadí hodnota této vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="144c6-112">A property definition contains declarations for a `get` and `set` accessor that retrieves and assigns the value of that property:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="144c6-113">Syntaxe uvedené výše je *automaticky vlastnost* syntaxe.</span><span class="sxs-lookup"><span data-stu-id="144c6-113">The syntax shown above is the *auto property* syntax.</span></span> <span data-ttu-id="144c6-114">Kompilátor generuje umístění úložiště pro pole, který zálohuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="144c6-114">The compiler generates the storage location for the field that backs up the property.</span></span> <span data-ttu-id="144c6-115">Kompilátor také implementuje text `get` a `set` přistupující objekty.</span><span class="sxs-lookup"><span data-stu-id="144c6-115">The compiler also implements the body of the `get` and `set` accessors.</span></span>

<span data-ttu-id="144c6-116">V některých případech je nutné inicializovat vlastnost na jinou hodnotu než výchozí u tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="144c6-116">Sometimes, you need to initialize a property to a value other than the default for its type.</span></span>  <span data-ttu-id="144c6-117">C# umožňuje který nastavením hodnoty po pravé složené závorce pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="144c6-117">C# enables that by setting a value after the closing brace for the property.</span></span> <span data-ttu-id="144c6-118">Dáte možná přednost počáteční hodnota `FirstName` vlastnost, která má být prázdný řetězec místo `null`.</span><span class="sxs-lookup"><span data-stu-id="144c6-118">You may prefer the initial value for the `FirstName` property to be the empty string rather than `null`.</span></span> <span data-ttu-id="144c6-119">Zadáte, jak je uvedeno níže:</span><span class="sxs-lookup"><span data-stu-id="144c6-119">You would specify that as shown below:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; } = string.Empty;

    // remaining implementation removed from listing
}
```

<span data-ttu-id="144c6-120">To je velmi užitečné pro vlastnosti jen pro čtení, jak uvidíte později v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="144c6-120">This is most useful for read-only properties, as you'll see later in this topic.</span></span>

<span data-ttu-id="144c6-121">Můžete také definovat úložiště sami, jak je uvedeno níže:</span><span class="sxs-lookup"><span data-stu-id="144c6-121">You can also define the storage yourself, as shown below:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get { return firstName; }
        set { firstName = value; }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="144c6-122">Pokud implementace vlastností jeden výraz, můžete použít *výraz vozidlo členy* pro mechanismu získání nebo nastavení:</span><span class="sxs-lookup"><span data-stu-id="144c6-122">When a property implementation is a single expression, you can use *expression bodied members* for the getter or setter:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set => firstName = value;
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="144c6-123">Tato zjednodušenou syntaxi se použije v případě potřeby v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="144c6-123">This simplified syntax will be used where applicable throughout this topic.</span></span>

<span data-ttu-id="144c6-124">Definici vlastnosti uvedené výše je vlastnost pro čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="144c6-124">The property definition shown above is a read-write property.</span></span> <span data-ttu-id="144c6-125">Všimněte si klíčové slovo `value` v přistupující objekt set.</span><span class="sxs-lookup"><span data-stu-id="144c6-125">Notice the keyword `value` in the set accessor.</span></span> <span data-ttu-id="144c6-126">`set` Přistupujícího objektu má vždy jeden parametr s názvem `value`.</span><span class="sxs-lookup"><span data-stu-id="144c6-126">The `set` accessor always has a single parameter named `value`.</span></span> <span data-ttu-id="144c6-127">`get` Přistupujícího objektu musí vracet hodnotu, která je převést na typ vlastnosti (`string` v tomto příkladu).</span><span class="sxs-lookup"><span data-stu-id="144c6-127">The `get` accessor must return a value that is convertible to the type of the property (`string` in this example).</span></span>
 
<span data-ttu-id="144c6-128">To je základní informace o syntaxi.</span><span class="sxs-lookup"><span data-stu-id="144c6-128">That's the basics of the syntax.</span></span> <span data-ttu-id="144c6-129">Existuje mnoho různých variant, které podporují celou řadu různých idioms.</span><span class="sxs-lookup"><span data-stu-id="144c6-129">There are many different variations that support a variety of different design idioms.</span></span> <span data-ttu-id="144c6-130">Umožňuje prozkoumat ty a další možnosti syntaxe pro každou.</span><span class="sxs-lookup"><span data-stu-id="144c6-130">Let's explore those, and learn the syntax options for each.</span></span>

## <a name="scenarios"></a><span data-ttu-id="144c6-131">Scénáře</span><span class="sxs-lookup"><span data-stu-id="144c6-131">Scenarios</span></span>

<span data-ttu-id="144c6-132">Výše uvedených příkladech vám ukázal, jedním z nejjednodušších definice vlastnost: vlastnost pro čtení a zápis bez ověřování.</span><span class="sxs-lookup"><span data-stu-id="144c6-132">The examples above showed one of the simplest cases of property definition: a read-write property with no validation.</span></span> <span data-ttu-id="144c6-133">Zápis kódu chcete `get` a `set` přístupové objekty, můžete vytvořit mnoho různých scénářů.</span><span class="sxs-lookup"><span data-stu-id="144c6-133">By writing the code you want in the `get` and `set` accessors, you can create many different scenarios.</span></span>

### <a name="validation"></a><span data-ttu-id="144c6-134">Ověřování</span><span class="sxs-lookup"><span data-stu-id="144c6-134">Validation</span></span>

<span data-ttu-id="144c6-135">Můžete napsat kód ve `set` přistupujícího objektu hodnoty reprezentována vlastnost musí být vždy platné.</span><span class="sxs-lookup"><span data-stu-id="144c6-135">You can write code in the `set` accessor to ensure that the values represented by a property are always valid.</span></span> <span data-ttu-id="144c6-136">Předpokládejme například, pro jedno pravidlo `Person` třída je, že název nemůže být prázdný ani prázdné.</span><span class="sxs-lookup"><span data-stu-id="144c6-136">For example, suppose one rule for the `Person` class is that the name cannot be blank, or whitespace.</span></span> <span data-ttu-id="144c6-137">By zápisu, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="144c6-137">You would write that as follows:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            firstName = value;
        }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="144c6-138">V předchozím příkladu vynucuje pravidlo, že jméno nesmí být prázdný ani prázdné.</span><span class="sxs-lookup"><span data-stu-id="144c6-138">The example above enforces the rule that the first name must not be blank, or whitespace.</span></span> <span data-ttu-id="144c6-139">Pokud vývojář zapíše</span><span class="sxs-lookup"><span data-stu-id="144c6-139">If a developer writes</span></span>

```csharp
hero.FirstName = "";
```

<span data-ttu-id="144c6-140">Vyvolá tuto přiřazení `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="144c6-140">That assignment throws an `ArgumentException`.</span></span> <span data-ttu-id="144c6-141">Protože vlastnosti musí mít typ vrácené hodnoty void, sestavu chyb v přistupující objekt set podle došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="144c6-141">Because a property set accessor must have a void return type, you report errors in the set accessor by throwing an exception.</span></span>

<span data-ttu-id="144c6-142">Který je jednoduchý případ ověření.</span><span class="sxs-lookup"><span data-stu-id="144c6-142">That is a simple case of validation.</span></span> <span data-ttu-id="144c6-143">Tato stejná syntaxe k ničemu potřeba ve vašem scénáři můžete rozšířit.</span><span class="sxs-lookup"><span data-stu-id="144c6-143">You can extend this same syntax to anything needed in your scenario.</span></span> <span data-ttu-id="144c6-144">Můžete zkontrolovat vztahy mezi různé vlastnosti nebo vyhodnotit proti případné externí podmínky.</span><span class="sxs-lookup"><span data-stu-id="144c6-144">You can check the relationships between different properties, or validate against any external conditions.</span></span> <span data-ttu-id="144c6-145">Všechny platné příkazy jazyka C# jsou platné v přistupujícího objektu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="144c6-145">Any valid C# statements are valid in a property accessor.</span></span>

### <a name="read-only"></a><span data-ttu-id="144c6-146">jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="144c6-146">Read-only</span></span>

<span data-ttu-id="144c6-147">V tomto okamžiku jsou všechny definice vlastností, které jste viděli vlastností čtení/zápisu s veřejné přistupující objekty.</span><span class="sxs-lookup"><span data-stu-id="144c6-147">Up to this point, all the property definitions you have seen are read/write properties with public accessors.</span></span> <span data-ttu-id="144c6-148">Toto není platné pouze pro usnadnění přístupu pro vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="144c6-148">That's not the only valid accessibility for properties.</span></span>
<span data-ttu-id="144c6-149">Můžete vytvořit vlastnosti jen pro čtení, nebo poskytnout jiné usnadnění přístupu k sadě a získat přístupové objekty.</span><span class="sxs-lookup"><span data-stu-id="144c6-149">You can create read-only properties, or give different accessibility to the set and get accessors.</span></span> <span data-ttu-id="144c6-150">Předpokládat, že vaše `Person` třída měli jenom povolit změna hodnoty `FirstName` vlastnost z jiné metody v dané třídě.</span><span class="sxs-lookup"><span data-stu-id="144c6-150">Suppose that your `Person` class should only enable changing the value of the `FirstName` property from other methods in that class.</span></span> <span data-ttu-id="144c6-151">Může poskytnout přistupující objekt set `private` usnadnění místo `public`:</span><span class="sxs-lookup"><span data-stu-id="144c6-151">You could give the set accessor `private` accessibility instead of `public`:</span></span>

```csharp
public class Person
{
    public string FirstName { get; private set; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="144c6-152">Nyní `FirstName` vlastnost je přístupná z žádný kód, ale lze přiřadit pouze z jiných kódu v `Person` třídy.</span><span class="sxs-lookup"><span data-stu-id="144c6-152">Now, the `FirstName` property can be accessed from any code, but it can only be assigned from other code in the `Person` class.</span></span>

<span data-ttu-id="144c6-153">Můžete přidat všechny – modifikátor přístupu omezující buď sadu nebo získat přístupové objekty.</span><span class="sxs-lookup"><span data-stu-id="144c6-153">You can add any restrictive access modifier to either the set or get accessors.</span></span> <span data-ttu-id="144c6-154">Žádné – modifikátor přístupu u jednotlivých přistupujícího objektu musí být omezenější než – modifikátor přístupu na definici vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="144c6-154">Any access modifier you place on the individual accessor must be more limited than the access modifier on the property definition.</span></span> <span data-ttu-id="144c6-155">Výše je právní protože `FirstName` vlastnost je `public`, ale je přistupující objekt set `private`.</span><span class="sxs-lookup"><span data-stu-id="144c6-155">The above is legal because the `FirstName` property is `public`, but the set accessor is `private`.</span></span> <span data-ttu-id="144c6-156">Nelze deklarovat `private` vlastnost s `public` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="144c6-156">You could not declare a `private` property with a `public` accessor.</span></span> <span data-ttu-id="144c6-157">Vlastnost deklarace lze také deklarovat `protected`, `internal`, `protected internal`, `private protected` nebo i `private`.</span><span class="sxs-lookup"><span data-stu-id="144c6-157">Property declarations can also be declared `protected`, `internal`, `protected internal`, `private protected` or even `private`.</span></span>   

<span data-ttu-id="144c6-158">Taky je platné umístit na víc omezující modifikátor `get` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="144c6-158">It is also legal to place the more restrictive modifier on the `get` accessor.</span></span> <span data-ttu-id="144c6-159">Například můžete mít `public` vlastnost, ale omezit `get` přistupujícího objektu `private`.</span><span class="sxs-lookup"><span data-stu-id="144c6-159">For example, you could have a `public` property, but restrict the `get` accessor to `private`.</span></span> <span data-ttu-id="144c6-160">Tento scénář se zřídka provádí v praxi.</span><span class="sxs-lookup"><span data-stu-id="144c6-160">That scenario is rarely done in practice.</span></span>

<span data-ttu-id="144c6-161">Úpravy vlastností můžete taky omezit tak, aby lze nastavit pouze v konstruktoru nebo inicializátoru vlastnost.</span><span class="sxs-lookup"><span data-stu-id="144c6-161">You can also restrict modifications to a property so that it can only be set in a constructor or a property initializer.</span></span> <span data-ttu-id="144c6-162">Můžete upravit `Person` třídy tak následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="144c6-162">You can modify the `Person` class so as follows:</span></span>

```csharp
public class Person
{
    public Person(string firstName)
    {
        this.FirstName = firstName;
    }

    public string FirstName { get; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="144c6-163">Tato funkce se nejčastěji používá pro inicializaci kolekce, které jsou zveřejněné jako jen pro čtení vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="144c6-163">This feature is most commonly used for initializing collections that are exposed as read-only properties:</span></span>

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a><span data-ttu-id="144c6-164">Počítané vlastnosti</span><span class="sxs-lookup"><span data-stu-id="144c6-164">Computed Properties</span></span>

<span data-ttu-id="144c6-165">Vlastnost není nutné jednoduše vrátí hodnotu pole členů.</span><span class="sxs-lookup"><span data-stu-id="144c6-165">A property does not need to simply return the value of a member field.</span></span> <span data-ttu-id="144c6-166">Můžete vytvořit vlastnosti, které vracejí vypočtená hodnota.</span><span class="sxs-lookup"><span data-stu-id="144c6-166">You can create properties that return a computed value.</span></span> <span data-ttu-id="144c6-167">Umožňuje rozšířit `Person` objekt, který chcete vrátit úplný název, počítaný zřetězením názvy první a poslední:</span><span class="sxs-lookup"><span data-stu-id="144c6-167">Let's expand the `Person` object to return the full name, computed by concatenating the first and last names:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName { get { return $"{FirstName} {LastName}"; } }
}
```

<span data-ttu-id="144c6-168">V příkladu výše používá *řetězec interpolace* syntaxe k vytvoření formátovaný řetězec pro úplný název.</span><span class="sxs-lookup"><span data-stu-id="144c6-168">The example above uses the *String Interpolation* syntax to create the formatted string for the full name.</span></span>

<span data-ttu-id="144c6-169">Můžete také použít *výraz vozidlo členy*, který poskytuje více stručného způsob, jak vytvořit použití počítaných `FullName` vlastnost:</span><span class="sxs-lookup"><span data-stu-id="144c6-169">You can also use *Expression-bodied Members*, which provides a more succinct way to create the computed `FullName` property:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName =>  $"{FirstName} {LastName}";
}
```
 
<span data-ttu-id="144c6-170">*Výraz vozidlo členy* použít *výrazu lambda* syntaxe zadat metodu, která obsahují jeden výraz.</span><span class="sxs-lookup"><span data-stu-id="144c6-170">*Expression-bodied Members* use the *lambda expression* syntax to define a method that contain a single expression.</span></span> <span data-ttu-id="144c6-171">Tento výraz zde, vrátí úplný název pro objekt osoby.</span><span class="sxs-lookup"><span data-stu-id="144c6-171">Here, that expression returns the full name for the person object.</span></span>

### <a name="lazy-evaluated-properties"></a><span data-ttu-id="144c6-172">Opožděné vyhodnotí vlastnosti</span><span class="sxs-lookup"><span data-stu-id="144c6-172">Lazy Evaluated Properties</span></span>

<span data-ttu-id="144c6-173">Můžete kombinovat koncept vypočítané vlastnosti s úložištěm a vytvořit *opožděné vyhodnocení vlastnost*.</span><span class="sxs-lookup"><span data-stu-id="144c6-173">You can mix the concept of a computed property with storage and create a *lazy evaluated property*.</span></span>  <span data-ttu-id="144c6-174">Například můžete aktualizovat `FullName` vlastnost tak, aby formátování řetězce pouze došlo při prvním byl přístup:</span><span class="sxs-lookup"><span data-stu-id="144c6-174">For example, you could update the `FullName` property so that the string formatting only happened the first time it was accessed:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

<span data-ttu-id="144c6-175">Výše uvedený kód obsahuje chybu, když.</span><span class="sxs-lookup"><span data-stu-id="144c6-175">The above code contains a bug though.</span></span> <span data-ttu-id="144c6-176">Pokud kód aktualizace hodnotu buď `FirstName` nebo `LastName` vlastnost, dříve vyhodnotí `fullName` pole je neplatné.</span><span class="sxs-lookup"><span data-stu-id="144c6-176">If code updates the value of either the `FirstName` or `LastName` property, the previously evaluated `fullName` field is invalid.</span></span> <span data-ttu-id="144c6-177">Je potřeba aktualizovat `set` přístupových objektů `FirstName` a `LastName` vlastnost tak, aby `fullName` pole se vypočítává znovu:</span><span class="sxs-lookup"><span data-stu-id="144c6-177">You need to update the `set` accessors of the `FirstName` and `LastName` property so that the `fullName` field is calculated again:</span></span>

```csharp
public class Person
{
    private string firstName;
    public string FirstName
    {
        get => firstName;
        set
        {
            firstName = value;
            fullName = null;
        }
    }

    private string lastName;
    public string LastName
    {
        get => lastName;
        set
        {
            lastName = value;
            fullName = null;
        }
    }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

<span data-ttu-id="144c6-178">Vyhodnotí této poslední verzi `FullName` vlastnost pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="144c6-178">This final version evaluates the `FullName` property only when needed.</span></span>
<span data-ttu-id="144c6-179">Pokud je platný dříve počítané verze, se používá.</span><span class="sxs-lookup"><span data-stu-id="144c6-179">If the previously calculated version is valid, it's used.</span></span> <span data-ttu-id="144c6-180">Další změnou stavu by způsobila neplatnost dříve počítané verze, bude přepočítána.</span><span class="sxs-lookup"><span data-stu-id="144c6-180">If another state change invalidates the previously calculated version, it will be recalculated.</span></span> <span data-ttu-id="144c6-181">Vývojáři, které používají tuto třídu není potřeba znát podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="144c6-181">Developers that use this class do not need to know the details of the implementation.</span></span> <span data-ttu-id="144c6-182">Žádná z těchto interní změny mají vliv na použití objektu osoby.</span><span class="sxs-lookup"><span data-stu-id="144c6-182">None of these internal changes affect the use of the Person object.</span></span> <span data-ttu-id="144c6-183">To je klíče důvod pomocí vlastnosti vystavit data členům v objektu.</span><span class="sxs-lookup"><span data-stu-id="144c6-183">That's the key reason for using Properties to expose data members of an object.</span></span>
 
### <a name="inotifypropertychanged"></a><span data-ttu-id="144c6-184">Rozhraní INotifyPropertyChanged.</span><span class="sxs-lookup"><span data-stu-id="144c6-184">INotifyPropertyChanged</span></span>

<span data-ttu-id="144c6-185">Poslední scénář, kde je potřeba psát kód v přistupujícího objektu vlastnosti je podpora `INotifyPropertyChanged` rozhraní sloužící k upozornění klientů vazby dat, která byla hodnota změněna.</span><span class="sxs-lookup"><span data-stu-id="144c6-185">A final scenario where you need to write code in a property accessor is to support the `INotifyPropertyChanged` interface used to notify data binding clients that a value has changed.</span></span> <span data-ttu-id="144c6-186">Při změně hodnoty vlastnosti, vyvolá objekt `PropertyChanged` události označit změny.</span><span class="sxs-lookup"><span data-stu-id="144c6-186">When the value of a property changes, the object raises the `PropertyChanged` event to indicate the change.</span></span> <span data-ttu-id="144c6-187">Datové vazby knihovny, pak aktualizovat zobrazení prvky založené na tuto změnu.</span><span class="sxs-lookup"><span data-stu-id="144c6-187">The data binding libraries, in turn, update display elements based on that change.</span></span> <span data-ttu-id="144c6-188">Následující kód ukazuje, jak můžete implementovat `INotifyPropertyChanged` pro `FirstName` vlastnost této třídy osoby.</span><span class="sxs-lookup"><span data-stu-id="144c6-188">The code below shows how you would implement `INotifyPropertyChanged` for the `FirstName` property of this person class.</span></span>

```csharp
public class Person : INotifyPropertyChanged
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            if (value != firstName)
            {
                PropertyChanged?.Invoke(this, 
                    new PropertyChangedEventArgs(nameof(FirstName)));
            }
            firstName = value;
        }
    }
    private string firstName;

    public event PropertyChangedEventHandler PropertyChanged;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="144c6-189">`?.` Operátor je volána *null podmíněný operátor*.</span><span class="sxs-lookup"><span data-stu-id="144c6-189">The `?.` operator is called the *null conditional operator*.</span></span> <span data-ttu-id="144c6-190">Před vyhodnocením pravé straně operátoru zkontroluje pro odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="144c6-190">It checks for a null reference before evaluating the right side of the operator.</span></span> <span data-ttu-id="144c6-191">Konečným výsledkem je, že pokud neexistují žádné odběratele, kteří mají `PropertyChanged` událostí, neprovede se kód pro vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="144c6-191">The end result is that if there are no subscribers to the `PropertyChanged` event, the code to raise the event doesn't execute.</span></span> <span data-ttu-id="144c6-192">By throw `NullReferenceException` bez zkontrolujte v takovém případě.</span><span class="sxs-lookup"><span data-stu-id="144c6-192">It would throw a `NullReferenceException` without this check in that case.</span></span> <span data-ttu-id="144c6-193">Naleznete na stránce na [ `events` ](delegates-events.md) další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="144c6-193">See the page on [`events`](delegates-events.md) for more details.</span></span> <span data-ttu-id="144c6-194">Tento příklad také používá nové `nameof` operátor převést z názvu symbolu vlastnost textové reprezentace.</span><span class="sxs-lookup"><span data-stu-id="144c6-194">This example also uses the new `nameof` operator to convert from the property name symbol to its text representation.</span></span>
<span data-ttu-id="144c6-195">Pomocí `nameof` můžete snížit počet chyb, které jste zadali název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="144c6-195">Using `nameof` can reduce errors where you have mistyped the name of the property.</span></span>

<span data-ttu-id="144c6-196">Znovu jedná se o příklad případu, kde můžete napsat kód ve vaší přístupových objektů pro podporu scénáře, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="144c6-196">Again, this is an example of a case where you can write code in your accessors to support the scenarios you need.</span></span>

## <a name="summing-up"></a><span data-ttu-id="144c6-197">Shrnutí</span><span class="sxs-lookup"><span data-stu-id="144c6-197">Summing up</span></span>

<span data-ttu-id="144c6-198">Vlastnosti jsou formuláře inteligentních polí ve třídě nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="144c6-198">Properties are a form of smart fields in a class or object.</span></span> <span data-ttu-id="144c6-199">Z mimo objekt, zobrazí se jako pole v objektu.</span><span class="sxs-lookup"><span data-stu-id="144c6-199">From outside the object, they appear like fields in the object.</span></span> <span data-ttu-id="144c6-200">Však vlastnosti se dají implementovat pomocí úplné palety funkcí jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="144c6-200">However, properties can be implemented using the full palette of C# functionality.</span></span>
<span data-ttu-id="144c6-201">Můžete zadat ověřování, jiný usnadnění, opožděné vyhodnocení nebo všechny požadavky potřebné pro vaše scénáře.</span><span class="sxs-lookup"><span data-stu-id="144c6-201">You can provide validation, different accessibility, lazy evaluation, or any requirements your scenarios need.</span></span>

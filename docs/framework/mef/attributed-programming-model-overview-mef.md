---
title: Přehled modelu programování s přidělenými atributy (MEF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MEF, attributed programming model
- attributed programming model [MEF]
ms.assetid: 49b787ff-2741-4836-ad51-c3017dc592d4
ms.openlocfilehash: c6b1093d2e821a55cc5513b077a270748a780b71
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347632"
---
# <a name="attributed-programming-model-overview-mef"></a><span data-ttu-id="62779-102">Přehled modelu programování s přidělenými atributy (MEF)</span><span class="sxs-lookup"><span data-stu-id="62779-102">Attributed Programming Model Overview (MEF)</span></span>

<span data-ttu-id="62779-103">V Managed Extensibility Framework (MEF) je *programovací model* specifickou metodou pro definování sady konceptuálních objektů, na kterých funguje MEF.</span><span class="sxs-lookup"><span data-stu-id="62779-103">In the Managed Extensibility Framework (MEF), a *programming model* is a particular method of defining the set of conceptual objects on which MEF operates.</span></span> <span data-ttu-id="62779-104">Tyto koncepční objekty zahrnují součásti, importy a exporty.</span><span class="sxs-lookup"><span data-stu-id="62779-104">These conceptual objects include parts, imports, and exports.</span></span> <span data-ttu-id="62779-105">MEF používá tyto objekty, ale neurčuje, jak by měly být reprezentovány.</span><span class="sxs-lookup"><span data-stu-id="62779-105">MEF uses these objects, but does not specify how they should be represented.</span></span> <span data-ttu-id="62779-106">Proto je možné využít širokou škálu programovacích modelů, včetně přizpůsobených programovacích modelů.</span><span class="sxs-lookup"><span data-stu-id="62779-106">Therefore, a wide variety of programming models are possible, including customized programming models.</span></span>

<span data-ttu-id="62779-107">Výchozím programovacím modelem používaným v MEF je *model programování s atributy*.</span><span class="sxs-lookup"><span data-stu-id="62779-107">The default programming model used in MEF is the *attributed programming model*.</span></span> <span data-ttu-id="62779-108">V částech modelu programování s atributy jsou importy, exporty a další objekty definovány s atributy, které upraví běžné .NET Framework třídy.</span><span class="sxs-lookup"><span data-stu-id="62779-108">In the attributed programming model parts, imports, exports, and other objects are defined with attributes that decorate ordinary .NET Framework classes.</span></span> <span data-ttu-id="62779-109">V tomto tématu se dozvíte, jak pomocí atributů poskytovaných programovacím modelem s atributy vytvořit aplikaci MEF.</span><span class="sxs-lookup"><span data-stu-id="62779-109">This topic explains how to use the attributes provided by the attributed programming model to create a MEF application.</span></span>

<a name="import_and_export_basics"></a>

## <a name="import-and-export-basics"></a><span data-ttu-id="62779-110">Základy importu a exportu</span><span class="sxs-lookup"><span data-stu-id="62779-110">Import and Export Basics</span></span>

<span data-ttu-id="62779-111">*Export* je hodnota, kterou část poskytuje jiným částem v kontejneru a *Import* je požadavek, aby část, která je vyjádřena v kontejneru, byla vyplněna z dostupných exportů.</span><span class="sxs-lookup"><span data-stu-id="62779-111">An *export* is a value that a part provides to other parts in the container, and an *import* is a requirement that a part expresses to the container, to be filled from the available exports.</span></span> <span data-ttu-id="62779-112">V programovacím modelu s atributy jsou importy a exporty deklarovány pomocí tříd upravení nebo členů `Import` s `Export` atributy a.</span><span class="sxs-lookup"><span data-stu-id="62779-112">In the attributed programming model, imports and exports are declared by decorating classes or members with the `Import` and `Export` attributes.</span></span> <span data-ttu-id="62779-113">`Export` Atribut může vytřídit třídu, pole, vlastnost nebo metodu, zatímco `Import` atribut může setřídit pole, vlastnost nebo parametr konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="62779-113">The `Export` attribute can decorate a class, field, property, or method, while the `Import` attribute can decorate a field, property, or constructor parameter.</span></span>

<span data-ttu-id="62779-114">Aby se import shodoval s exportem, musí mít import a export stejný *kontrakt*.</span><span class="sxs-lookup"><span data-stu-id="62779-114">In order for an import to be matched with an export, the import and export must have the same *contract*.</span></span> <span data-ttu-id="62779-115">Smlouva se skládá z řetězce, který se označuje jako *název kontraktu*a typ exportovaného nebo importovaného objektu, který se označuje jako *Typ kontraktu*.</span><span class="sxs-lookup"><span data-stu-id="62779-115">The contract consists of a string, called the *contract name*, and the type of the exported or imported object, called the *contract type*.</span></span> <span data-ttu-id="62779-116">Pouze v případě, že shoda názvu kontraktu a typu smlouvy je exportem, který je považován za splnění konkrétního importu.</span><span class="sxs-lookup"><span data-stu-id="62779-116">Only if both the contract name and contract type match is an export considered to fulfill a particular import.</span></span>

<span data-ttu-id="62779-117">Buď nebo oba parametry kontraktu mohou být implicitní nebo explicitní.</span><span class="sxs-lookup"><span data-stu-id="62779-117">Either or both of the contract parameters can be implicit or explicit.</span></span> <span data-ttu-id="62779-118">Následující kód ukazuje třídu, která deklaruje základní import.</span><span class="sxs-lookup"><span data-stu-id="62779-118">The following code shows a class that declares a basic import.</span></span>

```vb
Public Class MyClass1
    <Import()>
    Public Property MyAddin As IMyAddin
End Class
```

```csharp
public class MyClass
{
    [Import]
    public IMyAddin MyAddin { get; set; }
}
```

<span data-ttu-id="62779-119">V tomto importu nemá `Import` atribut ani typ kontraktu ani připojený parametr názvu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="62779-119">In this import, the `Import` attribute has neither a contract type nor a contract name parameter attached.</span></span> <span data-ttu-id="62779-120">Proto obě budou odvozeny z dekorované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="62779-120">Therefore, both will be inferred from the decorated property.</span></span> <span data-ttu-id="62779-121">V takovém případě bude typ `IMyAddin`kontraktu a název kontraktu bude jedinečným řetězcem vytvořeným z typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="62779-121">In this case, the contract type will be `IMyAddin`, and the contract name will be a unique string created from the contract type.</span></span> <span data-ttu-id="62779-122">(Jinými slovy, název kontraktu bude odpovídat pouze exportům, jejichž názvy jsou také odvozeny od typu `IMyAddin`.)</span><span class="sxs-lookup"><span data-stu-id="62779-122">(In other words, the contract name will match only exports whose names are also inferred from the type `IMyAddin`.)</span></span>

<span data-ttu-id="62779-123">Následující příklad ukazuje export, který odpovídá předchozímu importu.</span><span class="sxs-lookup"><span data-stu-id="62779-123">The following shows an export that matches the previous import.</span></span>

```vb
<Export(GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export(typeof(IMyAddin))]
public class MyLogger : IMyAddin { }
```

<span data-ttu-id="62779-124">V tomto exportu je `IMyAddin` typ kontraktu, protože je zadán jako parametr `Export` atributu.</span><span class="sxs-lookup"><span data-stu-id="62779-124">In this export, the contract type is `IMyAddin` because it is specified as a parameter of the `Export` attribute.</span></span> <span data-ttu-id="62779-125">Exportovaný typ musí být buď stejný jako typ kontraktu, odvozený od typu kontraktu, nebo implementovat typ kontraktu, pokud se jedná o rozhraní.</span><span class="sxs-lookup"><span data-stu-id="62779-125">The exported type must be either the same as the contract type, derive from the contract type, or implement the contract type if it is an interface.</span></span> <span data-ttu-id="62779-126">V tomto exportu samotný typ `MyLogger` implementuje rozhraní. `IMyAddin`</span><span class="sxs-lookup"><span data-stu-id="62779-126">In this export, the actual type `MyLogger` implements the interface `IMyAddin`.</span></span> <span data-ttu-id="62779-127">Název kontraktu je odvozený od typu kontraktu, což znamená, že tento export bude odpovídat předchozímu importu.</span><span class="sxs-lookup"><span data-stu-id="62779-127">The contract name is inferred from the contract type, which means that this export will match the previous import.</span></span>

> [!NOTE]
> <span data-ttu-id="62779-128">Exporty a importy by měly být obvykle deklarovány ve veřejných třídách nebo členech.</span><span class="sxs-lookup"><span data-stu-id="62779-128">Exports and imports should usually be declared on public classes or members.</span></span> <span data-ttu-id="62779-129">Další deklarace jsou podporovány, ale export nebo import privátního, chráněného nebo interního člena přerušuje model izolace pro danou část a proto se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="62779-129">Other declarations are supported, but exporting or importing a private, protected, or internal member breaks the isolation model for the part and is therefore not recommended.</span></span>

<span data-ttu-id="62779-130">Typ kontraktu se musí přesně shodovat s exportem a importem, aby se dalo považovat za shodu.</span><span class="sxs-lookup"><span data-stu-id="62779-130">The contract type must match exactly for the export and import to be considered a match.</span></span> <span data-ttu-id="62779-131">Vezměte v úvahu následující export.</span><span class="sxs-lookup"><span data-stu-id="62779-131">Consider the following export.</span></span>

```vb
<Export()> 'WILL NOT match the previous import!
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export] //WILL NOT match the previous import!
public class MyLogger : IMyAddin { }
```

<span data-ttu-id="62779-132">V tomto exportu je `MyLogger` jako typ kontraktu místo. `IMyAddin`</span><span class="sxs-lookup"><span data-stu-id="62779-132">In this export, the contract type is `MyLogger` instead of `IMyAddin`.</span></span> <span data-ttu-id="62779-133">I když `MyLogger` implementují `IMyAddin`, a proto lze přetypovat na `IMyAddin` objekt, tento export nebude odpovídat předchozímu importu, protože typy kontraktů nejsou stejné.</span><span class="sxs-lookup"><span data-stu-id="62779-133">Even though `MyLogger` implements `IMyAddin`, and therefore could be cast to an `IMyAddin` object, this export will not match the previous import because the contract types are not the same.</span></span>

<span data-ttu-id="62779-134">Obecně není nutné zadávat název kontraktu a většina kontraktů by měla být definována v souvislosti s typem a metadaty kontraktu.</span><span class="sxs-lookup"><span data-stu-id="62779-134">In general, it is not necessary to specify the contract name, and most contracts should be defined in terms of the contract type and metadata.</span></span> <span data-ttu-id="62779-135">Za určitých okolností je však důležité zadat název kontraktu přímo.</span><span class="sxs-lookup"><span data-stu-id="62779-135">However, under certain circumstances, it is important to specify the contract name directly.</span></span> <span data-ttu-id="62779-136">Nejběžnějším případem je, že třída exportuje několik hodnot, které sdílejí společný typ, jako jsou primitivní.</span><span class="sxs-lookup"><span data-stu-id="62779-136">The most common case is when a class exports several values that share a common type, such as primitives.</span></span> <span data-ttu-id="62779-137">Název kontraktu lze zadat jako první parametr atributu `Import` or. `Export`</span><span class="sxs-lookup"><span data-stu-id="62779-137">The contract name can be specified as the first parameter of the `Import` or `Export` attribute.</span></span> <span data-ttu-id="62779-138">Následující kód ukazuje import a export se zadaným názvem kontraktu `MajorRevision`.</span><span class="sxs-lookup"><span data-stu-id="62779-138">The following code shows an import and an export with a specified contract name of `MajorRevision`.</span></span>

```vb
Public Class MyExportClass

    'This one will match
    <Export("MajorRevision")>
    Public ReadOnly Property MajorRevision As Integer
        Get
            Return 4
        End Get
    End Property

    <Export("MinorRevision")>
    Public ReadOnly Property MinorRevision As Integer
        Get
            Return 16
        End Get
    End Property
End Class
```

```csharp
public class MyClass
{
    [Import("MajorRevision")]
    public int MajorRevision { get; set; }
}

public class MyExportClass
{
    [Export("MajorRevision")] //This one will match.
    public int MajorRevision = 4;

    [Export("MinorRevision")]
    public int MinorRevision = 16;
}
```

<span data-ttu-id="62779-139">Pokud není zadán typ kontraktu, bude stále odvozen od typu importu nebo exportu.</span><span class="sxs-lookup"><span data-stu-id="62779-139">If the contract type is not specified, it will still be inferred from the type of the import or export.</span></span> <span data-ttu-id="62779-140">Nicméně i v případě, že je název kontraktu zadán explicitně, musí se typ kontraktu přesně shodovat s importem a exportem, aby bylo možné považovat za shodu.</span><span class="sxs-lookup"><span data-stu-id="62779-140">However, even if the contract name is specified explicitly, the contract type must also match exactly for the import and export to be considered a match.</span></span> <span data-ttu-id="62779-141">Například pokud by `MajorRevision` pole bylo typu String, odvozené typy kontraktu se neshodují a export by neodpovídal importu, i když má stejný název kontraktu.</span><span class="sxs-lookup"><span data-stu-id="62779-141">For example, if the `MajorRevision` field was a string, the inferred contract types would not match and the export would not match the import, despite having the same contract name.</span></span>

### <a name="importing-and-exporting-a-method"></a><span data-ttu-id="62779-142">Import a export metody</span><span class="sxs-lookup"><span data-stu-id="62779-142">Importing and Exporting a Method</span></span>

<span data-ttu-id="62779-143">`Export` Atribut může také roztřídit metodu stejným způsobem jako třída, vlastnost nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="62779-143">The `Export` attribute can also decorate a method, in the same way as a class, property, or function.</span></span> <span data-ttu-id="62779-144">Exporty metod musí určovat typ kontraktu nebo název kontraktu, protože typ nelze odvodit.</span><span class="sxs-lookup"><span data-stu-id="62779-144">Method exports must specify a contract type or contract name, as the type cannot be inferred.</span></span> <span data-ttu-id="62779-145">Zadaný typ může být buď vlastní delegát, nebo obecný typ, například `Func`.</span><span class="sxs-lookup"><span data-stu-id="62779-145">The specified type can be either a custom delegate or a generic type, such as `Func`.</span></span> <span data-ttu-id="62779-146">Následující třída exportuje metodu s názvem `DoSomething`.</span><span class="sxs-lookup"><span data-stu-id="62779-146">The following class exports a method named `DoSomething`.</span></span>

```vb
Public Class MyAddin

    'Explicitly specifying a generic type
    <Export(GetType(Func(Of Integer, String)))>
    Public Function DoSomething(ByVal TheParam As Integer) As String
        Return Nothing 'Function body goes here
    End Function

End Class
```

```csharp
public class MyAddin
{
    //Explicitly specifying a generic type.
    [Export(typeof(Func<int, string>))]
    public string DoSomething(int TheParam);
}
```

<span data-ttu-id="62779-147">V této třídě `DoSomething` metoda přijímá jeden `int` parametr a vrátí. `string`</span><span class="sxs-lookup"><span data-stu-id="62779-147">In this class, the `DoSomething` method takes a single `int` parameter and returns a `string`.</span></span> <span data-ttu-id="62779-148">Aby bylo možné tento export vyhledat, musí součást importu deklarovat příslušného člena.</span><span class="sxs-lookup"><span data-stu-id="62779-148">To match this export, the importing part must declare an appropriate member.</span></span> <span data-ttu-id="62779-149">Následující třída importuje `DoSomething` metodu.</span><span class="sxs-lookup"><span data-stu-id="62779-149">The following class imports the `DoSomething` method.</span></span>

```vb
Public Class MyClass1

    'Contract name must match!
    <Import()>
    Public Property MajorRevision As Func(Of Integer, String)
End Class
```

```csharp
public class MyClass
{
    [Import] //Contract name must match!
    public Func<int, string> DoSomething { get; set; }
}
```

<span data-ttu-id="62779-150">Další informace o použití `Func<T, T>` objektu naleznete v tématu. <xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="62779-150">For more information about how to use of the `Func<T, T>` object, see <xref:System.Func%602>.</span></span>

<a name="types_of_imports"></a>

## <a name="types-of-imports"></a><span data-ttu-id="62779-151">Typy importů</span><span class="sxs-lookup"><span data-stu-id="62779-151">Types of Imports</span></span>

<span data-ttu-id="62779-152">Rozhraní MEF podporují několik typů importu, včetně dynamického, opožděného, předpokladu a volitelného.</span><span class="sxs-lookup"><span data-stu-id="62779-152">MEF support several import types, including dynamic, lazy, prerequisite, and optional.</span></span>

### <a name="dynamic-imports"></a><span data-ttu-id="62779-153">Dynamické importy</span><span class="sxs-lookup"><span data-stu-id="62779-153">Dynamic Imports</span></span>

<span data-ttu-id="62779-154">V některých případech je možné, že import třídy bude odpovídat exportům libovolného typu, který má konkrétní název kontraktu.</span><span class="sxs-lookup"><span data-stu-id="62779-154">In some cases, the importing class may want to match exports of any type that have a particular contract name.</span></span> <span data-ttu-id="62779-155">V tomto scénáři třída může deklarovat *dynamický import*.</span><span class="sxs-lookup"><span data-stu-id="62779-155">In this scenario, the class can declare a *dynamic import*.</span></span> <span data-ttu-id="62779-156">Následující import odpovídá jakémukoli exportu s názvem kontraktu "TheString".</span><span class="sxs-lookup"><span data-stu-id="62779-156">The following import matches any export with contract name "TheString".</span></span>

```vb
Public Class MyClass1

    <Import("TheString")>
    Public Property MyAddin

End Class
```

```csharp
public class MyClass
{
    [Import("TheString")]
    public dynamic MyAddin { get; set; }
}
```

<span data-ttu-id="62779-157">Pokud je typ kontraktu odvozen z `dynamic` klíčového slova, bude odpovídat jakémukoli typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="62779-157">When the contract type is inferred from the `dynamic` keyword, it will match any contract type.</span></span> <span data-ttu-id="62779-158">V takovém případě by měl import **vždy** určovat název kontraktu, na kterém se bude shodovat.</span><span class="sxs-lookup"><span data-stu-id="62779-158">In this case, an import should **always** specify a contract name to match on.</span></span> <span data-ttu-id="62779-159">(Pokud není zadaný žádný název kontraktu, import se považuje za neodpovídající žádným exportům.) Oba následující exporty by odpovídaly předchozímu importu.</span><span class="sxs-lookup"><span data-stu-id="62779-159">(If no contract name is specified, the import will be considered to match no exports.) Both of the following exports would match the previous import.</span></span>

```vb
<Export("TheString", GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class

<Export("TheString")>
Public Class MyToolbar

End Class
```

```csharp
[Export("TheString", typeof(IMyAddin))]
public class MyLogger : IMyAddin { }

[Export("TheString")]
public class MyToolbar { }
```

<span data-ttu-id="62779-160">Import třídy musí být připravený k práci s objektem libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="62779-160">Obviously, the importing class must be prepared to deal with an object of arbitrary type.</span></span>

### <a name="lazy-imports"></a><span data-ttu-id="62779-161">Opožděné importy</span><span class="sxs-lookup"><span data-stu-id="62779-161">Lazy Imports</span></span>

<span data-ttu-id="62779-162">V některých případech importovaná třída může vyžadovat nepřímý odkaz na importovaný objekt, aby se objekt nevytvořil okamžitě.</span><span class="sxs-lookup"><span data-stu-id="62779-162">In some cases, the importing class may require an indirect reference to the imported object, so that the object is not instantiated immediately.</span></span> <span data-ttu-id="62779-163">V tomto scénáři třída může deklarovat *opožděné importy* pomocí typu kontraktu `Lazy<T>`.</span><span class="sxs-lookup"><span data-stu-id="62779-163">In this scenario, the class can declare a *lazy import* by using a contract type of `Lazy<T>`.</span></span> <span data-ttu-id="62779-164">Následující importovaná vlastnost deklaruje opožděný import.</span><span class="sxs-lookup"><span data-stu-id="62779-164">The following importing property declares a lazy import.</span></span>

```vb
Public Class MyClass1

    <Import()>
    Public Property MyAddin As Lazy(Of IMyAddin)

End Class
```

```csharp
public class MyClass
{
    [Import]
    public Lazy<IMyAddin> MyAddin { get; set; }
}
```

<span data-ttu-id="62779-165">Z hlediska modulu kompozice `Lazy<T>` je typ kontraktu považován za shodný s typem kontraktu. `T`</span><span class="sxs-lookup"><span data-stu-id="62779-165">From the point of view of the composition engine, a contract type of `Lazy<T>` is considered identical to contract type of `T`.</span></span> <span data-ttu-id="62779-166">Předchozí import proto odpovídá následujícímu exportu.</span><span class="sxs-lookup"><span data-stu-id="62779-166">Therefore, the previous import would match the following export.</span></span>

```vb
<Export(GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export(typeof(IMyAddin))]
public class MyLogger : IMyAddin { }
```

<span data-ttu-id="62779-167">Název kontraktu a typ kontraktu lze zadat v `Import` atributu pro opožděné importy, jak je popsáno výše v části "základní importy a export".</span><span class="sxs-lookup"><span data-stu-id="62779-167">The contract name and contract type can be specified in the `Import` attribute for a lazy import, as described earlier in the "Basic Imports and Exports" section.</span></span>

### <a name="prerequisite-imports"></a><span data-ttu-id="62779-168">Import požadovaných součástí</span><span class="sxs-lookup"><span data-stu-id="62779-168">Prerequisite Imports</span></span>

<span data-ttu-id="62779-169">Exportované části MEF jsou obvykle vytvářeny modulem složení, a to v reakci na přímý požadavek nebo na nutnost vyplnit odpovídající import.</span><span class="sxs-lookup"><span data-stu-id="62779-169">Exported MEF parts are typically created by the composition engine, in response to a direct request or the need to fill a matched import.</span></span> <span data-ttu-id="62779-170">Ve výchozím nastavení používá modul kompozice při vytváření součásti konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="62779-170">By default, when creating a part, the composition engine uses the parameter-less constructor.</span></span> <span data-ttu-id="62779-171">Chcete-li, aby modul používal jiný konstruktor, můžete jej označit `ImportingConstructor` atributem.</span><span class="sxs-lookup"><span data-stu-id="62779-171">To make the engine use a different constructor, you can mark it with the `ImportingConstructor` attribute.</span></span>

<span data-ttu-id="62779-172">Každá část může mít pouze jeden konstruktor pro použití modulem složení.</span><span class="sxs-lookup"><span data-stu-id="62779-172">Each part may have only one constructor for use by the composition engine.</span></span> <span data-ttu-id="62779-173">Pokud neposkytnete žádný konstruktor bez `ImportingConstructor` parametrů ani žádný atribut, nebo pokud `ImportingConstructor` zadáte více než jeden atribut, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="62779-173">Providing no parameterless constructor and no `ImportingConstructor` attribute, or providing more than one `ImportingConstructor` attribute, will produce an error.</span></span>

<span data-ttu-id="62779-174">Chcete-li vyplnit parametry konstruktoru označeného `ImportingConstructor` atributem, všechny tyto parametry jsou automaticky deklarovány jako import.</span><span class="sxs-lookup"><span data-stu-id="62779-174">To fill the parameters of a constructor marked with the `ImportingConstructor` attribute, all of those parameters are automatically declared as imports.</span></span> <span data-ttu-id="62779-175">Toto je pohodlný způsob, jak deklarovat importy, které se používají při inicializaci části.</span><span class="sxs-lookup"><span data-stu-id="62779-175">This is a convenient way to declare imports that are used during part initialization.</span></span> <span data-ttu-id="62779-176">Následující třída používá `ImportingConstructor` pro deklaraci importu.</span><span class="sxs-lookup"><span data-stu-id="62779-176">The following class uses `ImportingConstructor` to declare an import.</span></span>

```vb
Public Class MyClass1

    Private _theAddin As IMyAddin

    'Parameterless constructor will NOT be used
    'because the ImportingConstructor
    'attribute is present.
    Public Sub New()

    End Sub

    'This constructor will be used.
    'An import with contract type IMyAddin
    'is declared automatically.
    <ImportingConstructor()>
    Public Sub New(ByVal MyAddin As IMyAddin)
        _theAddin = MyAddin
    End Sub

End Class
```

```csharp
public class MyClass
{
    private IMyAddin _theAddin;

    //Parameterless constructor will NOT be
    //used because the ImportingConstructor
    //attribute is present.
    public MyClass() { }

    //This constructor will be used.
    //An import with contract type IMyAddin is
    //declared automatically.
    [ImportingConstructor]
    public MyClass(IMyAddin MyAddin)
    {
        _theAddin = MyAddin;
    }
}
```

<span data-ttu-id="62779-177">Ve výchozím nastavení používá `ImportingConstructor` atribut pro všechny importy parametrů odvozené typy kontraktů a názvy kontraktů.</span><span class="sxs-lookup"><span data-stu-id="62779-177">By default, the `ImportingConstructor` attribute uses inferred contract types and contract names for all of the parameter imports.</span></span> <span data-ttu-id="62779-178">To lze přepsat tím, že upravení parametry s `Import` atributy, které mohou následně definovat typ kontraktu a název kontraktu explicitně.</span><span class="sxs-lookup"><span data-stu-id="62779-178">It is possible to override this by decorating the parameters with `Import` attributes, which can then define the contract type and contract name explicitly.</span></span> <span data-ttu-id="62779-179">Následující kód demonstruje konstruktor, který používá tuto syntaxi k importu odvozené třídy namísto nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="62779-179">The following code demonstrates a constructor that uses this syntax to import a derived class instead of a parent class.</span></span>

```vb
<ImportingConstructor()>
Public Sub New(<Import(GetType(IMySubAddin))> ByVal MyAddin As IMyAddin)

End Sub
```

```csharp
[ImportingConstructor]
public MyClass([Import(typeof(IMySubAddin))]IMyAddin MyAddin)
{
    _theAddin = MyAddin;
}
```

<span data-ttu-id="62779-180">Konkrétně byste měli být opatrní s parametry kolekce.</span><span class="sxs-lookup"><span data-stu-id="62779-180">In particular, you should be careful with collection parameters.</span></span> <span data-ttu-id="62779-181">`ImportingConstructor` Například pokud zadáte v konstruktoru s `IEnumerable<int>`parametrem typu, import bude odpovídat jedinému exportu typu `IEnumerable<int>`namísto sady EXPORTS typu. `int`</span><span class="sxs-lookup"><span data-stu-id="62779-181">For example, if you specify `ImportingConstructor` on a constructor with a parameter of type `IEnumerable<int>`, the import will match a single export of type `IEnumerable<int>`, instead of a set of exports of type `int`.</span></span> <span data-ttu-id="62779-182">Chcete-li porovnat sadu exportů typu `int`, je nutné zadat parametr s `ImportMany` atributem.</span><span class="sxs-lookup"><span data-stu-id="62779-182">To match a set of exports of type `int`, you have to decorate the parameter with the `ImportMany` attribute.</span></span>

<span data-ttu-id="62779-183">Parametry deklarované jako import pomocí `ImportingConstructor` atributu jsou také označeny jako *požadované importy*.</span><span class="sxs-lookup"><span data-stu-id="62779-183">Parameters declared as imports by the `ImportingConstructor` attribute are also marked as *prerequisite imports*.</span></span> <span data-ttu-id="62779-184">MEF normálně umožňuje exportům a importům vytvořit *cyklus*.</span><span class="sxs-lookup"><span data-stu-id="62779-184">MEF normally allows exports and imports to form a *cycle*.</span></span> <span data-ttu-id="62779-185">Například cyklus je místo, kde objekt A importuje objekt B, který zase importuje objekt A. Za běžných okolností není cyklem problém a kontejner kompozice vytvoří oba objekty normálně.</span><span class="sxs-lookup"><span data-stu-id="62779-185">For example, a cycle is where object A imports object B, which in turn imports object A. Under ordinary circumstances, a cycle is not a problem, and the composition container constructs both objects normally.</span></span>

<span data-ttu-id="62779-186">Pokud je importovaná hodnota požadována konstruktorem součásti, tento objekt se nemůže zúčastnit cyklu.</span><span class="sxs-lookup"><span data-stu-id="62779-186">When an imported value is required by the constructor of a part, that object cannot participate in a cycle.</span></span> <span data-ttu-id="62779-187">Pokud objekt A vyžaduje, aby byl objekt B vytvořen před samotným sestavením a objekt B importuje objekt A, pak se cyklus nebude moci vyřešit a dojde k chybě kompozice.</span><span class="sxs-lookup"><span data-stu-id="62779-187">If object A requires that object B be constructed before it can be constructed itself, and object B imports object A, then the cycle will be unable to resolve and a composition error will occur.</span></span> <span data-ttu-id="62779-188">Importy deklarované v parametrech konstruktoru jsou tedy požadavky na importy, které musí být vyplněny před jakýmkoli exportem z objektu, který je vyžaduje, aby je bylo možné použít.</span><span class="sxs-lookup"><span data-stu-id="62779-188">Imports declared on constructor parameters are therefore prerequisite imports, which must all be filled before any of the exports from the object that requires them can be used.</span></span>

### <a name="optional-imports"></a><span data-ttu-id="62779-189">Volitelné importy</span><span class="sxs-lookup"><span data-stu-id="62779-189">Optional Imports</span></span>

<span data-ttu-id="62779-190">`Import` Atribut určuje požadavek, který má součást fungovat.</span><span class="sxs-lookup"><span data-stu-id="62779-190">The `Import` attribute specifies a requirement for the part to function.</span></span> <span data-ttu-id="62779-191">Pokud import nelze splnit, složení této součásti selže a součást nebude k dispozici.</span><span class="sxs-lookup"><span data-stu-id="62779-191">If an import cannot be fulfilled, the composition of that part will fail and the part will not be available.</span></span>

<span data-ttu-id="62779-192">Pomocí `AllowDefault` vlastnosti můžete určit, že import je *nepovinný* .</span><span class="sxs-lookup"><span data-stu-id="62779-192">You can specify that an import is *optional* by using the `AllowDefault` property.</span></span> <span data-ttu-id="62779-193">V tomto případě bude kompozice úspěšná i v případě, že import neodpovídá žádnému dostupnému exportu a vlastnost import bude nastavena na výchozí hodnotu pro svůj typ vlastnosti (`null` pro vlastnosti objektu, `false` pro logické hodnoty nebo nula pro číselné vlastnosti.) Následující třída používá volitelný import.</span><span class="sxs-lookup"><span data-stu-id="62779-193">In this case, the composition will succeed even if the import does not match any available exports, and the importing property will be set to the default for its property type (`null` for object properties, `false` for Booleans, or zero for numeric properties.) The following class uses an optional import.</span></span>

```vb
Public Class MyClass1

    <Import(AllowDefault:=True)>
    Public Property thePlugin As Plugin

    'If no matching export is available,
    'thePlugin will be set to null.
End Class
```

```csharp
public class MyClass
{
    [Import(AllowDefault = true)]
    public Plugin thePlugin { get; set; }

    //If no matching export is available,
    //thePlugin will be set to null.
}
```

### <a name="importing-multiple-objects"></a><span data-ttu-id="62779-194">Importování více objektů</span><span class="sxs-lookup"><span data-stu-id="62779-194">Importing Multiple Objects</span></span>

<span data-ttu-id="62779-195">`Import` Atribut bude úspěšně sestaven pouze v případě, že odpovídá jednomu a pouze jednomu exportu.</span><span class="sxs-lookup"><span data-stu-id="62779-195">The `Import` attribute will only be successfully composed when it matches one and only one export.</span></span> <span data-ttu-id="62779-196">Jiné případy vytvoří chybu složení.</span><span class="sxs-lookup"><span data-stu-id="62779-196">Other cases will produce a composition error.</span></span> <span data-ttu-id="62779-197">Chcete-li importovat více než jeden export, který odpovídá stejné smlouvě, `ImportMany` použijte atribut.</span><span class="sxs-lookup"><span data-stu-id="62779-197">To import more than one export that matches the same contract, use the `ImportMany` attribute.</span></span> <span data-ttu-id="62779-198">Importy označené pomocí tohoto atributu jsou vždycky volitelné.</span><span class="sxs-lookup"><span data-stu-id="62779-198">Imports marked with this attribute are always optional.</span></span> <span data-ttu-id="62779-199">Například složení nebude úspěšné, pokud nejsou k dispozici žádné vyhovující exporty.</span><span class="sxs-lookup"><span data-stu-id="62779-199">For example, composition will not fail if no matching exports are present.</span></span> <span data-ttu-id="62779-200">Následující třída importuje libovolný počet exportů typu `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="62779-200">The following class imports any number of exports of type `IMyAddin`.</span></span>

```vb
Public Class MyClass1

    <ImportMany()>
    Public Property MyAddin As IEnumerable(Of IMyAddin)

End Class
```

```csharp
public class MyClass
{
    [ImportMany]
    public IEnumerable<IMyAddin> MyAddin { get; set; }
}
```

<span data-ttu-id="62779-201">K importovanému poli je možné přistupovat `IEnumerable<T>` pomocí běžných syntaxí a metod.</span><span class="sxs-lookup"><span data-stu-id="62779-201">The imported array can be accessed by using ordinary `IEnumerable<T>` syntax and methods.</span></span> <span data-ttu-id="62779-202">Místo toho je také možné použít běžné pole (`IMyAddin[]`).</span><span class="sxs-lookup"><span data-stu-id="62779-202">It is also possible to use an ordinary array (`IMyAddin[]`) instead.</span></span>

<span data-ttu-id="62779-203">Tento model může být velmi důležitý při použití v kombinaci s `Lazy<T>` syntaxí.</span><span class="sxs-lookup"><span data-stu-id="62779-203">This pattern can be very important when you use it in combination with the `Lazy<T>` syntax.</span></span> <span data-ttu-id="62779-204">Například pomocí `ImportMany`, `IEnumerable<T>`a `Lazy<T>`můžete importovat nepřímé odkazy na libovolný počet objektů a vytvořit pouze instance těch, které jsou nezbytné.</span><span class="sxs-lookup"><span data-stu-id="62779-204">For example, by using `ImportMany`, `IEnumerable<T>`, and `Lazy<T>`, you can import indirect references to any number of objects and only instantiate the ones that become necessary.</span></span> <span data-ttu-id="62779-205">Následující třída zobrazuje tento model.</span><span class="sxs-lookup"><span data-stu-id="62779-205">The following class shows this pattern.</span></span>

```vb
Public Class MyClass1

    <ImportMany()>
    Public Property MyAddin As IEnumerable(Of Lazy(Of IMyAddin))

End Class
```

```csharp
public class MyClass
{
    [ImportMany]
    public IEnumerable<Lazy<IMyAddin>> MyAddin { get; set; }
}
```

<a name="avoiding_discovery"></a>

## <a name="avoiding-discovery"></a><span data-ttu-id="62779-206">Zamezení zjišťování</span><span class="sxs-lookup"><span data-stu-id="62779-206">Avoiding Discovery</span></span>

<span data-ttu-id="62779-207">V některých případech můžete chtít zabránit tomu, aby se součást zjistila jako součást katalogu.</span><span class="sxs-lookup"><span data-stu-id="62779-207">In some cases, you may want to prevent a part from being discovered as part of a catalog.</span></span> <span data-ttu-id="62779-208">Například část může být základní třídou, která má být zděděna z, ale není použita.</span><span class="sxs-lookup"><span data-stu-id="62779-208">For example, the part may be a base class intended to be inherited from, but not used.</span></span> <span data-ttu-id="62779-209">To můžete provést dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="62779-209">There are two ways to accomplish this.</span></span> <span data-ttu-id="62779-210">Nejprve můžete použít `abstract` klíčové slovo pro třídu součásti.</span><span class="sxs-lookup"><span data-stu-id="62779-210">First, you can use the `abstract` keyword on the part class.</span></span> <span data-ttu-id="62779-211">Abstraktní třídy nikdy neposkytují export, i když mohou poskytnout děděné exporty třídám, které jsou z nich odvozeny.</span><span class="sxs-lookup"><span data-stu-id="62779-211">Abstract classes never provide exports, although they can provide inherited exports to classes that derive from them.</span></span>

<span data-ttu-id="62779-212">Pokud třídu nelze nastavit jako abstraktní, lze ji roztřídit pomocí `PartNotDiscoverable` atributu.</span><span class="sxs-lookup"><span data-stu-id="62779-212">If the class cannot be made abstract, you can decorate it with the `PartNotDiscoverable` attribute.</span></span> <span data-ttu-id="62779-213">Část upravená pomocí tohoto atributu nebude zahrnuta do žádných katalogů.</span><span class="sxs-lookup"><span data-stu-id="62779-213">A part decorated with this attribute will not be included in any catalogs.</span></span> <span data-ttu-id="62779-214">Následující příklad znázorňuje tyto vzory.</span><span class="sxs-lookup"><span data-stu-id="62779-214">The following example demonstrates these patterns.</span></span> <span data-ttu-id="62779-215">`DataOne`budou zjištěny katalogem.</span><span class="sxs-lookup"><span data-stu-id="62779-215">`DataOne` will be discovered by the catalog.</span></span> <span data-ttu-id="62779-216">Vzhledem `DataTwo` k tomu, že je abstraktní, nebude zjištěno.</span><span class="sxs-lookup"><span data-stu-id="62779-216">Since `DataTwo` is abstract, it will not be discovered.</span></span> <span data-ttu-id="62779-217">Vzhledem `DataThree` k `PartNotDiscoverable` tomu, že se atribut použil, nebude zjištěn.</span><span class="sxs-lookup"><span data-stu-id="62779-217">Since `DataThree` used the `PartNotDiscoverable` attribute, it will not be discovered.</span></span>

```vb
<Export()>
Public Class DataOne
    'This part will be discovered
    'as normal by the catalog.
End Class

<Export()>
Public MustInherit Class DataTwo
    'This part will not be discovered
    'by the catalog.
End Class

<PartNotDiscoverable()>
<Export()>
Public Class DataThree
    'This part will also not be discovered
    'by the catalog.
End Class
```

```csharp
[Export]
public class DataOne
{
    //This part will be discovered
    //as normal by the catalog.
}

[Export]
public abstract class DataTwo
{
    //This part will not be discovered
    //by the catalog.
}

[PartNotDiscoverable]
[Export]
public class DataThree
{
    //This part will also not be discovered
    //by the catalog.
}
```

<a name="metadata_and_metadata_views"></a>

## <a name="metadata-and-metadata-views"></a><span data-ttu-id="62779-218">Metadata a zobrazení metadat</span><span class="sxs-lookup"><span data-stu-id="62779-218">Metadata and Metadata Views</span></span>

<span data-ttu-id="62779-219">Exporty můžou poskytnout další informace o samotných údajích, které se nazývají *metadata*.</span><span class="sxs-lookup"><span data-stu-id="62779-219">Exports can provide additional information about themselves known as *metadata*.</span></span> <span data-ttu-id="62779-220">Metadata lze použít k předávání vlastností exportovaného objektu do importované části.</span><span class="sxs-lookup"><span data-stu-id="62779-220">Metadata can be used to convey properties of the exported object to the importing part.</span></span> <span data-ttu-id="62779-221">Importovaná část může pomocí těchto dat rozhodnout, které exporty se mají použít, nebo shromažďovat informace o exportu bez nutnosti jeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="62779-221">The importing part can use this data to decide which exports to use, or to gather information about an export without having to construct it.</span></span> <span data-ttu-id="62779-222">Z tohoto důvodu musí být import opožděný, aby používal metadata.</span><span class="sxs-lookup"><span data-stu-id="62779-222">For this reason, an import must be lazy to use metadata.</span></span>

<span data-ttu-id="62779-223">Chcete-li použít metadata, obvykle deklarujete rozhraní známé jako *zobrazení metadat*, které deklaruje, jaká metadata budou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="62779-223">To use metadata, you typically declare an interface known as a *metadata view*, which declares what metadata will be available.</span></span> <span data-ttu-id="62779-224">Rozhraní zobrazení metadat musí mít pouze vlastnosti, přičemž tyto vlastnosti musí mít `get` přistupující objekty.</span><span class="sxs-lookup"><span data-stu-id="62779-224">The metadata view interface must have only properties, and those properties must have `get` accessors.</span></span> <span data-ttu-id="62779-225">Následující rozhraní je příkladem zobrazení metadat.</span><span class="sxs-lookup"><span data-stu-id="62779-225">The following interface is an example metadata view.</span></span>

```vb
Public Interface IPluginMetadata

    ReadOnly Property Name As String

    <DefaultValue(1)>
    ReadOnly Property Version As Integer

End Interface
```

```csharp
public interface IPluginMetadata
{
    string Name { get; }

    [DefaultValue(1)]
    int Version { get; }
}
```

<span data-ttu-id="62779-226">Je také možné použít obecnou kolekci, `IDictionary<string, object>`jako zobrazení metadat, ale to propadá na výhody kontroly typu a je třeba se jim vyhnout.</span><span class="sxs-lookup"><span data-stu-id="62779-226">It is also possible to use a generic collection, `IDictionary<string, object>`, as a metadata view, but this forfeits the benefits of type checking and should be avoided.</span></span>

<span data-ttu-id="62779-227">Obvykle jsou požadovány všechny vlastnosti pojmenované v zobrazení metadat a jakékoli exporty, které je neposkytují, nebudou považovány za shodu.</span><span class="sxs-lookup"><span data-stu-id="62779-227">Ordinarily, all of the properties named in the metadata view are required, and any exports that do not provide them will not be considered a match.</span></span> <span data-ttu-id="62779-228">`DefaultValue` Atribut určuje, že vlastnost je volitelná.</span><span class="sxs-lookup"><span data-stu-id="62779-228">The `DefaultValue` attribute specifies that a property is optional.</span></span> <span data-ttu-id="62779-229">Pokud vlastnost není zahrnutá, přiřadí se výchozí hodnota zadaná jako parametr `DefaultValue`.</span><span class="sxs-lookup"><span data-stu-id="62779-229">If the property is not included, it will be assigned the default value specified as a parameter of `DefaultValue`.</span></span> <span data-ttu-id="62779-230">Níže jsou dvě různé třídy dekorované metadaty.</span><span class="sxs-lookup"><span data-stu-id="62779-230">The following are two different classes decorated with metadata.</span></span> <span data-ttu-id="62779-231">Obě tyto třídy by odpovídaly předchozímu zobrazení metadat.</span><span class="sxs-lookup"><span data-stu-id="62779-231">Both of these classes would match the previous metadata view.</span></span>

```vb
<Export(GetType(IPlugin))>
<ExportMetadata("Name", "Logger")>
<ExportMetadata("Version", 4)>
Public Class MyLogger
    Implements IPlugin

End Class

'Version is not required because of the DefaultValue
<Export(GetType(IPlugin))>
<ExportMetadata("Name", "Disk Writer")>
Public Class DWriter
    Implements IPlugin

End Class
```

```csharp
[Export(typeof(IPlugin)),
    ExportMetadata("Name", "Logger"),
    ExportMetadata("Version", 4)]
public class Logger : IPlugin
{
}

[Export(typeof(IPlugin)),
    ExportMetadata("Name", "Disk Writer")]
    //Version is not required because of the DefaultValue
public class DWriter : IPlugin
{
}
```

<span data-ttu-id="62779-232">Metadata jsou vyjádřena po `Export` atributu pomocí `ExportMetadata` atributu.</span><span class="sxs-lookup"><span data-stu-id="62779-232">Metadata is expressed after the `Export` attribute by using the `ExportMetadata` attribute.</span></span> <span data-ttu-id="62779-233">Každá část metadat se skládá z dvojice název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="62779-233">Each piece of metadata is composed of a name/value pair.</span></span> <span data-ttu-id="62779-234">Název v metadatech se musí shodovat s názvem příslušné vlastnosti v zobrazení metadat a hodnota bude přiřazena této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="62779-234">The name portion of the metadata must match the name of the appropriate property in the metadata view, and the value will be assigned to that property.</span></span>

<span data-ttu-id="62779-235">Je to dovozce, který určuje, jaké zobrazení metadat se bude používat.</span><span class="sxs-lookup"><span data-stu-id="62779-235">It is the importer that specifies what metadata view, if any, will be in use.</span></span> <span data-ttu-id="62779-236">Import s metadaty je deklarován jako opožděné importu s rozhraním metadat jako druhým parametrem typu `Lazy<T,T>`.</span><span class="sxs-lookup"><span data-stu-id="62779-236">An import with metadata is declared as a lazy import, with the metadata interface as the second type parameter to `Lazy<T,T>`.</span></span> <span data-ttu-id="62779-237">Následující třída importuje předchozí část s metadaty.</span><span class="sxs-lookup"><span data-stu-id="62779-237">The following class imports the previous part with metadata.</span></span>

```vb
Public Class Addin

    <Import()>
    Public Property plugin As Lazy(Of IPlugin, IPluginMetadata)
End Class
```

```csharp
public class Addin
{
    [Import]
    public Lazy<IPlugin, IPluginMetadata> plugin;
}
```

<span data-ttu-id="62779-238">V mnoha případech budete chtít kombinovat metadata s `ImportMany` atributem, aby bylo možné analyzovat v dostupných importech a vybírat a vytvářet instance pouze jeden, nebo filtrovat kolekci tak, aby odpovídala určité podmínce.</span><span class="sxs-lookup"><span data-stu-id="62779-238">In many cases, you will want to combine metadata with the `ImportMany` attribute, in order to parse through the available imports and choose and instantiate only one, or filter a collection to match a certain condition.</span></span> <span data-ttu-id="62779-239">Následující třída vytváří instance pouze `IPlugin` objekty, které mají `Name` hodnotu "protokolovací".</span><span class="sxs-lookup"><span data-stu-id="62779-239">The following class instantiates only `IPlugin` objects that have the `Name` value "Logger".</span></span>

```vb
Public Class User

    <ImportMany()>
    Public Property plugins As IEnumerable(Of Lazy(Of IPlugin, IPluginMetadata))

    Public Function InstantiateLogger() As IPlugin

        Dim logger As IPlugin
        logger = Nothing

        For Each Plugin As Lazy(Of IPlugin, IPluginMetadata) In plugins
            If Plugin.Metadata.Name = "Logger" Then
                logger = Plugin.Value
            End If
        Next
        Return logger
    End Function

End Class
```

```csharp
public class User
{
    [ImportMany]
    public IEnumerable<Lazy<IPlugin, IPluginMetadata>> plugins;

    public IPlugin InstantiateLogger()
    {
        IPlugin logger = null;

        foreach (Lazy<IPlugin, IPluginMetadata> plugin in plugins)
        {
            if (plugin.Metadata.Name == "Logger")
                logger = plugin.Value;
        }
        return logger;
    }
}
```

<a name="import_and_export_inheritance"></a>

## <a name="import-and-export-inheritance"></a><span data-ttu-id="62779-240">Dědičnost importu a exportu</span><span class="sxs-lookup"><span data-stu-id="62779-240">Import and Export Inheritance</span></span>

<span data-ttu-id="62779-241">Pokud třída dědí z části, může se také stát, že se tato třída stane součástí.</span><span class="sxs-lookup"><span data-stu-id="62779-241">If a class inherits from a part, that class may also become a part.</span></span> <span data-ttu-id="62779-242">Importy jsou vždy děděny podtřídami.</span><span class="sxs-lookup"><span data-stu-id="62779-242">Imports are always inherited by subclasses.</span></span> <span data-ttu-id="62779-243">Proto bude podtřídou součásti vždy součástí, se stejnými importy jako její nadřazená třída.</span><span class="sxs-lookup"><span data-stu-id="62779-243">Therefore, a subclass of a part will always be a part, with the same imports as its parent class.</span></span>

<span data-ttu-id="62779-244">Exporty deklarované pomocí `Export` atributu nejsou děděny podtřídami.</span><span class="sxs-lookup"><span data-stu-id="62779-244">Exports declared by using the `Export` attribute are not inherited by subclasses.</span></span> <span data-ttu-id="62779-245">Součást však může exportovat sebe sama pomocí `InheritedExport` atributu.</span><span class="sxs-lookup"><span data-stu-id="62779-245">However, a part can export itself by using the `InheritedExport` attribute.</span></span> <span data-ttu-id="62779-246">Podtřídy této části zdědí a poskytnou stejný export, včetně názvu kontraktu a typu smlouvy.</span><span class="sxs-lookup"><span data-stu-id="62779-246">Subclasses of the part will inherit and provide the same export, including contract name and contract type.</span></span> <span data-ttu-id="62779-247">Na rozdíl od `Export` atributu `InheritedExport` lze použít pouze na úrovni třídy, nikoli na úrovni člena.</span><span class="sxs-lookup"><span data-stu-id="62779-247">Unlike an `Export` attribute, `InheritedExport` can be applied only at the class level, and not at the member level.</span></span> <span data-ttu-id="62779-248">Proto nelze export na úrovni členů dědění nikdy dědit.</span><span class="sxs-lookup"><span data-stu-id="62779-248">Therefore, member-level exports can never be inherited.</span></span>

<span data-ttu-id="62779-249">Následující čtyři třídy demonstrují principy dědičnosti importu a exportu.</span><span class="sxs-lookup"><span data-stu-id="62779-249">The following four classes demonstrate the principles of import and export inheritance.</span></span> <span data-ttu-id="62779-250">`NumTwo`dědí z `NumOne`, takže `NumTwo` se naimportuje `IMyData`.</span><span class="sxs-lookup"><span data-stu-id="62779-250">`NumTwo` inherits from `NumOne`, so `NumTwo` will import `IMyData`.</span></span> <span data-ttu-id="62779-251">Běžné exporty nejsou děděny, `NumTwo` takže nebudou exportovány žádné výsledky.</span><span class="sxs-lookup"><span data-stu-id="62779-251">Ordinary exports are not inherited, so `NumTwo` will not export anything.</span></span> <span data-ttu-id="62779-252">`NumFour`dědí z `NumThree`.</span><span class="sxs-lookup"><span data-stu-id="62779-252">`NumFour` inherits from `NumThree`.</span></span> <span data-ttu-id="62779-253">Vzhledem `NumThree` k `InheritedExport`tomu `NumFour` , že používá, má jeden `NumThree`export s typem kontraktu.</span><span class="sxs-lookup"><span data-stu-id="62779-253">Because `NumThree` used `InheritedExport`, `NumFour` has one export with contract type `NumThree`.</span></span> <span data-ttu-id="62779-254">Exporty na úrovni členů nejsou nikdy zděděné `IMyData` , takže se neexportují.</span><span class="sxs-lookup"><span data-stu-id="62779-254">Member-level exports are never inherited, so `IMyData` is not exported.</span></span>

```vb
<Export()>
Public Class NumOne
    <Import()>
    Public Property MyData As IMyData
End Class

Public Class NumTwo
    Inherits NumOne

    'Imports are always inherited, so NumTwo will
    'Import IMyData

    'Ordinary exports are not inherited, so
    'NumTwo will NOT export anything.  As a result it
    'will not be discovered by the catalog!

End Class

<InheritedExport()>
Public Class NumThree

    <Export()>
    Public Property MyData As IMyData

    'This part provides two exports, one of
    'contract type NumThree, and one of
    'contract type IMyData.

End Class

Public Class NumFour
    Inherits NumThree

    'Because NumThree used InheritedExport,
    'this part has one export with contract
    'type NumThree.

    'Member-level exports are never inherited,
    'so IMyData is not exported.

End Class
```

```csharp
[Export]
public class NumOne
{
    [Import]
    public IMyData MyData { get; set; }
}

public class NumTwo : NumOne
{
    //Imports are always inherited, so NumTwo will
    //import IMyData.

    //Ordinary exports are not inherited, so
    //NumTwo will NOT export anything. As a result it
    //will not be discovered by the catalog!
}

[InheritedExport]
public class NumThree
{
    [Export]
    Public IMyData MyData { get; set; }

    //This part provides two exports, one of
    //contract type NumThree, and one of
    //contract type IMyData.
}

public class NumFour : NumThree
{
    //Because NumThree used InheritedExport,
    //this part has one export with contract
    //type NumThree.

    //Member-level exports are never inherited,
    //so IMyData is not exported.
}
```

<span data-ttu-id="62779-255">Pokud jsou k `InheritedExport` atributu přidružená metadata, budou tato metadata také děděna.</span><span class="sxs-lookup"><span data-stu-id="62779-255">If there is metadata associated with an `InheritedExport` attribute, that metadata will also be inherited.</span></span> <span data-ttu-id="62779-256">(Další informace najdete v části předchozí metadata a zobrazení metadat). Zděděná metadata nelze upravovat podtřídou.</span><span class="sxs-lookup"><span data-stu-id="62779-256">(For more information, see the earlier "Metadata and Metadata Views" section.) Inherited metadata cannot be modified by the subclass.</span></span> <span data-ttu-id="62779-257">Pokud však znovu deklarujete `InheritedExport` atribut se stejným názvem kontraktu a typem kontraktu, ale s novými metadaty, podtřída může nahradit zděděná metadata novými metadaty.</span><span class="sxs-lookup"><span data-stu-id="62779-257">However, by re-declaring the `InheritedExport` attribute with the same contract name and contract type, but with new metadata, the subclass can replace the inherited metadata with new metadata.</span></span> <span data-ttu-id="62779-258">Následující třída demonstruje tento princip.</span><span class="sxs-lookup"><span data-stu-id="62779-258">The following class demonstrates this principle.</span></span> <span data-ttu-id="62779-259">`MegaLogger` Část dědí z `Logger` a obsahuje `InheritedExport` atribut.</span><span class="sxs-lookup"><span data-stu-id="62779-259">The `MegaLogger` part inherits from `Logger` and includes the `InheritedExport` attribute.</span></span> <span data-ttu-id="62779-260">Vzhledem `MegaLogger` k tomu, že znovu deklaruje nová metadata s názvem status, nedědí název a metadata verze z `Logger`.</span><span class="sxs-lookup"><span data-stu-id="62779-260">Since `MegaLogger` re-declares new metadata named Status, it does not inherit the Name and Version metadata from `Logger`.</span></span>

```vb
<InheritedExport(GetType(IPlugin))>
<ExportMetadata("Name", "Logger")>
<ExportMetadata("Version", 4)>
Public Class Logger
    Implements IPlugin

    'Exports with contract type IPlugin
    'and metadata "Name" and "Version".
End Class

Public Class SuperLogger
    Inherits Logger

    'Exports with contract type IPlugin and
    'metadata "Name" and "Version", exactly the same
    'as the Logger class.

End Class

<InheritedExport(GetType(IPlugin))>
<ExportMetadata("Status", "Green")>
Public Class MegaLogger
    Inherits Logger

    'Exports with contract type IPlugin and
    'metadata "Status" only. Re-declaring
    'the attribute replaces all metadata.

End Class
```

```csharp
[InheritedExport(typeof(IPlugin)),
    ExportMetadata("Name", "Logger"),
    ExportMetadata("Version", 4)]
public class Logger : IPlugin
{
    //Exports with contract type IPlugin and
    //metadata "Name" and "Version".
}

public class SuperLogger : Logger
{
    //Exports with contract type IPlugin and
    //metadata "Name" and "Version", exactly the same
    //as the Logger class.
}

[InheritedExport(typeof(IPlugin)),
    ExportMetadata("Status", "Green")]
public class MegaLogger : Logger        {
    //Exports with contract type IPlugin and
    //metadata "Status" only. Re-declaring
    //the attribute replaces all metadata.
}
```

<span data-ttu-id="62779-261">Při opětovné deklaraci `InheritedExport` atributu pro přepsání metadat se ujistěte, že typy kontraktu jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="62779-261">When re-declaring the `InheritedExport` attribute to override metadata, make sure that the contract types are the same.</span></span> <span data-ttu-id="62779-262">(V předchozím příkladu `IPlugin` je to typ kontraktu.) Pokud se liší, místo přepsání, druhý atribut vytvoří druhý nezávislý export z části.</span><span class="sxs-lookup"><span data-stu-id="62779-262">(In the previous example, `IPlugin` is the contract type.) If they differ, instead of overriding, the second attribute will create a second, independent export from the part.</span></span> <span data-ttu-id="62779-263">Obecně to znamená, že budete muset explicitně zadat typ kontraktu při přepsání `InheritedExport` atributu, jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="62779-263">Generally, this means that you will have to explicitly specify the contract type when you override an `InheritedExport` attribute, as shown in the previous example.</span></span>

<span data-ttu-id="62779-264">Vzhledem k tomu, že rozhraní nemohou být vytvořena přímo, nesmí být obecně `Export` upravena pomocí atributů nebo `Import` .</span><span class="sxs-lookup"><span data-stu-id="62779-264">Since interfaces cannot be instantiated directly, they generally cannot be decorated with `Export` or `Import` attributes.</span></span> <span data-ttu-id="62779-265">Rozhraní lze však dekorovat pomocí `InheritedExport` atributu na úrovni rozhraní a export spolu s jakýmikoli přidruženými metadaty bude děděn všemi implementací tříd.</span><span class="sxs-lookup"><span data-stu-id="62779-265">However, an interface can be decorated with an `InheritedExport` attribute at the interface level, and that export along with any associated metadata will be inherited by any implementing classes.</span></span> <span data-ttu-id="62779-266">Samotné rozhraní nebude ale k dispozici jako součást.</span><span class="sxs-lookup"><span data-stu-id="62779-266">The interface itself will not be available as a part, however.</span></span>

<a name="custom_export_attributes"></a>

## <a name="custom-export-attributes"></a><span data-ttu-id="62779-267">Vlastní atributy exportu</span><span class="sxs-lookup"><span data-stu-id="62779-267">Custom Export Attributes</span></span>

<span data-ttu-id="62779-268">Základní atributy exportu `Export` a `InheritedExport`lze rozšířit tak, aby zahrnovaly metadata jako vlastnosti atributu.</span><span class="sxs-lookup"><span data-stu-id="62779-268">The basic export attributes, `Export` and `InheritedExport`, can be extended to include metadata as attribute properties.</span></span> <span data-ttu-id="62779-269">Tato technika je užitečná pro použití podobných metadat na mnoho částí nebo pro vytvoření stromu dědičnosti atributů metadat.</span><span class="sxs-lookup"><span data-stu-id="62779-269">This technique is useful for applying similar metadata to many parts, or creating an inheritance tree of metadata attributes.</span></span>

<span data-ttu-id="62779-270">Vlastní atribut může určovat typ kontraktu, název kontraktu nebo jiná metadata.</span><span class="sxs-lookup"><span data-stu-id="62779-270">A custom attribute can specify the contract type, the contract name, or any other metadata.</span></span> <span data-ttu-id="62779-271">Aby bylo možné definovat vlastní atribut, musí být třída, která dědí `ExportAttribute` z ( `InheritedExportAttribute`nebo), upravena `MetadataAttribute` atributem.</span><span class="sxs-lookup"><span data-stu-id="62779-271">In order to define a custom attribute, a class inheriting from `ExportAttribute` (or `InheritedExportAttribute`) must be decorated with the `MetadataAttribute` attribute.</span></span> <span data-ttu-id="62779-272">Následující třída definuje vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="62779-272">The following class defines a custom attribute.</span></span>

```vb
<MetadataAttribute()>
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=false)>
Public Class MyAttribute
    Inherits ExportAttribute

    Public Property MyMetadata As String

    Public Sub New(ByVal myMetadata As String)
        MyBase.New(GetType(IMyAddin))

        myMetadata = myMetadata
    End Sub

End Class
```

```csharp
[MetadataAttribute]
[AttributeUsage(AttributeTargets.Class, AllowMultiple=false)]
public class MyAttribute : ExportAttribute
{
    public MyAttribute(string myMetadata)
        : base(typeof(IMyAddin))
    {
        MyMetadata = myMetadata;
    }

    public string MyMetadata { get; private set; }
}
```

<span data-ttu-id="62779-273">Tato třída definuje vlastní atribut s názvem `MyAttribute` typu `IMyAddin` kontrakt a některá metadata s názvem `MyMetadata`.</span><span class="sxs-lookup"><span data-stu-id="62779-273">This class defines a custom attribute named `MyAttribute` with contract type `IMyAddin` and some metadata named `MyMetadata`.</span></span> <span data-ttu-id="62779-274">Všechny vlastnosti ve třídě označené `MetadataAttribute` atributem se považují za metadata definovaná ve vlastním atributu.</span><span class="sxs-lookup"><span data-stu-id="62779-274">All properties in a class marked with the `MetadataAttribute` attribute are considered to be metadata defined in the custom attribute.</span></span> <span data-ttu-id="62779-275">Následující dvě deklarace jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="62779-275">The following two declarations are equivalent.</span></span>

```vb
<Export(GetType(IMyAddin))>
<ExportMetadata("MyMetadata", "theData")>
Public Property myAddin As MyAddin
```

```vb
<MyAttribute("theData")>
Public Property myAddin As MyAddin
```

```csharp
[Export(typeof(IMyAddin)),
    ExportMetadata("MyMetadata", "theData")]
public MyAddin myAddin { get; set; }
```

```csharp
[MyAttribute("theData")]
public MyAddin myAddin { get; set; }
```

<span data-ttu-id="62779-276">V první deklaraci je typ kontraktu a metadata explicitně definovány.</span><span class="sxs-lookup"><span data-stu-id="62779-276">In the first declaration, the contract type and metadata are explicitly defined.</span></span> <span data-ttu-id="62779-277">Ve druhé deklaraci je typ kontraktu a metadata implicitní v přizpůsobeném atributu.</span><span class="sxs-lookup"><span data-stu-id="62779-277">In the second declaration, the contract type and metadata are implicit in the customized attribute.</span></span> <span data-ttu-id="62779-278">Zejména v případech, kdy je třeba použít velké množství identických metadat na mnoho částí (například informace o autorech nebo autorských právech), může použití vlastního atributu ušetřit spoustu času a duplikace.</span><span class="sxs-lookup"><span data-stu-id="62779-278">Particularly in cases where a large amount of identical metadata must be applied to many parts (for example, author or copyright information), using a custom attribute can save a lot of time and duplication.</span></span> <span data-ttu-id="62779-279">Kromě toho lze vytvořit stromy dědičnosti vlastních atributů, aby bylo možné variace.</span><span class="sxs-lookup"><span data-stu-id="62779-279">Further, inheritance trees of custom attributes can be created to allow for variations.</span></span>

<span data-ttu-id="62779-280">Chcete-li vytvořit volitelná metadata ve vlastním atributu, můžete použít `DefaultValue` atribut.</span><span class="sxs-lookup"><span data-stu-id="62779-280">To create optional metadata in a custom attribute, you can use the `DefaultValue` attribute.</span></span> <span data-ttu-id="62779-281">Pokud je tento atribut použit pro vlastnost ve vlastní třídě atributu, určuje, že dekorovaná vlastnost je volitelná a není nutné ji dodávat Exportér.</span><span class="sxs-lookup"><span data-stu-id="62779-281">When this attribute is applied to a property in a custom attribute class, it specifies that the decorated property is optional and does not have to be supplied by an exporter.</span></span> <span data-ttu-id="62779-282">Pokud hodnota vlastnosti není dodána, přiřadí se výchozí hodnota pro svůj typ vlastnosti (obvykle `null` `false`, nebo 0).</span><span class="sxs-lookup"><span data-stu-id="62779-282">If a value for the property is not supplied, it will be assigned the default value for its property type (usually `null`, `false`, or 0.)</span></span>

<a name="creation_policies"></a>

## <a name="creation-policies"></a><span data-ttu-id="62779-283">Zásady vytváření</span><span class="sxs-lookup"><span data-stu-id="62779-283">Creation Policies</span></span>

<span data-ttu-id="62779-284">Pokud část určuje import a složení, kontejner kompozice se pokusí najít vyhovující export.</span><span class="sxs-lookup"><span data-stu-id="62779-284">When a part specifies an import and composition is performed, the composition container attempts to find a matching export.</span></span> <span data-ttu-id="62779-285">Pokud odpovídá import s exportem úspěšně, je importovaný člen nastaven na instanci exportovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="62779-285">If it matches the import with an export successfully, the importing member is set to an instance of the exported object.</span></span> <span data-ttu-id="62779-286">Umístění, ze kterého pochází tato instance, je ovládáno pomocí *zásad vytváření*exportovaných částí.</span><span class="sxs-lookup"><span data-stu-id="62779-286">Where this instance comes from is controlled by the exporting part's *creation policy*.</span></span>

<span data-ttu-id="62779-287">Dvě možné zásady vytváření jsou *sdílené* a *nesdílené*.</span><span class="sxs-lookup"><span data-stu-id="62779-287">The two possible creation policies are *shared* and *non-shared*.</span></span> <span data-ttu-id="62779-288">Součást s zásadou vytváření Shared bude sdílená mezi každým importem v kontejneru pro součást s touto smlouvou.</span><span class="sxs-lookup"><span data-stu-id="62779-288">A part with a creation policy of shared will be shared between every import in the container for a part with that contract.</span></span> <span data-ttu-id="62779-289">Pokud modul kompozice najde shodu a musí nastavit vlastnost import, vytvoří instanci nové kopie součásti pouze v případě, že ještě neexistuje. v opačném případě poskytne existující kopii.</span><span class="sxs-lookup"><span data-stu-id="62779-289">When the composition engine finds a match and has to set an importing property, it will instantiate a new copy of the part only if one does not already exist; otherwise, it will supply the existing copy.</span></span> <span data-ttu-id="62779-290">To znamená, že mnoho objektů může mít odkazy na stejnou část.</span><span class="sxs-lookup"><span data-stu-id="62779-290">This means that many objects may have references to the same part.</span></span> <span data-ttu-id="62779-291">Tyto části by neměly spoléhat na vnitřní stav, který může být změněn z mnoha míst.</span><span class="sxs-lookup"><span data-stu-id="62779-291">Such parts should not rely on internal state that might be changed from many places.</span></span> <span data-ttu-id="62779-292">Tyto zásady jsou vhodné pro statické části, součásti, které poskytují služby, a součásti, které využívají spoustu paměti nebo jiných prostředků.</span><span class="sxs-lookup"><span data-stu-id="62779-292">This policy is appropriate for static parts, parts that provide services, and parts that consume a lot of memory or other resources.</span></span>

<span data-ttu-id="62779-293">Součást se zásadami vytváření nesdílených se vytvoří pokaždé, když se najde odpovídající import pro jeden z jeho exportů.</span><span class="sxs-lookup"><span data-stu-id="62779-293">A part with the creation policy of non-shared will be created every time a matching import for one of its exports is found.</span></span> <span data-ttu-id="62779-294">Pro každý import v kontejneru, který odpovídá jedné z exportovaných smluv, bude vytvořena instance nového kopírování.</span><span class="sxs-lookup"><span data-stu-id="62779-294">A new copy will therefore be instantiated for every import in the container that matches one of the part's exported contracts.</span></span> <span data-ttu-id="62779-295">Vnitřní stav těchto kopií nebude sdílen.</span><span class="sxs-lookup"><span data-stu-id="62779-295">The internal state of these copies will not be shared.</span></span> <span data-ttu-id="62779-296">Tyto zásady jsou vhodné pro části, kde každý import vyžaduje vlastní vnitřní stav.</span><span class="sxs-lookup"><span data-stu-id="62779-296">This policy is appropriate for parts where each import requires its own internal state.</span></span>

<span data-ttu-id="62779-297">Import i export může určovat zásadu vytváření součásti, a to z hodnot `Shared`, `NonShared`nebo. `Any`</span><span class="sxs-lookup"><span data-stu-id="62779-297">Both the import and the export can specify the creation policy of a part, from among the values `Shared`, `NonShared`, or `Any`.</span></span> <span data-ttu-id="62779-298">Výchozí hodnota je `Any` pro import i export.</span><span class="sxs-lookup"><span data-stu-id="62779-298">The default is `Any` for both imports and exports.</span></span> <span data-ttu-id="62779-299">Export, který určuje `Shared` nebo `NonShared` bude odpovídat pouze importu, který určuje stejné nebo které určuje `Any`.</span><span class="sxs-lookup"><span data-stu-id="62779-299">An export that specifies `Shared` or `NonShared` will only match an import that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="62779-300">Podobně import, který určuje `Shared` nebo `NonShared` , bude odpovídat pouze exportu, který určuje stejné nebo, které určuje. `Any`</span><span class="sxs-lookup"><span data-stu-id="62779-300">Similarly, an import that specifies `Shared` or `NonShared` will only match an export that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="62779-301">Importy a exporty s nekompatibilními zásadami vytváření nejsou považovány za shodu, a to stejným způsobem jako při importu a exportu, jejichž název kontraktu nebo typ kontraktu se neshodují.</span><span class="sxs-lookup"><span data-stu-id="62779-301">Imports and exports with incompatible creation policies are not considered a match, in the same way as an import and export whose contract name or contract type are not a match.</span></span> <span data-ttu-id="62779-302">Pokud pro import i export určíte `Any`nebo nezadáte zásadu vytváření a výchozí hodnotu pro `Any`, zásady vytváření se budou sdílet jako výchozí.</span><span class="sxs-lookup"><span data-stu-id="62779-302">If both import and export specify `Any`, or do not specify a creation policy and default to `Any`, the creation policy will default to shared.</span></span>

<span data-ttu-id="62779-303">Následující příklad ukazuje import i export, které určují zásady vytváření.</span><span class="sxs-lookup"><span data-stu-id="62779-303">The following example shows both imports and exports specifying creation policies.</span></span> <span data-ttu-id="62779-304">`PartOne`neurčuje zásadu vytváření, takže výchozí hodnota je `Any`.</span><span class="sxs-lookup"><span data-stu-id="62779-304">`PartOne` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="62779-305">`PartTwo`neurčuje zásadu vytváření, takže výchozí hodnota je `Any`.</span><span class="sxs-lookup"><span data-stu-id="62779-305">`PartTwo` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="62779-306">Vzhledem k tomu, že se naimportují i exportují výchozí hodnoty do `Any`, `PartOne` budou sdíleny.</span><span class="sxs-lookup"><span data-stu-id="62779-306">Since both import and export default to `Any`, `PartOne` will be shared.</span></span> <span data-ttu-id="62779-307">`PartThree`Určuje zásadu `Shared` vytváření, takže `PartTwo` a `PartThree` bude sdílet stejnou kopii. `PartOne`</span><span class="sxs-lookup"><span data-stu-id="62779-307">`PartThree` specifies a `Shared` creation policy, so `PartTwo` and `PartThree` will share the same copy of `PartOne`.</span></span> <span data-ttu-id="62779-308">`PartFour`Určuje zásadu `NonShared` vytváření, takže `PartFour` se v `PartFive`nástroji nesdílí.</span><span class="sxs-lookup"><span data-stu-id="62779-308">`PartFour` specifies a `NonShared` creation policy, so `PartFour` will be non-shared in `PartFive`.</span></span> <span data-ttu-id="62779-309">`PartSix`Určuje zásadu `NonShared` vytváření.</span><span class="sxs-lookup"><span data-stu-id="62779-309">`PartSix` specifies a `NonShared` creation policy.</span></span> <span data-ttu-id="62779-310">`PartFive`a `PartSix` každý z `PartFour`nich získá samostatné kopie.</span><span class="sxs-lookup"><span data-stu-id="62779-310">`PartFive` and `PartSix` will each receive separate copies of `PartFour`.</span></span> <span data-ttu-id="62779-311">`PartSeven`Určuje zásadu `Shared` vytváření.</span><span class="sxs-lookup"><span data-stu-id="62779-311">`PartSeven` specifies a `Shared` creation policy.</span></span> <span data-ttu-id="62779-312">Vzhledem k tomu `PartFour` `Shared`, že není exportována se zásadami vytváření, `PartSeven` import neshoduje s žádným a nebude vyplněn.</span><span class="sxs-lookup"><span data-stu-id="62779-312">Because there is no exported `PartFour` with a creation policy of `Shared`, the `PartSeven` import does not match anything and will not be filled.</span></span>

```vb
<Export()>
Public Class PartOne
    'The default creation policy for an export is Any.
End Class

Public Class PartTwo

    <Import()>
    Public Property partOne As PartOne

    'The default creation policy for an import is Any.
    'If both policies are Any, the part will be shared.

End Class

Public Class PartThree

    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>
    Public Property partOne As PartOne

    'The Shared creation policy is explicitly specified.
    'PartTwo and PartThree will receive references to the
    'SAME copy of PartOne.

End Class

<Export()>
<PartCreationPolicy(CreationPolicy.NonShared)>
Public Class PartFour
    'The NonShared creation policy is explicitly specified.
End Class

Public Class PartFive

    <Import()>
    Public Property partFour As PartFour

    'The default creation policy for an import is Any.
    'Since the export's creation policy was explicitly
    'defined, the creation policy for this property will
    'be non-shared.

End Class

Public Class PartSix

    <Import(RequiredCreationPolicy:=CreationPolicy.NonShared)>
    Public Property partFour As PartFour

    'Both import and export specify matching creation
    'policies.  PartFive and PartSix will each receive
    'SEPARATE copies of PartFour, each with its own
    'internal state.

End Class

Public Class PartSeven

    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>
    Public Property partFour As PartFour

    'A creation policy mismatch.  Because there is no
    'exported PartFour with a creation policy of Shared,
    'this import does not match anything and will not be
    'filled.

End Class
```

```csharp
[Export]
public class PartOne
{
    //The default creation policy for an export is Any.
}

public class PartTwo
{
    [Import]
    public PartOne partOne { get; set; }

    //The default creation policy for an import is Any.
    //If both policies are Any, the part will be shared.
}

public class PartThree
{
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]
    public PartOne partOne { get; set; }

    //The Shared creation policy is explicitly specified.
    //PartTwo and PartThree will receive references to the
    //SAME copy of PartOne.
}

[Export]
[PartCreationPolicy(CreationPolicy.NonShared)]
public class PartFour
{
    //The NonShared creation policy is explicitly specified.
}

public class PartFive
{
    [Import]
    public PartFour partFour { get; set; }

    //The default creation policy for an import is Any.
    //Since the export's creation policy was explicitly
    //defined, the creation policy for this property will
    //be non-shared.
}

public class PartSix
{
    [Import(RequiredCreationPolicy = CreationPolicy.NonShared)]
    public PartFour partFour { get; set; }

    //Both import and export specify matching creation
    //policies.  PartFive and PartSix will each receive
    //SEPARATE copies of PartFour, each with its own
    //internal state.
}

public class PartSeven
{
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]
    public PartFour partFour { get; set; }

    //A creation policy mismatch.  Because there is no
    //exported PartFour with a creation policy of Shared,
    //this import does not match anything and will not be
    //filled.
}
```

<a name="life_cycle_and_disposing"></a>

## <a name="life-cycle-and-disposing"></a><span data-ttu-id="62779-313">Životní cyklus a odstraňování</span><span class="sxs-lookup"><span data-stu-id="62779-313">Life Cycle and Disposing</span></span>

<span data-ttu-id="62779-314">Vzhledem k tomu, že části jsou hostovány v kontejneru složení, jejich životní cyklus může být složitější než běžné objekty.</span><span class="sxs-lookup"><span data-stu-id="62779-314">Because parts are hosted in the composition container, their life cycle can be more complex than ordinary objects.</span></span> <span data-ttu-id="62779-315">Části můžou implementovat dvě důležitá rozhraní související s životním `IDisposable` cyklem `IPartImportsSatisfiedNotification`: a.</span><span class="sxs-lookup"><span data-stu-id="62779-315">Parts can implement two important life cycle-related interfaces: `IDisposable` and `IPartImportsSatisfiedNotification`.</span></span>

<span data-ttu-id="62779-316">Součásti, které vyžadují, aby se prováděla práce při vypnutí nebo které potřebují uvolnit prostředky, `IDisposable`by měly implementovat běžné pro .NET Framework objekty.</span><span class="sxs-lookup"><span data-stu-id="62779-316">Parts that require work to be performed at shut down or that need to release resources should implement `IDisposable`, as usual for .NET Framework objects.</span></span> <span data-ttu-id="62779-317">Vzhledem k tomu, že kontejner vytváří a udržuje odkazy na části, pouze kontejner, který vlastní část, by měl `Dispose` volat metodu.</span><span class="sxs-lookup"><span data-stu-id="62779-317">However, since the container creates and maintains references to parts, only the container that owns a part should call the `Dispose` method on it.</span></span> <span data-ttu-id="62779-318">Samotný kontejner implementuje `IDisposable`a jako součást jeho vyčištění v `Dispose` rámci něj bude volat `Dispose` všechny části, které vlastní.</span><span class="sxs-lookup"><span data-stu-id="62779-318">The container itself implements `IDisposable`, and as portion of its cleanup in `Dispose` it will call `Dispose` on all the parts that it owns.</span></span> <span data-ttu-id="62779-319">Z tohoto důvodu byste měli kontejner kompozice vždy uvolnit, pokud je a jakékoliv součásti, které vlastní, již nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="62779-319">For this reason, you should always dispose the composition container when it and any parts it owns are no longer needed.</span></span>

<span data-ttu-id="62779-320">V případě dlouhodobých kontejnerů kompozice se může stát, že spotřeba paměti podle částí se zásadou vytváření nesdíleného není sdílená.</span><span class="sxs-lookup"><span data-stu-id="62779-320">For long-lived composition containers, memory consumption by parts with a creation policy of non-shared can become a problem.</span></span> <span data-ttu-id="62779-321">Tyto nesdílené části je možné vytvořit víckrát, takže nebudou uvolněny, dokud nedojde k uvolnění samotného kontejneru.</span><span class="sxs-lookup"><span data-stu-id="62779-321">These non-shared parts can be created multiple times and will not be disposed until the container itself is disposed.</span></span> <span data-ttu-id="62779-322">Chcete-li se tomuto `ReleaseExport` postupu zabývat, kontejner poskytuje metodu.</span><span class="sxs-lookup"><span data-stu-id="62779-322">To deal with this, the container provides the `ReleaseExport` method.</span></span> <span data-ttu-id="62779-323">Volání této metody u nesdíleného exportu odebere tento export z kontejneru složení a odstraní jej.</span><span class="sxs-lookup"><span data-stu-id="62779-323">Calling this method on a non-shared export removes that export from the composition container and disposes it.</span></span> <span data-ttu-id="62779-324">Části, které se používají jenom odebraným exportem, a tak i na stromové struktuře, se taky odeberou a odstraňují.</span><span class="sxs-lookup"><span data-stu-id="62779-324">Parts that are used only by the removed export, and so on down the tree, are also removed and disposed.</span></span> <span data-ttu-id="62779-325">Tímto způsobem lze prostředky uvolnit bez likvidace kontejneru kompozice.</span><span class="sxs-lookup"><span data-stu-id="62779-325">In this way, resources can be reclaimed without disposing the composition container itself.</span></span>

<span data-ttu-id="62779-326">`IPartImportsSatisfiedNotification`obsahuje jednu metodu s `OnImportsSatisfied`názvem.</span><span class="sxs-lookup"><span data-stu-id="62779-326">`IPartImportsSatisfiedNotification` contains one method named `OnImportsSatisfied`.</span></span> <span data-ttu-id="62779-327">Tato metoda je volána kontejnerem kompozice na všech částech, které implementují rozhraní po dokončení složení, a importy části jsou připravené k použití.</span><span class="sxs-lookup"><span data-stu-id="62779-327">This method is called by the composition container on any parts that implement the interface when composition has been completed and the part's imports are ready for use.</span></span> <span data-ttu-id="62779-328">Části jsou vytvořeny modulem složení, aby bylo možné vyplnit importy dalších částí.</span><span class="sxs-lookup"><span data-stu-id="62779-328">Parts are created by the composition engine to fill the imports of other parts.</span></span> <span data-ttu-id="62779-329">Před nastavením importu části nelze provést žádnou inicializaci, která spoléhá na nebo zpracovává importované hodnoty v konstruktoru součásti, pokud tyto hodnoty nebyly zadány jako požadavky pomocí `ImportingConstructor` atributu.</span><span class="sxs-lookup"><span data-stu-id="62779-329">Before the imports of a part have been set, you cannot perform any initialization that relies on or manipulates imported values in the part constructor unless those values have been specified as prerequisites by using the `ImportingConstructor` attribute.</span></span> <span data-ttu-id="62779-330">To je obvykle upřednostňovaná metoda, ale v některých případech nemusí být injektáže konstruktoru k dispozici.</span><span class="sxs-lookup"><span data-stu-id="62779-330">This is normally the preferred method, but in some cases, constructor injection may not be available.</span></span> <span data-ttu-id="62779-331">V těchto případech může být inicializace provedena v `OnImportsSatisfied`a část by měla implementovat. `IPartImportsSatisfiedNotification`</span><span class="sxs-lookup"><span data-stu-id="62779-331">In those cases, initialization can be performed in `OnImportsSatisfied`, and the part should implement `IPartImportsSatisfiedNotification`.</span></span>

## <a name="see-also"></a><span data-ttu-id="62779-332">Viz také</span><span class="sxs-lookup"><span data-stu-id="62779-332">See also</span></span>

- [<span data-ttu-id="62779-333">Video pro kanál 9: otevření aplikací pomocí Managed Extensibility Framework</span><span class="sxs-lookup"><span data-stu-id="62779-333">Channel 9 Video: Open Up Your Applications with the Managed Extensibility Framework</span></span>](https://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)
- [<span data-ttu-id="62779-334">Video pro kanál 9: Managed Extensibility Framework (MEF) 2,0</span><span class="sxs-lookup"><span data-stu-id="62779-334">Channel 9 Video: Managed Extensibility Framework (MEF) 2.0</span></span>](https://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)

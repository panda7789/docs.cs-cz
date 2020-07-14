---
title: Přehled modelu programování s přidělenými atributy (MEF)
description: Začněte s atributem programování modelu, což je výchozí programovací model pro Managed Extensibility Framework (MEF) v .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MEF, attributed programming model
- attributed programming model [MEF]
ms.assetid: 49b787ff-2741-4836-ad51-c3017dc592d4
ms.openlocfilehash: aea3a19ffe6f177901e5c0839b618bb36f573beb
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281365"
---
# <a name="attributed-programming-model-overview-mef"></a><span data-ttu-id="e1689-103">Přehled modelu programování s přidělenými atributy (MEF)</span><span class="sxs-lookup"><span data-stu-id="e1689-103">Attributed Programming Model Overview (MEF)</span></span>

<span data-ttu-id="e1689-104">V Managed Extensibility Framework (MEF) je *programovací model* specifickou metodou pro definování sady konceptuálních objektů, na kterých funguje MEF.</span><span class="sxs-lookup"><span data-stu-id="e1689-104">In the Managed Extensibility Framework (MEF), a *programming model* is a particular method of defining the set of conceptual objects on which MEF operates.</span></span> <span data-ttu-id="e1689-105">Tyto koncepční objekty zahrnují součásti, importy a exporty.</span><span class="sxs-lookup"><span data-stu-id="e1689-105">These conceptual objects include parts, imports, and exports.</span></span> <span data-ttu-id="e1689-106">MEF používá tyto objekty, ale neurčuje, jak by měly být reprezentovány.</span><span class="sxs-lookup"><span data-stu-id="e1689-106">MEF uses these objects, but does not specify how they should be represented.</span></span> <span data-ttu-id="e1689-107">Proto je možné využít širokou škálu programovacích modelů, včetně přizpůsobených programovacích modelů.</span><span class="sxs-lookup"><span data-stu-id="e1689-107">Therefore, a wide variety of programming models are possible, including customized programming models.</span></span>

<span data-ttu-id="e1689-108">Výchozím programovacím modelem používaným v MEF je *model programování s atributy*.</span><span class="sxs-lookup"><span data-stu-id="e1689-108">The default programming model used in MEF is the *attributed programming model*.</span></span> <span data-ttu-id="e1689-109">V částech modelu programování s atributy jsou importy, exporty a další objekty definovány s atributy, které upraví běžné .NET Framework třídy.</span><span class="sxs-lookup"><span data-stu-id="e1689-109">In the attributed programming model parts, imports, exports, and other objects are defined with attributes that decorate ordinary .NET Framework classes.</span></span> <span data-ttu-id="e1689-110">V tomto tématu se dozvíte, jak pomocí atributů poskytovaných programovacím modelem s atributy vytvořit aplikaci MEF.</span><span class="sxs-lookup"><span data-stu-id="e1689-110">This topic explains how to use the attributes provided by the attributed programming model to create a MEF application.</span></span>

<a name="import_and_export_basics"></a>

## <a name="import-and-export-basics"></a><span data-ttu-id="e1689-111">Základy importu a exportu</span><span class="sxs-lookup"><span data-stu-id="e1689-111">Import and Export Basics</span></span>

<span data-ttu-id="e1689-112">*Export* je hodnota, kterou část poskytuje jiným částem v kontejneru a *Import* je požadavek, aby část, která je vyjádřena v kontejneru, byla vyplněna z dostupných exportů.</span><span class="sxs-lookup"><span data-stu-id="e1689-112">An *export* is a value that a part provides to other parts in the container, and an *import* is a requirement that a part expresses to the container, to be filled from the available exports.</span></span> <span data-ttu-id="e1689-113">V programovacím modelu s atributy jsou importy a exporty deklarovány pomocí tříd upravení nebo členů `Import` s `Export` atributy a.</span><span class="sxs-lookup"><span data-stu-id="e1689-113">In the attributed programming model, imports and exports are declared by decorating classes or members with the `Import` and `Export` attributes.</span></span> <span data-ttu-id="e1689-114">`Export`Atribut může vytřídit třídu, pole, vlastnost nebo metodu, zatímco atribut může setřídit `Import` pole, vlastnost nebo parametr konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="e1689-114">The `Export` attribute can decorate a class, field, property, or method, while the `Import` attribute can decorate a field, property, or constructor parameter.</span></span>

<span data-ttu-id="e1689-115">Aby se import shodoval s exportem, musí mít import a export stejný *kontrakt*.</span><span class="sxs-lookup"><span data-stu-id="e1689-115">In order for an import to be matched with an export, the import and export must have the same *contract*.</span></span> <span data-ttu-id="e1689-116">Smlouva se skládá z řetězce, který se označuje jako *název kontraktu*a typ exportovaného nebo importovaného objektu, který se označuje jako *Typ kontraktu*.</span><span class="sxs-lookup"><span data-stu-id="e1689-116">The contract consists of a string, called the *contract name*, and the type of the exported or imported object, called the *contract type*.</span></span> <span data-ttu-id="e1689-117">Pouze v případě, že shoda názvu kontraktu a typu smlouvy je exportem, který je považován za splnění konkrétního importu.</span><span class="sxs-lookup"><span data-stu-id="e1689-117">Only if both the contract name and contract type match is an export considered to fulfill a particular import.</span></span>

<span data-ttu-id="e1689-118">Buď nebo oba parametry kontraktu mohou být implicitní nebo explicitní.</span><span class="sxs-lookup"><span data-stu-id="e1689-118">Either or both of the contract parameters can be implicit or explicit.</span></span> <span data-ttu-id="e1689-119">Následující kód ukazuje třídu, která deklaruje základní import.</span><span class="sxs-lookup"><span data-stu-id="e1689-119">The following code shows a class that declares a basic import.</span></span>

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

<span data-ttu-id="e1689-120">V tomto importu `Import` nemá atribut ani typ kontraktu ani připojený parametr názvu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e1689-120">In this import, the `Import` attribute has neither a contract type nor a contract name parameter attached.</span></span> <span data-ttu-id="e1689-121">Proto obě budou odvozeny z dekorované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e1689-121">Therefore, both will be inferred from the decorated property.</span></span> <span data-ttu-id="e1689-122">V takovém případě bude typ kontraktu `IMyAddin` a název kontraktu bude jedinečným řetězcem vytvořeným z typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e1689-122">In this case, the contract type will be `IMyAddin`, and the contract name will be a unique string created from the contract type.</span></span> <span data-ttu-id="e1689-123">(Jinými slovy, název kontraktu bude odpovídat pouze exportům, jejichž názvy jsou také odvozeny od typu `IMyAddin` .)</span><span class="sxs-lookup"><span data-stu-id="e1689-123">(In other words, the contract name will match only exports whose names are also inferred from the type `IMyAddin`.)</span></span>

<span data-ttu-id="e1689-124">Následující příklad ukazuje export, který odpovídá předchozímu importu.</span><span class="sxs-lookup"><span data-stu-id="e1689-124">The following shows an export that matches the previous import.</span></span>

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

<span data-ttu-id="e1689-125">V tomto exportu je typ kontraktu, `IMyAddin` protože je zadán jako parametr `Export` atributu.</span><span class="sxs-lookup"><span data-stu-id="e1689-125">In this export, the contract type is `IMyAddin` because it is specified as a parameter of the `Export` attribute.</span></span> <span data-ttu-id="e1689-126">Exportovaný typ musí být buď stejný jako typ kontraktu, odvozený od typu kontraktu, nebo implementovat typ kontraktu, pokud se jedná o rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e1689-126">The exported type must be either the same as the contract type, derive from the contract type, or implement the contract type if it is an interface.</span></span> <span data-ttu-id="e1689-127">V tomto exportu samotný typ `MyLogger` implementuje rozhraní `IMyAddin` .</span><span class="sxs-lookup"><span data-stu-id="e1689-127">In this export, the actual type `MyLogger` implements the interface `IMyAddin`.</span></span> <span data-ttu-id="e1689-128">Název kontraktu je odvozený od typu kontraktu, což znamená, že tento export bude odpovídat předchozímu importu.</span><span class="sxs-lookup"><span data-stu-id="e1689-128">The contract name is inferred from the contract type, which means that this export will match the previous import.</span></span>

> [!NOTE]
> <span data-ttu-id="e1689-129">Exporty a importy by měly být obvykle deklarovány ve veřejných třídách nebo členech.</span><span class="sxs-lookup"><span data-stu-id="e1689-129">Exports and imports should usually be declared on public classes or members.</span></span> <span data-ttu-id="e1689-130">Další deklarace jsou podporovány, ale export nebo import privátního, chráněného nebo interního člena přerušuje model izolace pro danou část a proto se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="e1689-130">Other declarations are supported, but exporting or importing a private, protected, or internal member breaks the isolation model for the part and is therefore not recommended.</span></span>

<span data-ttu-id="e1689-131">Typ kontraktu se musí přesně shodovat s exportem a importem, aby se dalo považovat za shodu.</span><span class="sxs-lookup"><span data-stu-id="e1689-131">The contract type must match exactly for the export and import to be considered a match.</span></span> <span data-ttu-id="e1689-132">Vezměte v úvahu následující export.</span><span class="sxs-lookup"><span data-stu-id="e1689-132">Consider the following export.</span></span>

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

<span data-ttu-id="e1689-133">V tomto exportu je jako typ kontraktu `MyLogger` místo `IMyAddin` .</span><span class="sxs-lookup"><span data-stu-id="e1689-133">In this export, the contract type is `MyLogger` instead of `IMyAddin`.</span></span> <span data-ttu-id="e1689-134">I když `MyLogger` implementují `IMyAddin` , a proto lze přetypovat na `IMyAddin` objekt, tento export nebude odpovídat předchozímu importu, protože typy kontraktů nejsou stejné.</span><span class="sxs-lookup"><span data-stu-id="e1689-134">Even though `MyLogger` implements `IMyAddin`, and therefore could be cast to an `IMyAddin` object, this export will not match the previous import because the contract types are not the same.</span></span>

<span data-ttu-id="e1689-135">Obecně není nutné zadávat název kontraktu a většina kontraktů by měla být definována v souvislosti s typem a metadaty kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e1689-135">In general, it is not necessary to specify the contract name, and most contracts should be defined in terms of the contract type and metadata.</span></span> <span data-ttu-id="e1689-136">Za určitých okolností je však důležité zadat název kontraktu přímo.</span><span class="sxs-lookup"><span data-stu-id="e1689-136">However, under certain circumstances, it is important to specify the contract name directly.</span></span> <span data-ttu-id="e1689-137">Nejběžnějším případem je, že třída exportuje několik hodnot, které sdílejí společný typ, jako jsou primitivní.</span><span class="sxs-lookup"><span data-stu-id="e1689-137">The most common case is when a class exports several values that share a common type, such as primitives.</span></span> <span data-ttu-id="e1689-138">Název kontraktu lze zadat jako první parametr `Import` `Export` atributu or.</span><span class="sxs-lookup"><span data-stu-id="e1689-138">The contract name can be specified as the first parameter of the `Import` or `Export` attribute.</span></span> <span data-ttu-id="e1689-139">Následující kód ukazuje import a export se zadaným názvem kontraktu `MajorRevision` .</span><span class="sxs-lookup"><span data-stu-id="e1689-139">The following code shows an import and an export with a specified contract name of `MajorRevision`.</span></span>

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

<span data-ttu-id="e1689-140">Pokud není zadán typ kontraktu, bude stále odvozen od typu importu nebo exportu.</span><span class="sxs-lookup"><span data-stu-id="e1689-140">If the contract type is not specified, it will still be inferred from the type of the import or export.</span></span> <span data-ttu-id="e1689-141">Nicméně i v případě, že je název kontraktu zadán explicitně, musí se typ kontraktu přesně shodovat s importem a exportem, aby bylo možné považovat za shodu.</span><span class="sxs-lookup"><span data-stu-id="e1689-141">However, even if the contract name is specified explicitly, the contract type must also match exactly for the import and export to be considered a match.</span></span> <span data-ttu-id="e1689-142">Například pokud by `MajorRevision` pole bylo typu String, odvozené typy kontraktu se neshodují a export by neodpovídal importu, i když má stejný název kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e1689-142">For example, if the `MajorRevision` field was a string, the inferred contract types would not match and the export would not match the import, despite having the same contract name.</span></span>

### <a name="importing-and-exporting-a-method"></a><span data-ttu-id="e1689-143">Import a export metody</span><span class="sxs-lookup"><span data-stu-id="e1689-143">Importing and Exporting a Method</span></span>

<span data-ttu-id="e1689-144">`Export`Atribut může také roztřídit metodu stejným způsobem jako třída, vlastnost nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="e1689-144">The `Export` attribute can also decorate a method, in the same way as a class, property, or function.</span></span> <span data-ttu-id="e1689-145">Exporty metod musí určovat typ kontraktu nebo název kontraktu, protože typ nelze odvodit.</span><span class="sxs-lookup"><span data-stu-id="e1689-145">Method exports must specify a contract type or contract name, as the type cannot be inferred.</span></span> <span data-ttu-id="e1689-146">Zadaný typ může být buď vlastní delegát, nebo obecný typ, například `Func` .</span><span class="sxs-lookup"><span data-stu-id="e1689-146">The specified type can be either a custom delegate or a generic type, such as `Func`.</span></span> <span data-ttu-id="e1689-147">Následující třída exportuje metodu s názvem `DoSomething` .</span><span class="sxs-lookup"><span data-stu-id="e1689-147">The following class exports a method named `DoSomething`.</span></span>

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

<span data-ttu-id="e1689-148">V této třídě `DoSomething` Metoda přijímá jeden `int` parametr a vrátí `string` .</span><span class="sxs-lookup"><span data-stu-id="e1689-148">In this class, the `DoSomething` method takes a single `int` parameter and returns a `string`.</span></span> <span data-ttu-id="e1689-149">Aby bylo možné tento export vyhledat, musí součást importu deklarovat příslušného člena.</span><span class="sxs-lookup"><span data-stu-id="e1689-149">To match this export, the importing part must declare an appropriate member.</span></span> <span data-ttu-id="e1689-150">Následující třída importuje `DoSomething` metodu.</span><span class="sxs-lookup"><span data-stu-id="e1689-150">The following class imports the `DoSomething` method.</span></span>

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

<span data-ttu-id="e1689-151">Další informace o použití `Func<T, T>` objektu naleznete v tématu <xref:System.Func%602> .</span><span class="sxs-lookup"><span data-stu-id="e1689-151">For more information about how to use of the `Func<T, T>` object, see <xref:System.Func%602>.</span></span>

<a name="types_of_imports"></a>

## <a name="types-of-imports"></a><span data-ttu-id="e1689-152">Typy importů</span><span class="sxs-lookup"><span data-stu-id="e1689-152">Types of Imports</span></span>

<span data-ttu-id="e1689-153">Rozhraní MEF podporují několik typů importu, včetně dynamického, opožděného, předpokladu a volitelného.</span><span class="sxs-lookup"><span data-stu-id="e1689-153">MEF support several import types, including dynamic, lazy, prerequisite, and optional.</span></span>

### <a name="dynamic-imports"></a><span data-ttu-id="e1689-154">Dynamické importy</span><span class="sxs-lookup"><span data-stu-id="e1689-154">Dynamic Imports</span></span>

<span data-ttu-id="e1689-155">V některých případech je možné, že import třídy bude odpovídat exportům libovolného typu, který má konkrétní název kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e1689-155">In some cases, the importing class may want to match exports of any type that have a particular contract name.</span></span> <span data-ttu-id="e1689-156">V tomto scénáři třída může deklarovat *dynamický import*.</span><span class="sxs-lookup"><span data-stu-id="e1689-156">In this scenario, the class can declare a *dynamic import*.</span></span> <span data-ttu-id="e1689-157">Následující import odpovídá jakémukoli exportu s názvem kontraktu "TheString".</span><span class="sxs-lookup"><span data-stu-id="e1689-157">The following import matches any export with contract name "TheString".</span></span>

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

<span data-ttu-id="e1689-158">Pokud je typ kontraktu odvozen z `dynamic` klíčového slova, bude odpovídat jakémukoli typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e1689-158">When the contract type is inferred from the `dynamic` keyword, it will match any contract type.</span></span> <span data-ttu-id="e1689-159">V takovém případě by měl import **vždy** určovat název kontraktu, na kterém se bude shodovat.</span><span class="sxs-lookup"><span data-stu-id="e1689-159">In this case, an import should **always** specify a contract name to match on.</span></span> <span data-ttu-id="e1689-160">(Pokud není zadaný žádný název kontraktu, import se považuje za neodpovídající žádným exportům.) Oba následující exporty by odpovídaly předchozímu importu.</span><span class="sxs-lookup"><span data-stu-id="e1689-160">(If no contract name is specified, the import will be considered to match no exports.) Both of the following exports would match the previous import.</span></span>

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

<span data-ttu-id="e1689-161">Import třídy musí být připravený k práci s objektem libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="e1689-161">Obviously, the importing class must be prepared to deal with an object of arbitrary type.</span></span>

### <a name="lazy-imports"></a><span data-ttu-id="e1689-162">Opožděné importy</span><span class="sxs-lookup"><span data-stu-id="e1689-162">Lazy Imports</span></span>

<span data-ttu-id="e1689-163">V některých případech importovaná třída může vyžadovat nepřímý odkaz na importovaný objekt, aby se objekt nevytvořil okamžitě.</span><span class="sxs-lookup"><span data-stu-id="e1689-163">In some cases, the importing class may require an indirect reference to the imported object, so that the object is not instantiated immediately.</span></span> <span data-ttu-id="e1689-164">V tomto scénáři třída může deklarovat *opožděné importy* pomocí typu kontraktu `Lazy<T>` .</span><span class="sxs-lookup"><span data-stu-id="e1689-164">In this scenario, the class can declare a *lazy import* by using a contract type of `Lazy<T>`.</span></span> <span data-ttu-id="e1689-165">Následující importovaná vlastnost deklaruje opožděný import.</span><span class="sxs-lookup"><span data-stu-id="e1689-165">The following importing property declares a lazy import.</span></span>

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

<span data-ttu-id="e1689-166">Z hlediska modulu kompozice je typ kontraktu `Lazy<T>` považován za shodný s typem kontraktu `T` .</span><span class="sxs-lookup"><span data-stu-id="e1689-166">From the point of view of the composition engine, a contract type of `Lazy<T>` is considered identical to contract type of `T`.</span></span> <span data-ttu-id="e1689-167">Předchozí import proto odpovídá následujícímu exportu.</span><span class="sxs-lookup"><span data-stu-id="e1689-167">Therefore, the previous import would match the following export.</span></span>

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

<span data-ttu-id="e1689-168">Název kontraktu a typ kontraktu lze zadat v `Import` atributu pro opožděné importy, jak je popsáno výše v části "základní importy a export".</span><span class="sxs-lookup"><span data-stu-id="e1689-168">The contract name and contract type can be specified in the `Import` attribute for a lazy import, as described earlier in the "Basic Imports and Exports" section.</span></span>

### <a name="prerequisite-imports"></a><span data-ttu-id="e1689-169">Import požadovaných součástí</span><span class="sxs-lookup"><span data-stu-id="e1689-169">Prerequisite Imports</span></span>

<span data-ttu-id="e1689-170">Exportované části MEF jsou obvykle vytvářeny modulem složení, a to v reakci na přímý požadavek nebo na nutnost vyplnit odpovídající import.</span><span class="sxs-lookup"><span data-stu-id="e1689-170">Exported MEF parts are typically created by the composition engine, in response to a direct request or the need to fill a matched import.</span></span> <span data-ttu-id="e1689-171">Ve výchozím nastavení používá modul kompozice při vytváření součásti konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="e1689-171">By default, when creating a part, the composition engine uses the parameter-less constructor.</span></span> <span data-ttu-id="e1689-172">Chcete-li, aby modul používal jiný konstruktor, můžete jej označit `ImportingConstructor` atributem.</span><span class="sxs-lookup"><span data-stu-id="e1689-172">To make the engine use a different constructor, you can mark it with the `ImportingConstructor` attribute.</span></span>

<span data-ttu-id="e1689-173">Každá část může mít pouze jeden konstruktor pro použití modulem složení.</span><span class="sxs-lookup"><span data-stu-id="e1689-173">Each part may have only one constructor for use by the composition engine.</span></span> <span data-ttu-id="e1689-174">Pokud neposkytnete žádný konstruktor bez parametrů ani žádný `ImportingConstructor` atribut, nebo pokud `ImportingConstructor` zadáte více než jeden atribut, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="e1689-174">Providing no parameterless constructor and no `ImportingConstructor` attribute, or providing more than one `ImportingConstructor` attribute, will produce an error.</span></span>

<span data-ttu-id="e1689-175">Chcete-li vyplnit parametry konstruktoru označeného `ImportingConstructor` atributem, všechny tyto parametry jsou automaticky deklarovány jako import.</span><span class="sxs-lookup"><span data-stu-id="e1689-175">To fill the parameters of a constructor marked with the `ImportingConstructor` attribute, all of those parameters are automatically declared as imports.</span></span> <span data-ttu-id="e1689-176">Toto je pohodlný způsob, jak deklarovat importy, které se používají při inicializaci části.</span><span class="sxs-lookup"><span data-stu-id="e1689-176">This is a convenient way to declare imports that are used during part initialization.</span></span> <span data-ttu-id="e1689-177">Následující třída používá `ImportingConstructor` pro deklaraci importu.</span><span class="sxs-lookup"><span data-stu-id="e1689-177">The following class uses `ImportingConstructor` to declare an import.</span></span>

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

<span data-ttu-id="e1689-178">Ve výchozím nastavení `ImportingConstructor` používá atribut pro všechny importy parametrů odvozené typy kontraktů a názvy kontraktů.</span><span class="sxs-lookup"><span data-stu-id="e1689-178">By default, the `ImportingConstructor` attribute uses inferred contract types and contract names for all of the parameter imports.</span></span> <span data-ttu-id="e1689-179">To lze přepsat tím, že upravení parametry s `Import` atributy, které mohou následně definovat typ kontraktu a název kontraktu explicitně.</span><span class="sxs-lookup"><span data-stu-id="e1689-179">It is possible to override this by decorating the parameters with `Import` attributes, which can then define the contract type and contract name explicitly.</span></span> <span data-ttu-id="e1689-180">Následující kód demonstruje konstruktor, který používá tuto syntaxi k importu odvozené třídy namísto nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="e1689-180">The following code demonstrates a constructor that uses this syntax to import a derived class instead of a parent class.</span></span>

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

<span data-ttu-id="e1689-181">Konkrétně byste měli být opatrní s parametry kolekce.</span><span class="sxs-lookup"><span data-stu-id="e1689-181">In particular, you should be careful with collection parameters.</span></span> <span data-ttu-id="e1689-182">Například pokud zadáte `ImportingConstructor` v konstruktoru s parametrem typu `IEnumerable<int>` , import bude odpovídat jedinému exportu typu `IEnumerable<int>` namísto sady EXPORTS typu `int` .</span><span class="sxs-lookup"><span data-stu-id="e1689-182">For example, if you specify `ImportingConstructor` on a constructor with a parameter of type `IEnumerable<int>`, the import will match a single export of type `IEnumerable<int>`, instead of a set of exports of type `int`.</span></span> <span data-ttu-id="e1689-183">Chcete-li porovnat sadu exportů typu `int` , je nutné zadat parametr s `ImportMany` atributem.</span><span class="sxs-lookup"><span data-stu-id="e1689-183">To match a set of exports of type `int`, you have to decorate the parameter with the `ImportMany` attribute.</span></span>

<span data-ttu-id="e1689-184">Parametry deklarované jako import pomocí `ImportingConstructor` atributu jsou také označeny jako *požadované importy*.</span><span class="sxs-lookup"><span data-stu-id="e1689-184">Parameters declared as imports by the `ImportingConstructor` attribute are also marked as *prerequisite imports*.</span></span> <span data-ttu-id="e1689-185">MEF normálně umožňuje exportům a importům vytvořit *cyklus*.</span><span class="sxs-lookup"><span data-stu-id="e1689-185">MEF normally allows exports and imports to form a *cycle*.</span></span> <span data-ttu-id="e1689-186">Například cyklus je místo, kde objekt A importuje objekt B, který zase importuje objekt A. Za běžných okolností není cyklem problém a kontejner kompozice vytvoří oba objekty normálně.</span><span class="sxs-lookup"><span data-stu-id="e1689-186">For example, a cycle is where object A imports object B, which in turn imports object A. Under ordinary circumstances, a cycle is not a problem, and the composition container constructs both objects normally.</span></span>

<span data-ttu-id="e1689-187">Pokud je importovaná hodnota požadována konstruktorem součásti, tento objekt se nemůže zúčastnit cyklu.</span><span class="sxs-lookup"><span data-stu-id="e1689-187">When an imported value is required by the constructor of a part, that object cannot participate in a cycle.</span></span> <span data-ttu-id="e1689-188">Pokud objekt A vyžaduje, aby byl objekt B vytvořen před samotným sestavením a objekt B importuje objekt A, pak se cyklus nebude moci vyřešit a dojde k chybě kompozice.</span><span class="sxs-lookup"><span data-stu-id="e1689-188">If object A requires that object B be constructed before it can be constructed itself, and object B imports object A, then the cycle will be unable to resolve and a composition error will occur.</span></span> <span data-ttu-id="e1689-189">Importy deklarované v parametrech konstruktoru jsou tedy požadavky na importy, které musí být vyplněny před jakýmkoli exportem z objektu, který je vyžaduje, aby je bylo možné použít.</span><span class="sxs-lookup"><span data-stu-id="e1689-189">Imports declared on constructor parameters are therefore prerequisite imports, which must all be filled before any of the exports from the object that requires them can be used.</span></span>

### <a name="optional-imports"></a><span data-ttu-id="e1689-190">Volitelné importy</span><span class="sxs-lookup"><span data-stu-id="e1689-190">Optional Imports</span></span>

<span data-ttu-id="e1689-191">`Import`Atribut určuje požadavek, který má součást fungovat.</span><span class="sxs-lookup"><span data-stu-id="e1689-191">The `Import` attribute specifies a requirement for the part to function.</span></span> <span data-ttu-id="e1689-192">Pokud import nelze splnit, složení této součásti selže a součást nebude k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e1689-192">If an import cannot be fulfilled, the composition of that part will fail and the part will not be available.</span></span>

<span data-ttu-id="e1689-193">Pomocí vlastnosti můžete určit, že import je *nepovinný* `AllowDefault` .</span><span class="sxs-lookup"><span data-stu-id="e1689-193">You can specify that an import is *optional* by using the `AllowDefault` property.</span></span> <span data-ttu-id="e1689-194">V tomto případě bude kompozice úspěšná i v případě, že import neodpovídá žádnému dostupnému exportu a vlastnost import bude nastavena na výchozí hodnotu pro svůj typ vlastnosti ( `null` pro vlastnosti objektu, `false` pro logické hodnoty nebo nula pro číselné vlastnosti.) Následující třída používá volitelný import.</span><span class="sxs-lookup"><span data-stu-id="e1689-194">In this case, the composition will succeed even if the import does not match any available exports, and the importing property will be set to the default for its property type (`null` for object properties, `false` for Booleans, or zero for numeric properties.) The following class uses an optional import.</span></span>

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

### <a name="importing-multiple-objects"></a><span data-ttu-id="e1689-195">Importování více objektů</span><span class="sxs-lookup"><span data-stu-id="e1689-195">Importing Multiple Objects</span></span>

<span data-ttu-id="e1689-196">`Import`Atribut bude úspěšně sestaven pouze v případě, že odpovídá jednomu a pouze jednomu exportu.</span><span class="sxs-lookup"><span data-stu-id="e1689-196">The `Import` attribute will only be successfully composed when it matches one and only one export.</span></span> <span data-ttu-id="e1689-197">Jiné případy vytvoří chybu složení.</span><span class="sxs-lookup"><span data-stu-id="e1689-197">Other cases will produce a composition error.</span></span> <span data-ttu-id="e1689-198">Chcete-li importovat více než jeden export, který odpovídá stejné smlouvě, použijte `ImportMany` atribut.</span><span class="sxs-lookup"><span data-stu-id="e1689-198">To import more than one export that matches the same contract, use the `ImportMany` attribute.</span></span> <span data-ttu-id="e1689-199">Importy označené pomocí tohoto atributu jsou vždycky volitelné.</span><span class="sxs-lookup"><span data-stu-id="e1689-199">Imports marked with this attribute are always optional.</span></span> <span data-ttu-id="e1689-200">Například složení nebude úspěšné, pokud nejsou k dispozici žádné vyhovující exporty.</span><span class="sxs-lookup"><span data-stu-id="e1689-200">For example, composition will not fail if no matching exports are present.</span></span> <span data-ttu-id="e1689-201">Následující třída importuje libovolný počet exportů typu `IMyAddin` .</span><span class="sxs-lookup"><span data-stu-id="e1689-201">The following class imports any number of exports of type `IMyAddin`.</span></span>

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

<span data-ttu-id="e1689-202">K importovanému poli je možné přistupovat pomocí běžných `IEnumerable<T>` syntaxí a metod.</span><span class="sxs-lookup"><span data-stu-id="e1689-202">The imported array can be accessed by using ordinary `IEnumerable<T>` syntax and methods.</span></span> <span data-ttu-id="e1689-203">Místo toho je také možné použít běžné pole ( `IMyAddin[]` ).</span><span class="sxs-lookup"><span data-stu-id="e1689-203">It is also possible to use an ordinary array (`IMyAddin[]`) instead.</span></span>

<span data-ttu-id="e1689-204">Tento model může být velmi důležitý při použití v kombinaci s `Lazy<T>` syntaxí.</span><span class="sxs-lookup"><span data-stu-id="e1689-204">This pattern can be very important when you use it in combination with the `Lazy<T>` syntax.</span></span> <span data-ttu-id="e1689-205">Například pomocí `ImportMany` , `IEnumerable<T>` a `Lazy<T>` můžete importovat nepřímé odkazy na libovolný počet objektů a vytvořit pouze instance těch, které jsou nezbytné.</span><span class="sxs-lookup"><span data-stu-id="e1689-205">For example, by using `ImportMany`, `IEnumerable<T>`, and `Lazy<T>`, you can import indirect references to any number of objects and only instantiate the ones that become necessary.</span></span> <span data-ttu-id="e1689-206">Následující třída zobrazuje tento model.</span><span class="sxs-lookup"><span data-stu-id="e1689-206">The following class shows this pattern.</span></span>

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

## <a name="avoiding-discovery"></a><span data-ttu-id="e1689-207">Zamezení zjišťování</span><span class="sxs-lookup"><span data-stu-id="e1689-207">Avoiding Discovery</span></span>

<span data-ttu-id="e1689-208">V některých případech můžete chtít zabránit tomu, aby se součást zjistila jako součást katalogu.</span><span class="sxs-lookup"><span data-stu-id="e1689-208">In some cases, you may want to prevent a part from being discovered as part of a catalog.</span></span> <span data-ttu-id="e1689-209">Například část může být základní třídou, která má být zděděna z, ale není použita.</span><span class="sxs-lookup"><span data-stu-id="e1689-209">For example, the part may be a base class intended to be inherited from, but not used.</span></span> <span data-ttu-id="e1689-210">To můžete provést dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="e1689-210">There are two ways to accomplish this.</span></span> <span data-ttu-id="e1689-211">Nejprve můžete použít `abstract` klíčové slovo pro třídu součásti.</span><span class="sxs-lookup"><span data-stu-id="e1689-211">First, you can use the `abstract` keyword on the part class.</span></span> <span data-ttu-id="e1689-212">Abstraktní třídy nikdy neposkytují export, i když mohou poskytnout děděné exporty třídám, které jsou z nich odvozeny.</span><span class="sxs-lookup"><span data-stu-id="e1689-212">Abstract classes never provide exports, although they can provide inherited exports to classes that derive from them.</span></span>

<span data-ttu-id="e1689-213">Pokud třídu nelze nastavit jako abstraktní, lze ji roztřídit pomocí `PartNotDiscoverable` atributu.</span><span class="sxs-lookup"><span data-stu-id="e1689-213">If the class cannot be made abstract, you can decorate it with the `PartNotDiscoverable` attribute.</span></span> <span data-ttu-id="e1689-214">Část upravená pomocí tohoto atributu nebude zahrnuta do žádných katalogů.</span><span class="sxs-lookup"><span data-stu-id="e1689-214">A part decorated with this attribute will not be included in any catalogs.</span></span> <span data-ttu-id="e1689-215">Následující příklad znázorňuje tyto vzory.</span><span class="sxs-lookup"><span data-stu-id="e1689-215">The following example demonstrates these patterns.</span></span> <span data-ttu-id="e1689-216">`DataOne`budou zjištěny katalogem.</span><span class="sxs-lookup"><span data-stu-id="e1689-216">`DataOne` will be discovered by the catalog.</span></span> <span data-ttu-id="e1689-217">Vzhledem `DataTwo` k tomu, že je abstraktní, nebude zjištěno.</span><span class="sxs-lookup"><span data-stu-id="e1689-217">Since `DataTwo` is abstract, it will not be discovered.</span></span> <span data-ttu-id="e1689-218">Vzhledem `DataThree` k `PartNotDiscoverable` tomu, že se atribut použil, nebude zjištěn.</span><span class="sxs-lookup"><span data-stu-id="e1689-218">Since `DataThree` used the `PartNotDiscoverable` attribute, it will not be discovered.</span></span>

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

## <a name="metadata-and-metadata-views"></a><span data-ttu-id="e1689-219">Metadata a zobrazení metadat</span><span class="sxs-lookup"><span data-stu-id="e1689-219">Metadata and Metadata Views</span></span>

<span data-ttu-id="e1689-220">Exporty můžou poskytnout další informace o samotných údajích, které se nazývají *metadata*.</span><span class="sxs-lookup"><span data-stu-id="e1689-220">Exports can provide additional information about themselves known as *metadata*.</span></span> <span data-ttu-id="e1689-221">Metadata lze použít k předávání vlastností exportovaného objektu do importované části.</span><span class="sxs-lookup"><span data-stu-id="e1689-221">Metadata can be used to convey properties of the exported object to the importing part.</span></span> <span data-ttu-id="e1689-222">Importovaná část může pomocí těchto dat rozhodnout, které exporty se mají použít, nebo shromažďovat informace o exportu bez nutnosti jeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="e1689-222">The importing part can use this data to decide which exports to use, or to gather information about an export without having to construct it.</span></span> <span data-ttu-id="e1689-223">Z tohoto důvodu musí být import opožděný, aby používal metadata.</span><span class="sxs-lookup"><span data-stu-id="e1689-223">For this reason, an import must be lazy to use metadata.</span></span>

<span data-ttu-id="e1689-224">Chcete-li použít metadata, obvykle deklarujete rozhraní známé jako *zobrazení metadat*, které deklaruje, jaká metadata budou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e1689-224">To use metadata, you typically declare an interface known as a *metadata view*, which declares what metadata will be available.</span></span> <span data-ttu-id="e1689-225">Rozhraní zobrazení metadat musí mít pouze vlastnosti, přičemž tyto vlastnosti musí mít `get` přistupující objekty.</span><span class="sxs-lookup"><span data-stu-id="e1689-225">The metadata view interface must have only properties, and those properties must have `get` accessors.</span></span> <span data-ttu-id="e1689-226">Následující rozhraní je příkladem zobrazení metadat.</span><span class="sxs-lookup"><span data-stu-id="e1689-226">The following interface is an example metadata view.</span></span>

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

<span data-ttu-id="e1689-227">Je také možné použít obecnou kolekci, `IDictionary<string, object>` jako zobrazení metadat, ale to propadá na výhody kontroly typu a je třeba se jim vyhnout.</span><span class="sxs-lookup"><span data-stu-id="e1689-227">It is also possible to use a generic collection, `IDictionary<string, object>`, as a metadata view, but this forfeits the benefits of type checking and should be avoided.</span></span>

<span data-ttu-id="e1689-228">Obvykle jsou požadovány všechny vlastnosti pojmenované v zobrazení metadat a jakékoli exporty, které je neposkytují, nebudou považovány za shodu.</span><span class="sxs-lookup"><span data-stu-id="e1689-228">Ordinarily, all of the properties named in the metadata view are required, and any exports that do not provide them will not be considered a match.</span></span> <span data-ttu-id="e1689-229">`DefaultValue`Atribut určuje, že vlastnost je volitelná.</span><span class="sxs-lookup"><span data-stu-id="e1689-229">The `DefaultValue` attribute specifies that a property is optional.</span></span> <span data-ttu-id="e1689-230">Pokud vlastnost není zahrnutá, přiřadí se výchozí hodnota zadaná jako parametr `DefaultValue` .</span><span class="sxs-lookup"><span data-stu-id="e1689-230">If the property is not included, it will be assigned the default value specified as a parameter of `DefaultValue`.</span></span> <span data-ttu-id="e1689-231">Níže jsou dvě různé třídy dekorované metadaty.</span><span class="sxs-lookup"><span data-stu-id="e1689-231">The following are two different classes decorated with metadata.</span></span> <span data-ttu-id="e1689-232">Obě tyto třídy by odpovídaly předchozímu zobrazení metadat.</span><span class="sxs-lookup"><span data-stu-id="e1689-232">Both of these classes would match the previous metadata view.</span></span>

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

<span data-ttu-id="e1689-233">Metadata jsou vyjádřena po `Export` atributu pomocí `ExportMetadata` atributu.</span><span class="sxs-lookup"><span data-stu-id="e1689-233">Metadata is expressed after the `Export` attribute by using the `ExportMetadata` attribute.</span></span> <span data-ttu-id="e1689-234">Každá část metadat se skládá z dvojice název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="e1689-234">Each piece of metadata is composed of a name/value pair.</span></span> <span data-ttu-id="e1689-235">Název v metadatech se musí shodovat s názvem příslušné vlastnosti v zobrazení metadat a hodnota bude přiřazena této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e1689-235">The name portion of the metadata must match the name of the appropriate property in the metadata view, and the value will be assigned to that property.</span></span>

<span data-ttu-id="e1689-236">Je to dovozce, který určuje, jaké zobrazení metadat se bude používat.</span><span class="sxs-lookup"><span data-stu-id="e1689-236">It is the importer that specifies what metadata view, if any, will be in use.</span></span> <span data-ttu-id="e1689-237">Import s metadaty je deklarován jako opožděné importu s rozhraním metadat jako druhým parametrem typu `Lazy<T,T>` .</span><span class="sxs-lookup"><span data-stu-id="e1689-237">An import with metadata is declared as a lazy import, with the metadata interface as the second type parameter to `Lazy<T,T>`.</span></span> <span data-ttu-id="e1689-238">Následující třída importuje předchozí část s metadaty.</span><span class="sxs-lookup"><span data-stu-id="e1689-238">The following class imports the previous part with metadata.</span></span>

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

<span data-ttu-id="e1689-239">V mnoha případech budete chtít kombinovat metadata s `ImportMany` atributem, aby bylo možné analyzovat v dostupných importech a vybírat a vytvářet instance pouze jeden, nebo filtrovat kolekci tak, aby odpovídala určité podmínce.</span><span class="sxs-lookup"><span data-stu-id="e1689-239">In many cases, you will want to combine metadata with the `ImportMany` attribute, in order to parse through the available imports and choose and instantiate only one, or filter a collection to match a certain condition.</span></span> <span data-ttu-id="e1689-240">Následující třída vytváří instance pouze `IPlugin` objekty, které mají `Name` hodnotu "protokolovací".</span><span class="sxs-lookup"><span data-stu-id="e1689-240">The following class instantiates only `IPlugin` objects that have the `Name` value "Logger".</span></span>

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

## <a name="import-and-export-inheritance"></a><span data-ttu-id="e1689-241">Dědičnost importu a exportu</span><span class="sxs-lookup"><span data-stu-id="e1689-241">Import and Export Inheritance</span></span>

<span data-ttu-id="e1689-242">Pokud třída dědí z části, může se také stát, že se tato třída stane součástí.</span><span class="sxs-lookup"><span data-stu-id="e1689-242">If a class inherits from a part, that class may also become a part.</span></span> <span data-ttu-id="e1689-243">Importy jsou vždy děděny podtřídami.</span><span class="sxs-lookup"><span data-stu-id="e1689-243">Imports are always inherited by subclasses.</span></span> <span data-ttu-id="e1689-244">Proto bude podtřídou součásti vždy součástí, se stejnými importy jako její nadřazená třída.</span><span class="sxs-lookup"><span data-stu-id="e1689-244">Therefore, a subclass of a part will always be a part, with the same imports as its parent class.</span></span>

<span data-ttu-id="e1689-245">Exporty deklarované pomocí `Export` atributu nejsou děděny podtřídami.</span><span class="sxs-lookup"><span data-stu-id="e1689-245">Exports declared by using the `Export` attribute are not inherited by subclasses.</span></span> <span data-ttu-id="e1689-246">Součást však může exportovat sebe sama pomocí `InheritedExport` atributu.</span><span class="sxs-lookup"><span data-stu-id="e1689-246">However, a part can export itself by using the `InheritedExport` attribute.</span></span> <span data-ttu-id="e1689-247">Podtřídy této části zdědí a poskytnou stejný export, včetně názvu kontraktu a typu smlouvy.</span><span class="sxs-lookup"><span data-stu-id="e1689-247">Subclasses of the part will inherit and provide the same export, including contract name and contract type.</span></span> <span data-ttu-id="e1689-248">Na rozdíl od `Export` atributu `InheritedExport` lze použít pouze na úrovni třídy, nikoli na úrovni člena.</span><span class="sxs-lookup"><span data-stu-id="e1689-248">Unlike an `Export` attribute, `InheritedExport` can be applied only at the class level, and not at the member level.</span></span> <span data-ttu-id="e1689-249">Proto nelze export na úrovni členů dědění nikdy dědit.</span><span class="sxs-lookup"><span data-stu-id="e1689-249">Therefore, member-level exports can never be inherited.</span></span>

<span data-ttu-id="e1689-250">Následující čtyři třídy demonstrují principy dědičnosti importu a exportu.</span><span class="sxs-lookup"><span data-stu-id="e1689-250">The following four classes demonstrate the principles of import and export inheritance.</span></span> <span data-ttu-id="e1689-251">`NumTwo`dědí z `NumOne` , takže `NumTwo` se naimportuje `IMyData` .</span><span class="sxs-lookup"><span data-stu-id="e1689-251">`NumTwo` inherits from `NumOne`, so `NumTwo` will import `IMyData`.</span></span> <span data-ttu-id="e1689-252">Běžné exporty nejsou děděny, takže `NumTwo` nebudou exportovány žádné výsledky.</span><span class="sxs-lookup"><span data-stu-id="e1689-252">Ordinary exports are not inherited, so `NumTwo` will not export anything.</span></span> <span data-ttu-id="e1689-253">`NumFour`dědí z `NumThree` .</span><span class="sxs-lookup"><span data-stu-id="e1689-253">`NumFour` inherits from `NumThree`.</span></span> <span data-ttu-id="e1689-254">Vzhledem `NumThree` k tomu, že používá `InheritedExport` , `NumFour` má jeden export s typem kontraktu `NumThree` .</span><span class="sxs-lookup"><span data-stu-id="e1689-254">Because `NumThree` used `InheritedExport`, `NumFour` has one export with contract type `NumThree`.</span></span> <span data-ttu-id="e1689-255">Exporty na úrovni členů nejsou nikdy zděděné, takže `IMyData` se neexportují.</span><span class="sxs-lookup"><span data-stu-id="e1689-255">Member-level exports are never inherited, so `IMyData` is not exported.</span></span>

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

<span data-ttu-id="e1689-256">Pokud jsou k atributu přidružená metadata `InheritedExport` , budou tato metadata také děděna.</span><span class="sxs-lookup"><span data-stu-id="e1689-256">If there is metadata associated with an `InheritedExport` attribute, that metadata will also be inherited.</span></span> <span data-ttu-id="e1689-257">(Další informace najdete v části předchozí metadata a zobrazení metadat). Zděděná metadata nelze upravovat podtřídou.</span><span class="sxs-lookup"><span data-stu-id="e1689-257">(For more information, see the earlier "Metadata and Metadata Views" section.) Inherited metadata cannot be modified by the subclass.</span></span> <span data-ttu-id="e1689-258">Pokud však znovu deklarujete `InheritedExport` atribut se stejným názvem kontraktu a typem kontraktu, ale s novými metadaty, podtřída může nahradit zděděná metadata novými metadaty.</span><span class="sxs-lookup"><span data-stu-id="e1689-258">However, by re-declaring the `InheritedExport` attribute with the same contract name and contract type, but with new metadata, the subclass can replace the inherited metadata with new metadata.</span></span> <span data-ttu-id="e1689-259">Následující třída demonstruje tento princip.</span><span class="sxs-lookup"><span data-stu-id="e1689-259">The following class demonstrates this principle.</span></span> <span data-ttu-id="e1689-260">`MegaLogger`Část dědí z `Logger` a obsahuje `InheritedExport` atribut.</span><span class="sxs-lookup"><span data-stu-id="e1689-260">The `MegaLogger` part inherits from `Logger` and includes the `InheritedExport` attribute.</span></span> <span data-ttu-id="e1689-261">Vzhledem `MegaLogger` k tomu, že znovu deklaruje nová metadata s názvem status, nedědí název a metadata verze z `Logger` .</span><span class="sxs-lookup"><span data-stu-id="e1689-261">Since `MegaLogger` re-declares new metadata named Status, it does not inherit the Name and Version metadata from `Logger`.</span></span>

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

<span data-ttu-id="e1689-262">Při opětovné deklaraci `InheritedExport` atributu pro přepsání metadat se ujistěte, že typy kontraktu jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="e1689-262">When re-declaring the `InheritedExport` attribute to override metadata, make sure that the contract types are the same.</span></span> <span data-ttu-id="e1689-263">(V předchozím příkladu je to `IPlugin` Typ kontraktu.) Pokud se liší, místo přepsání, druhý atribut vytvoří druhý nezávislý export z části.</span><span class="sxs-lookup"><span data-stu-id="e1689-263">(In the previous example, `IPlugin` is the contract type.) If they differ, instead of overriding, the second attribute will create a second, independent export from the part.</span></span> <span data-ttu-id="e1689-264">Obecně to znamená, že budete muset explicitně zadat typ kontraktu při přepsání `InheritedExport` atributu, jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e1689-264">Generally, this means that you will have to explicitly specify the contract type when you override an `InheritedExport` attribute, as shown in the previous example.</span></span>

<span data-ttu-id="e1689-265">Vzhledem k tomu, že rozhraní nemohou být vytvořena přímo, nesmí být obecně upravena pomocí `Export` `Import` atributů nebo.</span><span class="sxs-lookup"><span data-stu-id="e1689-265">Since interfaces cannot be instantiated directly, they generally cannot be decorated with `Export` or `Import` attributes.</span></span> <span data-ttu-id="e1689-266">Rozhraní lze však dekorovat pomocí `InheritedExport` atributu na úrovni rozhraní a export spolu s jakýmikoli přidruženými metadaty bude děděn všemi implementací tříd.</span><span class="sxs-lookup"><span data-stu-id="e1689-266">However, an interface can be decorated with an `InheritedExport` attribute at the interface level, and that export along with any associated metadata will be inherited by any implementing classes.</span></span> <span data-ttu-id="e1689-267">Samotné rozhraní nebude ale k dispozici jako součást.</span><span class="sxs-lookup"><span data-stu-id="e1689-267">The interface itself will not be available as a part, however.</span></span>

<a name="custom_export_attributes"></a>

## <a name="custom-export-attributes"></a><span data-ttu-id="e1689-268">Vlastní atributy exportu</span><span class="sxs-lookup"><span data-stu-id="e1689-268">Custom Export Attributes</span></span>

<span data-ttu-id="e1689-269">Základní atributy exportu `Export` a `InheritedExport` lze rozšířit tak, aby zahrnovaly metadata jako vlastnosti atributu.</span><span class="sxs-lookup"><span data-stu-id="e1689-269">The basic export attributes, `Export` and `InheritedExport`, can be extended to include metadata as attribute properties.</span></span> <span data-ttu-id="e1689-270">Tato technika je užitečná pro použití podobných metadat na mnoho částí nebo pro vytvoření stromu dědičnosti atributů metadat.</span><span class="sxs-lookup"><span data-stu-id="e1689-270">This technique is useful for applying similar metadata to many parts, or creating an inheritance tree of metadata attributes.</span></span>

<span data-ttu-id="e1689-271">Vlastní atribut může určovat typ kontraktu, název kontraktu nebo jiná metadata.</span><span class="sxs-lookup"><span data-stu-id="e1689-271">A custom attribute can specify the contract type, the contract name, or any other metadata.</span></span> <span data-ttu-id="e1689-272">Aby bylo možné definovat vlastní atribut, musí být třída, která dědí z `ExportAttribute` (nebo `InheritedExportAttribute` ), upravena `MetadataAttribute` atributem.</span><span class="sxs-lookup"><span data-stu-id="e1689-272">In order to define a custom attribute, a class inheriting from `ExportAttribute` (or `InheritedExportAttribute`) must be decorated with the `MetadataAttribute` attribute.</span></span> <span data-ttu-id="e1689-273">Následující třída definuje vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="e1689-273">The following class defines a custom attribute.</span></span>

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

<span data-ttu-id="e1689-274">Tato třída definuje vlastní atribut s názvem `MyAttribute` typu kontrakt `IMyAddin` a některá metadata s názvem `MyMetadata` .</span><span class="sxs-lookup"><span data-stu-id="e1689-274">This class defines a custom attribute named `MyAttribute` with contract type `IMyAddin` and some metadata named `MyMetadata`.</span></span> <span data-ttu-id="e1689-275">Všechny vlastnosti ve třídě označené `MetadataAttribute` atributem se považují za metadata definovaná ve vlastním atributu.</span><span class="sxs-lookup"><span data-stu-id="e1689-275">All properties in a class marked with the `MetadataAttribute` attribute are considered to be metadata defined in the custom attribute.</span></span> <span data-ttu-id="e1689-276">Následující dvě deklarace jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="e1689-276">The following two declarations are equivalent.</span></span>

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

<span data-ttu-id="e1689-277">V první deklaraci je typ kontraktu a metadata explicitně definovány.</span><span class="sxs-lookup"><span data-stu-id="e1689-277">In the first declaration, the contract type and metadata are explicitly defined.</span></span> <span data-ttu-id="e1689-278">Ve druhé deklaraci je typ kontraktu a metadata implicitní v přizpůsobeném atributu.</span><span class="sxs-lookup"><span data-stu-id="e1689-278">In the second declaration, the contract type and metadata are implicit in the customized attribute.</span></span> <span data-ttu-id="e1689-279">Zejména v případech, kdy je třeba použít velké množství identických metadat na mnoho částí (například informace o autorech nebo autorských právech), může použití vlastního atributu ušetřit spoustu času a duplikace.</span><span class="sxs-lookup"><span data-stu-id="e1689-279">Particularly in cases where a large amount of identical metadata must be applied to many parts (for example, author or copyright information), using a custom attribute can save a lot of time and duplication.</span></span> <span data-ttu-id="e1689-280">Kromě toho lze vytvořit stromy dědičnosti vlastních atributů, aby bylo možné variace.</span><span class="sxs-lookup"><span data-stu-id="e1689-280">Further, inheritance trees of custom attributes can be created to allow for variations.</span></span>

<span data-ttu-id="e1689-281">Chcete-li vytvořit volitelná metadata ve vlastním atributu, můžete použít `DefaultValue` atribut.</span><span class="sxs-lookup"><span data-stu-id="e1689-281">To create optional metadata in a custom attribute, you can use the `DefaultValue` attribute.</span></span> <span data-ttu-id="e1689-282">Pokud je tento atribut použit pro vlastnost ve vlastní třídě atributu, určuje, že dekorovaná vlastnost je volitelná a není nutné ji dodávat Exportér.</span><span class="sxs-lookup"><span data-stu-id="e1689-282">When this attribute is applied to a property in a custom attribute class, it specifies that the decorated property is optional and does not have to be supplied by an exporter.</span></span> <span data-ttu-id="e1689-283">Pokud hodnota vlastnosti není dodána, přiřadí se výchozí hodnota pro svůj typ vlastnosti (obvykle, `null` `false` nebo 0).</span><span class="sxs-lookup"><span data-stu-id="e1689-283">If a value for the property is not supplied, it will be assigned the default value for its property type (usually `null`, `false`, or 0.)</span></span>

<a name="creation_policies"></a>

## <a name="creation-policies"></a><span data-ttu-id="e1689-284">Zásady vytváření</span><span class="sxs-lookup"><span data-stu-id="e1689-284">Creation Policies</span></span>

<span data-ttu-id="e1689-285">Pokud část určuje import a složení, kontejner kompozice se pokusí najít vyhovující export.</span><span class="sxs-lookup"><span data-stu-id="e1689-285">When a part specifies an import and composition is performed, the composition container attempts to find a matching export.</span></span> <span data-ttu-id="e1689-286">Pokud odpovídá import s exportem úspěšně, je importovaný člen nastaven na instanci exportovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="e1689-286">If it matches the import with an export successfully, the importing member is set to an instance of the exported object.</span></span> <span data-ttu-id="e1689-287">Umístění, ze kterého pochází tato instance, je ovládáno pomocí *zásad vytváření*exportovaných částí.</span><span class="sxs-lookup"><span data-stu-id="e1689-287">Where this instance comes from is controlled by the exporting part's *creation policy*.</span></span>

<span data-ttu-id="e1689-288">Dvě možné zásady vytváření jsou *sdílené* a *nesdílené*.</span><span class="sxs-lookup"><span data-stu-id="e1689-288">The two possible creation policies are *shared* and *non-shared*.</span></span> <span data-ttu-id="e1689-289">Součást s zásadou vytváření Shared bude sdílená mezi každým importem v kontejneru pro součást s touto smlouvou.</span><span class="sxs-lookup"><span data-stu-id="e1689-289">A part with a creation policy of shared will be shared between every import in the container for a part with that contract.</span></span> <span data-ttu-id="e1689-290">Pokud modul kompozice najde shodu a musí nastavit vlastnost import, vytvoří instanci nové kopie součásti pouze v případě, že ještě neexistuje. v opačném případě poskytne existující kopii.</span><span class="sxs-lookup"><span data-stu-id="e1689-290">When the composition engine finds a match and has to set an importing property, it will instantiate a new copy of the part only if one does not already exist; otherwise, it will supply the existing copy.</span></span> <span data-ttu-id="e1689-291">To znamená, že mnoho objektů může mít odkazy na stejnou část.</span><span class="sxs-lookup"><span data-stu-id="e1689-291">This means that many objects may have references to the same part.</span></span> <span data-ttu-id="e1689-292">Tyto části by neměly spoléhat na vnitřní stav, který může být změněn z mnoha míst.</span><span class="sxs-lookup"><span data-stu-id="e1689-292">Such parts should not rely on internal state that might be changed from many places.</span></span> <span data-ttu-id="e1689-293">Tyto zásady jsou vhodné pro statické části, součásti, které poskytují služby, a součásti, které využívají spoustu paměti nebo jiných prostředků.</span><span class="sxs-lookup"><span data-stu-id="e1689-293">This policy is appropriate for static parts, parts that provide services, and parts that consume a lot of memory or other resources.</span></span>

<span data-ttu-id="e1689-294">Součást se zásadami vytváření nesdílených se vytvoří pokaždé, když se najde odpovídající import pro jeden z jeho exportů.</span><span class="sxs-lookup"><span data-stu-id="e1689-294">A part with the creation policy of non-shared will be created every time a matching import for one of its exports is found.</span></span> <span data-ttu-id="e1689-295">Pro každý import v kontejneru, který odpovídá jedné z exportovaných smluv, bude vytvořena instance nového kopírování.</span><span class="sxs-lookup"><span data-stu-id="e1689-295">A new copy will therefore be instantiated for every import in the container that matches one of the part's exported contracts.</span></span> <span data-ttu-id="e1689-296">Vnitřní stav těchto kopií nebude sdílen.</span><span class="sxs-lookup"><span data-stu-id="e1689-296">The internal state of these copies will not be shared.</span></span> <span data-ttu-id="e1689-297">Tyto zásady jsou vhodné pro části, kde každý import vyžaduje vlastní vnitřní stav.</span><span class="sxs-lookup"><span data-stu-id="e1689-297">This policy is appropriate for parts where each import requires its own internal state.</span></span>

<span data-ttu-id="e1689-298">Import i export může určovat zásadu vytváření součásti, a to z hodnot `Shared` , `NonShared` nebo `Any` .</span><span class="sxs-lookup"><span data-stu-id="e1689-298">Both the import and the export can specify the creation policy of a part, from among the values `Shared`, `NonShared`, or `Any`.</span></span> <span data-ttu-id="e1689-299">Výchozí hodnota je `Any` pro import i export.</span><span class="sxs-lookup"><span data-stu-id="e1689-299">The default is `Any` for both imports and exports.</span></span> <span data-ttu-id="e1689-300">Export, který určuje `Shared` nebo `NonShared` bude odpovídat pouze importu, který určuje stejné nebo které určuje `Any` .</span><span class="sxs-lookup"><span data-stu-id="e1689-300">An export that specifies `Shared` or `NonShared` will only match an import that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="e1689-301">Podobně import, který určuje `Shared` nebo, `NonShared` bude odpovídat pouze exportu, který určuje stejné nebo, které určuje `Any` .</span><span class="sxs-lookup"><span data-stu-id="e1689-301">Similarly, an import that specifies `Shared` or `NonShared` will only match an export that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="e1689-302">Importy a exporty s nekompatibilními zásadami vytváření nejsou považovány za shodu, a to stejným způsobem jako při importu a exportu, jejichž název kontraktu nebo typ kontraktu se neshodují.</span><span class="sxs-lookup"><span data-stu-id="e1689-302">Imports and exports with incompatible creation policies are not considered a match, in the same way as an import and export whose contract name or contract type are not a match.</span></span> <span data-ttu-id="e1689-303">Pokud pro import i export určíte `Any` nebo nezadáte zásadu vytváření a výchozí hodnotu pro `Any` , zásady vytváření se budou sdílet jako výchozí.</span><span class="sxs-lookup"><span data-stu-id="e1689-303">If both import and export specify `Any`, or do not specify a creation policy and default to `Any`, the creation policy will default to shared.</span></span>

<span data-ttu-id="e1689-304">Následující příklad ukazuje import i export, které určují zásady vytváření.</span><span class="sxs-lookup"><span data-stu-id="e1689-304">The following example shows both imports and exports specifying creation policies.</span></span> <span data-ttu-id="e1689-305">`PartOne`neurčuje zásadu vytváření, takže výchozí hodnota je `Any` .</span><span class="sxs-lookup"><span data-stu-id="e1689-305">`PartOne` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="e1689-306">`PartTwo`neurčuje zásadu vytváření, takže výchozí hodnota je `Any` .</span><span class="sxs-lookup"><span data-stu-id="e1689-306">`PartTwo` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="e1689-307">Vzhledem k tomu, že se naimportují i exportují výchozí hodnoty do `Any` , `PartOne` budou sdíleny.</span><span class="sxs-lookup"><span data-stu-id="e1689-307">Since both import and export default to `Any`, `PartOne` will be shared.</span></span> <span data-ttu-id="e1689-308">`PartThree`Určuje `Shared` zásadu vytváření, takže `PartTwo` a `PartThree` bude sdílet stejnou kopii `PartOne` .</span><span class="sxs-lookup"><span data-stu-id="e1689-308">`PartThree` specifies a `Shared` creation policy, so `PartTwo` and `PartThree` will share the same copy of `PartOne`.</span></span> <span data-ttu-id="e1689-309">`PartFour`Určuje `NonShared` zásadu vytváření, takže `PartFour` se v nástroji nesdílí `PartFive` .</span><span class="sxs-lookup"><span data-stu-id="e1689-309">`PartFour` specifies a `NonShared` creation policy, so `PartFour` will be non-shared in `PartFive`.</span></span> <span data-ttu-id="e1689-310">`PartSix`Určuje `NonShared` zásadu vytváření.</span><span class="sxs-lookup"><span data-stu-id="e1689-310">`PartSix` specifies a `NonShared` creation policy.</span></span> <span data-ttu-id="e1689-311">`PartFive`a `PartSix` každý z nich získá samostatné kopie `PartFour` .</span><span class="sxs-lookup"><span data-stu-id="e1689-311">`PartFive` and `PartSix` will each receive separate copies of `PartFour`.</span></span> <span data-ttu-id="e1689-312">`PartSeven`Určuje `Shared` zásadu vytváření.</span><span class="sxs-lookup"><span data-stu-id="e1689-312">`PartSeven` specifies a `Shared` creation policy.</span></span> <span data-ttu-id="e1689-313">Vzhledem k tomu, že není exportována `PartFour` se zásadami vytváření `Shared` , `PartSeven` Import neshoduje s žádným a nebude vyplněn.</span><span class="sxs-lookup"><span data-stu-id="e1689-313">Because there is no exported `PartFour` with a creation policy of `Shared`, the `PartSeven` import does not match anything and will not be filled.</span></span>

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

## <a name="life-cycle-and-disposing"></a><span data-ttu-id="e1689-314">Životní cyklus a odstraňování</span><span class="sxs-lookup"><span data-stu-id="e1689-314">Life Cycle and Disposing</span></span>

<span data-ttu-id="e1689-315">Vzhledem k tomu, že části jsou hostovány v kontejneru složení, jejich životní cyklus může být složitější než běžné objekty.</span><span class="sxs-lookup"><span data-stu-id="e1689-315">Because parts are hosted in the composition container, their life cycle can be more complex than ordinary objects.</span></span> <span data-ttu-id="e1689-316">Části můžou implementovat dvě důležitá rozhraní související s životním cyklem: `IDisposable` a `IPartImportsSatisfiedNotification` .</span><span class="sxs-lookup"><span data-stu-id="e1689-316">Parts can implement two important life cycle-related interfaces: `IDisposable` and `IPartImportsSatisfiedNotification`.</span></span>

<span data-ttu-id="e1689-317">Součásti, které vyžadují, aby se prováděla práce při vypnutí nebo které potřebují uvolnit prostředky, by měly implementovat `IDisposable` běžné pro .NET Framework objekty.</span><span class="sxs-lookup"><span data-stu-id="e1689-317">Parts that require work to be performed at shut down or that need to release resources should implement `IDisposable`, as usual for .NET Framework objects.</span></span> <span data-ttu-id="e1689-318">Vzhledem k tomu, že kontejner vytváří a udržuje odkazy na části, pouze kontejner, který vlastní část, by měl volat `Dispose` metodu.</span><span class="sxs-lookup"><span data-stu-id="e1689-318">However, since the container creates and maintains references to parts, only the container that owns a part should call the `Dispose` method on it.</span></span> <span data-ttu-id="e1689-319">Samotný kontejner implementuje `IDisposable` a jako součást jeho vyčištění v rámci `Dispose` něj bude volat `Dispose` všechny části, které vlastní.</span><span class="sxs-lookup"><span data-stu-id="e1689-319">The container itself implements `IDisposable`, and as portion of its cleanup in `Dispose` it will call `Dispose` on all the parts that it owns.</span></span> <span data-ttu-id="e1689-320">Z tohoto důvodu byste měli kontejner kompozice vždy uvolnit, pokud je a jakékoliv součásti, které vlastní, již nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="e1689-320">For this reason, you should always dispose the composition container when it and any parts it owns are no longer needed.</span></span>

<span data-ttu-id="e1689-321">V případě dlouhodobých kontejnerů kompozice se může stát, že spotřeba paměti podle částí se zásadou vytváření nesdíleného není sdílená.</span><span class="sxs-lookup"><span data-stu-id="e1689-321">For long-lived composition containers, memory consumption by parts with a creation policy of non-shared can become a problem.</span></span> <span data-ttu-id="e1689-322">Tyto nesdílené části je možné vytvořit víckrát, takže nebudou uvolněny, dokud nedojde k uvolnění samotného kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e1689-322">These non-shared parts can be created multiple times and will not be disposed until the container itself is disposed.</span></span> <span data-ttu-id="e1689-323">Chcete-li se tomuto postupu zabývat, kontejner poskytuje `ReleaseExport` metodu.</span><span class="sxs-lookup"><span data-stu-id="e1689-323">To deal with this, the container provides the `ReleaseExport` method.</span></span> <span data-ttu-id="e1689-324">Volání této metody u nesdíleného exportu odebere tento export z kontejneru složení a odstraní jej.</span><span class="sxs-lookup"><span data-stu-id="e1689-324">Calling this method on a non-shared export removes that export from the composition container and disposes it.</span></span> <span data-ttu-id="e1689-325">Části, které se používají jenom odebraným exportem, a tak i na stromové struktuře, se taky odeberou a odstraňují.</span><span class="sxs-lookup"><span data-stu-id="e1689-325">Parts that are used only by the removed export, and so on down the tree, are also removed and disposed.</span></span> <span data-ttu-id="e1689-326">Tímto způsobem lze prostředky uvolnit bez likvidace kontejneru kompozice.</span><span class="sxs-lookup"><span data-stu-id="e1689-326">In this way, resources can be reclaimed without disposing the composition container itself.</span></span>

<span data-ttu-id="e1689-327">`IPartImportsSatisfiedNotification`obsahuje jednu metodu s názvem `OnImportsSatisfied` .</span><span class="sxs-lookup"><span data-stu-id="e1689-327">`IPartImportsSatisfiedNotification` contains one method named `OnImportsSatisfied`.</span></span> <span data-ttu-id="e1689-328">Tato metoda je volána kontejnerem kompozice na všech částech, které implementují rozhraní po dokončení složení, a importy části jsou připravené k použití.</span><span class="sxs-lookup"><span data-stu-id="e1689-328">This method is called by the composition container on any parts that implement the interface when composition has been completed and the part's imports are ready for use.</span></span> <span data-ttu-id="e1689-329">Části jsou vytvořeny modulem složení, aby bylo možné vyplnit importy dalších částí.</span><span class="sxs-lookup"><span data-stu-id="e1689-329">Parts are created by the composition engine to fill the imports of other parts.</span></span> <span data-ttu-id="e1689-330">Před nastavením importu části nelze provést žádnou inicializaci, která spoléhá na nebo zpracovává importované hodnoty v konstruktoru součásti, pokud tyto hodnoty nebyly zadány jako požadavky pomocí `ImportingConstructor` atributu.</span><span class="sxs-lookup"><span data-stu-id="e1689-330">Before the imports of a part have been set, you cannot perform any initialization that relies on or manipulates imported values in the part constructor unless those values have been specified as prerequisites by using the `ImportingConstructor` attribute.</span></span> <span data-ttu-id="e1689-331">To je obvykle upřednostňovaná metoda, ale v některých případech nemusí být injektáže konstruktoru k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e1689-331">This is normally the preferred method, but in some cases, constructor injection may not be available.</span></span> <span data-ttu-id="e1689-332">V těchto případech může být inicializace provedena v `OnImportsSatisfied` a část by měla implementovat `IPartImportsSatisfiedNotification` .</span><span class="sxs-lookup"><span data-stu-id="e1689-332">In those cases, initialization can be performed in `OnImportsSatisfied`, and the part should implement `IPartImportsSatisfiedNotification`.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1689-333">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1689-333">See also</span></span>

- [<span data-ttu-id="e1689-334">Video pro kanál 9: otevření aplikací pomocí Managed Extensibility Framework</span><span class="sxs-lookup"><span data-stu-id="e1689-334">Channel 9 Video: Open Up Your Applications with the Managed Extensibility Framework</span></span>](https://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)
- [<span data-ttu-id="e1689-335">Video pro kanál 9: Managed Extensibility Framework (MEF) 2,0</span><span class="sxs-lookup"><span data-stu-id="e1689-335">Channel 9 Video: Managed Extensibility Framework (MEF) 2.0</span></span>](https://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)

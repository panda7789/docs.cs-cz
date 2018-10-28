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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7dab1474454f8169d8d0d80413c6fb95677fb4bf
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49453388"
---
# <a name="attributed-programming-model-overview-mef"></a><span data-ttu-id="73025-102">Přehled modelu programování s přidělenými atributy (MEF)</span><span class="sxs-lookup"><span data-stu-id="73025-102">Attributed Programming Model Overview (MEF)</span></span>
<span data-ttu-id="73025-103">V Managed Extensibility Framework (MEF), *programovací model* je konkrétní metoda definuje sadu rámcové objekty, na kterých pracuje MEF.</span><span class="sxs-lookup"><span data-stu-id="73025-103">In the Managed Extensibility Framework (MEF), a *programming model* is a particular method of defining the set of conceptual objects on which MEF operates.</span></span> <span data-ttu-id="73025-104">Mezi tyto rámcové objekty patří částí, importy a exporty.</span><span class="sxs-lookup"><span data-stu-id="73025-104">These conceptual objects include parts, imports, and exports.</span></span> <span data-ttu-id="73025-105">MEF používá tyto objekty, ale není zadán, jak by měly být zastoupeny.</span><span class="sxs-lookup"><span data-stu-id="73025-105">MEF uses these objects, but does not specify how they should be represented.</span></span> <span data-ttu-id="73025-106">Proto jsou celou řadu programovacích modelů je to možné, včetně přizpůsobit programovacích modelů.</span><span class="sxs-lookup"><span data-stu-id="73025-106">Therefore, a wide variety of programming models are possible, including customized programming models.</span></span>  
  
 <span data-ttu-id="73025-107">Výchozí hodnota je programovací model používaný v MEF *model programování s atributy*.</span><span class="sxs-lookup"><span data-stu-id="73025-107">The default programming model used in MEF is the *attributed programming model*.</span></span> <span data-ttu-id="73025-108">V části s atributy programovací model jsou definovány importy, exporty a dalších objektů s atributy, které uspořádání běžné třídy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="73025-108">In the attributed programming model parts, imports, exports, and other objects are defined with attributes that decorate ordinary .NET Framework classes.</span></span> <span data-ttu-id="73025-109">Toto téma vysvětluje, jak používat atributy poskytované modelu programování s atributy k vytvoření aplikace MEF.</span><span class="sxs-lookup"><span data-stu-id="73025-109">This topic explains how to use the attributes provided by the attributed programming model to create a MEF application.</span></span>  
  
<a name="import_and_export_basics"></a>   
## <a name="import-and-export-basics"></a><span data-ttu-id="73025-110">Import a Export základy</span><span class="sxs-lookup"><span data-stu-id="73025-110">Import and Export Basics</span></span>  
 <span data-ttu-id="73025-111">*Exportovat* je hodnota, která obsahuje část s ostatními částmi v kontejneru, a *importovat* je požadavek, který vyjadřuje část do kontejneru, vyplní se z dostupných exportů.</span><span class="sxs-lookup"><span data-stu-id="73025-111">An *export* is a value that a part provides to other parts in the container, and an *import* is a requirement that a part expresses to the container, to be filled from the available exports.</span></span> <span data-ttu-id="73025-112">V modelu programování s atributy importy a exporty jsou deklarovány přidáním upravení třídy nebo členy s `Import` a `Export` atributy.</span><span class="sxs-lookup"><span data-stu-id="73025-112">In the attributed programming model, imports and exports are declared by decorating classes or members with the `Import` and `Export` attributes.</span></span> <span data-ttu-id="73025-113">`Export` Atribut můžete uspořádání třída, pole, vlastnost nebo metoda, zatímco `Import` atribut můžete uspořádání parametr pole, vlastnost nebo konstruktor.</span><span class="sxs-lookup"><span data-stu-id="73025-113">The `Export` attribute can decorate a class, field, property, or method, while the `Import` attribute can decorate a field, property, or constructor parameter.</span></span>  
  
 <span data-ttu-id="73025-114">Pro import lze porovnat s export, import a export musí mít stejné *kontraktu*.</span><span class="sxs-lookup"><span data-stu-id="73025-114">In order for an import to be matched with an export, the import and export must have the same *contract*.</span></span> <span data-ttu-id="73025-115">Smlouva se skládá z řetězce, volá se *název kontraktu*a typ objektu importovaná nebo exportovaná, volá se *typ kontraktu*.</span><span class="sxs-lookup"><span data-stu-id="73025-115">The contract consists of a string, called the *contract name*, and the type of the exported or imported object, called the *contract type*.</span></span> <span data-ttu-id="73025-116">Pouze v případě, že název kontraktu i smlouva zadejte shoda se export považuje za splnit konkrétní importu.</span><span class="sxs-lookup"><span data-stu-id="73025-116">Only if both the contract name and contract type match is an export considered to fulfill a particular import.</span></span>  
  
 <span data-ttu-id="73025-117">Jeden nebo oba parametry smlouvy může být implicitní nebo explicitní.</span><span class="sxs-lookup"><span data-stu-id="73025-117">Either or both of the contract parameters can be implicit or explicit.</span></span> <span data-ttu-id="73025-118">Následující kód ukazuje třídu, která deklaruje základní import.</span><span class="sxs-lookup"><span data-stu-id="73025-118">The following code shows a class that declares a basic import.</span></span>  
  
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
  
 <span data-ttu-id="73025-119">V tomto importu `Import` atribut nemá typ kontraktu ani parametr název kontraktu připojen.</span><span class="sxs-lookup"><span data-stu-id="73025-119">In this import, the `Import` attribute has neither a contract type nor a contract name parameter attached.</span></span> <span data-ttu-id="73025-120">Proto i se odvodit z upravené vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="73025-120">Therefore, both will be inferred from the decorated property.</span></span> <span data-ttu-id="73025-121">V takovém případě budou mít typ kontraktu `IMyAddin`, a název smlouvy bude jedinečný řetězec vytvořený z typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="73025-121">In this case, the contract type will be `IMyAddin`, and the contract name will be a unique string created from the contract type.</span></span> <span data-ttu-id="73025-122">(Jinými slovy, název smlouvy budou odpovídat jenom exporty, jejichž názvy jsou také odvodit z typu `IMyAddin`.)</span><span class="sxs-lookup"><span data-stu-id="73025-122">(In other words, the contract name will match only exports whose names are also inferred from the type `IMyAddin`.)</span></span>  
  
 <span data-ttu-id="73025-123">Následuje ukázka export, který odpovídá předchozí import.</span><span class="sxs-lookup"><span data-stu-id="73025-123">The following shows an export that matches the previous import.</span></span>  
  
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
  
 <span data-ttu-id="73025-124">V tomto export, zajišťujeme typ kontraktu je `IMyAddin` vzhledem k tomu, že je zadán jako parametr `Export` atribut.</span><span class="sxs-lookup"><span data-stu-id="73025-124">In this export, the contract type is `IMyAddin` because it is specified as a parameter of the `Export` attribute.</span></span> <span data-ttu-id="73025-125">Exportovaný typ musí být buď stejná jako typ kontraktu, odvozen od typu kontraktu nebo implementovat typ kontraktu, pokud se jedná o rozhraní.</span><span class="sxs-lookup"><span data-stu-id="73025-125">The exported type must be either the same as the contract type, derive from the contract type, or implement the contract type if it is an interface.</span></span> <span data-ttu-id="73025-126">V tomto exportu, skutečný typ `MyLogger` implementuje rozhraní `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="73025-126">In this export, the actual type `MyLogger` implements the interface `IMyAddin`.</span></span> <span data-ttu-id="73025-127">Název smlouvy je odvozen z typu smlouvy, což znamená, že tento export bude odpovídat předchozí import.</span><span class="sxs-lookup"><span data-stu-id="73025-127">The contract name is inferred from the contract type, which means that this export will match the previous import.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73025-128">Exportuje a importuje by měl obvykle deklarované v veřejné třídy nebo členy.</span><span class="sxs-lookup"><span data-stu-id="73025-128">Exports and imports should usually be declared on public classes or members.</span></span> <span data-ttu-id="73025-129">Další deklarace jsou podporované, ale export nebo import privátní, chráněné nebo interní člen přeruší modelu izolace pro část a není proto doporučuje.</span><span class="sxs-lookup"><span data-stu-id="73025-129">Other declarations are supported, but exporting or importing a private, protected, or internal member breaks the isolation model for the part and is therefore not recommended.</span></span>  
  
 <span data-ttu-id="73025-130">Typ kontraktu musí odpovídat přesně pro export a import být považovány za shodné.</span><span class="sxs-lookup"><span data-stu-id="73025-130">The contract type must match exactly for the export and import to be considered a match.</span></span> <span data-ttu-id="73025-131">Vezměte v úvahu následující exportu.</span><span class="sxs-lookup"><span data-stu-id="73025-131">Consider the following export.</span></span>  
  
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
  
 <span data-ttu-id="73025-132">V tomto export, zajišťujeme typ kontraktu je `MyLogger` místo `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="73025-132">In this export, the contract type is `MyLogger` instead of `IMyAddin`.</span></span> <span data-ttu-id="73025-133">I když `MyLogger` implementuje `IMyAddin`a proto může být přetypovat na `IMyAddin` objektu, export nebudou odpovídat předchozí importovat, protože typy kontraktů nejsou stejné.</span><span class="sxs-lookup"><span data-stu-id="73025-133">Even though `MyLogger` implements `IMyAddin`, and therefore could be cast to an `IMyAddin` object, this export will not match the previous import because the contract types are not the same.</span></span>  
  
 <span data-ttu-id="73025-134">Obecně platí není potřeba zadávat název kontraktu a většina kontrakty by měl definovány jako typ kontraktu a metadata.</span><span class="sxs-lookup"><span data-stu-id="73025-134">In general, it is not necessary to specify the contract name, and most contracts should be defined in terms of the contract type and metadata.</span></span> <span data-ttu-id="73025-135">Za určitých okolností, je potřeba zadat název kontraktu přímo.</span><span class="sxs-lookup"><span data-stu-id="73025-135">However, under certain circumstances, it is important to specify the contract name directly.</span></span> <span data-ttu-id="73025-136">Nejběžnější případ je, když třída exportuje několik hodnot, které sdílejí společný typ, jako je například primitiv.</span><span class="sxs-lookup"><span data-stu-id="73025-136">The most common case is when a class exports several values that share a common type, such as primitives.</span></span> <span data-ttu-id="73025-137">Název smlouvy lze zadat jako první parametr `Import` nebo `Export` atribut.</span><span class="sxs-lookup"><span data-stu-id="73025-137">The contract name can be specified as the first parameter of the `Import` or `Export` attribute.</span></span> <span data-ttu-id="73025-138">Následující kód ukazuje, import a export s názvem zadaného smlouvy `MajorRevision`.</span><span class="sxs-lookup"><span data-stu-id="73025-138">The following code shows an import and an export with a specified contract name of `MajorRevision`.</span></span>  
  
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
  
 <span data-ttu-id="73025-139">Pokud není zadán typ kontraktu, bude stále odvozen z typu importu nebo exportu.</span><span class="sxs-lookup"><span data-stu-id="73025-139">If the contract type is not specified, it will still be inferred from the type of the import or export.</span></span> <span data-ttu-id="73025-140">Ale i v případě, že je explicitně zadán název kontraktu, typ kontraktu musí také odpovídat přesně pro import a export být považovány za shodné.</span><span class="sxs-lookup"><span data-stu-id="73025-140">However, even if the contract name is specified explicitly, the contract type must also match exactly for the import and export to be considered a match.</span></span> <span data-ttu-id="73025-141">Například pokud `MajorRevision` bylo pole řetězce, typy kontraktů odvozený shodě a export shodě import, přes který má stejný název kontraktu.</span><span class="sxs-lookup"><span data-stu-id="73025-141">For example, if the `MajorRevision` field was a string, the inferred contract types would not match and the export would not match the import, despite having the same contract name.</span></span>  
  
### <a name="importing-and-exporting-a-method"></a><span data-ttu-id="73025-142">Import a export metodu</span><span class="sxs-lookup"><span data-stu-id="73025-142">Importing and Exporting a Method</span></span>  
 <span data-ttu-id="73025-143">`Export` Atribut může také uspořádání metody, stejně jako třída, vlastnost nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="73025-143">The `Export` attribute can also decorate a method, in the same way as a class, property, or function.</span></span> <span data-ttu-id="73025-144">Metoda exporty musíte zadat název kontraktu a typ kontraktu jako typ nelze odvodit.</span><span class="sxs-lookup"><span data-stu-id="73025-144">Method exports must specify a contract type or contract name, as the type cannot be inferred.</span></span> <span data-ttu-id="73025-145">Zadaný typ může být vlastního delegáta nebo obecného typu, například `Func`.</span><span class="sxs-lookup"><span data-stu-id="73025-145">The specified type can be either a custom delegate or a generic type, such as `Func`.</span></span> <span data-ttu-id="73025-146">Následující třídy exportuje metodu s názvem `DoSomething`.</span><span class="sxs-lookup"><span data-stu-id="73025-146">The following class exports a method named `DoSomething`.</span></span>  
  
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
  
 <span data-ttu-id="73025-147">V této třídě `DoSomething` metoda přebírá jediný `int` parametr a vrátí `string`.</span><span class="sxs-lookup"><span data-stu-id="73025-147">In this class, the `DoSomething` method takes a single `int` parameter and returns a `string`.</span></span> <span data-ttu-id="73025-148">Tak, aby odpovídaly export, import část musí deklarovat příslušného člena.</span><span class="sxs-lookup"><span data-stu-id="73025-148">To match this export, the importing part must declare an appropriate member.</span></span> <span data-ttu-id="73025-149">Následující třídy importy `DoSomething` metody.</span><span class="sxs-lookup"><span data-stu-id="73025-149">The following class imports the `DoSomething` method.</span></span>  
  
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
  
 <span data-ttu-id="73025-150">Další informace o tom, jak používat nástroje `Func<T, T>` objektu, najdete v článku <xref:System.Func%602>.</span><span class="sxs-lookup"><span data-stu-id="73025-150">For more information about how to use of the `Func<T, T>` object, see <xref:System.Func%602>.</span></span>  
  
<a name="types_of_imports"></a>   
## <a name="types-of-imports"></a><span data-ttu-id="73025-151">Typy importy</span><span class="sxs-lookup"><span data-stu-id="73025-151">Types of Imports</span></span>  
 <span data-ttu-id="73025-152">Několik import MEF podporují typy, včetně dynamických, opožděné požadované a volitelné.</span><span class="sxs-lookup"><span data-stu-id="73025-152">MEF support several import types, including dynamic, lazy, prerequisite, and optional.</span></span>  
  
### <a name="dynamic-imports"></a><span data-ttu-id="73025-153">Dynamické importy</span><span class="sxs-lookup"><span data-stu-id="73025-153">Dynamic Imports</span></span>  
 <span data-ttu-id="73025-154">V některých případech může být vhodné importu třídy tak, aby odpovídaly exporty libovolného typu, které mají název konkrétní kontraktu.</span><span class="sxs-lookup"><span data-stu-id="73025-154">In some cases, the importing class may want to match exports of any type that have a particular contract name.</span></span> <span data-ttu-id="73025-155">V tomto scénáři můžete deklarovat třídy *dynamického importu*.</span><span class="sxs-lookup"><span data-stu-id="73025-155">In this scenario, the class can declare a *dynamic import*.</span></span> <span data-ttu-id="73025-156">Následující import odpovídá jakékoli export s názvem kontraktu "TheString".</span><span class="sxs-lookup"><span data-stu-id="73025-156">The following import matches any export with contract name "TheString".</span></span>  
  
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
  
 <span data-ttu-id="73025-157">Kdy typu kontraktu je odvozen z `dynamic` – klíčové slovo, budou se shodovat s libovolný typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="73025-157">When the contract type is inferred from the `dynamic` keyword, it will match any contract type.</span></span> <span data-ttu-id="73025-158">V takovém případě by měl importu **vždy** zadejte název smlouvy tak, aby odpovídaly na.</span><span class="sxs-lookup"><span data-stu-id="73025-158">In this case, an import should **always** specify a contract name to match on.</span></span> <span data-ttu-id="73025-159">(Pokud není zadán žádný název smlouvy, import bude považovat za tak, aby odpovídaly žádné exporty.) Obě tyto exporty odpovídá předchozí import.</span><span class="sxs-lookup"><span data-stu-id="73025-159">(If no contract name is specified, the import will be considered to match no exports.) Both of the following exports would match the previous import.</span></span>  
  
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
  
 <span data-ttu-id="73025-160">Samozřejmě musí být připravené třídu importu se objekt libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="73025-160">Obviously, the importing class must be prepared to deal with an object of arbitrary type.</span></span>  
  
### <a name="lazy-imports"></a><span data-ttu-id="73025-161">Opožděné importy</span><span class="sxs-lookup"><span data-stu-id="73025-161">Lazy Imports</span></span>  
 <span data-ttu-id="73025-162">V některých případech importu třídy vyžadují nepřímý odkaz na importovaný objekt tak, aby se okamžitě vytvořena instance objektu.</span><span class="sxs-lookup"><span data-stu-id="73025-162">In some cases, the importing class may require an indirect reference to the imported object, so that the object is not instantiated immediately.</span></span> <span data-ttu-id="73025-163">V tomto scénáři můžete deklarovat třídy *opožděné import* pomocí typu kontraktu `Lazy<T>`.</span><span class="sxs-lookup"><span data-stu-id="73025-163">In this scenario, the class can declare a *lazy import* by using a contract type of `Lazy<T>`.</span></span> <span data-ttu-id="73025-164">Následující vlastnost importu deklaruje opožděné importu.</span><span class="sxs-lookup"><span data-stu-id="73025-164">The following importing property declares a lazy import.</span></span>  
  
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
  
 <span data-ttu-id="73025-165">Z hlediska složení modulu, typu kontraktu `Lazy<T>` se považuje za stejný jako typ kontraktu `T`.</span><span class="sxs-lookup"><span data-stu-id="73025-165">From the point of view of the composition engine, a contract type of `Lazy<T>` is considered identical to contract type of `T`.</span></span> <span data-ttu-id="73025-166">Proto se předchozí import odpovídají následujícího exportu.</span><span class="sxs-lookup"><span data-stu-id="73025-166">Therefore, the previous import would match the following export.</span></span>  
  
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
  
 <span data-ttu-id="73025-167">Název kontraktu a typ smlouvy lze zadat v `Import` atributu opožděné import, jak je popsáno výše v části "Základní importy a exporty".</span><span class="sxs-lookup"><span data-stu-id="73025-167">The contract name and contract type can be specified in the `Import` attribute for a lazy import, as described earlier in the "Basic Imports and Exports" section.</span></span>  
  
### <a name="prerequisite-imports"></a><span data-ttu-id="73025-168">Požadované importy</span><span class="sxs-lookup"><span data-stu-id="73025-168">Prerequisite Imports</span></span>  
 <span data-ttu-id="73025-169">Kompoziční modul v reakci na žádost o přímé nebo nutnosti tak, aby vyplnil odpovídající import obvykle vytváří exportované částmi MEF.</span><span class="sxs-lookup"><span data-stu-id="73025-169">Exported MEF parts are typically created by the composition engine, in response to a direct request or the need to fill a matched import.</span></span> <span data-ttu-id="73025-170">Ve výchozím nastavení se při vytvoření části Kompoziční modul používá konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="73025-170">By default, when creating a part, the composition engine uses the parameter-less constructor.</span></span> <span data-ttu-id="73025-171">Chcete-li modul, použijte jiný konstruktor, můžete označit ji `ImportingConstructor` atribut.</span><span class="sxs-lookup"><span data-stu-id="73025-171">To make the engine use a different constructor, you can mark it with the `ImportingConstructor` attribute.</span></span>  
  
 <span data-ttu-id="73025-172">Každá část může mít pouze jeden konstruktor pro použití u Kompoziční modul.</span><span class="sxs-lookup"><span data-stu-id="73025-172">Each part may have only one constructor for use by the composition engine.</span></span> <span data-ttu-id="73025-173">Žádný výchozí konstruktor a ne `ImportingConstructor` atribut nebo poskytuje více než jeden `ImportingConstructor` atribut, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="73025-173">Providing no default constructor and no `ImportingConstructor` attribute, or providing more than one `ImportingConstructor` attribute, will produce an error.</span></span>  
  
 <span data-ttu-id="73025-174">Vyplnit parametry konstruktoru označeného klíčovým `ImportingConstructor` atribut, všechny tyto parametry jsou automaticky deklarován jako importy.</span><span class="sxs-lookup"><span data-stu-id="73025-174">To fill the parameters of a constructor marked with the `ImportingConstructor` attribute, all of those parameters are automatically declared as imports.</span></span> <span data-ttu-id="73025-175">Je to pohodlný způsob, jak deklarovat importy, které se používají při inicializaci části.</span><span class="sxs-lookup"><span data-stu-id="73025-175">This is a convenient way to declare imports that are used during part initialization.</span></span> <span data-ttu-id="73025-176">Následující třídy používá `ImportingConstructor` pro deklaraci importu.</span><span class="sxs-lookup"><span data-stu-id="73025-176">The following class uses `ImportingConstructor` to declare an import.</span></span>  
  
```vb  
Public Class MyClass1  
  
    Private _theAddin As IMyAddin  
  
    'Default constructor will NOT be used  
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
  
    //Default constructor will NOT be  
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
  
 <span data-ttu-id="73025-177">Ve výchozím nastavení `ImportingConstructor` atribut odvodit používá typy kontraktů a kontraktů pro všechny importy parametru.</span><span class="sxs-lookup"><span data-stu-id="73025-177">By default, the `ImportingConstructor` attribute uses inferred contract types and contract names for all of the parameter imports.</span></span> <span data-ttu-id="73025-178">Je možné přepsat pomocí upravení parametrů pomocí `Import` atributy, které můžete pak určit typ kontraktu a název kontraktu explicitně.</span><span class="sxs-lookup"><span data-stu-id="73025-178">It is possible to override this by decorating the parameters with `Import` attributes, which can then define the contract type and contract name explicitly.</span></span> <span data-ttu-id="73025-179">Následující kód ukazuje konstruktor, který používá tuto syntaxi pro import odvozenou třídu namísto nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="73025-179">The following code demonstrates a constructor that uses this syntax to import a derived class instead of a parent class.</span></span>  
  
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
  
 <span data-ttu-id="73025-180">Konkrétně byste měli být opatrní při práci s parametry kolekce.</span><span class="sxs-lookup"><span data-stu-id="73025-180">In particular, you should be careful with collection parameters.</span></span> <span data-ttu-id="73025-181">Pokud zadáte například `ImportingConstructor` na konstruktor s parametrem typu `IEnumerable<int>`, import bude odpovídat jeden export typu `IEnumerable<int>`, místo sady exporty typu `int`.</span><span class="sxs-lookup"><span data-stu-id="73025-181">For example, if you specify `ImportingConstructor` on a constructor with a parameter of type `IEnumerable<int>`, the import will match a single export of type `IEnumerable<int>`, instead of a set of exports of type `int`.</span></span> <span data-ttu-id="73025-182">Tak, aby odpovídaly sadu exporty typu `int`, máte k vyplnění parametr s `ImportMany` atribut.</span><span class="sxs-lookup"><span data-stu-id="73025-182">To match a set of exports of type `int`, you have to decorate the parameter with the `ImportMany` attribute.</span></span>  
  
 <span data-ttu-id="73025-183">Parametry deklarovány jako importy podle `ImportingConstructor` atribut jsou také označené jako *předpoklad importuje*.</span><span class="sxs-lookup"><span data-stu-id="73025-183">Parameters declared as imports by the `ImportingConstructor` attribute are also marked as *prerequisite imports*.</span></span> <span data-ttu-id="73025-184">Obvykle umožňuje exporty MEF a naimportuje do formuláře *cyklu*.</span><span class="sxs-lookup"><span data-stu-id="73025-184">MEF normally allows exports and imports to form a *cycle*.</span></span> <span data-ttu-id="73025-185">Cyklus je třeba where-object objekt A importů B, který zase importuje objekt A. Za běžných okolností cyklus nepředstavuje žádný problém a kontejner kompozic obvykle vytvoří oba objekty.</span><span class="sxs-lookup"><span data-stu-id="73025-185">For example, a cycle is where object A imports object B, which in turn imports object A. Under ordinary circumstances, a cycle is not a problem, and the composition container constructs both objects normally.</span></span>  
  
 <span data-ttu-id="73025-186">Když importované hodnoty je potřeba pomocí konstruktoru část, tento objekt se nemůže podílet na cyklus.</span><span class="sxs-lookup"><span data-stu-id="73025-186">When an imported value is required by the constructor of a part, that object cannot participate in a cycle.</span></span> <span data-ttu-id="73025-187">Pokud objekt A vyžaduje zkonstruovat tento objekt B předtím, než lze sestavit samostatně a objekt B importuje objektu A pak cyklu nejde přeložit a dojde k chybě složení.</span><span class="sxs-lookup"><span data-stu-id="73025-187">If object A requires that object B be constructed before it can be constructed itself, and object B imports object A, then the cycle will be unable to resolve and a composition error will occur.</span></span> <span data-ttu-id="73025-188">Importy deklarované parametry konstruktoru jsou proto požadované importy, které musí všechny být vyplněno před žádné exporty z objektu, který vyžaduje, je použít.</span><span class="sxs-lookup"><span data-stu-id="73025-188">Imports declared on constructor parameters are therefore prerequisite imports, which must all be filled before any of the exports from the object that requires them can be used.</span></span>  
  
### <a name="optional-imports"></a><span data-ttu-id="73025-189">Volitelné importy</span><span class="sxs-lookup"><span data-stu-id="73025-189">Optional Imports</span></span>  
 <span data-ttu-id="73025-190">`Import` Atribut určuje požadavek pro část funkce.</span><span class="sxs-lookup"><span data-stu-id="73025-190">The `Import` attribute specifies a requirement for the part to function.</span></span> <span data-ttu-id="73025-191">Pokud nelze splnit, import, složení této části se nezdaří a části nebude k dispozici.</span><span class="sxs-lookup"><span data-stu-id="73025-191">If an import cannot be fulfilled, the composition of that part will fail and the part will not be available.</span></span>  
  
 <span data-ttu-id="73025-192">Můžete určit, že je import *volitelné* pomocí `AllowDefault` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="73025-192">You can specify that an import is *optional* by using the `AllowDefault` property.</span></span> <span data-ttu-id="73025-193">V takovém případě bude složení úspěšné i v případě, že import neodpovídá žádné dostupné exporty a importu vlastnost bude nastavena na výchozí hodnoty pro jeho vlastnost typ (`null` na vlastnosti objektu `false` pro logické hodnoty nebo nula pro číselné Vlastnosti.) Následující třídy používá volitelný import.</span><span class="sxs-lookup"><span data-stu-id="73025-193">In this case, the composition will succeed even if the import does not match any available exports, and the importing property will be set to the default for its property type (`null` for object properties, `false` for Booleans, or zero for numeric properties.) The following class uses an optional import.</span></span>  
  
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
  
    //If no matching export is avaliable,  
    //thePlugin will be set to null.  
}  
```  
  
### <a name="importing-multiple-objects"></a><span data-ttu-id="73025-194">Import více objektů</span><span class="sxs-lookup"><span data-stu-id="73025-194">Importing Multiple Objects</span></span>  
 <span data-ttu-id="73025-195">`Import` Atribut bude být úspěšně tvořen pouze případě, že odpovídá pouze jeden export.</span><span class="sxs-lookup"><span data-stu-id="73025-195">The `Import` attribute will only be successfully composed when it matches one and only one export.</span></span> <span data-ttu-id="73025-196">Jindy ohlásí chybu kompozice.</span><span class="sxs-lookup"><span data-stu-id="73025-196">Other cases will produce a composition error.</span></span> <span data-ttu-id="73025-197">Chcete-li importovat víc než jeden export odpovídající stejný kontrakt, použijte `ImportMany` atribut.</span><span class="sxs-lookup"><span data-stu-id="73025-197">To import more than one export that matches the same contract, use the `ImportMany` attribute.</span></span> <span data-ttu-id="73025-198">Importy označené pomocí tohoto atributu jsou vždy volitelné.</span><span class="sxs-lookup"><span data-stu-id="73025-198">Imports marked with this attribute are always optional.</span></span> <span data-ttu-id="73025-199">Například složení nebude nezdaří, pokud jsou k dispozici žádné exporty odpovídající.</span><span class="sxs-lookup"><span data-stu-id="73025-199">For example, composition will not fail if no matching exports are present.</span></span> <span data-ttu-id="73025-200">Následující třídy importuje libovolný počet exportů typu `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="73025-200">The following class imports any number of exports of type `IMyAddin`.</span></span>  
  
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
  
 <span data-ttu-id="73025-201">Importované pole je přístupná pomocí běžných `IEnumerable<T>` syntaxi a metody.</span><span class="sxs-lookup"><span data-stu-id="73025-201">The imported array can be accessed by using ordinary `IEnumerable<T>` syntax and methods.</span></span> <span data-ttu-id="73025-202">Je také možné použít běžné pole (`IMyAddin[]`) místo toho.</span><span class="sxs-lookup"><span data-stu-id="73025-202">It is also possible to use an ordinary array (`IMyAddin[]`) instead.</span></span>  
  
 <span data-ttu-id="73025-203">Tento model může být velmi důležité, když ho použijete v kombinaci s `Lazy<T>` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="73025-203">This pattern can be very important when you use it in combination with the `Lazy<T>` syntax.</span></span> <span data-ttu-id="73025-204">Například s použitím `ImportMany`, `IEnumerable<T>`, a `Lazy<T>`, můžete importovat nepřímé odkazy na libovolný počet objektů a pouze ty, které budou potřebné instance.</span><span class="sxs-lookup"><span data-stu-id="73025-204">For example, by using `ImportMany`, `IEnumerable<T>`, and `Lazy<T>`, you can import indirect references to any number of objects and only instantiate the ones that become necessary.</span></span> <span data-ttu-id="73025-205">Následující třídy ukazuje tento model.</span><span class="sxs-lookup"><span data-stu-id="73025-205">The following class shows this pattern.</span></span>  
  
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
## <a name="avoiding-discovery"></a><span data-ttu-id="73025-206">Obcházení zjišťování</span><span class="sxs-lookup"><span data-stu-id="73025-206">Avoiding Discovery</span></span>  
 <span data-ttu-id="73025-207">V některých případech můžete chtít zabránit zjišťování katalogu v rámci části.</span><span class="sxs-lookup"><span data-stu-id="73025-207">In some cases, you may want to prevent a part from being discovered as part of a catalog.</span></span> <span data-ttu-id="73025-208">Části může být například základní třídu, má Zdědit z však nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="73025-208">For example, the part may be a base class intended to be inherited from, but not used.</span></span> <span data-ttu-id="73025-209">Existují dva způsoby, jak toho dosáhnout.</span><span class="sxs-lookup"><span data-stu-id="73025-209">There are two ways to accomplish this.</span></span> <span data-ttu-id="73025-210">Nejprve, můžete použít `abstract` – klíčové slovo ve třídě část.</span><span class="sxs-lookup"><span data-stu-id="73025-210">First, you can use the `abstract` keyword on the part class.</span></span> <span data-ttu-id="73025-211">Abstraktní třídy nikdy poskytují exporty, i když mohou poskytovat zděděné exporty do třídy, které jsou odvozeny z nich.</span><span class="sxs-lookup"><span data-stu-id="73025-211">Abstract classes never provide exports, although they can provide inherited exports to classes that derive from them.</span></span>  
  
 <span data-ttu-id="73025-212">Pokud nelze nastavit jako abstraktní třídu, můžete ji uspořádání `PartNotDiscoverable` atribut.</span><span class="sxs-lookup"><span data-stu-id="73025-212">If the class cannot be made abstract, you can decorate it with the `PartNotDiscoverable` attribute.</span></span> <span data-ttu-id="73025-213">Část upravené pomocí tohoto atributu se nezahrnuly do jakékoli katalogů.</span><span class="sxs-lookup"><span data-stu-id="73025-213">A part decorated with this attribute will not be included in any catalogs.</span></span> <span data-ttu-id="73025-214">Následující příklad ukazuje tyto vzory.</span><span class="sxs-lookup"><span data-stu-id="73025-214">The following example demonstrates these patterns.</span></span> <span data-ttu-id="73025-215">`DataOne` nebudou nalezeni funkcí katalogu.</span><span class="sxs-lookup"><span data-stu-id="73025-215">`DataOne` will be discovered by the catalog.</span></span> <span data-ttu-id="73025-216">Protože `DataTwo` je abstraktní, zjišťování selže.</span><span class="sxs-lookup"><span data-stu-id="73025-216">Since `DataTwo` is abstract, it will not be discovered.</span></span> <span data-ttu-id="73025-217">Protože `DataThree` použít `PartNotDiscoverable` atributu, nebudou zjištěna.</span><span class="sxs-lookup"><span data-stu-id="73025-217">Since `DataThree` used the `PartNotDiscoverable` attribute, it will not be discovered.</span></span>  
  
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
## <a name="metadata-and-metadata-views"></a><span data-ttu-id="73025-218">Metadata a zobrazení metadat</span><span class="sxs-lookup"><span data-stu-id="73025-218">Metadata and Metadata Views</span></span>  
 <span data-ttu-id="73025-219">Exporty můžou poskytnout další informace o samotné označované jako *metadat*.</span><span class="sxs-lookup"><span data-stu-id="73025-219">Exports can provide additional information about themselves known as *metadata*.</span></span> <span data-ttu-id="73025-220">Metadata můžete použít k předání vlastnosti objektu exportované do části importu.</span><span class="sxs-lookup"><span data-stu-id="73025-220">Metadata can be used to convey properties of the exported object to the importing part.</span></span> <span data-ttu-id="73025-221">Části importu můžete pomocí těchto dat se rozhodnout, který exportuje použití nebo shromažďovat informace o export bez nutnosti jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="73025-221">The importing part can use this data to decide which exports to use, or to gather information about an export without having to construct it.</span></span> <span data-ttu-id="73025-222">Z tohoto důvodu musí být importu opožděné použití metadat.</span><span class="sxs-lookup"><span data-stu-id="73025-222">For this reason, an import must be lazy to use metadata.</span></span>  
  
 <span data-ttu-id="73025-223">Použití metadat, deklarujete obvykle označuje jako rozhraní *zobrazení metadat*, který deklaruje metadat jaký bude k dispozici.</span><span class="sxs-lookup"><span data-stu-id="73025-223">To use metadata, you typically declare an interface known as a *metadata view*, which declares what metadata will be available.</span></span> <span data-ttu-id="73025-224">Rozhraní zobrazení metadat musí mít pouze vlastnosti, a tyto vlastnosti musí mít `get` přistupující objekty.</span><span class="sxs-lookup"><span data-stu-id="73025-224">The metadata view interface must have only properties, and those properties must have `get` accessors.</span></span> <span data-ttu-id="73025-225">Rozhraní následující je příklad zobrazení metadat.</span><span class="sxs-lookup"><span data-stu-id="73025-225">The following interface is an example metadata view.</span></span>  
  
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
  
 <span data-ttu-id="73025-226">Je také možné použít obecné kolekce `IDictionary<string, object>`, jako zobrazení metadat, ale to přichází výhody kontrolu typu a mělo by se vyhnout.</span><span class="sxs-lookup"><span data-stu-id="73025-226">It is also possible to use a generic collection, `IDictionary<string, object>`, as a metadata view, but this forfeits the benefits of type checking and should be avoided.</span></span>  
  
 <span data-ttu-id="73025-227">Obvykle jsou požadovány všechny vlastnosti v zobrazení metadat s názvem a žádné exporty, které se nevztahuje Smlouva je nesmí být považovány za shodné.</span><span class="sxs-lookup"><span data-stu-id="73025-227">Ordinarily, all of the properties named in the metadata view are required, and any exports that do not provide them will not be considered a match.</span></span> <span data-ttu-id="73025-228">`DefaultValue` Atribut určuje, že vlastnost je volitelná.</span><span class="sxs-lookup"><span data-stu-id="73025-228">The `DefaultValue` attribute specifies that a property is optional.</span></span> <span data-ttu-id="73025-229">Pokud je vlastnost neuvedete, se přiřadí výchozí hodnota zadaná jako parametr `DefaultValue`.</span><span class="sxs-lookup"><span data-stu-id="73025-229">If the property is not included, it will be assigned the default value specified as a parameter of `DefaultValue`.</span></span> <span data-ttu-id="73025-230">Tady jsou dvě různé třídy upravené pomocí metadat.</span><span class="sxs-lookup"><span data-stu-id="73025-230">The following are two different classes decorated with metadata.</span></span> <span data-ttu-id="73025-231">Obě tyto třídy by odpovídala na předchozí zobrazení metadat.</span><span class="sxs-lookup"><span data-stu-id="73025-231">Both of these classes would match the previous metadata view.</span></span>  
  
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
  
 <span data-ttu-id="73025-232">Metadata je vyjádřena po `Export` atribut s použitím `ExportMetadata` atribut.</span><span class="sxs-lookup"><span data-stu-id="73025-232">Metadata is expressed after the `Export` attribute by using the `ExportMetadata` attribute.</span></span> <span data-ttu-id="73025-233">Každá část metadata se skládá z dvojice název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="73025-233">Each piece of metadata is composed of a name/value pair.</span></span> <span data-ttu-id="73025-234">Část názvu metadat musí odpovídat názvu příslušné vlastnosti v zobrazení metadat a hodnota se přiřadí dané vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="73025-234">The name portion of the metadata must match the name of the appropriate property in the metadata view, and the value will be assigned to that property.</span></span>  
  
 <span data-ttu-id="73025-235">Pokud existuje, bude používán je programu pro import, který určuje, jaké zobrazení metadat.</span><span class="sxs-lookup"><span data-stu-id="73025-235">It is the importer that specifies what metadata view, if any, will be in use.</span></span> <span data-ttu-id="73025-236">Import metadat je deklarován jako opožděné import metadat rozhraní jako druhý parametr typu tím `Lazy<T,T>`.</span><span class="sxs-lookup"><span data-stu-id="73025-236">An import with metadata is declared as a lazy import, with the metadata interface as the second type parameter to `Lazy<T,T>`.</span></span> <span data-ttu-id="73025-237">Následující třídy importuje předchozí části s metadaty.</span><span class="sxs-lookup"><span data-stu-id="73025-237">The following class imports the previous part with metadata.</span></span>  
  
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
  
 <span data-ttu-id="73025-238">V mnoha případech budete chtít kombinovat metadat se `ImportMany` atribut, aby bylo možné analyzovat prostřednictvím dostupné importy a zvolte a vytvořit pouze jednu instanci nebo filtrovat kolekce tak, aby odpovídaly určité podmínky.</span><span class="sxs-lookup"><span data-stu-id="73025-238">In many cases, you will want to combine metadata with the `ImportMany` attribute, in order to parse through the available imports and choose and instantiate only one, or filter a collection to match a certain condition.</span></span> <span data-ttu-id="73025-239">Tyto třídy vytvoří pouze instanci `IPlugin` objekty, které mají `Name` hodnotu "Logger".</span><span class="sxs-lookup"><span data-stu-id="73025-239">The following class instantiates only `IPlugin` objects that have the `Name` value "Logger".</span></span>  
  
```vb  
Public Class User  
  
    <ImportMany()>  
    Public Property plugins As IEnumerable(Of Lazy(Of IPlugin, IPluginMetadata))  
  
    Public Function InstantiateLogger() As IPlugin  
  
        Dim logger As IPlugin  
        logger = Nothing  
  
        For Each Plugin As Lazy(Of IPlugin, IPluginMetadata) In plugins  
            If (Plugin.Metadata.Name = "Logger") Then  
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
  
    public IPlugin InstantiateLogger ()  
    {  
        IPlugin logger = null;  
  
        foreach (Lazy<IPlugin, IPluginMetadata> plugin in plugins)  
        {  
            if (plugin.Metadata.Name = "Logger") logger = plugin.Value;  
        }  
        return logger;  
    }  
}  
```  
  
<a name="import_and_export_inheritance"></a>   
## <a name="import-and-export-inheritance"></a><span data-ttu-id="73025-240">Import a Export dědičnosti</span><span class="sxs-lookup"><span data-stu-id="73025-240">Import and Export Inheritance</span></span>  
 <span data-ttu-id="73025-241">Pokud třída dědí z části, této třídy může být také součástí.</span><span class="sxs-lookup"><span data-stu-id="73025-241">If a class inherits from a part, that class may also become a part.</span></span> <span data-ttu-id="73025-242">Importy jsou vždy děděné podtřídy.</span><span class="sxs-lookup"><span data-stu-id="73025-242">Imports are always inherited by subclasses.</span></span> <span data-ttu-id="73025-243">Proto podtřídou třídy součástí bude vždy součástí, pomocí stejné importy jako své nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="73025-243">Therefore, a subclass of a part will always be a part, with the same imports as its parent class.</span></span>  
  
 <span data-ttu-id="73025-244">Exporty deklarovaná příkazem using `Export` nedědí atribut podtřídy.</span><span class="sxs-lookup"><span data-stu-id="73025-244">Exports declared by using the `Export` attribute are not inherited by subclasses.</span></span> <span data-ttu-id="73025-245">Ale součástí mohou exportovat samotného pomocí `InheritedExport` atribut.</span><span class="sxs-lookup"><span data-stu-id="73025-245">However, a part can export itself by using the `InheritedExport` attribute.</span></span> <span data-ttu-id="73025-246">Podtřídy třídy části bude dědit a poskytovat stejné exportu, včetně názvu kontraktu a typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="73025-246">Subclasses of the part will inherit and provide the same export, including contract name and contract type.</span></span> <span data-ttu-id="73025-247">Na rozdíl od `Export` atribut `InheritedExport` lze použít pouze na úrovni třídy a ne na úrovni člena.</span><span class="sxs-lookup"><span data-stu-id="73025-247">Unlike an `Export` attribute, `InheritedExport` can be applied only at the class level, and not at the member level.</span></span> <span data-ttu-id="73025-248">Proto je možné zdědit nikdy exporty úrovně členu.</span><span class="sxs-lookup"><span data-stu-id="73025-248">Therefore, member-level exports can never be inherited.</span></span>  
  
 <span data-ttu-id="73025-249">Následující čtyři třídy ukazují zásady import a export dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="73025-249">The following four classes demonstrate the principles of import and export inheritance.</span></span> <span data-ttu-id="73025-250">`NumTwo` dědí z `NumOne`, takže `NumTwo` naimportuje `IMyData`.</span><span class="sxs-lookup"><span data-stu-id="73025-250">`NumTwo` inherits from `NumOne`, so `NumTwo` will import `IMyData`.</span></span> <span data-ttu-id="73025-251">Běžné exporty nedědí, takže `NumTwo` nic nebude export.</span><span class="sxs-lookup"><span data-stu-id="73025-251">Ordinary exports are not inherited, so `NumTwo` will not export anything.</span></span> <span data-ttu-id="73025-252">`NumFour` dědí z `NumThree`.</span><span class="sxs-lookup"><span data-stu-id="73025-252">`NumFour` inherits from `NumThree`.</span></span> <span data-ttu-id="73025-253">Protože `NumThree` použít `InheritedExport`, `NumFour` má jeden export typu kontraktu `NumThree`.</span><span class="sxs-lookup"><span data-stu-id="73025-253">Because `NumThree` used `InheritedExport`, `NumFour` has one export with contract type `NumThree`.</span></span> <span data-ttu-id="73025-254">Nikdy dědí exporty úrovni člena, takže `IMyData` neexportoval.</span><span class="sxs-lookup"><span data-stu-id="73025-254">Member-level exports are never inherited, so `IMyData` is not exported.</span></span>  
  
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
  
 <span data-ttu-id="73025-255">Dojde-li metadata přidružené `InheritedExport` atribut, tato metadata se budou také dědit.</span><span class="sxs-lookup"><span data-stu-id="73025-255">If there is metadata associated with an `InheritedExport` attribute, that metadata will also be inherited.</span></span> <span data-ttu-id="73025-256">(Další informace najdete v předchozí části "Metadata a zobrazení metadat".) Podtřídy nemůže upravit zděděné metadat.</span><span class="sxs-lookup"><span data-stu-id="73025-256">(For more information, see the earlier "Metadata and Metadata Views" section.) Inherited metadata cannot be modified by the subclass.</span></span> <span data-ttu-id="73025-257">Ale deklarováním znovu `InheritedExport` atribut se stejným názvem kontraktu a typ smlouvy, ale s novými metadaty, podtřídy můžete nahradit zděděné metadat s novými metadaty.</span><span class="sxs-lookup"><span data-stu-id="73025-257">However, by re-declaring the `InheritedExport` attribute with the same contract name and contract type, but with new metadata, the subclass can replace the inherited metadata with new metadata.</span></span> <span data-ttu-id="73025-258">Následující třídy znázorňuje tento princip.</span><span class="sxs-lookup"><span data-stu-id="73025-258">The following class demonstrates this principle.</span></span> <span data-ttu-id="73025-259">`MegaLogger` Části dědí z `Logger` a zahrnuje `InheritedExport` atribut.</span><span class="sxs-lookup"><span data-stu-id="73025-259">The `MegaLogger` part inherits from `Logger` and includes the `InheritedExport` attribute.</span></span> <span data-ttu-id="73025-260">Protože `MegaLogger` novými metadaty znovu deklaruje pojmenované stav, nedědí názvu a verze metadat z `Logger`.</span><span class="sxs-lookup"><span data-stu-id="73025-260">Since `MegaLogger` re-declares new metadata named Status, it does not inherit the Name and Version metadata from `Logger`.</span></span>  
  
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
  
 <span data-ttu-id="73025-261">Při opětovné deklarování `InheritedExport` atribut přetížení metadat, ujistěte se, že typy kontraktů jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="73025-261">When re-declaring the `InheritedExport` attribute to override metadata, make sure that the contract types are the same.</span></span> <span data-ttu-id="73025-262">(V předchozím příkladu `IPlugin` je typ kontraktu.) Pokud se liší místo přepsání, druhý atribut se vytvoří druhé, nezávislé export z části.</span><span class="sxs-lookup"><span data-stu-id="73025-262">(In the previous example, `IPlugin` is the contract type.) If they differ, instead of overriding, the second attribute will create a second, independent export from the part.</span></span> <span data-ttu-id="73025-263">Obecně platí, to znamená, že je nutné explicitně zadat typ kontraktu při přepsání `InheritedExport` atributu, jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="73025-263">Generally, this means that you will have to explicitly specify the contract type when you override an `InheritedExport` attribute, as shown in the previous example.</span></span>  
  
 <span data-ttu-id="73025-264">Protože rozhraní nelze přímo vytvořit instanci, jsou obecně nedá dekorovat `Export` nebo `Import` atributy.</span><span class="sxs-lookup"><span data-stu-id="73025-264">Since interfaces cannot be instantiated directly, they generally cannot be decorated with `Export` or `Import` attributes.</span></span> <span data-ttu-id="73025-265">Rozhraní ale mohou být doplněny pomocí `InheritedExport` atribut na úrovni rozhraní, a že export spolu s související metadata zdědí všechny implementace třídy.</span><span class="sxs-lookup"><span data-stu-id="73025-265">However, an interface can be decorated with an `InheritedExport` attribute at the interface level, and that export along with any associated metadata will be inherited by any implementing classes.</span></span> <span data-ttu-id="73025-266">Ale nebudou k dispozici v rámci samotným rozhraním.</span><span class="sxs-lookup"><span data-stu-id="73025-266">The interface itself will not be available as a part, however.</span></span>  
  
<a name="custom_export_attributes"></a>   
## <a name="custom-export-attributes"></a><span data-ttu-id="73025-267">Export vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="73025-267">Custom Export Attributes</span></span>  
 <span data-ttu-id="73025-268">Atributy základní export `Export` a `InheritedExport`, je možné rozšířit na zahrnují metadata jako atribut vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="73025-268">The basic export attributes, `Export` and `InheritedExport`, can be extended to include metadata as attribute properties.</span></span> <span data-ttu-id="73025-269">Tato technika je užitečná pro použití podobné metadat pro mnoho částí nebo vytváření strom dědičnosti atributů metadat.</span><span class="sxs-lookup"><span data-stu-id="73025-269">This technique is useful for applying similar metadata to many parts, or creating an inheritance tree of metadata attributes.</span></span>  
  
 <span data-ttu-id="73025-270">Vlastní atribut můžete zadat typ smlouvy, název kontraktu nebo další metadata.</span><span class="sxs-lookup"><span data-stu-id="73025-270">A custom attribute can specify the contract type, the contract name, or any other metadata.</span></span> <span data-ttu-id="73025-271">Aby bylo možné definovat vlastní atribut třídu, která dědí z `ExportAttribute` (nebo `InheritedExportAttribute`) musí být doplněny pomocí `MetadataAttribute` atribut.</span><span class="sxs-lookup"><span data-stu-id="73025-271">In order to define a custom attribute, a class inheriting from `ExportAttribute` (or `InheritedExportAttribute`) must be decorated with the `MetadataAttribute` attribute.</span></span> <span data-ttu-id="73025-272">Následující třídy definuje vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="73025-272">The following class defines a custom attribute.</span></span>  
  
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
  
 <span data-ttu-id="73025-273">Tato třída definuje vlastní atribut s názvem `MyAttribute` s typem kontraktu `IMyData` a některé metadat s názvem `MyMetadata`.</span><span class="sxs-lookup"><span data-stu-id="73025-273">This class defines a custom attribute named `MyAttribute` with contract type `IMyData` and some metadata named `MyMetadata`.</span></span> <span data-ttu-id="73025-274">Všechny vlastnosti v třídě označené `MetadataAttribute` atribut jsou považovány za definovaný ve vlastním atributu metadat.</span><span class="sxs-lookup"><span data-stu-id="73025-274">All properties in a class marked with the `MetadataAttribute` attribute are considered to be metadata defined in the custom attribute.</span></span> <span data-ttu-id="73025-275">Jsou následující dvě deklarace ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="73025-275">The following two declarations are equivalent.</span></span>  
  
```vb  
<Export(GetType(IMyAddin))>  
<ExportMetadata("MyMetadata", "theData")>  
Public Property myAddin As MyAddin  
  
<MyAttribute("theData")>  
Public Property myAddin As MyAddin  
```  
  
```csharp  
[Export(typeof(IMyAddin)),   
    ExportMetadata("MyMetadata", "theData")]  
public MyAddin myAddin { get; set; }  
```  
  
```  
[MyAttribute("theData")]  
public MyAddin myAddin { get; set; }  
```  
  
 <span data-ttu-id="73025-276">V první deklaraci typu kontraktu a metadata jsou explicitně definovány.</span><span class="sxs-lookup"><span data-stu-id="73025-276">In the first declaration, the contract type and metadata are explicitly defined.</span></span> <span data-ttu-id="73025-277">V deklaraci druhý typ kontraktu a metadata jsou implicitní ve vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="73025-277">In the second declaration, the contract type and metadata are implicit in the customized attribute.</span></span> <span data-ttu-id="73025-278">Zejména v případech, kde je nutné použít velké množství identické metadat na mnoho částí (například autora nebo informace o autorských právech) můžete pomocí vlastního atributu uložit spoustu času a replikace.</span><span class="sxs-lookup"><span data-stu-id="73025-278">Particularly in cases where a large amount of identical metadata must be applied to many parts (for example, author or copyright information), using a custom attribute can save a lot of time and duplication.</span></span> <span data-ttu-id="73025-279">Stromové struktury dědičnosti vlastních atributů lze dále umožňovat plánování.</span><span class="sxs-lookup"><span data-stu-id="73025-279">Further, inheritance trees of custom attributes can be created to allow for variations.</span></span>  
  
 <span data-ttu-id="73025-280">Chcete-li vytvořit volitelná metadata ve vlastním atributu, můžete použít `DefaultValue` atribut.</span><span class="sxs-lookup"><span data-stu-id="73025-280">To create optional metadata in a custom attribute, you can use the `DefaultValue` attribute.</span></span> <span data-ttu-id="73025-281">Když tento atribut aplikován na vlastnost ve třídě vlastních atributů, určuje to, že dekorované vlastnost je volitelná a nebude muset zadávat Exportér.</span><span class="sxs-lookup"><span data-stu-id="73025-281">When this attribute is applied to a property in a custom attribute class, it specifies that the decorated property is optional and does not have to be supplied by an exporter.</span></span> <span data-ttu-id="73025-282">Pokud není zadána hodnota pro vlastnost, budou přiřazeny výchozí hodnotě pro jeho vlastnost typ (obvykle `null`, `false`, nebo 0.)</span><span class="sxs-lookup"><span data-stu-id="73025-282">If a value for the property is not supplied, it will be assigned the default value for its property type (usually `null`, `false`, or 0.)</span></span>  
  
<a name="creation_policies"></a>   
## <a name="creation-policies"></a><span data-ttu-id="73025-283">Vytvoření zásad</span><span class="sxs-lookup"><span data-stu-id="73025-283">Creation Policies</span></span>  
 <span data-ttu-id="73025-284">Když část určuje importu a skládání se provádí, kontejner kompozic se pokusí najít odpovídající exportu.</span><span class="sxs-lookup"><span data-stu-id="73025-284">When a part specifies an import and composition is performed, the composition container attempts to find a matching export.</span></span> <span data-ttu-id="73025-285">Pokud úspěšně odpovídá importu se export, import člen je nastavený na instanci objektu exportované.</span><span class="sxs-lookup"><span data-stu-id="73025-285">If it matches the import with an export successfully, the importing member is set to an instance of the exported object.</span></span> <span data-ttu-id="73025-286">Odkud pochází tato instance je řízen exportující část *vytváření zásad*.</span><span class="sxs-lookup"><span data-stu-id="73025-286">Where this instance comes from is controlled by the exporting part's *creation policy*.</span></span>  
  
 <span data-ttu-id="73025-287">Jsou dvě možné vytvoření zásady *sdílené* a *nesdílené*.</span><span class="sxs-lookup"><span data-stu-id="73025-287">The two possible creation policies are *shared* and *non-shared*.</span></span> <span data-ttu-id="73025-288">Část zásadám vytváření sdílených se sdílí mezi každému importu v kontejneru pro část s touto smlouvou.</span><span class="sxs-lookup"><span data-stu-id="73025-288">A part with a creation policy of shared will be shared between every import in the container for a part with that contract.</span></span> <span data-ttu-id="73025-289">Když Kompoziční modul najde shodu, musíme nastavit vlastnost importu ji jenom v případě, že již neexistuje, vytvoří instanci novou kopii části v opačném případě dodá stávající kopie.</span><span class="sxs-lookup"><span data-stu-id="73025-289">When the composition engine finds a match and has to set an importing property, it will instantiate a new copy of the part only if one does not already exist; otherwise, it will supply the existing copy.</span></span> <span data-ttu-id="73025-290">To znamená, že mnoho objektů může mít odkazy na stejné části.</span><span class="sxs-lookup"><span data-stu-id="73025-290">This means that many objects may have references to the same part.</span></span> <span data-ttu-id="73025-291">Tyto části neměli byste tedy spoléhat na vnitřní stav, který může být změněn z mnoha místech.</span><span class="sxs-lookup"><span data-stu-id="73025-291">Such parts should not rely on internal state that might be changed from many places.</span></span> <span data-ttu-id="73025-292">Tyto zásady jsou vhodné pro statické části, náhradní díly, které poskytují služby a částí, které využívají velké množství paměti nebo jiných prostředků.</span><span class="sxs-lookup"><span data-stu-id="73025-292">This policy is appropriate for static parts, parts that provide services, and parts that consume a lot of memory or other resources.</span></span>  
  
 <span data-ttu-id="73025-293">Část zásadám vytváření nesdílenými vytvoří pokaždé, když je nalezen odpovídající import pro jeden z jeho exporty.</span><span class="sxs-lookup"><span data-stu-id="73025-293">A part with the creation policy of non-shared will be created every time a matching import for one of its exports is found.</span></span> <span data-ttu-id="73025-294">Nová kopie bude vytvořena instance proto ke každému importu v kontejneru, který odpovídá jednomu z části exportovaných kontraktů.</span><span class="sxs-lookup"><span data-stu-id="73025-294">A new copy will therefore be instantiated for every import in the container that matches one of the part's exported contracts.</span></span> <span data-ttu-id="73025-295">Vnitřní stav tyto kopie nesmí sdílet.</span><span class="sxs-lookup"><span data-stu-id="73025-295">The internal state of these copies will not be shared.</span></span> <span data-ttu-id="73025-296">Tato zásada je vhodné pro části, kde každý import vyžaduje svou vlastní vnitřní stav.</span><span class="sxs-lookup"><span data-stu-id="73025-296">This policy is appropriate for parts where each import requires its own internal state.</span></span>  
  
 <span data-ttu-id="73025-297">Import a export můžete zadat zásady vytváření části, z hodnoty `Shared`, `NonShared`, nebo `Any`.</span><span class="sxs-lookup"><span data-stu-id="73025-297">Both the import and the export can specify the creation policy of a part, from among the values `Shared`, `NonShared`, or `Any`.</span></span> <span data-ttu-id="73025-298">Výchozí hodnota je `Any` pro obě importy a exporty.</span><span class="sxs-lookup"><span data-stu-id="73025-298">The default is `Any` for both imports and exports.</span></span> <span data-ttu-id="73025-299">Export, který určuje `Shared` nebo `NonShared` bude porovnávat pouze importu, který určuje stejný nebo, který určuje `Any`.</span><span class="sxs-lookup"><span data-stu-id="73025-299">An export that specifies `Shared` or `NonShared` will only match an import that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="73025-300">Podobně, import, který určuje `Shared` nebo `NonShared` bude porovnávat pouze export, který určuje stejný nebo, který určuje `Any`.</span><span class="sxs-lookup"><span data-stu-id="73025-300">Similarly, an import that specifies `Shared` or `NonShared` will only match an export that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="73025-301">Importy a exporty pomocí nekompatibilní vytváření zásad nejsou považovány za shodné, stejně jako import a export, jejíž název nebo smlouvy typ kontraktu nejsou odpovídající.</span><span class="sxs-lookup"><span data-stu-id="73025-301">Imports and exports with incompatible creation policies are not considered a match, in the same way as an import and export whose contract name or contract type are not a match.</span></span> <span data-ttu-id="73025-302">Import a export zadání `Any`, nebo nezadávejte vytvoření zásad a ve výchozím nastavení `Any`, vytvoření zásady budou ve výchozím nastavení sdílené.</span><span class="sxs-lookup"><span data-stu-id="73025-302">If both import and export specify `Any`, or do not specify a creation policy and default to `Any`, the creation policy will default to shared.</span></span>  
  
 <span data-ttu-id="73025-303">Následující příklad ukazuje importy a exporty určení zásad pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="73025-303">The following example shows both imports and exports specifying creation policies.</span></span> <span data-ttu-id="73025-304">`PartOne` neurčuje vytváření zásad, aby výchozí hodnota je `Any`.</span><span class="sxs-lookup"><span data-stu-id="73025-304">`PartOne` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="73025-305">`PartTwo` neurčuje vytváření zásad, aby výchozí hodnota je `Any`.</span><span class="sxs-lookup"><span data-stu-id="73025-305">`PartTwo` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="73025-306">Vzhledem k tomu, jak importovat a exportovat výchozí `Any`, `PartOne` se bude sdílet.</span><span class="sxs-lookup"><span data-stu-id="73025-306">Since both import and export default to `Any`, `PartOne` will be shared.</span></span> <span data-ttu-id="73025-307">`PartThree` Určuje `Shared` vytváření zásad, takže `PartTwo` a `PartThree` budou sdílet stejnou kopii `PartOne`.</span><span class="sxs-lookup"><span data-stu-id="73025-307">`PartThree` specifies a `Shared` creation policy, so `PartTwo` and `PartThree` will share the same copy of `PartOne`.</span></span> <span data-ttu-id="73025-308">`PartFour` Určuje `NonShared` vytváření zásad, takže `PartFour` bude nesdílené v `PartFive`.</span><span class="sxs-lookup"><span data-stu-id="73025-308">`PartFour` specifies a `NonShared` creation policy, so `PartFour` will be non-shared in `PartFive`.</span></span> <span data-ttu-id="73025-309">`PartSix` Určuje `NonShared` vytváření zásad.</span><span class="sxs-lookup"><span data-stu-id="73025-309">`PartSix` specifies a `NonShared` creation policy.</span></span> <span data-ttu-id="73025-310">`PartFive` a `PartSix` obdrží každou samostatnou kopii `PartFour`.</span><span class="sxs-lookup"><span data-stu-id="73025-310">`PartFive` and `PartSix` will each receive separate copies of `PartFour`.</span></span> <span data-ttu-id="73025-311">`PartSeven` Určuje `Shared` vytváření zásad.</span><span class="sxs-lookup"><span data-stu-id="73025-311">`PartSeven` specifies a `Shared` creation policy.</span></span> <span data-ttu-id="73025-312">Protože neexistuje žádné exportované `PartFour` s zásady vytváření `Shared`, `PartSeven` import ničemu neodpovídá a není vyplněné.</span><span class="sxs-lookup"><span data-stu-id="73025-312">Because there is no exported `PartFour` with a creation policy of `Shared`, the `PartSeven` import does not match anything and will not be filled.</span></span>  
  
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
    'Since the export's creation policy was explictly  
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
    //Since the export's creation policy was explictly  
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
## <a name="life-cycle-and-disposing"></a><span data-ttu-id="73025-313">Životní cyklus a připravuje se</span><span class="sxs-lookup"><span data-stu-id="73025-313">Life Cycle and Disposing</span></span>  
 <span data-ttu-id="73025-314">Protože součásti jsou hostované v kontejner kompozic, může být složitější než běžné objekty svůj životní cyklus.</span><span class="sxs-lookup"><span data-stu-id="73025-314">Because parts are hosted in the composition container, their life cycle can be more complex than ordinary objects.</span></span> <span data-ttu-id="73025-315">Části mohou implementovat rozhraní dvě důležité týkající se životního cyklu: `IDisposable` a `IPartImportsSatisfiedNotification`.</span><span class="sxs-lookup"><span data-stu-id="73025-315">Parts can implement two important life cycle-related interfaces: `IDisposable` and `IPartImportsSatisfiedNotification`.</span></span>  
  
 <span data-ttu-id="73025-316">Částí, které vyžadují práce, která musí provést vypnutí, dolů nebo které je třeba uvolnit prostředky by měly implementovat `IDisposable`, jako obvykle pro objekty rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="73025-316">Parts that require work to be performed at shut down or that need to release resources should implement `IDisposable`, as usual for .NET Framework objects.</span></span> <span data-ttu-id="73025-317">Ale protože kontejneru vytvoří a spravuje odkazy na části, pouze kontejneru, který vlastní součástí by měly volat `Dispose` metoda na něj.</span><span class="sxs-lookup"><span data-stu-id="73025-317">However, since the container creates and maintains references to parts, only the container that owns a part should call the `Dispose` method on it.</span></span> <span data-ttu-id="73025-318">Implementuje kontejner sám o sobě `IDisposable`a jako část jeho vyčištění v `Dispose` bude volat `Dispose` na všechny části, které vlastní.</span><span class="sxs-lookup"><span data-stu-id="73025-318">The container itself implements `IDisposable`, and as portion of its cleanup in `Dispose` it will call `Dispose` on all the parts that it owns.</span></span> <span data-ttu-id="73025-319">Z tohoto důvodu by měl vždy dispose kontejner kompozic, pokud už nepotřebujete a některé části, které vlastní.</span><span class="sxs-lookup"><span data-stu-id="73025-319">For this reason, you should always dispose the composition container when it and any parts it owns are no longer needed.</span></span>  
  
 <span data-ttu-id="73025-320">Pro kontejnery s dlouhým poločasem rozpadu složení využití paměti podle části zásadám vytváření nesdílenými stát problémem.</span><span class="sxs-lookup"><span data-stu-id="73025-320">For long-lived composition containers, memory consumption by parts with a creation policy of non-shared can become a problem.</span></span> <span data-ttu-id="73025-321">Tyto nesdílenými součástmi je možné vytvořit více než jednou a nebude odstraněn, dokud se kontejner sám o sobě je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="73025-321">These non-shared parts can be created multiple times and will not be disposed until the container itself is disposed.</span></span> <span data-ttu-id="73025-322">Nelze zpracovat takové, poskytuje kontejneru `ReleaseExport` metody.</span><span class="sxs-lookup"><span data-stu-id="73025-322">To deal with this, the container provides the `ReleaseExport` method.</span></span> <span data-ttu-id="73025-323">Voláním této metody na k exportu nesdílenými odstraní tento export z kontejner kompozic a zruší ho.</span><span class="sxs-lookup"><span data-stu-id="73025-323">Calling this method on a non-shared export removes that export from the composition container and disposes it.</span></span> <span data-ttu-id="73025-324">Části, které jsou používány pouze odebrané exportu, a tak dále dolů stromu, se taky odeberou a odstraněn.</span><span class="sxs-lookup"><span data-stu-id="73025-324">Parts that are used only by the removed export, and so on down the tree, are also removed and disposed.</span></span> <span data-ttu-id="73025-325">Tímto způsobem můžou uvolnit prostředky bez uvolnění samotný kontejner složení.</span><span class="sxs-lookup"><span data-stu-id="73025-325">In this way, resources can be reclaimed without disposing the composition container itself.</span></span>  
  
 <span data-ttu-id="73025-326">`IPartImportsSatisfiedNotification` obsahuje jednu metodu s názvem `OnImportsSatisfied`.</span><span class="sxs-lookup"><span data-stu-id="73025-326">`IPartImportsSatisfiedNotification` contains one method named `OnImportsSatisfied`.</span></span> <span data-ttu-id="73025-327">Tato metoda je volána kontejner kompozic v některé části, které implementují rozhraní, když dokončil složení a části importy jsou připravené k použití.</span><span class="sxs-lookup"><span data-stu-id="73025-327">This method is called by the composition container on any parts that implement the interface when composition has been completed and the part's imports are ready for use.</span></span> <span data-ttu-id="73025-328">Kompoziční modul tak, aby vyplnil importy z dalších částí vytvářejí částí.</span><span class="sxs-lookup"><span data-stu-id="73025-328">Parts are created by the composition engine to fill the imports of other parts.</span></span> <span data-ttu-id="73025-329">Importy z část jste nastavili, je nelze provést všechny inicializace, které spoléhá na nebo tyto hodnoty jste byla určena jako požadavky pomocí provádí úpravy importované hodnoty v konstruktoru část `ImportingConstructor` atribut.</span><span class="sxs-lookup"><span data-stu-id="73025-329">Before the imports of a part have been set, you cannot perform any initialization that relies on or manipulates imported values in the part constructor unless those values have been specified as prerequisites by using the `ImportingConstructor` attribute.</span></span> <span data-ttu-id="73025-330">Toto je obvykle upřednostňovanou metodou, ale v některých případech nemusí být k dispozici prostřednictvím injektáže konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="73025-330">This is normally the preferred method, but in some cases, constructor injection may not be available.</span></span> <span data-ttu-id="73025-331">V těchto případech je možné provádět inicializace `OnImportsSatisfied`, a měla by implementovat části `IPartImportsSatisfiedNotification`.</span><span class="sxs-lookup"><span data-stu-id="73025-331">In those cases, initialization can be performed in `OnImportsSatisfied`, and the part should implement `IPartImportsSatisfiedNotification`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73025-332">Viz také</span><span class="sxs-lookup"><span data-stu-id="73025-332">See Also</span></span>  
 [<span data-ttu-id="73025-333">Video pro kanál 9: Otevřete aplikací pomocí Managed Extensibility Framework</span><span class="sxs-lookup"><span data-stu-id="73025-333">Channel 9 Video: Open Up Your Applications with the Managed Extensibility Framework</span></span>](https://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)  
 [<span data-ttu-id="73025-334">Video pro kanál 9: Managed Extensibility Framework (MEF) 2.0</span><span class="sxs-lookup"><span data-stu-id="73025-334">Channel 9 Video: Managed Extensibility Framework (MEF) 2.0</span></span>](https://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)

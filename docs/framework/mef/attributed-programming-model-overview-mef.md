---
title: "Přehled modelu programování s přidělenými atributy (MEF)"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MEF, attributed programming model
- attributed programming model [MEF]
ms.assetid: 49b787ff-2741-4836-ad51-c3017dc592d4
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16ffe789635ee13c118c63c30ef255cc9b264a9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="attributed-programming-model-overview-mef"></a><span data-ttu-id="62fa6-102">Přehled modelu programování s přidělenými atributy (MEF)</span><span class="sxs-lookup"><span data-stu-id="62fa6-102">Attributed Programming Model Overview (MEF)</span></span>
<span data-ttu-id="62fa6-103">V Managed Extensibility Framework (MEF), *programovací model* je konkrétní metoda definování sady koncepční objektů, na kterých pracuje MEF.</span><span class="sxs-lookup"><span data-stu-id="62fa6-103">In the Managed Extensibility Framework (MEF), a *programming model* is a particular method of defining the set of conceptual objects on which MEF operates.</span></span> <span data-ttu-id="62fa6-104">Tyto rámcové objekty zahrnují části, import a export.</span><span class="sxs-lookup"><span data-stu-id="62fa6-104">These conceptual objects include parts, imports, and exports.</span></span> <span data-ttu-id="62fa6-105">MEF používá tyto objekty, ale neurčuje, jak by měly být zastoupeny.</span><span class="sxs-lookup"><span data-stu-id="62fa6-105">MEF uses these objects, but does not specify how they should be represented.</span></span> <span data-ttu-id="62fa6-106">Proto je možné, včetně přizpůsobit programovací modely celou řadu programovacích modelů.</span><span class="sxs-lookup"><span data-stu-id="62fa6-106">Therefore, a wide variety of programming models are possible, including customized programming models.</span></span>  
  
 <span data-ttu-id="62fa6-107">Výchozí hodnota je programovací model použitý v MEF *model programování s atributy*.</span><span class="sxs-lookup"><span data-stu-id="62fa6-107">The default programming model used in MEF is the *attributed programming model*.</span></span> <span data-ttu-id="62fa6-108">V části s atributy programovací model import, export a jiné objekty jsou definovány s atributy, které uspořádání běžné třídy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="62fa6-108">In the attributed programming model parts, imports, exports, and other objects are defined with attributes that decorate ordinary .NET Framework classes.</span></span> <span data-ttu-id="62fa6-109">Toto téma vysvětluje, jak použít atributy poskytované model programování s atributy pro vytvoření aplikace MEF.</span><span class="sxs-lookup"><span data-stu-id="62fa6-109">This topic explains how to use the attributes provided by the attributed programming model to create a MEF application.</span></span>  
  
<a name="import_and_export_basics"></a>   
## <a name="import-and-export-basics"></a><span data-ttu-id="62fa6-110">Import a Export základy</span><span class="sxs-lookup"><span data-stu-id="62fa6-110">Import and Export Basics</span></span>  
 <span data-ttu-id="62fa6-111">*Exportovat* je hodnota, která poskytuje součástí do dalších částí v kontejneru, a *importovat* je požadavek, který je součástí vyjadřoval do kontejneru, aby byla vyplněna z dostupných exporty.</span><span class="sxs-lookup"><span data-stu-id="62fa6-111">An *export* is a value that a part provides to other parts in the container, and an *import* is a requirement that a part expresses to the container, to be filled from the available exports.</span></span> <span data-ttu-id="62fa6-112">Ve model programování s atributy, import a export je deklarovaná architekturu třídy nebo členy s `Import` a `Export` atributy.</span><span class="sxs-lookup"><span data-stu-id="62fa6-112">In the attributed programming model, imports and exports are declared by decorating classes or members with the `Import` and `Export` attributes.</span></span> <span data-ttu-id="62fa6-113">`Export` Atributu můžete uspořádání třídu, pole, vlastnost nebo metoda, při `Import` atributu můžete uspořádání parametr pole, vlastnost nebo konstruktor.</span><span class="sxs-lookup"><span data-stu-id="62fa6-113">The `Export` attribute can decorate a class, field, property, or method, while the `Import` attribute can decorate a field, property, or constructor parameter.</span></span>  
  
 <span data-ttu-id="62fa6-114">Aby importu lze porovnat s exportu, import a export musí mít stejnou *kontrakt*.</span><span class="sxs-lookup"><span data-stu-id="62fa6-114">In order for an import to be matched with an export, the import and export must have the same *contract*.</span></span> <span data-ttu-id="62fa6-115">Smlouva se skládá z řetězec s názvem *název kontraktu*a typ objektu exportovanou nebo importované, volá se *typ kontraktu*.</span><span class="sxs-lookup"><span data-stu-id="62fa6-115">The contract consists of a string, called the *contract name*, and the type of the exported or imported object, called the *contract type*.</span></span> <span data-ttu-id="62fa6-116">Pouze v případě, že název kontraktu i smlouva zadejte shodu považuje exportu splnit konkrétní importu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-116">Only if both the contract name and contract type match is an export considered to fulfill a particular import.</span></span>  
  
 <span data-ttu-id="62fa6-117">Implicitním nebo explicitním, může být buď nebo oba parametry kontrakt.</span><span class="sxs-lookup"><span data-stu-id="62fa6-117">Either or both of the contract parameters can be implicit or explicit.</span></span> <span data-ttu-id="62fa6-118">Následující kód ukazuje třídu, který deklaruje základní import.</span><span class="sxs-lookup"><span data-stu-id="62fa6-118">The following code shows a class that declares a basic import.</span></span>  
  
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
  
 <span data-ttu-id="62fa6-119">V tomto importu `Import` atribut má typ smlouvy ani parametr název kontraktu připojen.</span><span class="sxs-lookup"><span data-stu-id="62fa6-119">In this import, the `Import` attribute has neither a contract type nor a contract name parameter attached.</span></span> <span data-ttu-id="62fa6-120">Proto i bude odvodit z dekorované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="62fa6-120">Therefore, both will be inferred from the decorated property.</span></span> <span data-ttu-id="62fa6-121">V takovém případě bude typ smlouvy `IMyAddin`, a název kontraktu bude jedinečný řetězec vytvořený z typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-121">In this case, the contract type will be `IMyAddin`, and the contract name will be a unique string created from the contract type.</span></span> <span data-ttu-id="62fa6-122">(Jinými slovy, název kontraktu bude odpovídat jenom exportuje, jejichž názvy jsou také odvodit z typu `IMyAddin`.)</span><span class="sxs-lookup"><span data-stu-id="62fa6-122">(In other words, the contract name will match only exports whose names are also inferred from the type `IMyAddin`.)</span></span>  
  
 <span data-ttu-id="62fa6-123">Následující obrázek znázorňuje exportu, který odpovídá předchozí importu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-123">The following shows an export that matches the previous import.</span></span>  
  
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
  
 <span data-ttu-id="62fa6-124">V tento export je typ kontraktu `IMyAddin` vzhledem k tomu, že je zadán jako parametr `Export` atribut.</span><span class="sxs-lookup"><span data-stu-id="62fa6-124">In this export, the contract type is `IMyAddin` because it is specified as a parameter of the `Export` attribute.</span></span> <span data-ttu-id="62fa6-125">Exportovaný typ musí být buď stejný jako typ smlouvy, jsou odvozeny od typu kontraktu nebo implementovat typ smlouvy, pokud je rozhraní.</span><span class="sxs-lookup"><span data-stu-id="62fa6-125">The exported type must be either the same as the contract type, derive from the contract type, or implement the contract type if it is an interface.</span></span> <span data-ttu-id="62fa6-126">V této exportu, skutečný typ `MyLogger` implementuje rozhraní `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-126">In this export, the actual type `MyLogger` implements the interface `IMyAddin`.</span></span> <span data-ttu-id="62fa6-127">Název smlouvy je odvozeno z typu kontraktu, což znamená, že tento export bude shodovat s předchozí importu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-127">The contract name is inferred from the contract type, which means that this export will match the previous import.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62fa6-128">Export a import by měl obvykle deklarovat na veřejné třídy nebo členy.</span><span class="sxs-lookup"><span data-stu-id="62fa6-128">Exports and imports should usually be declared on public classes or members.</span></span> <span data-ttu-id="62fa6-129">Další deklarace jsou podporovány, ale exportu nebo importu privátního, chráněný, nebo vnitřní člen dělí model izolace pro část a proto se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="62fa6-129">Other declarations are supported, but exporting or importing a private, protected, or internal member breaks the isolation model for the part and is therefore not recommended.</span></span>  
  
 <span data-ttu-id="62fa6-130">Typ smlouvy musí odpovídat přesně exportu a importu do být považovány za shodné.</span><span class="sxs-lookup"><span data-stu-id="62fa6-130">The contract type must match exactly for the export and import to be considered a match.</span></span> <span data-ttu-id="62fa6-131">Vezměte v úvahu následující exportu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-131">Consider the following export.</span></span>  
  
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
  
 <span data-ttu-id="62fa6-132">V tento export je typ kontraktu `MyLogger` místo `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-132">In this export, the contract type is `MyLogger` instead of `IMyAddin`.</span></span> <span data-ttu-id="62fa6-133">I když `MyLogger` implementuje `IMyAddin`a proto může být přetypovat `IMyAddin` objektu, tento export nebude odpovídat předchozí importovat, protože kontrakt typy nejsou stejné.</span><span class="sxs-lookup"><span data-stu-id="62fa6-133">Even though `MyLogger` implements `IMyAddin`, and therefore could be cast to an `IMyAddin` object, this export will not match the previous import because the contract types are not the same.</span></span>  
  
 <span data-ttu-id="62fa6-134">Obecně platí není nutné zadat název kontraktu a většina kontrakty by měl být definován jako typ smlouvy a metadata.</span><span class="sxs-lookup"><span data-stu-id="62fa6-134">In general, it is not necessary to specify the contract name, and most contracts should be defined in terms of the contract type and metadata.</span></span> <span data-ttu-id="62fa6-135">Za určitých okolností, je potřeba zadat název kontraktu přímo.</span><span class="sxs-lookup"><span data-stu-id="62fa6-135">However, under certain circumstances, it is important to specify the contract name directly.</span></span> <span data-ttu-id="62fa6-136">Nejběžnější případ je, když třída exportuje několik hodnot, které sdílejí společný typ, třeba primitiv.</span><span class="sxs-lookup"><span data-stu-id="62fa6-136">The most common case is when a class exports several values that share a common type, such as primitives.</span></span> <span data-ttu-id="62fa6-137">Název smlouvy lze zadat jako první parametr `Import` nebo `Export` atribut.</span><span class="sxs-lookup"><span data-stu-id="62fa6-137">The contract name can be specified as the first parameter of the `Import` or `Export` attribute.</span></span> <span data-ttu-id="62fa6-138">Následující kód ukazuje importu a exportu s názvem zadaného kontrakt `MajorRevision`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-138">The following code shows an import and an export with a specified contract name of `MajorRevision`.</span></span>  
  
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
  
 <span data-ttu-id="62fa6-139">Pokud není zadán typ smlouvy, bude stále odvodit z typu import nebo export.</span><span class="sxs-lookup"><span data-stu-id="62fa6-139">If the contract type is not specified, it will still be inferred from the type of the import or export.</span></span> <span data-ttu-id="62fa6-140">Ale i v případě, že název smlouvy je explicitně zadané, typ kontraktu se taky musí shodovat přesně pro import a export do být považovány za shodné.</span><span class="sxs-lookup"><span data-stu-id="62fa6-140">However, even if the contract name is specified explicitly, the contract type must also match exactly for the import and export to be considered a match.</span></span> <span data-ttu-id="62fa6-141">Například pokud `MajorRevision` pole byl to řetězec, nebude odpovídající typy odvozené kontraktu a export nebude odpovídat import, přes který má stejný název kontraktu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-141">For example, if the `MajorRevision` field was a string, the inferred contract types would not match and the export would not match the import, despite having the same contract name.</span></span>  
  
### <a name="importing-and-exporting-a-method"></a><span data-ttu-id="62fa6-142">Import a export metody</span><span class="sxs-lookup"><span data-stu-id="62fa6-142">Importing and Exporting a Method</span></span>  
 <span data-ttu-id="62fa6-143">`Export` Atributu můžete také uspořádání metodu, stejným způsobem jako třídu, vlastnost nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="62fa6-143">The `Export` attribute can also decorate a method, in the same way as a class, property, or function.</span></span> <span data-ttu-id="62fa6-144">Metoda Export třeba zadat typ smlouvy nebo název kontraktu jako typ nemůže být odvozený.</span><span class="sxs-lookup"><span data-stu-id="62fa6-144">Method exports must specify a contract type or contract name, as the type cannot be inferred.</span></span> <span data-ttu-id="62fa6-145">Zadaný typ může být vlastní delegáta nebo obecného typu, například `Func`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-145">The specified type can be either a custom delegate or a generic type, such as `Func`.</span></span> <span data-ttu-id="62fa6-146">Následující třídy exportuje metodu s názvem `DoSomething`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-146">The following class exports a method named `DoSomething`.</span></span>  
  
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
    [Export(typeof(Func<int, string>)]  
    public string DoSomething(int TheParam);  
}  
```  
  
 <span data-ttu-id="62fa6-147">V této třídě `DoSomething` metoda přebírá jediný `int` parametr a vrátí `string`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-147">In this class, the `DoSomething` method takes a single `int` parameter and returns a `string`.</span></span> <span data-ttu-id="62fa6-148">Pro tento export shodu, je třeba deklarovat import část příslušného člena.</span><span class="sxs-lookup"><span data-stu-id="62fa6-148">To match this export, the importing part must declare an appropriate member.</span></span> <span data-ttu-id="62fa6-149">Následující třídy importy `DoSomething` metoda.</span><span class="sxs-lookup"><span data-stu-id="62fa6-149">The following class imports the `DoSomething` method.</span></span>  
  
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
  
 <span data-ttu-id="62fa6-150">Další informace o tom, jak použít `Func<T, T>` objektu, najdete v části <xref:System.Func%602>.</span><span class="sxs-lookup"><span data-stu-id="62fa6-150">For more information about how to use of the `Func<T, T>` object, see <xref:System.Func%602>.</span></span>  
  
<a name="types_of_imports"></a>   
## <a name="types-of-imports"></a><span data-ttu-id="62fa6-151">Typy importy</span><span class="sxs-lookup"><span data-stu-id="62fa6-151">Types of Imports</span></span>  
 <span data-ttu-id="62fa6-152">Podpory MEF několik importovat typy včetně dynamické opožděné, požadované a volitelné.</span><span class="sxs-lookup"><span data-stu-id="62fa6-152">MEF support several import types, including dynamic, lazy, prerequisite, and optional.</span></span>  
  
### <a name="dynamic-imports"></a><span data-ttu-id="62fa6-153">Dynamické importy</span><span class="sxs-lookup"><span data-stu-id="62fa6-153">Dynamic Imports</span></span>  
 <span data-ttu-id="62fa6-154">V některých případech může chtít import třídy tak, aby odpovídaly exportuje libovolného typu, které mají název konkrétní kontraktu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-154">In some cases, the importing class may want to match exports of any type that have a particular contract name.</span></span> <span data-ttu-id="62fa6-155">V tomto scénáři můžou deklarovat třídy *dynamické import*.</span><span class="sxs-lookup"><span data-stu-id="62fa6-155">In this scenario, the class can declare a *dynamic import*.</span></span> <span data-ttu-id="62fa6-156">Následující importu odpovídá žádné exportu s název kontraktu "TheString".</span><span class="sxs-lookup"><span data-stu-id="62fa6-156">The following import matches any export with contract name "TheString".</span></span>  
  
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
  
 <span data-ttu-id="62fa6-157">Když je typ smlouvy odvodit z `dynamic` – klíčové slovo, se bude shodovat s jakýmikoli kontrakt.</span><span class="sxs-lookup"><span data-stu-id="62fa6-157">When the contract type is inferred from the `dynamic` keyword, it will match any contract type.</span></span> <span data-ttu-id="62fa6-158">V takovém případě by měl importu **vždy** zadejte název kontraktu tak, aby odpovídala na.</span><span class="sxs-lookup"><span data-stu-id="62fa6-158">In this case, an import should **always** specify a contract name to match on.</span></span> <span data-ttu-id="62fa6-159">(Pokud není zadán žádný název kontraktu, import bude považovat za tak, aby odpovídaly žádným exportům.) Obě tyto exporty odpovídá předchozí importu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-159">(If no contract name is specified, the import will be considered to match no exports.) Both of the following exports would match the previous import.</span></span>  
  
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
  
 <span data-ttu-id="62fa6-160">Samozřejmě musí být import třída připraveno jak nakládat s objekt libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-160">Obviously, the importing class must be prepared to deal with an object of arbitrary type.</span></span>  
  
### <a name="lazy-imports"></a><span data-ttu-id="62fa6-161">Opožděné importy</span><span class="sxs-lookup"><span data-stu-id="62fa6-161">Lazy Imports</span></span>  
 <span data-ttu-id="62fa6-162">V některých případech může import – třída vyžadovat nepřímý odkaz na importovaný objekt tak, aby objekt není instanci okamžitě.</span><span class="sxs-lookup"><span data-stu-id="62fa6-162">In some cases, the importing class may require an indirect reference to the imported object, so that the object is not instantiated immediately.</span></span> <span data-ttu-id="62fa6-163">V tomto scénáři můžou deklarovat třídy *opožděné import* pomocí typu kontraktu `Lazy<T>`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-163">In this scenario, the class can declare a *lazy import* by using a contract type of `Lazy<T>`.</span></span> <span data-ttu-id="62fa6-164">Následující import vlastnost deklaruje opožděné importu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-164">The following importing property declares a lazy import.</span></span>  
  
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
  
 <span data-ttu-id="62fa6-165">Z hlediska modulu složení, kontrakt typ `Lazy<T>` se považuje za identické smlouvy typ `T`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-165">From the point of view of the composition engine, a contract type of `Lazy<T>` is considered identical to contract type of `T`.</span></span> <span data-ttu-id="62fa6-166">Proto předchozí importu odpovídá následující exportu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-166">Therefore, the previous import would match the following export.</span></span>  
  
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
  
 <span data-ttu-id="62fa6-167">V lze zadat název kontraktu a typ smlouvy `Import` atribut pro opožděné import, jak je popsáno výše v části "Základní import a export".</span><span class="sxs-lookup"><span data-stu-id="62fa6-167">The contract name and contract type can be specified in the `Import` attribute for a lazy import, as described earlier in the "Basic Imports and Exports" section.</span></span>  
  
### <a name="prerequisite-imports"></a><span data-ttu-id="62fa6-168">Požadovaný importy</span><span class="sxs-lookup"><span data-stu-id="62fa6-168">Prerequisite Imports</span></span>  
 <span data-ttu-id="62fa6-169">Exportovaný částí rozhraní MEF se obvykle vytvářejí modul složení, v reakci na žádost o přímý nebo nutnosti zadejte odpovídající importu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-169">Exported MEF parts are typically created by the composition engine, in response to a direct request or the need to fill a matched import.</span></span> <span data-ttu-id="62fa6-170">Ve výchozím nastavení se při vytváření součástí používá modul složení konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="62fa6-170">By default, when creating a part, the composition engine uses the parameter-less constructor.</span></span> <span data-ttu-id="62fa6-171">Chcete-li modul použijte jiný konstruktor, můžete označit její `ImportingConstructor` atribut.</span><span class="sxs-lookup"><span data-stu-id="62fa6-171">To make the engine use a different constructor, you can mark it with the `ImportingConstructor` attribute.</span></span>  
  
 <span data-ttu-id="62fa6-172">Jednotlivé části může mít pouze jeden konstruktor pro použití modul složení.</span><span class="sxs-lookup"><span data-stu-id="62fa6-172">Each part may have only one constructor for use by the composition engine.</span></span> <span data-ttu-id="62fa6-173">Poskytnutí neexistoval výchozí konstruktor a ne `ImportingConstructor` atribut, nebo zadáním více než jeden `ImportingConstructor` atribut, vygeneruje chybu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-173">Providing no default constructor and no `ImportingConstructor` attribute, or providing more than one `ImportingConstructor` attribute, will produce an error.</span></span>  
  
 <span data-ttu-id="62fa6-174">K vyplnění parametry konstruktor označené jako `ImportingConstructor` atribut všechny tyto parametry jsou automaticky deklarované jako importy.</span><span class="sxs-lookup"><span data-stu-id="62fa6-174">To fill the parameters of a constructor marked with the `ImportingConstructor` attribute, all of those parameters are automatically declared as imports.</span></span> <span data-ttu-id="62fa6-175">Toto je pohodlný způsob, jak deklarovat importy, které se používají během inicializace část.</span><span class="sxs-lookup"><span data-stu-id="62fa6-175">This is a convenient way to declare imports that are used during part initialization.</span></span> <span data-ttu-id="62fa6-176">Následující třídy používá `ImportingConstructor` deklarovat importu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-176">The following class uses `ImportingConstructor` to declare an import.</span></span>  
  
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
  
 <span data-ttu-id="62fa6-177">Ve výchozím nastavení `ImportingConstructor` atribut používá odvozené typy kontraktů a smlouvy názvy pro všechny importy parametr.</span><span class="sxs-lookup"><span data-stu-id="62fa6-177">By default, the `ImportingConstructor` attribute uses inferred contract types and contract names for all of the parameter imports.</span></span> <span data-ttu-id="62fa6-178">Je možné přepsat to tak, že architekturu parametry s `Import` atributy, které lze poté zadejte typ smlouvy a název kontraktu explicitně.</span><span class="sxs-lookup"><span data-stu-id="62fa6-178">It is possible to override this by decorating the parameters with `Import` attributes, which can then define the contract type and contract name explicitly.</span></span> <span data-ttu-id="62fa6-179">Následující kód ukazuje konstruktor, který používá tuto syntaxi k importu do odvozené třídy místo nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="62fa6-179">The following code demonstrates a constructor that uses this syntax to import a derived class instead of a parent class.</span></span>  
  
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
  
 <span data-ttu-id="62fa6-180">Konkrétně byste měli být opatrní při práci s parametry kolekce.</span><span class="sxs-lookup"><span data-stu-id="62fa6-180">In particular, you should be careful with collection parameters.</span></span> <span data-ttu-id="62fa6-181">Pokud zadáte například `ImportingConstructor` na konstruktor s parametrem typu `IEnumerable<int>`, import bude odpovídat jedné export typu `IEnumerable<int>`, místo sadu exportuje typu `int`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-181">For example, if you specify `ImportingConstructor` on a constructor with a parameter of type `IEnumerable<int>`, the import will match a single export of type `IEnumerable<int>`, instead of a set of exports of type `int`.</span></span> <span data-ttu-id="62fa6-182">Tak, aby odpovídaly sadu exportuje typu `int`, budete muset uspořádání parametr pomocí `ImportMany` atribut.</span><span class="sxs-lookup"><span data-stu-id="62fa6-182">To match a set of exports of type `int`, you have to decorate the parameter with the `ImportMany` attribute.</span></span>  
  
 <span data-ttu-id="62fa6-183">Parametry deklarován jako importy pomocí `ImportingConstructor` atribut jsou také označen jako *importuje požadovaných součástí*.</span><span class="sxs-lookup"><span data-stu-id="62fa6-183">Parameters declared as imports by the `ImportingConstructor` attribute are also marked as *prerequisite imports*.</span></span> <span data-ttu-id="62fa6-184">MEF normálně umožňuje exportuje a naimportuje do formuláře *cyklus*.</span><span class="sxs-lookup"><span data-stu-id="62fa6-184">MEF normally allows exports and imports to form a *cycle*.</span></span> <span data-ttu-id="62fa6-185">Cyklus. je třeba kde importy objektu A objekt B, který naopak importuje objekt A. Za běžných okolností cyklus se nejedná o problém a kontejneru složení vytvoří oba objekty normálně.</span><span class="sxs-lookup"><span data-stu-id="62fa6-185">For example, a cycle is where object A imports object B, which in turn imports object A. Under ordinary circumstances, a cycle is not a problem, and the composition container constructs both objects normally.</span></span>  
  
 <span data-ttu-id="62fa6-186">Když importované hodnotu vyžaduje konstruktoru součástí, tento objekt nemůže být součástí cyklický odkaz.</span><span class="sxs-lookup"><span data-stu-id="62fa6-186">When an imported value is required by the constructor of a part, that object cannot participate in a cycle.</span></span> <span data-ttu-id="62fa6-187">Pokud objekt A vyžaduje, aby tento objekt B zkonstruovat před jde konstruovat samostatně a objekt B importuje objekt A potom na cyklus nelze vyřešit a dojde k chybě složení.</span><span class="sxs-lookup"><span data-stu-id="62fa6-187">If object A requires that object B be constructed before it can be constructed itself, and object B imports object A, then the cycle will be unable to resolve and a composition error will occur.</span></span> <span data-ttu-id="62fa6-188">Importy deklarovaná u konstruktor parametry jsou proto požadovaných importů, které musí všechny plnit před každý exporty z objektu, který vyžaduje je můžete použít.</span><span class="sxs-lookup"><span data-stu-id="62fa6-188">Imports declared on constructor parameters are therefore prerequisite imports, which must all be filled before any of the exports from the object that requires them can be used.</span></span>  
  
### <a name="optional-imports"></a><span data-ttu-id="62fa6-189">Volitelné importy</span><span class="sxs-lookup"><span data-stu-id="62fa6-189">Optional Imports</span></span>  
 <span data-ttu-id="62fa6-190">`Import` Atribut určuje požadavek pro část funkce.</span><span class="sxs-lookup"><span data-stu-id="62fa6-190">The `Import` attribute specifies a requirement for the part to function.</span></span> <span data-ttu-id="62fa6-191">Pokud nelze splnit importu, složení této části se nezdaří a části nebudete mít k dispozici.</span><span class="sxs-lookup"><span data-stu-id="62fa6-191">If an import cannot be fulfilled, the composition of that part will fail and the part will not be available.</span></span>  
  
 <span data-ttu-id="62fa6-192">Můžete určit, že bude importu *volitelné* pomocí `AllowDefault` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="62fa6-192">You can specify that an import is *optional* by using the `AllowDefault` property.</span></span> <span data-ttu-id="62fa6-193">V takovém případě bude složení úspěšné i v případě, že import neodpovídá žádné dostupné export a import vlastnost bude nastavena na výchozí hodnoty pro typ vlastnosti (`null` pro vlastnosti objektu `false` pro logických výrazů nebo nula pro číselné Vlastnosti.) Následující třídy používá volitelné importu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-193">In this case, the composition will succeed even if the import does not match any available exports, and the importing property will be set to the default for its property type (`null` for object properties, `false` for Booleans, or zero for numeric properties.) The following class uses an optional import.</span></span>  
  
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
  
### <a name="importing-multiple-objects"></a><span data-ttu-id="62fa6-194">Import více objektů</span><span class="sxs-lookup"><span data-stu-id="62fa6-194">Importing Multiple Objects</span></span>  
 <span data-ttu-id="62fa6-195">`Import` Atribut bude pouze úspěšně skládat při odpovídá pouze jeden export.</span><span class="sxs-lookup"><span data-stu-id="62fa6-195">The `Import` attribute will only be successfully composed when it matches one and only one export.</span></span> <span data-ttu-id="62fa6-196">Ostatních případech vygeneruje chyba složení.</span><span class="sxs-lookup"><span data-stu-id="62fa6-196">Other cases will produce a composition error.</span></span> <span data-ttu-id="62fa6-197">Chcete-li importovat více než jeden export, který odpovídá stejné smlouvy, použijte `ImportMany` atribut.</span><span class="sxs-lookup"><span data-stu-id="62fa6-197">To import more than one export that matches the same contract, use the `ImportMany` attribute.</span></span> <span data-ttu-id="62fa6-198">Importy označené jako tento atribut se vždycky volitelné.</span><span class="sxs-lookup"><span data-stu-id="62fa6-198">Imports marked with this attribute are always optional.</span></span> <span data-ttu-id="62fa6-199">Pokud jsou k dispozici žádné odpovídající exportuje se například nebudou složení.</span><span class="sxs-lookup"><span data-stu-id="62fa6-199">For example, composition will not fail if no matching exports are present.</span></span> <span data-ttu-id="62fa6-200">Následující třídy importuje libovolný počet exportuje typu `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-200">The following class imports any number of exports of type `IMyAddin`.</span></span>  
  
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
  
 <span data-ttu-id="62fa6-201">Importované pole je přístupná pomocí obyčejnou `IEnumerable<T>` syntaxe a metody.</span><span class="sxs-lookup"><span data-stu-id="62fa6-201">The imported array can be accessed by using ordinary `IEnumerable<T>` syntax and methods.</span></span> <span data-ttu-id="62fa6-202">Je také možné použít obyčejnou pole (`IMyAddin[]`) místo.</span><span class="sxs-lookup"><span data-stu-id="62fa6-202">It is also possible to use an ordinary array (`IMyAddin[]`) instead.</span></span>  
  
 <span data-ttu-id="62fa6-203">Tento vzor může být velmi důležité, pokud ji použít v kombinaci s `Lazy<T>` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="62fa6-203">This pattern can be very important when you use it in combination with the `Lazy<T>` syntax.</span></span> <span data-ttu-id="62fa6-204">Například pomocí `ImportMany`, `IEnumerable<T>`, a `Lazy<T>`, můžete importovat nepřímé odkazy na libovolný počet objektů a pouze ty, které se stanou nezbytnými doložit.</span><span class="sxs-lookup"><span data-stu-id="62fa6-204">For example, by using `ImportMany`, `IEnumerable<T>`, and `Lazy<T>`, you can import indirect references to any number of objects and only instantiate the ones that become necessary.</span></span> <span data-ttu-id="62fa6-205">Následující třídy ukazuje tento vzor.</span><span class="sxs-lookup"><span data-stu-id="62fa6-205">The following class shows this pattern.</span></span>  
  
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
## <a name="avoiding-discovery"></a><span data-ttu-id="62fa6-206">Zamezení zjišťování</span><span class="sxs-lookup"><span data-stu-id="62fa6-206">Avoiding Discovery</span></span>  
 <span data-ttu-id="62fa6-207">V některých případech můžete chtít zabránit části zjišťovat v rámci katalogu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-207">In some cases, you may want to prevent a part from being discovered as part of a catalog.</span></span> <span data-ttu-id="62fa6-208">Část může být například základní třída má od doby, ale nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="62fa6-208">For example, the part may be a base class intended to be inherited from, but not used.</span></span> <span data-ttu-id="62fa6-209">Existují dva způsoby, jak dosáhnout.</span><span class="sxs-lookup"><span data-stu-id="62fa6-209">There are two ways to accomplish this.</span></span> <span data-ttu-id="62fa6-210">První, můžete použít `abstract` – klíčové slovo k třídě část.</span><span class="sxs-lookup"><span data-stu-id="62fa6-210">First, you can use the `abstract` keyword on the part class.</span></span> <span data-ttu-id="62fa6-211">Abstraktní třídy nikdy zadejte exportuje, i když poskytují zděděné export do tříd, které vycházejí z nich.</span><span class="sxs-lookup"><span data-stu-id="62fa6-211">Abstract classes never provide exports, although they can provide inherited exports to classes that derive from them.</span></span>  
  
 <span data-ttu-id="62fa6-212">Pokud nemůže být provedena abstraktní třídu, můžete ho s uspořádání `PartNotDiscoverable` atribut.</span><span class="sxs-lookup"><span data-stu-id="62fa6-212">If the class cannot be made abstract, you can decorate it with the `PartNotDiscoverable` attribute.</span></span> <span data-ttu-id="62fa6-213">Součástí označených pomocí tento atribut nebude součástí žádné katalogů.</span><span class="sxs-lookup"><span data-stu-id="62fa6-213">A part decorated with this attribute will not be included in any catalogs.</span></span> <span data-ttu-id="62fa6-214">Následující příklad ukazuje tyto vzory.</span><span class="sxs-lookup"><span data-stu-id="62fa6-214">The following example demonstrates these patterns.</span></span> <span data-ttu-id="62fa6-215">`DataOne`Najde katalogu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-215">`DataOne` will be discovered by the catalog.</span></span> <span data-ttu-id="62fa6-216">Protože `DataTwo` je abstraktní, se nebudou vyhledány.</span><span class="sxs-lookup"><span data-stu-id="62fa6-216">Since `DataTwo` is abstract, it will not be discovered.</span></span> <span data-ttu-id="62fa6-217">Vzhledem k tomu `DataThree` použít `PartNotDiscoverable` atribut, nebudou vyhledány.</span><span class="sxs-lookup"><span data-stu-id="62fa6-217">Since `DataThree` used the `PartNotDiscoverable` attribute, it will not be discovered.</span></span>  
  
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
## <a name="metadata-and-metadata-views"></a><span data-ttu-id="62fa6-218">Metadata a zobrazení metadat</span><span class="sxs-lookup"><span data-stu-id="62fa6-218">Metadata and Metadata Views</span></span>  
 <span data-ttu-id="62fa6-219">Export může poskytovat další informace o samotné známé jako *metadata*.</span><span class="sxs-lookup"><span data-stu-id="62fa6-219">Exports can provide additional information about themselves known as *metadata*.</span></span> <span data-ttu-id="62fa6-220">Metadata slouží k předání informací o tom vlastnosti objektu exportovaný import část.</span><span class="sxs-lookup"><span data-stu-id="62fa6-220">Metadata can be used to convey properties of the exported object to the importing part.</span></span> <span data-ttu-id="62fa6-221">Tyto údaje můžete použít pro import část rozhodnout, který exportuje používat nebo shromažďovat informace o exportu bez nutnosti jej vytvořit.</span><span class="sxs-lookup"><span data-stu-id="62fa6-221">The importing part can use this data to decide which exports to use, or to gather information about an export without having to construct it.</span></span> <span data-ttu-id="62fa6-222">Z tohoto důvodu musí být importu opožděné používat metadata.</span><span class="sxs-lookup"><span data-stu-id="62fa6-222">For this reason, an import must be lazy to use metadata.</span></span>  
  
 <span data-ttu-id="62fa6-223">Použít metadata, je obvykle deklarovat rozhraní nazývá *zobrazení metadat*, který deklaruje, jaká metadata bude k dispozici.</span><span class="sxs-lookup"><span data-stu-id="62fa6-223">To use metadata, you typically declare an interface known as a *metadata view*, which declares what metadata will be available.</span></span> <span data-ttu-id="62fa6-224">Rozhraní metadat zobrazení musí mít pouze vlastnosti, a musí mít tyto vlastnosti `get` přistupující objekty.</span><span class="sxs-lookup"><span data-stu-id="62fa6-224">The metadata view interface must have only properties, and those properties must have `get` accessors.</span></span> <span data-ttu-id="62fa6-225">Následující rozhraní je zobrazení příkladu metadat.</span><span class="sxs-lookup"><span data-stu-id="62fa6-225">The following interface is an example metadata view.</span></span>  
  
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
  
 <span data-ttu-id="62fa6-226">Je také možné použít kolekci Obecné `IDictionary<string, object>`, jako zobrazení metadat, ale tím o výhody kontrola typu a je nutno.</span><span class="sxs-lookup"><span data-stu-id="62fa6-226">It is also possible to use a generic collection, `IDictionary<string, object>`, as a metadata view, but this forfeits the benefits of type checking and should be avoided.</span></span>  
  
 <span data-ttu-id="62fa6-227">Normálně všechny vlastnosti s názvem v zobrazení metadata jsou povinné a žádné export, které je neposkytují nebude být považovány za shodné.</span><span class="sxs-lookup"><span data-stu-id="62fa6-227">Ordinarily, all of the properties named in the metadata view are required, and any exports that do not provide them will not be considered a match.</span></span> <span data-ttu-id="62fa6-228">`DefaultValue` Atribut určuje, že vlastnost je volitelná.</span><span class="sxs-lookup"><span data-stu-id="62fa6-228">The `DefaultValue` attribute specifies that a property is optional.</span></span> <span data-ttu-id="62fa6-229">Pokud vlastnost není součástí, bude jí přiřazeno výchozí hodnota zadaná jako parametr funkce `DefaultValue`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-229">If the property is not included, it will be assigned the default value specified as a parameter of `DefaultValue`.</span></span> <span data-ttu-id="62fa6-230">Níže jsou uvedeny dva různé třídy dekorované s metadaty.</span><span class="sxs-lookup"><span data-stu-id="62fa6-230">The following are two different classes decorated with metadata.</span></span> <span data-ttu-id="62fa6-231">Obě tyto třídy odpovídá předchozí zobrazení metadat.</span><span class="sxs-lookup"><span data-stu-id="62fa6-231">Both of these classes would match the previous metadata view.</span></span>  
  
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
  
 <span data-ttu-id="62fa6-232">Metadata se vyjadřuje po `Export` atribut pomocí `ExportMetadata` atribut.</span><span class="sxs-lookup"><span data-stu-id="62fa6-232">Metadata is expressed after the `Export` attribute by using the `ExportMetadata` attribute.</span></span> <span data-ttu-id="62fa6-233">Každá část metadat se skládá z dvojice název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="62fa6-233">Each piece of metadata is composed of a name/value pair.</span></span> <span data-ttu-id="62fa6-234">Část názvu metadat musí odpovídat názvu příslušné vlastnosti v zobrazení metadat a hodnota se přiřadí této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="62fa6-234">The name portion of the metadata must match the name of the appropriate property in the metadata view, and the value will be assigned to that property.</span></span>  
  
 <span data-ttu-id="62fa6-235">Pokud existuje, bude používán je – Importér, která určuje, jaké zobrazení metadat.</span><span class="sxs-lookup"><span data-stu-id="62fa6-235">It is the importer that specifies what metadata view, if any, will be in use.</span></span> <span data-ttu-id="62fa6-236">Importu s metadaty je deklarován jako opožděné importu rozhraní metadat jako druhý parametr typu `Lazy<T,T>`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-236">An import with metadata is declared as a lazy import, with the metadata interface as the second type parameter to `Lazy<T,T>`.</span></span> <span data-ttu-id="62fa6-237">Následující třídy importuje předchozí část s metadaty.</span><span class="sxs-lookup"><span data-stu-id="62fa6-237">The following class imports the previous part with metadata.</span></span>  
  
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
  
 <span data-ttu-id="62fa6-238">V řadě případů budete chtít kombinovat metadat pomocí `ImportMany` atribut, aby bylo možné analyzovat prostřednictvím dostupné importy a vyberte a vytvořit pouze jednu instanci nebo filtrování kolekce splňují určité podmínky.</span><span class="sxs-lookup"><span data-stu-id="62fa6-238">In many cases, you will want to combine metadata with the `ImportMany` attribute, in order to parse through the available imports and choose and instantiate only one, or filter a collection to match a certain condition.</span></span> <span data-ttu-id="62fa6-239">Následující třídy vytvoří pouze `IPlugin` objekty, které mají `Name` hodnotu "Protokolovač".</span><span class="sxs-lookup"><span data-stu-id="62fa6-239">The following class instantiates only `IPlugin` objects that have the `Name` value "Logger".</span></span>  
  
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
## <a name="import-and-export-inheritance"></a><span data-ttu-id="62fa6-240">Import a Export dědičnosti</span><span class="sxs-lookup"><span data-stu-id="62fa6-240">Import and Export Inheritance</span></span>  
 <span data-ttu-id="62fa6-241">Pokud třídy dědí z části, této třídy může také stát součástí.</span><span class="sxs-lookup"><span data-stu-id="62fa6-241">If a class inherits from a part, that class may also become a part.</span></span> <span data-ttu-id="62fa6-242">Importy jsou vždy zděděny podtřídy.</span><span class="sxs-lookup"><span data-stu-id="62fa6-242">Imports are always inherited by subclasses.</span></span> <span data-ttu-id="62fa6-243">Proto podtřídou třídy součástí budou vždy částí, s stejné importy jako své nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="62fa6-243">Therefore, a subclass of a part will always be a part, with the same imports as its parent class.</span></span>  
  
 <span data-ttu-id="62fa6-244">Exportuje deklarovat pomocí `Export` atribut nejsou zdědí podtřídy.</span><span class="sxs-lookup"><span data-stu-id="62fa6-244">Exports declared by using the `Export` attribute are not inherited by subclasses.</span></span> <span data-ttu-id="62fa6-245">Však součástí můžete exportovat samotné pomocí `InheritedExport` atribut.</span><span class="sxs-lookup"><span data-stu-id="62fa6-245">However, a part can export itself by using the `InheritedExport` attribute.</span></span> <span data-ttu-id="62fa6-246">Podtřídy části bude dědit a zadejte stejné exportu, včetně názvu kontraktu a typ smlouvy.</span><span class="sxs-lookup"><span data-stu-id="62fa6-246">Subclasses of the part will inherit and provide the same export, including contract name and contract type.</span></span> <span data-ttu-id="62fa6-247">Na rozdíl od `Export` atribut `InheritedExport` lze použít pouze na úrovni třídy a nikoli na úrovni člena.</span><span class="sxs-lookup"><span data-stu-id="62fa6-247">Unlike an `Export` attribute, `InheritedExport` can be applied only at the class level, and not at the member level.</span></span> <span data-ttu-id="62fa6-248">Proto může být zděděna nikdy exportuje úrovni člena.</span><span class="sxs-lookup"><span data-stu-id="62fa6-248">Therefore, member-level exports can never be inherited.</span></span>  
  
 <span data-ttu-id="62fa6-249">Následující čtyři třídy předvedení zásady importu a exportu dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="62fa6-249">The following four classes demonstrate the principles of import and export inheritance.</span></span> <span data-ttu-id="62fa6-250">`NumTwo`dědí z `NumOne`, takže `NumTwo` naimportuje `IMyData`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-250">`NumTwo` inherits from `NumOne`, so `NumTwo` will import `IMyData`.</span></span> <span data-ttu-id="62fa6-251">Obyčejnou exportuje nedědí, takže `NumTwo` nebude nic exportovat.</span><span class="sxs-lookup"><span data-stu-id="62fa6-251">Ordinary exports are not inherited, so `NumTwo` will not export anything.</span></span> <span data-ttu-id="62fa6-252">`NumFour`dědí z `NumThree`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-252">`NumFour` inherits from `NumThree`.</span></span> <span data-ttu-id="62fa6-253">Protože `NumThree` používá `InheritedExport`, `NumFour` má jeden exportu s typ smlouvy `NumThree`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-253">Because `NumThree` used `InheritedExport`, `NumFour` has one export with contract type `NumThree`.</span></span> <span data-ttu-id="62fa6-254">Nikdy dědí exportuje úrovni člena, takže `IMyData` neexportoval.</span><span class="sxs-lookup"><span data-stu-id="62fa6-254">Member-level exports are never inherited, so `IMyData` is not exported.</span></span>  
  
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
  
 <span data-ttu-id="62fa6-255">Pokud je metadata přidružená `InheritedExport` atribut, aby metadata také zděděná.</span><span class="sxs-lookup"><span data-stu-id="62fa6-255">If there is metadata associated with an `InheritedExport` attribute, that metadata will also be inherited.</span></span> <span data-ttu-id="62fa6-256">(Další informace najdete v části "Metadata a zobrazení metadat" starší.) Zděděné metadata nelze změnit pomocí podtřídy.</span><span class="sxs-lookup"><span data-stu-id="62fa6-256">(For more information, see the earlier "Metadata and Metadata Views" section.) Inherited metadata cannot be modified by the subclass.</span></span> <span data-ttu-id="62fa6-257">Ale deklarováním znovu `InheritedExport` atribut se stejným názvem kontraktu a typ smlouvy, ale s novými metadaty podtřídy můžete nahradit zděděné metadata novými metadaty.</span><span class="sxs-lookup"><span data-stu-id="62fa6-257">However, by re-declaring the `InheritedExport` attribute with the same contract name and contract type, but with new metadata, the subclass can replace the inherited metadata with new metadata.</span></span> <span data-ttu-id="62fa6-258">Následující třídy ukazuje této zásady.</span><span class="sxs-lookup"><span data-stu-id="62fa6-258">The following class demonstrates this principle.</span></span> <span data-ttu-id="62fa6-259">`MegaLogger` Část dědí z `Logger` i `InheritedExport` atribut.</span><span class="sxs-lookup"><span data-stu-id="62fa6-259">The `MegaLogger` part inherits from `Logger` and includes the `InheritedExport` attribute.</span></span> <span data-ttu-id="62fa6-260">Vzhledem k tomu `MegaLogger` novými metadaty znovu deklaruje s názvem stav, nedědí název a verze metadata z `Logger`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-260">Since `MegaLogger` re-declares new metadata named Status, it does not inherit the Name and Version metadata from `Logger`.</span></span>  
  
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
  
 <span data-ttu-id="62fa6-261">Když znovu deklarace `InheritedExport` atribut přepsat metadata, ujistěte se, že typy kontraktů jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="62fa6-261">When re-declaring the `InheritedExport` attribute to override metadata, make sure that the contract types are the same.</span></span> <span data-ttu-id="62fa6-262">(V předchozím příkladu `IPlugin` je typ kontraktu.) Pokud se liší, místo přepsání, druhý atribut vytvoří druhý, nezávislé export z části.</span><span class="sxs-lookup"><span data-stu-id="62fa6-262">(In the previous example, `IPlugin` is the contract type.) If they differ, instead of overriding, the second attribute will create a second, independent export from the part.</span></span> <span data-ttu-id="62fa6-263">Obecně platí, to znamená, že budete mít k explicitnímu zadání typu kontraktu při přepsání `InheritedExport` atributu, jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-263">Generally, this means that you will have to explicitly specify the contract type when you override an `InheritedExport` attribute, as shown in the previous example.</span></span>  
  
 <span data-ttu-id="62fa6-264">Vzhledem k tomu, že rozhraní nemůže být přímo vytvořeny instance, se obecně nemůže být doplněny pomocí `Export` nebo `Import` atributy.</span><span class="sxs-lookup"><span data-stu-id="62fa6-264">Since interfaces cannot be instantiated directly, they generally cannot be decorated with `Export` or `Import` attributes.</span></span> <span data-ttu-id="62fa6-265">Ale rozhraní může být doplněny pomocí `InheritedExport` atribut na úrovni rozhraní, a že export společně s žádné přidružená metadata zdědí všechny implementující třídy.</span><span class="sxs-lookup"><span data-stu-id="62fa6-265">However, an interface can be decorated with an `InheritedExport` attribute at the interface level, and that export along with any associated metadata will be inherited by any implementing classes.</span></span> <span data-ttu-id="62fa6-266">Ale nebudete mít k dispozici v rámci rozhraní sám sebe.</span><span class="sxs-lookup"><span data-stu-id="62fa6-266">The interface itself will not be available as a part, however.</span></span>  
  
<a name="custom_export_attributes"></a>   
## <a name="custom-export-attributes"></a><span data-ttu-id="62fa6-267">Export vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="62fa6-267">Custom Export Attributes</span></span>  
 <span data-ttu-id="62fa6-268">Atributy základní export `Export` a `InheritedExport`, je možné rozšířit na obsahovat metadata jako atribut vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="62fa6-268">The basic export attributes, `Export` and `InheritedExport`, can be extended to include metadata as attribute properties.</span></span> <span data-ttu-id="62fa6-269">Tato metoda je užitečná pro použití podobné metadata pro mnoho částí nebo vytváření ve stromu dědičnosti metadata atributů.</span><span class="sxs-lookup"><span data-stu-id="62fa6-269">This technique is useful for applying similar metadata to many parts, or creating an inheritance tree of metadata attributes.</span></span>  
  
 <span data-ttu-id="62fa6-270">Vlastní atribut můžete určit typ smlouvy, název kontraktu nebo další metadata.</span><span class="sxs-lookup"><span data-stu-id="62fa6-270">A custom attribute can specify the contract type, the contract name, or any other metadata.</span></span> <span data-ttu-id="62fa6-271">Aby bylo možné definovat vlastní atribut, která dědí z třídy `ExportAttribute` (nebo `InheritedExportAttribute`) musí být doplněny pomocí `MetadataAttribute` atribut.</span><span class="sxs-lookup"><span data-stu-id="62fa6-271">In order to define a custom attribute, a class inheriting from `ExportAttribute` (or `InheritedExportAttribute`) must be decorated with the `MetadataAttribute` attribute.</span></span> <span data-ttu-id="62fa6-272">Následující třídy definuje vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="62fa6-272">The following class defines a custom attribute.</span></span>  
  
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
  
 <span data-ttu-id="62fa6-273">Tato třída definuje vlastní atribut s názvem `MyAttribute` s typem kontraktu `IMyData` a některé metadat s názvem `MyMetadata`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-273">This class defines a custom attribute named `MyAttribute` with contract type `IMyData` and some metadata named `MyMetadata`.</span></span> <span data-ttu-id="62fa6-274">Všechny vlastnosti v třídě označené jako `MetadataAttribute` atribut se považují za metadata definované ve vlastním atributu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-274">All properties in a class marked with the `MetadataAttribute` attribute are considered to be metadata defined in the custom attribute.</span></span> <span data-ttu-id="62fa6-275">Následující dva deklarace jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="62fa6-275">The following two declarations are equivalent.</span></span>  
  
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
  
 <span data-ttu-id="62fa6-276">V první deklaraci typu kontraktu a metadata jsou explicitně definovány.</span><span class="sxs-lookup"><span data-stu-id="62fa6-276">In the first declaration, the contract type and metadata are explicitly defined.</span></span> <span data-ttu-id="62fa6-277">V druhé deklaraci typu kontraktu a metadata jsou implicitní ve vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="62fa6-277">In the second declaration, the contract type and metadata are implicit in the customized attribute.</span></span> <span data-ttu-id="62fa6-278">Zvláště v případech, kdy musí být velké množství identické metadata používá pro mnoho částí (například autora nebo informace o autorských právech) můžete pomocí vlastní atribut uložit spoustu času a duplicita.</span><span class="sxs-lookup"><span data-stu-id="62fa6-278">Particularly in cases where a large amount of identical metadata must be applied to many parts (for example, author or copyright information), using a custom attribute can save a lot of time and duplication.</span></span> <span data-ttu-id="62fa6-279">Navíc dědičnosti stromy vlastních atributů vytvořením umožňující variace.</span><span class="sxs-lookup"><span data-stu-id="62fa6-279">Further, inheritance trees of custom attributes can be created to allow for variations.</span></span>  
  
 <span data-ttu-id="62fa6-280">Pokud chcete vytvořit volitelná metadata ve vlastním atributu, můžete použít `DefaultValue` atribut.</span><span class="sxs-lookup"><span data-stu-id="62fa6-280">To create optional metadata in a custom attribute, you can use the `DefaultValue` attribute.</span></span> <span data-ttu-id="62fa6-281">Když tento atribut se použije k vlastnosti ve třídě vlastních atributů, určuje to, že dekorované vlastnost je volitelná a nemá být poskytl exportu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-281">When this attribute is applied to a property in a custom attribute class, it specifies that the decorated property is optional and does not have to be supplied by an exporter.</span></span> <span data-ttu-id="62fa6-282">Pokud není zadána hodnota pro vlastnost, bude jí přiřazeno výchozí hodnota pro typ vlastnosti (obvykle `null`, `false`, nebo 0.)</span><span class="sxs-lookup"><span data-stu-id="62fa6-282">If a value for the property is not supplied, it will be assigned the default value for its property type (usually `null`, `false`, or 0.)</span></span>  
  
<a name="creation_policies"></a>   
## <a name="creation-policies"></a><span data-ttu-id="62fa6-283">Vytvoření zásad</span><span class="sxs-lookup"><span data-stu-id="62fa6-283">Creation Policies</span></span>  
 <span data-ttu-id="62fa6-284">Když součást určuje importu a složení se provádí, kontejneru složení se pokusí najít odpovídající export.</span><span class="sxs-lookup"><span data-stu-id="62fa6-284">When a part specifies an import and composition is performed, the composition container attempts to find a matching export.</span></span> <span data-ttu-id="62fa6-285">Pokud ho importovat s exportu odpovídá úspěšně, import člen je nastavena na instanci exportovaný objektu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-285">If it matches the import with an export successfully, the importing member is set to an instance of the exported object.</span></span> <span data-ttu-id="62fa6-286">Kde se tato instance pochází z řídí export části *vytvoření zásad*.</span><span class="sxs-lookup"><span data-stu-id="62fa6-286">Where this instance comes from is controlled by the exporting part's *creation policy*.</span></span>  
  
 <span data-ttu-id="62fa6-287">Jsou dvě možné vytvoření zásady, které *sdílené* a *nesdílené*.</span><span class="sxs-lookup"><span data-stu-id="62fa6-287">The two possible creation policies are *shared* and *non-shared*.</span></span> <span data-ttu-id="62fa6-288">Součástí zásadám vytváření sdílených bude možné sdílet mezi každých importu v kontejneru pro část s tohoto kontraktu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-288">A part with a creation policy of shared will be shared between every import in the container for a part with that contract.</span></span> <span data-ttu-id="62fa6-289">Pokud modul složení najde shoda a má nastavit vlastnost import, ji pouze v případě, že již neexistuje, vytvoří instanci novou kopii části jinak poskytne existující kopie.</span><span class="sxs-lookup"><span data-stu-id="62fa6-289">When the composition engine finds a match and has to set an importing property, it will instantiate a new copy of the part only if one does not already exist; otherwise, it will supply the existing copy.</span></span> <span data-ttu-id="62fa6-290">To znamená, že mnoho objektů, může mít odkazy na stejnou část.</span><span class="sxs-lookup"><span data-stu-id="62fa6-290">This means that many objects may have references to the same part.</span></span> <span data-ttu-id="62fa6-291">Tyto části neměli spoléhat na vnitřní stav, který může být změněn z mnoha místech.</span><span class="sxs-lookup"><span data-stu-id="62fa6-291">Such parts should not rely on internal state that might be changed from many places.</span></span> <span data-ttu-id="62fa6-292">Tato zásada je vhodné pro statické části, částí, které poskytují služby a částí, které využívají velké množství paměti nebo jiných prostředků.</span><span class="sxs-lookup"><span data-stu-id="62fa6-292">This policy is appropriate for static parts, parts that provide services, and parts that consume a lot of memory or other resources.</span></span>  
  
 <span data-ttu-id="62fa6-293">Část zásadám vytváření nesdílené vytvoří pokaždé, když je nalezen odpovídající import jednoho z jeho export.</span><span class="sxs-lookup"><span data-stu-id="62fa6-293">A part with the creation policy of non-shared will be created every time a matching import for one of its exports is found.</span></span> <span data-ttu-id="62fa6-294">Nové kopie bude vytvořena instance proto pro každý import v kontejneru, který odpovídá jednomu z exportovaný kontrakty pro část.</span><span class="sxs-lookup"><span data-stu-id="62fa6-294">A new copy will therefore be instantiated for every import in the container that matches one of the part's exported contracts.</span></span> <span data-ttu-id="62fa6-295">Vnitřní stav tyto kopie se sdílet nebude.</span><span class="sxs-lookup"><span data-stu-id="62fa6-295">The internal state of these copies will not be shared.</span></span> <span data-ttu-id="62fa6-296">Tato zásada je vhodná pro části, kde každý importu vyžaduje vlastní vnitřní stav.</span><span class="sxs-lookup"><span data-stu-id="62fa6-296">This policy is appropriate for parts where each import requires its own internal state.</span></span>  
  
 <span data-ttu-id="62fa6-297">Import a export můžete zadat zásady vytváření druhé, některé z těchto hodnot `Shared`, `NonShared`, nebo `Any`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-297">Both the import and the export can specify the creation policy of a part, from among the values `Shared`, `NonShared`, or `Any`.</span></span> <span data-ttu-id="62fa6-298">Výchozí hodnota je `Any` pro obě importuje a exportuje.</span><span class="sxs-lookup"><span data-stu-id="62fa6-298">The default is `Any` for both imports and exports.</span></span> <span data-ttu-id="62fa6-299">Exportu, která určuje `Shared` nebo `NonShared` bude odpovídá pouze importu stejné, nebo určuje určující `Any`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-299">An export that specifies `Shared` or `NonShared` will only match an import that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="62fa6-300">Podobně, která určuje importu `Shared` nebo `NonShared` bude odpovídá pouze exportu stejné, nebo určuje určující `Any`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-300">Similarly, an import that specifies `Shared` or `NonShared` will only match an export that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="62fa6-301">Import a export zásadám nekompatibilní vytvoření nejsou považovány za shodné, stejným způsobem jako import a export, jejíž název nebo kontrakt typ smlouvy nejsou shody.</span><span class="sxs-lookup"><span data-stu-id="62fa6-301">Imports and exports with incompatible creation policies are not considered a match, in the same way as an import and export whose contract name or contract type are not a match.</span></span> <span data-ttu-id="62fa6-302">Pokud import a export zadat `Any`, nebo nezadávejte vytvoření zásad a výchozí `Any`, vytvoření zásady, bude použita výchozí sdílet.</span><span class="sxs-lookup"><span data-stu-id="62fa6-302">If both import and export specify `Any`, or do not specify a creation policy and default to `Any`, the creation policy will default to shared.</span></span>  
  
 <span data-ttu-id="62fa6-303">Následující příklad ukazuje, import a export zadání vytvoření zásady.</span><span class="sxs-lookup"><span data-stu-id="62fa6-303">The following example shows both imports and exports specifying creation policies.</span></span> <span data-ttu-id="62fa6-304">`PartOne`neurčuje vytvoření zásady, takže výchozí hodnota je `Any`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-304">`PartOne` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="62fa6-305">`PartTwo`neurčuje vytvoření zásady, takže výchozí hodnota je `Any`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-305">`PartTwo` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="62fa6-306">Vzhledem k tomu, jak importovat a exportovat výchozí nastavení `Any`, `PartOne` budou sdílet.</span><span class="sxs-lookup"><span data-stu-id="62fa6-306">Since both import and export default to `Any`, `PartOne` will be shared.</span></span> <span data-ttu-id="62fa6-307">`PartThree`Určuje `Shared` vytvoření zásady, takže `PartTwo` a `PartThree` budou sdílet stejnou kopii `PartOne`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-307">`PartThree` specifies a `Shared` creation policy, so `PartTwo` and `PartThree` will share the same copy of `PartOne`.</span></span> <span data-ttu-id="62fa6-308">`PartFour`Určuje `NonShared` vytvoření zásady, takže `PartFour` bude nesdílené v `PartFive`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-308">`PartFour` specifies a `NonShared` creation policy, so `PartFour` will be non-shared in `PartFive`.</span></span> <span data-ttu-id="62fa6-309">`PartSix`Určuje `NonShared` vytváření zásad.</span><span class="sxs-lookup"><span data-stu-id="62fa6-309">`PartSix` specifies a `NonShared` creation policy.</span></span> <span data-ttu-id="62fa6-310">`PartFive`a `PartSix` obdrží každou samostatnou kopii `PartFour`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-310">`PartFive` and `PartSix` will each receive separate copies of `PartFour`.</span></span> <span data-ttu-id="62fa6-311">`PartSeven`Určuje `Shared` vytváření zásad.</span><span class="sxs-lookup"><span data-stu-id="62fa6-311">`PartSeven` specifies a `Shared` creation policy.</span></span> <span data-ttu-id="62fa6-312">Protože je ne exportovat `PartFour` s vytvoření zásady `Shared`, `PartSeven` import neodpovídá nic a nesmí být vyplněna.</span><span class="sxs-lookup"><span data-stu-id="62fa6-312">Because there is no exported `PartFour` with a creation policy of `Shared`, the `PartSeven` import does not match anything and will not be filled.</span></span>  
  
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
## <a name="life-cycle-and-disposing"></a><span data-ttu-id="62fa6-313">Životní cyklus a uvolnění</span><span class="sxs-lookup"><span data-stu-id="62fa6-313">Life Cycle and Disposing</span></span>  
 <span data-ttu-id="62fa6-314">Vzhledem k součásti jsou hostované v kontejneru složení, může být složitější než obyčejnou objekty jejich životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="62fa6-314">Because parts are hosted in the composition container, their life cycle can be more complex than ordinary objects.</span></span> <span data-ttu-id="62fa6-315">Části můžete implementovat dvě důležité rozhraní související s životní cyklus: `IDisposable` a `IPartImportsSatisfiedNotification`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-315">Parts can implement two important life cycle-related interfaces: `IDisposable` and `IPartImportsSatisfiedNotification`.</span></span>  
  
 <span data-ttu-id="62fa6-316">Částí, které vyžadují, aby se provést na vypnutí dolů nebo které potřebujete k uvolnění prostředků by měla implementovat `IDisposable`, pro objekty rozhraní .NET Framework jako obvykle.</span><span class="sxs-lookup"><span data-stu-id="62fa6-316">Parts that require work to be performed at shut down or that need to release resources should implement `IDisposable`, as usual for .NET Framework objects.</span></span> <span data-ttu-id="62fa6-317">Ale vzhledem k tomu, že kontejner vytvoří a udržuje odkazy na části, pouze kontejneru, který vlastní část by měly volat `Dispose` metoda na něm.</span><span class="sxs-lookup"><span data-stu-id="62fa6-317">However, since the container creates and maintains references to parts, only the container that owns a part should call the `Dispose` method on it.</span></span> <span data-ttu-id="62fa6-318">Implementuje kontejneru samotné `IDisposable`a jako část jeho vyčištění v `Dispose` bude volat `Dispose` na všechny části, které je vlastní.</span><span class="sxs-lookup"><span data-stu-id="62fa6-318">The container itself implements `IDisposable`, and as portion of its cleanup in `Dispose` it will call `Dispose` on all the parts that it owns.</span></span> <span data-ttu-id="62fa6-319">Z tohoto důvodu by měl vždycky dispose kontejneru složení, když ho a částí, které vlastní už nejsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="62fa6-319">For this reason, you should always dispose the composition container when it and any parts it owns are no longer needed.</span></span>  
  
 <span data-ttu-id="62fa6-320">Pro kontejnery dlohotrvající složení částí zásadám vytváření nesdílené spotřeba paměti se může stát problém.</span><span class="sxs-lookup"><span data-stu-id="62fa6-320">For long-lived composition containers, memory consumption by parts with a creation policy of non-shared can become a problem.</span></span> <span data-ttu-id="62fa6-321">Tyto části nesdílené lze vytvořit více než jednou a nebude uvolněno, dokud je zveřejněn kontejneru sám sebe.</span><span class="sxs-lookup"><span data-stu-id="62fa6-321">These non-shared parts can be created multiple times and will not be disposed until the container itself is disposed.</span></span> <span data-ttu-id="62fa6-322">Zpracovat takové, poskytuje kontejner `ReleaseExport` metoda.</span><span class="sxs-lookup"><span data-stu-id="62fa6-322">To deal with this, the container provides the `ReleaseExport` method.</span></span> <span data-ttu-id="62fa6-323">Voláním této metody na export nesdíleného odebere tento export z kontejneru složení a zruší ho.</span><span class="sxs-lookup"><span data-stu-id="62fa6-323">Calling this method on a non-shared export removes that export from the composition container and disposes it.</span></span> <span data-ttu-id="62fa6-324">Částí, které jsou používány pouze odebrané exportu, a tak dále hlouběji ve stromové struktuře, se taky odeberou a zlikvidován.</span><span class="sxs-lookup"><span data-stu-id="62fa6-324">Parts that are used only by the removed export, and so on down the tree, are also removed and disposed.</span></span> <span data-ttu-id="62fa6-325">Tímto způsobem se nedá uvolnit prostředky bez uvolnění kontejneru složení sám sebe.</span><span class="sxs-lookup"><span data-stu-id="62fa6-325">In this way, resources can be reclaimed without disposing the composition container itself.</span></span>  
  
 <span data-ttu-id="62fa6-326">`IPartImportsSatisfiedNotification`obsahuje jednu metodu s názvem `OnImportsSatisfied`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-326">`IPartImportsSatisfiedNotification` contains one method named `OnImportsSatisfied`.</span></span> <span data-ttu-id="62fa6-327">Tato metoda je volána kontejneru složení na všechny části, které implementují rozhraní při dokončení složení a rámci importy jsou připravené k použití.</span><span class="sxs-lookup"><span data-stu-id="62fa6-327">This method is called by the composition container on any parts that implement the interface when composition has been completed and the part's imports are ready for use.</span></span> <span data-ttu-id="62fa6-328">Části jsou vytvořené pomocí modulu složení k vyplnění importy dalších částí.</span><span class="sxs-lookup"><span data-stu-id="62fa6-328">Parts are created by the composition engine to fill the imports of other parts.</span></span> <span data-ttu-id="62fa6-329">Před importy části byly nastaveny, nelze provést všechny inicializace, který využívá nebo manipuluje importované hodnoty v rámci konstruktoru, pokud tyto hodnoty mají byl zadán jako požadavky pomocí `ImportingConstructor` atribut.</span><span class="sxs-lookup"><span data-stu-id="62fa6-329">Before the imports of a part have been set, you cannot perform any initialization that relies on or manipulates imported values in the part constructor unless those values have been specified as prerequisites by using the `ImportingConstructor` attribute.</span></span> <span data-ttu-id="62fa6-330">To je obvykle upřednostňovanou metodou, ale v některých případech vkládání konstruktor nemusí být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="62fa6-330">This is normally the preferred method, but in some cases, constructor injection may not be available.</span></span> <span data-ttu-id="62fa6-331">V takových případech lze provést inicializaci v `OnImportsSatisfied`, a měly by implementovat části `IPartImportsSatisfiedNotification`.</span><span class="sxs-lookup"><span data-stu-id="62fa6-331">In those cases, initialization can be performed in `OnImportsSatisfied`, and the part should implement `IPartImportsSatisfiedNotification`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62fa6-332">Viz také</span><span class="sxs-lookup"><span data-stu-id="62fa6-332">See Also</span></span>  
 [<span data-ttu-id="62fa6-333">Video Channel 9: Otevře aplikace s použitím spravovaných rozšíření Framework</span><span class="sxs-lookup"><span data-stu-id="62fa6-333">Channel 9 Video: Open Up Your Applications with the Managed Extensibility Framework</span></span>](http://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)  
 [<span data-ttu-id="62fa6-334">Video Channel 9: Spravovaných rozšíření Framework (MEF) 2.0</span><span class="sxs-lookup"><span data-stu-id="62fa6-334">Channel 9 Video: Managed Extensibility Framework (MEF) 2.0</span></span>](http://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)

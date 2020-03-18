---
title: Řešení zavedení sestavení
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], resolving loads
- application domains, loading assemblies
- resolving assembly loads
- assemblies [.NET Framework], loading
- application domains, resolving assembly loads
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: d6314fae266505fbb4410aaaa351973070ab3811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156436"
---
# <a name="resolve-assembly-loads"></a><span data-ttu-id="45495-102">Řešení zavedení sestavení</span><span class="sxs-lookup"><span data-stu-id="45495-102">Resolve assembly loads</span></span>
<span data-ttu-id="45495-103">Rozhraní .NET <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> poskytuje událost pro aplikace, které vyžadují větší kontrolu nad načítánísestavení.</span><span class="sxs-lookup"><span data-stu-id="45495-103">.NET provides the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event for applications that require greater control over assembly loading.</span></span> <span data-ttu-id="45495-104">Zpracováním této události aplikace můžete načíst sestavení do kontextu zatížení z mimo normální sondování cesty, vyberte, které z několika verzí sestavení načíst, vyzařují dynamické sestavení a vrátit ji a tak dále.</span><span class="sxs-lookup"><span data-stu-id="45495-104">By handling this event, your application can load an assembly into the load context from outside the normal probing paths, select which of several assembly versions to load, emit a dynamic assembly and return it, and so on.</span></span> <span data-ttu-id="45495-105">Toto téma obsahuje <xref:System.AppDomain.AssemblyResolve> pokyny pro zpracování události.</span><span class="sxs-lookup"><span data-stu-id="45495-105">This topic provides guidance for handling the <xref:System.AppDomain.AssemblyResolve> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45495-106">Pro řešení zatížení sestavy v kontextu pouze <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> reflexe použijte místo toho událost.</span><span class="sxs-lookup"><span data-stu-id="45495-106">For resolving assembly loads in the reflection-only context, use the <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> event instead.</span></span>  
  
## <a name="how-the-assemblyresolve-event-works"></a><span data-ttu-id="45495-107">Jak funguje událost AssemblyResolve</span><span class="sxs-lookup"><span data-stu-id="45495-107">How the AssemblyResolve event works</span></span>  
 <span data-ttu-id="45495-108">Při registraci obslužné rutiny <xref:System.AppDomain.AssemblyResolve> pro událost je obslužná rutina vyvolána vždy, když se runtime nepodaří vytvořit vazbu na sestavení podle názvu.</span><span class="sxs-lookup"><span data-stu-id="45495-108">When you register a handler for the <xref:System.AppDomain.AssemblyResolve> event, the handler is invoked whenever the runtime fails to bind to an assembly by name.</span></span> <span data-ttu-id="45495-109">Například volání následující metody z uživatelského <xref:System.AppDomain.AssemblyResolve> kódu může způsobit, že událost má být vyvolána:</span><span class="sxs-lookup"><span data-stu-id="45495-109">For example, calling the following methods from user code can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised:</span></span>  
  
- <span data-ttu-id="45495-110">Přetížení <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> nebo přetížení metody, jehož první argument je řetězec, který představuje zobrazovaný název <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> sestavení načíst (to znamená řetězec vrácený vlastností).</span><span class="sxs-lookup"><span data-stu-id="45495-110">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is a string that represents the display name of the assembly to load (that is, the string returned by the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property).</span></span>  
  
- <span data-ttu-id="45495-111">Přetížení <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> nebo přetížení metody, <xref:System.Reflection.AssemblyName> jehož první argument je objekt, který identifikuje sestavení načíst.</span><span class="sxs-lookup"><span data-stu-id="45495-111">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is an <xref:System.Reflection.AssemblyName> object that identifies the assembly to load.</span></span>  
  
- <span data-ttu-id="45495-112">Přetížení <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="45495-112">An <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> method overload.</span></span>  
  
- <span data-ttu-id="45495-113">Přetížení <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> metody nebo metody, které inkonzisuje objekt v jiné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="45495-113">An <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> method overload that instantiates an object in another application domain.</span></span>  
  
### <a name="what-the-event-handler-does"></a><span data-ttu-id="45495-114">Co obslužná rutina události dělá</span><span class="sxs-lookup"><span data-stu-id="45495-114">What the event handler does</span></span>  
 <span data-ttu-id="45495-115">Obslužná rutina <xref:System.AppDomain.AssemblyResolve> události obdrží zobrazovaný název sestavení, které má být načteno, ve vlastnosti. <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="45495-115">The handler for the <xref:System.AppDomain.AssemblyResolve> event receives the display name of the assembly to be loaded, in the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="45495-116">Pokud obslužná rutina nerozpozná název sestavení, vrátí `null` (C#), `Nothing` (Visual Basic) nebo `nullptr` (Visual C++).</span><span class="sxs-lookup"><span data-stu-id="45495-116">If the handler does not recognize the assembly name, it returns `null` (C#), `Nothing` (Visual Basic), or `nullptr` (Visual C++).</span></span>  
  
 <span data-ttu-id="45495-117">Pokud obslužná rutina rozpozná název sestavení, může načíst a vrátit sestavení, které splňuje požadavek.</span><span class="sxs-lookup"><span data-stu-id="45495-117">If the handler recognizes the assembly name, it can load and return an assembly that satisfies the request.</span></span> <span data-ttu-id="45495-118">Následující seznam popisuje některé ukázkové scénáře.</span><span class="sxs-lookup"><span data-stu-id="45495-118">The following list describes some sample scenarios.</span></span>  
  
- <span data-ttu-id="45495-119">Pokud obslužná rutina zná umístění verze sestavení, může <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> načíst sestavení pomocí metody nebo a může vrátit načtené sestavení, pokud je úspěšné.</span><span class="sxs-lookup"><span data-stu-id="45495-119">If the handler knows the location of a version of the assembly, it can load the assembly by using the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> method, and can return the loaded assembly if successful.</span></span>  
  
- <span data-ttu-id="45495-120">Pokud obslužná rutina má přístup k databázi sestavení uložených jako bajtová <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> pole, může načíst bajtové pole pomocí jednoho z přetížení metody, které berou bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="45495-120">If the handler has access to a database of assemblies stored as byte arrays, it can load a byte array by using one of the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that take a byte array.</span></span>  
  
- <span data-ttu-id="45495-121">Obslužná rutina může generovat dynamické sestavení a vrátit ji.</span><span class="sxs-lookup"><span data-stu-id="45495-121">The handler can generate a dynamic assembly and return it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45495-122">Obslužná rutina musí načíst sestavení do kontextu load-from, do kontextu zatížení nebo bez kontextu. Pokud obslužná rutina načte sestavení <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> do <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> kontextu pouze reflexe <xref:System.AppDomain.AssemblyResolve> pomocí nebo metody, pokus o načtení, který vyvolal událost nezdaří.</span><span class="sxs-lookup"><span data-stu-id="45495-122">The handler must load the assembly into the load-from context, into the load context, or without context.If the handler loads the assembly into the reflection-only context by using the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> method, the load attempt that raised the <xref:System.AppDomain.AssemblyResolve> event fails.</span></span>  
  
 <span data-ttu-id="45495-123">Je odpovědností obslužné rutiny události vrátit vhodné sestavení.</span><span class="sxs-lookup"><span data-stu-id="45495-123">It is the responsibility of the event handler to return a suitable assembly.</span></span> <span data-ttu-id="45495-124">Obslužná rutina může analyzovat zobrazovaný <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> název požadovaného sestavení předáním hodnoty vlastnosti konstruktoru. <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29></span><span class="sxs-lookup"><span data-stu-id="45495-124">The handler can parse the display name of the requested assembly by passing the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property value to the <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> constructor.</span></span> <span data-ttu-id="45495-125">Počínaje rozhraním .NET Framework 4 může <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> obslužná rutina použít vlastnost k určení, zda je aktuální požadavek závislostí jiného sestavení.</span><span class="sxs-lookup"><span data-stu-id="45495-125">Beginning with the .NET Framework 4, the handler can use the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property to determine whether the current request is a dependency of another assembly.</span></span> <span data-ttu-id="45495-126">Tyto informace mohou pomoci identifikovat sestavení, které bude splňovat závislost.</span><span class="sxs-lookup"><span data-stu-id="45495-126">This information can help identify an assembly that will satisfy the dependency.</span></span>  
  
 <span data-ttu-id="45495-127">Obslužná rutina události může vrátit jinou verzi sestavení než verze, která byla požadována.</span><span class="sxs-lookup"><span data-stu-id="45495-127">The event handler can return a different version of the assembly than the version that was requested.</span></span>  
  
 <span data-ttu-id="45495-128">Ve většině případů se sestavení, které je vráceno obslužnou rutinou, zobrazí v kontextu zatížení bez ohledu na kontext, do kterého ji obslužná rutina načte.</span><span class="sxs-lookup"><span data-stu-id="45495-128">In most cases, the assembly that is returned by the handler appears in the load context, regardless of the context the handler loads it into.</span></span> <span data-ttu-id="45495-129">Například pokud obslužná rutina používá metodu <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> k načtení sestavení do kontextu load-from, sestavení se zobrazí v kontextu zatížení, když ho obslužná rutina vrátí.</span><span class="sxs-lookup"><span data-stu-id="45495-129">For example, if the handler uses the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method to load an assembly into the load-from context, the assembly appears in the load context when the handler returns it.</span></span> <span data-ttu-id="45495-130">V následujícím případě se však sestavení zobrazí bez kontextu, když jej obslužná rutina vrátí:</span><span class="sxs-lookup"><span data-stu-id="45495-130">However, in the following case the assembly appears without context when the handler returns it:</span></span>  
  
- <span data-ttu-id="45495-131">Obslužná rutina načte sestavení bez kontextu.</span><span class="sxs-lookup"><span data-stu-id="45495-131">The handler loads an assembly without context.</span></span>  
  
- <span data-ttu-id="45495-132">Vlastnost <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> není null.</span><span class="sxs-lookup"><span data-stu-id="45495-132">The <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property is not null.</span></span>  
  
- <span data-ttu-id="45495-133">Žádající sestavení (to znamená sestavení, které <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> je vráceno vlastností) bylo načteno bez kontextu.</span><span class="sxs-lookup"><span data-stu-id="45495-133">The requesting assembly (that is, the assembly that is returned by the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property) was loaded without context.</span></span>  
  
 <span data-ttu-id="45495-134">Informace o kontextech naleznete <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> v tématu přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="45495-134">For information about contexts, see the <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> method overload.</span></span>  
  
 <span data-ttu-id="45495-135">Do stejné domény aplikace lze načíst více verzí stejného sestavení.</span><span class="sxs-lookup"><span data-stu-id="45495-135">Multiple versions of the same assembly can be loaded into the same application domain.</span></span> <span data-ttu-id="45495-136">Tento postup se nedoporučuje, protože může vést k problémům přiřazení typu.</span><span class="sxs-lookup"><span data-stu-id="45495-136">This practice is not recommended, because it can lead to type assignment problems.</span></span> <span data-ttu-id="45495-137">Viz [Doporučené postupy pro načítání sestavy](../../framework/deployment/best-practices-for-assembly-loading.md).</span><span class="sxs-lookup"><span data-stu-id="45495-137">See [Best practices for assembly loading](../../framework/deployment/best-practices-for-assembly-loading.md).</span></span>  
  
### <a name="what-the-event-handler-should-not-do"></a><span data-ttu-id="45495-138">Co by obslužná rutina události neměla dělat</span><span class="sxs-lookup"><span data-stu-id="45495-138">What the event handler should not do</span></span>  
<span data-ttu-id="45495-139">Primární pravidlo pro <xref:System.AppDomain.AssemblyResolve> zpracování události je, že byste se neměli pokoušet vrátit sestavení, které nepoznáváte.</span><span class="sxs-lookup"><span data-stu-id="45495-139">The primary rule for handling the <xref:System.AppDomain.AssemblyResolve> event is that you should not try to return an assembly you do not recognize.</span></span> <span data-ttu-id="45495-140">Při psaní obslužné rutiny byste měli vědět, která sestavení mohou způsobit vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="45495-140">When you write the handler, you should know which assemblies might cause the event to be raised.</span></span> <span data-ttu-id="45495-141">Obslužná rutina by měla vrátit hodnotu null pro jiná sestavení.</span><span class="sxs-lookup"><span data-stu-id="45495-141">Your handler should return null for other assemblies.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="45495-142">Počínaje rozhraním .NET Framework <xref:System.AppDomain.AssemblyResolve> 4 je událost vyvolána pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="45495-142">Beginning with the .NET Framework 4, the <xref:System.AppDomain.AssemblyResolve> event is raised for satellite assemblies.</span></span> <span data-ttu-id="45495-143">Tato změna ovlivní obslužnou rutinu události, která byla napsána pro starší verzi rozhraní .NET Framework, pokud se obslužná rutina pokusí vyřešit všechny požadavky na zatížení sestavení.</span><span class="sxs-lookup"><span data-stu-id="45495-143">This change affects an event handler that was written for an earlier version of the .NET Framework, if the handler tries to resolve all assembly load requests.</span></span> <span data-ttu-id="45495-144">Obslužné rutiny událostí, které ignorují sestavení, která nerozpoznávají, nejsou touto změnou ovlivněny: Vrátí hodnotu null a budou následovat normální záložní mechanismy.</span><span class="sxs-lookup"><span data-stu-id="45495-144">Event handlers that ignore assemblies they do not recognize are not affected by this change: They return null, and normal fallback mechanisms are followed.</span></span>  

<span data-ttu-id="45495-145">Při načítání sestavení obslužná rutina <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> události nesmí používat žádné <xref:System.AppDomain.AssemblyResolve> přetížení metody nebo metody, které může způsobit, že událost bude vyvolána rekurzivně, protože to může vést k přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="45495-145">When loading an assembly, the event handler must not use any of the <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised recursively, because this can lead to a stack overflow.</span></span> <span data-ttu-id="45495-146">(Viz seznam uvedený výše v tomto tématu.) K tomu dochází i v případě, že poskytujete zpracování výjimek pro požadavek na načtení, protože není vyvolána žádná výjimka, dokud se nevrátí všechny obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="45495-146">(See the list provided earlier in this topic.) This happens even if you provide exception handling for the load request, because no exception is thrown until all event handlers have returned.</span></span> <span data-ttu-id="45495-147">Následující kód má za následek přetečení zásobníku, pokud `MyAssembly` není nalezen:</span><span class="sxs-lookup"><span data-stu-id="45495-147">Thus, the following code results in a stack overflow if `MyAssembly` is not found:</span></span>  

```cpp
using namespace System;
using namespace System::Reflection;

ref class Example
{
internal:
    static Assembly^ MyHandler(Object^ source, ResolveEventArgs^ e)
    {
        Console::WriteLine("Resolving {0}", e->Name);
        return Assembly::Load(e->Name);
    }
};

void main()
{
    AppDomain^ ad = AppDomain::CreateDomain("Test");
    ad->AssemblyResolve += gcnew ResolveEventHandler(&Example::MyHandler);

    try
    {
        Object^ obj = ad->CreateInstanceAndUnwrap(
            "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
            "MyType");
    }
    catch (Exception^ ex)
    {
        Console::WriteLine(ex->Message);
    }
}

/* This example produces output similar to the following:

Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
...
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null

Process is terminated due to StackOverflowException.
 */
```

```csharp
using System;
using System.Reflection;

class BadExample
{
    static void Main()
    {
        AppDomain ad = AppDomain.CreateDomain("Test");
        ad.AssemblyResolve += MyHandler;

        try
        {
            object obj = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType");
        }
        catch (Exception ex)
        {
            Console.WriteLine(ex.Message);
        }
    }

    static Assembly MyHandler(object source, ResolveEventArgs e)
    {
        Console.WriteLine("Resolving {0}", e.Name);
        return Assembly.Load(e.Name);
    }
}

/* This example produces output similar to the following:

Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
...
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null

Process is terminated due to StackOverflowException.
 */
```

```vb
Imports System.Reflection

Class BadExample

    Shared Sub Main()

        Dim ad As AppDomain = AppDomain.CreateDomain("Test")
        AddHandler ad.AssemblyResolve, AddressOf MyHandler

        Try
            Dim obj As object = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType")
        Catch ex As Exception
            Console.WriteLine(ex.Message)
        End Try
    End Sub

    Shared Function MyHandler(ByVal source As Object, _
                              ByVal e As ResolveEventArgs) As Assembly
        Console.WriteLine("Resolving {0}", e.Name)
        Return Assembly.Load(e.Name)
    End Function
End Class

' This example produces output similar to the following:
'
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'...
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'
'Process is terminated due to StackOverflowException.
```

## <a name="see-also"></a><span data-ttu-id="45495-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="45495-148">See also</span></span>

- [<span data-ttu-id="45495-149">Doporučené postupy pro načítání sestavy</span><span class="sxs-lookup"><span data-stu-id="45495-149">Best practices for assembly loading</span></span>](../../framework/deployment/best-practices-for-assembly-loading.md)
- [<span data-ttu-id="45495-150">Použití aplikačních domén</span><span class="sxs-lookup"><span data-stu-id="45495-150">Use application domains</span></span>](../../framework/app-domains/use.md)

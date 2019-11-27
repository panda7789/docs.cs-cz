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
ms.openlocfilehash: edd398cd3e42e23301dcc992093d14d087754e76
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347244"
---
# <a name="resolve-assembly-loads"></a><span data-ttu-id="e47b4-102">Řešení zavedení sestavení</span><span class="sxs-lookup"><span data-stu-id="e47b4-102">Resolve assembly loads</span></span>
<span data-ttu-id="e47b4-103">Rozhraní .NET poskytuje <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost pro aplikace, které vyžadují větší kontrolu nad načítáním sestavení.</span><span class="sxs-lookup"><span data-stu-id="e47b4-103">.NET provides the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event for applications that require greater control over assembly loading.</span></span> <span data-ttu-id="e47b4-104">Při zpracování této události může vaše aplikace načíst sestavení do kontextu zatížení z vnějšku běžných cest zjišťování, vybrat, která z několika verzí sestavení má být načtena, generovat dynamické sestavení a vrátit je a tak dále.</span><span class="sxs-lookup"><span data-stu-id="e47b4-104">By handling this event, your application can load an assembly into the load context from outside the normal probing paths, select which of several assembly versions to load, emit a dynamic assembly and return it, and so on.</span></span> <span data-ttu-id="e47b4-105">Toto téma poskytuje pokyny pro zpracování události <xref:System.AppDomain.AssemblyResolve>.</span><span class="sxs-lookup"><span data-stu-id="e47b4-105">This topic provides guidance for handling the <xref:System.AppDomain.AssemblyResolve> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e47b4-106">Pro řešení zátěže sestavení v kontextu pouze pro reflexi použijte místo toho událost <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e47b4-106">For resolving assembly loads in the reflection-only context, use the <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> event instead.</span></span>  
  
## <a name="how-the-assemblyresolve-event-works"></a><span data-ttu-id="e47b4-107">Jak funguje Událost AssemblyResolve</span><span class="sxs-lookup"><span data-stu-id="e47b4-107">How the AssemblyResolve event works</span></span>  
 <span data-ttu-id="e47b4-108">Při registraci obslužné rutiny pro událost <xref:System.AppDomain.AssemblyResolve> je obslužná rutina vyvolána vždy, když se modul runtime nepřipojí k sestavení podle názvu.</span><span class="sxs-lookup"><span data-stu-id="e47b4-108">When you register a handler for the <xref:System.AppDomain.AssemblyResolve> event, the handler is invoked whenever the runtime fails to bind to an assembly by name.</span></span> <span data-ttu-id="e47b4-109">Například volání následujících metod z uživatelského kódu může způsobit vyvolání události <xref:System.AppDomain.AssemblyResolve>:</span><span class="sxs-lookup"><span data-stu-id="e47b4-109">For example, calling the following methods from user code can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised:</span></span>  
  
- <span data-ttu-id="e47b4-110">Přetížení metody <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> nebo přetížení metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, jejichž první argument je řetězec, který představuje zobrazovaný název sestavení, které se má načíst (tj. řetězec vrácený vlastností <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="e47b4-110">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is a string that represents the display name of the assembly to load (that is, the string returned by the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property).</span></span>  
  
- <span data-ttu-id="e47b4-111">Přetížení metody <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> nebo přetížení metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, jejichž první argument je objekt <xref:System.Reflection.AssemblyName>, který identifikuje sestavení, které se má načíst.</span><span class="sxs-lookup"><span data-stu-id="e47b4-111">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is an <xref:System.Reflection.AssemblyName> object that identifies the assembly to load.</span></span>  
  
- <span data-ttu-id="e47b4-112">Přetížení metody <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e47b4-112">An <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> method overload.</span></span>  
  
- <span data-ttu-id="e47b4-113">Přetížení metody <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> nebo <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>, která vytvoří instanci objektu v jiné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="e47b4-113">An <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> method overload that instantiates an object in another application domain.</span></span>  
  
### <a name="what-the-event-handler-does"></a><span data-ttu-id="e47b4-114">Co obslužná rutina události dělá</span><span class="sxs-lookup"><span data-stu-id="e47b4-114">What the event handler does</span></span>  
 <span data-ttu-id="e47b4-115">Obslužná rutina události <xref:System.AppDomain.AssemblyResolve> přijímá zobrazovaný název sestavení, které má být načteno, ve vlastnosti <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e47b4-115">The handler for the <xref:System.AppDomain.AssemblyResolve> event receives the display name of the assembly to be loaded, in the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="e47b4-116">Pokud obslužná rutina nerozpozná název sestavení, vrátí `null` (C#), `Nothing` (Visual Basic) nebo `nullptr` (vizuál C++).</span><span class="sxs-lookup"><span data-stu-id="e47b4-116">If the handler does not recognize the assembly name, it returns `null` (C#), `Nothing` (Visual Basic), or `nullptr` (Visual C++).</span></span>  
  
 <span data-ttu-id="e47b4-117">Pokud obslužná rutina rozpozná název sestavení, může načíst a vrátit sestavení, které splňuje požadavek.</span><span class="sxs-lookup"><span data-stu-id="e47b4-117">If the handler recognizes the assembly name, it can load and return an assembly that satisfies the request.</span></span> <span data-ttu-id="e47b4-118">Následující seznam popisuje některé ukázkové scénáře.</span><span class="sxs-lookup"><span data-stu-id="e47b4-118">The following list describes some sample scenarios.</span></span>  
  
- <span data-ttu-id="e47b4-119">Pokud obslužná rutina ví umístění verze sestavení, může načíst sestavení pomocí metody <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> a může vrátit načtené sestavení, pokud bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="e47b4-119">If the handler knows the location of a version of the assembly, it can load the assembly by using the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> method, and can return the loaded assembly if successful.</span></span>  
  
- <span data-ttu-id="e47b4-120">Pokud má obslužná rutina přístup k databázi sestavení uložených jako pole bajtů, může načíst pole bajtů pomocí jednoho z přetížení metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, které přebírají bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="e47b4-120">If the handler has access to a database of assemblies stored as byte arrays, it can load a byte array by using one of the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that take a byte array.</span></span>  
  
- <span data-ttu-id="e47b4-121">Obslužná rutina může generovat dynamické sestavení a vrátit ho.</span><span class="sxs-lookup"><span data-stu-id="e47b4-121">The handler can generate a dynamic assembly and return it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e47b4-122">Obslužná rutina musí načíst sestavení do kontextu load-from, do kontextu načtení nebo bez kontextu. Pokud obslužná rutina načte sestavení do kontextu pouze pro reflexi pomocí <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> nebo metody <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType>, pokus o načtení, který vyvolal událost <xref:System.AppDomain.AssemblyResolve>, se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="e47b4-122">The handler must load the assembly into the load-from context, into the load context, or without context.If the handler loads the assembly into the reflection-only context by using the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> method, the load attempt that raised the <xref:System.AppDomain.AssemblyResolve> event fails.</span></span>  
  
 <span data-ttu-id="e47b4-123">Je zodpovědný za to, že obslužná rutina události vrátí vhodné sestavení.</span><span class="sxs-lookup"><span data-stu-id="e47b4-123">It is the responsibility of the event handler to return a suitable assembly.</span></span> <span data-ttu-id="e47b4-124">Obslužná rutina může analyzovat zobrazovaný název požadovaného sestavení předáním hodnoty vlastnosti <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> do konstruktoru <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="e47b4-124">The handler can parse the display name of the requested assembly by passing the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property value to the <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> constructor.</span></span> <span data-ttu-id="e47b4-125">Počínaje .NET Framework 4 může obslužná rutina použít vlastnost <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> k určení, zda je aktuální žádost závislá na jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="e47b4-125">Beginning with the .NET Framework 4, the handler can use the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property to determine whether the current request is a dependency of another assembly.</span></span> <span data-ttu-id="e47b4-126">Tyto informace mohou napomoci identifikaci sestavení, které vyhoví závislosti.</span><span class="sxs-lookup"><span data-stu-id="e47b4-126">This information can help identify an assembly that will satisfy the dependency.</span></span>  
  
 <span data-ttu-id="e47b4-127">Obslužná rutina události může vrátit jinou verzi sestavení než požadovaná verze.</span><span class="sxs-lookup"><span data-stu-id="e47b4-127">The event handler can return a different version of the assembly than the version that was requested.</span></span>  
  
 <span data-ttu-id="e47b4-128">Ve většině případů se sestavení, které je vráceno obslužnou rutinou, zobrazuje v kontextu načtení, bez ohledu na kontext, do kterého obslužná rutina načte.</span><span class="sxs-lookup"><span data-stu-id="e47b4-128">In most cases, the assembly that is returned by the handler appears in the load context, regardless of the context the handler loads it into.</span></span> <span data-ttu-id="e47b4-129">Například pokud obslužná rutina používá metodu <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> pro načtení sestavení do kontextu load-from, sestavení se zobrazí v kontextu načtení, když ho obslužná rutina vrátí.</span><span class="sxs-lookup"><span data-stu-id="e47b4-129">For example, if the handler uses the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method to load an assembly into the load-from context, the assembly appears in the load context when the handler returns it.</span></span> <span data-ttu-id="e47b4-130">V tomto případě se ale sestavení objeví bez kontextu, když ho obslužná rutina vrátí:</span><span class="sxs-lookup"><span data-stu-id="e47b4-130">However, in the following case the assembly appears without context when the handler returns it:</span></span>  
  
- <span data-ttu-id="e47b4-131">Obslužná rutina načte sestavení bez kontextu.</span><span class="sxs-lookup"><span data-stu-id="e47b4-131">The handler loads an assembly without context.</span></span>  
  
- <span data-ttu-id="e47b4-132">Vlastnost <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> nemá hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="e47b4-132">The <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property is not null.</span></span>  
  
- <span data-ttu-id="e47b4-133">Žádající sestavení (to znamená, sestavení, které je vráceno vlastností <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType>) bylo načteno bez kontextu.</span><span class="sxs-lookup"><span data-stu-id="e47b4-133">The requesting assembly (that is, the assembly that is returned by the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property) was loaded without context.</span></span>  
  
 <span data-ttu-id="e47b4-134">Informace o kontextech naleznete v tématu přetížení metody <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e47b4-134">For information about contexts, see the <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> method overload.</span></span>  
  
 <span data-ttu-id="e47b4-135">Do stejné domény aplikace lze načíst více verzí stejného sestavení.</span><span class="sxs-lookup"><span data-stu-id="e47b4-135">Multiple versions of the same assembly can be loaded into the same application domain.</span></span> <span data-ttu-id="e47b4-136">Tento postup nedoporučujeme, protože může vést k potížím s přiřazení typu.</span><span class="sxs-lookup"><span data-stu-id="e47b4-136">This practice is not recommended, because it can lead to type assignment problems.</span></span> <span data-ttu-id="e47b4-137">Viz [osvědčené postupy pro načítání sestavení](../../framework/deployment/best-practices-for-assembly-loading.md).</span><span class="sxs-lookup"><span data-stu-id="e47b4-137">See [Best practices for assembly loading](../../framework/deployment/best-practices-for-assembly-loading.md).</span></span>  
  
### <a name="what-the-event-handler-should-not-do"></a><span data-ttu-id="e47b4-138">Co by obslužná rutina události neměla dělat</span><span class="sxs-lookup"><span data-stu-id="e47b4-138">What the event handler should not do</span></span>  
<span data-ttu-id="e47b4-139">Primárním pravidlem pro zpracování události <xref:System.AppDomain.AssemblyResolve> je, že se nepokoušíte vrátit sestavení, které nepoznáváte.</span><span class="sxs-lookup"><span data-stu-id="e47b4-139">The primary rule for handling the <xref:System.AppDomain.AssemblyResolve> event is that you should not try to return an assembly you do not recognize.</span></span> <span data-ttu-id="e47b4-140">Při psaní obslužné rutiny byste měli zjistit, která sestavení by mohla způsobit vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="e47b4-140">When you write the handler, you should know which assemblies might cause the event to be raised.</span></span> <span data-ttu-id="e47b4-141">Obslužná rutina by měla pro jiná sestavení vracet hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="e47b4-141">Your handler should return null for other assemblies.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="e47b4-142">Počínaje .NET Framework 4 se událost <xref:System.AppDomain.AssemblyResolve> vyvolá pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="e47b4-142">Beginning with the .NET Framework 4, the <xref:System.AppDomain.AssemblyResolve> event is raised for satellite assemblies.</span></span> <span data-ttu-id="e47b4-143">Tato změna má vliv na obslužnou rutinu události, která byla napsána pro starší verzi .NET Framework, pokud se obslužná rutina pokusí vyřešit všechny požadavky na načtení sestavení.</span><span class="sxs-lookup"><span data-stu-id="e47b4-143">This change affects an event handler that was written for an earlier version of the .NET Framework, if the handler tries to resolve all assembly load requests.</span></span> <span data-ttu-id="e47b4-144">Obslužné rutiny událostí, které ignorují sestavení, která nerozpoznají, nejsou touto změnou ovlivněny: vrací hodnotu null a jsou následovány normální nouzové mechanismy.</span><span class="sxs-lookup"><span data-stu-id="e47b4-144">Event handlers that ignore assemblies they do not recognize are not affected by this change: They return null, and normal fallback mechanisms are followed.</span></span>  

<span data-ttu-id="e47b4-145">Při načítání sestavení nesmí obslužná rutina události použít žádné přetížení metody <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, která může způsobit Rekurzivní vyvolání události <xref:System.AppDomain.AssemblyResolve>, protože to může vést k přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="e47b4-145">When loading an assembly, the event handler must not use any of the <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised recursively, because this can lead to a stack overflow.</span></span> <span data-ttu-id="e47b4-146">(Viz seznam uvedený dříve v tomto tématu.) K tomu dojde i v případě, že zadáváte zpracování výjimek pro požadavek na načtení, protože není vyvolána žádná výjimka, dokud všechny obslužné rutiny události nevrátí.</span><span class="sxs-lookup"><span data-stu-id="e47b4-146">(See the list provided earlier in this topic.) This happens even if you provide exception handling for the load request, because no exception is thrown until all event handlers have returned.</span></span> <span data-ttu-id="e47b4-147">Následující kód proto má za následek přetečení zásobníku, pokud `MyAssembly` nebyla nalezena:</span><span class="sxs-lookup"><span data-stu-id="e47b4-147">Thus, the following code results in a stack overflow if `MyAssembly` is not found:</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="e47b4-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e47b4-148">See also</span></span>

- [<span data-ttu-id="e47b4-149">Osvědčené postupy pro načítání sestavení</span><span class="sxs-lookup"><span data-stu-id="e47b4-149">Best practices for assembly loading</span></span>](../../framework/deployment/best-practices-for-assembly-loading.md)
- [<span data-ttu-id="e47b4-150">Použití aplikačních domén</span><span class="sxs-lookup"><span data-stu-id="e47b4-150">Use application domains</span></span>](../../framework/app-domains/use.md)

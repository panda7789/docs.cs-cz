---
title: Přeložit zatížení sestavení
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], resolving loads
- application domains, loading assemblies
- resolving assembly loads
- assemblies [.NET Framework], loading
- application domains, resolving assembly loads
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: ee9ce292b18c75893dae46582dc5bb966981a614
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973122"
---
# <a name="resolve-assembly-loads"></a>Přeložit zatížení sestavení
Rozhraní .NET poskytuje <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost pro aplikace, které vyžadují větší kontrolu nad načítáním sestavení. Při zpracování této události může vaše aplikace načíst sestavení do kontextu zatížení z vnějšku běžných cest zjišťování, vybrat, která z několika verzí sestavení má být načtena, generovat dynamické sestavení a vrátit je a tak dále. Toto téma poskytuje pokyny pro zpracování <xref:System.AppDomain.AssemblyResolve> události.  
  
> [!NOTE]
> Pro řešení zátěže sestavení v kontextu pouze pro reflexi použijte <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> místo toho událost.  
  
## <a name="how-the-assemblyresolve-event-works"></a>Jak funguje Událost AssemblyResolve  
 Při registraci obslužné rutiny pro <xref:System.AppDomain.AssemblyResolve> událost je obslužná rutina vyvolána vždy, když se modul runtime nepřipojí k sestavení podle názvu. Například volání následujících metod z uživatelského kódu může způsobit <xref:System.AppDomain.AssemblyResolve> vyvolání události:  
  
- Přetížení metody nebo <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> přetížení metody, jejichž první argument je řetězec, který představuje zobrazovaný název sestavení, které se má načíst (tj. řetězec vrácený <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> vlastností). <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
- Přetížení metody nebo <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> přetížení metody, <xref:System.Reflection.AssemblyName> jejichž první argument je objekt, který identifikuje sestavení, které se má načíst. <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
- Přetížení <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> metody.  
  
- Přetížení metody <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> nebo, která vytvoří instanci objektu v jiné doméně aplikace. <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType>  
  
### <a name="what-the-event-handler-does"></a>Co obslužná rutina události dělá  
 Obslužná rutina <xref:System.AppDomain.AssemblyResolve> události přijme zobrazovaný název sestavení, které má být načteno, <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> ve vlastnosti. Pokud obslužná rutina nerozpozná název sestavení, vrátí `null` (C#) `Nothing` , (Visual Basic), nebo `nullptr` (vizuál C++).  
  
 Pokud obslužná rutina rozpozná název sestavení, může načíst a vrátit sestavení, které splňuje požadavek. Následující seznam popisuje některé ukázkové scénáře.  
  
- Pokud obslužná rutina ví umístění verze sestavení, může načíst sestavení pomocí <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metody nebo <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> a v případě úspěchu může vrátit načtené sestavení.  
  
- Pokud má obslužná rutina přístup k databázi sestavení uložených jako pole bajtů, může načíst pole bajtů pomocí jednoho z <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> přetížení metod, které přebírají bajtové pole.  
  
- Obslužná rutina může generovat dynamické sestavení a vrátit ho.  
  
> [!NOTE]
> Obslužná rutina musí načíst sestavení do kontextu load-from, do kontextu načtení nebo bez kontextu. Pokud obslužná rutina načte sestavení do kontextu <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> pouze pro reflexi pomocí <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> metody nebo, pokus o <xref:System.AppDomain.AssemblyResolve> načtení, který událost vyvolal, se nezdaří.  
  
 Je zodpovědný za to, že obslužná rutina události vrátí vhodné sestavení. Obslužná rutina může analyzovat zobrazovaný název požadovaného sestavení předáním <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> hodnoty <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> vlastnosti konstruktoru. Počínaje .NET Framework 4 může obslužná rutina použít <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> vlastnost k určení, zda je aktuální požadavek závislá na jiném sestavení. Tyto informace mohou napomoci identifikaci sestavení, které vyhoví závislosti.  
  
 Obslužná rutina události může vrátit jinou verzi sestavení než požadovaná verze.  
  
 Ve většině případů se sestavení, které je vráceno obslužnou rutinou, zobrazuje v kontextu načtení, bez ohledu na kontext, do kterého obslužná rutina načte. Například pokud obslužná rutina používá <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metodu pro načtení sestavení do kontextu load-from, sestavení se zobrazí v kontextu načtení, když ho obslužná rutina vrátí. V tomto případě se ale sestavení objeví bez kontextu, když ho obslužná rutina vrátí:  
  
- Obslužná rutina načte sestavení bez kontextu.  
  
- <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> Vlastnost nemá hodnotu null.  
  
- Žádající sestavení (to znamená, sestavení, které je vráceno <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> vlastností) bylo načteno bez kontextu.  
  
 Informace o kontextech naleznete v tématu <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> přetížení metody.  
  
 Do stejné domény aplikace lze načíst více verzí stejného sestavení. Tento postup nedoporučujeme, protože může vést k potížím s přiřazení typu. Viz [osvědčené postupy pro načítání sestavení](../../framework/deployment/best-practices-for-assembly-loading.md).  
  
### <a name="what-the-event-handler-should-not-do"></a>Co by obslužná rutina události neměla dělat  
Primárním pravidlem pro zpracování <xref:System.AppDomain.AssemblyResolve> události je, že se nepokoušíte vrátit sestavení, které neznáte. Při psaní obslužné rutiny byste měli zjistit, která sestavení by mohla způsobit vyvolání události. Obslužná rutina by měla pro jiná sestavení vracet hodnotu null.  

> [!IMPORTANT]
> Počínaje .NET Framework 4 <xref:System.AppDomain.AssemblyResolve> se událost vyvolá pro satelitní sestavení. Tato změna má vliv na obslužnou rutinu události, která byla napsána pro starší verzi .NET Framework, pokud se obslužná rutina pokusí vyřešit všechny požadavky na načtení sestavení. Obslužné rutiny událostí, které ignorují sestavení, která nerozpoznají, nejsou touto změnou ovlivněny: Vrací hodnotu null a jsou následovány normální nouzové mechanismy.  

Při načítání sestavení nesmí obslužná rutina události použít žádné <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> přetížení metody nebo <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> , která by mohla způsobit <xref:System.AppDomain.AssemblyResolve> Rekurzivní vyvolání události, protože to může vést k přetečení zásobníku. (Viz seznam uvedený dříve v tomto tématu.) K tomu dojde i v případě, že zadáváte zpracování výjimek pro požadavek na načtení, protože není vyvolána žádná výjimka, dokud všechny obslužné rutiny události nevrátí. Následující kód proto má za následek přetečení zásobníku, pokud `MyAssembly` nebyl nalezen:  

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
Imports System
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

## <a name="see-also"></a>Viz také:

- [Osvědčené postupy pro načítání sestavení](../../framework/deployment/best-practices-for-assembly-loading.md)
- [Použití aplikačních domén](../../framework/app-domains/use.md)
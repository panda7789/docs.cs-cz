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
# <a name="resolve-assembly-loads"></a>Řešení zavedení sestavení
Rozhraní .NET poskytuje <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost pro aplikace, které vyžadují větší kontrolu nad načítáním sestavení. Při zpracování této události může vaše aplikace načíst sestavení do kontextu zatížení z vnějšku běžných cest zjišťování, vybrat, která z několika verzí sestavení má být načtena, generovat dynamické sestavení a vrátit je a tak dále. Toto téma poskytuje pokyny pro zpracování události <xref:System.AppDomain.AssemblyResolve>.  
  
> [!NOTE]
> Pro řešení zátěže sestavení v kontextu pouze pro reflexi použijte místo toho událost <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType>.  
  
## <a name="how-the-assemblyresolve-event-works"></a>Jak funguje Událost AssemblyResolve  
 Při registraci obslužné rutiny pro událost <xref:System.AppDomain.AssemblyResolve> je obslužná rutina vyvolána vždy, když se modul runtime nepřipojí k sestavení podle názvu. Například volání následujících metod z uživatelského kódu může způsobit vyvolání události <xref:System.AppDomain.AssemblyResolve>:  
  
- Přetížení metody <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> nebo přetížení metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, jejichž první argument je řetězec, který představuje zobrazovaný název sestavení, které se má načíst (tj. řetězec vrácený vlastností <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>).  
  
- Přetížení metody <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> nebo přetížení metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, jejichž první argument je objekt <xref:System.Reflection.AssemblyName>, který identifikuje sestavení, které se má načíst.  
  
- Přetížení metody <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.  
  
- Přetížení metody <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> nebo <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>, která vytvoří instanci objektu v jiné doméně aplikace.  
  
### <a name="what-the-event-handler-does"></a>Co obslužná rutina události dělá  
 Obslužná rutina události <xref:System.AppDomain.AssemblyResolve> přijímá zobrazovaný název sestavení, které má být načteno, ve vlastnosti <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType>. Pokud obslužná rutina nerozpozná název sestavení, vrátí `null` (C#), `Nothing` (Visual Basic) nebo `nullptr` (vizuál C++).  
  
 Pokud obslužná rutina rozpozná název sestavení, může načíst a vrátit sestavení, které splňuje požadavek. Následující seznam popisuje některé ukázkové scénáře.  
  
- Pokud obslužná rutina ví umístění verze sestavení, může načíst sestavení pomocí metody <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> a může vrátit načtené sestavení, pokud bylo úspěšné.  
  
- Pokud má obslužná rutina přístup k databázi sestavení uložených jako pole bajtů, může načíst pole bajtů pomocí jednoho z přetížení metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, které přebírají bajtové pole.  
  
- Obslužná rutina může generovat dynamické sestavení a vrátit ho.  
  
> [!NOTE]
> Obslužná rutina musí načíst sestavení do kontextu load-from, do kontextu načtení nebo bez kontextu. Pokud obslužná rutina načte sestavení do kontextu pouze pro reflexi pomocí <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> nebo metody <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType>, pokus o načtení, který vyvolal událost <xref:System.AppDomain.AssemblyResolve>, se nezdaří.  
  
 Je zodpovědný za to, že obslužná rutina události vrátí vhodné sestavení. Obslužná rutina může analyzovat zobrazovaný název požadovaného sestavení předáním hodnoty vlastnosti <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> do konstruktoru <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29>. Počínaje .NET Framework 4 může obslužná rutina použít vlastnost <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> k určení, zda je aktuální žádost závislá na jiném sestavení. Tyto informace mohou napomoci identifikaci sestavení, které vyhoví závislosti.  
  
 Obslužná rutina události může vrátit jinou verzi sestavení než požadovaná verze.  
  
 Ve většině případů se sestavení, které je vráceno obslužnou rutinou, zobrazuje v kontextu načtení, bez ohledu na kontext, do kterého obslužná rutina načte. Například pokud obslužná rutina používá metodu <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> pro načtení sestavení do kontextu load-from, sestavení se zobrazí v kontextu načtení, když ho obslužná rutina vrátí. V tomto případě se ale sestavení objeví bez kontextu, když ho obslužná rutina vrátí:  
  
- Obslužná rutina načte sestavení bez kontextu.  
  
- Vlastnost <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> nemá hodnotu null.  
  
- Žádající sestavení (to znamená, sestavení, které je vráceno vlastností <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType>) bylo načteno bez kontextu.  
  
 Informace o kontextech naleznete v tématu přetížení metody <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType>.  
  
 Do stejné domény aplikace lze načíst více verzí stejného sestavení. Tento postup nedoporučujeme, protože může vést k potížím s přiřazení typu. Viz [osvědčené postupy pro načítání sestavení](../../framework/deployment/best-practices-for-assembly-loading.md).  
  
### <a name="what-the-event-handler-should-not-do"></a>Co by obslužná rutina události neměla dělat  
Primárním pravidlem pro zpracování události <xref:System.AppDomain.AssemblyResolve> je, že se nepokoušíte vrátit sestavení, které nepoznáváte. Při psaní obslužné rutiny byste měli zjistit, která sestavení by mohla způsobit vyvolání události. Obslužná rutina by měla pro jiná sestavení vracet hodnotu null.  

> [!IMPORTANT]
> Počínaje .NET Framework 4 se událost <xref:System.AppDomain.AssemblyResolve> vyvolá pro satelitní sestavení. Tato změna má vliv na obslužnou rutinu události, která byla napsána pro starší verzi .NET Framework, pokud se obslužná rutina pokusí vyřešit všechny požadavky na načtení sestavení. Obslužné rutiny událostí, které ignorují sestavení, která nerozpoznají, nejsou touto změnou ovlivněny: vrací hodnotu null a jsou následovány normální nouzové mechanismy.  

Při načítání sestavení nesmí obslužná rutina události použít žádné přetížení metody <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, která může způsobit Rekurzivní vyvolání události <xref:System.AppDomain.AssemblyResolve>, protože to může vést k přetečení zásobníku. (Viz seznam uvedený dříve v tomto tématu.) K tomu dojde i v případě, že zadáváte zpracování výjimek pro požadavek na načtení, protože není vyvolána žádná výjimka, dokud všechny obslužné rutiny události nevrátí. Následující kód proto má za následek přetečení zásobníku, pokud `MyAssembly` nebyla nalezena:  

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

## <a name="see-also"></a>Viz také:

- [Osvědčené postupy pro načítání sestavení](../../framework/deployment/best-practices-for-assembly-loading.md)
- [Použití aplikačních domén](../../framework/app-domains/use.md)

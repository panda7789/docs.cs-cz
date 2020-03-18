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
# <a name="resolve-assembly-loads"></a>Řešení zavedení sestavení
Rozhraní .NET <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> poskytuje událost pro aplikace, které vyžadují větší kontrolu nad načítánísestavení. Zpracováním této události aplikace můžete načíst sestavení do kontextu zatížení z mimo normální sondování cesty, vyberte, které z několika verzí sestavení načíst, vyzařují dynamické sestavení a vrátit ji a tak dále. Toto téma obsahuje <xref:System.AppDomain.AssemblyResolve> pokyny pro zpracování události.  
  
> [!NOTE]
> Pro řešení zatížení sestavy v kontextu pouze <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> reflexe použijte místo toho událost.  
  
## <a name="how-the-assemblyresolve-event-works"></a>Jak funguje událost AssemblyResolve  
 Při registraci obslužné rutiny <xref:System.AppDomain.AssemblyResolve> pro událost je obslužná rutina vyvolána vždy, když se runtime nepodaří vytvořit vazbu na sestavení podle názvu. Například volání následující metody z uživatelského <xref:System.AppDomain.AssemblyResolve> kódu může způsobit, že událost má být vyvolána:  
  
- Přetížení <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> nebo přetížení metody, jehož první argument je řetězec, který představuje zobrazovaný název <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> sestavení načíst (to znamená řetězec vrácený vlastností).  
  
- Přetížení <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> nebo přetížení metody, <xref:System.Reflection.AssemblyName> jehož první argument je objekt, který identifikuje sestavení načíst.  
  
- Přetížení <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> metody.  
  
- Přetížení <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> metody nebo metody, které inkonzisuje objekt v jiné doméně aplikace.  
  
### <a name="what-the-event-handler-does"></a>Co obslužná rutina události dělá  
 Obslužná rutina <xref:System.AppDomain.AssemblyResolve> události obdrží zobrazovaný název sestavení, které má být načteno, ve vlastnosti. <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> Pokud obslužná rutina nerozpozná název sestavení, vrátí `null` (C#), `Nothing` (Visual Basic) nebo `nullptr` (Visual C++).  
  
 Pokud obslužná rutina rozpozná název sestavení, může načíst a vrátit sestavení, které splňuje požadavek. Následující seznam popisuje některé ukázkové scénáře.  
  
- Pokud obslužná rutina zná umístění verze sestavení, může <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> načíst sestavení pomocí metody nebo a může vrátit načtené sestavení, pokud je úspěšné.  
  
- Pokud obslužná rutina má přístup k databázi sestavení uložených jako bajtová <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> pole, může načíst bajtové pole pomocí jednoho z přetížení metody, které berou bajtové pole.  
  
- Obslužná rutina může generovat dynamické sestavení a vrátit ji.  
  
> [!NOTE]
> Obslužná rutina musí načíst sestavení do kontextu load-from, do kontextu zatížení nebo bez kontextu. Pokud obslužná rutina načte sestavení <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> do <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> kontextu pouze reflexe <xref:System.AppDomain.AssemblyResolve> pomocí nebo metody, pokus o načtení, který vyvolal událost nezdaří.  
  
 Je odpovědností obslužné rutiny události vrátit vhodné sestavení. Obslužná rutina může analyzovat zobrazovaný <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> název požadovaného sestavení předáním hodnoty vlastnosti konstruktoru. <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> Počínaje rozhraním .NET Framework 4 může <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> obslužná rutina použít vlastnost k určení, zda je aktuální požadavek závislostí jiného sestavení. Tyto informace mohou pomoci identifikovat sestavení, které bude splňovat závislost.  
  
 Obslužná rutina události může vrátit jinou verzi sestavení než verze, která byla požadována.  
  
 Ve většině případů se sestavení, které je vráceno obslužnou rutinou, zobrazí v kontextu zatížení bez ohledu na kontext, do kterého ji obslužná rutina načte. Například pokud obslužná rutina používá metodu <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> k načtení sestavení do kontextu load-from, sestavení se zobrazí v kontextu zatížení, když ho obslužná rutina vrátí. V následujícím případě se však sestavení zobrazí bez kontextu, když jej obslužná rutina vrátí:  
  
- Obslužná rutina načte sestavení bez kontextu.  
  
- Vlastnost <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> není null.  
  
- Žádající sestavení (to znamená sestavení, které <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> je vráceno vlastností) bylo načteno bez kontextu.  
  
 Informace o kontextech naleznete <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> v tématu přetížení metody.  
  
 Do stejné domény aplikace lze načíst více verzí stejného sestavení. Tento postup se nedoporučuje, protože může vést k problémům přiřazení typu. Viz [Doporučené postupy pro načítání sestavy](../../framework/deployment/best-practices-for-assembly-loading.md).  
  
### <a name="what-the-event-handler-should-not-do"></a>Co by obslužná rutina události neměla dělat  
Primární pravidlo pro <xref:System.AppDomain.AssemblyResolve> zpracování události je, že byste se neměli pokoušet vrátit sestavení, které nepoznáváte. Při psaní obslužné rutiny byste měli vědět, která sestavení mohou způsobit vyvolání události. Obslužná rutina by měla vrátit hodnotu null pro jiná sestavení.  

> [!IMPORTANT]
> Počínaje rozhraním .NET Framework <xref:System.AppDomain.AssemblyResolve> 4 je událost vyvolána pro satelitní sestavení. Tato změna ovlivní obslužnou rutinu události, která byla napsána pro starší verzi rozhraní .NET Framework, pokud se obslužná rutina pokusí vyřešit všechny požadavky na zatížení sestavení. Obslužné rutiny událostí, které ignorují sestavení, která nerozpoznávají, nejsou touto změnou ovlivněny: Vrátí hodnotu null a budou následovat normální záložní mechanismy.  

Při načítání sestavení obslužná rutina <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> události nesmí používat žádné <xref:System.AppDomain.AssemblyResolve> přetížení metody nebo metody, které může způsobit, že událost bude vyvolána rekurzivně, protože to může vést k přetečení zásobníku. (Viz seznam uvedený výše v tomto tématu.) K tomu dochází i v případě, že poskytujete zpracování výjimek pro požadavek na načtení, protože není vyvolána žádná výjimka, dokud se nevrátí všechny obslužné rutiny událostí. Následující kód má za následek přetečení zásobníku, pokud `MyAssembly` není nalezen:  

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

## <a name="see-also"></a>Viz také

- [Doporučené postupy pro načítání sestavy](../../framework/deployment/best-practices-for-assembly-loading.md)
- [Použití aplikačních domén](../../framework/app-domains/use.md)

---
title: 'Postup: Vyhledání plně kvalifikovaného názvu sestavy'
ms.date: 08/20/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 49ebaeabee7a346fb84f09e5a9e34590d1ea9811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348201"
---
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a>Postup: Vyhledání plně kvalifikovaného názvu sestavy

Chcete-li zjistit plně kvalifikovaný název sestavení rozhraní .NET Framework v globální mezipaměti sestavení, použijte nástroj globální mezipaměti sestavení ([Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md)). Viz [Postup: Zobrazení obsahu globální mezipaměti sestavení](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).

Pro sestavení .NET Core a pro sestavení rozhraní .NET Framework, která nejsou v globální mezipaměti sestavení, můžete získat plně kvalifikovaný název sestavení několika způsoby:

- Můžete použít kód pro výstup informací do konzoly nebo do proměnné, nebo můžete použít [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) prozkoumat metadata sestavení, která obsahuje plně kvalifikovaný název.

- Pokud je sestavení již načteno aplikací, můžete načíst hodnotu vlastnosti <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> a získat plně kvalifikovaný název. Vlastnost <xref:System.Type.Assembly> <xref:System.Type> definovaného v tomto sestavení můžete použít k <xref:System.Reflection.Assembly> načtení odkazu na objekt. Příklad uvádí ukázku.

- Pokud znáte cestu k systému souborů sestavení, `static` můžete volat `Shared` metodu (C#) nebo (Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> a získat plně kvalifikovaný název sestavení. Následuje jednoduchý příklad.

  ```csharp
  using System;
  using System.Reflection;

  public class Example
  {
     public static void Main()
     {
        Console.WriteLine(AssemblyName.GetAssemblyName(@".\UtilityLibrary.dll"));
     }
  }
  // The example displays output like the following:
  //   UtilityLibrary, Version=1.1.0.0, Culture=neutral, PublicKeyToken=null
  ```

  ```vb
  Imports System.Reflection

  Public Module Example
     Public Sub Main
        Console.WriteLine(AssemblyName.GetAssemblyName(".\UtilityLibrary.dll"))
     End Sub
  End Module
  ' The example displays output like the following:
  '   UtilityLibrary, Version=1.1.0.0, Culture=neutral, PublicKeyToken=null
  ```

- [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) můžete použít ke kontrole metadat sestavení, která obsahuje plně kvalifikovaný název.

Další informace o nastavení atributů sestavení, jako je verze, jazyková verze a název sestavení, naleznete v [tématu Nastavení atributů sestavení](set-attributes.md). Další informace o udělení silného názvu sestavení naleznete v tématu [Vytvoření a použití sestavení se silným názvem](create-use-strong-named.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zobrazit plně kvalifikovaný název sestavení obsahující zadanou třídu do konzoly. Používá <xref:System.Type.Assembly?displayProperty=nameWithType> vlastnost k načtení odkazu na sestavení z typu, který je definován v tomto sestavení.

```cpp
#using <System.dll>
#using <System.Data.dll>

using namespace System;
using namespace System::Reflection;

ref class asmname
{
public:
    static void Main()
    {
        Type^ t = System::Data::DataSet::typeid;
        String^ s = t->Assembly->FullName->ToString();
        Console::WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s);
    }
};

int main()
{
    asmname::Main();
}
```

```csharp
using System;
using System.Reflection;

class asmname
{
    public static void Main()
    {
        Type t = typeof(System.Data.DataSet);
        string s = t.Assembly.FullName.ToString();
        Console.WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s);
    }
}
```

```vb
Imports System.Reflection

Class asmname
    Public Shared Sub Main()
        Dim t As Type = GetType(System.Data.DataSet)
        Dim s As String = t.Assembly.FullName.ToString()
        Console.WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s)
    End Sub
End Class
```

## <a name="see-also"></a>Viz také

- [Názvy sestavení](names.md)
- [Vytváření sestavení](create.md)
- [Vytváření a používání sestavení se silným názvem](create-use-strong-named.md)
- [Globální mezipaměť sestavení](../../framework/app-domains/gac.md)
- [Jak runtime vyhledá sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md)

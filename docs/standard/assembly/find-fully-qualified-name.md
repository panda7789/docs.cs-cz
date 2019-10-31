---
title: 'Postupy: hledání plně kvalifikovaného názvu sestavení'
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
ms.openlocfilehash: 49d6d6cf5c138df671d061beb23cb57bcb0667b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140302"
---
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a>Postupy: hledání plně kvalifikovaného názvu sestavení

Chcete-li zjistit plně kvalifikovaný název .NET Framework sestavení v globální mezipaměti sestavení (GAC), použijte nástroj Global Assembly Cache ([Gacutil. exe](../../framework/tools/gacutil-exe-gac-tool.md)). Viz [Postup: zobrazení obsahu globální mezipaměti sestavení (GAC](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md)).

Pro sestavení .NET Core a pro .NET Framework sestavení, která nejsou v globální mezipaměti sestavení (GAC), můžete získat plně kvalifikovaný název sestavení několika způsoby:

- Můžete použít kód pro výstup informací do konzoly nebo proměnné, nebo můžete použít nástroj [Ildasm. exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) k prohlédnutí metadat sestavení, která obsahují plně kvalifikovaný název.

- Pokud je sestavení již načteno aplikací, můžete získat hodnotu vlastnosti <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> pro získání plně kvalifikovaného názvu. Můžete použít vlastnost <xref:System.Type.Assembly> <xref:System.Type> definované v tomto sestavení k načtení odkazu na objekt <xref:System.Reflection.Assembly>. Příklad uvádí ukázku.

- Pokud znáte cestu k systému souborů sestavení, můžete volat <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> metodu `static` (C#) nebo `Shared` (Visual Basic) k získání plně kvalifikovaného názvu sestavení. Následuje jednoduchý příklad.

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

- Pomocí nástroje [Ildasm. exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) můžete prozkoumávat metadata sestavení, která obsahují plně kvalifikovaný název.

Další informace o nastavení atributů sestavení, jako je verze, jazyková verze a název sestavení, naleznete v tématu [nastavení atributů sestavení](set-attributes.md). Další informace o poskytnutí silného názvu sestavení naleznete v tématu [Vytvoření a použití sestavení se silným názvem](create-use-strong-named.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zobrazit plně kvalifikovaný název sestavení, které obsahuje zadanou třídu, do konzoly. Pomocí vlastnosti <xref:System.Type.Assembly?displayProperty=nameWithType> načte odkaz na sestavení z typu, který je definován v tomto sestavení.

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
Imports System
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

## <a name="see-also"></a>Viz také:

- [Názvy sestavení](names.md)
- [Vytváření sestavení](create.md)
- [Vytváření a používání sestavení se silným názvem](create-use-strong-named.md)
- [Globální mezipaměť sestavení](../../framework/app-domains/gac.md)
- [Způsob, jakým modul runtime vyhledává sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Program se sestaveními](program.md)

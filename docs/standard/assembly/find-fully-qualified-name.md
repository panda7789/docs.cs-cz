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
ms.openlocfilehash: bf24db03ca1dc4fbf3041f5e83d740029d87928f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740495"
---
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a><span data-ttu-id="8f837-102">Postupy: hledání plně kvalifikovaného názvu sestavení</span><span class="sxs-lookup"><span data-stu-id="8f837-102">How to: Find an assembly's fully qualified name</span></span>

<span data-ttu-id="8f837-103">Chcete-li zjistit plně kvalifikovaný název .NET Framework sestavení v globální mezipaměti sestavení (GAC), použijte nástroj Global Assembly Cache ([Gacutil. exe](../../framework/tools/gacutil-exe-gac-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="8f837-103">To discover the fully qualified name of a .NET Framework assembly in the global assembly cache, use the Global Assembly Cache tool ([Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md)).</span></span> <span data-ttu-id="8f837-104">Viz [Postup: zobrazení obsahu globální mezipaměti sestavení (GAC](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md)).</span><span class="sxs-lookup"><span data-stu-id="8f837-104">See [How to: View the contents of the global assembly cache](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span></span>

<span data-ttu-id="8f837-105">Pro sestavení .NET Core a pro .NET Framework sestavení, která nejsou v globální mezipaměti sestavení (GAC), můžete získat plně kvalifikovaný název sestavení několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="8f837-105">For .NET Core assemblies, and for .NET Framework assemblies that aren't in the global assembly cache, you can get the fully qualified assembly name in a number of ways:</span></span>

- <span data-ttu-id="8f837-106">Můžete použít kód pro výstup informací do konzoly nebo proměnné, nebo můžete použít nástroj [Ildasm. exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) k prohlédnutí metadat sestavení, která obsahují plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="8f837-106">You can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>

- <span data-ttu-id="8f837-107">Pokud je sestavení již načteno aplikací, můžete získat hodnotu vlastnosti <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> pro získání plně kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="8f837-107">If the assembly is already loaded by the application, you can retrieve the value of the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property to get the fully qualified name.</span></span> <span data-ttu-id="8f837-108">Můžete použít vlastnost <xref:System.Type.Assembly> <xref:System.Type> definované v tomto sestavení k načtení odkazu na objekt <xref:System.Reflection.Assembly>.</span><span class="sxs-lookup"><span data-stu-id="8f837-108">You can use the <xref:System.Type.Assembly> property of a <xref:System.Type> defined in that assembly to retrieve a reference to the <xref:System.Reflection.Assembly> object.</span></span> <span data-ttu-id="8f837-109">Příklad uvádí ukázku.</span><span class="sxs-lookup"><span data-stu-id="8f837-109">The example provides an illustration.</span></span>

- <span data-ttu-id="8f837-110">Pokud znáte cestu k systému souborů sestavení, můžete volat <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> metodu `static` (C#) nebo `Shared` (Visual Basic) k získání plně kvalifikovaného názvu sestavení.</span><span class="sxs-lookup"><span data-stu-id="8f837-110">If you know the assembly's file system path, you can call the `static` (C#) or `Shared` (Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method to get the fully qualified assembly name.</span></span> <span data-ttu-id="8f837-111">Následuje jednoduchý příklad.</span><span class="sxs-lookup"><span data-stu-id="8f837-111">The following is a simple example.</span></span>

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

- <span data-ttu-id="8f837-112">Pomocí nástroje [Ildasm. exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) můžete prozkoumávat metadata sestavení, která obsahují plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="8f837-112">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>

<span data-ttu-id="8f837-113">Další informace o nastavení atributů sestavení, jako je verze, jazyková verze a název sestavení, naleznete v tématu [nastavení atributů sestavení](set-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="8f837-113">For more information about setting assembly attributes such as version, culture, and assembly name, see [Set assembly attributes](set-attributes.md).</span></span> <span data-ttu-id="8f837-114">Další informace o poskytnutí silného názvu sestavení naleznete v tématu [Vytvoření a použití sestavení se silným názvem](create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="8f837-114">For more information about giving an assembly a strong name, see [Create and use strong-named assemblies](create-use-strong-named.md).</span></span>

## <a name="example"></a><span data-ttu-id="8f837-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="8f837-115">Example</span></span>

<span data-ttu-id="8f837-116">Následující příklad ukazuje, jak zobrazit plně kvalifikovaný název sestavení, které obsahuje zadanou třídu, do konzoly.</span><span class="sxs-lookup"><span data-stu-id="8f837-116">The following example shows how to display the fully qualified name of an assembly containing a specified class to the console.</span></span> <span data-ttu-id="8f837-117">Pomocí vlastnosti <xref:System.Type.Assembly?displayProperty=nameWithType> načte odkaz na sestavení z typu, který je definován v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="8f837-117">It uses the <xref:System.Type.Assembly?displayProperty=nameWithType> property to retrieve a reference to an assembly from a type that's defined in that assembly.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8f837-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8f837-118">See also</span></span>

- [<span data-ttu-id="8f837-119">Názvy sestavení</span><span class="sxs-lookup"><span data-stu-id="8f837-119">Assembly names</span></span>](names.md)
- [<span data-ttu-id="8f837-120">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="8f837-120">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="8f837-121">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="8f837-121">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="8f837-122">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="8f837-122">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="8f837-123">Způsob, jakým modul runtime vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="8f837-123">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)

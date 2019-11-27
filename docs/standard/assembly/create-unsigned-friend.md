---
title: 'Postupy: vytváření nepodepsaných přátelských sestavení'
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: f8fec064507553b8208083578165965de2303a33
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352440"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a><span data-ttu-id="9ca27-102">Postupy: vytváření nepodepsaných přátelských sestavení</span><span class="sxs-lookup"><span data-stu-id="9ca27-102">How to: Create unsigned friend assemblies</span></span>

<span data-ttu-id="9ca27-103">Tento příklad ukazuje, jak použít sestavení typu Friend se sestaveními, která jsou bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="9ca27-103">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>

## <a name="create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="9ca27-104">Vytvoření sestavení a sestavení typu Friend</span><span class="sxs-lookup"><span data-stu-id="9ca27-104">Create an assembly and a friend assembly</span></span>

1. <span data-ttu-id="9ca27-105">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="9ca27-105">Open a command prompt.</span></span>

2. <span data-ttu-id="9ca27-106">Vytvořte soubor C# nebo Visual Basic s názvem *friend_unsigned_A* , který obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="9ca27-106">Create a C# or Visual Basic file named *friend_unsigned_A* that contains the following code.</span></span> <span data-ttu-id="9ca27-107">Kód používá atribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> k deklaraci *friend_unsigned_B* jako sestavení typu Friend.</span><span class="sxs-lookup"><span data-stu-id="9ca27-107">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_unsigned_B* as a friend assembly.</span></span>

   ```csharp
   // friend_unsigned_A.cs
   // Compile with:
   // csc /target:library friend_unsigned_A.cs
   using System.Runtime.CompilerServices;
   using System;

   [assembly: InternalsVisibleTo("friend_unsigned_B")]

   // Type is internal by default.
   class Class1
   {
       public void Test()
       {
           Console.WriteLine("Class1.Test");
       }
   }

   // Public type with internal member.
   public class Class2
   {
       internal void Test()
       {
           Console.WriteLine("Class2.Test");
       }
   }
   ```

   ```vb
   ' friend_unsigned_A.vb
   ' Compile with:
   ' vbc -target:library friend_unsigned_A.vb
   Imports System.Runtime.CompilerServices

   <Assembly: InternalsVisibleTo("friend_unsigned_B")>

   ' Friend type.
   Friend Class Class1
       Public Sub Test()
           Console.WriteLine("Class1.Test")
       End Sub
   End Class

   ' Public type with Friend member.
   Public Class Class2
       Friend Sub Test()
           Console.WriteLine("Class2.Test")
       End Sub
   End Class
   ```

3. <span data-ttu-id="9ca27-108">Zkompilujte a podepište *friend_unsigned_A* pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="9ca27-108">Compile and sign *friend_unsigned_A* by using the following command:</span></span>

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. <span data-ttu-id="9ca27-109">Vytvořte soubor C# nebo Visual Basic s názvem *friend_unsigned_B* , který obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="9ca27-109">Create a C# or Visual Basic file named *friend_unsigned_B* that contains the following code.</span></span> <span data-ttu-id="9ca27-110">Vzhledem k tomu, že *friend_unsigned_A* Určuje *friend_unsigned_B* jako sestavení typu friend, kód v *friend_unsigned_B* můžeC#přistupovat k typům `internal` () nebo `Friend` (Visual Basic) a členům z *friend_unsigned_A*.</span><span class="sxs-lookup"><span data-stu-id="9ca27-110">Because *friend_unsigned_A* specifies *friend_unsigned_B* as a friend assembly, the code in *friend_unsigned_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_unsigned_A*.</span></span>

   ```csharp
   // friend_unsigned_B.cs
   // Compile with:
   // csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   public class Program
   {
       static void Main()
       {
           // Access an internal type.
           Class1 inst1 = new Class1();
           inst1.Test();

           Class2 inst2 = new Class2();
           // Access an internal member of a public type.
           inst2.Test();

           System.Console.ReadLine();
       }
   }
   ```

   ```vb
   ' friend_unsigned_B.vb
   ' Compile with:
   ' vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   Module Module1
       Sub Main()
           ' Access a Friend type.
           Dim inst1 As New Class1()
           inst1.Test()

           Dim inst2 As New Class2()
           ' Access a Friend member of a public type.
           inst2.Test()

           System.Console.ReadLine()
       End Sub
   End Module
   ```

5. <span data-ttu-id="9ca27-111">Zkompilujte *friend_unsigned_B* pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="9ca27-111">Compile *friend_unsigned_B* by using the following command.</span></span>

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   <span data-ttu-id="9ca27-112">Název sestavení, který je generován kompilátorem, se musí shodovat s názvem sestavení typu Friend, které je předáno atributu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9ca27-112">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="9ca27-113">Musíte explicitně zadat název výstupního sestavení ( *. exe* nebo *. dll*) pomocí možnosti kompilátoru `-out`.</span><span class="sxs-lookup"><span data-stu-id="9ca27-113">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="9ca27-114">Další informace naleznete v tématu [-out (C# možnosti kompilátoru)](../../csharp/language-reference/compiler-options/out-compiler-option.md) nebo [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="9ca27-114">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span></span>

6. <span data-ttu-id="9ca27-115">Spusťte soubor *friend_unsigned_B. exe* .</span><span class="sxs-lookup"><span data-stu-id="9ca27-115">Run the *friend_unsigned_B.exe* file.</span></span>

   <span data-ttu-id="9ca27-116">Program vytvoří výstup dvou řetězců: **Class1. test** a **Class2. test**.</span><span class="sxs-lookup"><span data-stu-id="9ca27-116">The program outputs two strings: **Class1.Test** and **Class2.Test**.</span></span>

## <a name="net-security"></a><span data-ttu-id="9ca27-117">Zabezpečení .NET</span><span class="sxs-lookup"><span data-stu-id="9ca27-117">.NET security</span></span>

<span data-ttu-id="9ca27-118">Existují podobnosti mezi atributem <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> a třídou <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="9ca27-118">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="9ca27-119">Hlavním rozdílem je, že <xref:System.Security.Permissions.StrongNameIdentityPermission> může vyžadovat oprávnění zabezpečení ke spuštění konkrétní části kódu, zatímco atribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> řídí viditelnost typů a členů `internal` nebo `Friend` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="9ca27-119">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal`  or `Friend` (Visual Basic) types and members.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ca27-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ca27-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="9ca27-121">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="9ca27-121">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="9ca27-122">Friend – sestavení</span><span class="sxs-lookup"><span data-stu-id="9ca27-122">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="9ca27-123">Postupy: Vytváření podepsaných přátelských sestavení</span><span class="sxs-lookup"><span data-stu-id="9ca27-123">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="9ca27-124">C#Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="9ca27-124">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="9ca27-125">Koncepty programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ca27-125">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)

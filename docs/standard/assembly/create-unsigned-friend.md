---
title: 'Postupy: Vytvořit nepodepsaná sestavení typu Friend'
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: 9d5699f772dba994b10408d15422faa3c5931f45
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991685"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a><span data-ttu-id="20699-102">Postupy: Vytvořit nepodepsaná sestavení typu Friend</span><span class="sxs-lookup"><span data-stu-id="20699-102">How to: Create unsigned friend assemblies</span></span>

<span data-ttu-id="20699-103">Tento příklad ukazuje, jak použít sestavení typu Friend se sestaveními, která jsou bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="20699-103">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>

## <a name="create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="20699-104">Vytvoření sestavení a sestavení typu Friend</span><span class="sxs-lookup"><span data-stu-id="20699-104">Create an assembly and a friend assembly</span></span>

1. <span data-ttu-id="20699-105">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="20699-105">Open a command prompt.</span></span>

2. <span data-ttu-id="20699-106">Vytvořte soubor C# nebo Visual Basic s názvem *friend_unsigned_A* , který obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="20699-106">Create a C# or Visual Basic file named *friend_unsigned_A* that contains the following code.</span></span> <span data-ttu-id="20699-107">Kód používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut k deklaraci *friend_unsigned_B* jako sestavení typu Friend.</span><span class="sxs-lookup"><span data-stu-id="20699-107">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_unsigned_B* as a friend assembly.</span></span>

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
   Imports System

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

3. <span data-ttu-id="20699-108">Zkompilujte a podepište *friend_unsigned_A* pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="20699-108">Compile and sign *friend_unsigned_A* by using the following command:</span></span>

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. <span data-ttu-id="20699-109">Vytvořte soubor C# nebo Visual Basic s názvem *friend_unsigned_B* , který obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="20699-109">Create a C# or Visual Basic file named *friend_unsigned_B* that contains the following code.</span></span> <span data-ttu-id="20699-110">Vzhledem k tomu, že *friend_unsigned_A* Určuje *friend_unsigned_B* jako sestavení typu Friend, kód v `internal` *friend_unsigned_B* může přistupovat `Friend` k typům (C#) nebo (Visual Basic) a členům z *friend_unsigned_A* .</span><span class="sxs-lookup"><span data-stu-id="20699-110">Because *friend_unsigned_A* specifies *friend_unsigned_B* as a friend assembly, the code in *friend_unsigned_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_unsigned_A*.</span></span>

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

5. <span data-ttu-id="20699-111">Zkompilujte *friend_unsigned_B* pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="20699-111">Compile *friend_unsigned_B* by using the following command.</span></span>

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   <span data-ttu-id="20699-112">Název sestavení, který je generován kompilátorem, se musí shodovat s názvem sestavení typu Friend, které je předáno <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributu.</span><span class="sxs-lookup"><span data-stu-id="20699-112">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="20699-113">Je nutné explicitně zadat název výstupního sestavení ( *. exe* nebo *. dll*) pomocí `/out` možnosti kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="20699-113">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `/out` compiler option.</span></span> <span data-ttu-id="20699-114">Další informace naleznete v tématu [/out (C# možnosti kompilátoru)](../../csharp/language-reference/compiler-options/out-compiler-option.md) nebo [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="20699-114">For more information, see [/out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span></span>

6. <span data-ttu-id="20699-115">Spusťte soubor *friend_unsigned_B. exe* .</span><span class="sxs-lookup"><span data-stu-id="20699-115">Run the *friend_unsigned_B.exe* file.</span></span>

   <span data-ttu-id="20699-116">Program vytvoří výstup dvou řetězců: **Class1. test** a **Class2. test**.</span><span class="sxs-lookup"><span data-stu-id="20699-116">The program outputs two strings: **Class1.Test** and **Class2.Test**.</span></span>

## <a name="net-security"></a><span data-ttu-id="20699-117">Zabezpečení .NET</span><span class="sxs-lookup"><span data-stu-id="20699-117">.NET security</span></span>

<span data-ttu-id="20699-118">Existují podobnosti mezi <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributem <xref:System.Security.Permissions.StrongNameIdentityPermission> a třídou.</span><span class="sxs-lookup"><span data-stu-id="20699-118">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="20699-119">Hlavním rozdílem je, <xref:System.Security.Permissions.StrongNameIdentityPermission> že může vyžadovat oprávnění zabezpečení ke spuštění konkrétní části kódu, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> zatímco `internal` atribut `Friend` řídí viditelnost typů a členů (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="20699-119">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal`  or `Friend` (Visual Basic) types and members.</span></span>

## <a name="see-also"></a><span data-ttu-id="20699-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20699-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="20699-121">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="20699-121">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="20699-122">Friend – sestavení</span><span class="sxs-lookup"><span data-stu-id="20699-122">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="20699-123">Postupy: Vytvořit podepsaná sestavení typu Friend</span><span class="sxs-lookup"><span data-stu-id="20699-123">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="20699-124">C#Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="20699-124">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="20699-125">Koncepty programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20699-125">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)

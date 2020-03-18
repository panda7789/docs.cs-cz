---
title: 'Postup: Vytvoření nepodepsaných sestavení přátel'
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: f8fec064507553b8208083578165965de2303a33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352440"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a><span data-ttu-id="26013-102">Postup: Vytvoření nepodepsaných sestavení přátel</span><span class="sxs-lookup"><span data-stu-id="26013-102">How to: Create unsigned friend assemblies</span></span>

<span data-ttu-id="26013-103">Tento příklad ukazuje, jak používat sestavení přátel s sestaveními, která nejsou podepsána.</span><span class="sxs-lookup"><span data-stu-id="26013-103">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>

## <a name="create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="26013-104">Vytvoření sestavy a sestavy přítele</span><span class="sxs-lookup"><span data-stu-id="26013-104">Create an assembly and a friend assembly</span></span>

1. <span data-ttu-id="26013-105">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="26013-105">Open a command prompt.</span></span>

2. <span data-ttu-id="26013-106">Vytvořte soubor jazyka C# nebo Visual Basic s názvem *friend_unsigned_A,* který obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="26013-106">Create a C# or Visual Basic file named *friend_unsigned_A* that contains the following code.</span></span> <span data-ttu-id="26013-107">Kód používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut deklarovat *friend_unsigned_B* jako sestavení přítele.</span><span class="sxs-lookup"><span data-stu-id="26013-107">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_unsigned_B* as a friend assembly.</span></span>

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

3. <span data-ttu-id="26013-108">Kompilujte a podepisujte *friend_unsigned_A* pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="26013-108">Compile and sign *friend_unsigned_A* by using the following command:</span></span>

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. <span data-ttu-id="26013-109">Vytvořte soubor jazyka C# nebo Visual Basic s názvem *friend_unsigned_B,* který obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="26013-109">Create a C# or Visual Basic file named *friend_unsigned_B* that contains the following code.</span></span> <span data-ttu-id="26013-110">Vzhledem k tomu, *že friend_unsigned_A* určuje *friend_unsigned_B* `internal` jako přátelské sestavení, kód v *friend_unsigned_B* může přistupovat (C#) nebo `Friend` (Visual Basic) typy a členy z *friend_unsigned_A*.</span><span class="sxs-lookup"><span data-stu-id="26013-110">Because *friend_unsigned_A* specifies *friend_unsigned_B* as a friend assembly, the code in *friend_unsigned_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_unsigned_A*.</span></span>

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

5. <span data-ttu-id="26013-111">Kompilace *friend_unsigned_B* pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="26013-111">Compile *friend_unsigned_B* by using the following command.</span></span>

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   <span data-ttu-id="26013-112">Název sestavení, které je generováno kompilátorem, musí odpovídat názvu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> sestavení friend, který je předán atributu.</span><span class="sxs-lookup"><span data-stu-id="26013-112">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="26013-113">Je nutné explicitně zadat název výstupního sestavení (*.exe* `-out` nebo *.dll*) pomocí možnosti kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="26013-113">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="26013-114">Další informace naleznete [v tématu -out (C# možnosti kompilátoru)](../../csharp/language-reference/compiler-options/out-compiler-option.md) nebo [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span><span class="sxs-lookup"><span data-stu-id="26013-114">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span></span>

6. <span data-ttu-id="26013-115">Spusťte soubor *friend_unsigned_B.exe.*</span><span class="sxs-lookup"><span data-stu-id="26013-115">Run the *friend_unsigned_B.exe* file.</span></span>

   <span data-ttu-id="26013-116">Program vyveze dva řetězce: **Class1.Test** a **Class2.Test**.</span><span class="sxs-lookup"><span data-stu-id="26013-116">The program outputs two strings: **Class1.Test** and **Class2.Test**.</span></span>

## <a name="net-security"></a><span data-ttu-id="26013-117">Zabezpečení .NET</span><span class="sxs-lookup"><span data-stu-id="26013-117">.NET security</span></span>

<span data-ttu-id="26013-118">Existují podobnosti mezi <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributem <xref:System.Security.Permissions.StrongNameIdentityPermission> a třídou.</span><span class="sxs-lookup"><span data-stu-id="26013-118">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="26013-119">Hlavní rozdíl je, <xref:System.Security.Permissions.StrongNameIdentityPermission> že může vyžadovat oprávnění zabezpečení ke spuštění <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> určité části kódu, zatímco atribut řídí viditelnost `internal` nebo `Friend` (Visual Basic) typy a členy.</span><span class="sxs-lookup"><span data-stu-id="26013-119">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal`  or `Friend` (Visual Basic) types and members.</span></span>

## <a name="see-also"></a><span data-ttu-id="26013-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="26013-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="26013-121">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="26013-121">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="26013-122">Přátelská sestavení</span><span class="sxs-lookup"><span data-stu-id="26013-122">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="26013-123">Postup: Vytvoření podepsaných sestavení přátel</span><span class="sxs-lookup"><span data-stu-id="26013-123">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="26013-124">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="26013-124">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="26013-125">Koncepty programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26013-125">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)

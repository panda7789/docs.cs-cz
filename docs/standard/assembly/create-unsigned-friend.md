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
# <a name="how-to-create-unsigned-friend-assemblies"></a>Postupy: Vytvořit nepodepsaná sestavení typu Friend

Tento příklad ukazuje, jak použít sestavení typu Friend se sestaveními, která jsou bez znaménka.

## <a name="create-an-assembly-and-a-friend-assembly"></a>Vytvoření sestavení a sestavení typu Friend

1. Otevřete příkazový řádek.

2. Vytvořte soubor C# nebo Visual Basic s názvem *friend_unsigned_A* , který obsahuje následující kód. Kód používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut k deklaraci *friend_unsigned_B* jako sestavení typu Friend.

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

3. Zkompilujte a podepište *friend_unsigned_A* pomocí následujícího příkazu:

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. Vytvořte soubor C# nebo Visual Basic s názvem *friend_unsigned_B* , který obsahuje následující kód. Vzhledem k tomu, že *friend_unsigned_A* Určuje *friend_unsigned_B* jako sestavení typu Friend, kód v `internal` *friend_unsigned_B* může přistupovat `Friend` k typům (C#) nebo (Visual Basic) a členům z *friend_unsigned_A* .

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

5. Zkompilujte *friend_unsigned_B* pomocí následujícího příkazu.

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   Název sestavení, který je generován kompilátorem, se musí shodovat s názvem sestavení typu Friend, které je předáno <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributu. Je nutné explicitně zadat název výstupního sestavení ( *. exe* nebo *. dll*) pomocí `/out` možnosti kompilátoru. Další informace naleznete v tématu [/out (C# možnosti kompilátoru)](../../csharp/language-reference/compiler-options/out-compiler-option.md) nebo [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).

6. Spusťte soubor *friend_unsigned_B. exe* .

   Program vytvoří výstup dvou řetězců: **Class1. test** a **Class2. test**.

## <a name="net-security"></a>Zabezpečení .NET

Existují podobnosti mezi <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributem <xref:System.Security.Permissions.StrongNameIdentityPermission> a třídou. Hlavním rozdílem je, <xref:System.Security.Permissions.StrongNameIdentityPermission> že může vyžadovat oprávnění zabezpečení ke spuštění konkrétní části kódu, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> zatímco `internal` atribut `Friend` řídí viditelnost typů a členů (Visual Basic).

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Sestavení v .NET](index.md)
- [Friend – sestavení](friend.md)
- [Postupy: Vytvořit podepsaná sestavení typu Friend](create-signed-friend.md)
- [C#Průvodce programováním](../../csharp/programming-guide/index.md)
- [Koncepty programování (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)

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
# <a name="how-to-create-unsigned-friend-assemblies"></a>Postupy: vytváření nepodepsaných přátelských sestavení

Tento příklad ukazuje, jak použít sestavení typu Friend se sestaveními, která jsou bez znaménka.

## <a name="create-an-assembly-and-a-friend-assembly"></a>Vytvoření sestavení a sestavení typu Friend

1. Otevřete příkazový řádek.

2. Vytvořte soubor C# nebo Visual Basic s názvem *friend_unsigned_A* , který obsahuje následující kód. Kód používá atribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> k deklaraci *friend_unsigned_B* jako sestavení typu Friend.

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

3. Zkompilujte a podepište *friend_unsigned_A* pomocí následujícího příkazu:

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. Vytvořte soubor C# nebo Visual Basic s názvem *friend_unsigned_B* , který obsahuje následující kód. Vzhledem k tomu, že *friend_unsigned_A* Určuje *friend_unsigned_B* jako sestavení typu friend, kód v *friend_unsigned_B* můžeC#přistupovat k typům `internal` () nebo `Friend` (Visual Basic) a členům z *friend_unsigned_A*.

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

   Název sestavení, který je generován kompilátorem, se musí shodovat s názvem sestavení typu Friend, které je předáno atributu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Musíte explicitně zadat název výstupního sestavení ( *. exe* nebo *. dll*) pomocí možnosti kompilátoru `-out`. Další informace naleznete v tématu [-out (C# možnosti kompilátoru)](../../csharp/language-reference/compiler-options/out-compiler-option.md) nebo [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).

6. Spusťte soubor *friend_unsigned_B. exe* .

   Program vytvoří výstup dvou řetězců: **Class1. test** a **Class2. test**.

## <a name="net-security"></a>Zabezpečení .NET

Existují podobnosti mezi atributem <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> a třídou <xref:System.Security.Permissions.StrongNameIdentityPermission>. Hlavním rozdílem je, že <xref:System.Security.Permissions.StrongNameIdentityPermission> může vyžadovat oprávnění zabezpečení ke spuštění konkrétní části kódu, zatímco atribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> řídí viditelnost typů a členů `internal` nebo `Friend` (Visual Basic).

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Sestavení v .NET](index.md)
- [Friend – sestavení](friend.md)
- [Postupy: Vytváření podepsaných přátelských sestavení](create-signed-friend.md)
- [C#Průvodce programováním](../../csharp/programming-guide/index.md)
- [Koncepty programování (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)

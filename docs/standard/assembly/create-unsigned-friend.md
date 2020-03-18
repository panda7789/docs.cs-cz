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
# <a name="how-to-create-unsigned-friend-assemblies"></a>Postup: Vytvoření nepodepsaných sestavení přátel

Tento příklad ukazuje, jak používat sestavení přátel s sestaveními, která nejsou podepsána.

## <a name="create-an-assembly-and-a-friend-assembly"></a>Vytvoření sestavy a sestavy přítele

1. Otevřete příkazový řádek.

2. Vytvořte soubor jazyka C# nebo Visual Basic s názvem *friend_unsigned_A,* který obsahuje následující kód. Kód používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut deklarovat *friend_unsigned_B* jako sestavení přítele.

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

3. Kompilujte a podepisujte *friend_unsigned_A* pomocí následujícího příkazu:

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. Vytvořte soubor jazyka C# nebo Visual Basic s názvem *friend_unsigned_B,* který obsahuje následující kód. Vzhledem k tomu, *že friend_unsigned_A* určuje *friend_unsigned_B* `internal` jako přátelské sestavení, kód v *friend_unsigned_B* může přistupovat (C#) nebo `Friend` (Visual Basic) typy a členy z *friend_unsigned_A*.

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

5. Kompilace *friend_unsigned_B* pomocí následujícího příkazu.

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   Název sestavení, které je generováno kompilátorem, musí odpovídat názvu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> sestavení friend, který je předán atributu. Je nutné explicitně zadat název výstupního sestavení (*.exe* `-out` nebo *.dll*) pomocí možnosti kompilátoru. Další informace naleznete [v tématu -out (C# možnosti kompilátoru)](../../csharp/language-reference/compiler-options/out-compiler-option.md) nebo [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..

6. Spusťte soubor *friend_unsigned_B.exe.*

   Program vyveze dva řetězce: **Class1.Test** a **Class2.Test**.

## <a name="net-security"></a>Zabezpečení .NET

Existují podobnosti mezi <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributem <xref:System.Security.Permissions.StrongNameIdentityPermission> a třídou. Hlavní rozdíl je, <xref:System.Security.Permissions.StrongNameIdentityPermission> že může vyžadovat oprávnění zabezpečení ke spuštění <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> určité části kódu, zatímco atribut řídí viditelnost `internal` nebo `Friend` (Visual Basic) typy a členy.

## <a name="see-also"></a>Viz také

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Sestavení v .NET](index.md)
- [Přátelská sestavení](friend.md)
- [Postup: Vytvoření podepsaných sestavení přátel](create-signed-friend.md)
- [Průvodce programováním v C#](../../csharp/programming-guide/index.md)
- [Koncepty programování (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)

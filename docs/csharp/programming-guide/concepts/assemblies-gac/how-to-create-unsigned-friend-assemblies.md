---
title: 'Postupy: Vytvořit nepodepsaná Friend sestaveníC#()'
ms.date: 07/20/2015
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
ms.openlocfilehash: 5dadd725234048c4b6a4f9a0fa9b38dbf92671aa
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595918"
---
# <a name="how-to-create-unsigned-friend-assemblies-c"></a>Postupy: Vytvořit nepodepsaná Friend sestaveníC#()
Tento příklad ukazuje, jak použít sestavení typu Friend se sestaveními, která jsou bez znaménka.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Vytvoření sestavení a sestavení typu Friend  
  
1. Otevřete příkazový řádek.  
  
2. Vytvořte C# soubor s názvem `friend_unsigned_A.` , který obsahuje následující kód. Kód používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut k deklaraci friend_unsigned_B jako sestavení typu Friend.  
  
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
  
3. Zkompilujte a podepište friend_unsigned_A pomocí následujícího příkazu.  
  
    ```csharp  
    csc /target:library friend_unsigned_A.cs  
    ```  
  
4. Vytvořte C# soubor s názvem `friend_unsigned_B` , který obsahuje následující kód. Vzhledem k tomu, že friend_unsigned_A určuje friend_unsigned_B jako sestavení typu Friend, kód v `internal` friend_unsigned_B může přistupovat k typům a členům z friend_unsigned_A.  
  
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
  
5. Zkompilujte friend_unsigned_B pomocí následujícího příkazu.  
  
    ```csharp  
    csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    ```  
  
     Název sestavení, který je generován kompilátorem, se musí shodovat s názvem sestavení typu Friend, které je předáno <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributu. Je nutné explicitně zadat název výstupního sestavení (. exe nebo. dll) pomocí `/out` možnosti kompilátoru. Další informace naleznete v tématu [/out (C# možnosti kompilátoru)](../../../language-reference/compiler-options/out-compiler-option.md).  
  
6. Spusťte soubor friend_unsigned_B. exe.  
  
     Program vytiskne dva řetězce: "Class1. test" a "Class2. test".  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Existují podobnosti mezi <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributem <xref:System.Security.Permissions.StrongNameIdentityPermission> a třídou. Hlavním rozdílem je, <xref:System.Security.Permissions.StrongNameIdentityPermission> že může vyžadovat oprávnění zabezpečení ke spuštění konkrétní části kódu, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> zatímco `internal` atribut řídí viditelnost typů a členů.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Sestavení v .NET](../../../../standard/assembly/index.md)
- [Přátelská sestavení](../../../../standard/assembly/friend-assemblies.md)
- [Postupy: Vytvořit podepsaná sestavení typu FriendC#()](./how-to-create-signed-friend-assemblies.md)
- [Průvodce programováním v jazyce C#](../../index.md)

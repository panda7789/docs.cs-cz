---
title: 'Postupy: Vytváření nepodepsaných přátelských sestavení (C#)'
ms.date: 07/20/2015
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
ms.openlocfilehash: 7bf9a8bd18a1b98ae5e128ca67ca185baa7d599d
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745260"
---
# <a name="how-to-create-unsigned-friend-assemblies-c"></a>Postupy: Vytváření nepodepsaných přátelských sestavení (C#)
Tento příklad ukazuje způsob použití sestavení typu friend se sestaveními, která jsou bez znaménka.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Chcete-li vytvořit sestavení a sestavení typu friend  
  
1.  Otevřete příkazový řádek.  
  
2.  Vytvořte soubor jazyka C# s názvem `friend_unsigned_A.` , který obsahuje následující kód. Tento kód použije <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut pro deklaraci friend_unsigned_B jako sestavení typu friend.  
  
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
  
3.  Kompilace a podepsání friend_unsigned_A pomocí následujícího příkazu.  
  
    ```csharp  
    csc /target:library friend_unsigned_A.cs  
    ```  
  
4.  Vytvořte soubor jazyka C# s názvem `friend_unsigned_B` , který obsahuje následující kód. Protože friend_unsigned_A určuje friend_unsigned_B jako sestavení typu friend, můžete přístup ke kódu v friend_unsigned_B `internal` typy a členy z friend_unsigned_A.  
  
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
  
5.  Zkompilujte friend_unsigned_B pomocí následujícího příkazu.  
  
    ```csharp  
    csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    ```  
  
     Název sestavení, který je generován kompilátorem musí odpovídat názvu sestavení typu friend, která je předána <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut. Musíte explicitně zadat název výstupního sestavení (.exe nebo .dll) s použitím `/out` – možnost kompilátoru. Další informace najdete v tématu [/out (možnosti kompilátoru C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).  
  
6.  Spusťte soubor friend_unsigned_B.exe.  
  
     Program vytiskne dva řetězce: "Class1.Test" a "Class2.Test".  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Existují podobnost <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut a <xref:System.Security.Permissions.StrongNameIdentityPermission> třídy. Hlavní rozdíl je, že <xref:System.Security.Permissions.StrongNameIdentityPermission> může požadovat oprávnění zabezpečení ke spuštění konkrétní části kódu, zatímco <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut určuje, zda `internal` typy a členy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Sestavení v rozhraní .NET](../../../../standard/assembly/index.md)
- [Přátelská sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)
- [Postupy: Vytváření podepsaných přátelských sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)

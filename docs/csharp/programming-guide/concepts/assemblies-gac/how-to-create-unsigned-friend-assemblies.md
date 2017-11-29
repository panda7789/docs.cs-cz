---
title: "Postupy: vytváření nepodepsaných přátelských sestavení (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 854df39394ef10bf2404fb3f762586fb102fba7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-unsigned-friend-assemblies-c"></a>Postupy: vytváření nepodepsaných přátelských sestavení (C#)
Tento příklad ukazuje způsob použití přátelských sestavení s sestavení, které jsou bez znaménka.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Chcete-li vytvořit sestavení a přátelských sestavení  
  
1.  Otevřete příkazový řádek.  
  
2.  Vytvoření souboru C# s názvem `friend_signed_A.` obsahující následující kód. Kód používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut deklarovat friend_signed_B jako přátelského sestavení.  
  
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
  
3.  Kompilace a friend_signed_A se přihlaste pomocí následujícího příkazu.  
  
    ```csharp  
    csc /target:library friend_unsigned_A.cs  
    ```  
  
4.  Vytvoření souboru C# s názvem `friend_unsigned_B` obsahující následující kód. Protože friend_unsigned_A určuje friend_unsigned_B jako přátelského sestavení, můžete přístup k kód v friend_unsigned_B `internal` typy a členy z friend_unsigned_A.  
  
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
  
5.  Zkompilujte friend_signed_B pomocí následujícího příkazu.  
  
    ```csharp  
    csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    ```  
  
     Název sestavení, který je generovaný kompilátoru shodovat friend název sestavení, který je předán <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut. Musíte explicitně zadat název výstupu sestavení (.exe nebo .dll) pomocí `/out` – možnost kompilátoru. Další informace najdete v tématu [/out (možnosti kompilátoru C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).  
  
6.  Spusťte soubor friend_signed_B.exe.  
  
     Program vytiskne dva řetězce: "Class1.Test" a "Class2.Test".  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Existují podobnosti mezi <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut a <xref:System.Security.Permissions.StrongNameIdentityPermission> třídy. Hlavní rozdíl je, že <xref:System.Security.Permissions.StrongNameIdentityPermission> oprávnění zabezpečení ke spuštění konkrétní části kódu, můžete požadovat, zatímco <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut určuje, zda se `internal` typy a členy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Sestavení a globální mezipaměti sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [Přátelská sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [Postupy: vytváření podepsaných přátelských sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [Průvodce programováním v C#](../../../../csharp/programming-guide/index.md)

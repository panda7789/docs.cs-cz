---
title: "Postupy: vytváření podepsaných přátelských sestavení (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 79f5ff0615a572db162906c698c47196c6f045da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-signed-friend-assemblies-c"></a>Postupy: vytváření podepsaných přátelských sestavení (C#)
Tento příklad ukazuje způsob použití přátelských sestavení s sestavení, které mají silné názvy. Obě sestavení musí mít silné názvy. I když obě sestavení v tomto příkladu používat stejné klíče, můžete použít různé klíče pro dvě sestavení.  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>Chcete-li vytvořit podepsané sestavení a přátelských sestavení  
  
1.  Otevřete příkazový řádek.  
  
2.  Generování keyfile a zobrazit svůj veřejný klíč, použijte následující sekvence příkazů pomocí nástroje silného názvu. Další informace najdete v tématu [Sn.exe (nástroj silným názvem)](https://msdn.microsoft.com/library/k5b5tt23).  
  
    1.  Vygenerovat klíč silné jméno – v tomto příkladu a uložit ho do souboru FriendAssemblies.snk:  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  Extrahování veřejný klíč z FriendAssemblies.snk a umístí jej do FriendAssemblies.publickey:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  Zobrazí veřejný klíč uložený v souboru FriendAssemblies.publickey:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  Vytvoření souboru C# s názvem `friend_signed_A` obsahující následující kód. Kód používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut deklarovat friend_signed_B jako přátelského sestavení.  
  
     Nástroje pro silný název generuje nový veřejný klíč pokaždé, když ji spustí. Proto je potřeba nahradit veřejný klíč v následujícím kódu veřejný klíč, který jste právě vygenerovali, jak je znázorněno v následujícím příkladu.  
  
    ```csharp  
    // friend_signed_A.cs  
    // Compile with:   
    // csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    using System.Runtime.CompilerServices;  
  
    [assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")]  
    class Class1  
    {  
        public void Test()  
        {  
            System.Console.WriteLine("Class1.Test");  
            System.Console.ReadLine();  
        }  
    }  
    ```  
  
4.  Kompilace a friend_signed_A se přihlaste pomocí následujícího příkazu.  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5.  Vytvoření souboru C#, který je pojmenován `friend_signed_B` a obsahuje následující kód. Protože friend_signed_A určuje friend_signed_B jako přátelského sestavení, můžete přístup k kód v friend_signed_B `internal` typy a členy z friend_signed_A. Soubor obsahuje následující kód.  
  
    ```csharp  
    // friend_signed_B.cs  
    // Compile with:   
    // csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    public class Program  
    {  
        static void Main()  
        {  
            Class1 inst = new Class1();  
            inst.Test();  
        }  
    }  
    ```  
  
6.  Kompilace a friend_signed_B se přihlaste pomocí následujícího příkazu.  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     Název sestavení generované kompilátorem musí odpovídat názvu sestavení friend předaný <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut. Musíte explicitně zadat název výstupu sestavení (.exe nebo .dll) pomocí `/out` – možnost kompilátoru.  Další informace najdete v tématu [/out (možnosti kompilátoru C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).  
  
7.  Spusťte soubor friend_signed_B.exe.  
  
     Program vytiskne řetězec "Class1.Test".  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Existují podobnosti mezi <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut a <xref:System.Security.Permissions.StrongNameIdentityPermission> třídy. Hlavní rozdíl je, že <xref:System.Security.Permissions.StrongNameIdentityPermission> oprávnění zabezpečení ke spuštění konkrétní části kódu, můžete požadovat, zatímco <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut určuje, zda se `internal` typy a členy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Sestavení a globální mezipaměti sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [Přátelská sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [Postupy: vytváření nepodepsaných přátelských sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [/ keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [Sn.exe (nástroj pro silný název)](https://msdn.microsoft.com/library/k5b5tt23)  
 [Vytváření a používání sestavení se silným názvem](https://msdn.microsoft.com/library/xwb8f617)  
 [Průvodce programováním v C#](../../../../csharp/programming-guide/index.md)

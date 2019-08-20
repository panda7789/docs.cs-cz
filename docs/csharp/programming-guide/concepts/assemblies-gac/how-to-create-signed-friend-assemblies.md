---
title: 'Postupy: Vytvořit podepsaná sestavení typu FriendC#()'
ms.date: 07/20/2015
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
ms.openlocfilehash: 7715726a200150b044fb8e97216fa02d0e784838
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595923"
---
# <a name="how-to-create-signed-friend-assemblies-c"></a>Postupy: Vytvořit podepsaná sestavení typu FriendC#()
Tento příklad ukazuje, jak použít sestavení typu Friend se sestaveními, která mají silné názvy. Obě sestavení musí mít silný název. I když obě sestavení v tomto příkladu používají stejné klíče, můžete použít různé klíče pro dvě sestavení.  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>Vytvoření podepsaného sestavení a sestavení typu Friend  
  
1. Otevřete příkazový řádek.  
  
2. Použijte následující posloupnost příkazů s nástrojem silného názvu k vygenerování souboru klíče a k zobrazení jeho veřejného klíče. Další informace naleznete v tématu [sn. exe (Nástroj pro silný název)](../../../../framework/tools/sn-exe-strong-name-tool.md).  
  
    1. Vygenerujte klíč se silným názvem pro tento příklad a uložte ho do souboru FriendAssemblies. snk:  
  
         `sn -k FriendAssemblies.snk`  
  
    2. Extrahujte veřejný klíč z FriendAssemblies. snk a vložte ho do FriendAssemblies. PublicKey:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. Zobrazit veřejný klíč uložený v souboru FriendAssemblies. PublicKey:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. Vytvořte C# soubor s názvem `friend_signed_A` , který obsahuje následující kód. Kód používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut k deklaraci friend_signed_B jako sestavení typu Friend.  
  
     Nástroj silného názvu vygeneruje nový veřejný klíč při každém spuštění. Proto je nutné nahradit veřejný klíč v následujícím kódu veřejným klíčem, který jste právě vygenerovali, jak je znázorněno v následujícím příkladu.  
  
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
  
4. Zkompilujte a podepište friend_signed_A pomocí následujícího příkazu.  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5. Vytvořte C# soubor s názvem `friend_signed_B` a obsahující následující kód. Vzhledem k tomu, že friend_signed_A určuje friend_signed_B jako sestavení typu Friend, kód v `internal` friend_signed_B může přistupovat k typům a členům z friend_signed_A. Soubor obsahuje následující kód.  
  
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
  
6. Zkompilujte a podepište friend_signed_B pomocí následujícího příkazu.  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     Název sestavení generované kompilátorem se musí shodovat s názvem sestavení typu Friend předanému <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributu. Je nutné explicitně zadat název výstupního sestavení (. exe nebo. dll) pomocí `/out` možnosti kompilátoru.  Další informace naleznete v tématu [/out (C# možnosti kompilátoru)](../../../language-reference/compiler-options/out-compiler-option.md).  
  
7. Spusťte soubor friend_signed_B. exe.  
  
     Program vytiskne řetězec "Class1. test".  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Existují podobnosti mezi <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributem <xref:System.Security.Permissions.StrongNameIdentityPermission> a třídou. Hlavním rozdílem je, <xref:System.Security.Permissions.StrongNameIdentityPermission> že může vyžadovat oprávnění zabezpečení ke spuštění konkrétní části kódu, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> zatímco `internal` atribut řídí viditelnost typů a členů.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Sestavení v .NET](../../../../standard/assembly/index.md)
- [Přátelská sestavení](../../../../standard/assembly/friend-assemblies.md)
- [Postupy: Vytvořit nepodepsaná Friend sestaveníC#()](./how-to-create-unsigned-friend-assemblies.md)
- [/keyfile](../../../language-reference/compiler-options/keyfile-compiler-option.md)
- [Sn.exe (nástroj pro silný název)](../../../../framework/tools/sn-exe-strong-name-tool.md)
- [Vytváření a používání sestavení se silným názvem](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md)
- [Průvodce programováním v jazyce C#](../../index.md)

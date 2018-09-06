---
title: 'Postupy: vytváření podepsaných přátelských sestavení (C#)'
ms.date: 07/20/2015
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
ms.openlocfilehash: 8f310055db6899bf315310efc22b67bca2c4500f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874849"
---
# <a name="how-to-create-signed-friend-assemblies-c"></a>Postupy: vytváření podepsaných přátelských sestavení (C#)
Tento příklad ukazuje způsob použití sestavení typu friend se sestaveními, která mít silné názvy. Obě sestavení musí být silný název. Přestože obě sestavení v tomto příkladu pomocí stejných klíčů, můžete použít různé klíče pro dvě sestavení.  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>Chcete-li vytvořit podepsané sestavení a sestavení typu friend  
  
1.  Otevřete příkazový řádek.  
  
2.  Použijte následující posloupnost příkazů s nástroj Strong Name keyfile generovat a zobrazit jeho veřejný klíč. Další informace najdete v tématu [Sn.exe (nástroj Strong Name)](../../../../framework/tools/sn-exe-strong-name-tool.md).  
  
    1.  Vygenerování klíče se silným názvem v tomto příkladu a uložit ho do souboru FriendAssemblies.snk:  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  Extrahujte veřejný klíč z FriendAssemblies.snk a vložit ho do FriendAssemblies.publickey:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  Zobrazení veřejného klíče uložené v souboru FriendAssemblies.publickey:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  Vytvořte soubor jazyka C# s názvem `friend_signed_A` , který obsahuje následující kód. Tento kód použije <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut pro deklaraci friend_signed_B jako sestavení typu friend.  
  
     Nástroj Strong Name vygeneruje nový veřejný klíč pokaždé, když ji spustí. Proto je potřeba nahradit veřejný klíč v následujícím kódu veřejný klíč, který jste právě vygenerovali, jak je znázorněno v následujícím příkladu.  
  
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
  
4.  Kompilace a podepsání friend_signed_A pomocí následujícího příkazu.  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5.  Vytvořte soubor jazyka C#, který je pojmenován `friend_signed_B` a obsahuje následující kód. Protože friend_signed_A určuje friend_signed_B jako sestavení typu friend, můžete přístup ke kódu v friend_signed_B `internal` typy a členy z friend_signed_A. Soubor obsahuje následující kód.  
  
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
  
6.  Kompilace a podepsání friend_signed_B pomocí následujícího příkazu.  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     Název sestavení generovaný kompilátorem musí odpovídat názvu sestavení typu friend předán <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut. Musíte explicitně zadat název výstupního sestavení (.exe nebo .dll) s použitím `/out` – možnost kompilátoru.  Další informace najdete v tématu [/out (možnosti kompilátoru C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).  
  
7.  Spusťte soubor friend_signed_B.exe.  
  
     Program zobrazí řetězec "Class1.Test".  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Existují podobnost <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut a <xref:System.Security.Permissions.StrongNameIdentityPermission> třídy. Hlavní rozdíl je, že <xref:System.Security.Permissions.StrongNameIdentityPermission> může požadovat oprávnění zabezpečení ke spuštění konkrétní části kódu, zatímco <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut určuje, zda `internal` typy a členy.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
- [Sestavení a globální mezipaměti sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
- [Přátelská sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
- [Postupy: vytváření nepodepsaných přátelských sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
- [/keyfile](../../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)  
- [Sn.exe (nástroj pro silný název)](../../../../framework/tools/sn-exe-strong-name-tool.md)  
- [Vytváření a používání sestavení se silným názvem](../../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
- [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)

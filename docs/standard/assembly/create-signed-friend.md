---
title: 'Postup: Vytvoření podepsaných sestavení přátel'
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 9912fa70014a8828e994cf528644aaa7cb351fea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159491"
---
# <a name="how-to-create-signed-friend-assemblies"></a>Postup: Vytvoření podepsaných sestavení přátel
Tento příklad ukazuje, jak používat sestavení přátel s sestaveními, které mají silné názvy. Obě sestavení musí být silné pojmenované. Přestože obě sestavení v tomto příkladu používají stejné klíče, můžete použít různé klíče pro dvě sestavení.  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a>Vytvoření podepsaného sestavení a sestavy přítele  
  
1. Otevřete příkazový řádek.  
  
2. Pomocí následující posloupnosti příkazů s nástrojem Silný název vygenerujte soubor kláves a zobrazte jeho veřejný klíč. Další informace naleznete v [tématu Sn.exe (nástroj silný název).](../../framework/tools/sn-exe-strong-name-tool.md)  
  
    1. Vygenerujte klíč silného názvu pro tento příklad a uložte jej do souboru *FriendAssemblies.snk*:  
  
         `sn -k FriendAssemblies.snk`  
  
    2. Extrahujte veřejný klíč z *FriendAssemblies.snk* a vložte jej do *FriendAssemblies.publickey*:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. Zobrazí veřejný klíč uložený v souboru *FriendAssemblies.publickey*:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. Vytvořte soubor jazyka C# nebo Visual Basic s názvem *friend_signed_A,* který obsahuje následující kód. Kód používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut deklarovat *friend_signed_B* jako sestavení přítele.  

   Nástroj Silný název vygeneruje nový veřejný klíč při každém spuštění. Proto je nutné nahradit veřejný klíč v následujícím kódu veřejným klíčem, který jste právě vygenerovali, jak je znázorněno v následujícím příkladu.  

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

   ```vb  
   ' friend_signed_A.vb  
   ' Compile with:
   ' Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   Imports System.Runtime.CompilerServices  

   <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>
   Public Class Class1  
       Public Sub Test()  
           System.Console.WriteLine("Class1.Test")  
           System.Console.ReadLine()  
       End Sub  
   End Class  
   ```  

4. Kompilujte a podepište *friend_signed_A* pomocí následujícího příkazu.  

   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  

   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  

5. Vytvořte soubor jazyka C# nebo Visual Basic s názvem *friend_signed_B,* který obsahuje následující kód. Vzhledem k tomu, *že friend_signed_A* určuje *friend_signed_B* `internal` jako sestavení přítele, kód v *friend_signed_B* může přistupovat (C#) nebo `Friend` (Visual Basic) typy a členy z *friend_signed_A*. Soubor obsahuje následující kód.  

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

   ```vb  
   ' friend_signed_B.vb  
   ' Compile with:
   ' Vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   Module Sample  
       Public Sub Main()  
           Dim inst As New Class1  
           inst.Test()  
       End Sub  
   End Module  
   ```  

6. Kompilace a podepisování *friend_signed_B* pomocí následujícího příkazu.  

   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  

   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  

   Název sestavení generovanékompilátorem musí odpovídat názvu sestavení friend <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> předaném atributu. Je nutné explicitně zadat název výstupního sestavení (*.exe* `-out` nebo *.dll*) pomocí možnosti kompilátoru. Další informace naleznete [v tématu -out (C# možnosti kompilátoru)](../../csharp/language-reference/compiler-options/out-compiler-option.md) nebo [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).  

7. Spusťte soubor *friend_signed_B.exe.*  

   Program vyveze řetězec **Class1.Test**.  
  
## <a name="net-security"></a>Zabezpečení .NET  
 Existují podobnosti mezi <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributem <xref:System.Security.Permissions.StrongNameIdentityPermission> a třídou. Hlavní <xref:System.Security.Permissions.StrongNameIdentityPermission> rozdíl je, že můžete požadovat oprávnění zabezpečení ke spuštění <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> určité části kódu, zatímco atribut řídí viditelnost `internal` (C#) nebo `Friend` (Visual Basic) typy a členy.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Sestavení v .NET](index.md)
- [Přátelská sestavení](friend.md)
- [Postup: Vytvoření nepodepsaných sestavení přátel](create-unsigned-friend.md)
- [-keyfile (C#)](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [-keyfile (Visual Basic)](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [Sn.exe (nástroj silný název)](../../framework/tools/sn-exe-strong-name-tool.md)
- [Vytváření a používání sestavení se silným názvem](create-use-strong-named.md)
- [Průvodce programováním v C#](../../csharp/programming-guide/index.md)
- [Koncepty programování (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)

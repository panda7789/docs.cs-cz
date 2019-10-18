---
title: 'Postupy: Vytváření podepsaných přátelských sestavení'
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 3bf71adc694f3c6e072990717198b4f2003cd503
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523882"
---
# <a name="how-to-create-signed-friend-assemblies"></a>Postupy: Vytváření podepsaných přátelských sestavení
Tento příklad ukazuje, jak použít sestavení typu Friend se sestaveními, která mají silné názvy. Obě sestavení musí mít silný název. I když obě sestavení v tomto příkladu používají stejné klíče, můžete použít různé klíče pro dvě sestavení.  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a>Vytvořit podepsané sestavení a sestavení typu Friend  
  
1. Otevřete příkazový řádek.  
  
2. Použijte následující posloupnost příkazů s nástrojem silného názvu k vygenerování souboru klíče a k zobrazení jeho veřejného klíče. Další informace naleznete v tématu [sn. exe (Nástroj pro silný název)](../../framework/tools/sn-exe-strong-name-tool.md).  
  
    1. Vygenerujte klíč se silným názvem pro tento příklad a uložte ho do souboru *FriendAssemblies. snk*:  
  
         `sn -k FriendAssemblies.snk`  
  
    2. Extrahujte veřejný klíč z *FriendAssemblies. snk* a vložte ho do *FriendAssemblies. PublicKey*:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. Zobrazit veřejný klíč uložený v souboru *FriendAssemblies. PublicKey*:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. Vytvořte soubor C# nebo Visual Basic s názvem *friend_signed_A* , který obsahuje následující kód. Kód používá atribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> k deklaraci *friend_signed_B* jako sestavení typu Friend.  
   
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
   
4. Zkompilujte a podepište *friend_signed_A* pomocí následujícího příkazu.  
   
   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  
   
   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  
   
5. Vytvořte soubor C# nebo Visual Basic s názvem *friend_signed_B* , který obsahuje následující kód. Vzhledem k tomu, že *friend_signed_A* Určuje *friend_signed_B* jako sestavení typu Friend, kód v *friend_signed_B* můžeC#přistupovat k typům `internal` () nebo `Friend` (Visual Basic) a členům z *friend_signed_A*. Soubor obsahuje následující kód.  
   
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
   
6. Zkompilujte a podepište *friend_signed_B* pomocí následujícího příkazu.  
   
   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  
   
   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  
   
   Název sestavení generované kompilátorem se musí shodovat s názvem sestavení typu Friend předanému atributu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Musíte explicitně zadat název výstupního sestavení ( *. exe* nebo *. dll*) pomocí možnosti kompilátoru `/out`. Další informace naleznete v tématu [/out (C# možnosti kompilátoru)](../../csharp/language-reference/compiler-options/out-compiler-option.md) nebo [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).  
   
7. Spusťte soubor *friend_signed_B. exe* .  
   
   Program vytvoří výstup řetězce **Class1. test**.  
  
## <a name="net-security"></a>Zabezpečení .NET  
 Existují podobnosti mezi atributem <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> a třídou <xref:System.Security.Permissions.StrongNameIdentityPermission>. Hlavním rozdílem je, že <xref:System.Security.Permissions.StrongNameIdentityPermission> může vyžadovat oprávnění zabezpečení ke spuštění konkrétní části kódu, zatímco atribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> řídí viditelnost typů a členů `internal` (C#) nebo `Friend` (Visual Basic).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Sestavení v .NET](index.md)
- [Friend – sestavení](friend.md)
- [Postupy: vytváření nepodepsaných přátelských sestavení](create-unsigned-friend.md)
- [-keyfile (C#)](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [-keyfile (Visual Basic)](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [SN. exe (Nástroj pro silný název)](../../framework/tools/sn-exe-strong-name-tool.md)
- [Vytváření a používání sestavení se silným názvem](create-use-strong-named.md)
- [C#Průvodce programováním](../../csharp/programming-guide/index.md)
- [Koncepty programování (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)

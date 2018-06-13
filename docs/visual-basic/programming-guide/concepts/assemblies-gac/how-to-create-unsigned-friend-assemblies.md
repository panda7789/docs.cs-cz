---
title: 'Postupy: vytváření nepodepsaných přátelských sestavení (Visual Basic)'
ms.date: 03/14/2018
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 873a5bf235b43b4460a1489a964539c4e4c18de3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643062"
---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a>Postupy: vytváření nepodepsaných přátelských sestavení (Visual Basic)
Tento příklad ukazuje způsob použití přátelských sestavení s sestavení, které jsou bez znaménka.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Chcete-li vytvořit sestavení a přátelských sestavení  
  
1.  Otevřete příkazový řádek.  
  
2.  Vytvořte soubor jazyka Visual Basic s názvem `friend_signed_A.` obsahující následující kód. Kód používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut deklarovat friend_signed_B jako přátelského sestavení.  
  
    ```vb  
    ' friend_unsigned_A.vb  
    ' Compile with:   
    ' vbc -target:library friend_unsigned_A.vb  
    Imports System.Runtime.CompilerServices  
    Imports System  
  
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
  
3.  Kompilace a friend_signed_A se přihlaste pomocí následujícího příkazu.  
  
    ```console  
    vbc -target:library friend_unsigned_A.vb  
    ```  
  
4.  Vytvořte soubor jazyka Visual Basic s názvem `friend_unsigned_B` obsahující následující kód. Protože friend_unsigned_A určuje friend_unsigned_B jako přátelského sestavení, můžete přístup k kód v friend_unsigned_B `Friend` typy a členy z friend_unsigned_A.  
  
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
  
5.  Zkompilujte friend_signed_B pomocí následujícího příkazu.  
  
    ```console
    vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb  
    ```  
  
     Název sestavení, který je generovaný kompilátoru shodovat friend název sestavení, který je předán <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut. Sestavení je možné nastavit explicitně pomocí `/out` – možnost kompilátoru.  
  
6.  Spusťte soubor friend_signed_B.exe.  
  
     Program zobrazí dva řetězce: "Class1.Test" a "Class2.Test".  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Existují podobnosti mezi <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut a <xref:System.Security.Permissions.StrongNameIdentityPermission> třídy. Hlavní rozdíl je, že <xref:System.Security.Permissions.StrongNameIdentityPermission> oprávnění zabezpečení ke spuštění konkrétní části kódu, můžete požadovat, zatímco <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut určuje, zda se `Friend` typy a členy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Sestavení a globální mezipaměti sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Přátelská sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [Postupy: vytváření podepsaných přátelských sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [Programování konceptů Průvodce](../../../../visual-basic/programming-guide/concepts/index.md)

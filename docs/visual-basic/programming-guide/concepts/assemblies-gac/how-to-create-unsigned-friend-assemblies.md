---
title: 'Postupy: Vytváření nepodepsaných přátelských sestavení (Visual Basic)'
ms.date: 03/14/2018
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
ms.openlocfilehash: f5e475f3a0fdc9350e43b89db16724ef0f544071
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369562"
---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a>Postupy: Vytváření nepodepsaných přátelských sestavení (Visual Basic)
Tento příklad ukazuje způsob použití sestavení typu friend se sestaveními, která jsou bez znaménka.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Chcete-li vytvořit sestavení a sestavení typu friend  
  
1.  Otevřete příkazový řádek.  
  
2.  Vytvořte soubor jazyka Visual Basic `friend_signed_A.` , který obsahuje následující kód. Tento kód použije <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut pro deklaraci friend_signed_B jako sestavení typu friend.  
  
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
  
3.  Kompilace a podepsání friend_signed_A pomocí následujícího příkazu.  
  
    ```console  
    vbc -target:library friend_unsigned_A.vb  
    ```  
  
4.  Vytvořte soubor jazyka Visual Basic `friend_unsigned_B` , který obsahuje následující kód. Protože friend_unsigned_A určuje friend_unsigned_B jako sestavení typu friend, můžete přístup ke kódu v friend_unsigned_B `Friend` typy a členy z friend_unsigned_A.  
  
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
  
     Název sestavení, který je generován kompilátorem musí odpovídat názvu sestavení typu friend, která je předána <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut. Sestavení můžete explicitně nastavit pomocí `/out` – možnost kompilátoru.  
  
6.  Spusťte soubor friend_signed_B.exe.  
  
     Program zobrazí dva řetězce: "Class1.Test" a "Class2.Test".  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Existují podobnost <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut a <xref:System.Security.Permissions.StrongNameIdentityPermission> třídy. Hlavní rozdíl je, že <xref:System.Security.Permissions.StrongNameIdentityPermission> může požadovat oprávnění zabezpečení ke spuštění konkrétní části kódu, zatímco <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut určuje, zda `Friend` typy a členy.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Sestavení v .NET](../../../../standard/assembly/index.md)
- [Přátelská sestavení](../../../../standard/assembly/friend-assemblies.md)
- [Postupy: Vytváření podepsaných přátelských sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [Průvodce koncepty programování](../../../../visual-basic/programming-guide/concepts/index.md)

---
title: "Postupy: vytváření nepodepsaných přátelských sestavení (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a2b2667c60a07a2897a0934d210901042e2e43c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a>Postupy: vytváření nepodepsaných přátelských sestavení (Visual Basic)
Tento příklad ukazuje způsob použití přátelských sestavení s sestavení, které jsou bez znaménka.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Chcete-li vytvořit sestavení a přátelských sestavení  
  
1.  Otevřete příkazový řádek.  
  
2.  Vytvořte soubor jazyka Visual Basic s názvem `friend_signed_A.` obsahující následující kód. Kód používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut deklarovat friend_signed_B jako přátelského sestavení.  
  
    ```vb  
    ' friend_unsigned_A.vb  
    ' Compile with:   
    ' Vbc /target:library friend_unsigned_A.vb  
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
  
    ```vb  
    Vbc /target:library friend_unsigned_A.vb  
    ```  
  
4.  Vytvořte soubor jazyka Visual Basic s názvem `friend_unsigned_B` obsahující následující kód. Protože friend_unsigned_A určuje friend_unsigned_B jako přátelského sestavení, můžete přístup k kód v friend_unsigned_B `Friend` typy a členy z friend_unsigned_A.  
  
    ```vb  
    ' friend_unsigned_B.vb  
    ' Compile with:   
    ' Vbc /r:friend_unsigned_A.dll friend_unsigned_B.vb  
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
  
    ```vb  
    Vbc /r:friend_unsigned_A.dll friend_unsigned_B.vb  
    ```  
  
     Název sestavení, který je generovaný kompilátoru shodovat friend název sestavení, který je předán <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut. Sestavení je možné nastavit explicitně pomocí `/out` – možnost kompilátoru.  
  
6.  Spusťte soubor friend_signed_B.exe.  
  
     Program vytiskne dva řetězce: "Class1.Test" a "Class2.Test".  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Existují podobnosti mezi <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut a <xref:System.Security.Permissions.StrongNameIdentityPermission> třídy. Hlavní rozdíl je, že <xref:System.Security.Permissions.StrongNameIdentityPermission> oprávnění zabezpečení ke spuštění konkrétní části kódu, můžete požadovat, zatímco <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut určuje, zda se `Friend` typy a členy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Sestavení a globální mezipaměti sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Přátelská sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [Postupy: vytváření podepsaných přátelských sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [Programování konceptů Průvodce](../../../../visual-basic/programming-guide/concepts/index.md)

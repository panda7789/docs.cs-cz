---
title: Přátelská sestavení (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b3d5716-e6e4-47a7-a3e9-084d7fba5c28
ms.openlocfilehash: 91bc33f33c4fc34c6e0f3ae197ecd2b876161de3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644378"
---
# <a name="friend-assemblies-visual-basic"></a>Přátelská sestavení (Visual Basic)
A *přátelského sestavení* je sestavení, které můžete přístup k jiné sestavení [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) typy a členy. Pokud identifikovat sestavení jako přátelského sestavení, již není k označení typy a členy jako veřejné, aby k nim přístup ostatních sestavení. To je zvlášť vhodné v následujících scénářích:  
  
-   Během testování částí, při spuštění testovacího kódu v samostatné sestavení, ale vyžaduje přístupu ke členům v sestavení testuje, které jsou označeny jako `Friend`.  
  
-   Pokud vyvíjíte knihovny tříd a přidané do knihovny jsou obsaženy v samostatné sestavení, ale vyžadují přístup ke členům v existujících sestavení, které jsou označeny jako `Friend`.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut k identifikaci jeden nebo více sestavení, přítele pro zadaného sestavení. Následující příklad používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> v sestavení A a určuje sestavení `AssemblyB` jako přátelského sestavení. Díky tomu sestavení `AssemblyB` přístup ke všem typy a členy v sestavení, které jsou označeny jako `Friend`.  
  
> [!NOTE]
>  Při kompilaci sestavení (sestavení `AssemblyB`), bude přístup k interní typy nebo interní členy jiné sestavení (sestavení *A*), musíte explicitně zadat název výstupního souboru (.exe nebo .dll) pomocí **/out** – možnost kompilátoru. To je potřeba, protože kompilátor ještě nebyl vygenerován název sestavení, ve kterém je sestavení v době, kdy je vytvoření vazby na externí odkazy. Další informace najdete v tématu [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).  
  
```vb  
Imports System.Runtime.CompilerServices  
Imports System  
<Assembly: InternalsVisibleTo("AssemblyB")>   
  
' Friend class.  
Friend Class FriendClass  
    Public Sub Test()  
        Console.WriteLine("Sample Class")  
    End Sub  
End Class  
  
' Public class with a Friend method.  
Public Class ClassWithFriendMethod  
    Friend Sub Test()  
        Console.WriteLine("Sample Method")  
    End Sub  
End Class  
```  
  
 Pouze sestavení, která explicitně zadáte jako přístup přátel `Friend` typy a členy. Například pokud je sestavení B přátelských sestavení A a sestavení C odkazy na sestavení B, C nemá přístup k `Friend` typy v A.  
  
 Kompilátor provádí základní ověření předaný název sestavení friend <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut. Pokud sestavení *A* deklaruje *B* jako přátelského sestavení ověřovacích pravidel jsou následující:  
  
-   Pokud sestavení *A* se silným názvem, sestavení *B* musí také mít silné název. Název sestavení friend, který je předán do atribut musí obsahovat název sestavení a veřejného klíče pro silné jméno – klíč, který se používá k podepsání sestavení *B*.  
  
     Název sestavení friend, který je předán <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut nemůže být silného názvu sestavení *B*: nezahrnují verze sestavení, jazykovou verzi, architektury nebo tokenu veřejného klíče.  
  
-   Pokud sestavení *A* není silné s názvem, přítele název sestavení by měla obsahovat jenom název sestavení. Další informace najdete v tématu [postupy: vytváření nepodepsaných přátelských sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).  
  
-   Pokud sestavení *B* je silné s názvem, je nutné zadat silné jméno – klíč pro sestavení *B* pomocí nastavení projektu nebo příkazového řádku `/keyfile` – možnost kompilátoru. Další informace najdete v tématu [postupy: vytvoření podepsané přátelská sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).  
  
 <xref:System.Security.Permissions.StrongNameIdentityPermission> Třída rovněž poskytuje možnost sdílet typy, s následující rozdíly:  
  
-   <xref:System.Security.Permissions.StrongNameIdentityPermission> platí pro typ jednotlivých během přátelského sestavení celá sestava.  
  
-   Pokud se používají stovky typy v sestavení *A* , kterou chcete sdílet s sestavení *B*, budete muset přidat <xref:System.Security.Permissions.StrongNameIdentityPermission> ke všem z nich. Pokud používáte přátelského sestavení, musíte pouze deklarovat vztah friend jednou.  
  
-   Pokud používáte <xref:System.Security.Permissions.StrongNameIdentityPermission>, typy, které chcete sdílet muset být deklarována jako veřejné. Pokud používáte přátelského sestavení, sdílené typy jsou deklarovány jako `Friend`.  
  
 Informace o tom, jak přistupovat sestavení `Friend` typy a metody ze souboru modulu (soubor s příponou .netmodule), najdete v části [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 <xref:System.Security.Permissions.StrongNameIdentityPermission>  
 [Postupy: vytváření nepodepsaných přátelských sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [Postupy: vytváření podepsaných přátelských sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [Sestavení a globální mezipaměti sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Koncepty programování](../../../../visual-basic/programming-guide/concepts/index.md)

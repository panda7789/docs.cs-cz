---
title: Přátelská sestavení
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: 6387e93bcd4efeec57ada9228dcaf015d053dbf7
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973234"
---
# <a name="friend-assemblies"></a>Přátelská sestavení

*Sestavení typu Friend* je sestavení, které má přístup k [interním](../../csharp/language-reference/keywords/internal.md) typůmC#() nebo [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) jiného sestavení a k těmto členům. Pokud identifikujete sestavení jako sestavení typu Friend, již není nutné označit typy a členy jako veřejné, aby byly přístupné z jiných sestavení. To je zvlášť užitečné v následujících scénářích:

- Při testování částí, při spuštění testovacího kódu v samostatném sestavení, ale vyžaduje přístup ke členům v testovaném sestavení, které jsou `internal` označeny C# jako `Friend` v nebo v Visual Basic.

- Při vývoji knihovny tříd a přidání do knihovny jsou obsaženy v samostatných sestaveních, ale vyžadují přístup ke členům v existujících sestaveních, která jsou označena `internal` jako C# v `Friend` nebo v Visual Basic.

## <a name="remarks"></a>Poznámky

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Atribut můžete použít k identifikaci jednoho nebo více sestavení typu Friend pro dané sestavení. Následující příklad používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut v *sestavení a* a určuje sestavení *AssemblyB* jako sestavení typu Friend. To dává sestavení *AssemblyB* přístup ke všem typům a členům v *sestavení a* , které jsou `internal` označeny C# jako `Friend` v nebo v Visual Basic.

> [!NOTE]
> Při kompilaci sestavení, jako je *AssemblyB* , který bude přistupovat k interním typům nebo interním členům jiného sestavení, jako je *sestavení A*, je nutné explicitně zadat název výstupního souboru ( *. exe* nebo *. dll*) pomocí **/out** možnost kompilátoru To je nutné, protože kompilátor ještě negeneroval název sestavení, který sestaví, v době, kdy je svázán s externími odkazy. Další informace naleznete v tématu [/out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) nebo [/out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).

```csharp
using System.Runtime.CompilerServices;
using System;

[assembly: InternalsVisibleTo("AssemblyB")]

// The class is internal by default.
class FriendClass
{
    public void Test()
    {
        Console.WriteLine("Sample Class");
    }
}

// Public class that has an internal method.
public class ClassWithFriendMethod
{
    internal void Test()
    {
        Console.WriteLine("Sample Method");
    }

}
```

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

Pouze sestavení, která explicitně zadáte jako přátelé, `internal` mohouC#přistupovat k `Friend` typům a členům () nebo (Visual Basic). Například pokud je *AssemblyB* přítele *sestavení* a a *sestavení c* odkazuje na *AssemblyB*, *sestavení c* nemá přístup k `internal` typům (C#) nebo `Friend` (Visual Basic) v *sestavení a* .

Kompilátor provede základní ověření názvu sestavení typu Friend předaného <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributu. Pokud *sestavení A* deklaruje *AssemblyB* jako sestavení typu Friend, ověřovací pravidla jsou následující:

- Pokud je *sestavení A* silně pojmenované, *AssemblyB* musí také mít silný název. Název sestavení typu Friend, který je předán atributu, musí obsahovat název sestavení a veřejný klíč klíče silného názvu, který se používá k podepsání *AssemblyB*.

     Název sestavení typu Friend, který je předán <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributu, nemůže být silným názvem *AssemblyB*. Nezahrnujte verze sestavení, jazykovou verzi, architekturu nebo token veřejného klíče.

- Pokud *sestavení A* není silného názvu, název sestavení typu Friend by měl obsahovat pouze název sestavení. Další informace najdete v tématu [jak: Vytvořte nepodepsaná sestavení](create-unsigned-friend.md)typu Friend.

- Pokud je *AssemblyB* silným názvem, je nutné zadat klíč silného názvu pro *AssemblyB* pomocí nastavení projektu nebo možnosti kompilátoru příkazového řádku `/keyfile` . Další informace najdete v tématu [jak: Vytvořit podepsaná sestavení](create-signed-friend.md)typu Friend.

 <xref:System.Security.Permissions.StrongNameIdentityPermission> Třída také poskytuje možnost sdílet typy s následujícími rozdíly:

- <xref:System.Security.Permissions.StrongNameIdentityPermission>platí pro individuální typ, zatímco sestavení typu Friend se vztahuje na celé sestavení.

- Pokud existují stovky typů v *sestavení A* , které chcete sdílet s *AssemblyB*, musíte je přidat <xref:System.Security.Permissions.StrongNameIdentityPermission> do všech. Použijete-li sestavení typu Friend, stačí pouze deklarovat relaci typu Friend.

- Pokud používáte, musí být typy, které chcete sdílet, deklarovány jako veřejné. <xref:System.Security.Permissions.StrongNameIdentityPermission> Pokud používáte sestavení typu Friend, sdílené typy jsou deklarovány jako `internal` (C#) nebo `Friend` (Visual Basic).

Informace o tom, jak získat přístup k typůmC#a metodám `Friend` sestavení `internal` () nebo (Visual Basic) ze souboru modulu (soubor s příponou *. netmodule* ), naleznete v tématu [/moduleassemblynameC#()](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) nebo [/ moduleassemblyname – (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [Postupy: Vytvořit nepodepsaná sestavení typu Friend](create-unsigned-friend.md)
- [Postupy: Vytvořit podepsaná sestavení typu Friend](create-signed-friend.md)
- [Sestavení v .NET](index.md)
- [C#Průvodce programováním](../../csharp/programming-guide/index.md)
- [Koncepty programování (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)

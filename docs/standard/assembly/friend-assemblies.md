---
title: Přátelská sestavení (C#)
ms.date: 03/03/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
ms.openlocfilehash: 770eb70a5350d7d26e03cb4e605b442100da2a53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61627871"
---
# <a name="friend-assemblies"></a>Přátelská sestavení

A *sestavení typu friend* je sestavení, které můžou přistupovat k jiné sestavení [interní](../../csharp/language-reference/keywords/internal.md) (v C# nebo [Friend](../../visual-basic/language-reference/modifiers/friend.md) v jazyce Visual Basic) typy a členy. Pokud identifikujete sestavení jako sestavení typu friend, máte již označit typy a členy jako veřejné je přístupná pomocí jiné sestavení. To je zvlášť vhodné v následujících scénářích:

- Během testování částí, pokud testovací kód je spuštěn samostatné sestavení ale vyžaduje přístup k členům v sestavení, testování, která jsou označena jako `internal` v C# nebo `Friend` v jazyce Visual Basic.

- Když vyvíjíte knihovny tříd a dodatky ke knihovně jsou obsaženy v samostatné sestavení, ale vyžadují přístup ke členům v existující sestavení, které jsou označeny jako `internal` v C# nebo `Friend` v jazyce Visual Basic.

## <a name="remarks"></a>Poznámky

Můžete použít <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut k identifikaci přátelských sestavení pro dané sestavení. V následujícím příkladu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut v sestavení A a určuje sestavení `AssemblyB` jako sestavení typu friend. To umožňuje sestavení `AssemblyB` přístup pro všechny typy a členy v sestavení, které jsou označeny jako `internal` v C# nebo `Friend` v jazyce Visual Basic.

> [!NOTE]
> Pokud kompilujete sestavení (sestavení `AssemblyB`), které budou přistupovat k interní typy nebo interní členy jiné sestavení (sestavení *A*), musíte explicitně zadat název výstupního souboru (.exe nebo .dll) s použitím **/out** – možnost kompilátoru. To je požadované, protože kompilátor nebyl zatím nevygenerovaly název sestavení, ve kterém je sestavení v době, kdy je vytvoření vazby na externí odkazy. Další informace najdete v tématu [/out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) nebo [/out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

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

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

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

---

Pouze sestavení, která explicitně zadáte jako přátelé dostanete `internal` (v C# nebo `Friend` v jazyce Visual Basic) typy a členy. Například, pokud sestavení B je přátelská sestavení A a sestavení C odkazy na sestavení B, C nemá přístup k `internal` (v C# nebo `Friend` v jazyce Visual Basic) typy v A.

Kompilátor provádí nějaké základní ověření předat název sestavení typu friend <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut. Pokud sestavení *A* deklaruje *B* jako sestavení typu friend, ověřovacích pravidel jsou následující:

- Pokud sestavení *A* je silný název sestavení *B* musí také být silný název. Název sestavení typu friend, který je předán atributu musí obsahovat název sestavení a veřejný klíč, který se používá k podepsání sestavení silným názvem klíče *B*.

     Název sestavení typu friend, který je předán <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut nemůže být silný název sestavení *B*: nezahrnují sestavení verze, jazykovou verzi, architektury nebo token veřejného klíče.

- Pokud sestavení *A* není silným názvem, název sestavení typu friend musí obsahovat pouze název sestavení. Další informace najdete v tématu [jak: Vytváření nepodepsaných přátelských sestavení (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) nebo [jak: Vytváření nepodepsaných přátelských sestavení (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).

- Pokud sestavení *B* je silným názvem, je nutné zadat klíče silného názvu pro sestavení *B* pomocí nastavení projektu nebo příkazového řádku `/keyfile` – možnost kompilátoru. Další informace najdete v tématu [jak: Vytváření podepsaných přátelských sestavení (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) nebo [jak: Vytváření podepsaných přátelských sestavení (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).

 <xref:System.Security.Permissions.StrongNameIdentityPermission> Třída rovněž poskytuje možnost sdílení typů, s těmito rozdíly:

- <xref:System.Security.Permissions.StrongNameIdentityPermission> platí pro určitého typu, zatímco sestavení typu friend se vztahuje na celé sestavení.

- Pokud existují stovky typy v sestavení *A* , kterou chcete sdílet s sestavení *B*, budete muset přidat <xref:System.Security.Permissions.StrongNameIdentityPermission> pro všechny z nich. Pokud používáte spřátelené sestavení, stačí jednou deklarace typu friend vztah.

- Pokud používáte <xref:System.Security.Permissions.StrongNameIdentityPermission>, typy, které chcete sdílet musí být deklarován jako veřejná. Pokud používáte spřátelené sestavení, sdílené typy jsou deklarovány jako `internal` (v C# nebo `Friend` v jazyce Visual Basic).

Informace o tom, jak získat přístup k sestavení `internal` (v C# nebo `Friend` v jazyce Visual Basic) typy a metody ze soubor modulu (soubor s příponou .netmodule), najdete v části [/moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) nebo [/moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [Postupy: Vytváření nepodepsaných přátelských sestavení (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [Postupy: Vytváření nepodepsaných přátelských sestavení (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [Postupy: Vytváření podepsaných přátelských sestavení (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [Postupy: Vytváření podepsaných přátelských sestavení (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [Sestavení v .NET](index.md)
- [Průvodce programováním v jazyce C#](../../csharp/programming-guide/index.md)
- [Koncepty programování](../../visual-basic/programming-guide/concepts/index.md)

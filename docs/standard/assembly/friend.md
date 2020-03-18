---
title: Přátelská sestavení
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: a74d4b74ead8492028a092e090f9281231802a87
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348166"
---
# <a name="friend-assemblies"></a>Přátelská sestavení

Sestavení *přítele* je sestavení, které může přistupovat k typům a členům [jiného](../../csharp/language-reference/keywords/internal.md) sestavení interní (C#) nebo [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic). Pokud identifikujete sestavení jako sestavení přítele, již není třeba označovat typy a členy jako veřejné, aby k nim měly přístup jiná sestavení. To je zvláště výhodné v následujících scénářích:

- Během testování částí při spuštění testovacího kódu v samostatném sestavení, ale vyžaduje `internal` přístup k `Friend` členům v testovaném sestavení, které jsou označeny jako v jazyce C# nebo v jazyce Visual Basic.

- Při vývoji knihovny tříd a dodatky do knihovny jsou obsaženy v samostatných sestaveních, `internal` ale vyžadují `Friend` přístup k členům v existujících sestaveních, které jsou označeny jako c# nebo v jazyce Visual Basic.

## <a name="remarks"></a>Poznámky

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Atribut můžete použít k identifikaci jednoho nebo více sestavení přátel pro dané sestavení. Následující příklad používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut v *sestavení A* a určuje sestavení *AssemblyB* jako sestavení friend. To poskytuje *assemblyb* přístup ke všem typům a `internal` členům v `Friend` *sestavení A,* které jsou označeny jako v jazyce C# nebo v jazyce Visual Basic.

> [!NOTE]
> Při kompilaci sestavení, jako je *AssemblyB,* který bude přistupovat k interní typy nebo interní členy jiného sestavení, jako *je sestavení A*, je nutné explicitně zadat název výstupního souboru (*.exe* nebo *.dll*) pomocí možnosti kompilátoru **-out.** To je nutné, protože kompilátor ještě nevygeneroval název sestavení, které vytváří v době, kdy je vazby na externí odkazy. Další informace naleznete [v tématu -out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) nebo [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).

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

Pouze sestavení, která explicitně zadáte `internal` jako přátelé `Friend` přístup (C#) nebo (Visual Basic) typy a členy. Například pokud *AssemblyB* je přítelem *sestavení A* a sestavení *C* odkazy *AssemblyB* `internal` , sestavení *C* nemá přístup k (C#) nebo `Friend` (Visual Basic) typy v sestavení *A*.

Kompilátor provádí některé základní ověření názvu sestavení <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> friend předané atributu. Pokud *sestavení A* deklaruje *AssemblyB* jako sestavení přítele, ověřovací pravidla jsou následující:

- Pokud *sestavení A* je silný pojmenovaný, *AssemblyB* musí být také silný pojmenovaný. Název sestavení friend, který je předán atributu, se musí skládat z názvu sestavení a veřejného klíče klíče silného názvu, který se používá k podpisu *AssemblyB*.

     Název sestavení friend, který <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> je předán atributu, nemůže být silným názvem *AssemblyB*. Nezahrnejte verzi sestavení, jazykovou verzi, architekturu nebo token veřejného klíče.

- Pokud *sestavení A* není silný pojmenovaný, název sestavení přítele by se měl skládat pouze z názvu sestavení. Další informace naleznete v [tématu Postup: Vytvoření nepodepsaných sestavení přátel](create-unsigned-friend.md).

- Pokud je silnou s názvem *AssemblyB,* musíte zadat klíč silného názvu pro `/keyfile` *AssemblyB* pomocí nastavení projektu nebo možnosti kompilátoru příkazového řádku. Další informace naleznete v [tématu Postup: Vytvoření podepsaných sestavení přátel](create-signed-friend.md).

 Třída <xref:System.Security.Permissions.StrongNameIdentityPermission> také poskytuje možnost sdílet typy, s následujícími rozdíly:

- <xref:System.Security.Permissions.StrongNameIdentityPermission>platí pro individuální typ, zatímco sestava přítele se vztahuje na celou sestavu.

- Pokud existují stovky typů v *sestavení A,* které chcete sdílet s <xref:System.Security.Permissions.StrongNameIdentityPermission> *AssemblyB*, budete muset přidat ke všem z nich. Pokud používáte sestavení přítele, stačí deklarovat vztah přítele jednou.

- Pokud používáte <xref:System.Security.Permissions.StrongNameIdentityPermission>, typy, které chcete sdílet, musí být deklarovány jako veřejné. Pokud používáte sestavení přítele, sdílené typy `internal` jsou deklarovány jako (C#) nebo `Friend` (Visual Basic).

Informace o tom, jak získat `internal` přístup k `Friend` typům a metodám sestavení (C#) nebo (Visual Basic) ze souboru modulu (soubor s příponou *.netmodule),* naleznete v [tématu -moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) nebo [-moduleassemblyname (Visual Basic).](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)

## <a name="see-also"></a>Viz také

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [Postup: Vytvoření nepodepsaných sestavení přátel](create-unsigned-friend.md)
- [Postup: Vytvoření podepsaných sestavení přátel](create-signed-friend.md)
- [Sestavení v .NET](index.md)
- [Průvodce programováním v C#](../../csharp/programming-guide/index.md)
- [Koncepty programování (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)

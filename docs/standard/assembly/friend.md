---
title: Přátelská sestavení
description: Sestavení typu Friend je sestavení .NET, které má přístup k interním typům (C#) nebo typu Friend (Visual Basic) jiného sestavení a členům.
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: 105621da2bd418c6294fa2bbec474809599cb6a5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378937"
---
# <a name="friend-assemblies"></a><span data-ttu-id="84f1a-103">Přátelská sestavení</span><span class="sxs-lookup"><span data-stu-id="84f1a-103">Friend assemblies</span></span>

<span data-ttu-id="84f1a-104">*Sestavení typu Friend* je sestavení, které má přístup k [interním](../../csharp/language-reference/keywords/internal.md) typům (C#) nebo [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) jiných sestavení.</span><span class="sxs-lookup"><span data-stu-id="84f1a-104">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (C#) or [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) types and members.</span></span> <span data-ttu-id="84f1a-105">Pokud identifikujete sestavení jako sestavení typu Friend, již není nutné označit typy a členy jako veřejné, aby byly přístupné z jiných sestavení.</span><span class="sxs-lookup"><span data-stu-id="84f1a-105">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="84f1a-106">To je zvlášť užitečné v následujících scénářích:</span><span class="sxs-lookup"><span data-stu-id="84f1a-106">This is especially convenient in the following scenarios:</span></span>

- <span data-ttu-id="84f1a-107">Při testování částí, při spuštění testovacího kódu v samostatném sestavení, ale vyžaduje přístup ke členům v testovaném sestavení, které jsou označeny jako `internal` v jazyce C# nebo `Friend` v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="84f1a-107">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

- <span data-ttu-id="84f1a-108">Při vývoji knihovny tříd a přidání do knihovny jsou obsaženy v samostatných sestaveních, ale vyžadují přístup ke členům v existujících sestaveních, která jsou označena jako `internal` v jazyce C# nebo `Friend` v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="84f1a-108">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

## <a name="remarks"></a><span data-ttu-id="84f1a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84f1a-109">Remarks</span></span>

<span data-ttu-id="84f1a-110">Atribut můžete použít <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> k identifikaci jednoho nebo více sestavení typu Friend pro dané sestavení.</span><span class="sxs-lookup"><span data-stu-id="84f1a-110">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="84f1a-111">Následující příklad používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut v *sestavení a* a určuje sestavení *AssemblyB* jako sestavení typu Friend.</span><span class="sxs-lookup"><span data-stu-id="84f1a-111">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in *Assembly A* and specifies assembly *AssemblyB* as a friend assembly.</span></span> <span data-ttu-id="84f1a-112">To dává sestavení *AssemblyB* přístup ke všem typům a členům v *sestavení a* , které jsou označeny jako `internal` v jazyce C# nebo `Friend` v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="84f1a-112">This gives assembly *AssemblyB* access to all types and members in *Assembly A* that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

> [!NOTE]
> <span data-ttu-id="84f1a-113">Při kompilaci sestavení, jako je *AssemblyB* , který bude přistupovat k interním typům nebo interním členům jiného sestavení, jako je *sestavení A*, je nutné explicitně zadat název výstupního souboru (*. exe* nebo *. dll*) pomocí možnosti kompilátoru **-out** .</span><span class="sxs-lookup"><span data-stu-id="84f1a-113">When you compile an assembly like *AssemblyB* that will access internal types or internal members of another assembly like *Assembly A*, you must explicitly specify the name of the output file (*.exe* or *.dll*) by using the **-out** compiler option.</span></span> <span data-ttu-id="84f1a-114">To je nutné, protože kompilátor ještě negeneroval název sestavení, který sestaví, v době, kdy je svázán s externími odkazy.</span><span class="sxs-lookup"><span data-stu-id="84f1a-114">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="84f1a-115">Další informace naleznete v tématu [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) nebo [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="84f1a-115">For more information, see [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>

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

<span data-ttu-id="84f1a-116">Pouze sestavení, která explicitně zadáte jako přátelé, mohou přistupovat k `internal` `Friend` typům a členům (C#) nebo (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="84f1a-116">Only assemblies that you explicitly specify as friends can access `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span> <span data-ttu-id="84f1a-117">Například pokud je *AssemblyB* přítele *sestavení* a a *sestavení C* odkazuje *AssemblyB*, *sestavení c* nemá přístup k `internal` typům (C#) nebo `Friend` (Visual Basic) v *sestavení a*.</span><span class="sxs-lookup"><span data-stu-id="84f1a-117">For example, if *AssemblyB* is a friend of *Assembly A* and *Assembly C* references *AssemblyB*, *Assembly C* does not have access to `internal` (C#) or `Friend` (Visual Basic) types in *Assembly A*.</span></span>

<span data-ttu-id="84f1a-118">Kompilátor provede základní ověření názvu sestavení typu Friend předaného <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributu.</span><span class="sxs-lookup"><span data-stu-id="84f1a-118">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="84f1a-119">Pokud *sestavení A* deklaruje *AssemblyB* jako sestavení typu Friend, ověřovací pravidla jsou následující:</span><span class="sxs-lookup"><span data-stu-id="84f1a-119">If *Assembly A* declares *AssemblyB* as a friend assembly, the validation rules are as follows:</span></span>

- <span data-ttu-id="84f1a-120">Pokud je *sestavení A* silně pojmenované, *AssemblyB* musí také mít silný název.</span><span class="sxs-lookup"><span data-stu-id="84f1a-120">If *Assembly A* is strong named, *AssemblyB* must also be strong named.</span></span> <span data-ttu-id="84f1a-121">Název sestavení typu Friend, který je předán atributu, musí obsahovat název sestavení a veřejný klíč klíče silného názvu, který se používá k podepsání *AssemblyB*.</span><span class="sxs-lookup"><span data-stu-id="84f1a-121">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign *AssemblyB*.</span></span>

     <span data-ttu-id="84f1a-122">Název sestavení typu Friend, který je předán <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributu, nemůže být silným názvem *AssemblyB*.</span><span class="sxs-lookup"><span data-stu-id="84f1a-122">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of *AssemblyB*.</span></span> <span data-ttu-id="84f1a-123">Nezahrnujte verze sestavení, jazykovou verzi, architekturu nebo token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="84f1a-123">Don't include the assembly version, culture, architecture, or public key token.</span></span>

- <span data-ttu-id="84f1a-124">Pokud *sestavení A* není silného názvu, název sestavení typu Friend by měl obsahovat pouze název sestavení.</span><span class="sxs-lookup"><span data-stu-id="84f1a-124">If *Assembly A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="84f1a-125">Další informace naleznete v tématu [Postupy: vytváření nepodepsaných přátelských sestavení](create-unsigned-friend.md).</span><span class="sxs-lookup"><span data-stu-id="84f1a-125">For more information, see [How to: Create unsigned friend assemblies](create-unsigned-friend.md).</span></span>

- <span data-ttu-id="84f1a-126">Pokud je *AssemblyB* silným názvem, je nutné zadat klíč silného názvu pro *AssemblyB* pomocí nastavení projektu nebo možnosti kompilátoru příkazového řádku `/keyfile` .</span><span class="sxs-lookup"><span data-stu-id="84f1a-126">If *AssemblyB* is strong named, you must specify the strong-name key for *AssemblyB* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="84f1a-127">Další informace naleznete v tématu [Postupy: vytvoření podepsaných sestavení typu Friend](create-signed-friend.md).</span><span class="sxs-lookup"><span data-stu-id="84f1a-127">For more information, see [How to: Create signed friend assemblies](create-signed-friend.md).</span></span>

 <span data-ttu-id="84f1a-128"><xref:System.Security.Permissions.StrongNameIdentityPermission>Třída také poskytuje možnost sdílet typy s následujícími rozdíly:</span><span class="sxs-lookup"><span data-stu-id="84f1a-128">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>

- <span data-ttu-id="84f1a-129"><xref:System.Security.Permissions.StrongNameIdentityPermission>platí pro individuální typ, zatímco sestavení typu Friend se vztahuje na celé sestavení.</span><span class="sxs-lookup"><span data-stu-id="84f1a-129"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>

- <span data-ttu-id="84f1a-130">Pokud existují stovky typů v *sestavení A* , které chcete sdílet s *AssemblyB*, musíte je přidat <xref:System.Security.Permissions.StrongNameIdentityPermission> do všech.</span><span class="sxs-lookup"><span data-stu-id="84f1a-130">If there are hundreds of types in *Assembly A* that you want to share with *AssemblyB*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="84f1a-131">Použijete-li sestavení typu Friend, stačí pouze deklarovat relaci typu Friend.</span><span class="sxs-lookup"><span data-stu-id="84f1a-131">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>

- <span data-ttu-id="84f1a-132">Pokud používáte <xref:System.Security.Permissions.StrongNameIdentityPermission> , musí být typy, které chcete sdílet, deklarovány jako veřejné.</span><span class="sxs-lookup"><span data-stu-id="84f1a-132">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="84f1a-133">Pokud používáte sestavení typu Friend, sdílené typy jsou deklarovány jako `internal` (C#) nebo `Friend` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="84f1a-133">If you use a friend assembly, the shared types are declared as `internal` (C#) or `Friend` (Visual Basic).</span></span>

<span data-ttu-id="84f1a-134">Informace o tom, jak získat přístup k `internal` typům a metodám sestavení (C#) nebo `Friend` (Visual Basic) ze souboru modulu (soubor s příponou *. netmodule* ), naleznete v tématu [-moduleassemblyname – (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) nebo [-moduleassemblyname – (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span><span class="sxs-lookup"><span data-stu-id="84f1a-134">For information about how to access an assembly's `internal` (C#) or `Friend` (Visual Basic) types and methods from a module file (a file with the *.netmodule* extension), see [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="84f1a-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="84f1a-135">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="84f1a-136">Postupy: vytváření nepodepsaných přátelských sestavení</span><span class="sxs-lookup"><span data-stu-id="84f1a-136">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="84f1a-137">Postupy: Vytváření podepsaných přátelských sestavení</span><span class="sxs-lookup"><span data-stu-id="84f1a-137">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="84f1a-138">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="84f1a-138">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="84f1a-139">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="84f1a-139">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="84f1a-140">Koncepty programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84f1a-140">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)

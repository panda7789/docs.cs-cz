---
title: Přátelská sestavení
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: a74d4b74ead8492028a092e090f9281231802a87
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348166"
---
# <a name="friend-assemblies"></a><span data-ttu-id="adb39-102">Přátelská sestavení</span><span class="sxs-lookup"><span data-stu-id="adb39-102">Friend assemblies</span></span>

<span data-ttu-id="adb39-103">*Sestavení typu Friend* je sestavení, které má přístup k [interním](../../csharp/language-reference/keywords/internal.md) typůmC#() nebo [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) jiného sestavení a k těmto členům.</span><span class="sxs-lookup"><span data-stu-id="adb39-103">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (C#) or [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) types and members.</span></span> <span data-ttu-id="adb39-104">Pokud identifikujete sestavení jako sestavení typu Friend, již není nutné označit typy a členy jako veřejné, aby byly přístupné z jiných sestavení.</span><span class="sxs-lookup"><span data-stu-id="adb39-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="adb39-105">To je zvlášť užitečné v následujících scénářích:</span><span class="sxs-lookup"><span data-stu-id="adb39-105">This is especially convenient in the following scenarios:</span></span>

- <span data-ttu-id="adb39-106">Při testování částí, při spuštění testovacího kódu v samostatném sestavení, ale vyžaduje přístup ke členům v testovaném sestavení, které jsou označeny jako C# `internal` v nebo `Friend` v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="adb39-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

- <span data-ttu-id="adb39-107">Při vývoji knihovny tříd a přidání do knihovny jsou obsaženy v samostatných sestaveních, ale vyžadují přístup ke členům v existujících sestaveních, která jsou označena jako `internal` C# v nebo `Friend` v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="adb39-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

## <a name="remarks"></a><span data-ttu-id="adb39-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="adb39-108">Remarks</span></span>

<span data-ttu-id="adb39-109">Můžete použít atribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> k identifikaci jednoho nebo více sestavení typu Friend pro dané sestavení.</span><span class="sxs-lookup"><span data-stu-id="adb39-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="adb39-110">Následující příklad používá atribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> v *sestavení a* a určuje sestavení *AssemblyB* jako sestavení typu Friend.</span><span class="sxs-lookup"><span data-stu-id="adb39-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in *Assembly A* and specifies assembly *AssemblyB* as a friend assembly.</span></span> <span data-ttu-id="adb39-111">To dává sestavení *AssemblyB* přístup ke všem typům a členům v *sestavení a* , které jsou označeny jako C# `internal` v nebo `Friend` v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="adb39-111">This gives assembly *AssemblyB* access to all types and members in *Assembly A* that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

> [!NOTE]
> <span data-ttu-id="adb39-112">Při kompilaci sestavení, jako je *AssemblyB* , který bude přistupovat k interním typům nebo interním členům jiného sestavení, jako je *sestavení A*, je nutné explicitně zadat název výstupního souboru ( *. exe* nebo *. dll*) pomocí možnosti kompilátoru **-out** .</span><span class="sxs-lookup"><span data-stu-id="adb39-112">When you compile an assembly like *AssemblyB* that will access internal types or internal members of another assembly like *Assembly A*, you must explicitly specify the name of the output file (*.exe* or *.dll*) by using the **-out** compiler option.</span></span> <span data-ttu-id="adb39-113">To je nutné, protože kompilátor ještě negeneroval název sestavení, který sestaví, v době, kdy je svázán s externími odkazy.</span><span class="sxs-lookup"><span data-stu-id="adb39-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="adb39-114">Další informace naleznete v tématu [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) nebo [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="adb39-114">For more information, see [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>

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

<span data-ttu-id="adb39-115">Pouze sestavení, která explicitně zadáte jako přátelé, mají přístupC#k typům a členům `internal` () nebo `Friend` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="adb39-115">Only assemblies that you explicitly specify as friends can access `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span> <span data-ttu-id="adb39-116">Například pokud je *AssemblyB* přítele *sestavení* a a *sestavení c* odkazuje na *AssemblyB*, *sestavení c* nemá přístup k typům `internal` (C#) nebo `Friend` (Visual Basic) v *sestavení a*.</span><span class="sxs-lookup"><span data-stu-id="adb39-116">For example, if *AssemblyB* is a friend of *Assembly A* and *Assembly C* references *AssemblyB*, *Assembly C* does not have access to `internal` (C#) or `Friend` (Visual Basic) types in *Assembly A*.</span></span>

<span data-ttu-id="adb39-117">Kompilátor provádí základní ověření názvu sestavení typu Friend předaného atributu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="adb39-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="adb39-118">Pokud *sestavení A* deklaruje *AssemblyB* jako sestavení typu Friend, ověřovací pravidla jsou následující:</span><span class="sxs-lookup"><span data-stu-id="adb39-118">If *Assembly A* declares *AssemblyB* as a friend assembly, the validation rules are as follows:</span></span>

- <span data-ttu-id="adb39-119">Pokud je *sestavení A* silně pojmenované, *AssemblyB* musí také mít silný název.</span><span class="sxs-lookup"><span data-stu-id="adb39-119">If *Assembly A* is strong named, *AssemblyB* must also be strong named.</span></span> <span data-ttu-id="adb39-120">Název sestavení typu Friend, který je předán atributu, musí obsahovat název sestavení a veřejný klíč klíče silného názvu, který se používá k podepsání *AssemblyB*.</span><span class="sxs-lookup"><span data-stu-id="adb39-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign *AssemblyB*.</span></span>

     <span data-ttu-id="adb39-121">Název sestavení typu Friend, který je předán atributu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>, nemůže být silným názvem *AssemblyB*.</span><span class="sxs-lookup"><span data-stu-id="adb39-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of *AssemblyB*.</span></span> <span data-ttu-id="adb39-122">Nezahrnujte verze sestavení, jazykovou verzi, architekturu nebo token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="adb39-122">Don't include the assembly version, culture, architecture, or public key token.</span></span>

- <span data-ttu-id="adb39-123">Pokud *sestavení A* není silného názvu, název sestavení typu Friend by měl obsahovat pouze název sestavení.</span><span class="sxs-lookup"><span data-stu-id="adb39-123">If *Assembly A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="adb39-124">Další informace naleznete v tématu [Postupy: vytváření nepodepsaných přátelských sestavení](create-unsigned-friend.md).</span><span class="sxs-lookup"><span data-stu-id="adb39-124">For more information, see [How to: Create unsigned friend assemblies](create-unsigned-friend.md).</span></span>

- <span data-ttu-id="adb39-125">Pokud je *AssemblyB* silným názvem, je nutné zadat klíč silného názvu pro *AssemblyB* pomocí nastavení projektu nebo možnosti kompilátoru příkazového řádku `/keyfile`.</span><span class="sxs-lookup"><span data-stu-id="adb39-125">If *AssemblyB* is strong named, you must specify the strong-name key for *AssemblyB* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="adb39-126">Další informace naleznete v tématu [Postupy: vytvoření podepsaných sestavení typu Friend](create-signed-friend.md).</span><span class="sxs-lookup"><span data-stu-id="adb39-126">For more information, see [How to: Create signed friend assemblies](create-signed-friend.md).</span></span>

 <span data-ttu-id="adb39-127">Třída <xref:System.Security.Permissions.StrongNameIdentityPermission> také poskytuje možnost sdílet typy s následujícími rozdíly:</span><span class="sxs-lookup"><span data-stu-id="adb39-127">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>

- <span data-ttu-id="adb39-128"><xref:System.Security.Permissions.StrongNameIdentityPermission> platí pro individuální typ, zatímco sestavení typu Friend se vztahuje na celé sestavení.</span><span class="sxs-lookup"><span data-stu-id="adb39-128"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>

- <span data-ttu-id="adb39-129">Pokud existují stovky typů v *sestavení A* , které chcete sdílet s *AssemblyB*, je nutné přidat <xref:System.Security.Permissions.StrongNameIdentityPermission> do všech těchto.</span><span class="sxs-lookup"><span data-stu-id="adb39-129">If there are hundreds of types in *Assembly A* that you want to share with *AssemblyB*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="adb39-130">Použijete-li sestavení typu Friend, stačí pouze deklarovat relaci typu Friend.</span><span class="sxs-lookup"><span data-stu-id="adb39-130">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>

- <span data-ttu-id="adb39-131">Použijete-li <xref:System.Security.Permissions.StrongNameIdentityPermission>, musí být typy, které chcete sdílet, deklarovány jako veřejné.</span><span class="sxs-lookup"><span data-stu-id="adb39-131">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="adb39-132">Použijete-li sestavení typu Friend, sdílené typy jsou deklarovány jako `internal`C#() nebo `Friend` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="adb39-132">If you use a friend assembly, the shared types are declared as `internal` (C#) or `Friend` (Visual Basic).</span></span>

<span data-ttu-id="adb39-133">Informace o tom, jak získat přístup k typům aC#metodám sestavení `internal` () nebo `Friend` (Visual Basic), ze souboru modulu (soubor s příponou *. netmodule* ), naleznete v tématu [-C#moduleassemblyname – ()](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) nebo [-moduleassemblyname – (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span><span class="sxs-lookup"><span data-stu-id="adb39-133">For information about how to access an assembly's `internal` (C#) or `Friend` (Visual Basic) types and methods from a module file (a file with the *.netmodule* extension), see [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="adb39-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="adb39-134">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="adb39-135">Postupy: vytváření nepodepsaných přátelských sestavení</span><span class="sxs-lookup"><span data-stu-id="adb39-135">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="adb39-136">Postupy: Vytváření podepsaných přátelských sestavení</span><span class="sxs-lookup"><span data-stu-id="adb39-136">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="adb39-137">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="adb39-137">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="adb39-138">C#Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="adb39-138">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="adb39-139">Koncepty programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="adb39-139">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)

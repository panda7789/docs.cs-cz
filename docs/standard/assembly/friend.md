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
# <a name="friend-assemblies"></a><span data-ttu-id="81c09-102">Přátelská sestavení</span><span class="sxs-lookup"><span data-stu-id="81c09-102">Friend assemblies</span></span>

<span data-ttu-id="81c09-103">Sestavení *přítele* je sestavení, které může přistupovat k typům a členům [jiného](../../csharp/language-reference/keywords/internal.md) sestavení interní (C#) nebo [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="81c09-103">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (C#) or [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) types and members.</span></span> <span data-ttu-id="81c09-104">Pokud identifikujete sestavení jako sestavení přítele, již není třeba označovat typy a členy jako veřejné, aby k nim měly přístup jiná sestavení.</span><span class="sxs-lookup"><span data-stu-id="81c09-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="81c09-105">To je zvláště výhodné v následujících scénářích:</span><span class="sxs-lookup"><span data-stu-id="81c09-105">This is especially convenient in the following scenarios:</span></span>

- <span data-ttu-id="81c09-106">Během testování částí při spuštění testovacího kódu v samostatném sestavení, ale vyžaduje `internal` přístup k `Friend` členům v testovaném sestavení, které jsou označeny jako v jazyce C# nebo v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="81c09-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

- <span data-ttu-id="81c09-107">Při vývoji knihovny tříd a dodatky do knihovny jsou obsaženy v samostatných sestaveních, `internal` ale vyžadují `Friend` přístup k členům v existujících sestaveních, které jsou označeny jako c# nebo v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="81c09-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

## <a name="remarks"></a><span data-ttu-id="81c09-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81c09-108">Remarks</span></span>

<span data-ttu-id="81c09-109"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Atribut můžete použít k identifikaci jednoho nebo více sestavení přátel pro dané sestavení.</span><span class="sxs-lookup"><span data-stu-id="81c09-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="81c09-110">Následující příklad používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut v *sestavení A* a určuje sestavení *AssemblyB* jako sestavení friend.</span><span class="sxs-lookup"><span data-stu-id="81c09-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in *Assembly A* and specifies assembly *AssemblyB* as a friend assembly.</span></span> <span data-ttu-id="81c09-111">To poskytuje *assemblyb* přístup ke všem typům a `internal` členům v `Friend` *sestavení A,* které jsou označeny jako v jazyce C# nebo v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="81c09-111">This gives assembly *AssemblyB* access to all types and members in *Assembly A* that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

> [!NOTE]
> <span data-ttu-id="81c09-112">Při kompilaci sestavení, jako je *AssemblyB,* který bude přistupovat k interní typy nebo interní členy jiného sestavení, jako *je sestavení A*, je nutné explicitně zadat název výstupního souboru (*.exe* nebo *.dll*) pomocí možnosti kompilátoru **-out.**</span><span class="sxs-lookup"><span data-stu-id="81c09-112">When you compile an assembly like *AssemblyB* that will access internal types or internal members of another assembly like *Assembly A*, you must explicitly specify the name of the output file (*.exe* or *.dll*) by using the **-out** compiler option.</span></span> <span data-ttu-id="81c09-113">To je nutné, protože kompilátor ještě nevygeneroval název sestavení, které vytváří v době, kdy je vazby na externí odkazy.</span><span class="sxs-lookup"><span data-stu-id="81c09-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="81c09-114">Další informace naleznete [v tématu -out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) nebo [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="81c09-114">For more information, see [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>

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

<span data-ttu-id="81c09-115">Pouze sestavení, která explicitně zadáte `internal` jako přátelé `Friend` přístup (C#) nebo (Visual Basic) typy a členy.</span><span class="sxs-lookup"><span data-stu-id="81c09-115">Only assemblies that you explicitly specify as friends can access `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span> <span data-ttu-id="81c09-116">Například pokud *AssemblyB* je přítelem *sestavení A* a sestavení *C* odkazy *AssemblyB* `internal` , sestavení *C* nemá přístup k (C#) nebo `Friend` (Visual Basic) typy v sestavení *A*.</span><span class="sxs-lookup"><span data-stu-id="81c09-116">For example, if *AssemblyB* is a friend of *Assembly A* and *Assembly C* references *AssemblyB*, *Assembly C* does not have access to `internal` (C#) or `Friend` (Visual Basic) types in *Assembly A*.</span></span>

<span data-ttu-id="81c09-117">Kompilátor provádí některé základní ověření názvu sestavení <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> friend předané atributu.</span><span class="sxs-lookup"><span data-stu-id="81c09-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="81c09-118">Pokud *sestavení A* deklaruje *AssemblyB* jako sestavení přítele, ověřovací pravidla jsou následující:</span><span class="sxs-lookup"><span data-stu-id="81c09-118">If *Assembly A* declares *AssemblyB* as a friend assembly, the validation rules are as follows:</span></span>

- <span data-ttu-id="81c09-119">Pokud *sestavení A* je silný pojmenovaný, *AssemblyB* musí být také silný pojmenovaný.</span><span class="sxs-lookup"><span data-stu-id="81c09-119">If *Assembly A* is strong named, *AssemblyB* must also be strong named.</span></span> <span data-ttu-id="81c09-120">Název sestavení friend, který je předán atributu, se musí skládat z názvu sestavení a veřejného klíče klíče silného názvu, který se používá k podpisu *AssemblyB*.</span><span class="sxs-lookup"><span data-stu-id="81c09-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign *AssemblyB*.</span></span>

     <span data-ttu-id="81c09-121">Název sestavení friend, který <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> je předán atributu, nemůže být silným názvem *AssemblyB*.</span><span class="sxs-lookup"><span data-stu-id="81c09-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of *AssemblyB*.</span></span> <span data-ttu-id="81c09-122">Nezahrnejte verzi sestavení, jazykovou verzi, architekturu nebo token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="81c09-122">Don't include the assembly version, culture, architecture, or public key token.</span></span>

- <span data-ttu-id="81c09-123">Pokud *sestavení A* není silný pojmenovaný, název sestavení přítele by se měl skládat pouze z názvu sestavení.</span><span class="sxs-lookup"><span data-stu-id="81c09-123">If *Assembly A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="81c09-124">Další informace naleznete v [tématu Postup: Vytvoření nepodepsaných sestavení přátel](create-unsigned-friend.md).</span><span class="sxs-lookup"><span data-stu-id="81c09-124">For more information, see [How to: Create unsigned friend assemblies](create-unsigned-friend.md).</span></span>

- <span data-ttu-id="81c09-125">Pokud je silnou s názvem *AssemblyB,* musíte zadat klíč silného názvu pro `/keyfile` *AssemblyB* pomocí nastavení projektu nebo možnosti kompilátoru příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="81c09-125">If *AssemblyB* is strong named, you must specify the strong-name key for *AssemblyB* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="81c09-126">Další informace naleznete v [tématu Postup: Vytvoření podepsaných sestavení přátel](create-signed-friend.md).</span><span class="sxs-lookup"><span data-stu-id="81c09-126">For more information, see [How to: Create signed friend assemblies](create-signed-friend.md).</span></span>

 <span data-ttu-id="81c09-127">Třída <xref:System.Security.Permissions.StrongNameIdentityPermission> také poskytuje možnost sdílet typy, s následujícími rozdíly:</span><span class="sxs-lookup"><span data-stu-id="81c09-127">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>

- <span data-ttu-id="81c09-128"><xref:System.Security.Permissions.StrongNameIdentityPermission>platí pro individuální typ, zatímco sestava přítele se vztahuje na celou sestavu.</span><span class="sxs-lookup"><span data-stu-id="81c09-128"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>

- <span data-ttu-id="81c09-129">Pokud existují stovky typů v *sestavení A,* které chcete sdílet s <xref:System.Security.Permissions.StrongNameIdentityPermission> *AssemblyB*, budete muset přidat ke všem z nich.</span><span class="sxs-lookup"><span data-stu-id="81c09-129">If there are hundreds of types in *Assembly A* that you want to share with *AssemblyB*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="81c09-130">Pokud používáte sestavení přítele, stačí deklarovat vztah přítele jednou.</span><span class="sxs-lookup"><span data-stu-id="81c09-130">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>

- <span data-ttu-id="81c09-131">Pokud používáte <xref:System.Security.Permissions.StrongNameIdentityPermission>, typy, které chcete sdílet, musí být deklarovány jako veřejné.</span><span class="sxs-lookup"><span data-stu-id="81c09-131">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="81c09-132">Pokud používáte sestavení přítele, sdílené typy `internal` jsou deklarovány jako (C#) nebo `Friend` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="81c09-132">If you use a friend assembly, the shared types are declared as `internal` (C#) or `Friend` (Visual Basic).</span></span>

<span data-ttu-id="81c09-133">Informace o tom, jak získat `internal` přístup k `Friend` typům a metodám sestavení (C#) nebo (Visual Basic) ze souboru modulu (soubor s příponou *.netmodule),* naleznete v [tématu -moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) nebo [-moduleassemblyname (Visual Basic).](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)</span><span class="sxs-lookup"><span data-stu-id="81c09-133">For information about how to access an assembly's `internal` (C#) or `Friend` (Visual Basic) types and methods from a module file (a file with the *.netmodule* extension), see [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="81c09-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="81c09-134">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="81c09-135">Postup: Vytvoření nepodepsaných sestavení přátel</span><span class="sxs-lookup"><span data-stu-id="81c09-135">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="81c09-136">Postup: Vytvoření podepsaných sestavení přátel</span><span class="sxs-lookup"><span data-stu-id="81c09-136">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="81c09-137">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="81c09-137">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="81c09-138">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="81c09-138">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="81c09-139">Koncepty programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81c09-139">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)

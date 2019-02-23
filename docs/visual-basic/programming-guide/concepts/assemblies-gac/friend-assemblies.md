---
title: Přátelská sestavení (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b3d5716-e6e4-47a7-a3e9-084d7fba5c28
ms.openlocfilehash: 9b91f894f9b10c85eb322b4421fd0473335df7a3
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748151"
---
# <a name="friend-assemblies-visual-basic"></a><span data-ttu-id="78454-102">Přátelská sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78454-102">Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="78454-103">A *sestavení typu friend* je sestavení, které můžou přistupovat k jiné sestavení [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) typy a členy.</span><span class="sxs-lookup"><span data-stu-id="78454-103">A *friend assembly* is an assembly that can access another assembly's [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) types and members.</span></span> <span data-ttu-id="78454-104">Pokud identifikujete sestavení jako sestavení typu friend, máte již označit typy a členy jako veřejné je přístupná pomocí jiné sestavení.</span><span class="sxs-lookup"><span data-stu-id="78454-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="78454-105">To je zvlášť vhodné v následujících scénářích:</span><span class="sxs-lookup"><span data-stu-id="78454-105">This is especially convenient in the following scenarios:</span></span>  
  
-   <span data-ttu-id="78454-106">Během testování částí, pokud testovací kód je spuštěn samostatné sestavení ale vyžaduje přístupu ke členům v sestavení, testování, které jsou označeny jako `Friend`.</span><span class="sxs-lookup"><span data-stu-id="78454-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `Friend`.</span></span>  
  
-   <span data-ttu-id="78454-107">Když vyvíjíte knihovny tříd a dodatky ke knihovně jsou obsaženy v samostatné sestavení, ale vyžadují přístup ke členům v existující sestavení, které jsou označeny jako `Friend`.</span><span class="sxs-lookup"><span data-stu-id="78454-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `Friend`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78454-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="78454-108">Remarks</span></span>  
 <span data-ttu-id="78454-109">Můžete použít <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut k identifikaci přátelských sestavení pro dané sestavení.</span><span class="sxs-lookup"><span data-stu-id="78454-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="78454-110">V následujícím příkladu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut v sestavení A a určuje sestavení `AssemblyB` jako sestavení typu friend.</span><span class="sxs-lookup"><span data-stu-id="78454-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in assembly A and specifies assembly `AssemblyB` as a friend assembly.</span></span> <span data-ttu-id="78454-111">To umožňuje sestavení `AssemblyB` přístup ke všem typy a členy v sestavení, které jsou označeny jako `Friend`.</span><span class="sxs-lookup"><span data-stu-id="78454-111">This gives assembly `AssemblyB` access to all types and members in assembly A that are marked as `Friend`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78454-112">Pokud kompilujete sestavení (sestavení `AssemblyB`), které budou přistupovat k interní typy nebo interní členy jiné sestavení (sestavení *A*), musíte explicitně zadat název výstupního souboru (.exe nebo .dll) s použitím **/out** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="78454-112">When you compile an assembly (assembly `AssemblyB`) that will access internal types or internal members of another assembly (assembly *A*), you must explicitly specify the name of the output file (.exe or .dll) by using the **/out** compiler option.</span></span> <span data-ttu-id="78454-113">To je požadované, protože kompilátor nebyl zatím nevygenerovaly název sestavení, ve kterém je sestavení v době, kdy je vytvoření vazby na externí odkazy.</span><span class="sxs-lookup"><span data-stu-id="78454-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="78454-114">Další informace najdete v tématu [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="78454-114">For more information, see [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
  
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
  
 <span data-ttu-id="78454-115">Pouze sestavení, která explicitně zadáte jako přátelé dostanete `Friend` typy a členy.</span><span class="sxs-lookup"><span data-stu-id="78454-115">Only assemblies that you explicitly specify as friends can access `Friend` types and members.</span></span> <span data-ttu-id="78454-116">Například, pokud sestavení B je přátelská sestavení A a sestavení C odkazy na sestavení B, C nemá přístup k `Friend` typy v A.</span><span class="sxs-lookup"><span data-stu-id="78454-116">For example, if assembly B is a friend of assembly A and assembly C references assembly B, C does not have access to `Friend` types in A.</span></span>  
  
 <span data-ttu-id="78454-117">Kompilátor provádí nějaké základní ověření předat název sestavení typu friend <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="78454-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="78454-118">Pokud sestavení *A* deklaruje *B* jako sestavení typu friend, ověřovacích pravidel jsou následující:</span><span class="sxs-lookup"><span data-stu-id="78454-118">If assembly *A* declares *B* as a friend assembly, the validation rules are as follows:</span></span>  
  
-   <span data-ttu-id="78454-119">Pokud sestavení *A* je silný název sestavení *B* musí také být silný název.</span><span class="sxs-lookup"><span data-stu-id="78454-119">If assembly *A* is strong named, assembly *B* must also be strong named.</span></span> <span data-ttu-id="78454-120">Název sestavení typu friend, který je předán atributu musí obsahovat název sestavení a veřejný klíč, který se používá k podepsání sestavení silným názvem klíče *B*.</span><span class="sxs-lookup"><span data-stu-id="78454-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign assembly *B*.</span></span>  
  
     <span data-ttu-id="78454-121">Název sestavení typu friend, který je předán <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut nemůže být silný název sestavení *B*: nezahrnují sestavení verze, jazykovou verzi, architektury nebo token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="78454-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of assembly *B*: do not include the assembly version, culture, architecture, or public key token.</span></span>  
  
-   <span data-ttu-id="78454-122">Pokud sestavení *A* není silným názvem, název sestavení typu friend musí obsahovat pouze název sestavení.</span><span class="sxs-lookup"><span data-stu-id="78454-122">If assembly *A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="78454-123">Další informace najdete v tématu [jak: Vytváření nepodepsaných přátelských sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="78454-123">For more information, see [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span></span>  
  
-   <span data-ttu-id="78454-124">Pokud sestavení *B* je silným názvem, je nutné zadat klíče silného názvu pro sestavení *B* pomocí nastavení projektu nebo příkazového řádku `/keyfile` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="78454-124">If assembly *B* is strong named, you must specify the strong-name key for assembly *B* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="78454-125">Další informace najdete v tématu [jak: Vytváření podepsaných přátelských sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="78454-125">For more information, see [How to: Create Signed Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span></span>  
  
 <span data-ttu-id="78454-126"><xref:System.Security.Permissions.StrongNameIdentityPermission> Třída rovněž poskytuje možnost sdílení typů, s těmito rozdíly:</span><span class="sxs-lookup"><span data-stu-id="78454-126">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>  
  
-   <span data-ttu-id="78454-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> platí pro určitého typu, zatímco sestavení typu friend se vztahuje na celé sestavení.</span><span class="sxs-lookup"><span data-stu-id="78454-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>  
  
-   <span data-ttu-id="78454-128">Pokud existují stovky typy v sestavení *A* , kterou chcete sdílet s sestavení *B*, budete muset přidat <xref:System.Security.Permissions.StrongNameIdentityPermission> pro všechny z nich.</span><span class="sxs-lookup"><span data-stu-id="78454-128">If there are hundreds of types in assembly *A* that you want to share with assembly *B*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="78454-129">Pokud používáte spřátelené sestavení, stačí jednou deklarace typu friend vztah.</span><span class="sxs-lookup"><span data-stu-id="78454-129">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>  
  
-   <span data-ttu-id="78454-130">Pokud používáte <xref:System.Security.Permissions.StrongNameIdentityPermission>, typy, které chcete sdílet musí být deklarován jako veřejná.</span><span class="sxs-lookup"><span data-stu-id="78454-130">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="78454-131">Pokud používáte spřátelené sestavení, sdílené typy jsou deklarovány jako `Friend`.</span><span class="sxs-lookup"><span data-stu-id="78454-131">If you use a friend assembly, the shared types are declared as `Friend`.</span></span>  
  
 <span data-ttu-id="78454-132">Informace o tom, jak získat přístup k sestavení `Friend` typy a metody ze soubor modulu (soubor s příponou .netmodule), najdete v části [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span><span class="sxs-lookup"><span data-stu-id="78454-132">For information about how to access an assembly's `Friend` types and methods from a module file (a file with the .netmodule extension), see [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78454-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78454-133">See also</span></span>
- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="78454-134">Postupy: Vytváření nepodepsaných přátelských sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78454-134">How to: Create Unsigned Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [<span data-ttu-id="78454-135">Postupy: Vytváření podepsaných přátelských sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78454-135">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [<span data-ttu-id="78454-136">Sestavení v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="78454-136">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
- [<span data-ttu-id="78454-137">Koncepty programování</span><span class="sxs-lookup"><span data-stu-id="78454-137">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)

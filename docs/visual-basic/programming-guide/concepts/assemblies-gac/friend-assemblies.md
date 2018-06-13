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
# <a name="friend-assemblies-visual-basic"></a><span data-ttu-id="f23ce-102">Přátelská sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f23ce-102">Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="f23ce-103">A *přátelského sestavení* je sestavení, které můžete přístup k jiné sestavení [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) typy a členy.</span><span class="sxs-lookup"><span data-stu-id="f23ce-103">A *friend assembly* is an assembly that can access another assembly's [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) types and members.</span></span> <span data-ttu-id="f23ce-104">Pokud identifikovat sestavení jako přátelského sestavení, již není k označení typy a členy jako veřejné, aby k nim přístup ostatních sestavení.</span><span class="sxs-lookup"><span data-stu-id="f23ce-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="f23ce-105">To je zvlášť vhodné v následujících scénářích:</span><span class="sxs-lookup"><span data-stu-id="f23ce-105">This is especially convenient in the following scenarios:</span></span>  
  
-   <span data-ttu-id="f23ce-106">Během testování částí, při spuštění testovacího kódu v samostatné sestavení, ale vyžaduje přístupu ke členům v sestavení testuje, které jsou označeny jako `Friend`.</span><span class="sxs-lookup"><span data-stu-id="f23ce-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `Friend`.</span></span>  
  
-   <span data-ttu-id="f23ce-107">Pokud vyvíjíte knihovny tříd a přidané do knihovny jsou obsaženy v samostatné sestavení, ale vyžadují přístup ke členům v existujících sestavení, které jsou označeny jako `Friend`.</span><span class="sxs-lookup"><span data-stu-id="f23ce-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `Friend`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f23ce-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f23ce-108">Remarks</span></span>  
 <span data-ttu-id="f23ce-109">Můžete použít <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut k identifikaci jeden nebo více sestavení, přítele pro zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="f23ce-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="f23ce-110">Následující příklad používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> v sestavení A a určuje sestavení `AssemblyB` jako přátelského sestavení.</span><span class="sxs-lookup"><span data-stu-id="f23ce-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in assembly A and specifies assembly `AssemblyB` as a friend assembly.</span></span> <span data-ttu-id="f23ce-111">Díky tomu sestavení `AssemblyB` přístup ke všem typy a členy v sestavení, které jsou označeny jako `Friend`.</span><span class="sxs-lookup"><span data-stu-id="f23ce-111">This gives assembly `AssemblyB` access to all types and members in assembly A that are marked as `Friend`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f23ce-112">Při kompilaci sestavení (sestavení `AssemblyB`), bude přístup k interní typy nebo interní členy jiné sestavení (sestavení *A*), musíte explicitně zadat název výstupního souboru (.exe nebo .dll) pomocí **/out** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f23ce-112">When you compile an assembly (assembly `AssemblyB`) that will access internal types or internal members of another assembly (assembly *A*), you must explicitly specify the name of the output file (.exe or .dll) by using the **/out** compiler option.</span></span> <span data-ttu-id="f23ce-113">To je potřeba, protože kompilátor ještě nebyl vygenerován název sestavení, ve kterém je sestavení v době, kdy je vytvoření vazby na externí odkazy.</span><span class="sxs-lookup"><span data-stu-id="f23ce-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="f23ce-114">Další informace najdete v tématu [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="f23ce-114">For more information, see [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
  
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
  
 <span data-ttu-id="f23ce-115">Pouze sestavení, která explicitně zadáte jako přístup přátel `Friend` typy a členy.</span><span class="sxs-lookup"><span data-stu-id="f23ce-115">Only assemblies that you explicitly specify as friends can access `Friend` types and members.</span></span> <span data-ttu-id="f23ce-116">Například pokud je sestavení B přátelských sestavení A a sestavení C odkazy na sestavení B, C nemá přístup k `Friend` typy v A.</span><span class="sxs-lookup"><span data-stu-id="f23ce-116">For example, if assembly B is a friend of assembly A and assembly C references assembly B, C does not have access to `Friend` types in A.</span></span>  
  
 <span data-ttu-id="f23ce-117">Kompilátor provádí základní ověření předaný název sestavení friend <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="f23ce-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="f23ce-118">Pokud sestavení *A* deklaruje *B* jako přátelského sestavení ověřovacích pravidel jsou následující:</span><span class="sxs-lookup"><span data-stu-id="f23ce-118">If assembly *A* declares *B* as a friend assembly, the validation rules are as follows:</span></span>  
  
-   <span data-ttu-id="f23ce-119">Pokud sestavení *A* se silným názvem, sestavení *B* musí také mít silné název.</span><span class="sxs-lookup"><span data-stu-id="f23ce-119">If assembly *A* is strong named, assembly *B* must also be strong named.</span></span> <span data-ttu-id="f23ce-120">Název sestavení friend, který je předán do atribut musí obsahovat název sestavení a veřejného klíče pro silné jméno – klíč, který se používá k podepsání sestavení *B*.</span><span class="sxs-lookup"><span data-stu-id="f23ce-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign assembly *B*.</span></span>  
  
     <span data-ttu-id="f23ce-121">Název sestavení friend, který je předán <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut nemůže být silného názvu sestavení *B*: nezahrnují verze sestavení, jazykovou verzi, architektury nebo tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="f23ce-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of assembly *B*: do not include the assembly version, culture, architecture, or public key token.</span></span>  
  
-   <span data-ttu-id="f23ce-122">Pokud sestavení *A* není silné s názvem, přítele název sestavení by měla obsahovat jenom název sestavení.</span><span class="sxs-lookup"><span data-stu-id="f23ce-122">If assembly *A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="f23ce-123">Další informace najdete v tématu [postupy: vytváření nepodepsaných přátelských sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="f23ce-123">For more information, see [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span></span>  
  
-   <span data-ttu-id="f23ce-124">Pokud sestavení *B* je silné s názvem, je nutné zadat silné jméno – klíč pro sestavení *B* pomocí nastavení projektu nebo příkazového řádku `/keyfile` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f23ce-124">If assembly *B* is strong named, you must specify the strong-name key for assembly *B* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="f23ce-125">Další informace najdete v tématu [postupy: vytvoření podepsané přátelská sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="f23ce-125">For more information, see [How to: Create Signed Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span></span>  
  
 <span data-ttu-id="f23ce-126"><xref:System.Security.Permissions.StrongNameIdentityPermission> Třída rovněž poskytuje možnost sdílet typy, s následující rozdíly:</span><span class="sxs-lookup"><span data-stu-id="f23ce-126">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>  
  
-   <span data-ttu-id="f23ce-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> platí pro typ jednotlivých během přátelského sestavení celá sestava.</span><span class="sxs-lookup"><span data-stu-id="f23ce-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>  
  
-   <span data-ttu-id="f23ce-128">Pokud se používají stovky typy v sestavení *A* , kterou chcete sdílet s sestavení *B*, budete muset přidat <xref:System.Security.Permissions.StrongNameIdentityPermission> ke všem z nich.</span><span class="sxs-lookup"><span data-stu-id="f23ce-128">If there are hundreds of types in assembly *A* that you want to share with assembly *B*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="f23ce-129">Pokud používáte přátelského sestavení, musíte pouze deklarovat vztah friend jednou.</span><span class="sxs-lookup"><span data-stu-id="f23ce-129">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>  
  
-   <span data-ttu-id="f23ce-130">Pokud používáte <xref:System.Security.Permissions.StrongNameIdentityPermission>, typy, které chcete sdílet muset být deklarována jako veřejné.</span><span class="sxs-lookup"><span data-stu-id="f23ce-130">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="f23ce-131">Pokud používáte přátelského sestavení, sdílené typy jsou deklarovány jako `Friend`.</span><span class="sxs-lookup"><span data-stu-id="f23ce-131">If you use a friend assembly, the shared types are declared as `Friend`.</span></span>  
  
 <span data-ttu-id="f23ce-132">Informace o tom, jak přistupovat sestavení `Friend` typy a metody ze souboru modulu (soubor s příponou .netmodule), najdete v části [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span><span class="sxs-lookup"><span data-stu-id="f23ce-132">For information about how to access an assembly's `Friend` types and methods from a module file (a file with the .netmodule extension), see [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f23ce-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="f23ce-133">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 <xref:System.Security.Permissions.StrongNameIdentityPermission>  
 [<span data-ttu-id="f23ce-134">Postupy: vytváření nepodepsaných přátelských sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f23ce-134">How to: Create Unsigned Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [<span data-ttu-id="f23ce-135">Postupy: vytváření podepsaných přátelských sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f23ce-135">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [<span data-ttu-id="f23ce-136">Sestavení a globální mezipaměti sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f23ce-136">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="f23ce-137">Koncepty programování</span><span class="sxs-lookup"><span data-stu-id="f23ce-137">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)

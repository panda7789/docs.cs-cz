---
title: "Přátelská sestavení (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 20b8d4f2d58af510a28160d28e6ef740d293d835
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="friend-assemblies-c"></a><span data-ttu-id="47717-102">Přátelská sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="47717-102">Friend Assemblies (C#)</span></span>
<span data-ttu-id="47717-103">A *přátelského sestavení* je sestavení, které můžete přístup k jiné sestavení [interní](../../../../csharp/language-reference/keywords/internal.md) typy a členy.</span><span class="sxs-lookup"><span data-stu-id="47717-103">A *friend assembly* is an assembly that can access another assembly's [internal](../../../../csharp/language-reference/keywords/internal.md) types and members.</span></span> <span data-ttu-id="47717-104">Pokud identifikovat sestavení jako přátelského sestavení, již není k označení typy a členy jako veřejné, aby k nim přístup ostatních sestavení.</span><span class="sxs-lookup"><span data-stu-id="47717-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="47717-105">To je zvlášť vhodné v následujících scénářích:</span><span class="sxs-lookup"><span data-stu-id="47717-105">This is especially convenient in the following scenarios:</span></span>  
  
-   <span data-ttu-id="47717-106">Během testování částí, při spuštění testovacího kódu v samostatné sestavení, ale vyžaduje přístupu ke členům v sestavení testuje, které jsou označeny jako `internal` .</span><span class="sxs-lookup"><span data-stu-id="47717-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` .</span></span>  
  
-   <span data-ttu-id="47717-107">Pokud vyvíjíte knihovny tříd a přidané do knihovny jsou obsaženy v samostatné sestavení, ale vyžadují přístup ke členům v existujících sestavení, které jsou označeny jako `internal` .</span><span class="sxs-lookup"><span data-stu-id="47717-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` .</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47717-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47717-108">Remarks</span></span>  
 <span data-ttu-id="47717-109">Můžete použít <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut k identifikaci jeden nebo více sestavení, přítele pro zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="47717-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="47717-110">Následující příklad používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> v sestavení A a určuje sestavení `AssemblyB` jako přátelského sestavení.</span><span class="sxs-lookup"><span data-stu-id="47717-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in assembly A and specifies assembly `AssemblyB` as a friend assembly.</span></span> <span data-ttu-id="47717-111">Díky tomu sestavení `AssemblyB` přístup ke všem typy a členy v sestavení, které jsou označeny jako `internal`.</span><span class="sxs-lookup"><span data-stu-id="47717-111">This gives assembly `AssemblyB` access to all types and members in assembly A that are marked as `internal`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47717-112">Při kompilaci sestavení (sestavení `AssemblyB`), bude přístup k interní typy nebo interní členy jiné sestavení (sestavení *A*), musíte explicitně zadat název výstupního souboru (.exe nebo .dll) pomocí **/out** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="47717-112">When you compile an assembly (assembly `AssemblyB`) that will access internal types or internal members of another assembly (assembly *A*), you must explicitly specify the name of the output file (.exe or .dll) by using the **/out** compiler option.</span></span> <span data-ttu-id="47717-113">To je potřeba, protože kompilátor ještě nebyl vygenerován název sestavení, ve kterém je sestavení v době, kdy je vytvoření vazby na externí odkazy.</span><span class="sxs-lookup"><span data-stu-id="47717-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="47717-114">Další informace najdete v tématu [/out (C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="47717-114">For more information, see [/out (C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) .</span></span>  
  
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
  
 <span data-ttu-id="47717-115">Pouze sestavení, která explicitně zadáte jako přístup přátel `internal` typy a členy.</span><span class="sxs-lookup"><span data-stu-id="47717-115">Only assemblies that you explicitly specify as friends can access `internal` types and members.</span></span> <span data-ttu-id="47717-116">Například pokud je sestavení B přátelských sestavení A a sestavení C odkazy na sestavení B, C nemá přístup k `internal` typy v A.</span><span class="sxs-lookup"><span data-stu-id="47717-116">For example, if assembly B is a friend of assembly A and assembly C references assembly B, C does not have access to `internal` types in A.</span></span>  
  
 <span data-ttu-id="47717-117">Kompilátor provádí základní ověření předaný název sestavení friend <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="47717-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="47717-118">Pokud sestavení *A* deklaruje *B* jako přátelského sestavení ověřovacích pravidel jsou následující:</span><span class="sxs-lookup"><span data-stu-id="47717-118">If assembly *A* declares *B* as a friend assembly, the validation rules are as follows:</span></span>  
  
-   <span data-ttu-id="47717-119">Pokud sestavení *A* se silným názvem, sestavení *B* musí také mít silné název.</span><span class="sxs-lookup"><span data-stu-id="47717-119">If assembly *A* is strong named, assembly *B* must also be strong named.</span></span> <span data-ttu-id="47717-120">Název sestavení friend, který je předán do atribut musí obsahovat název sestavení a veřejného klíče pro silné jméno – klíč, který se používá k podepsání sestavení *B*.</span><span class="sxs-lookup"><span data-stu-id="47717-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign assembly *B*.</span></span>  
  
     <span data-ttu-id="47717-121">Název sestavení friend, který je předán <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut nemůže být silného názvu sestavení *B*: nezahrnují verze sestavení, jazykovou verzi, architektury nebo tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="47717-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of assembly *B*: do not include the assembly version, culture, architecture, or public key token.</span></span>  
  
-   <span data-ttu-id="47717-122">Pokud sestavení *A* není silné s názvem, přítele název sestavení by měla obsahovat jenom název sestavení.</span><span class="sxs-lookup"><span data-stu-id="47717-122">If assembly *A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="47717-123">Další informace najdete v tématu [postupy: vytváření nepodepsaných přátelských sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="47717-123">For more information, see [How to: Create Unsigned Friend Assemblies (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span></span>  
  
-   <span data-ttu-id="47717-124">Pokud sestavení *B* je silné s názvem, je nutné zadat silné jméno – klíč pro sestavení *B* pomocí nastavení projektu nebo příkazového řádku `/keyfile` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="47717-124">If assembly *B* is strong named, you must specify the strong-name key for assembly *B* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="47717-125">Další informace najdete v tématu [postupy: vytvoření podepsané přátelských sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="47717-125">For more information, see [How to: Create Signed Friend Assemblies (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span></span>  
  
 <span data-ttu-id="47717-126"><xref:System.Security.Permissions.StrongNameIdentityPermission> Třída rovněž poskytuje možnost sdílet typy, s následující rozdíly:</span><span class="sxs-lookup"><span data-stu-id="47717-126">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>  
  
-   <span data-ttu-id="47717-127"><xref:System.Security.Permissions.StrongNameIdentityPermission>platí pro typ jednotlivých během přátelského sestavení celá sestava.</span><span class="sxs-lookup"><span data-stu-id="47717-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>  
  
-   <span data-ttu-id="47717-128">Pokud se používají stovky typy v sestavení *A* , kterou chcete sdílet s sestavení *B*, budete muset přidat <xref:System.Security.Permissions.StrongNameIdentityPermission> ke všem z nich.</span><span class="sxs-lookup"><span data-stu-id="47717-128">If there are hundreds of types in assembly *A* that you want to share with assembly *B*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="47717-129">Pokud používáte přátelského sestavení, musíte pouze deklarovat vztah friend jednou.</span><span class="sxs-lookup"><span data-stu-id="47717-129">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>  
  
-   <span data-ttu-id="47717-130">Pokud používáte <xref:System.Security.Permissions.StrongNameIdentityPermission>, typy, které chcete sdílet muset být deklarována jako veřejné.</span><span class="sxs-lookup"><span data-stu-id="47717-130">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="47717-131">Pokud používáte přátelského sestavení, sdílené typy jsou deklarovány jako `internal`.</span><span class="sxs-lookup"><span data-stu-id="47717-131">If you use a friend assembly, the shared types are declared as `internal`.</span></span>  
  
 <span data-ttu-id="47717-132">Informace o tom, jak přistupovat sestavení `internal` typy a metody ze souboru modulu (soubor s příponou .netmodule), najdete v části [/moduleassemblyname (C#)](../../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="47717-132">For information about how to access an assembly's `internal` types and methods from a module file (a file with the .netmodule extension), see [/moduleassemblyname (C#)](../../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47717-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="47717-133">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 <xref:System.Security.Permissions.StrongNameIdentityPermission>  
 [<span data-ttu-id="47717-134">Postupy: vytváření nepodepsaných přátelských sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="47717-134">How to: Create Unsigned Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [<span data-ttu-id="47717-135">Postupy: vytváření podepsaných přátelských sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="47717-135">How to: Create Signed Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [<span data-ttu-id="47717-136">Sestavení a globální mezipaměti sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="47717-136">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="47717-137">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="47717-137">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)

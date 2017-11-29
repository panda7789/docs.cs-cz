---
title: "Postupy: vytváření nepodepsaných přátelských sestavení (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a2b2667c60a07a2897a0934d210901042e2e43c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a><span data-ttu-id="c6945-102">Postupy: vytváření nepodepsaných přátelských sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6945-102">How to: Create Unsigned Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="c6945-103">Tento příklad ukazuje způsob použití přátelských sestavení s sestavení, které jsou bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="c6945-103">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="c6945-104">Chcete-li vytvořit sestavení a přátelských sestavení</span><span class="sxs-lookup"><span data-stu-id="c6945-104">To create an assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="c6945-105">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="c6945-105">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="c6945-106">Vytvořte soubor jazyka Visual Basic s názvem `friend_signed_A.` obsahující následující kód.</span><span class="sxs-lookup"><span data-stu-id="c6945-106">Create a Visual Basic file named `friend_signed_A.` that contains the following code.</span></span> <span data-ttu-id="c6945-107">Kód používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut deklarovat friend_signed_B jako přátelského sestavení.</span><span class="sxs-lookup"><span data-stu-id="c6945-107">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
    ```vb  
    ' friend_unsigned_A.vb  
    ' Compile with:   
    ' Vbc /target:library friend_unsigned_A.vb  
    Imports System.Runtime.CompilerServices  
    Imports System  
  
    <Assembly: InternalsVisibleTo("friend_unsigned_B")>   
  
    ' Friend type.  
    Friend Class Class1  
        Public Sub Test()  
            Console.WriteLine("Class1.Test")  
        End Sub  
    End Class  
  
    ' Public type with Friend member.  
    Public Class Class2  
        Friend Sub Test()  
            Console.WriteLine("Class2.Test")  
        End Sub  
    End Class  
    ```  
  
3.  <span data-ttu-id="c6945-108">Kompilace a friend_signed_A se přihlaste pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="c6945-108">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```vb  
    Vbc /target:library friend_unsigned_A.vb  
    ```  
  
4.  <span data-ttu-id="c6945-109">Vytvořte soubor jazyka Visual Basic s názvem `friend_unsigned_B` obsahující následující kód.</span><span class="sxs-lookup"><span data-stu-id="c6945-109">Create a Visual Basic file named `friend_unsigned_B` that contains the following code.</span></span> <span data-ttu-id="c6945-110">Protože friend_unsigned_A určuje friend_unsigned_B jako přátelského sestavení, můžete přístup k kód v friend_unsigned_B `Friend` typy a členy z friend_unsigned_A.</span><span class="sxs-lookup"><span data-stu-id="c6945-110">Because friend_unsigned_A specifies friend_unsigned_B as a friend assembly, the code in friend_unsigned_B can access `Friend` types and members from friend_unsigned_A.</span></span>  
  
    ```vb  
    ' friend_unsigned_B.vb  
    ' Compile with:   
    ' Vbc /r:friend_unsigned_A.dll friend_unsigned_B.vb  
    Module Module1  
        Sub Main()  
            ' Access a Friend type.  
            Dim inst1 As New Class1()  
            inst1.Test()  
  
            Dim inst2 As New Class2()  
            ' Access a Friend member of a public type.  
            inst2.Test()  
  
            System.Console.ReadLine()  
        End Sub  
    End Module  
    ```  
  
5.  <span data-ttu-id="c6945-111">Zkompilujte friend_signed_B pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="c6945-111">Compile friend_signed_B by using the following command.</span></span>  
  
    ```vb  
    Vbc /r:friend_unsigned_A.dll friend_unsigned_B.vb  
    ```  
  
     <span data-ttu-id="c6945-112">Název sestavení, který je generovaný kompilátoru shodovat friend název sestavení, který je předán <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="c6945-112">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="c6945-113">Sestavení je možné nastavit explicitně pomocí `/out` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="c6945-113">You can explicitly set the assembly by using the `/out` compiler option.</span></span>  
  
6.  <span data-ttu-id="c6945-114">Spusťte soubor friend_signed_B.exe.</span><span class="sxs-lookup"><span data-stu-id="c6945-114">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="c6945-115">Program vytiskne dva řetězce: "Class1.Test" a "Class2.Test".</span><span class="sxs-lookup"><span data-stu-id="c6945-115">The program prints two strings: "Class1.Test" and "Class2.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c6945-116">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c6945-116">.NET Framework Security</span></span>  
 <span data-ttu-id="c6945-117">Existují podobnosti mezi <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut a <xref:System.Security.Permissions.StrongNameIdentityPermission> třídy.</span><span class="sxs-lookup"><span data-stu-id="c6945-117">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="c6945-118">Hlavní rozdíl je, že <xref:System.Security.Permissions.StrongNameIdentityPermission> oprávnění zabezpečení ke spuštění konkrétní části kódu, můžete požadovat, zatímco <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut určuje, zda se `Friend` typy a členy.</span><span class="sxs-lookup"><span data-stu-id="c6945-118">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `Friend` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6945-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6945-119">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="c6945-120">Sestavení a globální mezipaměti sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6945-120">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="c6945-121">Přátelská sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6945-121">Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [<span data-ttu-id="c6945-122">Postupy: vytváření podepsaných přátelských sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6945-122">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [<span data-ttu-id="c6945-123">Programování konceptů Průvodce</span><span class="sxs-lookup"><span data-stu-id="c6945-123">Programming Guide Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)

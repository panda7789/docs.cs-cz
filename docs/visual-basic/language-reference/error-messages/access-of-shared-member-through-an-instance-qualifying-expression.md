---
title: Přístup sdíleného člena prostřednictvím instance; kvalifikující výraz nebyl vyhodnocen.
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 8e6ddab16c59d7ce95d96b377e3f372f6ebe5278
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843562"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a><span data-ttu-id="bd864-102">Přístup sdíleného člena prostřednictvím instance; kvalifikující výraz nebyl vyhodnocen.</span><span class="sxs-lookup"><span data-stu-id="bd864-102">Access of shared member through an instance; qualifying expression will not be evaluated</span></span>
<span data-ttu-id="bd864-103">Proměnná instance třídy nebo struktury se používá k přístupu `Shared` proměnná, vlastnost, procedura nebo události definované v této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="bd864-103">An instance variable of a class or structure is used to access a `Shared` variable, property, procedure, or event defined in that class or structure.</span></span> <span data-ttu-id="bd864-104">Toto upozornění může také dojít, pokud proměnnou instance se používá pro přístup k implicitně sdílenému členu třídy nebo struktury, jako je konstantní nebo výčtu, nebo vnořené třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="bd864-104">This warning can also occur if an instance variable is used to access an implicitly shared member of a class or structure, such as a constant or enumeration, or a nested class or structure.</span></span>  
  
 <span data-ttu-id="bd864-105">Účelem sdílení člen je vytvořit pouze jednu kopii tohoto člena a zadáte jednu kopii k dispozici pro každou instanci třídy nebo struktury, ve kterém je deklarována.</span><span class="sxs-lookup"><span data-stu-id="bd864-105">The purpose of sharing a member is to create only a single copy of that member and make that single copy available to every instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="bd864-106">Je konzistentní s pro přístup k tomuto účelu `Shared` člen prostřednictvím názvu třídy nebo struktury, a nikoli prostřednictvím proměnné, který obsahuje jednotlivé instance této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="bd864-106">It is consistent with this purpose to access a `Shared` member through the name of its class or structure, rather than through a variable that holds an individual instance of that class or structure.</span></span>  
  
 <span data-ttu-id="bd864-107">Přístup k `Shared` člena prostřednictvím instance proměnné může ztížit váš kód pochopit zakódováním skutečnost, že je člen `Shared`.</span><span class="sxs-lookup"><span data-stu-id="bd864-107">Accessing a `Shared` member through an instance variable can make your code more difficult to understand by obscuring the fact that the member is `Shared`.</span></span> <span data-ttu-id="bd864-108">Kromě toho pokud takový přístup je součástí výrazu, který provede další akce, například `Function` proceduru, která vrací instanci sdíleného členu, Visual Basic obchází výraz a všechny akce, které by jinak provedl.</span><span class="sxs-lookup"><span data-stu-id="bd864-108">Furthermore, if such access is part of an expression that performs other actions, such as a `Function` procedure that returns an instance of the shared member, Visual Basic bypasses the expression and any other actions it would otherwise perform.</span></span>  
  
 <span data-ttu-id="bd864-109">Další informace a příklad najdete v tématu [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="bd864-109">For more information and an example, see [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
 <span data-ttu-id="bd864-110">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="bd864-110">By default, this message is a warning.</span></span> <span data-ttu-id="bd864-111">Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="bd864-111">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="bd864-112">**ID chyby:** BC42025</span><span class="sxs-lookup"><span data-stu-id="bd864-112">**Error ID:** BC42025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bd864-113">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="bd864-113">To correct this error</span></span>  
  
-   <span data-ttu-id="bd864-114">Použijte název třídy nebo struktury, která definuje `Shared` člen k přístupu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="bd864-114">Use the name of the class or structure that defines the `Shared` member to access it, as shown in the following example.</span></span>  
  
```vb  
Public Class testClass  
    Public Shared Sub sayHello()  
        MsgBox("Hello")  
    End Sub  
End Class  
  
Module testModule  
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New testClass  
        tc.sayHello()  
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        testClass.sayHello()  
    End Sub  
End Module  
```  
  
> [!NOTE]
>  <span data-ttu-id="bd864-115">Být výstraha pro efekty oboru, pokud dva programovací elementy mají stejný název.</span><span class="sxs-lookup"><span data-stu-id="bd864-115">Be alert for the effects of scope when two programming elements have the same name.</span></span> <span data-ttu-id="bd864-116">V předchozím příkladu, je-li deklarována instance pomocí `Dim testClass as testClass = Nothing`, kompilátor zpracovává volání `testClass.sayHello()` jako dochází přístupu metody pomocí názvu třídy a žádné upozornění.</span><span class="sxs-lookup"><span data-stu-id="bd864-116">In the previous example, if you declare an instance by using `Dim testClass as testClass = Nothing`, the compiler treats a call to `testClass.sayHello()` as an access of the method through the class name, and no warning occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd864-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd864-117">See also</span></span>

- [<span data-ttu-id="bd864-118">Shared</span><span class="sxs-lookup"><span data-stu-id="bd864-118">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="bd864-119">Obor v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bd864-119">Scope in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)

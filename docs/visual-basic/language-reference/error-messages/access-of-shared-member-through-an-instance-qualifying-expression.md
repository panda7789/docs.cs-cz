---
title: Přístup sdíleného člena prostřednictvím instance; kvalifikující výraz nebyl vyhodnocen.
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 035882b60c90d9a6141ad0d34b4c40682e0c32a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588980"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a><span data-ttu-id="2e25c-102">Přístup sdíleného člena prostřednictvím instance; kvalifikující výraz nebyl vyhodnocen.</span><span class="sxs-lookup"><span data-stu-id="2e25c-102">Access of shared member through an instance; qualifying expression will not be evaluated</span></span>
<span data-ttu-id="2e25c-103">Proměnnou instance třídy nebo struktura slouží k přístupu `Shared` proměnnou, vlastnost, postup nebo událostí, které jsou definované v tomto třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="2e25c-103">An instance variable of a class or structure is used to access a `Shared` variable, property, procedure, or event defined in that class or structure.</span></span> <span data-ttu-id="2e25c-104">Toto upozornění se může také nastat, pokud proměnnou instance se používá pro přístup implicitně sdíleného člena třídy nebo struktuře, například konstanta nebo výčtu nebo vnořenou třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="2e25c-104">This warning can also occur if an instance variable is used to access an implicitly shared member of a class or structure, such as a constant or enumeration, or a nested class or structure.</span></span>  
  
 <span data-ttu-id="2e25c-105">Účelem sdílení členem je vytvořit pouze jednu kopii tohoto člena a ujistěte se, že jedna kopie k dispozici pro všechny instance řetězce třídu nebo strukturu, ve kterém je deklarovaná.</span><span class="sxs-lookup"><span data-stu-id="2e25c-105">The purpose of sharing a member is to create only a single copy of that member and make that single copy available to every instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="2e25c-106">Je v souladu s pro přístup k tomuto účelu `Shared` člen prostřednictvím název jeho třídu nebo strukturu, a nikoli prostřednictvím proměnné, která obsahuje jednotlivé instance třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="2e25c-106">It is consistent with this purpose to access a `Shared` member through the name of its class or structure, rather than through a variable that holds an individual instance of that class or structure.</span></span>  
  
 <span data-ttu-id="2e25c-107">Přístup k `Shared` člena prostřednictvím instance proměnné můžete byl váš kód více těžko srozumitelné zakódováním skutečnost, že je člen `Shared`.</span><span class="sxs-lookup"><span data-stu-id="2e25c-107">Accessing a `Shared` member through an instance variable can make your code more difficult to understand by obscuring the fact that the member is `Shared`.</span></span> <span data-ttu-id="2e25c-108">Kromě toho pokud tento přístup je součástí výrazu, která přistupuje jiné akce, například `Function` procedury, která vrátí instanci sdíleného člena, Visual Basic obchází ve výrazu a všechny akce, které by jinak provedl.</span><span class="sxs-lookup"><span data-stu-id="2e25c-108">Furthermore, if such access is part of an expression that performs other actions, such as a `Function` procedure that returns an instance of the shared member, Visual Basic bypasses the expression and any other actions it would otherwise perform.</span></span>  
  
 <span data-ttu-id="2e25c-109">Další informace a příklady naleznete v tématu [sdílené](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="2e25c-109">For more information and an example, see [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
 <span data-ttu-id="2e25c-110">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="2e25c-110">By default, this message is a warning.</span></span> <span data-ttu-id="2e25c-111">Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2e25c-111">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="2e25c-112">**ID chyby:** BC42025</span><span class="sxs-lookup"><span data-stu-id="2e25c-112">**Error ID:** BC42025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2e25c-113">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2e25c-113">To correct this error</span></span>  
  
-   <span data-ttu-id="2e25c-114">Použijte název třídy nebo struktura, která definuje `Shared` člen k přístupu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2e25c-114">Use the name of the class or structure that defines the `Shared` member to access it, as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="2e25c-115">Být výstraha pro důsledky oboru, pokud dva programovací elementy mají stejný název.</span><span class="sxs-lookup"><span data-stu-id="2e25c-115">Be alert for the effects of scope when two programming elements have the same name.</span></span> <span data-ttu-id="2e25c-116">V předchozím příkladu, pokud deklarace instance pomocí `Dim testClass as testClass = Nothing`, kompilátor zpracovává volání `testClass.sayHello()` jako dochází přístupu metody pomocí názvu třídy a bez upozornění.</span><span class="sxs-lookup"><span data-stu-id="2e25c-116">In the previous example, if you declare an instance by using `Dim testClass as testClass = Nothing`, the compiler treats a call to `testClass.sayHello()` as an access of the method through the class name, and no warning occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e25c-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e25c-117">See Also</span></span>  
 [<span data-ttu-id="2e25c-118">Shared</span><span class="sxs-lookup"><span data-stu-id="2e25c-118">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="2e25c-119">Rozsah v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e25c-119">Scope in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)

---
title: Přístup sdíleného člena prostřednictvím instance; kvalifikující výraz nebyl vyhodnocen.
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 3174d463744303e8c90ed0b2e1a4d86ed08fbcfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947702"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a><span data-ttu-id="b0eb1-102">Přístup sdíleného člena prostřednictvím instance; kvalifikující výraz nebyl vyhodnocen.</span><span class="sxs-lookup"><span data-stu-id="b0eb1-102">Access of shared member through an instance; qualifying expression will not be evaluated</span></span>
<span data-ttu-id="b0eb1-103">Instance proměnné třídy nebo struktury se používá pro přístup `Shared` k proměnné, vlastnosti, proceduře nebo události, které jsou definovány v této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="b0eb1-103">An instance variable of a class or structure is used to access a `Shared` variable, property, procedure, or event defined in that class or structure.</span></span> <span data-ttu-id="b0eb1-104">Toto upozornění může nastat také v případě, že proměnná instance slouží k přístupu k implicitnímu sdílenému členu třídy nebo struktury, jako je například konstanta nebo výčet nebo vnořená třída nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="b0eb1-104">This warning can also occur if an instance variable is used to access an implicitly shared member of a class or structure, such as a constant or enumeration, or a nested class or structure.</span></span>  
  
 <span data-ttu-id="b0eb1-105">Účelem sdílení člena je vytvořit pouze jednu kopii daného člena a učinit jednu kopii k dispozici pro každou instanci třídy nebo struktury, ve které je deklarována.</span><span class="sxs-lookup"><span data-stu-id="b0eb1-105">The purpose of sharing a member is to create only a single copy of that member and make that single copy available to every instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="b0eb1-106">Je v souladu s tímto účelem pro přístup `Shared` ke členu prostřednictvím názvu jeho třídy nebo struktury, nikoli prostřednictvím proměnné, která obsahuje jednotlivou instanci dané třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="b0eb1-106">It is consistent with this purpose to access a `Shared` member through the name of its class or structure, rather than through a variable that holds an individual instance of that class or structure.</span></span>  
  
 <span data-ttu-id="b0eb1-107">Přístup ke `Shared` členu prostřednictvím proměnné instance může ztížit pochopení kódu tím, že zakrývá skutečnost, že je `Shared`členem.</span><span class="sxs-lookup"><span data-stu-id="b0eb1-107">Accessing a `Shared` member through an instance variable can make your code more difficult to understand by obscuring the fact that the member is `Shared`.</span></span> <span data-ttu-id="b0eb1-108">Kromě toho, pokud je takový přístup součástí výrazu, který provádí jiné akce, jako je `Function` například procedura, která vrací instanci sdíleného člena, Visual Basic obejít výraz a jakékoli další akce, které by jinak prováděly.</span><span class="sxs-lookup"><span data-stu-id="b0eb1-108">Furthermore, if such access is part of an expression that performs other actions, such as a `Function` procedure that returns an instance of the shared member, Visual Basic bypasses the expression and any other actions it would otherwise perform.</span></span>  
  
 <span data-ttu-id="b0eb1-109">Další informace a příklad najdete v tématu [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="b0eb1-109">For more information and an example, see [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
 <span data-ttu-id="b0eb1-110">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="b0eb1-110">By default, this message is a warning.</span></span> <span data-ttu-id="b0eb1-111">Další informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b0eb1-111">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="b0eb1-112">**ID chyby:** BC42025</span><span class="sxs-lookup"><span data-stu-id="b0eb1-112">**Error ID:** BC42025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b0eb1-113">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b0eb1-113">To correct this error</span></span>  
  
- <span data-ttu-id="b0eb1-114">Použijte název třídy nebo struktury, který definuje `Shared` člena k přístupu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b0eb1-114">Use the name of the class or structure that defines the `Shared` member to access it, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="b0eb1-115">Pokud dva programovací prvky mají stejný název, je třeba upozornit na účinky rozsahu.</span><span class="sxs-lookup"><span data-stu-id="b0eb1-115">Be alert for the effects of scope when two programming elements have the same name.</span></span> <span data-ttu-id="b0eb1-116">V předchozím příkladu, pokud deklarujete instanci pomocí `Dim testClass as testClass = Nothing`, kompilátor zpracovává `testClass.sayHello()` volání jako přístup k metodě přes název třídy a nedochází k žádnému upozornění.</span><span class="sxs-lookup"><span data-stu-id="b0eb1-116">In the previous example, if you declare an instance by using `Dim testClass as testClass = Nothing`, the compiler treats a call to `testClass.sayHello()` as an access of the method through the class name, and no warning occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0eb1-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0eb1-117">See also</span></span>

- [<span data-ttu-id="b0eb1-118">Shared</span><span class="sxs-lookup"><span data-stu-id="b0eb1-118">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="b0eb1-119">Obor v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b0eb1-119">Scope in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)

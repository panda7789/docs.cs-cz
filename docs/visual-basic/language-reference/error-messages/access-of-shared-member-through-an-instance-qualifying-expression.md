---
title: Přístup ke sdílenému členu prostřednictvím instance; kvalifikační výraz se nevyhodnotí.
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 773a97c301e7cb5bec0234ae466d487ec9716437
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250350"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a><span data-ttu-id="bb1af-102">Přístup ke sdílenému členu prostřednictvím instance; kvalifikační výraz se nevyhodnotí.</span><span class="sxs-lookup"><span data-stu-id="bb1af-102">Access of shared member through an instance; qualifying expression will not be evaluated</span></span>

<span data-ttu-id="bb1af-103">Instance proměnné třídy nebo struktury se používá pro přístup k proměnné, vlastnosti, proceduře nebo události `Shared` definované v této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="bb1af-103">An instance variable of a class or structure is used to access a `Shared` variable, property, procedure, or event defined in that class or structure.</span></span> <span data-ttu-id="bb1af-104">Toto upozornění může nastat také v případě, že proměnná instance slouží k přístupu k implicitnímu sdílenému členu třídy nebo struktury, jako je například konstanta nebo výčet nebo vnořená třída nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="bb1af-104">This warning can also occur if an instance variable is used to access an implicitly shared member of a class or structure, such as a constant or enumeration, or a nested class or structure.</span></span>

<span data-ttu-id="bb1af-105">Účelem sdílení člena je vytvořit pouze jednu kopii daného člena a učinit jednu kopii k dispozici pro každou instanci třídy nebo struktury, ve které je deklarována.</span><span class="sxs-lookup"><span data-stu-id="bb1af-105">The purpose of sharing a member is to create only a single copy of that member and make that single copy available to every instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="bb1af-106">Je v souladu s tímto účelem pro přístup k členu `Shared` prostřednictvím názvu jeho třídy nebo struktury, nikoli prostřednictvím proměnné, která obsahuje jednotlivou instanci dané třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="bb1af-106">It is consistent with this purpose to access a `Shared` member through the name of its class or structure, rather than through a variable that holds an individual instance of that class or structure.</span></span>

<span data-ttu-id="bb1af-107">Přístup k členu `Shared` prostřednictvím proměnné instance může ztížit pochopení kódu tím, že skryje fakt, že člen je `Shared`.</span><span class="sxs-lookup"><span data-stu-id="bb1af-107">Accessing a `Shared` member through an instance variable can make your code more difficult to understand by obscuring the fact that the member is `Shared`.</span></span> <span data-ttu-id="bb1af-108">Kromě toho, pokud je takový přístup součástí výrazu, který provádí jiné akce, jako je například `Function`, která vrací instanci sdíleného člena, Visual Basic vynechá výraz a všechny další akce, které by jinak prováděly.</span><span class="sxs-lookup"><span data-stu-id="bb1af-108">Furthermore, if such access is part of an expression that performs other actions, such as a `Function` procedure that returns an instance of the shared member, Visual Basic bypasses the expression and any other actions it would otherwise perform.</span></span>  
  
<span data-ttu-id="bb1af-109">Další informace a příklad najdete v tématu [Shared](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="bb1af-109">For more information and an example, see [Shared](../modifiers/shared.md).</span></span>  
  
<span data-ttu-id="bb1af-110">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="bb1af-110">By default, this message is a warning.</span></span> <span data-ttu-id="bb1af-111">Další informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="bb1af-111">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
<span data-ttu-id="bb1af-112">**ID chyby:** BC42025</span><span class="sxs-lookup"><span data-stu-id="bb1af-112">**Error ID:** BC42025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bb1af-113">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="bb1af-113">To correct this error</span></span>  
  
<span data-ttu-id="bb1af-114">Použijte název třídy nebo struktury, která definuje člena `Shared` pro přístup, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="bb1af-114">Use the name of the class or structure that defines the `Shared` member to access it, as shown in the following example:</span></span>
  
```vb
Public Class TestClass
    Public Shared Sub SayHello()
        MsgBox("Hello")
    End Sub
End Class
  
Module Program
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New TestClass()
        tc.SayHello()
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        TestClass.SayHello()
    End Sub  
End Module  
```  
  
> [!NOTE]
> <span data-ttu-id="bb1af-115">Pokud dva programovací prvky mají stejný název, je třeba upozornit na účinky rozsahu.</span><span class="sxs-lookup"><span data-stu-id="bb1af-115">Be alert for the effects of scope when two programming elements have the same name.</span></span> <span data-ttu-id="bb1af-116">Pokud jste v předchozím příkladu deklarovali instanci pomocí `Dim testClass as testClass = Nothing`, kompilátor zpracovává volání `testClass.sayHello()` jako přístup k metodě přes název třídy a žádné upozornění.</span><span class="sxs-lookup"><span data-stu-id="bb1af-116">In the previous example, if you declare an instance by using `Dim testClass as testClass = Nothing`, the compiler treats a call to `testClass.sayHello()` as an access of the method through the class name, and no warning occurs.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bb1af-117">Související témata</span><span class="sxs-lookup"><span data-stu-id="bb1af-117">See also</span></span>

- [<span data-ttu-id="bb1af-118">Sdíleného</span><span class="sxs-lookup"><span data-stu-id="bb1af-118">Shared</span></span>](../modifiers/shared.md)
- [<span data-ttu-id="bb1af-119">Obor v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb1af-119">Scope in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/scope.md)

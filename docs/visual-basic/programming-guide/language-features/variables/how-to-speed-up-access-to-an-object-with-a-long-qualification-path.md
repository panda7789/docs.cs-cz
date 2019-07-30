---
title: 'Postupy: Urychlení přístupu k objektu pomocí cesty s dlouhou kvalifikací (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: a8e50a2ed04037b48091321dc0c9ac2ea1db35f4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631096"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="cc1cf-102">Postupy: Urychlení přístupu k objektu pomocí cesty s dlouhou kvalifikací (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc1cf-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>

<span data-ttu-id="cc1cf-103">Pokud často přistupujete k objektu, který vyžaduje cestu kvalifikace několika metod a vlastností, můžete kód urychlit tak, že neopakujete cestu kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="cc1cf-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>

<span data-ttu-id="cc1cf-104">Existují dva způsoby, jak se vyhnout opakování cesty kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="cc1cf-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="cc1cf-105">Objekt můžete přiřadit proměnné nebo ho můžete použít v `With`... `End With` blok.</span><span class="sxs-lookup"><span data-stu-id="cc1cf-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="cc1cf-106">Urychlení přístupu k silně kvalifikovanému objektu přiřazením k proměnné</span><span class="sxs-lookup"><span data-stu-id="cc1cf-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>

1. <span data-ttu-id="cc1cf-107">Deklarujte proměnnou typu objektu, ke kterému se často přistupuje.</span><span class="sxs-lookup"><span data-stu-id="cc1cf-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="cc1cf-108">Zadejte cestu kvalifikace v části inicializace deklarace.</span><span class="sxs-lookup"><span data-stu-id="cc1cf-108">Specify the qualification path in the initialization part of the declaration.</span></span>

    ```vb
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="cc1cf-109">Pro přístup ke členům objektu použijte proměnnou.</span><span class="sxs-lookup"><span data-stu-id="cc1cf-109">Use the variable to access the object's members.</span></span>

    ```vb
    ctrlActv.Text = "Test"
    ctrlActv.Location = New Point(100, 100)
    ctrlActv.Show()
    ```

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="cc1cf-110">Chcete-li zrychlit přístup k silně kvalifikovanému objektu pomocí s... Ukončit s blokem</span><span class="sxs-lookup"><span data-stu-id="cc1cf-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>

1. <span data-ttu-id="cc1cf-111">Zadejte cestu kvalifikace do `With` příkazu.</span><span class="sxs-lookup"><span data-stu-id="cc1cf-111">Put the qualification path in a `With` statement.</span></span>

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="cc1cf-112">Před příkazem přistoupit k členům objektu `With` uvnitř bloku. `End With`</span><span class="sxs-lookup"><span data-stu-id="cc1cf-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a><span data-ttu-id="cc1cf-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc1cf-113">See also</span></span>

- [<span data-ttu-id="cc1cf-114">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="cc1cf-114">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="cc1cf-115">Příkaz With...End With</span><span class="sxs-lookup"><span data-stu-id="cc1cf-115">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)

---
title: <type1>'<typename>musí implementovat<methodname>'pro rozhraní'<interfacename>.
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: c387b0225375f4675042bef593b23a084305b4fd
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591598"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="f5188-102">\<Type1 >'\<typename >' musí implementovat '\<methodname > 'rozhraní'\<interfacename > '</span><span class="sxs-lookup"><span data-stu-id="f5188-102">\<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="f5188-103">Deklarace třídy nebo struktury pro implementaci rozhraní, ale neimplementuje proceduru definovanou rozhraním.</span><span class="sxs-lookup"><span data-stu-id="f5188-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="f5188-104">Je nutné implementovat všechny členy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f5188-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="f5188-105">**ID chyby:** BC30149</span><span class="sxs-lookup"><span data-stu-id="f5188-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f5188-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f5188-106">To correct this error</span></span>  
  
1. <span data-ttu-id="f5188-107">Deklarujte proceduru se stejným názvem a signaturou, jak je definováno v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f5188-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="f5188-108">Nezapomeňte zahrnout alespoň příkaz `End Function` nebo `End Sub`.</span><span class="sxs-lookup"><span data-stu-id="f5188-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="f5188-109">Přidejte klauzuli `Implements` na konec příkazu `Function` nebo `Sub`.</span><span class="sxs-lookup"><span data-stu-id="f5188-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="f5188-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f5188-110">For example:</span></span>  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f5188-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5188-111">See also</span></span>

- [<span data-ttu-id="f5188-112">Příkaz Implements</span><span class="sxs-lookup"><span data-stu-id="f5188-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="f5188-113">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5188-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

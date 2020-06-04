---
title: <type1>'<typename>' musí implementovat '<methodname>' pro rozhraní '<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 90d2b6d70390bfb732af4a5868c935de61d18f94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408494"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="01ec9-102">\<type1>'\<typename>' musí implementovat '\<methodname>' pro rozhraní '\<interfacename>'</span><span class="sxs-lookup"><span data-stu-id="01ec9-102">\<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="01ec9-103">Deklarace třídy nebo struktury pro implementaci rozhraní, ale neimplementuje proceduru definovanou rozhraním.</span><span class="sxs-lookup"><span data-stu-id="01ec9-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="01ec9-104">Je nutné implementovat všechny členy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="01ec9-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="01ec9-105">**ID chyby:** BC30149</span><span class="sxs-lookup"><span data-stu-id="01ec9-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="01ec9-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="01ec9-106">To correct this error</span></span>  
  
1. <span data-ttu-id="01ec9-107">Deklarujte proceduru se stejným názvem a signaturou, jak je definováno v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="01ec9-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="01ec9-108">Nezapomeňte zahrnout alespoň `End Function` `End Sub` příkaz nebo.</span><span class="sxs-lookup"><span data-stu-id="01ec9-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="01ec9-109">Přidejte `Implements` klauzuli na konec `Function` `Sub` příkazu or.</span><span class="sxs-lookup"><span data-stu-id="01ec9-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="01ec9-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="01ec9-110">For example:</span></span>  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="01ec9-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="01ec9-111">See also</span></span>

- [<span data-ttu-id="01ec9-112">Implements – Příkaz</span><span class="sxs-lookup"><span data-stu-id="01ec9-112">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="01ec9-113">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="01ec9-113">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)

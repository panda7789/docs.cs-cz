---
title: AddressOf – operátor
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 3e7db8e7329ce8d21b6e07863e6f1673a6389608
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372061"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="7e392-102">AddressOf – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e392-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="7e392-103">Vytvoří instanci delegáta, která odkazuje na konkrétní proceduru.</span><span class="sxs-lookup"><span data-stu-id="7e392-103">Creates a delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e392-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e392-104">Syntax</span></span>  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="7e392-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="7e392-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="7e392-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="7e392-106">Required.</span></span> <span data-ttu-id="7e392-107">Určuje proceduru, na kterou má nově vytvořený delegát odkazovat.</span><span class="sxs-lookup"><span data-stu-id="7e392-107">Specifies the procedure to be referenced by the newly created delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e392-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e392-108">Remarks</span></span>  
 <span data-ttu-id="7e392-109">`AddressOf`Operátor vytvoří delegáta, který odkazuje na proceduru nebo funkci určenou parametrem `procedurename` .</span><span class="sxs-lookup"><span data-stu-id="7e392-109">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span></span> <span data-ttu-id="7e392-110">Pokud je zadaná procedura metodou instance, pak delegát odkazuje na instanci i na metodu.</span><span class="sxs-lookup"><span data-stu-id="7e392-110">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span></span> <span data-ttu-id="7e392-111">Poté, když je vyvolán delegát, je volána zadaná metoda zadané instance.</span><span class="sxs-lookup"><span data-stu-id="7e392-111">Then, when the  delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="7e392-112">`AddressOf`Operátor lze použít jako operand konstruktoru delegáta nebo jej lze použít v kontextu, ve kterém lze určit typ delegáta kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="7e392-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e392-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e392-113">Example</span></span>  
 <span data-ttu-id="7e392-114">Tento příklad používá `AddressOf` operátor k určení delegáta pro zpracování `Click` události tlačítka.</span><span class="sxs-lookup"><span data-stu-id="7e392-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="7e392-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e392-115">Example</span></span>  
 <span data-ttu-id="7e392-116">Následující příklad používá `AddressOf` operátor k určení spouštěcí funkce pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="7e392-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="7e392-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e392-117">See also</span></span>

- [<span data-ttu-id="7e392-118">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="7e392-118">Declare Statement</span></span>](../statements/declare-statement.md)
- [<span data-ttu-id="7e392-119">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="7e392-119">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="7e392-120">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="7e392-120">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="7e392-121">Delegáti</span><span class="sxs-lookup"><span data-stu-id="7e392-121">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)

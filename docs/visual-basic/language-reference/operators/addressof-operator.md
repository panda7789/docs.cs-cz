---
title: AddressOf – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 2ebadf5ded1a23fe46b8e16cf18ae265b5d3c255
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591659"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="f0f7a-102">AddressOf – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0f7a-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="f0f7a-103">Vytvoří instanci delegáta, která odkazuje na konkrétní proceduru.</span><span class="sxs-lookup"><span data-stu-id="f0f7a-103">Creates a delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0f7a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0f7a-104">Syntax</span></span>  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="f0f7a-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="f0f7a-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="f0f7a-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f0f7a-106">Required.</span></span> <span data-ttu-id="f0f7a-107">Určuje proceduru, na kterou má nově vytvořený delegát odkazovat.</span><span class="sxs-lookup"><span data-stu-id="f0f7a-107">Specifies the procedure to be referenced by the newly created delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0f7a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f0f7a-108">Remarks</span></span>  
 <span data-ttu-id="f0f7a-109">Operátor `AddressOf` vytvoří delegáta, který odkazuje na sub nebo funkci určenou parametrem `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="f0f7a-109">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span></span> <span data-ttu-id="f0f7a-110">Pokud je zadaná procedura metodou instance, pak delegát odkazuje na instanci i na metodu.</span><span class="sxs-lookup"><span data-stu-id="f0f7a-110">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span></span> <span data-ttu-id="f0f7a-111">Poté, když je vyvolán delegát, je volána zadaná metoda zadané instance.</span><span class="sxs-lookup"><span data-stu-id="f0f7a-111">Then, when the  delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="f0f7a-112">Operátor `AddressOf` lze použít jako operand konstruktoru delegáta nebo jej lze použít v kontextu, ve kterém může být typ delegáta určen kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="f0f7a-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0f7a-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0f7a-113">Example</span></span>  
 <span data-ttu-id="f0f7a-114">V tomto příkladu se používá operátor `AddressOf` k určení delegáta pro zpracování události `Click` tlačítka.</span><span class="sxs-lookup"><span data-stu-id="f0f7a-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="f0f7a-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0f7a-115">Example</span></span>  
 <span data-ttu-id="f0f7a-116">Následující příklad používá operátor `AddressOf` k určení spouštěcí funkce pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="f0f7a-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="f0f7a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0f7a-117">See also</span></span>

- [<span data-ttu-id="f0f7a-118">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="f0f7a-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="f0f7a-119">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="f0f7a-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="f0f7a-120">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="f0f7a-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="f0f7a-121">Delegáti</span><span class="sxs-lookup"><span data-stu-id="f0f7a-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)

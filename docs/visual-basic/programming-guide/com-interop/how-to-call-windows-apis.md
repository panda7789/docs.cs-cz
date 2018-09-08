---
title: 'Postupy: Volání rozhraní API systému Windows (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 081f4242ef5883a8b25b8819ba3aff835b1e6ac7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44208267"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="2140c-102">Postupy: Volání rozhraní API systému Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2140c-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="2140c-103">Tento příklad definuje a volá `MessageBox` funkce v user32.dll a poté předá řetězec k němu.</span><span class="sxs-lookup"><span data-stu-id="2140c-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2140c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="2140c-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2140c-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="2140c-105">Compiling the Code</span></span>  
 <span data-ttu-id="2140c-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="2140c-106">This example requires:</span></span>  
  
-   <span data-ttu-id="2140c-107">Odkaz na <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2140c-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2140c-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="2140c-108">Robust Programming</span></span>  
 <span data-ttu-id="2140c-109">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="2140c-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="2140c-110">Metoda není statická, je abstraktní nebo dříve definované.</span><span class="sxs-lookup"><span data-stu-id="2140c-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="2140c-111">Nadřazený typ je rozhraní nebo délka *název* nebo *názevsouboru* je nula.</span><span class="sxs-lookup"><span data-stu-id="2140c-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="2140c-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="2140c-112">(<xref:System.ArgumentException>)</span></span>  
  
-   <span data-ttu-id="2140c-113">*Název* nebo *názevsouboru* je `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="2140c-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="2140c-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="2140c-114">(<xref:System.ArgumentNullException>)</span></span>  
  
-   <span data-ttu-id="2140c-115">Nadřazený typ byl dříve vytvořen pomocí `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="2140c-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="2140c-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="2140c-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2140c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2140c-117">See also</span></span>

- [<span data-ttu-id="2140c-118">Bližší pohled na vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="2140c-118">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)  
- [<span data-ttu-id="2140c-119">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="2140c-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)  
- [<span data-ttu-id="2140c-120">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="2140c-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)  
- [<span data-ttu-id="2140c-121">Definování metody pomocí reflexe generování</span><span class="sxs-lookup"><span data-stu-id="2140c-121">Defining a Method with Reflection Emit</span></span>](https://msdn.microsoft.com/library/84fd3bf6-628f-41aa-83d9-b990cf926e81)  
- [<span data-ttu-id="2140c-122">Návod: Volání rozhraní API systému Windows</span><span class="sxs-lookup"><span data-stu-id="2140c-122">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
- [<span data-ttu-id="2140c-123">Zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="2140c-123">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)

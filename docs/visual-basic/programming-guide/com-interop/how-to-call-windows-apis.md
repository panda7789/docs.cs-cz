---
title: 'Postupy: Volání rozhraní API systému Windows (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: de568c3273d4d040c6566136e5d59e2155b86f8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643637"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="cb600-102">Postupy: Volání rozhraní API systému Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb600-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="cb600-103">Tento příklad definuje a volá `MessageBox` funkce v user32.dll a pak předá řetězec k němu.</span><span class="sxs-lookup"><span data-stu-id="cb600-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb600-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="cb600-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cb600-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="cb600-105">Compiling the Code</span></span>  
 <span data-ttu-id="cb600-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="cb600-106">This example requires:</span></span>  
  
-   <span data-ttu-id="cb600-107">Odkaz na <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cb600-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="cb600-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="cb600-108">Robust Programming</span></span>  
 <span data-ttu-id="cb600-109">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="cb600-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="cb600-110">Metoda nejsou statické, je abstraktní nebo byla definována dříve.</span><span class="sxs-lookup"><span data-stu-id="cb600-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="cb600-111">Nadřazený typ je rozhraní nebo délka *název* nebo *názevsouboru* je nulová.</span><span class="sxs-lookup"><span data-stu-id="cb600-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="cb600-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="cb600-112">(<xref:System.ArgumentException>)</span></span>  
  
-   <span data-ttu-id="cb600-113">*Název* nebo *názevsouboru* je `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="cb600-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="cb600-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="cb600-114">(<xref:System.ArgumentNullException>)</span></span>  
  
-   <span data-ttu-id="cb600-115">Typ obsahující byla dříve vytvořena pomocí `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="cb600-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="cb600-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="cb600-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb600-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb600-117">See Also</span></span>  
 [<span data-ttu-id="cb600-118">Vyvolání bližší pohled na platformy</span><span class="sxs-lookup"><span data-stu-id="cb600-118">A Closer Look at Platform Invoke</span></span>](http://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
 [<span data-ttu-id="cb600-119">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="cb600-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="cb600-120">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="cb600-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="cb600-121">Emitování definování metoda pomocí reflexe</span><span class="sxs-lookup"><span data-stu-id="cb600-121">Defining a Method with Reflection Emit</span></span>](http://msdn.microsoft.com/library/84fd3bf6-628f-41aa-83d9-b990cf926e81)  
 [<span data-ttu-id="cb600-122">Návod: Volání rozhraní API systému Windows</span><span class="sxs-lookup"><span data-stu-id="cb600-122">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [<span data-ttu-id="cb600-123">Zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="cb600-123">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)

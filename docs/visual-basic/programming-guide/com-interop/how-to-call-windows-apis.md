---
title: 'Postupy: Volání rozhraní API systému Windows'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 9de9f0fbcca291af0b6aadfd8e3fe7033708fbc6
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347531"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="11c3b-102">Postupy: Volání rozhraní API systému Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11c3b-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="11c3b-103">Tento příklad definuje a zavolá funkci `MessageBox` v souboru User32. dll a poté předá do ní řetězec.</span><span class="sxs-lookup"><span data-stu-id="11c3b-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11c3b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="11c3b-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="11c3b-105">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="11c3b-105">Compile the code</span></span>  
 <span data-ttu-id="11c3b-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="11c3b-106">This example requires:</span></span>  
  
- <span data-ttu-id="11c3b-107">Odkaz na obor názvů <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="11c3b-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="11c3b-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="11c3b-108">Robust Programming</span></span>  
 <span data-ttu-id="11c3b-109">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="11c3b-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="11c3b-110">Metoda není statická, je abstraktní nebo dříve definovaná.</span><span class="sxs-lookup"><span data-stu-id="11c3b-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="11c3b-111">Nadřazený typ je rozhraní nebo délka *názvu* nebo *Název_souboru_DLL* je nula.</span><span class="sxs-lookup"><span data-stu-id="11c3b-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="11c3b-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="11c3b-112">(<xref:System.ArgumentException>)</span></span>  
  
- <span data-ttu-id="11c3b-113">*Název* nebo název *Název_souboru_DLL* je `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="11c3b-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="11c3b-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="11c3b-114">(<xref:System.ArgumentNullException>)</span></span>  
  
- <span data-ttu-id="11c3b-115">Nadřazený typ byl dříve vytvořen pomocí `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="11c3b-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="11c3b-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="11c3b-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11c3b-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11c3b-117">See also</span></span>

- [<span data-ttu-id="11c3b-118">Bližší pohled na vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="11c3b-118">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="11c3b-119">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="11c3b-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="11c3b-120">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="11c3b-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- <span data-ttu-id="11c3b-121">[Definování metody pomocí generování reflexe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="11c3b-121">[Defining a Method with Reflection Emit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span></span>
- [<span data-ttu-id="11c3b-122">Návod: Volání rozhraní API systému Windows</span><span class="sxs-lookup"><span data-stu-id="11c3b-122">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="11c3b-123">Zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="11c3b-123">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)

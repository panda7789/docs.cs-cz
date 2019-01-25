---
title: '#pragma – C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 216adebae8a498ef2f4263f46f8ccd7a20d9202f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622374"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="6005f-102">#pragma (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6005f-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="6005f-103">`#pragma` kompilátor poskytuje zvláštní pokyny pro kompilaci souboru, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="6005f-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="6005f-104">Kompilátor musí podporovat pokynů.</span><span class="sxs-lookup"><span data-stu-id="6005f-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="6005f-105">Jinými slovy, nemůžete použít `#pragma` můžete vytvořit vlastní pokyny k předběžného zpracování.</span><span class="sxs-lookup"><span data-stu-id="6005f-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="6005f-106">Kompilátor jazyka Microsoft C# podporuje následující dva `#pragma` pokyny:</span><span class="sxs-lookup"><span data-stu-id="6005f-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="6005f-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="6005f-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="6005f-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="6005f-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="6005f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6005f-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6005f-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="6005f-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="6005f-111">Název rozpoznaný direktivy pragma.</span><span class="sxs-lookup"><span data-stu-id="6005f-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="6005f-112">Argumenty direktivy pragma specifické.</span><span class="sxs-lookup"><span data-stu-id="6005f-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6005f-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6005f-113">See also</span></span>

- [<span data-ttu-id="6005f-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6005f-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="6005f-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6005f-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="6005f-116">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="6005f-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
- [<span data-ttu-id="6005f-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="6005f-117">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)
- [<span data-ttu-id="6005f-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="6005f-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

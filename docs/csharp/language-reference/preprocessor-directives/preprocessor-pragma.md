---
title: '#direktivy pragma (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 5ae397cc61e0c6b58ed2079369131ebb7e352eae
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747480"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="dcbe4-102">#pragma (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="dcbe4-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="dcbe4-103">`#pragma` kompilátor poskytuje zvláštní pokyny pro kompilaci souboru, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="dcbe4-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="dcbe4-104">Kompilátor musí podporovat pokynů.</span><span class="sxs-lookup"><span data-stu-id="dcbe4-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="dcbe4-105">Jinými slovy, nemůžete použít `#pragma` můžete vytvořit vlastní pokyny k předběžného zpracování.</span><span class="sxs-lookup"><span data-stu-id="dcbe4-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="dcbe4-106">Kompilátor jazyka Microsoft C# podporuje následující dva `#pragma` pokyny:</span><span class="sxs-lookup"><span data-stu-id="dcbe4-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="dcbe4-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="dcbe4-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="dcbe4-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="dcbe4-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="dcbe4-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcbe4-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dcbe4-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="dcbe4-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="dcbe4-111">Název rozpoznaný direktivy pragma.</span><span class="sxs-lookup"><span data-stu-id="dcbe4-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="dcbe4-112">Argumenty direktivy pragma specifické.</span><span class="sxs-lookup"><span data-stu-id="dcbe4-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcbe4-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="dcbe4-113">See Also</span></span>

- [<span data-ttu-id="dcbe4-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dcbe4-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="dcbe4-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="dcbe4-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="dcbe4-116">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="dcbe4-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
- [<span data-ttu-id="dcbe4-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="dcbe4-117">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
- [<span data-ttu-id="dcbe4-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="dcbe4-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

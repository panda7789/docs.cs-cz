---
title: '#Direktiva pragma (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: a4829d5062474922d45a2f4f8e1cddf9023b6ad8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278806"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="0cce4-102">#pragma (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0cce4-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="0cce4-103">`#pragma` poskytuje kompilátor zvláštní pokyny pro kompilaci souboru, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="0cce4-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="0cce4-104">Kompilátor musí podporovat pokynů.</span><span class="sxs-lookup"><span data-stu-id="0cce4-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="0cce4-105">Jinými slovy, nemůžete použít `#pragma` k vytvoření vlastních pokynů předběžného zpracování.</span><span class="sxs-lookup"><span data-stu-id="0cce4-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="0cce4-106">Kompilátor jazyka Microsoft C# podporuje následující dva `#pragma` pokyny:</span><span class="sxs-lookup"><span data-stu-id="0cce4-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="0cce4-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="0cce4-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="0cce4-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="0cce4-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="0cce4-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cce4-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0cce4-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="0cce4-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="0cce4-111">Název známá Direktiva pragma.</span><span class="sxs-lookup"><span data-stu-id="0cce4-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="0cce4-112">Direktiva pragma specifické argumenty.</span><span class="sxs-lookup"><span data-stu-id="0cce4-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cce4-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="0cce4-113">See Also</span></span>  
 [<span data-ttu-id="0cce4-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0cce4-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0cce4-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0cce4-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0cce4-116">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="0cce4-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="0cce4-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="0cce4-117">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
 [<span data-ttu-id="0cce4-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="0cce4-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

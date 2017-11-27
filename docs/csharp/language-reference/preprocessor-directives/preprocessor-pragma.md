---
title: "#<a name=\"pragma-c-reference\"></a>Direktiva pragma (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#pragma'
helpviewer_keywords: '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6f53bd0ed3f35f049b0a1cbb21c5b9a563f9fce9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="pragma-c-reference"></a><span data-ttu-id="d098f-102">#pragma (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d098f-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="d098f-103">`#pragma`poskytuje kompilátor zvláštní pokyny pro kompilaci souboru, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="d098f-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="d098f-104">Kompilátor musí podporovat pokynů.</span><span class="sxs-lookup"><span data-stu-id="d098f-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="d098f-105">Jinými slovy, nemůžete použít `#pragma` k vytvoření vlastních pokynů předběžného zpracování.</span><span class="sxs-lookup"><span data-stu-id="d098f-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="d098f-106">Kompilátor jazyka Microsoft C# podporuje následující dva `#pragma` pokyny:</span><span class="sxs-lookup"><span data-stu-id="d098f-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="d098f-107">#pragma – upozornění</span><span class="sxs-lookup"><span data-stu-id="d098f-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="d098f-108">#pragma – kontrolní součet</span><span class="sxs-lookup"><span data-stu-id="d098f-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="d098f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d098f-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d098f-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="d098f-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="d098f-111">Název známá Direktiva pragma.</span><span class="sxs-lookup"><span data-stu-id="d098f-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="d098f-112">Direktiva pragma specifické argumenty.</span><span class="sxs-lookup"><span data-stu-id="d098f-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d098f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d098f-113">See Also</span></span>  
 [<span data-ttu-id="d098f-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d098f-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d098f-115">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="d098f-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d098f-116">C# direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="d098f-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="d098f-117">#pragma – upozornění</span><span class="sxs-lookup"><span data-stu-id="d098f-117">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
 [<span data-ttu-id="d098f-118">#pragma – kontrolní součet</span><span class="sxs-lookup"><span data-stu-id="d098f-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

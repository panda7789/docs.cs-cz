---
title: '#pragma - C# Reference'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 3bd62364aeae0f21715711324655ef7d00d88afc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712452"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="3ec1c-102">#pragma (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3ec1c-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="3ec1c-103">`#pragma`poskytuje kompilátoru zvláštní pokyny pro kompilaci souboru, ve kterém se objeví.</span><span class="sxs-lookup"><span data-stu-id="3ec1c-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="3ec1c-104">Pokyny musí být podporovány kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="3ec1c-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="3ec1c-105">Jinými slovy nelze `#pragma` použít k vytvoření vlastních pokynů pro předběžné zpracování.</span><span class="sxs-lookup"><span data-stu-id="3ec1c-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="3ec1c-106">Kompilátor Microsoft C# podporuje `#pragma` následující dva pokyny:</span><span class="sxs-lookup"><span data-stu-id="3ec1c-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="3ec1c-107">#pragma varování</span><span class="sxs-lookup"><span data-stu-id="3ec1c-107">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="3ec1c-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="3ec1c-108">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="3ec1c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ec1c-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ec1c-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ec1c-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="3ec1c-111">Jméno uznávaného pragma.</span><span class="sxs-lookup"><span data-stu-id="3ec1c-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="3ec1c-112">Pragma-specifické argumenty.</span><span class="sxs-lookup"><span data-stu-id="3ec1c-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ec1c-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ec1c-113">See also</span></span>

- [<span data-ttu-id="3ec1c-114">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3ec1c-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3ec1c-115">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3ec1c-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3ec1c-116">Direktivy preprocesoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3ec1c-116">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="3ec1c-117">#pragma varování</span><span class="sxs-lookup"><span data-stu-id="3ec1c-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="3ec1c-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="3ec1c-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

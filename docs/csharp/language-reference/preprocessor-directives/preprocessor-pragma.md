---
title: '#pragma – C# reference'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 3bd62364aeae0f21715711324655ef7d00d88afc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712452"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="8ee5d-102">#pragma (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8ee5d-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="8ee5d-103">`#pragma` poskytuje kompilátoru speciální pokyny pro kompilaci souboru, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="8ee5d-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="8ee5d-104">Pokyny musí kompilátor podporovat.</span><span class="sxs-lookup"><span data-stu-id="8ee5d-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="8ee5d-105">Jinými slovy, nemůžete použít `#pragma` k vytvoření vlastních instrukcí pro předzpracování.</span><span class="sxs-lookup"><span data-stu-id="8ee5d-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="8ee5d-106">Kompilátor společnosti C# Microsoft podporuje následující dvě `#pragma` instrukce:</span><span class="sxs-lookup"><span data-stu-id="8ee5d-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="8ee5d-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="8ee5d-107">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="8ee5d-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="8ee5d-108">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="8ee5d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ee5d-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ee5d-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ee5d-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="8ee5d-111">Název rozpoznané direktivy pragma.</span><span class="sxs-lookup"><span data-stu-id="8ee5d-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="8ee5d-112">Argumenty specifické pro direktivu pragma.</span><span class="sxs-lookup"><span data-stu-id="8ee5d-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ee5d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ee5d-113">See also</span></span>

- [<span data-ttu-id="8ee5d-114">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="8ee5d-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8ee5d-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8ee5d-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8ee5d-116">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="8ee5d-116">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="8ee5d-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="8ee5d-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="8ee5d-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="8ee5d-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

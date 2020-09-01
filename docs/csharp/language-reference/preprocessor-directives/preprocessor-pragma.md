---
description: '#pragma – reference jazyka C#'
title: '#pragma – reference jazyka C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 97d7a786c83a8be21f7fd38873061dba0f9278ae
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137952"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="f18f8-103">#pragma (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f18f8-103">#pragma (C# Reference)</span></span>
<span data-ttu-id="f18f8-104">`#pragma` poskytne kompilátoru zvláštní pokyny pro kompilaci souboru, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="f18f8-104">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="f18f8-105">Pokyny musí kompilátor podporovat.</span><span class="sxs-lookup"><span data-stu-id="f18f8-105">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="f18f8-106">Jinými slovy, nemůžete použít `#pragma` k vytvoření vlastních instrukcí pro předzpracování.</span><span class="sxs-lookup"><span data-stu-id="f18f8-106">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="f18f8-107">Kompilátor Microsoft C# podporuje následující dvě `#pragma` pokyny:</span><span class="sxs-lookup"><span data-stu-id="f18f8-107">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="f18f8-108">upozornění #pragma</span><span class="sxs-lookup"><span data-stu-id="f18f8-108">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="f18f8-109">kontrolní součet #pragma</span><span class="sxs-lookup"><span data-stu-id="f18f8-109">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="f18f8-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f18f8-110">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="f18f8-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="f18f8-111">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="f18f8-112">Název rozpoznané direktivy pragma.</span><span class="sxs-lookup"><span data-stu-id="f18f8-112">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="f18f8-113">Argumenty specifické pro direktivu pragma.</span><span class="sxs-lookup"><span data-stu-id="f18f8-113">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f18f8-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f18f8-114">See also</span></span>

- [<span data-ttu-id="f18f8-115">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f18f8-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f18f8-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f18f8-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f18f8-117">C# – direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="f18f8-117">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="f18f8-118">upozornění #pragma</span><span class="sxs-lookup"><span data-stu-id="f18f8-118">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="f18f8-119">kontrolní součet #pragma</span><span class="sxs-lookup"><span data-stu-id="f18f8-119">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

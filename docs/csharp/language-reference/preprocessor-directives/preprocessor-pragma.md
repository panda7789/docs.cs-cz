---
title: '#pragma – C# reference'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 65ca38ff6993117b6ed9f716d4ac93ba2d4a9ddf
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605668"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="85370-102">#pragma (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="85370-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="85370-103">`#pragma`poskytne kompilátoru zvláštní pokyny pro kompilaci souboru, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="85370-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="85370-104">Pokyny musí kompilátor podporovat.</span><span class="sxs-lookup"><span data-stu-id="85370-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="85370-105">Jinými slovy, nemůžete použít `#pragma` k vytvoření vlastních instrukcí pro předzpracování.</span><span class="sxs-lookup"><span data-stu-id="85370-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="85370-106">Kompilátor společnosti C# Microsoft podporuje následující dvě `#pragma` pokyny:</span><span class="sxs-lookup"><span data-stu-id="85370-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="85370-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="85370-107">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="85370-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="85370-108">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="85370-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85370-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="85370-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="85370-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="85370-111">Název rozpoznané direktivy pragma.</span><span class="sxs-lookup"><span data-stu-id="85370-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="85370-112">Argumenty specifické pro direktivu pragma.</span><span class="sxs-lookup"><span data-stu-id="85370-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85370-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85370-113">See also</span></span>

- [<span data-ttu-id="85370-114">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="85370-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="85370-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="85370-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="85370-116">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="85370-116">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="85370-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="85370-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="85370-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="85370-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

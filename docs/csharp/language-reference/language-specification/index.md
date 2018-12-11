---
title: Specifikace konceptu jazyka C# 6.0
ms.date: 05/22/2018
ms.topic: language-reference
helpviewer_keywords:
- C# language, specification
- what's new [C#], language specification
- Visual C#, C# language specification
- language specification [C#]
ms.assetid: e5d5a5cc-636b-4bff-b9c8-a8edc6207c22
ms.openlocfilehash: 0a108e9e625fed3801c283c84a58ea0b503101ff
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147946"
---
# <a name="c-60-draft-language-specification"></a><span data-ttu-id="7bd0e-102">Specifikace konceptu jazyka C# 6.0</span><span class="sxs-lookup"><span data-stu-id="7bd0e-102">C# 6.0 draft language specification</span></span>

<span data-ttu-id="7bd0e-103">Specifikace jazyka C# je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="7bd0e-103">The C# language specification is the definitive source for C# syntax and usage.</span></span> <span data-ttu-id="7bd0e-104">Tato specifikace obsahuje podrobné informace o všech aspektech jazyka, včetně počtu bodů, které nepokrývá dokumentace pro jazyk C#.</span><span class="sxs-lookup"><span data-stu-id="7bd0e-104">This specification contains detailed information about all aspects of the language, including many points that the documentation for C# doesn't cover.</span></span>

<span data-ttu-id="7bd0e-105">Specifikace verze 5.0 vydala v prosinci 2017 jako [Standard ECMA-334 5th Edition](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf) dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7bd0e-105">Version 5.0 of the specification has been released in December 2017 as the [Standard ECMA-334 5th Edition](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf) document.</span></span>

<span data-ttu-id="7bd0e-106">Specifikace verze 6.0 nebyla schválena jako standard.</span><span class="sxs-lookup"><span data-stu-id="7bd0e-106">Version 6.0 of the specification has not been approved as a standard.</span></span> <span data-ttu-id="7bd0e-107">Tento web obsahuje [ *koncept* specifikace jazyka C# 6.0](../../../../_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="7bd0e-107">This site contains the [*draft* C# 6.0 specification](../../../../_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="7bd0e-108">Je sestaven z součástí souborů markdownu [úložiště GitHub dotnet/csharplang](https://github.com/dotnet/csharplang/blob/master/spec/README.md).</span><span class="sxs-lookup"><span data-stu-id="7bd0e-108">It's built from the markdown files contained in the [dotnet/csharplang GitHub repository](https://github.com/dotnet/csharplang/blob/master/spec/README.md).</span></span>

<span data-ttu-id="7bd0e-109">Problémy na specifikace konceptu by měl být vytvořen v [dotnet/csharplang](https://github.com/dotnet/csharplang/issues) úložiště.</span><span class="sxs-lookup"><span data-stu-id="7bd0e-109">Issues on the draft specification should be created in the [dotnet/csharplang](https://github.com/dotnet/csharplang/issues) repository.</span></span> <span data-ttu-id="7bd0e-110">Nebo, pokud vás zajímají opravení chyb můžete najít, můžete odeslat [žádostí o přijetí změn](https://github.com/dotnet/csharplang/pulls) do stejného úložiště.</span><span class="sxs-lookup"><span data-stu-id="7bd0e-110">Or, if you are interested in fixing any errors you find, you may submit a [Pull Request](https://github.com/dotnet/csharplang/pulls) to the same repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="7bd0e-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7bd0e-111">See also</span></span>

- [<span data-ttu-id="7bd0e-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7bd0e-112">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="7bd0e-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7bd0e-113">C# Programming Guide</span></span>](../../programming-guide/index.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="7bd0e-114">Next</span><span class="sxs-lookup"><span data-stu-id="7bd0e-114">Next</span></span>](../../../../_csharplang/spec/introduction.md)
---
title: '#ExternalSource – direktiva'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: fa0a40827c1b3865b90c7d796ea4dd364774e1c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343834"
---
# <a name="externalsource-directive"></a><span data-ttu-id="e6e7e-102">#ExternalSource – direktiva</span><span class="sxs-lookup"><span data-stu-id="e6e7e-102">#ExternalSource Directive</span></span>

<span data-ttu-id="e6e7e-103">Indicates a mapping between specific lines of source code and text external to the source.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6e7e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6e7e-104">Syntax</span></span>  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="e6e7e-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e6e7e-105">Parts</span></span>  

 `StringLiteral`  
 <span data-ttu-id="e6e7e-106">The path to the external source.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="e6e7e-107">The line number of the first line of the external source.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="e6e7e-108">The line where the error occurs in the external source.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="e6e7e-109">Terminates the `#ExternalSource` block.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6e7e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6e7e-110">Remarks</span></span>  

 <span data-ttu-id="e6e7e-111">This directive is used only by the compiler and the debugger.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="e6e7e-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="e6e7e-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="e6e7e-114">External source directives have no effect on compilation and cannot be nested.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="e6e7e-115">They are intended for internal use by the application only.</span><span class="sxs-lookup"><span data-stu-id="e6e7e-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6e7e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6e7e-116">See also</span></span>

- [<span data-ttu-id="e6e7e-117">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="e6e7e-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)

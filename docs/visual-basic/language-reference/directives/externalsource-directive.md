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
ms.openlocfilehash: 146ab41d74b45acc4063e2463baca26c7caa4652
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586588"
---
# <a name="externalsource-directive"></a><span data-ttu-id="3f8c4-102">#ExternalSource – direktiva</span><span class="sxs-lookup"><span data-stu-id="3f8c4-102">#ExternalSource Directive</span></span>
<span data-ttu-id="3f8c4-103">Určuje mapování mezi konkrétní řádků zdrojového kódu a textové externí zdroj.</span><span class="sxs-lookup"><span data-stu-id="3f8c4-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f8c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f8c4-104">Syntax</span></span>  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="3f8c4-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="3f8c4-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="3f8c4-106">Cesta k externí zdroj.</span><span class="sxs-lookup"><span data-stu-id="3f8c4-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="3f8c4-107">Číslo řádku prvního řádku externí zdroje.</span><span class="sxs-lookup"><span data-stu-id="3f8c4-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="3f8c4-108">Na řádku, kde dojde k chybě v externím zdroji.</span><span class="sxs-lookup"><span data-stu-id="3f8c4-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="3f8c4-109">Ukončí `#ExternalSource` bloku.</span><span class="sxs-lookup"><span data-stu-id="3f8c4-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f8c4-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3f8c4-110">Remarks</span></span>  
 <span data-ttu-id="3f8c4-111">Tato direktiva je používána pouze kompilátor a ladicí program.</span><span class="sxs-lookup"><span data-stu-id="3f8c4-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="3f8c4-112">Zdrojový soubor může obsahovat direktivy externího zdroje, které označují mapování mezi konkrétní řádky kódu ve zdrojovém souboru a text externí zdroj, například soubor .aspx.</span><span class="sxs-lookup"><span data-stu-id="3f8c4-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="3f8c4-113">Pokud dojde k chybám v určené zdrojový kód během kompilace, jsou identifikovány jako pocházející z externího zdroje.</span><span class="sxs-lookup"><span data-stu-id="3f8c4-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="3f8c4-114">Externí zdroj direktivy mít žádný vliv na kompilace a nelze je vnořovat.</span><span class="sxs-lookup"><span data-stu-id="3f8c4-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="3f8c4-115">Ty jsou určené aplikací pouze pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="3f8c4-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f8c4-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f8c4-116">See Also</span></span>  
 [<span data-ttu-id="3f8c4-117">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="3f8c4-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)

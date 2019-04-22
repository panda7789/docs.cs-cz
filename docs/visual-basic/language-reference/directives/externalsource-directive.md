---
title: '#ExternalSource – direktiva (Visual Basic)'
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
ms.openlocfilehash: 39e6963c97340daab3f0ab7ad6860695f1f6c135
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823425"
---
# <a name="externalsource-directive"></a><span data-ttu-id="5244b-102">#ExternalSource – direktiva</span><span class="sxs-lookup"><span data-stu-id="5244b-102">#ExternalSource Directive</span></span>
<span data-ttu-id="5244b-103">Určuje mapování mezi konkrétní řádky zdrojového kódu a textem mimo zdroj.</span><span class="sxs-lookup"><span data-stu-id="5244b-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5244b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5244b-104">Syntax</span></span>  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="5244b-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="5244b-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="5244b-106">Cesta k externího zdroje.</span><span class="sxs-lookup"><span data-stu-id="5244b-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="5244b-107">Číslo řádku prvního řádku externího zdroje.</span><span class="sxs-lookup"><span data-stu-id="5244b-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="5244b-108">Na řádku, kde dojde k chybě v externím zdroji.</span><span class="sxs-lookup"><span data-stu-id="5244b-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="5244b-109">Ukončuje `#ExternalSource` bloku.</span><span class="sxs-lookup"><span data-stu-id="5244b-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5244b-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5244b-110">Remarks</span></span>  
 <span data-ttu-id="5244b-111">Tato direktiva se používá pouze v kompilátoru a ladicí program.</span><span class="sxs-lookup"><span data-stu-id="5244b-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="5244b-112">Zdrojový soubor může obsahovat direktivy externího zdroje, které označují mapování mezi konkrétní řádky kódu ve zdrojovém souboru a textem mimo zdroj, například soubor .aspx.</span><span class="sxs-lookup"><span data-stu-id="5244b-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="5244b-113">Pokud nedojde k chybám v kódu zdrojové během kompilace, jsou identifikované jako pocházející z externího zdroje.</span><span class="sxs-lookup"><span data-stu-id="5244b-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="5244b-114">Direktivy externího zdroje nemají žádný vliv při kompilaci a nemohou být vnořeny.</span><span class="sxs-lookup"><span data-stu-id="5244b-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="5244b-115">Ty jsou určené pro interní použití jenom aplikace.</span><span class="sxs-lookup"><span data-stu-id="5244b-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5244b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5244b-116">See also</span></span>

- [<span data-ttu-id="5244b-117">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="5244b-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)

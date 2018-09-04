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
ms.openlocfilehash: dcde8507eb033d0a47d5c5d3fa36176cd63b0856
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556315"
---
# <a name="externalsource-directive"></a><span data-ttu-id="546ea-102">#ExternalSource – direktiva</span><span class="sxs-lookup"><span data-stu-id="546ea-102">#ExternalSource Directive</span></span>
<span data-ttu-id="546ea-103">Určuje mapování mezi konkrétní řádky zdrojového kódu a textem mimo zdroj.</span><span class="sxs-lookup"><span data-stu-id="546ea-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="546ea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="546ea-104">Syntax</span></span>  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="546ea-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="546ea-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="546ea-106">Cesta k externího zdroje.</span><span class="sxs-lookup"><span data-stu-id="546ea-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="546ea-107">Číslo řádku prvního řádku externího zdroje.</span><span class="sxs-lookup"><span data-stu-id="546ea-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="546ea-108">Na řádku, kde dojde k chybě v externím zdroji.</span><span class="sxs-lookup"><span data-stu-id="546ea-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="546ea-109">Ukončuje `#ExternalSource` bloku.</span><span class="sxs-lookup"><span data-stu-id="546ea-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="546ea-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="546ea-110">Remarks</span></span>  
 <span data-ttu-id="546ea-111">Tato direktiva se používá pouze v kompilátoru a ladicí program.</span><span class="sxs-lookup"><span data-stu-id="546ea-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="546ea-112">Zdrojový soubor může obsahovat direktivy externího zdroje, které označují mapování mezi konkrétní řádky kódu ve zdrojovém souboru a textem mimo zdroj, například soubor .aspx.</span><span class="sxs-lookup"><span data-stu-id="546ea-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="546ea-113">Pokud nedojde k chybám v kódu zdrojové během kompilace, jsou identifikované jako pocházející z externího zdroje.</span><span class="sxs-lookup"><span data-stu-id="546ea-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="546ea-114">Direktivy externího zdroje nemají žádný vliv při kompilaci a nemohou být vnořeny.</span><span class="sxs-lookup"><span data-stu-id="546ea-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="546ea-115">Ty jsou určené pro interní použití jenom aplikace.</span><span class="sxs-lookup"><span data-stu-id="546ea-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="546ea-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="546ea-116">See Also</span></span>  
 [<span data-ttu-id="546ea-117">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="546ea-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)

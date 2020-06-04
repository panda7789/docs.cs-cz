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
ms.openlocfilehash: e4c7704c32c3a6c73e069d0b7129d5386696b438
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402989"
---
# <a name="externalsource-directive"></a><span data-ttu-id="30b1d-102">#ExternalSource – direktiva</span><span class="sxs-lookup"><span data-stu-id="30b1d-102">#ExternalSource Directive</span></span>

<span data-ttu-id="30b1d-103">Označuje mapování mezi konkrétními řádky zdrojového kódu a textem externím ke zdroji.</span><span class="sxs-lookup"><span data-stu-id="30b1d-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30b1d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30b1d-104">Syntax</span></span>  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="30b1d-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="30b1d-105">Parts</span></span>  

 `StringLiteral`  
 <span data-ttu-id="30b1d-106">Cesta k externímu zdroji</span><span class="sxs-lookup"><span data-stu-id="30b1d-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="30b1d-107">Číslo řádku prvního řádku externího zdroje.</span><span class="sxs-lookup"><span data-stu-id="30b1d-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="30b1d-108">Řádek, kde dojde k chybě v externím zdroji.</span><span class="sxs-lookup"><span data-stu-id="30b1d-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="30b1d-109">Ukončí `#ExternalSource` blok.</span><span class="sxs-lookup"><span data-stu-id="30b1d-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30b1d-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30b1d-110">Remarks</span></span>  

 <span data-ttu-id="30b1d-111">Tuto direktivu používá pouze kompilátor a ladicí program.</span><span class="sxs-lookup"><span data-stu-id="30b1d-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="30b1d-112">Zdrojový soubor může obsahovat externí zdrojové direktivy, které označují mapování mezi konkrétními řádky kódu ve zdrojovém souboru a textem externím ke zdroji, jako je například soubor. aspx.</span><span class="sxs-lookup"><span data-stu-id="30b1d-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="30b1d-113">Pokud dojde k chybám v určeném zdrojovém kódu během kompilace, jsou identifikovány jako pocházející z externího zdroje.</span><span class="sxs-lookup"><span data-stu-id="30b1d-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="30b1d-114">Direktivy externího zdroje nemají žádný vliv na kompilaci a nemohou být vnořené.</span><span class="sxs-lookup"><span data-stu-id="30b1d-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="30b1d-115">Jsou určené pouze pro interní použití pouze aplikací.</span><span class="sxs-lookup"><span data-stu-id="30b1d-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30b1d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="30b1d-116">See also</span></span>

- [<span data-ttu-id="30b1d-117">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="30b1d-117">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)

---
title: "#<a name=\"externalsource-directive\"></a>ExternalSource – direktiva"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "160"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f90b838e50b65b8652cd9cf6f6ee084e9552f025
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="externalsource-directive"></a><span data-ttu-id="83c24-102">#ExternalSource – direktiva</span><span class="sxs-lookup"><span data-stu-id="83c24-102">#ExternalSource Directive</span></span>
<span data-ttu-id="83c24-103">Určuje mapování mezi konkrétní řádků zdrojového kódu a textové externí zdroj.</span><span class="sxs-lookup"><span data-stu-id="83c24-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83c24-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83c24-104">Syntax</span></span>  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="83c24-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="83c24-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="83c24-106">Cesta k externí zdroj.</span><span class="sxs-lookup"><span data-stu-id="83c24-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="83c24-107">Číslo řádku prvního řádku externí zdroje.</span><span class="sxs-lookup"><span data-stu-id="83c24-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="83c24-108">Na řádku, kde dojde k chybě v externím zdroji.</span><span class="sxs-lookup"><span data-stu-id="83c24-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="83c24-109">Ukončí `#ExternalSource` bloku.</span><span class="sxs-lookup"><span data-stu-id="83c24-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83c24-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83c24-110">Remarks</span></span>  
 <span data-ttu-id="83c24-111">Tato direktiva je používána pouze kompilátor a ladicí program.</span><span class="sxs-lookup"><span data-stu-id="83c24-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="83c24-112">Zdrojový soubor může obsahovat direktivy externího zdroje, které označují mapování mezi konkrétní řádky kódu ve zdrojovém souboru a text externí zdroj, například soubor .aspx.</span><span class="sxs-lookup"><span data-stu-id="83c24-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="83c24-113">Pokud dojde k chybám v určené zdrojový kód během kompilace, jsou identifikovány jako pocházející z externího zdroje.</span><span class="sxs-lookup"><span data-stu-id="83c24-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="83c24-114">Externí zdroj direktivy mít žádný vliv na kompilace a nelze je vnořovat.</span><span class="sxs-lookup"><span data-stu-id="83c24-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="83c24-115">Ty jsou určené aplikací pouze pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="83c24-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83c24-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="83c24-116">See Also</span></span>  
 [<span data-ttu-id="83c24-117">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="83c24-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)

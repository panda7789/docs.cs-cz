---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 011c9499eaa728588e6181e33a96dd75b4a7b84b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648538"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="a5ce4-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5ce4-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="a5ce4-103">Potlačí zobrazení autorským banner a informační zprávy během kompilace.</span><span class="sxs-lookup"><span data-stu-id="a5ce4-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5ce4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5ce4-104">Syntax</span></span>  
  
```  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="a5ce4-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5ce4-105">Remarks</span></span>  
 <span data-ttu-id="a5ce4-106">Pokud zadáte `-nologo`, kompilátor nemá zobrazovat nápis informující o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="a5ce4-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="a5ce4-107">Ve výchozím nastavení `-nologo` není funkční.</span><span class="sxs-lookup"><span data-stu-id="a5ce4-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5ce4-108">`-nologo` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a5ce4-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5ce4-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5ce4-109">Example</span></span>  
 <span data-ttu-id="a5ce4-110">Následující kód zkompiluje `T2.vb` a nemá zobrazovat nápis informující o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="a5ce4-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5ce4-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5ce4-111">See Also</span></span>  
 [<span data-ttu-id="a5ce4-112">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="a5ce4-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="a5ce4-113">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="a5ce4-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

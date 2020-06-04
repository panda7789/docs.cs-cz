---
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: d1307603ebc06b4eb4c3786f1cd2fb432c0cf636
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360459"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="394f2-102">-unlogo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="394f2-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="394f2-103">Potlačí zobrazení nápisu copyrightu a informativní zprávy během kompilace.</span><span class="sxs-lookup"><span data-stu-id="394f2-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="394f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="394f2-104">Syntax</span></span>  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="394f2-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="394f2-105">Remarks</span></span>  
 <span data-ttu-id="394f2-106">Pokud zadáte `-nologo` , kompilátor nezobrazí banner o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="394f2-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="394f2-107">Ve výchozím nastavení `-nologo` není platná.</span><span class="sxs-lookup"><span data-stu-id="394f2-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="394f2-108">Tato `-nologo` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="394f2-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="394f2-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="394f2-109">Example</span></span>  
 <span data-ttu-id="394f2-110">Následující kód zkompiluje `T2.vb` a nezobrazuje banner s copyrightem.</span><span class="sxs-lookup"><span data-stu-id="394f2-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="394f2-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="394f2-111">See also</span></span>

- [<span data-ttu-id="394f2-112">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="394f2-112">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="394f2-113">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="394f2-113">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)

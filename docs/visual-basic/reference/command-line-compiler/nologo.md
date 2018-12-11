---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 21c708ef632cc0ed923713cd49e22d44848b4db3
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131141"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="65ad5-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65ad5-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="65ad5-103">Potlačí zobrazení nápisu o autorských právech a informačních zpráv během kompilace.</span><span class="sxs-lookup"><span data-stu-id="65ad5-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65ad5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65ad5-104">Syntax</span></span>  
  
```  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="65ad5-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65ad5-105">Remarks</span></span>  
 <span data-ttu-id="65ad5-106">Pokud zadáte `-nologo`, kompilátor nezobrazuje o autorských právech banner.</span><span class="sxs-lookup"><span data-stu-id="65ad5-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="65ad5-107">Ve výchozím nastavení `-nologo` není platná.</span><span class="sxs-lookup"><span data-stu-id="65ad5-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65ad5-108">`-nologo` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="65ad5-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65ad5-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="65ad5-109">Example</span></span>  
 <span data-ttu-id="65ad5-110">Následující kód zkompiluje `T2.vb` a o autorských právech banner nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="65ad5-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="65ad5-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="65ad5-111">See Also</span></span>  
 [<span data-ttu-id="65ad5-112">Kompilátor příkazového řádku jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="65ad5-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="65ad5-113">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="65ad5-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

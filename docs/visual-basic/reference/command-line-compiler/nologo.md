---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: c1824e4a086ecdd4b6a776bd6894f6e003d02867
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789000"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="0bf7b-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bf7b-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="0bf7b-103">Potlačí zobrazení nápisu o autorských právech a informačních zpráv během kompilace.</span><span class="sxs-lookup"><span data-stu-id="0bf7b-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bf7b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bf7b-104">Syntax</span></span>  
  
```  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="0bf7b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0bf7b-105">Remarks</span></span>  
 <span data-ttu-id="0bf7b-106">Pokud zadáte `-nologo`, kompilátor nezobrazuje o autorských právech banner.</span><span class="sxs-lookup"><span data-stu-id="0bf7b-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="0bf7b-107">Ve výchozím nastavení `-nologo` není platná.</span><span class="sxs-lookup"><span data-stu-id="0bf7b-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0bf7b-108">`-nologo` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0bf7b-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bf7b-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="0bf7b-109">Example</span></span>  
 <span data-ttu-id="0bf7b-110">Následující kód zkompiluje `T2.vb` a o autorských právech banner nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="0bf7b-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0bf7b-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0bf7b-111">See also</span></span>

- [<span data-ttu-id="0bf7b-112">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="0bf7b-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="0bf7b-113">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="0bf7b-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

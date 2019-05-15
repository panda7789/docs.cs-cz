---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: b707899c845b6b08e008fe229497f682c930044a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588856"
---
# <a name="-noconfig"></a><span data-ttu-id="11d36-102">-noconfig</span><span class="sxs-lookup"><span data-stu-id="11d36-102">-noconfig</span></span>
<span data-ttu-id="11d36-103">Určuje, že by měl kompilátor automaticky odkazovat běžně používané sestavení rozhraní .NET Framework nebo importovat `System` a `Microsoft.VisualBasic` obory názvů.</span><span class="sxs-lookup"><span data-stu-id="11d36-103">Specifies that the compiler should not automatically reference the commonly used .NET Framework assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11d36-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11d36-104">Syntax</span></span>  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="11d36-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11d36-105">Remarks</span></span>  
 <span data-ttu-id="11d36-106">`-noconfig` Přikáže kompilátoru, aby kompilovat s soubor Vbc.rsp, který je umístěn ve stejném adresáři jako soubor Vbc.exe.</span><span class="sxs-lookup"><span data-stu-id="11d36-106">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="11d36-107">Soubor Vbc.rsp odkazuje na běžně používané sestavení rozhraní .NET Framework a importuje `System` a `Microsoft.VisualBasic` obory názvů.</span><span class="sxs-lookup"><span data-stu-id="11d36-107">The Vbc.rsp file references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="11d36-108">Kompilátor implicitně odkazuje na sestavení System.dll, není-li `-nostdlib` je zadána možnost.</span><span class="sxs-lookup"><span data-stu-id="11d36-108">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="11d36-109">`-nostdlib` Přikáže kompilátoru, aby kompilovat s Vbc.rsp nebo automaticky odkazují na toto sestavení System.dll.</span><span class="sxs-lookup"><span data-stu-id="11d36-109">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11d36-110">Vždy je odkazováno na sestavení Mscorlib.dll a Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="11d36-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="11d36-111">Můžete upravit soubor Vbc.rsp zadat další možnosti kompilátoru, které by měl být součástí každé Vbc.exe kompilaci (s výjimkou při zadávání `-noconfig` možnost).</span><span class="sxs-lookup"><span data-stu-id="11d36-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="11d36-112">Další informace najdete v tématu [@ (určení souboru odezvy)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="11d36-112">For more information, see [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span></span>  
  
 <span data-ttu-id="11d36-113">Kompilátor zpracovává možnosti předané `vbc` poslední příkaz.</span><span class="sxs-lookup"><span data-stu-id="11d36-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="11d36-114">Proto všechny možnost na příkazovém řádku přepíše nastavení stejná možnost v soubor Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="11d36-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11d36-115">`-noconfig` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="11d36-115">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11d36-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11d36-116">See also</span></span>

- [<span data-ttu-id="11d36-117">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11d36-117">-nostdlib (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [<span data-ttu-id="11d36-118">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="11d36-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="11d36-119">@ (určení souboru odezvy)</span><span class="sxs-lookup"><span data-stu-id="11d36-119">@ (Specify Response File)</span></span>](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [<span data-ttu-id="11d36-120">– referenční dokumentace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11d36-120">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)

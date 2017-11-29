---
title: /sdkpath
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- sdkpath
- /sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 876922385124db3e8db12c93c75194da83d2526c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sdkpath"></a><span data-ttu-id="1d952-102">/sdkpath</span><span class="sxs-lookup"><span data-stu-id="1d952-102">/sdkpath</span></span>
<span data-ttu-id="1d952-103">Určuje umístění Mscorlib.dll a souboru Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="1d952-103">Specifies the location of Mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d952-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d952-104">Syntax</span></span>  
  
```  
/sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="1d952-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1d952-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="1d952-106">Adresář obsahující verze Mscorlib.dll a souboru Microsoft.VisualBasic.dll sloužící ke kompilaci.</span><span class="sxs-lookup"><span data-stu-id="1d952-106">The directory containing the versions of Mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="1d952-107">Tato cesta se neověří, dokud je načten.</span><span class="sxs-lookup"><span data-stu-id="1d952-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="1d952-108">Uveďte název adresáře v uvozovkách ("") Pokud obsahuje mezeru.</span><span class="sxs-lookup"><span data-stu-id="1d952-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d952-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1d952-109">Remarks</span></span>  
 <span data-ttu-id="1d952-110">Tato možnost umožňuje [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilátoru k načtení souborů Mscorlib.dll a souboru Microsoft.VisualBasic.dll z jiné než výchozí umístění.</span><span class="sxs-lookup"><span data-stu-id="1d952-110">This option tells the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler to load the Mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="1d952-111">`/sdkpath` Možnost byla určena pro použití s [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span><span class="sxs-lookup"><span data-stu-id="1d952-111">The `/sdkpath` option was designed to be used with [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="1d952-112">[!INCLUDE[Compact](~/includes/compact-md.md)] Používá jiné verze těchto podporu knihovny nepoužívejte typy a funkce jazyka nebyla nalezena na zařízení.</span><span class="sxs-lookup"><span data-stu-id="1d952-112">The [!INCLUDE[Compact](~/includes/compact-md.md)] uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d952-113">`/sdkpath` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="1d952-113">The `/sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="1d952-114">`/sdkpath` Když je možnost nastavena [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] načtení projektu zařízení.</span><span class="sxs-lookup"><span data-stu-id="1d952-114">The `/sdkpath` option is set when a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] device project is loaded.</span></span>  
  
 <span data-ttu-id="1d952-115">Můžete určit, že by měl kompilátor kompilovat bez odkazu na Visual Basic Runtime Library pomocí `/vbruntime` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="1d952-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `/vbruntime` compiler option.</span></span> <span data-ttu-id="1d952-116">Další informace najdete v tématu [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span><span class="sxs-lookup"><span data-stu-id="1d952-116">For more information, see [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d952-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d952-117">Example</span></span>  
 <span data-ttu-id="1d952-118">Následující kód zkompiluje `Myfile.vb` s [!INCLUDE[Compact](~/includes/compact-md.md)], pomocí verze Mscorlib.dll a souboru Microsoft.VisualBasic.dll najde v adresáři výchozí instalace z [!INCLUDE[Compact](~/includes/compact-md.md)] na jednotce C.</span><span class="sxs-lookup"><span data-stu-id="1d952-118">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="1d952-119">Obvykle byste použili nejnovější verzi [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1d952-119">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d952-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d952-120">See Also</span></span>  
 [<span data-ttu-id="1d952-121">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="1d952-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1d952-122">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="1d952-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="1d952-123">/ netcf</span><span class="sxs-lookup"><span data-stu-id="1d952-123">/netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [<span data-ttu-id="1d952-124">/ vbruntime</span><span class="sxs-lookup"><span data-stu-id="1d952-124">/vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)

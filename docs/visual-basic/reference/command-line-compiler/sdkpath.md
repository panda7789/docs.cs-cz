---
title: -sdkpath
ms.date: 07/20/2015
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 162c7d58350c381ec667e8a4cd11c03e83fcdf44
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925682"
---
# <a name="-sdkpath"></a><span data-ttu-id="dc85d-102">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="dc85d-102">-sdkpath</span></span>
<span data-ttu-id="dc85d-103">Určuje umístění knihovny mscorlib.dll a Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="dc85d-103">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc85d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc85d-104">Syntax</span></span>  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="dc85d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="dc85d-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="dc85d-106">Adresáře, který obsahuje verze knihovny mscorlib.dll a Microsoft.VisualBasic.dll používat pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="dc85d-106">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="dc85d-107">Tato cesta není ověřená, dokud jej načíst.</span><span class="sxs-lookup"><span data-stu-id="dc85d-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="dc85d-108">Název adresáře uzavřete do uvozovek ("") Pokud obsahuje mezery.</span><span class="sxs-lookup"><span data-stu-id="dc85d-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc85d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dc85d-109">Remarks</span></span>  
 <span data-ttu-id="dc85d-110">Tato možnost informuje kompilátor jazyka Visual Basic se načíst knihovnu mscorlib.dll a Microsoft.VisualBasic.dll soubory z jiné než výchozí umístění.</span><span class="sxs-lookup"><span data-stu-id="dc85d-110">This option tells the Visual Basic compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="dc85d-111">`-sdkpath` Možnost byla navržena pro použití s [- netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span><span class="sxs-lookup"><span data-stu-id="dc85d-111">The `-sdkpath` option was designed to be used with [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="dc85d-112">[!INCLUDE[Compact](~/includes/compact-md.md)] Používá různé verze těchto podporu knihoven a vyhněte se použití typů a jazykových funkcí na zařízeních, nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="dc85d-112">The [!INCLUDE[Compact](~/includes/compact-md.md)] uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc85d-113">`-sdkpath` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="dc85d-113">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="dc85d-114">`-sdkpath` Nastavena možnost při načtení projektu Visual Basic zařízení.</span><span class="sxs-lookup"><span data-stu-id="dc85d-114">The `-sdkpath` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="dc85d-115">Můžete určit, že kompilátor by měl kompilovat bez odkazu na knihovnu Runtime jazyka Visual Basic pomocí `-vbruntime` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="dc85d-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="dc85d-116">Další informace najdete v tématu [- vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span><span class="sxs-lookup"><span data-stu-id="dc85d-116">For more information, see [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc85d-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="dc85d-117">Example</span></span>  
 <span data-ttu-id="dc85d-118">Následující kód zkompiluje `Myfile.vb` s [!INCLUDE[Compact](~/includes/compact-md.md)], použití verze knihovny Mscorlib.dll a Microsoft.VisualBasic.dll součástí výchozí instalační adresář [!INCLUDE[Compact](~/includes/compact-md.md)] na jednotce C:.</span><span class="sxs-lookup"><span data-stu-id="dc85d-118">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="dc85d-119">Obvykle byste použili nejnovější verzi [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dc85d-119">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc85d-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc85d-120">See Also</span></span>  
 [<span data-ttu-id="dc85d-121">Kompilátor příkazového řádku jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dc85d-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="dc85d-122">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="dc85d-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="dc85d-123">-netcf</span><span class="sxs-lookup"><span data-stu-id="dc85d-123">-netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [<span data-ttu-id="dc85d-124">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="dc85d-124">-vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)

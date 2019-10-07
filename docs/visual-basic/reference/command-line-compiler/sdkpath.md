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
ms.openlocfilehash: 46cec7ac3cb78c4fc97e299535f9085eff6daeff
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004691"
---
# <a name="-sdkpath"></a><span data-ttu-id="10ec2-102">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="10ec2-102">-sdkpath</span></span>
<span data-ttu-id="10ec2-103">Určuje umístění knihovny mscorlib. dll a Microsoft. VisualBasic. dll.</span><span class="sxs-lookup"><span data-stu-id="10ec2-103">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10ec2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10ec2-104">Syntax</span></span>  
  
```console  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="10ec2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="10ec2-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="10ec2-106">Adresář obsahující verze mscorlib. dll a Microsoft. VisualBasic. dll, které mají být použity pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="10ec2-106">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="10ec2-107">Tato cesta není ověřena, dokud není načtena.</span><span class="sxs-lookup"><span data-stu-id="10ec2-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="10ec2-108">Uzavřete název adresáře v uvozovkách (""), pokud obsahuje mezeru.</span><span class="sxs-lookup"><span data-stu-id="10ec2-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10ec2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="10ec2-109">Remarks</span></span>  
 <span data-ttu-id="10ec2-110">Tato možnost instruuje kompilátor Visual Basic, aby načetl soubory mscorlib. dll a Microsoft. VisualBasic. dll z jiného než výchozího umístění.</span><span class="sxs-lookup"><span data-stu-id="10ec2-110">This option tells the Visual Basic compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="10ec2-111">Možnost `-sdkpath` byla navržena pro použití s parametrem [-netcf –](../../../visual-basic/reference/command-line-compiler/netcf.md).</span><span class="sxs-lookup"><span data-stu-id="10ec2-111">The `-sdkpath` option was designed to be used with [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="10ec2-112">Prostředí .NET Compact Framework používá různé verze těchto knihoven podpory, aby nedocházelo k použití typů a funkcí jazyka, které se na zařízeních nenašly.</span><span class="sxs-lookup"><span data-stu-id="10ec2-112">The .NET Compact Framework uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="10ec2-113">Možnost `-sdkpath` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="10ec2-113">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="10ec2-114">Možnost `-sdkpath` je nastavena při načtení projektu Visual Basic zařízení.</span><span class="sxs-lookup"><span data-stu-id="10ec2-114">The `-sdkpath` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="10ec2-115">Můžete určit, že má být kompilátor zkompilován bez odkazu na knihovnu modulu runtime Visual Basic pomocí možnosti kompilátoru `-vbruntime`.</span><span class="sxs-lookup"><span data-stu-id="10ec2-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="10ec2-116">Další informace najdete v tématu [– vbruntime –](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span><span class="sxs-lookup"><span data-stu-id="10ec2-116">For more information, see [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="10ec2-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="10ec2-117">Example</span></span>  
 <span data-ttu-id="10ec2-118">Následující kód zkompiluje `Myfile.vb` s prostředí .NET Compact Framework pomocí verzí knihovny mscorlib. dll a Microsoft. VisualBasic. dll, která se nachází ve výchozím instalačním adresáři prostředí .NET Compact Framework na jednotce C.</span><span class="sxs-lookup"><span data-stu-id="10ec2-118">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="10ec2-119">Obvykle byste použili nejnovější verzi prostředí .NET Compact Framework.</span><span class="sxs-lookup"><span data-stu-id="10ec2-119">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="10ec2-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10ec2-120">See also</span></span>

- [<span data-ttu-id="10ec2-121">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="10ec2-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="10ec2-122">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="10ec2-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="10ec2-123">-netcf</span><span class="sxs-lookup"><span data-stu-id="10ec2-123">-netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [<span data-ttu-id="10ec2-124">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="10ec2-124">-vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)

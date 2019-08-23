---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 19a70e500f6b75fd003bdb798f242cddb3926935
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964348"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="6cbb8-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6cbb8-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="6cbb8-103">Způsobí, že kompilátor nebude automaticky odkazovat na standardní knihovny.</span><span class="sxs-lookup"><span data-stu-id="6cbb8-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cbb8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cbb8-104">Syntax</span></span>  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="6cbb8-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6cbb8-105">Remarks</span></span>  
 <span data-ttu-id="6cbb8-106">`-nostdlib` Možnost odebere automatický odkaz na sestavení System. dll a zabrání kompilátoru v čtení souboru Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="6cbb8-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="6cbb8-107">Soubor Vbc. rsp, který je umístěn ve stejném adresáři jako soubor Vbc. exe, odkazuje na běžně používané .NET Framework sestavení a importuje `System` obory názvů a. `Microsoft.VisualBasic`</span><span class="sxs-lookup"><span data-stu-id="6cbb8-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6cbb8-108">Na sestavení knihovny mscorlib. dll a Microsoft. VisualBasic. dll jsou odkazy vždy odkazovány.</span><span class="sxs-lookup"><span data-stu-id="6cbb8-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6cbb8-109">Tato `-nostdlib` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="6cbb8-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cbb8-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="6cbb8-110">Example</span></span>  
 <span data-ttu-id="6cbb8-111">Následující kód zkompiluje `T2.vb` bez odkazování na standardní knihovny.</span><span class="sxs-lookup"><span data-stu-id="6cbb8-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="6cbb8-112">Chcete-li `My` odebrat `_MYTYPE` objekt, je nutné nastavit konstantu podmíněné kompilace na řetězec "Empty".</span><span class="sxs-lookup"><span data-stu-id="6cbb8-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="6cbb8-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6cbb8-113">See also</span></span>

- [<span data-ttu-id="6cbb8-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="6cbb8-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="6cbb8-115">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="6cbb8-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="6cbb8-116">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="6cbb8-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="6cbb8-117">Přizpůsobení výběru objektů dostupných v oboru názvů My</span><span class="sxs-lookup"><span data-stu-id="6cbb8-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)

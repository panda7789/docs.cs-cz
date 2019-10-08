---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 819505df2e7d5f93302f9ed601de856e36ed7124
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005411"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="efbd5-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efbd5-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="efbd5-103">Způsobí, že kompilátor nebude automaticky odkazovat na standardní knihovny.</span><span class="sxs-lookup"><span data-stu-id="efbd5-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efbd5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efbd5-104">Syntax</span></span>  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="efbd5-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="efbd5-105">Remarks</span></span>  
 <span data-ttu-id="efbd5-106">Možnost `-nostdlib` odstraní automatický odkaz na sestavení System. dll a zabrání kompilátoru v čtení souboru Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="efbd5-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="efbd5-107">Soubor Vbc. rsp, který je umístěn ve stejném adresáři jako soubor Vbc. exe, odkazuje na běžně používané .NET Framework sestavení a importuje obory názvů `System` a `Microsoft.VisualBasic`.</span><span class="sxs-lookup"><span data-stu-id="efbd5-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="efbd5-108">Na sestavení knihovny mscorlib. dll a Microsoft. VisualBasic. dll jsou odkazy vždy odkazovány.</span><span class="sxs-lookup"><span data-stu-id="efbd5-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="efbd5-109">Možnost `-nostdlib` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="efbd5-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efbd5-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="efbd5-110">Example</span></span>  
 <span data-ttu-id="efbd5-111">Následující kód zkompiluje `T2.vb` bez odkazování na standardní knihovny.</span><span class="sxs-lookup"><span data-stu-id="efbd5-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="efbd5-112">Chcete-li odebrat objekt `My`, je nutné nastavit konstantu podmíněné kompilace `_MYTYPE` na řetězec "Empty".</span><span class="sxs-lookup"><span data-stu-id="efbd5-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="efbd5-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="efbd5-113">See also</span></span>

- [<span data-ttu-id="efbd5-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="efbd5-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="efbd5-115">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="efbd5-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="efbd5-116">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="efbd5-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="efbd5-117">Přizpůsobení výběru objektů dostupných v oboru názvů My</span><span class="sxs-lookup"><span data-stu-id="efbd5-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)

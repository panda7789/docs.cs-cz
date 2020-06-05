---
title: -nostdlib
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 0934799853323110e73087ba6d8975c30f84d8f7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387709"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="74c1e-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74c1e-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="74c1e-103">Způsobí, že kompilátor nebude automaticky odkazovat na standardní knihovny.</span><span class="sxs-lookup"><span data-stu-id="74c1e-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74c1e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74c1e-104">Syntax</span></span>  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="74c1e-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74c1e-105">Remarks</span></span>  
 <span data-ttu-id="74c1e-106">`-nostdlib`Možnost odebere automatický odkaz na sestavení System. dll a zabrání kompilátoru v čtení souboru Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="74c1e-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="74c1e-107">Soubor Vbc. rsp, který je umístěn ve stejném adresáři jako soubor Vbc. exe, odkazuje na běžně používané .NET Framework sestavení a importuje `System` `Microsoft.VisualBasic` obory názvů a.</span><span class="sxs-lookup"><span data-stu-id="74c1e-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74c1e-108">Na sestavení knihovny mscorlib. dll a Microsoft. VisualBasic. dll jsou odkazy vždy odkazovány.</span><span class="sxs-lookup"><span data-stu-id="74c1e-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74c1e-109">Tato `-nostdlib` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="74c1e-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74c1e-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="74c1e-110">Example</span></span>  
 <span data-ttu-id="74c1e-111">Následující kód zkompiluje `T2.vb` bez odkazování na standardní knihovny.</span><span class="sxs-lookup"><span data-stu-id="74c1e-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="74c1e-112">Chcete-li odebrat objekt, je nutné nastavit `_MYTYPE` konstantu podmíněné kompilace na řetězec "Empty" `My` .</span><span class="sxs-lookup"><span data-stu-id="74c1e-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="74c1e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="74c1e-113">See also</span></span>

- [<span data-ttu-id="74c1e-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="74c1e-114">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="74c1e-115">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="74c1e-115">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="74c1e-116">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="74c1e-116">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="74c1e-117">Přizpůsobení výběru objektů dostupných v oboru názvů My</span><span class="sxs-lookup"><span data-stu-id="74c1e-117">Customizing Which Objects are Available in My</span></span>](../../developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)

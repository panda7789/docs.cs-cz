---
description: -align (možnosti kompilátoru C#)
title: -align (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /filealign
helpviewer_keywords:
- /alignment compiler option [C#]
- filealign compiler option [C#]
- -filealign compiler option [C#]
- /sections compiler option [C#]
- alignment compiler option [C#]
- sections compiler option [C#]
- -sections compiler option [C#]
- /filealign compiler option [C#]
- file sharing [C#]
- -alignment compiler option [C#]
- section alignment [C#]
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
ms.openlocfilehash: d4abe6c3825de211d737f402a745c8953adca4b8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125706"
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="0d049-103">-align (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="0d049-103">-filealign (C# Compiler Options)</span></span>
<span data-ttu-id="0d049-104">Možnost **-souboru align** umožňuje určit velikost oddílů ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="0d049-104">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d049-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d049-105">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="0d049-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0d049-106">Arguments</span></span>  
 `number`  
 <span data-ttu-id="0d049-107">Hodnota, která určuje velikost oddílů ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="0d049-107">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="0d049-108">Platné hodnoty jsou 512, 1024, 2048, 4096 a 8192.</span><span class="sxs-lookup"><span data-stu-id="0d049-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="0d049-109">Tyto hodnoty jsou v bajtech.</span><span class="sxs-lookup"><span data-stu-id="0d049-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d049-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d049-110">Remarks</span></span>  
 <span data-ttu-id="0d049-111">Každý oddíl bude zarovnán na hranici, která je násobkem hodnoty **Zarovnání** .</span><span class="sxs-lookup"><span data-stu-id="0d049-111">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="0d049-112">Neexistuje žádná pevná výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="0d049-112">There is no fixed default.</span></span> <span data-ttu-id="0d049-113">Pokud **parametr není zadán** , modul CLR (Common Language Runtime) vybere výchozí hodnotu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="0d049-113">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="0d049-114">Když zadáte velikost oddílu, ovlivníte velikost výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="0d049-114">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="0d049-115">Změna velikosti oddílu může být užitečná pro programy, které se spustí na menších zařízeních.</span><span class="sxs-lookup"><span data-stu-id="0d049-115">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="0d049-116">Pomocí služby [DUMPBIN](/cpp/build/reference/dumpbin-options) můžete zobrazit informace o oddílech ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="0d049-116">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="0d049-117">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0d049-117">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="0d049-118">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="0d049-118">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="0d049-119">Klikněte na stránku vlastností **Build (sestavit** ).</span><span class="sxs-lookup"><span data-stu-id="0d049-119">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="0d049-120">Klikněte na tlačítko **Upřesnit** .</span><span class="sxs-lookup"><span data-stu-id="0d049-120">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="0d049-121">Upravte vlastnost **Zarovnání souboru** .</span><span class="sxs-lookup"><span data-stu-id="0d049-121">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="0d049-122">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A> .</span><span class="sxs-lookup"><span data-stu-id="0d049-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d049-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d049-123">See also</span></span>

- [<span data-ttu-id="0d049-124">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="0d049-124">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="0d049-125">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="0d049-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

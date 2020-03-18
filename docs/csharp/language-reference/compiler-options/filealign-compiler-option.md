---
title: -filealign (C# Možnosti kompilátoru)
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
ms.openlocfilehash: aed8b412ea1580f7dfa4f87333598d76a85b5e64
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69603020"
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="5e98d-102">-filealign (C# Možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="5e98d-102">-filealign (C# Compiler Options)</span></span>
<span data-ttu-id="5e98d-103">Volba **-filealign** umožňuje určit velikost oddílů ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="5e98d-103">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e98d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e98d-104">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="5e98d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5e98d-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="5e98d-106">Hodnota, která určuje velikost oddílů ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="5e98d-106">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="5e98d-107">Platné hodnoty jsou 512, 1024, 2048, 4096 a 8192.</span><span class="sxs-lookup"><span data-stu-id="5e98d-107">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="5e98d-108">Tyto hodnoty jsou v bajtů.</span><span class="sxs-lookup"><span data-stu-id="5e98d-108">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e98d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5e98d-109">Remarks</span></span>  
 <span data-ttu-id="5e98d-110">Každý oddíl bude zarovnán na hranici, která je násobkem hodnoty **-filealign.**</span><span class="sxs-lookup"><span data-stu-id="5e98d-110">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="5e98d-111">Neexistuje žádné pevné výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="5e98d-111">There is no fixed default.</span></span> <span data-ttu-id="5e98d-112">Pokud **-filealign** není zadán, soubor runtime společného jazyka vybere výchozí v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="5e98d-112">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="5e98d-113">Zadáním velikosti oddílu ovlivníte velikost výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="5e98d-113">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="5e98d-114">Změna velikosti oddílu může být užitečná pro programy, které budou spuštěny na menších zařízeních.</span><span class="sxs-lookup"><span data-stu-id="5e98d-114">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="5e98d-115">Pomocí [funkce DUMPBIN](/cpp/build/reference/dumpbin-options) můžete zobrazit informace o oddílech ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="5e98d-115">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="5e98d-116">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5e98d-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="5e98d-117">Otevřete stránku **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="5e98d-117">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="5e98d-118">Klikněte na stránku vlastností **Sestavení.**</span><span class="sxs-lookup"><span data-stu-id="5e98d-118">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="5e98d-119">Klepněte na tlačítko **Upřesnit.**</span><span class="sxs-lookup"><span data-stu-id="5e98d-119">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="5e98d-120">Upravte vlastnost **Zarovnání souborů.**</span><span class="sxs-lookup"><span data-stu-id="5e98d-120">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="5e98d-121">Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>kompilátoru programově, naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="5e98d-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e98d-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e98d-122">See also</span></span>

- [<span data-ttu-id="5e98d-123">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5e98d-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="5e98d-124">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="5e98d-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

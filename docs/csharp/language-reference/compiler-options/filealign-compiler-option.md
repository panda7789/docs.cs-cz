---
title: -align (C# možnosti kompilátoru)
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
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603020"
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="0725d-102">-align (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="0725d-102">-filealign (C# Compiler Options)</span></span>
<span data-ttu-id="0725d-103">Možnost **-souboru align** umožňuje určit velikost oddílů ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="0725d-103">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0725d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0725d-104">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="0725d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0725d-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="0725d-106">Hodnota, která určuje velikost oddílů ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="0725d-106">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="0725d-107">Platné hodnoty jsou 512, 1024, 2048, 4096 a 8192.</span><span class="sxs-lookup"><span data-stu-id="0725d-107">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="0725d-108">Tyto hodnoty jsou v bajtech.</span><span class="sxs-lookup"><span data-stu-id="0725d-108">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0725d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0725d-109">Remarks</span></span>  
 <span data-ttu-id="0725d-110">Každý oddíl bude zarovnán na hranici, která je násobkem hodnoty **Zarovnání** .</span><span class="sxs-lookup"><span data-stu-id="0725d-110">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="0725d-111">Neexistuje žádná pevná výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="0725d-111">There is no fixed default.</span></span> <span data-ttu-id="0725d-112">Pokud parametr není zadán, modul CLR (Common Language Runtime) vybere výchozí hodnotu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="0725d-112">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="0725d-113">Když zadáte velikost oddílu, ovlivníte velikost výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="0725d-113">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="0725d-114">Změna velikosti oddílu může být užitečná pro programy, které se spustí na menších zařízeních.</span><span class="sxs-lookup"><span data-stu-id="0725d-114">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="0725d-115">Pomocí služby [DUMPBIN](/cpp/build/reference/dumpbin-options) můžete zobrazit informace o oddílech ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="0725d-115">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="0725d-116">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0725d-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="0725d-117">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="0725d-117">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="0725d-118">Klikněte na stránku vlastností **Build (sestavit** ).</span><span class="sxs-lookup"><span data-stu-id="0725d-118">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="0725d-119">Klikněte na tlačítko **Upřesnit** .</span><span class="sxs-lookup"><span data-stu-id="0725d-119">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="0725d-120">Upravte vlastnost **Zarovnání souboru** .</span><span class="sxs-lookup"><span data-stu-id="0725d-120">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="0725d-121">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>v tématu.</span><span class="sxs-lookup"><span data-stu-id="0725d-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0725d-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0725d-122">See also</span></span>

- [<span data-ttu-id="0725d-123">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0725d-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="0725d-124">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="0725d-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

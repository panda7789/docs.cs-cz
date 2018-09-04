---
title: -filealign (možnosti kompilátoru C#)
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
ms.openlocfilehash: 39b5aeecba39c0e5377fd4f76902dae4b678c324
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530399"
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="9493d-102">-filealign (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="9493d-102">-filealign (C# Compiler Options)</span></span>
<span data-ttu-id="9493d-103">**- Filealign** možnost umožňuje zadat velikost oddíly výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="9493d-103">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9493d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9493d-104">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="9493d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9493d-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="9493d-106">Hodnota, která určuje velikost oddíly výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="9493d-106">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="9493d-107">Platné hodnoty jsou 512, 1024, 2048, 4096 a 8192.</span><span class="sxs-lookup"><span data-stu-id="9493d-107">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="9493d-108">Tyto hodnoty jsou v bajtech.</span><span class="sxs-lookup"><span data-stu-id="9493d-108">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9493d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9493d-109">Remarks</span></span>  
 <span data-ttu-id="9493d-110">Každý oddíl se zarovnáno na hranici, která je násobkem **- filealign** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9493d-110">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="9493d-111">Neexistuje žádná pevná výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="9493d-111">There is no fixed default.</span></span> <span data-ttu-id="9493d-112">Pokud **- filealign** není zadán, modul common language runtime zvolí výchozí v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="9493d-112">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="9493d-113">Tak, že určíte velikost oddílu, vliv na velikost výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="9493d-113">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="9493d-114">Změna velikosti oddílu může být užitečné pro programy, které poběží na menších zařízeních.</span><span class="sxs-lookup"><span data-stu-id="9493d-114">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="9493d-115">Použití [DUMPBIN](/cpp/build/reference/dumpbin-options) zobrazíte informace o oddílech výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="9493d-115">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="9493d-116">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9493d-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="9493d-117">Otevřete v projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="9493d-117">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="9493d-118">Klikněte na tlačítko **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="9493d-118">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="9493d-119">Klikněte na tlačítko **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="9493d-119">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="9493d-120">Upravit **zarovnání souboru** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9493d-120">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="9493d-121">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="9493d-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9493d-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="9493d-122">See Also</span></span>  

- [<span data-ttu-id="9493d-123">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9493d-123">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="9493d-124">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="9493d-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

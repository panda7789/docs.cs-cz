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
ms.openlocfilehash: f3ce1bb864c4cb0b1c330de7d96649f9870231e8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328696"
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="26290-102">-filealign (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="26290-102">-filealign (C# Compiler Options)</span></span>
<span data-ttu-id="26290-103">**- Filealign** možnost umožňuje zadat velikost oddíly výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="26290-103">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26290-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26290-104">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="26290-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="26290-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="26290-106">Hodnota, která určuje velikost oddíly výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="26290-106">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="26290-107">Platné hodnoty jsou 512, 1024, 2048, 4096 a 8192.</span><span class="sxs-lookup"><span data-stu-id="26290-107">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="26290-108">Tyto hodnoty jsou v bajtech.</span><span class="sxs-lookup"><span data-stu-id="26290-108">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26290-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="26290-109">Remarks</span></span>  
 <span data-ttu-id="26290-110">Každý oddíl se zarovnáno na hranici, která je násobkem **- filealign** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="26290-110">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="26290-111">Neexistuje žádná pevná výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="26290-111">There is no fixed default.</span></span> <span data-ttu-id="26290-112">Pokud **- filealign** není zadán, modul common language runtime zvolí výchozí v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="26290-112">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="26290-113">Tak, že určíte velikost oddílu, vliv na velikost výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="26290-113">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="26290-114">Změna velikosti oddílu může být užitečné pro programy, které poběží na menších zařízeních.</span><span class="sxs-lookup"><span data-stu-id="26290-114">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="26290-115">Použití [DUMPBIN](/cpp/build/reference/dumpbin-options) zobrazíte informace o oddílech výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="26290-115">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="26290-116">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="26290-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="26290-117">Otevřete v projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="26290-117">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="26290-118">Klikněte na tlačítko **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="26290-118">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="26290-119">Klikněte na tlačítko **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="26290-119">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="26290-120">Upravit **zarovnání souboru** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="26290-120">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="26290-121">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="26290-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26290-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26290-122">See also</span></span>

- [<span data-ttu-id="26290-123">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="26290-123">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="26290-124">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="26290-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

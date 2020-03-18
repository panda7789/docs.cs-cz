---
title: -checked (C# Možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: cb4dbadfa4efd0750ffd3dea88a3f661e2f85a8e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173767"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="6e6d4-102">-checked (C# Možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="6e6d4-102">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="6e6d4-103">Možnost **-checked** určuje, zda celočíselný aritmetický příkaz, jehož výsledkem je hodnota, která je mimo rozsah datového typu a která není v oboru [zaškrtnutého](../keywords/checked.md) nebo [nekontrolovaného](../keywords/unchecked.md) klíčového slova, způsobí výjimku za běhu.</span><span class="sxs-lookup"><span data-stu-id="6e6d4-103">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../keywords/checked.md) or [unchecked](../keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e6d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e6d4-104">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="6e6d4-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6e6d4-105">Remarks</span></span>  
 <span data-ttu-id="6e6d4-106">Celočíselný aritmetický příkaz, který je `checked` v `unchecked` oboru nebo klíčové slovo, nepodléhá účinku **zaškrtnuté možnosti ..The** integer arithmetic statement that is in the scope of a or keyword is not subject to the effect of the-checked option.</span><span class="sxs-lookup"><span data-stu-id="6e6d4-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="6e6d4-107">Pokud celočíselné aritmetické prohlášení, které není `checked` v `unchecked` oboru nebo klíčové slovo má za následek hodnotu mimo rozsah datového typu a **-checked+** (nebo-checked ) se používá v kompilaci, tento příkaz způsobí výjimku v době běhu. **-checked**</span><span class="sxs-lookup"><span data-stu-id="6e6d4-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="6e6d4-108">Pokud **-checked-** se používá v kompilaci, tento příkaz nezpůsobí výjimku za běhu.</span><span class="sxs-lookup"><span data-stu-id="6e6d4-108">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="6e6d4-109">Výchozí hodnota pro tuto možnost je **-checked-**; kontrola přetečení je zakázána.</span><span class="sxs-lookup"><span data-stu-id="6e6d4-109">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>

 <span data-ttu-id="6e6d4-110">Někdy automatizované nástroje, které se používají k vytváření velkých aplikací nastavených na +.</span><span class="sxs-lookup"><span data-stu-id="6e6d4-110">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="6e6d4-111">Jedním z scénářů pro použití -checked- je přepsat globální výchozí nástroj zadáním -checked-.</span><span class="sxs-lookup"><span data-stu-id="6e6d4-111">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6e6d4-112">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6e6d4-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="6e6d4-113">Otevřete stránku **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="6e6d4-113">Open the project's **Properties** page.</span></span> <span data-ttu-id="6e6d4-114">Další informace naleznete v [tématu Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="6e6d4-114">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="6e6d4-115">Klikněte na stránku vlastností **Sestavení.**</span><span class="sxs-lookup"><span data-stu-id="6e6d4-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="6e6d4-116">Klepněte na tlačítko **Upřesnit.**</span><span class="sxs-lookup"><span data-stu-id="6e6d4-116">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="6e6d4-117">Upravte vlastnost **Kontrola aritmetického přetečení.**</span><span class="sxs-lookup"><span data-stu-id="6e6d4-117">Modify the **Check for arithmetic overflow** property.</span></span>  
  
 <span data-ttu-id="6e6d4-118">Chcete-li získat přístup k této <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>možnosti kompilátoru programově, naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="6e6d4-118">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e6d4-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="6e6d4-119">Example</span></span>  
 <span data-ttu-id="6e6d4-120">Následující příkaz zkompiluje `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="6e6d4-120">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="6e6d4-121">Použití `-checked` v příkazu určuje, že všechny celé číslo aritmetické prohlášení v souboru, který není v oboru `checked` nebo `unchecked` klíčové slovo a výsledkem hodnota, která je mimo rozsah datového typu, způsobí výjimku za běhu.</span><span class="sxs-lookup"><span data-stu-id="6e6d4-121">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e6d4-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e6d4-122">See also</span></span>

- [<span data-ttu-id="6e6d4-123">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6e6d4-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="6e6d4-124">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="6e6d4-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

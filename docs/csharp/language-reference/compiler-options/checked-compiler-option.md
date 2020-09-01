---
description: -Checked (možnosti kompilátoru C#)
title: -Checked (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: 5c90696edd3031271e16cd2c1a332da5b605f81f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125940"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="89e57-103">-Checked (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="89e57-103">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="89e57-104">Možnost **-checked** určuje, zda celočíselný aritmetický příkaz, jehož výsledkem je hodnota, která je mimo rozsah datového typu a který není v oboru klíčového slova [checked](../keywords/checked.md) nebo [unchecked](../keywords/unchecked.md) , způsobuje výjimku za běhu.</span><span class="sxs-lookup"><span data-stu-id="89e57-104">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../keywords/checked.md) or [unchecked](../keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89e57-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="89e57-105">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="89e57-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89e57-106">Remarks</span></span>  
 <span data-ttu-id="89e57-107">Celočíselný aritmetický příkaz, který je v oboru `checked` `unchecked` klíčového slova or, není v souladu s možností **-checked** .</span><span class="sxs-lookup"><span data-stu-id="89e57-107">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="89e57-108">Pokud celočíselný aritmetický příkaz, který není v oboru `checked` `unchecked` klíčového slova nebo, má za následek hodnotu mimo rozsah datového typu a **-zaškrtnuto +** (nebo **-checked**), je použita v kompilaci, tento příkaz způsobí výjimku za běhu.</span><span class="sxs-lookup"><span data-stu-id="89e57-108">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="89e57-109">Pokud je **zaškrtnuto –** používá se v kompilaci, tento příkaz během běhu nezpůsobí výjimku.</span><span class="sxs-lookup"><span data-stu-id="89e57-109">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="89e57-110">Výchozí hodnota pro tuto možnost je **-zaškrtnuto –**; kontrola přetečení je zakázána.</span><span class="sxs-lookup"><span data-stu-id="89e57-110">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>

 <span data-ttu-id="89e57-111">V některých případech se automatizované nástroje, které se používají k sestavení velkých aplikací, zaškrtne na +.</span><span class="sxs-lookup"><span data-stu-id="89e57-111">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="89e57-112">Jeden scénář pro použití – zaškrtnuto – slouží k přepsání globální výchozí hodnoty nástroje zadáním-Checked-.</span><span class="sxs-lookup"><span data-stu-id="89e57-112">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="89e57-113">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="89e57-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="89e57-114">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="89e57-114">Open the project's **Properties** page.</span></span> <span data-ttu-id="89e57-115">Další informace naleznete v tématu [Stránka sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="89e57-115">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="89e57-116">Klikněte na stránku vlastností **Build (sestavit** ).</span><span class="sxs-lookup"><span data-stu-id="89e57-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="89e57-117">Klikněte na tlačítko **Upřesnit** .</span><span class="sxs-lookup"><span data-stu-id="89e57-117">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="89e57-118">Upravte vlastnost **check pro aritmetické přetečení** .</span><span class="sxs-lookup"><span data-stu-id="89e57-118">Modify the **Check for arithmetic overflow** property.</span></span>  
  
 <span data-ttu-id="89e57-119">Chcete-li získat přístup k této možnosti kompilátoru programově, přečtěte si téma <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A> .</span><span class="sxs-lookup"><span data-stu-id="89e57-119">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89e57-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="89e57-120">Example</span></span>  
 <span data-ttu-id="89e57-121">Následující příkaz zkompiluje `t2.cs` .</span><span class="sxs-lookup"><span data-stu-id="89e57-121">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="89e57-122">Použití `-checked` v příkazu určuje, že jakýkoli celočíselný aritmetický příkaz v souboru, který není v oboru `checked` `unchecked` klíčového slova or, a který má za následek hodnotu, která je mimo rozsah datového typu, způsobuje výjimku za běhu.</span><span class="sxs-lookup"><span data-stu-id="89e57-122">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="89e57-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="89e57-123">See also</span></span>

- [<span data-ttu-id="89e57-124">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="89e57-124">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="89e57-125">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="89e57-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

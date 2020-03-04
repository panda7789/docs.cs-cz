---
title: -Checked (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: 44dc0fc8f50e5248ce2fca17c36f7309a6aca8d1
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239689"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="51242-102">-Checked (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="51242-102">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="51242-103">Možnost **-checked** určuje, zda celočíselný aritmetický příkaz, jehož výsledkem je hodnota, která je mimo rozsah datového typu a který není v oboru klíčového slova [checked](../keywords/checked.md) nebo [unchecked](../keywords/unchecked.md) , způsobuje výjimku za běhu.</span><span class="sxs-lookup"><span data-stu-id="51242-103">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../keywords/checked.md) or [unchecked](../keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51242-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51242-104">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="51242-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51242-105">Remarks</span></span>  
 <span data-ttu-id="51242-106">Celočíselný aritmetický příkaz, který je v oboru klíčového slova `checked` nebo `unchecked`, nepodléhá vlivu možnosti **-checked** .</span><span class="sxs-lookup"><span data-stu-id="51242-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="51242-107">Pokud celočíselný aritmetický příkaz, který není v rozsahu `checked` nebo `unchecked`, má za následek hodnotu mimo rozsah datového typu a **-zaškrtnuto +** (nebo **-checked**) se používá v kompilaci, tento příkaz způsobí výjimku v době běhu.</span><span class="sxs-lookup"><span data-stu-id="51242-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="51242-108">Pokud je **zaškrtnuto –** používá se v kompilaci, tento příkaz během běhu nezpůsobí výjimku.</span><span class="sxs-lookup"><span data-stu-id="51242-108">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="51242-109">Výchozí hodnota pro tuto možnost je **-zaškrtnuto –** ; kontrola přetečení je zakázána.</span><span class="sxs-lookup"><span data-stu-id="51242-109">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>
 
 <span data-ttu-id="51242-110">V některých případech se automatizované nástroje, které se používají k sestavení velkých aplikací, zaškrtne na +.</span><span class="sxs-lookup"><span data-stu-id="51242-110">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="51242-111">Jeden scénář pro použití – zaškrtnuto – slouží k přepsání globální výchozí hodnoty nástroje zadáním-Checked-.</span><span class="sxs-lookup"><span data-stu-id="51242-111">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="51242-112">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="51242-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="51242-113">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="51242-113">Open the project's **Properties** page.</span></span> <span data-ttu-id="51242-114">Další informace naleznete v tématu [Stránka sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="51242-114">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="51242-115">Klikněte na stránku vlastností **Build (sestavit** ).</span><span class="sxs-lookup"><span data-stu-id="51242-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="51242-116">Klikněte na tlačítko **Upřesnit**.</span><span class="sxs-lookup"><span data-stu-id="51242-116">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="51242-117">Upravte vlastnost **check pro aritmetické přetečení** .</span><span class="sxs-lookup"><span data-stu-id="51242-117">Modify the **Check for arithmetic overflow** property.</span></span>  
  
 <span data-ttu-id="51242-118">Chcete-li získat přístup k této možnosti kompilátoru programově, přečtěte si téma <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span><span class="sxs-lookup"><span data-stu-id="51242-118">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51242-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="51242-119">Example</span></span>  
 <span data-ttu-id="51242-120">Následující příkaz zkompiluje `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="51242-120">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="51242-121">Použití `-checked` v příkazu určuje, že jakýkoli celočíselný aritmetický příkaz v souboru, který není v oboru klíčového slova `checked` nebo `unchecked`, a jehož výsledkem je hodnota, která je mimo rozsah datového typu, způsobuje výjimku za běhu.</span><span class="sxs-lookup"><span data-stu-id="51242-121">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="51242-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="51242-122">See also</span></span>

- [<span data-ttu-id="51242-123">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="51242-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="51242-124">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="51242-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

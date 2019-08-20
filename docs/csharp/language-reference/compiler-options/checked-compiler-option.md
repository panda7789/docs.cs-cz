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
ms.openlocfilehash: 4e07698e7abdad00983b61412fa2a57e651d4d46
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606996"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="79816-102">-Checked (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="79816-102">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="79816-103">Možnost **-checked** určuje, zda celočíselný aritmetický příkaz, jehož výsledkem je hodnota, která je mimo rozsah datového typu a který není v oboru klíčového slova [checked](../keywords/checked.md) nebo unchecked [](../keywords/unchecked.md) , způsobuje výjimku za běhu.</span><span class="sxs-lookup"><span data-stu-id="79816-103">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../keywords/checked.md) or [unchecked](../keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79816-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79816-104">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="79816-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79816-105">Remarks</span></span>  
 <span data-ttu-id="79816-106">Celočíselný aritmetický příkaz, který je v oboru `checked` klíčového slova or `unchecked` , není v souladu s možností **-checked** .</span><span class="sxs-lookup"><span data-stu-id="79816-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="79816-107">`checked` Pokud celočíselný aritmetický příkaz, který není v oboru klíčového slova nebo `unchecked` , má za následek hodnotu mimo rozsah datového typu a **-zaškrtnuto +** (nebo **-checked**) se používá v kompilaci, tento příkaz způsobí výjimka v době běhu.</span><span class="sxs-lookup"><span data-stu-id="79816-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="79816-108">Pokud je **zaškrtnuto –** používá se v kompilaci, tento příkaz během běhu nezpůsobí výjimku.</span><span class="sxs-lookup"><span data-stu-id="79816-108">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="79816-109">Výchozí hodnota pro tuto možnost je **-zaškrtnuto –** ; kontrola přetečení je zakázána.</span><span class="sxs-lookup"><span data-stu-id="79816-109">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>
 
 <span data-ttu-id="79816-110">V některých případech se automatizované nástroje, které se používají k sestavení velkých aplikací, zaškrtne na +.</span><span class="sxs-lookup"><span data-stu-id="79816-110">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="79816-111">Jeden scénář pro použití – zaškrtnuto – slouží k přepsání globální výchozí hodnoty nástroje zadáním-Checked-.</span><span class="sxs-lookup"><span data-stu-id="79816-111">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="79816-112">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="79816-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="79816-113">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="79816-113">Open the project's **Properties** page.</span></span> <span data-ttu-id="79816-114">Další informace naleznete v tématu [Stránka sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="79816-114">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="79816-115">Klikněte na stránku vlastností **Build (sestavit** ).</span><span class="sxs-lookup"><span data-stu-id="79816-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="79816-116">Klikněte na tlačítko **Upřesnit** .</span><span class="sxs-lookup"><span data-stu-id="79816-116">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="79816-117">Upravte vlastnost **check pro vlastnost aritmetického přetečení nebo podtečení** .</span><span class="sxs-lookup"><span data-stu-id="79816-117">Modify the **Check for arithmetic overflow/underflow** property.</span></span>  
  
 <span data-ttu-id="79816-118">Chcete-li získat přístup k této možnosti <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>kompilátoru programově, přečtěte si téma.</span><span class="sxs-lookup"><span data-stu-id="79816-118">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79816-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="79816-119">Example</span></span>  
 <span data-ttu-id="79816-120">Následující příkaz zkompiluje `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="79816-120">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="79816-121">Použití `-checked` v příkazu určuje, že jakýkoli celočíselný aritmetický příkaz v souboru, který není v oboru `checked` klíčového slova or `unchecked` , a který vede k hodnotě, která je mimo rozsah datového typu, způsobuje výjimku při spuštění. interval.</span><span class="sxs-lookup"><span data-stu-id="79816-121">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="79816-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79816-122">See also</span></span>

- [<span data-ttu-id="79816-123">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="79816-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="79816-124">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="79816-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

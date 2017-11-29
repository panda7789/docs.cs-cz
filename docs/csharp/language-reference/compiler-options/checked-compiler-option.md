---
title: "-zaškrtnutí (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e02f82bb0dd2952bd2f192af7ff233194a045619
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="checked-c-compiler-options"></a><span data-ttu-id="6b2b9-102">/checked (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="6b2b9-102">/checked (C# Compiler Options)</span></span>
<span data-ttu-id="6b2b9-103">**/ Checked** možnost určuje, zda celočíselný aritmetický příkaz výsledkem hodnotu, která je mimo rozsah datového typu a zda není v oboru [zaškrtnutí](../../../csharp/language-reference/keywords/checked.md) nebo [ nezaškrtnuté](../../../csharp/language-reference/keywords/unchecked.md) – klíčové slovo, způsobí spuštění výjimky.</span><span class="sxs-lookup"><span data-stu-id="6b2b9-103">The **/checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../../../csharp/language-reference/keywords/checked.md) or [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b2b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b2b9-104">Syntax</span></span>  
  
```console  
/checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="6b2b9-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b2b9-105">Remarks</span></span>  
 <span data-ttu-id="6b2b9-106">Celočíselný aritmetický příkaz, který je v oboru `checked` nebo `unchecked` – klíčové slovo není v souladu účinku **/ checked** možnost.</span><span class="sxs-lookup"><span data-stu-id="6b2b9-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **/checked** option.</span></span>  
  
 <span data-ttu-id="6b2b9-107">Pokud celočíselný aritmetický příkaz, který není v oboru `checked` nebo `unchecked` – klíčové slovo, které jsou výsledkem je hodnota mimo rozsah datového typu, a **/ checked +** (**/ checked**) se používá v kompilace, že příkaz dojde k výjimce v době běhu.</span><span class="sxs-lookup"><span data-stu-id="6b2b9-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **/checked+** (**/checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="6b2b9-108">Pokud **/ checked –** se používá při kompilaci, že příkaz nezpůsobí výjimku za běhu.</span><span class="sxs-lookup"><span data-stu-id="6b2b9-108">If **/checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="6b2b9-109">Výchozí hodnota pro tuto možnost je **/ checked –**.</span><span class="sxs-lookup"><span data-stu-id="6b2b9-109">The default value for this option is **/checked-**.</span></span> <span data-ttu-id="6b2b9-110">Jeden scénář použití **/ checked –** je vytváření velkých aplikací.</span><span class="sxs-lookup"><span data-stu-id="6b2b9-110">One scenario for using **/checked-** is in building large applications.</span></span> <span data-ttu-id="6b2b9-111">Někdy automatizované nástroje se používají k vytváření těchto aplikací a může takový nástroj automaticky nastaví **/ checked** na +.</span><span class="sxs-lookup"><span data-stu-id="6b2b9-111">Sometimes automated tools are used to build such applications, and such a tool might automatically set **/checked** to +.</span></span> <span data-ttu-id="6b2b9-112">Výchozí globální nástroje můžete přepsat zadáním **/ checked –**.</span><span class="sxs-lookup"><span data-stu-id="6b2b9-112">You can override the tool's global default by specifying **/checked-**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6b2b9-113">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6b2b9-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="6b2b9-114">Otevření projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="6b2b9-114">Open the project's **Properties** page.</span></span> <span data-ttu-id="6b2b9-115">Další informace najdete v tématu [stránka sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="6b2b9-115">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="6b2b9-116">Klikněte **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="6b2b9-116">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="6b2b9-117">Klikněte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="6b2b9-117">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="6b2b9-118">Změnit **Kontrola aritmetického přetečení nebo podtečení** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6b2b9-118">Modify the **Check for arithmetic overflow/underflow** property.</span></span>  
  
 <span data-ttu-id="6b2b9-119">K této možnosti kompilátoru prostřednictvím kódu programu, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span><span class="sxs-lookup"><span data-stu-id="6b2b9-119">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b2b9-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b2b9-120">Example</span></span>  
 <span data-ttu-id="6b2b9-121">Následující příkaz zkompiluje `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="6b2b9-121">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="6b2b9-122">Použití `/checked` v příkazu určuje, že všechny celočíselný aritmetický příkaz v souboru, který není v oboru `checked` nebo `unchecked` – klíčové slovo a jehož výsledkem je hodnota, která je mimo rozsah datového typu, dojde k výjimce při spuštění čas.</span><span class="sxs-lookup"><span data-stu-id="6b2b9-122">The use of `/checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs /checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b2b9-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b2b9-123">See Also</span></span>  
 [<span data-ttu-id="6b2b9-124">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="6b2b9-124">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="6b2b9-125">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="6b2b9-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  

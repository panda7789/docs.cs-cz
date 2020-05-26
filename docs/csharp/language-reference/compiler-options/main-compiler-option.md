---
title: -Main (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 7d3cfce474023907eda0bc40b692e4bbb65ffb96
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802834"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="fc010-102">-Main (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="fc010-102">-main (C# Compiler Options)</span></span>
<span data-ttu-id="fc010-103">Tato možnost určuje třídu, která obsahuje vstupní bod pro program, pokud více než jedna třída obsahuje metodu **Main** .</span><span class="sxs-lookup"><span data-stu-id="fc010-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc010-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc010-104">Syntax</span></span>  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="fc010-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fc010-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="fc010-106">Typ, který obsahuje metodu **Main** .</span><span class="sxs-lookup"><span data-stu-id="fc010-106">The type that contains the **Main** method.</span></span>  
 <span data-ttu-id="fc010-107">Poskytnutý název třídy musí být plně kvalifikovaný; musí zahrnovat úplný obor názvů obsahující třídu následovaný názvem třídy.</span><span class="sxs-lookup"><span data-stu-id="fc010-107">The provided class name must be fully qualified; it must include the full namespace containing the class, followed by the class name.</span></span> <span data-ttu-id="fc010-108">Například pokud `Main` je metoda umístěna uvnitř `Program` třídy v `MyApplication.Core` oboru názvů, musí být možnost kompilátoru `-main:MyApplication.Core.Program` .</span><span class="sxs-lookup"><span data-stu-id="fc010-108">For example, when the `Main` method is located inside the `Program` class in the `MyApplication.Core` namespace, the compiler option has to be `-main:MyApplication.Core.Program`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="fc010-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc010-109">Remarks</span></span>  
 <span data-ttu-id="fc010-110">Pokud vaše kompilace obsahuje více než jeden typ s metodou [Main](../../programming-guide/main-and-command-args/index.md) , můžete určit, který typ obsahuje metodu **Main** , kterou chcete použít jako vstupní bod do programu.</span><span class="sxs-lookup"><span data-stu-id="fc010-110">If your compilation includes more than one type with a [Main](../../programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="fc010-111">Tato možnost je určena pro použití při kompilaci souboru. exe.</span><span class="sxs-lookup"><span data-stu-id="fc010-111">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="fc010-112">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fc010-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="fc010-113">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="fc010-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="fc010-114">Klikněte na stránku vlastností **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="fc010-114">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="fc010-115">Upravte vlastnost **objektu po spuštění** .</span><span class="sxs-lookup"><span data-stu-id="fc010-115">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="fc010-116">Chcete-li nastavit tuto možnost kompilátoru programově, přečtěte si téma <xref:VSLangProj80.ProjectProperties3.StartupObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="fc010-116">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
### <a name="to-set-this-compiler-option-by-manually-editing-the-csproj-file"></a><span data-ttu-id="fc010-117">Nastavení této možnosti kompilátoru ruční úpravou souboru. csproj</span><span class="sxs-lookup"><span data-stu-id="fc010-117">To set this compiler option by manually editing the .csproj file</span></span>
  
<span data-ttu-id="fc010-118">Tuto možnost můžete nastavit úpravou souboru. csproj a přidáním prvku `StartupObject` do `PropertyGroup` oddílu.</span><span class="sxs-lookup"><span data-stu-id="fc010-118">You can set this option by editing the .csproj file and adding an element `StartupObject` inside the `PropertyGroup` section.</span></span> <span data-ttu-id="fc010-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="fc010-119">For example:</span></span>

```
  <PropertyGroup>
    ...
    <StartupObject>MyApplication.Core.Program</StartupObject>
  </PropertyGroup>
```

## <a name="example"></a><span data-ttu-id="fc010-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="fc010-120">Example</span></span>  
 <span data-ttu-id="fc010-121">Zkompiluje `t2.cs` a `t3.cs` určí, že metoda **Main** bude nalezena v `Test2` :</span><span class="sxs-lookup"><span data-stu-id="fc010-121">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc010-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc010-122">See also</span></span>

- [<span data-ttu-id="fc010-123">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="fc010-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="fc010-124">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="fc010-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

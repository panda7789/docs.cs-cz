---
title: -main (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 6c842abc1423e7ee0d98b71392e02410c6cf9172
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602734"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="100a7-102">-main (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="100a7-102">-main (C# Compiler Options)</span></span>
<span data-ttu-id="100a7-103">Tato možnost určuje třídu, která obsahuje vstupní bod do programu, pokud více než jedna třída obsahuje **Main** metoda.</span><span class="sxs-lookup"><span data-stu-id="100a7-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="100a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="100a7-104">Syntax</span></span>  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="100a7-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="100a7-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="100a7-106">Typ, který obsahuje **Main** metoda.</span><span class="sxs-lookup"><span data-stu-id="100a7-106">The type that contains the **Main** method.</span></span>  
 <span data-ttu-id="100a7-107">Uvedený název třídy musí být plně kvalifikovaný; musí obsahovat celý obor názvů obsahující třídu, následovaný názvem třídy.</span><span class="sxs-lookup"><span data-stu-id="100a7-107">The provided class name must be fully qualified; it must include the full namespace containing the class, followed by the class name.</span></span> <span data-ttu-id="100a7-108">Například pokud `Main` je metoda umístěna `Program` uvnitř `MyApplication.Core` třídy v oboru názvů, `-main:MyApplication.Core.Program`musí být možnost kompilátoru .</span><span class="sxs-lookup"><span data-stu-id="100a7-108">For example, when the `Main` method is located inside the `Program` class in the `MyApplication.Core` namespace, the compiler option has to be `-main:MyApplication.Core.Program`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="100a7-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="100a7-109">Remarks</span></span>  
 <span data-ttu-id="100a7-110">Pokud kompilace obsahuje více než jeden typ s [Main](../../programming-guide/main-and-command-args/index.md) metoda, můžete určit, který typ obsahuje **Main** metoda, která chcete použít jako vstupní bod do programu.</span><span class="sxs-lookup"><span data-stu-id="100a7-110">If your compilation includes more than one type with a [Main](../../programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="100a7-111">Tato možnost je pro použití při kompilaci souboru EXE.</span><span class="sxs-lookup"><span data-stu-id="100a7-111">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="100a7-112">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="100a7-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="100a7-113">Otevřete stránku **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="100a7-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="100a7-114">Klikněte na stránku vlastností **Aplikace.**</span><span class="sxs-lookup"><span data-stu-id="100a7-114">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="100a7-115">Upravte vlastnost **Pospuštění objektu.**</span><span class="sxs-lookup"><span data-stu-id="100a7-115">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="100a7-116">Chcete-li tuto možnost kompilátoru nastavit programově, přečtěte si téma <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="100a7-116">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="100a7-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="100a7-117">Example</span></span>  
 <span data-ttu-id="100a7-118">Zkompilovat `t2.cs` a `t3.cs`, s uvedením, že **Main** metoda bude nalezena v `Test2`:</span><span class="sxs-lookup"><span data-stu-id="100a7-118">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="100a7-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="100a7-119">See also</span></span>

- [<span data-ttu-id="100a7-120">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="100a7-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="100a7-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="100a7-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

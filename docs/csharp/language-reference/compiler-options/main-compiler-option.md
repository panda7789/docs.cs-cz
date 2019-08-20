---
title: -Main (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 6c842abc1423e7ee0d98b71392e02410c6cf9172
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602734"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="3306e-102">-Main (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="3306e-102">-main (C# Compiler Options)</span></span>
<span data-ttu-id="3306e-103">Tato možnost určuje třídu, která obsahuje vstupní bod pro program, pokud více než jedna třída obsahuje metodu **Main** .</span><span class="sxs-lookup"><span data-stu-id="3306e-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3306e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3306e-104">Syntax</span></span>  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="3306e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3306e-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="3306e-106">Typ, který obsahuje metodu **Main** .</span><span class="sxs-lookup"><span data-stu-id="3306e-106">The type that contains the **Main** method.</span></span>  
 <span data-ttu-id="3306e-107">Poskytnutý název třídy musí být plně kvalifikovaný; musí zahrnovat úplný obor názvů obsahující třídu následovaný názvem třídy.</span><span class="sxs-lookup"><span data-stu-id="3306e-107">The provided class name must be fully qualified; it must include the full namespace containing the class, followed by the class name.</span></span> <span data-ttu-id="3306e-108">Například pokud `Main` je metoda umístěna `Program` uvnitř třídy v `MyApplication.Core` oboru názvů, musí být `-main:MyApplication.Core.Program`možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="3306e-108">For example, when the `Main` method is located inside the `Program` class in the `MyApplication.Core` namespace, the compiler option has to be `-main:MyApplication.Core.Program`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="3306e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3306e-109">Remarks</span></span>  
 <span data-ttu-id="3306e-110">Pokud vaše kompilace obsahuje více než jeden typ s metodou [Main](../../programming-guide/main-and-command-args/index.md) , můžete určit, který typ obsahuje metodu **Main** , kterou chcete použít jako vstupní bod do programu.</span><span class="sxs-lookup"><span data-stu-id="3306e-110">If your compilation includes more than one type with a [Main](../../programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="3306e-111">Tato možnost je určena pro použití při kompilaci souboru. exe.</span><span class="sxs-lookup"><span data-stu-id="3306e-111">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3306e-112">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3306e-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="3306e-113">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="3306e-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="3306e-114">Klikněte na stránku vlastností **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="3306e-114">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="3306e-115">Upravte vlastnost **objektu po spuštění** .</span><span class="sxs-lookup"><span data-stu-id="3306e-115">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="3306e-116">Chcete-li nastavit tuto možnost kompilátoru programově <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>, přečtěte si téma.</span><span class="sxs-lookup"><span data-stu-id="3306e-116">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3306e-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="3306e-117">Example</span></span>  
 <span data-ttu-id="3306e-118">Zkompiluje `t2.cs` `Test2`a `t3.cs`určí, že metoda **Main** bude nalezena v:</span><span class="sxs-lookup"><span data-stu-id="3306e-118">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="3306e-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3306e-119">See also</span></span>

- [<span data-ttu-id="3306e-120">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3306e-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="3306e-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="3306e-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

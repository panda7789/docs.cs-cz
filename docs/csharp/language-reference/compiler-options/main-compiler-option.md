---
title: -main (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 2f3c9daf98bfe77ea9462c8126f7a8368016875c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468862"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="43eba-102">-main (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="43eba-102">-main (C# Compiler Options)</span></span>
<span data-ttu-id="43eba-103">Tato možnost určuje třídu, která obsahuje položku, přejděte na program, pokud obsahuje více než jedné třídy **hlavní** metody.</span><span class="sxs-lookup"><span data-stu-id="43eba-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43eba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43eba-104">Syntax</span></span>  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="43eba-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="43eba-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="43eba-106">Typ, který obsahuje **hlavní** metody.</span><span class="sxs-lookup"><span data-stu-id="43eba-106">The type that contains the **Main** method.</span></span>  
 <span data-ttu-id="43eba-107">Název zadaný třídy musí být plně kvalifikovaný; musí obsahovat úplný obor názvů obsahující třídu, za nímž následuje název třídy.</span><span class="sxs-lookup"><span data-stu-id="43eba-107">The provided class name must be fully qualified; it must include the full namespace containing the class, followed by the class name.</span></span> <span data-ttu-id="43eba-108">Například, když `Main` metoda se nachází uvnitř `Program` třídy v `MyApplication.Core` obor názvů, parametrem kompilátoru musí být `-main:MyApplication.Core.Program`.</span><span class="sxs-lookup"><span data-stu-id="43eba-108">For example, when the `Main` method is located inside the `Program` class in the `MyApplication.Core` namespace, the compiler option has to be `-main:MyApplication.Core.Program`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="43eba-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43eba-109">Remarks</span></span>  
 <span data-ttu-id="43eba-110">Pokud kompilace obsahuje více než jeden typ [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metodu, můžete určit, jaký typ obsahuje **hlavní** metodu, která chcete použít jako vstupní bod do programu.</span><span class="sxs-lookup"><span data-stu-id="43eba-110">If your compilation includes more than one type with a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="43eba-111">Tato možnost je pro použití při kompilaci souboru .exe.</span><span class="sxs-lookup"><span data-stu-id="43eba-111">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="43eba-112">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="43eba-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="43eba-113">Otevřete v projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="43eba-113">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="43eba-114">Klikněte na tlačítko **aplikace** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="43eba-114">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="43eba-115">Upravit **spouštěcí objekt** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="43eba-115">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="43eba-116">Programové nastavení tohoto parametru kompilátoru, naleznete v tématu <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="43eba-116">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43eba-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="43eba-117">Example</span></span>  
 <span data-ttu-id="43eba-118">Kompilace `t2.cs` a `t3.cs`, určující, který **hlavní** metoda najdete v `Test2`:</span><span class="sxs-lookup"><span data-stu-id="43eba-118">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="43eba-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="43eba-119">See Also</span></span>

- [<span data-ttu-id="43eba-120">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="43eba-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="43eba-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="43eba-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

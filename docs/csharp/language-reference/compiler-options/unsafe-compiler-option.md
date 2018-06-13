---
title: -unsafe (možnosti kompilátoru C#)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: e308cae4a46efd53a77baf5b175e9069b5371fa4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214036"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="b9abf-102">-unsafe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="b9abf-102">-unsafe (C# Compiler Options)</span></span>
<span data-ttu-id="b9abf-103">**-Unsafe** – možnost kompilátoru umožňuje kód, který používá [unsafe](../../../csharp/language-reference/keywords/unsafe.md) – klíčové slovo zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="b9abf-103">The **-unsafe** compiler option allows code that uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9abf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9abf-104">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="b9abf-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9abf-105">Remarks</span></span>  
 <span data-ttu-id="b9abf-106">Další informace o nebezpečného kódu najdete v tématu [nezabezpečený kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="b9abf-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="b9abf-107">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b9abf-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="b9abf-108">Otevření projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="b9abf-108">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="b9abf-109">Klikněte **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="b9abf-109">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="b9abf-110">Vyberte **povolit nezabezpečený kód** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="b9abf-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="b9abf-111">Chcete-li přidat tuto možnost v souboru csproj</span><span class="sxs-lookup"><span data-stu-id="b9abf-111">To add this option in a csproj file</span></span>

<span data-ttu-id="b9abf-112">Otevřete soubor .csproj pro projekt a přidejte následující prvky:</span><span class="sxs-lookup"><span data-stu-id="b9abf-112">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="b9abf-113">Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span><span class="sxs-lookup"><span data-stu-id="b9abf-113">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9abf-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="b9abf-114">Example</span></span>  
 <span data-ttu-id="b9abf-115">Kompilace `in.cs` pro nebezpečný režim:</span><span class="sxs-lookup"><span data-stu-id="b9abf-115">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9abf-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9abf-116">See Also</span></span>  
 [<span data-ttu-id="b9abf-117">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b9abf-117">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="b9abf-118">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="b9abf-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

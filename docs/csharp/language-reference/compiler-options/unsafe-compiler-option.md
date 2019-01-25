---
title: -unsafe (možnosti kompilátoru C#)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 4a8f7d099b2cd3c1b4331c87f853b617fef505ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726530"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="3b8e4-102">-unsafe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="3b8e4-102">-unsafe (C# Compiler Options)</span></span>
<span data-ttu-id="3b8e4-103">**-Unsafe** – možnost kompilátoru umožňuje kód, který se používá [nebezpečné](../../../csharp/language-reference/keywords/unsafe.md) ke kompilaci klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="3b8e4-103">The **-unsafe** compiler option allows code that uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b8e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b8e4-104">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="3b8e4-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3b8e4-105">Remarks</span></span>  
 <span data-ttu-id="3b8e4-106">Další informace o nebezpečný kód, naleznete v tématu [nezabezpečený kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="3b8e4-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3b8e4-107">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b8e4-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="3b8e4-108">Otevřete v projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="3b8e4-108">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="3b8e4-109">Klikněte na tlačítko **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="3b8e4-109">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="3b8e4-110">Vyberte **povolit nezabezpečený kód** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="3b8e4-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="3b8e4-111">Chcete-li přidat tuto možnost v souboru csproj</span><span class="sxs-lookup"><span data-stu-id="3b8e4-111">To add this option in a csproj file</span></span>

<span data-ttu-id="3b8e4-112">Otevřete soubor .csproj projektu a přidejte následující prvky:</span><span class="sxs-lookup"><span data-stu-id="3b8e4-112">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="3b8e4-113">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span><span class="sxs-lookup"><span data-stu-id="3b8e4-113">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b8e4-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b8e4-114">Example</span></span>  
 <span data-ttu-id="3b8e4-115">Kompilace `in.cs` pro nezabezpečeného režimu:</span><span class="sxs-lookup"><span data-stu-id="3b8e4-115">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b8e4-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b8e4-116">See also</span></span>

- [<span data-ttu-id="3b8e4-117">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3b8e4-117">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="3b8e4-118">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="3b8e4-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

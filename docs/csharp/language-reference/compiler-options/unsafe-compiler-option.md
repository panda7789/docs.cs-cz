---
title: -unsafe (Možnosti kompilátoru Jazyka C#)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 146299fda103567b111c66400c17edf36addd843
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "65877996"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="e4767-102">-unsafe (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e4767-102">-unsafe (C# Compiler Options)</span></span>

<span data-ttu-id="e4767-103">Možnost **-unsafe** kompilátor umožňuje kód, který používá [nebezpečné](../keywords/unsafe.md) klíčové slovo ke kompilaci.</span><span class="sxs-lookup"><span data-stu-id="e4767-103">The **-unsafe** compiler option allows code that uses the [unsafe](../keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4767-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4767-104">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="e4767-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4767-105">Remarks</span></span>

<span data-ttu-id="e4767-106">Další informace o nebezpečném kódu naleznete v [tématu Nebezpečný kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="e4767-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="e4767-107">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e4767-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="e4767-108">Otevřete stránku **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="e4767-108">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="e4767-109">Klikněte na stránku vlastností **Sestavení.**</span><span class="sxs-lookup"><span data-stu-id="e4767-109">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="e4767-110">Zaškrtněte **políčko Povolit nebezpečný kód.**</span><span class="sxs-lookup"><span data-stu-id="e4767-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="e4767-111">Přidání této možnosti do souboru csproj</span><span class="sxs-lookup"><span data-stu-id="e4767-111">To add this option in a csproj file</span></span>

<span data-ttu-id="e4767-112">Otevřete soubor CSProJ pro projekt a přidejte následující prvky:</span><span class="sxs-lookup"><span data-stu-id="e4767-112">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="e4767-113">Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>kompilátoru programově, naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="e4767-113">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4767-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4767-114">Example</span></span>

<span data-ttu-id="e4767-115">Kompilace `in.cs` pro nebezpečný režim:</span><span class="sxs-lookup"><span data-stu-id="e4767-115">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4767-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4767-116">See also</span></span>

- [<span data-ttu-id="e4767-117">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e4767-117">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="e4767-118">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="e4767-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

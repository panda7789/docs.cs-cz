---
description: -unsafe (možnosti kompilátoru C#)
title: -unsafe (možnosti kompilátoru C#)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 0f6d94dd25a020d96430746c4b5e7aefd0f679da
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140838"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="c2601-103">-unsafe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="c2601-103">-unsafe (C# Compiler Options)</span></span>

<span data-ttu-id="c2601-104">Možnost kompilátoru **-unsafe** umožňuje kód, který používá klíčové slovo [unsafe](../keywords/unsafe.md) ke kompilaci.</span><span class="sxs-lookup"><span data-stu-id="c2601-104">The **-unsafe** compiler option allows code that uses the [unsafe](../keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2601-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c2601-105">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="c2601-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2601-106">Remarks</span></span>

<span data-ttu-id="c2601-107">Další informace o nebezpečném kódu naleznete v tématu [nezabezpečený kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="c2601-107">For more information about unsafe code, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c2601-108">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c2601-108">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="c2601-109">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="c2601-109">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="c2601-110">Klikněte na stránku vlastností **Build (sestavit** ).</span><span class="sxs-lookup"><span data-stu-id="c2601-110">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="c2601-111">Zaškrtněte políčko **Povolení nezabezpečeného kódu** .</span><span class="sxs-lookup"><span data-stu-id="c2601-111">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="c2601-112">Přidání této možnosti do souboru csproj</span><span class="sxs-lookup"><span data-stu-id="c2601-112">To add this option in a csproj file</span></span>

<span data-ttu-id="c2601-113">Otevřete soubor. csproj pro projekt a přidejte následující prvky:</span><span class="sxs-lookup"><span data-stu-id="c2601-113">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="c2601-114">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A> .</span><span class="sxs-lookup"><span data-stu-id="c2601-114">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2601-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2601-115">Example</span></span>

<span data-ttu-id="c2601-116">Kompilovat `in.cs` pro nezabezpečený režim:</span><span class="sxs-lookup"><span data-stu-id="c2601-116">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2601-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2601-117">See also</span></span>

- [<span data-ttu-id="c2601-118">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="c2601-118">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="c2601-119">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="c2601-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

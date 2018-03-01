---
title: "-unsafe (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.assetid: fdb77ed9-da03-45bd-bb7f-250704da1bcc
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b253a9ddafead823480f9893e809f17b6c22a179
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="cec4f-102">-unsafe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="cec4f-102">-unsafe (C# Compiler Options)</span></span>
<span data-ttu-id="cec4f-103">**-Unsafe** – možnost kompilátoru umožňuje kód, který používá [unsafe](../../../csharp/language-reference/keywords/unsafe.md) – klíčové slovo zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="cec4f-103">The **-unsafe** compiler option allows code that uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cec4f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cec4f-104">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="cec4f-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cec4f-105">Remarks</span></span>  
 <span data-ttu-id="cec4f-106">Další informace o nebezpečného kódu najdete v tématu [nezabezpečený kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="cec4f-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="cec4f-107">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cec4f-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="cec4f-108">Otevření projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="cec4f-108">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="cec4f-109">Klikněte **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="cec4f-109">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="cec4f-110">Vyberte **povolit nezabezpečený kód** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="cec4f-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
 <span data-ttu-id="cec4f-111">Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span><span class="sxs-lookup"><span data-stu-id="cec4f-111">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cec4f-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="cec4f-112">Example</span></span>  
 <span data-ttu-id="cec4f-113">Kompilace `in.cs` pro nebezpečný režim:</span><span class="sxs-lookup"><span data-stu-id="cec4f-113">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="cec4f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="cec4f-114">See Also</span></span>  
 [<span data-ttu-id="cec4f-115">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cec4f-115">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="cec4f-116">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="cec4f-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

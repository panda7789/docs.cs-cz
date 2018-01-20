---
title: "-win32res (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4c24da8bb745847612d882d00eff7f03dbc60475
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-win32res-c-compiler-options"></a><span data-ttu-id="1f39e-102">-win32res (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="1f39e-102">-win32res (C# Compiler Options)</span></span>
<span data-ttu-id="1f39e-103">**-Win32res** možnost vloží prostředek systému Win32 ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="1f39e-103">The **-win32res** option inserts a Win32 resource in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f39e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f39e-104">Syntax</span></span>  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="1f39e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1f39e-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="1f39e-106">Soubor prostředků, který chcete přidat do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="1f39e-106">The resource file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f39e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1f39e-107">Remarks</span></span>  
 <span data-ttu-id="1f39e-108">Zdrojového souboru Win32 může být vytvořen pomocí [kompilátor prostředků](../../language-reference/compiler-options/resource-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="1f39e-108">A Win32 resource file can be created with the [Resource Compiler](../../language-reference/compiler-options/resource-compiler-option.md).</span></span> <span data-ttu-id="1f39e-109">Nástroj Resource Compiler je vyvolán při kompilaci programu Visual C++; soubor .res je vytvořen ze souboru .rc.</span><span class="sxs-lookup"><span data-stu-id="1f39e-109">The Resource Compiler is invoked when you compile a Visual C++ program; a .res file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="1f39e-110">Win32 prostředků může obsahovat verzi nebo rastrový obrázek (ikona) informace, které pomohou identifikovat aplikace v Průzkumníkovi souborů.</span><span class="sxs-lookup"><span data-stu-id="1f39e-110">A Win32 resource can contain version or bitmap (icon) information that would help identify your application in the File Explorer.</span></span> <span data-ttu-id="1f39e-111">Pokud nezadáte **-win32res**, kompilátor vygeneruje informace o verzi na základě verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="1f39e-111">If you do not specify **-win32res**, the compiler will generate version information based on the assembly version.</span></span>  
  
 <span data-ttu-id="1f39e-112">V tématu [- linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (pro referenční dokumentace) nebo [– prostředek](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (pro připojení) souboru prostředků rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1f39e-112">See [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (to reference) or [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1f39e-113">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1f39e-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="1f39e-114">Otevření projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="1f39e-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="1f39e-115">Klikněte **aplikace** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="1f39e-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="1f39e-116">Klikněte na **souboru prostředků** tlačítko a zvolte soubor pomocí pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="1f39e-116">Click on the **Resource File** button and choose a file by using the combo box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f39e-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f39e-117">Example</span></span>  
 <span data-ttu-id="1f39e-118">Kompilace `in.cs` a připojte soubor prostředků Win32 `rf.res` k vytvoření `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="1f39e-118">Compile `in.cs` and attach a Win32 resource file `rf.res` to produce `in.exe`:</span></span>  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f39e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f39e-119">See Also</span></span>  
 [<span data-ttu-id="1f39e-120">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1f39e-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="1f39e-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="1f39e-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

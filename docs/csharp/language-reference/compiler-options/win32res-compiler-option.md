---
description: -win32res (možnosti kompilátoru C#)
title: -win32res (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
ms.openlocfilehash: c220c78a6d2c3109402a20f0de40fe9665d6c730
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140812"
---
# <a name="-win32res-c-compiler-options"></a><span data-ttu-id="a28d1-103">-win32res (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="a28d1-103">-win32res (C# Compiler Options)</span></span>
<span data-ttu-id="a28d1-104">Možnost **-win32res** vloží prostředek Win32 do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="a28d1-104">The **-win32res** option inserts a Win32 resource in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a28d1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a28d1-105">Syntax</span></span>  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="a28d1-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a28d1-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="a28d1-107">Soubor prostředků, který chcete přidat do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="a28d1-107">The resource file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a28d1-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a28d1-108">Remarks</span></span>  
 <span data-ttu-id="a28d1-109">Soubor prostředků Win32 se dá vytvořit s [kompilátorem prostředků](resource-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="a28d1-109">A Win32 resource file can be created with the [Resource Compiler](resource-compiler-option.md).</span></span> <span data-ttu-id="a28d1-110">Nástroj Resource Compiler je vyvolán při kompilaci programu Visual C++; soubor .res je vytvořen ze souboru .rc.</span><span class="sxs-lookup"><span data-stu-id="a28d1-110">The Resource Compiler is invoked when you compile a Visual C++ program; a .res file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="a28d1-111">Prostředek Win32 může obsahovat informace o verzi nebo bitmapě (ikony), které vám pomůžou identifikovat vaši aplikaci v Průzkumníkovi souborů.</span><span class="sxs-lookup"><span data-stu-id="a28d1-111">A Win32 resource can contain version or bitmap (icon) information that would help identify your application in the File Explorer.</span></span> <span data-ttu-id="a28d1-112">Pokud nezadáte **-win32res**, kompilátor vygeneruje informace o verzi na základě verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="a28d1-112">If you do not specify **-win32res**, the compiler will generate version information based on the assembly version.</span></span>  
  
 <span data-ttu-id="a28d1-113">Viz [– linkresource –](./linkresource-compiler-option.md) (odkazování) nebo [-Resource](./resource-compiler-option.md) (pro připojení) .NET Frameworkho souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="a28d1-113">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a28d1-114">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a28d1-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="a28d1-115">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="a28d1-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="a28d1-116">Klikněte na stránku vlastností **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="a28d1-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="a28d1-117">Klikněte na tlačítko **soubor prostředků** a vyberte soubor pomocí pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="a28d1-117">Click on the **Resource File** button and choose a file by using the combo box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a28d1-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="a28d1-118">Example</span></span>  
 <span data-ttu-id="a28d1-119">Zkompilujte `in.cs` a připojte soubor prostředků Win32 `rf.res` k vytvoření `in.exe` :</span><span class="sxs-lookup"><span data-stu-id="a28d1-119">Compile `in.cs` and attach a Win32 resource file `rf.res` to produce `in.exe`:</span></span>  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="a28d1-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a28d1-120">See also</span></span>

- [<span data-ttu-id="a28d1-121">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="a28d1-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="a28d1-122">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="a28d1-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

---
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
ms.openlocfilehash: 3bb1614fcf28c62a9000c9b96af2f046f329fb1e
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794374"
---
# <a name="-win32res-c-compiler-options"></a><span data-ttu-id="611cb-102">-win32res (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="611cb-102">-win32res (C# Compiler Options)</span></span>
<span data-ttu-id="611cb-103">Možnost **-win32res** vloží prostředek Win32 do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="611cb-103">The **-win32res** option inserts a Win32 resource in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="611cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="611cb-104">Syntax</span></span>  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="611cb-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="611cb-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="611cb-106">Soubor prostředků, který chcete přidat do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="611cb-106">The resource file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="611cb-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="611cb-107">Remarks</span></span>  
 <span data-ttu-id="611cb-108">Soubor prostředků Win32 se dá vytvořit s [kompilátorem prostředků](resource-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="611cb-108">A Win32 resource file can be created with the [Resource Compiler](resource-compiler-option.md).</span></span> <span data-ttu-id="611cb-109">Nástroj Resource Compiler je vyvolán při kompilaci programu Visual C++; soubor .res je vytvořen ze souboru .rc.</span><span class="sxs-lookup"><span data-stu-id="611cb-109">The Resource Compiler is invoked when you compile a Visual C++ program; a .res file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="611cb-110">Prostředek Win32 může obsahovat informace o verzi nebo bitmapě (ikony), které vám pomůžou identifikovat vaši aplikaci v Průzkumníkovi souborů.</span><span class="sxs-lookup"><span data-stu-id="611cb-110">A Win32 resource can contain version or bitmap (icon) information that would help identify your application in the File Explorer.</span></span> <span data-ttu-id="611cb-111">Pokud nezadáte **-win32res**, kompilátor vygeneruje informace o verzi na základě verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="611cb-111">If you do not specify **-win32res**, the compiler will generate version information based on the assembly version.</span></span>  
  
 <span data-ttu-id="611cb-112">Viz [– linkresource –](./linkresource-compiler-option.md) (odkazování) nebo [-Resource](./resource-compiler-option.md) (pro připojení) .NET Frameworkho souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="611cb-112">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="611cb-113">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="611cb-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="611cb-114">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="611cb-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="611cb-115">Klikněte na stránku vlastností **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="611cb-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="611cb-116">Klikněte na tlačítko **soubor prostředků** a vyberte soubor pomocí pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="611cb-116">Click on the **Resource File** button and choose a file by using the combo box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="611cb-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="611cb-117">Example</span></span>  
 <span data-ttu-id="611cb-118">Zkompilujte `in.cs` a připojte soubor `rf.res` prostředků Win32 k vytvoření `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="611cb-118">Compile `in.cs` and attach a Win32 resource file `rf.res` to produce `in.exe`:</span></span>  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="611cb-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="611cb-119">See also</span></span>

- [<span data-ttu-id="611cb-120">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="611cb-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="611cb-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="611cb-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

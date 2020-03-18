---
title: -win32res (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
ms.openlocfilehash: 39f02c4c2e060c4be40002a2f48b0da31004a9ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606194"
---
# <a name="-win32res-c-compiler-options"></a><span data-ttu-id="46c0e-102">-win32res (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="46c0e-102">-win32res (C# Compiler Options)</span></span>
<span data-ttu-id="46c0e-103">Možnost **-win32res** vloží prostředek Win32 do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="46c0e-103">The **-win32res** option inserts a Win32 resource in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46c0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46c0e-104">Syntax</span></span>  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="46c0e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="46c0e-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="46c0e-106">Soubor prostředků, který chcete přidat do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="46c0e-106">The resource file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46c0e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46c0e-107">Remarks</span></span>  
 <span data-ttu-id="46c0e-108">Soubor prostředků Win32 lze vytvořit pomocí [kompilátoru prostředků](../../language-reference/compiler-options/resource-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="46c0e-108">A Win32 resource file can be created with the [Resource Compiler](../../language-reference/compiler-options/resource-compiler-option.md).</span></span> <span data-ttu-id="46c0e-109">Nástroj Resource Compiler je vyvolán při kompilaci programu Visual C++; soubor .res je vytvořen ze souboru .rc.</span><span class="sxs-lookup"><span data-stu-id="46c0e-109">The Resource Compiler is invoked when you compile a Visual C++ program; a .res file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="46c0e-110">Prostředek win32 může obsahovat informace o verzi nebo rastrové mapě (ikona), které by pomohly identifikovat vaši aplikaci v Průzkumníku souborů.</span><span class="sxs-lookup"><span data-stu-id="46c0e-110">A Win32 resource can contain version or bitmap (icon) information that would help identify your application in the File Explorer.</span></span> <span data-ttu-id="46c0e-111">Pokud nezadáte **-win32res**, kompilátor vygeneruje informace o verzi na základě verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="46c0e-111">If you do not specify **-win32res**, the compiler will generate version information based on the assembly version.</span></span>  
  
 <span data-ttu-id="46c0e-112">Viz [-linkresource](./linkresource-compiler-option.md) (odkaz) nebo [-resource](./resource-compiler-option.md) (připojit) soubor prostředků rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="46c0e-112">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="46c0e-113">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="46c0e-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="46c0e-114">Otevřete stránku **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="46c0e-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="46c0e-115">Klikněte na stránku vlastností **Aplikace.**</span><span class="sxs-lookup"><span data-stu-id="46c0e-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="46c0e-116">Klikněte na tlačítko **Soubor prostředků** a zvolte soubor pomocí pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="46c0e-116">Click on the **Resource File** button and choose a file by using the combo box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46c0e-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="46c0e-117">Example</span></span>  
 <span data-ttu-id="46c0e-118">Kompilace `in.cs` a připojení souboru `rf.res` prostředků `in.exe`Win32 k vytvoření :</span><span class="sxs-lookup"><span data-stu-id="46c0e-118">Compile `in.cs` and attach a Win32 resource file `rf.res` to produce `in.exe`:</span></span>  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="46c0e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="46c0e-119">See also</span></span>

- [<span data-ttu-id="46c0e-120">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="46c0e-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="46c0e-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="46c0e-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

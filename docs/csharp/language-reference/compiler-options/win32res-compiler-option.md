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
ms.openlocfilehash: 522d80ce6be277c048fa62cc1a7b077d8bb08bfe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544699"
---
# <a name="-win32res-c-compiler-options"></a><span data-ttu-id="0ec59-102">-win32res (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="0ec59-102">-win32res (C# Compiler Options)</span></span>
<span data-ttu-id="0ec59-103">**-Win32res** možnost vloží prostředek systému Win32 do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="0ec59-103">The **-win32res** option inserts a Win32 resource in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ec59-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ec59-104">Syntax</span></span>  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="0ec59-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0ec59-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="0ec59-106">Soubor prostředků, kterou chcete přidat do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="0ec59-106">The resource file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ec59-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ec59-107">Remarks</span></span>  
 <span data-ttu-id="0ec59-108">Soubor prostředků Win32 lze vytvořit pomocí [Resource Compiler](../../language-reference/compiler-options/resource-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="0ec59-108">A Win32 resource file can be created with the [Resource Compiler](../../language-reference/compiler-options/resource-compiler-option.md).</span></span> <span data-ttu-id="0ec59-109">Nástroj Resource Compiler je vyvolán při kompilaci programu Visual C++; soubor .res je vytvořen ze souboru .rc.</span><span class="sxs-lookup"><span data-stu-id="0ec59-109">The Resource Compiler is invoked when you compile a Visual C++ program; a .res file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="0ec59-110">Prostředek systému Win32 mohou obsahovat verzi nebo rastrový obrázek (ikona) informace, které by pomohl identifikovat aplikace v Průzkumníkovi souborů.</span><span class="sxs-lookup"><span data-stu-id="0ec59-110">A Win32 resource can contain version or bitmap (icon) information that would help identify your application in the File Explorer.</span></span> <span data-ttu-id="0ec59-111">Pokud nezadáte **-win32res**, bude kompilátor generovat informace o verzi na základě verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ec59-111">If you do not specify **-win32res**, the compiler will generate version information based on the assembly version.</span></span>  
  
 <span data-ttu-id="0ec59-112">Zobrazit [- linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (na odkaz) nebo [– prostředků](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (pro připojení) soubor prostředků rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0ec59-112">See [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (to reference) or [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="0ec59-113">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0ec59-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="0ec59-114">Otevřete v projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="0ec59-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="0ec59-115">Klikněte na tlačítko **aplikace** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="0ec59-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="0ec59-116">Klikněte na **soubor prostředků** tlačítko a vyberte soubor s použitím pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="0ec59-116">Click on the **Resource File** button and choose a file by using the combo box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ec59-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="0ec59-117">Example</span></span>  
 <span data-ttu-id="0ec59-118">Kompilace `in.cs` a připojte soubor prostředků Win32 `rf.res` k vytvoření `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="0ec59-118">Compile `in.cs` and attach a Win32 resource file `rf.res` to produce `in.exe`:</span></span>  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ec59-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ec59-119">See also</span></span>

- [<span data-ttu-id="0ec59-120">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0ec59-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="0ec59-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="0ec59-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

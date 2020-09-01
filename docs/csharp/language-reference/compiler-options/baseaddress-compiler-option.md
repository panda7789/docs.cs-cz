---
description: -BaseAddress (možnosti kompilátoru C#)
title: -BaseAddress (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: 42b1891c29457745689542a4c9e0482ec5e918fa
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126005"
---
# <a name="-baseaddress-c-compiler-options"></a><span data-ttu-id="49a1e-103">-BaseAddress (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="49a1e-103">-baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="49a1e-104">Možnost **-BaseAddress** umožňuje zadat upřednostňovanou základní adresu, na které se má načíst knihovna DLL.</span><span class="sxs-lookup"><span data-stu-id="49a1e-104">The **-baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="49a1e-105">Další informace o tom, kdy a proč použít tuto možnost, najdete v tématu [blog Larry Osterman](https://docs.microsoft.com/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span><span class="sxs-lookup"><span data-stu-id="49a1e-105">For more information about when and why to use this option, see [Larry Osterman's WebLog](https://docs.microsoft.com/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49a1e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49a1e-106">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="49a1e-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="49a1e-107">Arguments</span></span>  
 `address`  
 <span data-ttu-id="49a1e-108">Základní adresa knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="49a1e-108">The base address for the DLL.</span></span> <span data-ttu-id="49a1e-109">Tuto adresu lze zadat jako desítkové, šestnáctkové nebo osmičkové číslo.</span><span class="sxs-lookup"><span data-stu-id="49a1e-109">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49a1e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="49a1e-110">Remarks</span></span>  
 <span data-ttu-id="49a1e-111">Výchozí základní adresa pro knihovnu DLL je nastavena .NET Framework modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="49a1e-111">The default base address for a DLL is set by the .NET Framework common language runtime.</span></span>  
  
 <span data-ttu-id="49a1e-112">Uvědomte si, že slovo v této adrese bude zaokrouhleno.</span><span class="sxs-lookup"><span data-stu-id="49a1e-112">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="49a1e-113">Pokud například zadáte 0x11110001, bude se zaokrouhlit na 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="49a1e-113">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="49a1e-114">Chcete-li dokončit proces podepisování pro knihovnu DLL, použijte SN.EXE s možností-R.</span><span class="sxs-lookup"><span data-stu-id="49a1e-114">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="49a1e-115">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="49a1e-115">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="49a1e-116">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="49a1e-116">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="49a1e-117">Klikněte na stránku vlastností **Build (sestavit** ).</span><span class="sxs-lookup"><span data-stu-id="49a1e-117">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="49a1e-118">Klikněte na tlačítko **Upřesnit** .</span><span class="sxs-lookup"><span data-stu-id="49a1e-118">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="49a1e-119">Upravte vlastnost **základní adresy knihovny DLL** .</span><span class="sxs-lookup"><span data-stu-id="49a1e-119">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="49a1e-120">Chcete-li nastavit tuto možnost kompilátoru programově, přečtěte si téma <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A> .</span><span class="sxs-lookup"><span data-stu-id="49a1e-120">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49a1e-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="49a1e-121">See also</span></span>

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [<span data-ttu-id="49a1e-122">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="49a1e-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="49a1e-123">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="49a1e-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

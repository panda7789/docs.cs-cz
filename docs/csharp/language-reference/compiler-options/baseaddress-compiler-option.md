---
title: -BaseAddress (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: e96ab3ece6edc36c913a8efc0097ff9c4a1e3c22
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69607028"
---
# <a name="-baseaddress-c-compiler-options"></a><span data-ttu-id="b11fb-102">-BaseAddress (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="b11fb-102">-baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="b11fb-103">Možnost **-BaseAddress** umožňuje zadat upřednostňovanou základní adresu, na které se má načíst knihovna DLL.</span><span class="sxs-lookup"><span data-stu-id="b11fb-103">The **-baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="b11fb-104">Další informace o tom, kdy a proč použít tuto možnost, najdete v tématu [blog Larry Osterman](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).</span><span class="sxs-lookup"><span data-stu-id="b11fb-104">For more information about when and why to use this option, see [Larry Osterman's WebLog](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b11fb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b11fb-105">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="b11fb-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="b11fb-106">Arguments</span></span>  
 `address`  
 <span data-ttu-id="b11fb-107">Základní adresa knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="b11fb-107">The base address for the DLL.</span></span> <span data-ttu-id="b11fb-108">Tuto adresu lze zadat jako desítkové, šestnáctkové nebo osmičkové číslo.</span><span class="sxs-lookup"><span data-stu-id="b11fb-108">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b11fb-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b11fb-109">Remarks</span></span>  
 <span data-ttu-id="b11fb-110">Výchozí základní adresa pro knihovnu DLL je nastavena .NET Framework modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="b11fb-110">The default base address for a DLL is set by the .NET Framework common language runtime.</span></span>  
  
 <span data-ttu-id="b11fb-111">Uvědomte si, že slovo v této adrese bude zaokrouhleno.</span><span class="sxs-lookup"><span data-stu-id="b11fb-111">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="b11fb-112">Pokud například zadáte 0x11110001, bude se zaokrouhlit na 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="b11fb-112">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="b11fb-113">Chcete-li dokončit proces podepisování pro knihovnu DLL, použijte SN. EXE s parametrem-R.</span><span class="sxs-lookup"><span data-stu-id="b11fb-113">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="b11fb-114">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b11fb-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="b11fb-115">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="b11fb-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="b11fb-116">Klikněte na stránku vlastností **Build (sestavit** ).</span><span class="sxs-lookup"><span data-stu-id="b11fb-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="b11fb-117">Klikněte na tlačítko **Upřesnit** .</span><span class="sxs-lookup"><span data-stu-id="b11fb-117">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="b11fb-118">Upravte vlastnost **základní adresy knihovny DLL** .</span><span class="sxs-lookup"><span data-stu-id="b11fb-118">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="b11fb-119">Chcete-li nastavit tuto možnost kompilátoru programově <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>, přečtěte si téma.</span><span class="sxs-lookup"><span data-stu-id="b11fb-119">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b11fb-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b11fb-120">See also</span></span>

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b11fb-121">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b11fb-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="b11fb-122">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="b11fb-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

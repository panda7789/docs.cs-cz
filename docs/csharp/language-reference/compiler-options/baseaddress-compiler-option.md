---
title: -baseaddress (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: 3759067731902ba4f460ff850fb5e81f2e544e99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215229"
---
# <a name="-baseaddress-c-compiler-options"></a><span data-ttu-id="76ec5-102">-baseaddress (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="76ec5-102">-baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="76ec5-103">**- Baseaddress** možnost umožňuje zadat upřednostňovaná základní adresa, na které se mají načíst knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="76ec5-103">The **-baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="76ec5-104">Další informace o kdy a proč použít tuto možnost najdete v tématu [Larry Osterman-blog](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).</span><span class="sxs-lookup"><span data-stu-id="76ec5-104">For more information about when and why to use this option, see [Larry Osterman's WebLog](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76ec5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76ec5-105">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="76ec5-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="76ec5-106">Arguments</span></span>  
 `address`  
 <span data-ttu-id="76ec5-107">Základní adresa pro knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="76ec5-107">The base address for the DLL.</span></span> <span data-ttu-id="76ec5-108">Tuto adresu můžete zadat hodnotu decimal, šestnáctkovém nebo osmičkové číslo.</span><span class="sxs-lookup"><span data-stu-id="76ec5-108">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76ec5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="76ec5-109">Remarks</span></span>  
 <span data-ttu-id="76ec5-110">Výchozí základní adresy knihovny DLL je nastavena pomocí modulu CLR rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="76ec5-110">The default base address for a DLL is set by the .NET Framework common language runtime.</span></span>  
  
 <span data-ttu-id="76ec5-111">Mějte na paměti se zaokrouhlí na slovo nižší pořadí v tuto adresu.</span><span class="sxs-lookup"><span data-stu-id="76ec5-111">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="76ec5-112">Například pokud zadáte 0x11110001, ji budou zaokrouhlí 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="76ec5-112">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="76ec5-113">Chcete-li dokončit proces podepisování pro knihovny DLL, použijte SN. EXE s parametrem -R.</span><span class="sxs-lookup"><span data-stu-id="76ec5-113">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="76ec5-114">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="76ec5-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="76ec5-115">Otevření projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="76ec5-115">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="76ec5-116">Klikněte **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="76ec5-116">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="76ec5-117">Klikněte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="76ec5-117">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="76ec5-118">Změnit **základní adresa knihovny DLL** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="76ec5-118">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="76ec5-119">Pokud chcete nastavit tuto možnost kompilátoru prostřednictvím kódu programu, najdete v části <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span><span class="sxs-lookup"><span data-stu-id="76ec5-119">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76ec5-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="76ec5-120">See Also</span></span>  
 <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="76ec5-121">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="76ec5-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="76ec5-122">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="76ec5-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

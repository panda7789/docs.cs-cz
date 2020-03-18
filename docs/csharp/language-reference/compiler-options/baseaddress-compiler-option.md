---
title: -baseaddress (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: f138f445b8a335c7505e25b34f560c4da40ab2dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937215"
---
# <a name="-baseaddress-c-compiler-options"></a><span data-ttu-id="54d16-102">-baseaddress (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="54d16-102">-baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="54d16-103">Možnost **-baseaddress** umožňuje zadat upřednostňovanou základní adresu, na které chcete načíst dll.</span><span class="sxs-lookup"><span data-stu-id="54d16-103">The **-baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="54d16-104">Další informace o tom, kdy a proč tuto možnost použít, naleznete v [tématu WebLog Larryho Ostermana](https://docs.microsoft.com/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span><span class="sxs-lookup"><span data-stu-id="54d16-104">For more information about when and why to use this option, see [Larry Osterman's WebLog](https://docs.microsoft.com/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54d16-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54d16-105">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="54d16-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="54d16-106">Arguments</span></span>  
 `address`  
 <span data-ttu-id="54d16-107">Základní adresa pro dll.</span><span class="sxs-lookup"><span data-stu-id="54d16-107">The base address for the DLL.</span></span> <span data-ttu-id="54d16-108">Tuto adresu lze zadat jako desetinné, šestnáctkové nebo osmičkové číslo.</span><span class="sxs-lookup"><span data-stu-id="54d16-108">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54d16-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54d16-109">Remarks</span></span>  
 <span data-ttu-id="54d16-110">Výchozí základní adresa pro dll je nastavena za běhu mll .NET Framework common language.</span><span class="sxs-lookup"><span data-stu-id="54d16-110">The default base address for a DLL is set by the .NET Framework common language runtime.</span></span>  
  
 <span data-ttu-id="54d16-111">Uvědomte si, že slovo nižšího řádu v této adrese bude zaokrouhleno.</span><span class="sxs-lookup"><span data-stu-id="54d16-111">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="54d16-112">Pokud například zadáte 0x11110001, bude zaokrouhleno na 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="54d16-112">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="54d16-113">Chcete-li dokončit proces podepisování pro DLL, použijte SN. EXE s volbou -R.</span><span class="sxs-lookup"><span data-stu-id="54d16-113">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="54d16-114">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="54d16-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="54d16-115">Otevřete stránku **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="54d16-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="54d16-116">Klikněte na stránku vlastností **Sestavení.**</span><span class="sxs-lookup"><span data-stu-id="54d16-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="54d16-117">Klepněte na tlačítko **Upřesnit.**</span><span class="sxs-lookup"><span data-stu-id="54d16-117">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="54d16-118">Upravte vlastnost **Základní adresa DLL.**</span><span class="sxs-lookup"><span data-stu-id="54d16-118">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="54d16-119">Chcete-li tuto možnost kompilátoru nastavit programově, přečtěte si téma <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span><span class="sxs-lookup"><span data-stu-id="54d16-119">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54d16-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="54d16-120">See also</span></span>

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [<span data-ttu-id="54d16-121">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="54d16-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="54d16-122">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="54d16-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

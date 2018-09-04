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
ms.openlocfilehash: 58d1511387c93841f49d6ced934b492fe097876b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518517"
---
# <a name="-baseaddress-c-compiler-options"></a><span data-ttu-id="3610f-102">-baseaddress (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="3610f-102">-baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="3610f-103">**- Baseaddress** umožní zadat upřednostňované základní adrese, ve kterém se má načíst knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="3610f-103">The **-baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="3610f-104">Další informace o kdy a proč chcete použít tuto možnost najdete v tématu [Larry Osterman Weblogu](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).</span><span class="sxs-lookup"><span data-stu-id="3610f-104">For more information about when and why to use this option, see [Larry Osterman's WebLog](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3610f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3610f-105">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="3610f-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="3610f-106">Arguments</span></span>  
 `address`  
 <span data-ttu-id="3610f-107">Základní adresa pro knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="3610f-107">The base address for the DLL.</span></span> <span data-ttu-id="3610f-108">Tato adresa je zadat jako desítkové, hexadecimální nebo osmičkové číslo.</span><span class="sxs-lookup"><span data-stu-id="3610f-108">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3610f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3610f-109">Remarks</span></span>  
 <span data-ttu-id="3610f-110">Výchozí základní adresa knihovny DLL je nastavit modul common language runtime rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3610f-110">The default base address for a DLL is set by the .NET Framework common language runtime.</span></span>  
  
 <span data-ttu-id="3610f-111">Mějte na paměti, že se zaokrouhlí nižší řád slova v této adrese.</span><span class="sxs-lookup"><span data-stu-id="3610f-111">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="3610f-112">Například pokud chcete zadat 0x11110001, to se zaokrouhlí na 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="3610f-112">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="3610f-113">Dokončete proces podepisování pro knihovnu DLL pomocí sériové číslo. Soubor EXE s parametrem -R.</span><span class="sxs-lookup"><span data-stu-id="3610f-113">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3610f-114">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3610f-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="3610f-115">Otevřete v projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="3610f-115">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="3610f-116">Klikněte na tlačítko **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="3610f-116">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="3610f-117">Klikněte na tlačítko **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="3610f-117">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="3610f-118">Upravit **základní adresa knihovny DLL** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3610f-118">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="3610f-119">Programové nastavení tohoto parametru kompilátoru, naleznete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span><span class="sxs-lookup"><span data-stu-id="3610f-119">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3610f-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="3610f-120">See Also</span></span>  

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="3610f-121">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3610f-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="3610f-122">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="3610f-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

---
title: "-baseaddress (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7cd3269754f783ab8b26683f5215aa81825673e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="baseaddress-c-compiler-options"></a><span data-ttu-id="2f039-102">/baseaddress (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="2f039-102">/baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="2f039-103">**/BaseAddress** možnost umožňuje zadat upřednostňovaná základní adresa, na které se mají načíst knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="2f039-103">The **/baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="2f039-104">Další informace o kdy a proč použít tuto možnost najdete v tématu [Larry Osterman-blog](http://go.microsoft.com/fwlink/?LinkId=107044).</span><span class="sxs-lookup"><span data-stu-id="2f039-104">For more information about when and why to use this option, see [Larry Osterman's WebLog](http://go.microsoft.com/fwlink/?LinkId=107044).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f039-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f039-105">Syntax</span></span>  
  
```console  
/baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="2f039-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="2f039-106">Arguments</span></span>  
 `address`  
 <span data-ttu-id="2f039-107">Základní adresa pro knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="2f039-107">The base address for the DLL.</span></span> <span data-ttu-id="2f039-108">Tuto adresu můžete zadat hodnotu decimal, šestnáctkovém nebo osmičkové číslo.</span><span class="sxs-lookup"><span data-stu-id="2f039-108">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f039-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f039-109">Remarks</span></span>  
 <span data-ttu-id="2f039-110">Výchozí základní adresy knihovny DLL je nastavena pomocí modulu CLR rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2f039-110">The default base address for a DLL is set by the .NET Framework common language runtime.</span></span>  
  
 <span data-ttu-id="2f039-111">Mějte na paměti se zaokrouhlí na slovo nižší pořadí v tuto adresu.</span><span class="sxs-lookup"><span data-stu-id="2f039-111">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="2f039-112">Například pokud zadáte 0x11110001, ji budou zaokrouhlí 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="2f039-112">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="2f039-113">Chcete-li dokončit proces podepisování pro knihovny DLL, použijte SN. EXE s parametrem -R.</span><span class="sxs-lookup"><span data-stu-id="2f039-113">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="2f039-114">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2f039-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="2f039-115">Otevření projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="2f039-115">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="2f039-116">Klikněte **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="2f039-116">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="2f039-117">Klikněte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="2f039-117">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="2f039-118">Změnit **základní adresa knihovny DLL** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2f039-118">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="2f039-119">Pokud chcete nastavit tuto možnost kompilátoru prostřednictvím kódu programu, najdete v části <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span><span class="sxs-lookup"><span data-stu-id="2f039-119">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f039-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f039-120">See Also</span></span>  
 <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="2f039-121">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="2f039-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="2f039-122">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="2f039-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

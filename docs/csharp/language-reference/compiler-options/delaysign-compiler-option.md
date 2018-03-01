---
title: "-delaysign (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a931dccb2aebd2c898b55f0a007d9fac8da42f2e
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2018
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="18bf2-102">-delaysign (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="18bf2-102">-delaysign (C# Compiler Options)</span></span>
<span data-ttu-id="18bf2-103">Tato možnost způsobí, že kompilátor rezervovat místo ve výstupním souboru tak, aby digitální podpis lze přidat později.</span><span class="sxs-lookup"><span data-stu-id="18bf2-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18bf2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18bf2-104">Syntax</span></span>  
  
```console  
-delaysign[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="18bf2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="18bf2-105">Arguments</span></span>  
 <span data-ttu-id="18bf2-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="18bf2-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="18bf2-107">Použití **- delaysign –** Pokud chcete plně podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="18bf2-107">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="18bf2-108">Použití **- delaysign +** Pokud chcete umístit veřejný klíč v sestavení.</span><span class="sxs-lookup"><span data-stu-id="18bf2-108">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="18bf2-109">Výchozí hodnota je **- delaysign –**.</span><span class="sxs-lookup"><span data-stu-id="18bf2-109">The default is **-delaysign-**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18bf2-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18bf2-110">Remarks</span></span>  
 <span data-ttu-id="18bf2-111">**- Delaysign** možnost nemá žádný vliv, pokud není použita s [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) nebo [- keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="18bf2-111">The **-delaysign** option has no effect unless used with [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) or [-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span></span>  
  
 <span data-ttu-id="18bf2-112">Pokud budete požadovat plně podepsané sestavení, kompilátor vytvoří hodnotu hash souboru, který obsahuje manifest (metadata sestavení) a podepíše tuto hodnotu hash s privátním klíčem.</span><span class="sxs-lookup"><span data-stu-id="18bf2-112">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="18bf2-113">Výsledný digitální podpis je uložen do souboru obsahujícího manifest.</span><span class="sxs-lookup"><span data-stu-id="18bf2-113">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="18bf2-114">Při sestavení zpoždění, které jsou podepsané, kompilátor nepodporuje výpočetní a uložení podpis, ale rezervy místa v souboru, takže podpis lze přidat později.</span><span class="sxs-lookup"><span data-stu-id="18bf2-114">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="18bf2-115">Například pomocí **- delaysign +** umožňuje tester vložení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="18bf2-115">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="18bf2-116">Po otestování, je plně podepsat sestavení tak, že privátní klíč sestavení pomocí [Linker sestavení](../../../framework/tools/al-exe-assembly-linker.md) nástroj.</span><span class="sxs-lookup"><span data-stu-id="18bf2-116">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>  
  
 <span data-ttu-id="18bf2-117">Další informace najdete v tématu [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) a [zpoždění podepsání sestavení](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="18bf2-117">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="18bf2-118">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="18bf2-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="18bf2-119">Otevřete **vlastnosti** stránky pro projekt.</span><span class="sxs-lookup"><span data-stu-id="18bf2-119">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="18bf2-120">Změnit **zpoždění podepsání** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="18bf2-120">Modify the **Delay sign only** property.</span></span>  
  
 <span data-ttu-id="18bf2-121">Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="18bf2-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18bf2-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="18bf2-122">See Also</span></span>  
 [<span data-ttu-id="18bf2-123">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="18bf2-123">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="18bf2-124">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="18bf2-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

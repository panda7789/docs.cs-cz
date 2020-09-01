---
description: -delaysign (možnosti kompilátoru C#)
title: -delaysign (možnosti kompilátoru C#)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 5512ebeca4672f5d69852ab07c3f3fa40c305327
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125836"
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="1ff2a-103">-delaysign (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="1ff2a-103">-delaysign (C# Compiler Options)</span></span>

<span data-ttu-id="1ff2a-104">Tato možnost způsobí, že kompilátor vyhradí místo ve výstupním souboru, aby bylo možné přidat digitální podpis později.</span><span class="sxs-lookup"><span data-stu-id="1ff2a-104">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ff2a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ff2a-105">Syntax</span></span>

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a><span data-ttu-id="1ff2a-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1ff2a-106">Arguments</span></span>

<span data-ttu-id="1ff2a-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="1ff2a-107">`+` &#124; `-`</span></span>

<span data-ttu-id="1ff2a-108">Použijte **-delaysign –** Pokud chcete sestavení plně podepsaného.</span><span class="sxs-lookup"><span data-stu-id="1ff2a-108">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="1ff2a-109">Použijte **-delaysign +** , pokud chcete umístit pouze veřejný klíč do sestavení.</span><span class="sxs-lookup"><span data-stu-id="1ff2a-109">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="1ff2a-110">Výchozí hodnota je **-delaysign-**.</span><span class="sxs-lookup"><span data-stu-id="1ff2a-110">The default is **-delaysign-**.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ff2a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ff2a-111">Remarks</span></span>

<span data-ttu-id="1ff2a-112">Možnost **-delaysign** nemá žádný vliv, pokud se nepoužívá s parametrem [-keyfile](./keyfile-compiler-option.md) nebo [-](./keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="1ff2a-112">The **-delaysign** option has no effect unless used with [-keyfile](./keyfile-compiler-option.md) or [-keycontainer](./keycontainer-compiler-option.md).</span></span>

<span data-ttu-id="1ff2a-113">Možnosti **-delaysign** a **-publicsign** se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="1ff2a-113">The **-delaysign** and **-publicsign** options are mutually exclusive.</span></span>

<span data-ttu-id="1ff2a-114">Když vyžádáte plně podepsané sestavení, kompilátor vyhodnotí hodnotu hash souboru obsahujícího manifest (metadata sestavení) a podepíše tuto hodnotu hash privátním klíčem.</span><span class="sxs-lookup"><span data-stu-id="1ff2a-114">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="1ff2a-115">Tato operace vytvoří digitální podpis, který je uložený v souboru, který obsahuje manifest.</span><span class="sxs-lookup"><span data-stu-id="1ff2a-115">That operation creates a digital signature which is stored in the file that contains the manifest.</span></span> <span data-ttu-id="1ff2a-116">Když je sestavení podepsáno opožděně, kompilátor nevypočítá a uloží podpis, ale rezervuje místo v souboru, aby se podpis mohl přidat později.</span><span class="sxs-lookup"><span data-stu-id="1ff2a-116">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="1ff2a-117">Například použití možnosti **-delaysign +** umožní testerovi vložit sestavení do globální mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="1ff2a-117">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="1ff2a-118">Po otestování můžete sestavení plně podepsat umístěním privátního klíče do sestavení pomocí nástroje [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) .</span><span class="sxs-lookup"><span data-stu-id="1ff2a-118">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>

<span data-ttu-id="1ff2a-119">Další informace naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) a [Zpožděné podepisování sestavení](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="1ff2a-119">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1ff2a-120">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1ff2a-120">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="1ff2a-121">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="1ff2a-121">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="1ff2a-122">Upravte vlastnost **pouze pro Zpožděné podepsání** .</span><span class="sxs-lookup"><span data-stu-id="1ff2a-122">Modify the **Delay sign only** property.</span></span>

<span data-ttu-id="1ff2a-123">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.DelaySign%2A> .</span><span class="sxs-lookup"><span data-stu-id="1ff2a-123">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ff2a-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ff2a-124">See also</span></span>

- [<span data-ttu-id="1ff2a-125">C# – možnost publicsign</span><span class="sxs-lookup"><span data-stu-id="1ff2a-125">C# -publicsign option</span></span>](publicsign-compiler-option.md)
- [<span data-ttu-id="1ff2a-126">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="1ff2a-126">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="1ff2a-127">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="1ff2a-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

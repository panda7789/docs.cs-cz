---
title: -delaysign (C# možnosti kompilátoru)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 9fdc02c22d9d8c8a709155e43a17ebf0d86dfd69
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970446"
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="4086f-102">-delaysign (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="4086f-102">-delaysign (C# Compiler Options)</span></span>

<span data-ttu-id="4086f-103">Tato možnost způsobí, že kompilátor vyhradí místo ve výstupním souboru, aby bylo možné přidat digitální podpis později.</span><span class="sxs-lookup"><span data-stu-id="4086f-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>

## <a name="syntax"></a><span data-ttu-id="4086f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4086f-104">Syntax</span></span>

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a><span data-ttu-id="4086f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4086f-105">Arguments</span></span>

<span data-ttu-id="4086f-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="4086f-106">`+` &#124; `-`</span></span>

<span data-ttu-id="4086f-107">Použijte **-delaysign –** Pokud chcete sestavení plně podepsaného.</span><span class="sxs-lookup"><span data-stu-id="4086f-107">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="4086f-108">Použijte **-delaysign +** , pokud chcete umístit pouze veřejný klíč do sestavení.</span><span class="sxs-lookup"><span data-stu-id="4086f-108">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="4086f-109">Výchozí hodnota je **-delaysign-** .</span><span class="sxs-lookup"><span data-stu-id="4086f-109">The default is **-delaysign-**.</span></span>

## <a name="remarks"></a><span data-ttu-id="4086f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4086f-110">Remarks</span></span>

<span data-ttu-id="4086f-111">Možnost **-delaysign** nemá žádný vliv, pokud se nepoužívá s parametrem [-keyfile](./keyfile-compiler-option.md) nebo [-](./keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="4086f-111">The **-delaysign** option has no effect unless used with [-keyfile](./keyfile-compiler-option.md) or [-keycontainer](./keycontainer-compiler-option.md).</span></span>

<span data-ttu-id="4086f-112">Možnosti **-delaysign** a **-publicsign** se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="4086f-112">The **-delaysign** and **-publicsign** options are mutually exclusive.</span></span>

<span data-ttu-id="4086f-113">Když vyžádáte plně podepsané sestavení, kompilátor vyhodnotí hodnotu hash souboru obsahujícího manifest (metadata sestavení) a podepíše tuto hodnotu hash privátním klíčem.</span><span class="sxs-lookup"><span data-stu-id="4086f-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="4086f-114">Tato operace vytvoří digitální podpis, který je uložený v souboru, který obsahuje manifest.</span><span class="sxs-lookup"><span data-stu-id="4086f-114">That operation creates a digital signature which is stored in the file that contains the manifest.</span></span> <span data-ttu-id="4086f-115">Když je sestavení podepsáno opožděně, kompilátor nevypočítá a uloží podpis, ale rezervuje místo v souboru, aby se podpis mohl přidat později.</span><span class="sxs-lookup"><span data-stu-id="4086f-115">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="4086f-116">Například použití možnosti **-delaysign +** umožní testerovi vložit sestavení do globální mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="4086f-116">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="4086f-117">Po otestování můžete sestavení plně podepsat umístěním privátního klíče do sestavení pomocí nástroje [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) .</span><span class="sxs-lookup"><span data-stu-id="4086f-117">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>

<span data-ttu-id="4086f-118">Další informace naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) a [Zpožděné podepisování sestavení](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="4086f-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="4086f-119">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4086f-119">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="4086f-120">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="4086f-120">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="4086f-121">Upravte vlastnost **pouze pro Zpožděné podepsání** .</span><span class="sxs-lookup"><span data-stu-id="4086f-121">Modify the **Delay sign only** property.</span></span>

<span data-ttu-id="4086f-122">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>v tématu.</span><span class="sxs-lookup"><span data-stu-id="4086f-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="4086f-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4086f-123">See also</span></span>

- [<span data-ttu-id="4086f-124">C#-publicsign – možnost</span><span class="sxs-lookup"><span data-stu-id="4086f-124">C# -publicsign option</span></span>](publicsign-compiler-option.md)
- [<span data-ttu-id="4086f-125">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4086f-125">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="4086f-126">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="4086f-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

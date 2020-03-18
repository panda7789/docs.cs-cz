---
title: -delaysign (C# Možnosti kompilátoru)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 9fdc02c22d9d8c8a709155e43a17ebf0d86dfd69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970446"
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="7422e-102">-delaysign (C# Možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="7422e-102">-delaysign (C# Compiler Options)</span></span>

<span data-ttu-id="7422e-103">Tato možnost způsobí, že kompilátor rezervovat místo ve výstupním souboru tak, aby digitální podpis lze přidat později.</span><span class="sxs-lookup"><span data-stu-id="7422e-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>

## <a name="syntax"></a><span data-ttu-id="7422e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7422e-104">Syntax</span></span>

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a><span data-ttu-id="7422e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7422e-105">Arguments</span></span>

<span data-ttu-id="7422e-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="7422e-106">`+` &#124; `-`</span></span>

<span data-ttu-id="7422e-107">Použijte **-delaysign-** pokud chcete plně podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="7422e-107">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="7422e-108">Použijte **-delaysign+,** pokud chcete umístit veřejný klíč pouze do sestavení.</span><span class="sxs-lookup"><span data-stu-id="7422e-108">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="7422e-109">Výchozí hodnota je **-delaysign-**.</span><span class="sxs-lookup"><span data-stu-id="7422e-109">The default is **-delaysign-**.</span></span>

## <a name="remarks"></a><span data-ttu-id="7422e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7422e-110">Remarks</span></span>

<span data-ttu-id="7422e-111">Možnost **-delaysign** nemá žádný vliv, pokud není použita s [-keyfile](./keyfile-compiler-option.md) nebo [-keycontainer](./keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="7422e-111">The **-delaysign** option has no effect unless used with [-keyfile](./keyfile-compiler-option.md) or [-keycontainer](./keycontainer-compiler-option.md).</span></span>

<span data-ttu-id="7422e-112">Možnosti **-delaysign** a **-publicsign** se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="7422e-112">The **-delaysign** and **-publicsign** options are mutually exclusive.</span></span>

<span data-ttu-id="7422e-113">Když požadujete plně podepsané sestavení, kompilátor zařazuje soubor, který obsahuje manifest (metadata sestavení) a podepisuje, že hash s privátní klíč.</span><span class="sxs-lookup"><span data-stu-id="7422e-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="7422e-114">Tato operace vytvoří digitální podpis, který je uložen v souboru, který obsahuje manifest.</span><span class="sxs-lookup"><span data-stu-id="7422e-114">That operation creates a digital signature which is stored in the file that contains the manifest.</span></span> <span data-ttu-id="7422e-115">Při podepsání sestavení kompilátor nevypočítá a uloží podpis, ale rezervuje místo v souboru, takže podpis lze přidat později.</span><span class="sxs-lookup"><span data-stu-id="7422e-115">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="7422e-116">Například pomocí **-delaysign+** umožňuje tester umístit sestavení do globální mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="7422e-116">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="7422e-117">Po testování můžete plně podepsat sestavení umístěním soukromého klíče v sestavení pomocí nástroje [Linker sestavení.](../../../framework/tools/al-exe-assembly-linker.md)</span><span class="sxs-lookup"><span data-stu-id="7422e-117">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>

<span data-ttu-id="7422e-118">Další informace naleznete [v tématu Vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) a [zpožděné podepisování sestavení](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="7422e-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="7422e-119">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7422e-119">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="7422e-120">Otevřete stránku **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="7422e-120">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="7422e-121">Upravte pouze vlastnost **znaménko Zpoždění.**</span><span class="sxs-lookup"><span data-stu-id="7422e-121">Modify the **Delay sign only** property.</span></span>

<span data-ttu-id="7422e-122">Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>kompilátoru programově, naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="7422e-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="7422e-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="7422e-123">See also</span></span>

- [<span data-ttu-id="7422e-124">Možnost C# -publicsign</span><span class="sxs-lookup"><span data-stu-id="7422e-124">C# -publicsign option</span></span>](publicsign-compiler-option.md)
- [<span data-ttu-id="7422e-125">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7422e-125">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="7422e-126">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="7422e-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

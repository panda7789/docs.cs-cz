---
title: -delaysign (možnosti kompilátoru C#)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 105f564d40799c1c006caf8b59d6199dbd8e9318
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400193"
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="0d59d-102">-delaysign (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="0d59d-102">-delaysign (C# Compiler Options)</span></span>

<span data-ttu-id="0d59d-103">Tato možnost způsobí, že kompilátor rezervuje místo ve výstupním souboru tak, aby digitální podpis se dají přidat později.</span><span class="sxs-lookup"><span data-stu-id="0d59d-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d59d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d59d-104">Syntax</span></span>

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a><span data-ttu-id="0d59d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0d59d-105">Arguments</span></span>

<span data-ttu-id="0d59d-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="0d59d-106">`+` &#124; `-`</span></span>

<span data-ttu-id="0d59d-107">Použití **- delaysign-** potřebujete-li plně podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="0d59d-107">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="0d59d-108">Použití **- delaysign +** Pokud chcete umístit veřejný klíč v sestavení.</span><span class="sxs-lookup"><span data-stu-id="0d59d-108">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="0d59d-109">Výchozí hodnota je **- delaysign-**.</span><span class="sxs-lookup"><span data-stu-id="0d59d-109">The default is **-delaysign-**.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d59d-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d59d-110">Remarks</span></span>

<span data-ttu-id="0d59d-111">**- Delaysign** možnost nemá žádný vliv, pokud nejsou použity s [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) nebo [- keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="0d59d-111">The **-delaysign** option has no effect unless used with [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) or [-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span></span>

<span data-ttu-id="0d59d-112">**- Delaysign** a **- publicsign** možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="0d59d-112">The **-delaysign** and **-publicsign** options are mutually exclusive.</span></span>

<span data-ttu-id="0d59d-113">Pokud budete požadovat plně podepsané sestavení, kompilátor vytvoří hodnotu hash souboru, který obsahuje manifest (metadata sestavení) a podepíše tuto hodnotu hash pomocí soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="0d59d-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="0d59d-114">Tato operace vytvoří digitální podpis, který je uložený v souboru, který obsahuje manifest.</span><span class="sxs-lookup"><span data-stu-id="0d59d-114">That operation creates a digital signature which is stored in the file that contains the manifest.</span></span> <span data-ttu-id="0d59d-115">Pokud je sestavení podepisováno, kompilátor a neukládá podpis, ale rezervuje prostor v souboru tak, že podpis se dají přidat později.</span><span class="sxs-lookup"><span data-stu-id="0d59d-115">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="0d59d-116">Například použití **- delaysign +** umožňuje testerovi vložit sestavení do globální mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="0d59d-116">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="0d59d-117">Po otestování je tak, že privátní klíč v sestavení s využitím plně podepsat sestavení [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) nástroj.</span><span class="sxs-lookup"><span data-stu-id="0d59d-117">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>

<span data-ttu-id="0d59d-118">Další informace najdete v tématu [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) a [zpožděné podepisování sestavení](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="0d59d-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="0d59d-119">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0d59d-119">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="0d59d-120">Otevřít **vlastnosti** stránky pro projekt.</span><span class="sxs-lookup"><span data-stu-id="0d59d-120">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="0d59d-121">Upravit **zpoždění podepsání** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0d59d-121">Modify the **Delay sign only** property.</span></span>

<span data-ttu-id="0d59d-122">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d59d-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d59d-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d59d-123">See Also</span></span>

- [<span data-ttu-id="0d59d-124">-Publicsign možnosti jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0d59d-124">C# -publicsign option</span></span>](publicsign-compiler-option.md)  
- [<span data-ttu-id="0d59d-125">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0d59d-125">C# Compiler Options</span></span>](index.md)  
- [<span data-ttu-id="0d59d-126">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="0d59d-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

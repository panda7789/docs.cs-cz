---
title: "-delaysign (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 62f76747a29a90562706dff5fa742316c5b99b74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="delaysign-c-compiler-options"></a><span data-ttu-id="64fe6-102">/delaysign (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="64fe6-102">/delaysign (C# Compiler Options)</span></span>
<span data-ttu-id="64fe6-103">Tato možnost způsobí, že kompilátor rezervovat místo ve výstupním souboru tak, aby digitální podpis lze přidat později.</span><span class="sxs-lookup"><span data-stu-id="64fe6-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64fe6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64fe6-104">Syntax</span></span>  
  
```console  
/delaysign[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="64fe6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="64fe6-105">Arguments</span></span>  
 <span data-ttu-id="64fe6-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="64fe6-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="64fe6-107">Použití **/delaysign-** Pokud chcete plně podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="64fe6-107">Use **/delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="64fe6-108">Použití **/delaysign+** Pokud chcete umístit veřejný klíč v sestavení.</span><span class="sxs-lookup"><span data-stu-id="64fe6-108">Use **/delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="64fe6-109">Výchozí hodnota je **/delaysign-**.</span><span class="sxs-lookup"><span data-stu-id="64fe6-109">The default is **/delaysign-**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64fe6-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="64fe6-110">Remarks</span></span>  
 <span data-ttu-id="64fe6-111">**/Delaysign** možnost nemá žádný vliv, pokud není použita s [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) nebo [/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="64fe6-111">The **/delaysign** option has no effect unless used with [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) or [/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span></span>  
  
 <span data-ttu-id="64fe6-112">Pokud budete požadovat plně podepsané sestavení, kompilátor vytvoří hodnotu hash souboru, který obsahuje manifest (metadata sestavení) a podepíše tuto hodnotu hash s privátním klíčem.</span><span class="sxs-lookup"><span data-stu-id="64fe6-112">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="64fe6-113">Výsledný digitální podpis je uložen do souboru obsahujícího manifest.</span><span class="sxs-lookup"><span data-stu-id="64fe6-113">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="64fe6-114">Při sestavení zpoždění, které jsou podepsané, kompilátor nepodporuje výpočetní a uložení podpis, ale rezervy místa v souboru, takže podpis lze přidat později.</span><span class="sxs-lookup"><span data-stu-id="64fe6-114">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="64fe6-115">Například pomocí **/delaysign+** umožňuje tester vložení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="64fe6-115">For example, using **/delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="64fe6-116">Po otestování, je plně podepsat sestavení tak, že privátní klíč sestavení pomocí [Linker sestavení](../../../framework/tools/al-exe-assembly-linker.md) nástroj.</span><span class="sxs-lookup"><span data-stu-id="64fe6-116">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>  
  
 <span data-ttu-id="64fe6-117">Další informace najdete v tématu [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) a [zpoždění podepsání sestavení](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="64fe6-117">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="64fe6-118">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="64fe6-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="64fe6-119">Otevřete **vlastnosti** stránky pro projekt.</span><span class="sxs-lookup"><span data-stu-id="64fe6-119">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="64fe6-120">Změnit **zpoždění podepsání** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="64fe6-120">Modify the **Delay sign only** property.</span></span>  
  
 <span data-ttu-id="64fe6-121">Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="64fe6-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64fe6-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="64fe6-122">See Also</span></span>  
 [<span data-ttu-id="64fe6-123">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="64fe6-123">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="64fe6-124">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="64fe6-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

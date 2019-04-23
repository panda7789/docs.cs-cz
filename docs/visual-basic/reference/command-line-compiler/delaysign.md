---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: 770dcad385c522a548a0c6fd3b6ef02dfbac82f5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59334598"
---
# <a name="-delaysign"></a><span data-ttu-id="4a6a2-102">-delaysign</span><span class="sxs-lookup"><span data-stu-id="4a6a2-102">-delaysign</span></span>
<span data-ttu-id="4a6a2-103">Určuje, zda bude sestavení zcela nebo částečně podepsáno.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-103">Specifies whether the assembly will be fully or partially signed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a6a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a6a2-104">Syntax</span></span>  
  
```  
-delaysign[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4a6a2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4a6a2-105">Arguments</span></span>  
 <span data-ttu-id="4a6a2-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="4a6a2-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="4a6a2-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-107">Optional.</span></span> <span data-ttu-id="4a6a2-108">Použití `-delaysign-` potřebujete-li plně podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-108">Use `-delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="4a6a2-109">Použití `-delaysign+` Pokud chcete umístit veřejný klíč v sestavení a rezervy místa pro podepsané hash.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-109">Use `-delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="4a6a2-110">Výchozí hodnota je `-delaysign-`.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-110">The default is `-delaysign-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a6a2-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a6a2-111">Remarks</span></span>  
 <span data-ttu-id="4a6a2-112">`-delaysign` Možnost nemá žádný vliv, pokud nejsou použity s [- keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) nebo [- keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="4a6a2-112">The `-delaysign` option has no effect unless used with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>  
  
 <span data-ttu-id="4a6a2-113">Pokud budete požadovat plně podepsané sestavení, kompilátor vytvoří hodnotu hash souboru, který obsahuje manifest (metadata sestavení) a podepíše tuto hodnotu hash pomocí soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="4a6a2-114">Výsledný digitální podpis je uložen do souboru obsahujícího manifest.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="4a6a2-115">Pokud je sestavení podepisováno, kompilátor a neukládá podpis, ale rezervy místa v souboru tak, že podpis se dají přidat později.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="4a6a2-116">Například s použitím `-delaysign+`, vývojář v organizaci můžete distribuovat bez znaménka testovací verze sestavení, které testerů můžete zaregistrovat do globální mezipaměti sestavení a použít.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-116">For example, by using `-delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="4a6a2-117">Po dokončení práce na sestavení je osoba zodpovědná za soukromého klíče organizace plně podepsat sestavení.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="4a6a2-118">Tento takové chrání privátní klíče organizace před vyzrazením, zároveň umožní všem vývojářům umožňuje pracovat na sestavení.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>  
  
 <span data-ttu-id="4a6a2-119">Zobrazit [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) Další informace o podepisování sestavení.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-119">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="4a6a2-120">Chcete-li nastavit - delaysign v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4a6a2-120">To set -delaysign in the Visual Studio integrated development environment</span></span>  
  
1. <span data-ttu-id="4a6a2-121">Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="4a6a2-122">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-122">On the **Project** menu, click **Properties**.</span></span>   
  
2. <span data-ttu-id="4a6a2-123">Klikněte na tlačítko **podepisování** kartu.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-123">Click the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="4a6a2-124">Nastavte hodnotu **zpoždění podepsání** pole.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-124">Set the value in the **Delay sign only** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a6a2-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a6a2-125">See also</span></span>

- [<span data-ttu-id="4a6a2-126">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="4a6a2-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="4a6a2-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="4a6a2-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="4a6a2-128">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="4a6a2-128">-keycontainer</span></span>](../../../visual-basic/reference/command-line-compiler/keycontainer.md)
- [<span data-ttu-id="4a6a2-129">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="4a6a2-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

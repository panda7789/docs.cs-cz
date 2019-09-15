---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: 6d3c89d598714446e04ba40155951f771d474866
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971995"
---
# <a name="-delaysign"></a><span data-ttu-id="87a02-102">-delaysign</span><span class="sxs-lookup"><span data-stu-id="87a02-102">-delaysign</span></span>
<span data-ttu-id="87a02-103">Určuje, zda bude sestavení zcela nebo částečně podepsáno.</span><span class="sxs-lookup"><span data-stu-id="87a02-103">Specifies whether the assembly will be fully or partially signed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87a02-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87a02-104">Syntax</span></span>  
  
```  
-delaysign[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="87a02-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="87a02-105">Arguments</span></span>  
 <span data-ttu-id="87a02-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="87a02-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="87a02-107">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="87a02-107">Optional.</span></span> <span data-ttu-id="87a02-108">Použijte `-delaysign-` , pokud chcete sestavení plně podepsaného.</span><span class="sxs-lookup"><span data-stu-id="87a02-108">Use `-delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="87a02-109">Použijte `-delaysign+` , pokud chcete umístit veřejný klíč do sestavení a rezervovat místo pro podepsaný algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="87a02-109">Use `-delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="87a02-110">Výchozí hodnota je `-delaysign-`.</span><span class="sxs-lookup"><span data-stu-id="87a02-110">The default is `-delaysign-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87a02-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87a02-111">Remarks</span></span>  
 <span data-ttu-id="87a02-112">Možnost nemá žádný vliv, pokud se nepoužívá s parametrem [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) nebo-. [](../../../visual-basic/reference/command-line-compiler/keycontainer.md) `-delaysign`</span><span class="sxs-lookup"><span data-stu-id="87a02-112">The `-delaysign` option has no effect unless used with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>  
  
 <span data-ttu-id="87a02-113">Když vyžádáte plně podepsané sestavení, kompilátor vyhodnotí hodnotu hash souboru obsahujícího manifest (metadata sestavení) a podepíše tuto hodnotu hash privátním klíčem.</span><span class="sxs-lookup"><span data-stu-id="87a02-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="87a02-114">Výsledný digitální podpis je uložen do souboru obsahujícího manifest.</span><span class="sxs-lookup"><span data-stu-id="87a02-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="87a02-115">Když je sestavení podepsáno opožděně, kompilátor nevypočítá a uloží podpis, ale rezervuje místo v souboru, aby bylo možné podpis přidat později.</span><span class="sxs-lookup"><span data-stu-id="87a02-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="87a02-116">Například pomocí nástroje `-delaysign+`může vývojář v organizaci distribuovat nepodepsané testovací verze sestavení, které mohou testeri zaregistrovat s globální mezipamětí sestavení a použít.</span><span class="sxs-lookup"><span data-stu-id="87a02-116">For example, by using `-delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="87a02-117">Po dokončení práce na sestavení může osoba odpovědná za soukromý klíč organizace plně podepsat sestavení.</span><span class="sxs-lookup"><span data-stu-id="87a02-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="87a02-118">Tato compartmentalization chrání privátní klíč organizace před zveřejněním a umožňuje všem vývojářům pracovat na sestaveních.</span><span class="sxs-lookup"><span data-stu-id="87a02-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>  
  
 <span data-ttu-id="87a02-119">Další informace o podepsání sestavení naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) .</span><span class="sxs-lookup"><span data-stu-id="87a02-119">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="87a02-120">Nastavení-delaysign v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="87a02-120">To set -delaysign in the Visual Studio integrated development environment</span></span>  
  
1. <span data-ttu-id="87a02-121">Máte projekt vybraný v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="87a02-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="87a02-122">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="87a02-122">On the **Project** menu, click **Properties**.</span></span>   
  
2. <span data-ttu-id="87a02-123">Klikněte na kartu **podepisování** .</span><span class="sxs-lookup"><span data-stu-id="87a02-123">Click the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="87a02-124">Nastavte hodnotu v poli **pouze Zpožděné podepsání** .</span><span class="sxs-lookup"><span data-stu-id="87a02-124">Set the value in the **Delay sign only** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87a02-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87a02-125">See also</span></span>

- [<span data-ttu-id="87a02-126">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="87a02-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="87a02-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="87a02-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="87a02-128">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="87a02-128">-keycontainer</span></span>](../../../visual-basic/reference/command-line-compiler/keycontainer.md)
- [<span data-ttu-id="87a02-129">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="87a02-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

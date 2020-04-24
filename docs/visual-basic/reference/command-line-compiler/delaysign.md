---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: 3ee94df096b756be544964cfbbd405355e3f728f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581275"
---
# <a name="-delaysign"></a><span data-ttu-id="26ee0-102">-delaysign</span><span class="sxs-lookup"><span data-stu-id="26ee0-102">-delaysign</span></span>

<span data-ttu-id="26ee0-103">Určuje, zda bude sestavení zcela nebo částečně podepsáno.</span><span class="sxs-lookup"><span data-stu-id="26ee0-103">Specifies whether the assembly will be fully or partially signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="26ee0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26ee0-104">Syntax</span></span>

```console
-delaysign[+ | -]
```

## <a name="arguments"></a><span data-ttu-id="26ee0-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="26ee0-105">Arguments</span></span>

<span data-ttu-id="26ee0-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="26ee0-106">`+` &#124; `-`</span></span>  
<span data-ttu-id="26ee0-107">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="26ee0-107">Optional.</span></span> <span data-ttu-id="26ee0-108">Použijte `-delaysign-` , pokud chcete sestavení plně podepsaného.</span><span class="sxs-lookup"><span data-stu-id="26ee0-108">Use `-delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="26ee0-109">Použijte `-delaysign+` , pokud chcete umístit veřejný klíč do sestavení a rezervovat místo pro podepsaný algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="26ee0-109">Use `-delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="26ee0-110">Výchozí formát je `-delaysign-`.</span><span class="sxs-lookup"><span data-stu-id="26ee0-110">The default is `-delaysign-`.</span></span>

## <a name="remarks"></a><span data-ttu-id="26ee0-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="26ee0-111">Remarks</span></span>

<span data-ttu-id="26ee0-112">`-delaysign` Možnost nemá žádný vliv, pokud se nepoužívá s parametrem [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) nebo [-](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="26ee0-112">The `-delaysign` option has no effect unless used with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>

<span data-ttu-id="26ee0-113">Když vyžádáte plně podepsané sestavení, kompilátor vyhodnotí hodnotu hash souboru obsahujícího manifest (metadata sestavení) a podepíše tuto hodnotu hash privátním klíčem.</span><span class="sxs-lookup"><span data-stu-id="26ee0-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="26ee0-114">Výsledný digitální podpis je uložen do souboru obsahujícího manifest.</span><span class="sxs-lookup"><span data-stu-id="26ee0-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="26ee0-115">Když je sestavení podepsáno opožděně, kompilátor nevypočítá a uloží podpis, ale rezervuje místo v souboru, aby bylo možné podpis přidat později.</span><span class="sxs-lookup"><span data-stu-id="26ee0-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="26ee0-116">Například pomocí nástroje `-delaysign+`může vývojář v organizaci distribuovat nepodepsané testovací verze sestavení, které mohou testeri zaregistrovat s globální mezipamětí sestavení a použít.</span><span class="sxs-lookup"><span data-stu-id="26ee0-116">For example, by using `-delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="26ee0-117">Po dokončení práce na sestavení může osoba odpovědná za soukromý klíč organizace plně podepsat sestavení.</span><span class="sxs-lookup"><span data-stu-id="26ee0-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="26ee0-118">Tato compartmentalization chrání privátní klíč organizace před zveřejněním a umožňuje všem vývojářům pracovat na sestaveních.</span><span class="sxs-lookup"><span data-stu-id="26ee0-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>

<span data-ttu-id="26ee0-119">Další informace o podepsání sestavení naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) .</span><span class="sxs-lookup"><span data-stu-id="26ee0-119">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>

### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="26ee0-120">Nastavení-delaysign v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="26ee0-120">To set -delaysign in the Visual Studio integrated development environment</span></span>

1. <span data-ttu-id="26ee0-121">Máte projekt vybraný v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="26ee0-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="26ee0-122">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="26ee0-122">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="26ee0-123">Klikněte na kartu **podepisování** .</span><span class="sxs-lookup"><span data-stu-id="26ee0-123">Click the **Signing** tab.</span></span>

3. <span data-ttu-id="26ee0-124">Nastavte hodnotu v poli **pouze Zpožděné podepsání** .</span><span class="sxs-lookup"><span data-stu-id="26ee0-124">Set the value in the **Delay sign only** box.</span></span>

## <a name="see-also"></a><span data-ttu-id="26ee0-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="26ee0-125">See also</span></span>

- [<span data-ttu-id="26ee0-126">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="26ee0-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="26ee0-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="26ee0-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="26ee0-128">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="26ee0-128">-keycontainer</span></span>](../../../visual-basic/reference/command-line-compiler/keycontainer.md)
- [<span data-ttu-id="26ee0-129">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="26ee0-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

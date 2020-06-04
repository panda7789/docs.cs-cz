---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: c9bb302e2b34ebe1f51cf39bb3db1094d420d7f4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408696"
---
# <a name="-delaysign"></a><span data-ttu-id="19b40-102">-delaysign</span><span class="sxs-lookup"><span data-stu-id="19b40-102">-delaysign</span></span>

<span data-ttu-id="19b40-103">Určuje, zda bude sestavení zcela nebo částečně podepsáno.</span><span class="sxs-lookup"><span data-stu-id="19b40-103">Specifies whether the assembly will be fully or partially signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="19b40-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19b40-104">Syntax</span></span>

```console
-delaysign[+ | -]
```

## <a name="arguments"></a><span data-ttu-id="19b40-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="19b40-105">Arguments</span></span>

<span data-ttu-id="19b40-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="19b40-106">`+` &#124; `-`</span></span>  
<span data-ttu-id="19b40-107">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="19b40-107">Optional.</span></span> <span data-ttu-id="19b40-108">Použijte, `-delaysign-` Pokud chcete sestavení plně podepsaného.</span><span class="sxs-lookup"><span data-stu-id="19b40-108">Use `-delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="19b40-109">Použijte, `-delaysign+` Pokud chcete umístit veřejný klíč do sestavení a rezervovat místo pro podepsaný algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="19b40-109">Use `-delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="19b40-110">Výchozí formát je `-delaysign-`.</span><span class="sxs-lookup"><span data-stu-id="19b40-110">The default is `-delaysign-`.</span></span>

## <a name="remarks"></a><span data-ttu-id="19b40-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19b40-111">Remarks</span></span>

<span data-ttu-id="19b40-112">`-delaysign`Možnost nemá žádný vliv, pokud se nepoužívá s parametrem [-keyfile](keyfile.md) nebo [-](keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="19b40-112">The `-delaysign` option has no effect unless used with [-keyfile](keyfile.md) or [-keycontainer](keycontainer.md).</span></span>

<span data-ttu-id="19b40-113">Když vyžádáte plně podepsané sestavení, kompilátor vyhodnotí hodnotu hash souboru obsahujícího manifest (metadata sestavení) a podepíše tuto hodnotu hash privátním klíčem.</span><span class="sxs-lookup"><span data-stu-id="19b40-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="19b40-114">Výsledný digitální podpis je uložen do souboru obsahujícího manifest.</span><span class="sxs-lookup"><span data-stu-id="19b40-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="19b40-115">Když je sestavení podepsáno opožděně, kompilátor nevypočítá a uloží podpis, ale rezervuje místo v souboru, aby bylo možné podpis přidat později.</span><span class="sxs-lookup"><span data-stu-id="19b40-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="19b40-116">Například pomocí nástroje `-delaysign+` může vývojář v organizaci distribuovat nepodepsané testovací verze sestavení, které mohou testeri zaregistrovat s globální mezipamětí sestavení a použít.</span><span class="sxs-lookup"><span data-stu-id="19b40-116">For example, by using `-delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="19b40-117">Po dokončení práce na sestavení může osoba odpovědná za soukromý klíč organizace plně podepsat sestavení.</span><span class="sxs-lookup"><span data-stu-id="19b40-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="19b40-118">Tato compartmentalization chrání privátní klíč organizace před zveřejněním a umožňuje všem vývojářům pracovat na sestaveních.</span><span class="sxs-lookup"><span data-stu-id="19b40-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>

<span data-ttu-id="19b40-119">Další informace o podepsání sestavení naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) .</span><span class="sxs-lookup"><span data-stu-id="19b40-119">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>

### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="19b40-120">Nastavení-delaysign v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="19b40-120">To set -delaysign in the Visual Studio integrated development environment</span></span>

1. <span data-ttu-id="19b40-121">Máte projekt vybraný v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="19b40-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="19b40-122">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="19b40-122">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="19b40-123">Klikněte na kartu **podepisování** .</span><span class="sxs-lookup"><span data-stu-id="19b40-123">Click the **Signing** tab.</span></span>

3. <span data-ttu-id="19b40-124">Nastavte hodnotu v poli **pouze Zpožděné podepsání** .</span><span class="sxs-lookup"><span data-stu-id="19b40-124">Set the value in the **Delay sign only** box.</span></span>

## <a name="see-also"></a><span data-ttu-id="19b40-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="19b40-125">See also</span></span>

- [<span data-ttu-id="19b40-126">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="19b40-126">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="19b40-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="19b40-127">-keyfile</span></span>](keyfile.md)
- [<span data-ttu-id="19b40-128">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="19b40-128">-keycontainer</span></span>](keycontainer.md)
- [<span data-ttu-id="19b40-129">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="19b40-129">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)

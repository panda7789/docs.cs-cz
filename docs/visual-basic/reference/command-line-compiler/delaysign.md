---
title: /delaysign
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- /delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dc457a1a32048441f82976488158f223e7e3e087
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="delaysign"></a><span data-ttu-id="5d831-102">/delaysign</span><span class="sxs-lookup"><span data-stu-id="5d831-102">/delaysign</span></span>
<span data-ttu-id="5d831-103">Určuje, zda bude sestavení zcela nebo částečně podepsáno.</span><span class="sxs-lookup"><span data-stu-id="5d831-103">Specifies whether the assembly will be fully or partially signed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d831-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d831-104">Syntax</span></span>  
  
```  
/delaysign[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5d831-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5d831-105">Arguments</span></span>  
 <span data-ttu-id="5d831-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="5d831-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="5d831-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="5d831-107">Optional.</span></span> <span data-ttu-id="5d831-108">Použití `/delaysign-` Pokud chcete plně podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="5d831-108">Use `/delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="5d831-109">Použití `/delaysign+` Pokud chcete umístit veřejný klíč v sestavení a rezervy místa pro podepsané hash.</span><span class="sxs-lookup"><span data-stu-id="5d831-109">Use `/delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="5d831-110">Výchozí hodnota je `/delaysign-`.</span><span class="sxs-lookup"><span data-stu-id="5d831-110">The default is `/delaysign-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d831-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d831-111">Remarks</span></span>  
 <span data-ttu-id="5d831-112">`/delaysign` Možnost nemá žádný vliv, pokud není použita s [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) nebo [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="5d831-112">The `/delaysign` option has no effect unless used with [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>  
  
 <span data-ttu-id="5d831-113">Pokud budete požadovat plně podepsané sestavení, kompilátor vytvoří hodnotu hash souboru, který obsahuje manifest (metadata sestavení) a podepíše tuto hodnotu hash s privátním klíčem.</span><span class="sxs-lookup"><span data-stu-id="5d831-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="5d831-114">Výsledný digitální podpis je uložen do souboru obsahujícího manifest.</span><span class="sxs-lookup"><span data-stu-id="5d831-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="5d831-115">Při sestavení zpoždění, které jsou podepsané, kompilátor nepodporuje výpočetní a uložení podpis ale rezervy místa v souboru, takže podpis lze přidat později.</span><span class="sxs-lookup"><span data-stu-id="5d831-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="5d831-116">Například pomocí `/delaysign+`, vývojáři v organizaci můžete distribuovat nepodepsané testovací verze sestavení, které testery můžete zaregistrovat s globální mezipaměti sestavení a použít.</span><span class="sxs-lookup"><span data-stu-id="5d831-116">For example, by using `/delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="5d831-117">Po dokončení práce na sestavení může osoba odpovědná za soukromého klíče organizace plně podepsat sestavení.</span><span class="sxs-lookup"><span data-stu-id="5d831-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="5d831-118">Tato takové soukromého klíče organizace chrání před zpřístupnění současně všechny vývojářům pracovat na sestavení.</span><span class="sxs-lookup"><span data-stu-id="5d831-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>  
  
 <span data-ttu-id="5d831-119">V tématu [vytvoření a použití sestavení](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md) Další informace o podepisování sestavení.</span><span class="sxs-lookup"><span data-stu-id="5d831-119">See [Creating and Using Strong-Named Assemblies](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
### <a name="to-set-delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="5d831-120">Chcete-li nastavit/delaysign v sadě Visual Studio integrované vývojové prostředí</span><span class="sxs-lookup"><span data-stu-id="5d831-120">To set /delaysign in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="5d831-121">Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="5d831-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="5d831-122">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="5d831-122">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="5d831-123">Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="5d831-123">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="5d831-124">Klikněte **podpisování** kartě.</span><span class="sxs-lookup"><span data-stu-id="5d831-124">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="5d831-125">Nastavte hodnotu v **zpoždění podepsání** pole.</span><span class="sxs-lookup"><span data-stu-id="5d831-125">Set the value in the **Delay sign only** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d831-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d831-126">See Also</span></span>  
 [<span data-ttu-id="5d831-127">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="5d831-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="5d831-128">/ keyfile</span><span class="sxs-lookup"><span data-stu-id="5d831-128">/keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="5d831-129">/ keycontainer</span><span class="sxs-lookup"><span data-stu-id="5d831-129">/keycontainer</span></span>](../../../visual-basic/reference/command-line-compiler/keycontainer.md)  
 [<span data-ttu-id="5d831-130">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="5d831-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

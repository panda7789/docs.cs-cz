---
title: "Chyba při vytváření sestavení manifestu: &lt;chybová zpráva&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords: BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5e88d28ef787eb57b71d94f4ee51c09e9751dbff
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a><span data-ttu-id="aa8cc-102">Chyba při vytváření sestavení manifestu: &lt;chybová zpráva&gt;</span><span class="sxs-lookup"><span data-stu-id="aa8cc-102">Error creating assembly manifest: &lt;error message&gt;</span></span>
<span data-ttu-id="aa8cc-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilátoru volá Linker sestavení (Al.exe, také známé jako Alink) ke generování sestavení s manifestu.</span><span class="sxs-lookup"><span data-stu-id="aa8cc-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="aa8cc-104">Linkeru ohlásilo chybu ve fázi před emisí vytváření sestavení.</span><span class="sxs-lookup"><span data-stu-id="aa8cc-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="aa8cc-105">Tato situace může nastat, pokud dochází k problémům s souboru klíče nebo klíče zadaný kontejner.</span><span class="sxs-lookup"><span data-stu-id="aa8cc-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="aa8cc-106">Chcete-li plně podepsání sestavení, je nutné zadat platný soubor klíče, který obsahuje informace o veřejné a soukromé klíče.</span><span class="sxs-lookup"><span data-stu-id="aa8cc-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="aa8cc-107">Zpoždění podepsání sestavení, musíte vybrat **zpoždění podepsání** zaškrtněte políčko a zadejte platný soubor klíče, který obsahuje informace o informace o veřejném klíči.</span><span class="sxs-lookup"><span data-stu-id="aa8cc-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="aa8cc-108">Privátní klíč není nutné, pokud je sestavení podepsané zpoždění.</span><span class="sxs-lookup"><span data-stu-id="aa8cc-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="aa8cc-109">Další informace najdete v tématu [postupy: podepsání sestavení se silným názvem](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="aa8cc-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
 <span data-ttu-id="aa8cc-110">**ID chyby:** BC30140</span><span class="sxs-lookup"><span data-stu-id="aa8cc-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aa8cc-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="aa8cc-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="aa8cc-112">Prověřením uvozovkách chybové zprávy a podívejte se téma [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="aa8cc-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="aa8cc-113">došlo k chybě AL1019 další vysvětlení a Rady, jak</span><span class="sxs-lookup"><span data-stu-id="aa8cc-113">for error AL1019 further explanation and advice</span></span>  
  
2.  <span data-ttu-id="aa8cc-114">Pokud potíže potrvají, shromažďovat informace o okolnostech a upozornění služby Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="aa8cc-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa8cc-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa8cc-115">See Also</span></span>  
 [<span data-ttu-id="aa8cc-116">Postupy: Podepsání sestavení silným názvem</span><span class="sxs-lookup"><span data-stu-id="aa8cc-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="aa8cc-117">Stránka Podepisování, Návrhář projektu</span><span class="sxs-lookup"><span data-stu-id="aa8cc-117">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)  
 <span data-ttu-id="aa8cc-118">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="aa8cc-118">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span>  
 [<span data-ttu-id="aa8cc-119">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="aa8cc-119">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)

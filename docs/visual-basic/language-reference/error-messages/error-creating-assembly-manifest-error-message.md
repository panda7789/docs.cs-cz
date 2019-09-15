---
title: 'Při vytváření manifestu sestavení došlo k chybě: <error message>'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: 560635718a931cc9cdb687154a1d23970136de97
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972289"
---
# <a name="error-creating-assembly-manifest-error-message"></a><span data-ttu-id="0ba1f-102">Chyba při vytváření manifestu sestavení \<: chybová zpráva ></span><span class="sxs-lookup"><span data-stu-id="0ba1f-102">Error creating assembly manifest: \<error message></span></span>
<span data-ttu-id="0ba1f-103">Kompilátor Visual Basic volá linker sestavení (Al. exe, označovaný také jako ALink), aby vygeneroval sestavení s manifestem.</span><span class="sxs-lookup"><span data-stu-id="0ba1f-103">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="0ba1f-104">Linker oznámil chybu v předprodukční fázi vytváření sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ba1f-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="0ba1f-105">K tomu může dojít, pokud dojde k potížím se souborem klíče nebo s určeným kontejnerem klíčů.</span><span class="sxs-lookup"><span data-stu-id="0ba1f-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="0ba1f-106">Pro úplné podepsání sestavení je nutné zadat platný soubor klíče, který obsahuje informace o veřejných a privátních klíčích.</span><span class="sxs-lookup"><span data-stu-id="0ba1f-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="0ba1f-107">Chcete-li zpozdit podepsání sestavení, je nutné zaškrtnout políčko **pouze zpožděné znaménko** a zadat platný soubor klíče, který obsahuje informace o informacích o veřejném klíči.</span><span class="sxs-lookup"><span data-stu-id="0ba1f-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="0ba1f-108">Privátní klíč není nezbytný, pokud je sestavení podepsáno opožděně.</span><span class="sxs-lookup"><span data-stu-id="0ba1f-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="0ba1f-109">Další informace najdete v tématu [jak: Podepište sestavení silným názvem](../../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="0ba1f-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../standard/assembly/sign-strong-name.md).</span></span>  
  
 <span data-ttu-id="0ba1f-110">**ID chyby:** BC30140</span><span class="sxs-lookup"><span data-stu-id="0ba1f-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0ba1f-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0ba1f-111">To correct this error</span></span>  
  
1. <span data-ttu-id="0ba1f-112">Prohlédněte si chybovou zprávu v uvozovkách a Projděte si téma [Al. exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="0ba1f-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="0ba1f-113">Další vysvětlení a Rady k chybě AL1019</span><span class="sxs-lookup"><span data-stu-id="0ba1f-113">for error AL1019 further explanation and advice</span></span>  
  
2. <span data-ttu-id="0ba1f-114">Pokud chyba přetrvává, shromážděte informace o okolnostech a upozorněte služby podpory společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0ba1f-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ba1f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ba1f-115">See also</span></span>

- [<span data-ttu-id="0ba1f-116">Postupy: Podepsat sestavení silným názvem</span><span class="sxs-lookup"><span data-stu-id="0ba1f-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="0ba1f-117">Stránka Podepisování, Návrhář projektu</span><span class="sxs-lookup"><span data-stu-id="0ba1f-117">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
- [<span data-ttu-id="0ba1f-118">Al.exe</span><span class="sxs-lookup"><span data-stu-id="0ba1f-118">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="0ba1f-119">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="0ba1f-119">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)

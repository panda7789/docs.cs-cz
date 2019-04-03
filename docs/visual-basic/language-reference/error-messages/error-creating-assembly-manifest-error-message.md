---
title: 'Při vytváření manifestu sestavení došlo k chybě: <error message>'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: f9d7867157b65d746809d9b2f50797285d7fcd9c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831956"
---
# <a name="error-creating-assembly-manifest-error-message"></a><span data-ttu-id="cd40e-102">Chyba při vytváření manifestu sestavení: \<chybová zpráva ></span><span class="sxs-lookup"><span data-stu-id="cd40e-102">Error creating assembly manifest: \<error message></span></span>
<span data-ttu-id="cd40e-103">Kompilátor jazyka Visual Basic volá Assembly Linker (Al.exe, označované také jako Alink) ke generování sestavení s manifestem.</span><span class="sxs-lookup"><span data-stu-id="cd40e-103">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="cd40e-104">Linker ohlásilo chybu ve fázi předběžného emisí vytváření sestavení.</span><span class="sxs-lookup"><span data-stu-id="cd40e-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="cd40e-105">Tato situace může nastat, pokud dochází k problémům s souboru klíče nebo kontejneru klíčů určeném.</span><span class="sxs-lookup"><span data-stu-id="cd40e-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="cd40e-106">Chcete-li plně podepsat sestavení, je nutné zadat platný soubor s klíčem, který obsahuje informace o veřejných a privátních klíčů.</span><span class="sxs-lookup"><span data-stu-id="cd40e-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="cd40e-107">Zpoždění podepsání sestavení, musíte vybrat **zpoždění podepsání** zaškrtněte políčko a zadejte platný soubor s klíčem, který obsahuje informace o informace o veřejném klíči.</span><span class="sxs-lookup"><span data-stu-id="cd40e-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="cd40e-108">Privátní klíč není nezbytné, pokud sestavení se zpožděným podpisem.</span><span class="sxs-lookup"><span data-stu-id="cd40e-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="cd40e-109">Další informace najdete v tématu [jak: Podepsání sestavení silným názvem](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="cd40e-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
 <span data-ttu-id="cd40e-110">**ID chyby:** BC30140</span><span class="sxs-lookup"><span data-stu-id="cd40e-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cd40e-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="cd40e-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="cd40e-112">Zkontrolujte v uvozovkách chybovou zprávu a najdete v tématu [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="cd40e-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="cd40e-113">pro další vysvětlení chyby AL1019 a poradenství</span><span class="sxs-lookup"><span data-stu-id="cd40e-113">for error AL1019 further explanation and advice</span></span>  
  
2.  <span data-ttu-id="cd40e-114">Pokud potíže potrvají, shromážděte informace o okolnostech a upozornit Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="cd40e-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd40e-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd40e-115">See also</span></span>

- [<span data-ttu-id="cd40e-116">Postupy: Podepsání sestavení silným názvem</span><span class="sxs-lookup"><span data-stu-id="cd40e-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- [<span data-ttu-id="cd40e-117">Stránka Podepisování, Návrhář projektu</span><span class="sxs-lookup"><span data-stu-id="cd40e-117">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
- [<span data-ttu-id="cd40e-118">Al.exe</span><span class="sxs-lookup"><span data-stu-id="cd40e-118">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="cd40e-119">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="cd40e-119">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)

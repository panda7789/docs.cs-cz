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
ms.openlocfilehash: d846ef88f0c36b49e79b9d11252fcef419dfa0ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a><span data-ttu-id="b8c32-102">Chyba při vytváření sestavení manifestu: &lt;chybová zpráva&gt;</span><span class="sxs-lookup"><span data-stu-id="b8c32-102">Error creating assembly manifest: &lt;error message&gt;</span></span>
<span data-ttu-id="b8c32-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilátoru volá Linker sestavení (Al.exe, také známé jako Alink) ke generování sestavení s manifestu.</span><span class="sxs-lookup"><span data-stu-id="b8c32-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="b8c32-104">Linkeru ohlásilo chybu ve fázi před emisí vytváření sestavení.</span><span class="sxs-lookup"><span data-stu-id="b8c32-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="b8c32-105">Tato situace může nastat, pokud dochází k problémům s souboru klíče nebo klíče zadaný kontejner.</span><span class="sxs-lookup"><span data-stu-id="b8c32-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="b8c32-106">Chcete-li plně podepsání sestavení, je nutné zadat platný soubor klíče, který obsahuje informace o veřejné a soukromé klíče.</span><span class="sxs-lookup"><span data-stu-id="b8c32-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="b8c32-107">Zpoždění podepsání sestavení, musíte vybrat **zpoždění podepsání** zaškrtněte políčko a zadejte platný soubor klíče, který obsahuje informace o informace o veřejném klíči.</span><span class="sxs-lookup"><span data-stu-id="b8c32-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="b8c32-108">Privátní klíč není nutné, pokud je sestavení podepsané zpoždění.</span><span class="sxs-lookup"><span data-stu-id="b8c32-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="b8c32-109">Další informace najdete v tématu [postupy: podepsání sestavení (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).</span><span class="sxs-lookup"><span data-stu-id="b8c32-109">For more information, see [How to: Sign an Assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).</span></span>  
  
 <span data-ttu-id="b8c32-110">**ID chyby:** BC30140</span><span class="sxs-lookup"><span data-stu-id="b8c32-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b8c32-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b8c32-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="b8c32-112">Prověřením uvozovkách chybové zprávy a podívejte se téma [Nástroj Al.exe chyby a upozornění](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) došlo k chybě AL1019 další vysvětlení a Rady, jak</span><span class="sxs-lookup"><span data-stu-id="b8c32-112">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for error AL1019 further explanation and advice</span></span>  
  
2.  <span data-ttu-id="b8c32-113">Pokud potíže potrvají, shromažďovat informace o okolnostech a upozornění služby Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="b8c32-113">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8c32-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8c32-114">See Also</span></span>  
 [<span data-ttu-id="b8c32-115">Postupy: podepsání sestavení (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="b8c32-115">How to: Sign an Assembly (Visual Studio)</span></span>](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564)  
 [<span data-ttu-id="b8c32-116">Stránka podepisování, Návrhář projektu</span><span class="sxs-lookup"><span data-stu-id="b8c32-116">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)  
 [<span data-ttu-id="b8c32-117">Al.exe (Linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="b8c32-117">Al.exe (Assembly Linker)</span></span>](https://msdn.microsoft.com/library/c405shex)  
 [<span data-ttu-id="b8c32-118">Al.exe nástroj chyby a upozornění</span><span class="sxs-lookup"><span data-stu-id="b8c32-118">Al.exe Tool Errors and Warnings</span></span>](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [<span data-ttu-id="b8c32-119">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="b8c32-119">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)

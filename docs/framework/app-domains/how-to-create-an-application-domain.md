---
title: 'Postupy: Vytvoření domény aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f42f85adf3e9b0874df6c0360bea25b07facc0d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053149"
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="470e0-102">Postupy: Vytvoření domény aplikace</span><span class="sxs-lookup"><span data-stu-id="470e0-102">How to: Create an Application Domain</span></span>
<span data-ttu-id="470e0-103">Hostitel společného jazykového modulu runtime vytváří domény aplikace automaticky v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="470e0-103">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="470e0-104">Můžete však vytvořit vlastní domény aplikace a načíst je do těchto sestavení, která chcete spravovat osobně.</span><span class="sxs-lookup"><span data-stu-id="470e0-104">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="470e0-105">Můžete také vytvořit domény aplikace, ze kterých můžete spustit kód.</span><span class="sxs-lookup"><span data-stu-id="470e0-105">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="470e0-106">Novou doménu aplikace vytvoříte pomocí jedné z přetížených metod **CreateDomain –** ve <xref:System.AppDomain?displayProperty=nameWithType> třídě.</span><span class="sxs-lookup"><span data-stu-id="470e0-106">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="470e0-107">Doméně aplikace můžete přidělit název a odkazovat na ni tímto názvem.</span><span class="sxs-lookup"><span data-stu-id="470e0-107">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="470e0-108">Následující příklad vytvoří novou doménu aplikace, přiřadí jí název `MyDomain`a potom vypíše název domény hostitele a nově vytvořenou podřízenou doménu aplikace do konzoly.</span><span class="sxs-lookup"><span data-stu-id="470e0-108">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="470e0-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="470e0-109">Example</span></span>  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="470e0-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="470e0-110">See also</span></span>

- [<span data-ttu-id="470e0-111">Programování s aplikačními doménami</span><span class="sxs-lookup"><span data-stu-id="470e0-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="470e0-112">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="470e0-112">Using Application Domains</span></span>](use.md)

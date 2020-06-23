---
title: 'Postupy: Vytvoření domény aplikace'
description: Přečtěte si, jak vytvořit doménu aplikace v rozhraní .NET. Můžete vytvořit doménu aplikace pro načtení sestavení pro správu osobně nebo vytvořit kód pro spuštění kódu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
ms.openlocfilehash: 8e44e682f64854dbc0181b26f6ed3fa2905b7814
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104810"
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="28ee3-104">Postupy: Vytvoření domény aplikace</span><span class="sxs-lookup"><span data-stu-id="28ee3-104">How to: Create an Application Domain</span></span>
<span data-ttu-id="28ee3-105">Hostitel společného jazykového modulu runtime vytváří domény aplikace automaticky v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="28ee3-105">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="28ee3-106">Můžete však vytvořit vlastní domény aplikace a načíst je do těchto sestavení, která chcete spravovat osobně.</span><span class="sxs-lookup"><span data-stu-id="28ee3-106">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="28ee3-107">Můžete také vytvořit domény aplikace, ze kterých můžete spustit kód.</span><span class="sxs-lookup"><span data-stu-id="28ee3-107">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="28ee3-108">Novou doménu aplikace vytvoříte pomocí jedné z přetížených metod **CreateDomain –** ve <xref:System.AppDomain?displayProperty=nameWithType> třídě.</span><span class="sxs-lookup"><span data-stu-id="28ee3-108">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="28ee3-109">Doméně aplikace můžete přidělit název a odkazovat na ni tímto názvem.</span><span class="sxs-lookup"><span data-stu-id="28ee3-109">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="28ee3-110">Následující příklad vytvoří novou doménu aplikace, přiřadí jí název `MyDomain` a potom vypíše název domény hostitele a nově vytvořenou podřízenou doménu aplikace do konzoly.</span><span class="sxs-lookup"><span data-stu-id="28ee3-110">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28ee3-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="28ee3-111">Example</span></span>  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="28ee3-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="28ee3-112">See also</span></span>

- [<span data-ttu-id="28ee3-113">Programování s aplikačními doménami</span><span class="sxs-lookup"><span data-stu-id="28ee3-113">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="28ee3-114">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="28ee3-114">Using Application Domains</span></span>](use.md)

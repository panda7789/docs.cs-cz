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
ms.openlocfilehash: ff85f5737babb73d87f4918ca0f4981263f7dadc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166748"
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="bcad9-102">Postupy: Vytvoření domény aplikace</span><span class="sxs-lookup"><span data-stu-id="bcad9-102">How to: Create an Application Domain</span></span>
<span data-ttu-id="bcad9-103">Hostitel common language runtime automaticky vytvoří aplikační domény v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="bcad9-103">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="bcad9-104">Můžete však vytvořit vlastní domény aplikace a načíst do nich tato sestavení, které chcete spravovat sami.</span><span class="sxs-lookup"><span data-stu-id="bcad9-104">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="bcad9-105">Můžete také vytvořit aplikační domény, ze kterých je kód spuštěn.</span><span class="sxs-lookup"><span data-stu-id="bcad9-105">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="bcad9-106">Vytvořit novou doménu aplikace pomocí jedné z přetížené **CreateDomain** metody v <xref:System.AppDomain?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="bcad9-106">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="bcad9-107">Můžete pojmenujte doménu aplikace a na něj odkazovat s tímto názvem.</span><span class="sxs-lookup"><span data-stu-id="bcad9-107">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="bcad9-108">Následující příklad vytvoří novou doménu aplikace, přiřadí název `MyDomain`a potom vypíše název domény hostitele a nově vytvořený podřízené domény aplikace do konzoly.</span><span class="sxs-lookup"><span data-stu-id="bcad9-108">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcad9-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="bcad9-109">Example</span></span>  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="bcad9-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bcad9-110">See also</span></span>

- [<span data-ttu-id="bcad9-111">Programování pomocí domén aplikace</span><span class="sxs-lookup"><span data-stu-id="bcad9-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="bcad9-112">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="bcad9-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)

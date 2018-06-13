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
ms.openlocfilehash: c579c97e273e7d3e149e04f7aa7670313663b617
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751767"
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="7265d-102">Postupy: Vytvoření domény aplikace</span><span class="sxs-lookup"><span data-stu-id="7265d-102">How to: Create an Application Domain</span></span>
<span data-ttu-id="7265d-103">Běžné hostitel běhu jazyka automaticky vytvoří aplikační domény v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="7265d-103">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="7265d-104">Můžete však vytvořit vlastní domény aplikace a načíst do nich ty sestavení, které chcete spravovat osobní.</span><span class="sxs-lookup"><span data-stu-id="7265d-104">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="7265d-105">Můžete také vytvořit aplikační domény, ze kterých je kód spuštěn.</span><span class="sxs-lookup"><span data-stu-id="7265d-105">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="7265d-106">Vytvořit novou doménu aplikace pomocí jednoho z přetížené **CreateDomain** metody v <xref:System.AppDomain?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="7265d-106">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="7265d-107">Můžete pojmenujte doménu aplikace a odkaz s tímto názvem.</span><span class="sxs-lookup"><span data-stu-id="7265d-107">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="7265d-108">Následující příklad vytvoří novou doménu aplikace a přiřadí ji název `MyDomain`a potom zobrazí název domény hostitele a nově vytvořené podřízené domény aplikace do konzoly.</span><span class="sxs-lookup"><span data-stu-id="7265d-108">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7265d-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="7265d-109">Example</span></span>  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7265d-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="7265d-110">See Also</span></span>  
 [<span data-ttu-id="7265d-111">Programování s doménami aplikací</span><span class="sxs-lookup"><span data-stu-id="7265d-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)  
 [<span data-ttu-id="7265d-112">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="7265d-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)

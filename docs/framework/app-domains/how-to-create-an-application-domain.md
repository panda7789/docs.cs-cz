---
title: "Postupy: Vytvoření domény aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cdbab5e43d2af7608c4d8322eb071baf591e18d5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="66b90-102">Postupy: Vytvoření domény aplikace</span><span class="sxs-lookup"><span data-stu-id="66b90-102">How to: Create an Application Domain</span></span>
<span data-ttu-id="66b90-103">Běžné hostitel běhu jazyka automaticky vytvoří aplikační domény v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="66b90-103">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="66b90-104">Můžete však vytvořit vlastní domény aplikace a načíst do nich ty sestavení, které chcete spravovat osobní.</span><span class="sxs-lookup"><span data-stu-id="66b90-104">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="66b90-105">Můžete také vytvořit aplikační domény, ze kterých je kód spuštěn.</span><span class="sxs-lookup"><span data-stu-id="66b90-105">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="66b90-106">Vytvořit novou doménu aplikace pomocí jednoho z přetížené **CreateDomain** metody v <xref:System.AppDomain?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="66b90-106">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="66b90-107">Můžete pojmenujte doménu aplikace a odkaz s tímto názvem.</span><span class="sxs-lookup"><span data-stu-id="66b90-107">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="66b90-108">Následující příklad vytvoří novou doménu aplikace a přiřadí ji název `MyDomain`a potom zobrazí název domény hostitele a nově vytvořené podřízené domény aplikace do konzoly.</span><span class="sxs-lookup"><span data-stu-id="66b90-108">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66b90-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="66b90-109">Example</span></span>  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="66b90-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="66b90-110">See Also</span></span>  
 [<span data-ttu-id="66b90-111">Programování s doménami aplikací</span><span class="sxs-lookup"><span data-stu-id="66b90-111">Programming with Application Domains</span></span>](http://msdn.microsoft.com/library/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [<span data-ttu-id="66b90-112">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="66b90-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)

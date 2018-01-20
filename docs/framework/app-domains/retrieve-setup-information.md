---
title: "Načítání informací nastavení z domény aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- AppDomainSetup object
- retrieving setup information
- application domains, retrieving setup information
ms.assetid: 5cdb12ae-1e37-4a62-8ec7-93d6dcc6e8d9
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eeb0921eefc7ac157b94f3b6de43460cdfd42ba8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="retrieving-setup-information-from-an-application-domain"></a><span data-ttu-id="f1630-102">Načítání informací nastavení z domény aplikace</span><span class="sxs-lookup"><span data-stu-id="f1630-102">Retrieving Setup Information from an Application Domain</span></span>
<span data-ttu-id="f1630-103">Každá instance domény aplikace se skládá z obě vlastnosti a <xref:System.AppDomainSetup> informace.</span><span class="sxs-lookup"><span data-stu-id="f1630-103">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="f1630-104">Informace o instalaci můžete načíst z domény aplikace pomocí <xref:System.AppDomain?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="f1630-104">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="f1630-105">Tato třída poskytuje několik členů, kteří získávají informace o konfiguraci o domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1630-105">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="f1630-106">Můžete taky zadat dotaz **AppDomainSetup** objekt pro doménu aplikace pro získání informací o nastavení, který byl předán do domény, pokud byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="f1630-106">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="f1630-107">Následující příklad vytvoří novou doménu aplikace a potom zobrazí několik hodnoty členů do konzoly.</span><span class="sxs-lookup"><span data-stu-id="f1630-107">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 <span data-ttu-id="f1630-108">Následující příklad sady a potom načte, informace o nastavení domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1630-108">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="f1630-109">Všimněte si, že `AppDomain.SetupInformation.ApplicationBase` získá informace o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="f1630-109">Note that `AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f1630-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1630-110">See Also</span></span>  
 [<span data-ttu-id="f1630-111">Programování s doménami aplikací</span><span class="sxs-lookup"><span data-stu-id="f1630-111">Programming with Application Domains</span></span>](http://msdn.microsoft.com/library/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [<span data-ttu-id="f1630-112">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="f1630-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)

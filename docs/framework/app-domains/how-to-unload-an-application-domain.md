---
title: "Postupy: Uvolnění domény aplikace"
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
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 58fd1477715bafa4e3455a3e476acbae3a098dbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="01f07-102">Postupy: Uvolnění domény aplikace</span><span class="sxs-lookup"><span data-stu-id="01f07-102">How to: Unload an Application Domain</span></span>
<span data-ttu-id="01f07-103">Po dokončení používání domény aplikace uvolnit pomocí <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="01f07-103">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="01f07-104">**Uvolnění** metoda řádně vypne zadanou doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="01f07-104">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="01f07-105">Během procesu uvolnění žádné nové vláken můžete přístup k doméně aplikace a všechny domény – konkrétní datové struktury aplikace jsou uvolněny.</span><span class="sxs-lookup"><span data-stu-id="01f07-105">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="01f07-106">Sestavení načtená do domény aplikace se odeberou a již nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="01f07-106">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="01f07-107">Pokud je sestavení v doméně aplikace domény jazykově neutrální, zůstane data pro sestavení v paměti, dokud celý proces je vypnutý.</span><span class="sxs-lookup"><span data-stu-id="01f07-107">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="01f07-108">Neexistuje žádný mechanismus k uvolnění domény jazykově neutrální sestavení než vypíná celý proces.</span><span class="sxs-lookup"><span data-stu-id="01f07-108">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="01f07-109">Existují situacích, kdy požadavek na uvolnění domény aplikace nefunguje a výsledkem <xref:System.CannotUnloadAppDomainException>.</span><span class="sxs-lookup"><span data-stu-id="01f07-109">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="01f07-110">Následující příklad vytvoří novou doménu aplikace nazvanou `MyDomain`, vytiskne některé informace do konzoly a poté uvolní doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="01f07-110">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="01f07-111">Všimněte si, že kód pak pokusí vytisknout popisný název domény odpojen aplikaci do konzoly.</span><span class="sxs-lookup"><span data-stu-id="01f07-111">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="01f07-112">Tato akce vygeneruje výjimku, která se zpracovává souborem try/catch – příkazy na konci tohoto programu.</span><span class="sxs-lookup"><span data-stu-id="01f07-112">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01f07-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="01f07-113">Example</span></span>  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="01f07-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="01f07-114">See Also</span></span>  
 [<span data-ttu-id="01f07-115">Programování s doménami aplikací</span><span class="sxs-lookup"><span data-stu-id="01f07-115">Programming with Application Domains</span></span>](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [<span data-ttu-id="01f07-116">Postupy: vytvoření domény aplikace</span><span class="sxs-lookup"><span data-stu-id="01f07-116">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 [<span data-ttu-id="01f07-117">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="01f07-117">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)

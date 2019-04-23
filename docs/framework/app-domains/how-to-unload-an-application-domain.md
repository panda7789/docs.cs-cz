---
title: 'Postupy: Uvolnění domény aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3011bd0327440cd04d5eccf5f88c036ddd76267
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212177"
---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="31604-102">Postupy: Uvolnění domény aplikace</span><span class="sxs-lookup"><span data-stu-id="31604-102">How to: Unload an Application Domain</span></span>
<span data-ttu-id="31604-103">Po dokončení používání domény aplikace, odinstalovat ji pomocí <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="31604-103">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="31604-104">**Uvolnění** metoda řádně ukončí zadanou doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="31604-104">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="31604-105">Během procesu uvolnění žádná nová vlákna můžete přístup k doméně aplikace a všechny aplikace domény specifické datové struktury jsou uvolněny.</span><span class="sxs-lookup"><span data-stu-id="31604-105">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="31604-106">Sestavení načtena do domény aplikace jsou odebrány a nadále již nebudou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="31604-106">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="31604-107">Pokud je sestavení v aplikační doméně doménově neutrální, zůstávají data pro sestavení v paměti, dokud nebude ukončen celý proces.</span><span class="sxs-lookup"><span data-stu-id="31604-107">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="31604-108">Neexistuje žádný mechanismus uvolnění sestavení jako doménově neutrální než celý proces ukončen.</span><span class="sxs-lookup"><span data-stu-id="31604-108">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="31604-109">Existují situace, kdy požadavek na uvolnění domény aplikace nefunguje, výsledkem <xref:System.CannotUnloadAppDomainException>.</span><span class="sxs-lookup"><span data-stu-id="31604-109">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="31604-110">Následující příklad vytvoří novou doménu aplikace volá `MyDomain`, vypíše některé informace o do konzoly a potom uvolnění domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="31604-110">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="31604-111">Všimněte si, že kód poté se pokusí tisk popisný název uvolněné doméně aplikace do konzoly.</span><span class="sxs-lookup"><span data-stu-id="31604-111">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="31604-112">Tato akce vygeneruje výjimku, která zpracovává příkazy try/catch – na konci programu.</span><span class="sxs-lookup"><span data-stu-id="31604-112">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31604-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="31604-113">Example</span></span>  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="31604-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31604-114">See also</span></span>

- [<span data-ttu-id="31604-115">Programování pomocí domén aplikace</span><span class="sxs-lookup"><span data-stu-id="31604-115">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="31604-116">Postupy: Vytvoření domény aplikace</span><span class="sxs-lookup"><span data-stu-id="31604-116">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)
- [<span data-ttu-id="31604-117">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="31604-117">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)

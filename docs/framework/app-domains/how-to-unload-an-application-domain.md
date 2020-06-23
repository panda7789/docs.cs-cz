---
title: 'Postupy: Uvolnění domény aplikace'
description: Přečtěte si, jak uvolnit doménu aplikace v rozhraní .NET pomocí metody AppDomain. Unload k bezproblémovému vypnutí zadané domény aplikace.
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
ms.openlocfilehash: b64a9553f63aa4a8deb57f23a97fa464edd64fee
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104682"
---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="9f2df-103">Postupy: Uvolnění domény aplikace</span><span class="sxs-lookup"><span data-stu-id="9f2df-103">How to: Unload an Application Domain</span></span>
<span data-ttu-id="9f2df-104">Po dokončení používání domény aplikace ji uvolněte pomocí <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="9f2df-104">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9f2df-105">Metoda **Unload** řádně vypne zadanou doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="9f2df-105">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="9f2df-106">Během procesu uvolňování nemohou žádná nová vlákna přistupovat k doméně aplikace a jsou uvolněny všechny datové struktury specifické pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="9f2df-106">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="9f2df-107">Sestavení načítaná do domény aplikace jsou odebrána a již nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9f2df-107">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="9f2df-108">Pokud je sestavení v doméně aplikace neutrální vzhledem k doméně, data pro sestavení zůstanou v paměti, dokud se celý proces nevypne.</span><span class="sxs-lookup"><span data-stu-id="9f2df-108">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="9f2df-109">Neexistuje žádný mechanismus pro uvolnění mezidoménově neutrálních sestavení než vypnutí celého procesu.</span><span class="sxs-lookup"><span data-stu-id="9f2df-109">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="9f2df-110">Existují situace, kdy požadavek na uvolnění domény aplikace nefunguje a má za následek <xref:System.CannotUnloadAppDomainException> .</span><span class="sxs-lookup"><span data-stu-id="9f2df-110">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="9f2df-111">Následující příklad vytvoří novou doménu aplikace s názvem `MyDomain` , vytiskne některé informace do konzoly a poté uvolní doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="9f2df-111">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="9f2df-112">Všimněte si, že se kód pak pokusí vytisknout popisný název uvolněné domény aplikace do konzoly.</span><span class="sxs-lookup"><span data-stu-id="9f2df-112">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="9f2df-113">Tato akce generuje výjimku, která je zpracována příkazy try/catch na konci programu.</span><span class="sxs-lookup"><span data-stu-id="9f2df-113">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f2df-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f2df-114">Example</span></span>  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="9f2df-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f2df-115">See also</span></span>

- [<span data-ttu-id="9f2df-116">Programování s aplikačními doménami</span><span class="sxs-lookup"><span data-stu-id="9f2df-116">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="9f2df-117">Postupy: Vytvoření domény aplikace</span><span class="sxs-lookup"><span data-stu-id="9f2df-117">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)
- [<span data-ttu-id="9f2df-118">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="9f2df-118">Using Application Domains</span></span>](use.md)

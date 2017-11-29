---
title: "Zabezpečení aplikací ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 143447020f41368a3553a0c8cda78e80806b75ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="6abf2-102">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6abf2-102">Securing ADO.NET Applications</span></span>
<span data-ttu-id="6abf2-103">Zápis zabezpečené aplikace ADO.NET zahrnuje více než zabraňující běžné kódování nástrahy například není ověřování uživatelského vstupu.</span><span class="sxs-lookup"><span data-stu-id="6abf2-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="6abf2-104">Aplikace, která přistupuje k datům má mnoho potenciální body selhání, které může útočník zneužít k načtení, manipulaci nebo destroy citlivá data.</span><span class="sxs-lookup"><span data-stu-id="6abf2-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="6abf2-105">Proto je důležité si uvědomit, všechny aspekty zabezpečení, z procesu modelování během fáze návrhu vaší aplikace, jeho případné nasazení a následné údržbě hrozeb.</span><span class="sxs-lookup"><span data-stu-id="6abf2-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
 <span data-ttu-id="6abf2-106">Rozhraní .NET Framework poskytuje mnoho užitečných tříd, služby a nástroje pro zabezpečení a správě databázových aplikací.</span><span class="sxs-lookup"><span data-stu-id="6abf2-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="6abf2-107">Modul CLR (CLR) poskytuje prostředí pro kód pro spuštění, se zabezpečení přístupu kódu (CAS) dále omezit oprávnění spravovaného kódu a bezpečnost typů.</span><span class="sxs-lookup"><span data-stu-id="6abf2-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="6abf2-108">Následující data zabezpečeného přístupu kódování postupy omezuje škody, které může být si způsobilo potenciálním útočníkům.</span><span class="sxs-lookup"><span data-stu-id="6abf2-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
 <span data-ttu-id="6abf2-109">Psaní kódu zabezpečené není chránit proti samo celistvosti při práci s nespravovaných prostředků, jako jsou třeba databáze.</span><span class="sxs-lookup"><span data-stu-id="6abf2-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="6abf2-110">Většina databáze serveru, jako je SQL Server, mají vlastní systémy zabezpečení, které vylepšují zabezpečení, když je implementovaná správně.</span><span class="sxs-lookup"><span data-stu-id="6abf2-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="6abf2-111">Ale i k datovému zdroji prostřednictvím systému robustní zabezpečení můžete obětí při útoku, pokud není správně nakonfigurován.</span><span class="sxs-lookup"><span data-stu-id="6abf2-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6abf2-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6abf2-112">In This Section</span></span>  
 [<span data-ttu-id="6abf2-113">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6abf2-113">Security Overview</span></span>](../../../../docs/framework/data/adonet/security-overview.md)  
 <span data-ttu-id="6abf2-114">Poskytuje doporučení pro navrhování zabezpečených aplikací ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="6abf2-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="6abf2-115">Zabezpečení přístupu k datům</span><span class="sxs-lookup"><span data-stu-id="6abf2-115">Secure Data Access</span></span>](../../../../docs/framework/data/adonet/secure-data-access.md)  
 <span data-ttu-id="6abf2-116">Popisuje, jak pracovat s daty ze zdroje zabezpečená data.</span><span class="sxs-lookup"><span data-stu-id="6abf2-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="6abf2-117">Zabezpečení klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="6abf2-117">Secure Client Applications</span></span>](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 <span data-ttu-id="6abf2-118">Popisuje důležité informace o zabezpečení pro klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="6abf2-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="6abf2-119">Zabezpečení přístupu kódu a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6abf2-119">Code Access Security and ADO.NET</span></span>](../../../../docs/framework/data/adonet/code-access-security.md)  
 <span data-ttu-id="6abf2-120">Popisuje, jak certifikační Autority může pomoct chránit kód ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="6abf2-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="6abf2-121">Také popisuje, jak pracovat s částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="6abf2-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="6abf2-122">Ochrana osobních údajů a zabezpečení dat</span><span class="sxs-lookup"><span data-stu-id="6abf2-122">Privacy and Data Security</span></span>](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 <span data-ttu-id="6abf2-123">Popisuje možnosti šifrování pro technologii ADO.NET aplikace.</span><span class="sxs-lookup"><span data-stu-id="6abf2-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6abf2-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="6abf2-124">Related Sections</span></span>  
 [<span data-ttu-id="6abf2-125">Zabezpečení SQL serveru</span><span class="sxs-lookup"><span data-stu-id="6abf2-125">SQL Server Security</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="6abf2-126">Popisuje funkce zabezpečení systému SQL Server z hlediska pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="6abf2-126">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="6abf2-127">Aspekty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6abf2-127">Security Considerations</span></span>](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 <span data-ttu-id="6abf2-128">Popisuje zabezpečení pro aplikace rozhraní Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="6abf2-128">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="6abf2-129">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6abf2-129">Security</span></span>](../../../../docs/standard/security/index.md)  
 <span data-ttu-id="6abf2-130">Obsahuje odkazy na témata s popisem všechny aspekty zabezpečení v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6abf2-130">Contains links to topics describing all aspects of security in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="6abf2-131">Nástroje zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6abf2-131">Security Tools</span></span>](http://msdn.microsoft.com/en-us/2a3eb98a-2de6-4fba-b41c-01a74d354c11)  
 <span data-ttu-id="6abf2-132">Rozhraní .NET framework – nástroje pro zabezpečení a správu zásad zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6abf2-132">.NET Framework tools for securing and administering security policy.</span></span>  
  
 [<span data-ttu-id="6abf2-133">Prostředky pro vytvoření zabezpečených aplikací</span><span class="sxs-lookup"><span data-stu-id="6abf2-133">Resources for Creating Secure Applications</span></span>](http://msdn.microsoft.com/en-us/0ebf5f69-76f2-498a-a2df-83cf3443e132)  
 <span data-ttu-id="6abf2-134">Poskytuje odkazy na témata pro vytváření zabezpečených aplikací.</span><span class="sxs-lookup"><span data-stu-id="6abf2-134">Provides links to topics for creating secure applications.</span></span>  
  
 [<span data-ttu-id="6abf2-135">Bibliografie k zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6abf2-135">Security Bibliography</span></span>](/visualstudio/ide/security-bibliography)  
 <span data-ttu-id="6abf2-136">Obsahuje odkazy na externí zdroje, které jsou k dispozici online a v tisku.</span><span class="sxs-lookup"><span data-stu-id="6abf2-136">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6abf2-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="6abf2-137">See Also</span></span>  
 [<span data-ttu-id="6abf2-138">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6abf2-138">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="6abf2-139">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="6abf2-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

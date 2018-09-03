---
title: Zabezpečení aplikací ADO.NET
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: e5b99621989e9f14c6c734a497f210780f3c7e57
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481075"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="7c9d9-102">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7c9d9-102">Securing ADO.NET Applications</span></span>
<span data-ttu-id="7c9d9-103">Vytváření zabezpečených aplikací ADO.NET zahrnuje více než jak se vyhnout běžným nástrahám psaní kódu, jako je například není ověřování uživatelského vstupu.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="7c9d9-104">Aplikace, která přistupuje k datům má mnoho potenciálních bodů selhání, které může útočník zneužít k načtení, manipulaci nebo zničit citlivá data.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="7c9d9-105">Proto je důležité Porozumějte všem jejich aspektům zabezpečení z procesu před internetovými útoky modelování během fáze návrhu vaší aplikace, pro jeho nasazení konečné a průběžnou péči.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
 <span data-ttu-id="7c9d9-106">Rozhraní .NET Framework poskytuje mnoho užitečných tříd, služby a nástroje pro zabezpečení a správu databázových aplikací.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="7c9d9-107">Common language runtime (CLR) poskytuje prostředí typově bezpečný kód ke spuštění, se zabezpečení přístupu kódu (CAS) pro další omezení oprávnění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="7c9d9-108">Po zabezpečení dat omezuje přístup kódování škody, které může být způsobené potenciální útočníky.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
 <span data-ttu-id="7c9d9-109">Psaní bezpečného kódu není pomáhalo chránit před poškozují bezpečnostní díry při práci s nespravované prostředky, jako jsou databáze.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="7c9d9-110">Většina databází serveru, jako je SQL Server, mají vlastní systémy zabezpečení, které umožňuje zvýšit zabezpečení při správné implementaci.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="7c9d9-111">Ale i datovému zdroji prostřednictvím robustní zabezpečení systému můžete obětí útoku, pokud není správně nakonfigurován.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c9d9-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7c9d9-112">In This Section</span></span>  
 [<span data-ttu-id="7c9d9-113">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7c9d9-113">Security Overview</span></span>](../../../../docs/framework/data/adonet/security-overview.md)  
 <span data-ttu-id="7c9d9-114">Poskytuje doporučení pro návrh zabezpečených aplikací ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="7c9d9-115">Zabezpečený přístup k datům</span><span class="sxs-lookup"><span data-stu-id="7c9d9-115">Secure Data Access</span></span>](../../../../docs/framework/data/adonet/secure-data-access.md)  
 <span data-ttu-id="7c9d9-116">Popisuje, jak pracovat s daty ze zdroje zabezpečeným datům.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="7c9d9-117">Zabezpečené klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="7c9d9-117">Secure Client Applications</span></span>](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 <span data-ttu-id="7c9d9-118">Popisuje aspekty zabezpečení pro klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="7c9d9-119">Zabezpečení přístupu ke kódu a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7c9d9-119">Code Access Security and ADO.NET</span></span>](../../../../docs/framework/data/adonet/code-access-security.md)  
 <span data-ttu-id="7c9d9-120">Popisuje, jak certifikačních Autorit může pomoci chránit kódu ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="7c9d9-121">Také popisuje, jak pracovat s částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="7c9d9-122">Ochrana osobních údajů a zabezpečení dat</span><span class="sxs-lookup"><span data-stu-id="7c9d9-122">Privacy and Data Security</span></span>](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 <span data-ttu-id="7c9d9-123">Popisuje možnosti šifrování pro aplikace, ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7c9d9-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="7c9d9-124">Related Sections</span></span>  
 [<span data-ttu-id="7c9d9-125">SQL Server – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7c9d9-125">SQL Server Security</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="7c9d9-126">Popisuje funkce zabezpečení produktu SQL Server z pohledu vývojáře.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-126">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="7c9d9-127">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7c9d9-127">Security Considerations</span></span>](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 <span data-ttu-id="7c9d9-128">Popisuje zabezpečení pro aplikace Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-128">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="7c9d9-129">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7c9d9-129">Security</span></span>](../../../../docs/standard/security/index.md)  
 <span data-ttu-id="7c9d9-130">Obsahuje odkazy na témata popisující všech aspektů zabezpečení v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-130">Contains links to topics describing all aspects of security in .NET.</span></span>  
  
 [<span data-ttu-id="7c9d9-131">Nástroje zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7c9d9-131">Security Tools</span></span>](https://msdn.microsoft.com/library/2a3eb98a-2de6-4fba-b41c-01a74d354c11)  
 <span data-ttu-id="7c9d9-132">Rozhraní .NET framework – nástroje pro zabezpečení a správě zásad zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-132">.NET Framework tools for securing and administering security policy.</span></span>  
  
 [<span data-ttu-id="7c9d9-133">Prostředky pro vytváření zabezpečených aplikací</span><span class="sxs-lookup"><span data-stu-id="7c9d9-133">Resources for Creating Secure Applications</span></span>](https://msdn.microsoft.com/library/0ebf5f69-76f2-498a-a2df-83cf3443e132)  
 <span data-ttu-id="7c9d9-134">Obsahuje odkazy na témata pro vytváření zabezpečených aplikací.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-134">Provides links to topics for creating secure applications.</span></span>  
  
 [<span data-ttu-id="7c9d9-135">Bibliografie k zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7c9d9-135">Security Bibliography</span></span>](/visualstudio/ide/security-bibliography)  
 <span data-ttu-id="7c9d9-136">Obsahuje odkazy na externí prostředky, které jsou k dispozici online a v tisku.</span><span class="sxs-lookup"><span data-stu-id="7c9d9-136">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c9d9-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c9d9-137">See Also</span></span>  
 [<span data-ttu-id="7c9d9-138">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7c9d9-138">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="7c9d9-139">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="7c9d9-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

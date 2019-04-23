---
title: Zabezpečení aplikací ADO.NET
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: 32d3de15242aaf9cfacd9371289a5a0a675f884b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149380"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="c1812-102">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c1812-102">Securing ADO.NET Applications</span></span>
<span data-ttu-id="c1812-103">Vytváření zabezpečených aplikací ADO.NET zahrnuje více než jak se vyhnout běžným nástrahám psaní kódu, jako je například není ověřování uživatelského vstupu.</span><span class="sxs-lookup"><span data-stu-id="c1812-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="c1812-104">Aplikace, která přistupuje k datům má mnoho potenciálních bodů selhání, které může útočník zneužít k načtení, manipulaci nebo zničit citlivá data.</span><span class="sxs-lookup"><span data-stu-id="c1812-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="c1812-105">Proto je důležité Porozumějte všem jejich aspektům zabezpečení z procesu před internetovými útoky modelování během fáze návrhu vaší aplikace, pro jeho nasazení konečné a průběžnou péči.</span><span class="sxs-lookup"><span data-stu-id="c1812-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
 <span data-ttu-id="c1812-106">Rozhraní .NET Framework poskytuje mnoho užitečných tříd, služby a nástroje pro zabezpečení a správu databázových aplikací.</span><span class="sxs-lookup"><span data-stu-id="c1812-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="c1812-107">Common language runtime (CLR) poskytuje prostředí typově bezpečný kód ke spuštění, se zabezpečení přístupu kódu (CAS) pro další omezení oprávnění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="c1812-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="c1812-108">Po zabezpečení dat omezuje přístup kódování škody, které může být způsobené potenciální útočníky.</span><span class="sxs-lookup"><span data-stu-id="c1812-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
 <span data-ttu-id="c1812-109">Psaní bezpečného kódu není pomáhalo chránit před poškozují bezpečnostní díry při práci s nespravované prostředky, jako jsou databáze.</span><span class="sxs-lookup"><span data-stu-id="c1812-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="c1812-110">Většina databází serveru, jako je SQL Server, mají vlastní systémy zabezpečení, které umožňuje zvýšit zabezpečení při správné implementaci.</span><span class="sxs-lookup"><span data-stu-id="c1812-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="c1812-111">Ale i datovému zdroji prostřednictvím robustní zabezpečení systému můžete obětí útoku, pokud není správně nakonfigurován.</span><span class="sxs-lookup"><span data-stu-id="c1812-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1812-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c1812-112">In This Section</span></span>  
 [<span data-ttu-id="c1812-113">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c1812-113">Security Overview</span></span>](../../../../docs/framework/data/adonet/security-overview.md)  
 <span data-ttu-id="c1812-114">Poskytuje doporučení pro návrh zabezpečených aplikací ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="c1812-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="c1812-115">Zabezpečený přístup k datům</span><span class="sxs-lookup"><span data-stu-id="c1812-115">Secure Data Access</span></span>](../../../../docs/framework/data/adonet/secure-data-access.md)  
 <span data-ttu-id="c1812-116">Popisuje, jak pracovat s daty ze zdroje zabezpečeným datům.</span><span class="sxs-lookup"><span data-stu-id="c1812-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="c1812-117">Zabezpečené klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="c1812-117">Secure Client Applications</span></span>](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 <span data-ttu-id="c1812-118">Popisuje aspekty zabezpečení pro klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="c1812-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="c1812-119">Zabezpečení přístupu ke kódu a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c1812-119">Code Access Security and ADO.NET</span></span>](../../../../docs/framework/data/adonet/code-access-security.md)  
 <span data-ttu-id="c1812-120">Popisuje, jak certifikačních Autorit může pomoci chránit kódu ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="c1812-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="c1812-121">Také popisuje, jak pracovat s částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="c1812-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="c1812-122">Ochrana osobních údajů a zabezpečení dat</span><span class="sxs-lookup"><span data-stu-id="c1812-122">Privacy and Data Security</span></span>](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 <span data-ttu-id="c1812-123">Popisuje možnosti šifrování pro aplikace, ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="c1812-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c1812-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="c1812-124">Related Sections</span></span>  
 [<span data-ttu-id="c1812-125">SQL Server – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c1812-125">SQL Server Security</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="c1812-126">Popisuje funkce zabezpečení produktu SQL Server z pohledu vývojáře.</span><span class="sxs-lookup"><span data-stu-id="c1812-126">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="c1812-127">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c1812-127">Security Considerations</span></span>](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 <span data-ttu-id="c1812-128">Popisuje zabezpečení pro aplikace Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="c1812-128">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="c1812-129">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c1812-129">Security</span></span>](../../../../docs/standard/security/index.md)  
 <span data-ttu-id="c1812-130">Obsahuje odkazy na témata popisující všech aspektů zabezpečení v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="c1812-130">Contains links to topics describing all aspects of security in .NET.</span></span>  
  
 <span data-ttu-id="c1812-131">[Nástroje zabezpečení](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c1812-131">[Security Tools](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span></span>  
 <span data-ttu-id="c1812-132">Rozhraní .NET framework – nástroje pro zabezpečení a správě zásad zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c1812-132">.NET Framework tools for securing and administering security policy.</span></span>  
  
 <span data-ttu-id="c1812-133">[Prostředky pro vytváření zabezpečených aplikací](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c1812-133">[Resources for Creating Secure Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span></span>  
 <span data-ttu-id="c1812-134">Obsahuje odkazy na témata pro vytváření zabezpečených aplikací.</span><span class="sxs-lookup"><span data-stu-id="c1812-134">Provides links to topics for creating secure applications.</span></span>  
  
 [<span data-ttu-id="c1812-135">Bibliografie k zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c1812-135">Security Bibliography</span></span>](/visualstudio/ide/security-bibliography)  
 <span data-ttu-id="c1812-136">Obsahuje odkazy na externí prostředky, které jsou k dispozici online a v tisku.</span><span class="sxs-lookup"><span data-stu-id="c1812-136">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1812-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1812-137">See also</span></span>

- [<span data-ttu-id="c1812-138">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c1812-138">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
- [<span data-ttu-id="c1812-139">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="c1812-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

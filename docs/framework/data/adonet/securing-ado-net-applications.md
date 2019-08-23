---
title: Zabezpečení aplikací ADO.NET
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: d4c9c21f4d1f4a08ca6d676ee7b4c9e80709ba19
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963124"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="9b90e-102">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9b90e-102">Securing ADO.NET Applications</span></span>
<span data-ttu-id="9b90e-103">Zápis zabezpečené aplikace ADO.NET zahrnuje víc než vyhnout se běžnému kódování nástrah, jako je třeba ověřování vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="9b90e-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="9b90e-104">Aplikace, která přistupuje k datům, má mnoho potenciálních bodů selhání, které může útočník zneužít k načítání citlivých dat, manipulaci s nimi nebo jejich zničení.</span><span class="sxs-lookup"><span data-stu-id="9b90e-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="9b90e-105">Proto je důležité porozumět všem aspektům zabezpečení, a to od procesu modelování hrozeb během fáze návrhu vaší aplikace až po její případné nasazení a průběžnou údržbu.</span><span class="sxs-lookup"><span data-stu-id="9b90e-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
 <span data-ttu-id="9b90e-106">.NET Framework poskytuje spoustu užitečných tříd, služeb a nástrojů pro zabezpečení a správu databázových aplikací.</span><span class="sxs-lookup"><span data-stu-id="9b90e-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="9b90e-107">Modul CLR (Common Language Runtime) poskytuje typově bezpečné prostředí pro kód, který se má spustit v rámci, s použitím zabezpečení přístupu kódu (CAS) k omezení dalších oprávnění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="9b90e-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="9b90e-108">Následující postupy zabezpečení přístupu k datům omezují škodu, která může být způsobena potenciálním útočníkem.</span><span class="sxs-lookup"><span data-stu-id="9b90e-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
 <span data-ttu-id="9b90e-109">Při práci s nespravovanými prostředky, jako jsou databáze, nechrání zabezpečený kód bezpečnostní otvory způsobené držiteli.</span><span class="sxs-lookup"><span data-stu-id="9b90e-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="9b90e-110">Většina databází serveru, například SQL Server, má vlastní systémy zabezpečení, které zvyšují zabezpečení při správném implementaci.</span><span class="sxs-lookup"><span data-stu-id="9b90e-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="9b90e-111">I když není správně nakonfigurovaný, může být i zdroj dat s robustním systémem zabezpečení obětí útoku.</span><span class="sxs-lookup"><span data-stu-id="9b90e-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b90e-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9b90e-112">In This Section</span></span>  
 [<span data-ttu-id="9b90e-113">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9b90e-113">Security Overview</span></span>](../../../../docs/framework/data/adonet/security-overview.md)  
 <span data-ttu-id="9b90e-114">Poskytuje doporučení pro navrhování zabezpečených aplikací ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="9b90e-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="9b90e-115">Zabezpečený přístup k datům</span><span class="sxs-lookup"><span data-stu-id="9b90e-115">Secure Data Access</span></span>](../../../../docs/framework/data/adonet/secure-data-access.md)  
 <span data-ttu-id="9b90e-116">Popisuje, jak pracovat s daty ze zabezpečeného zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="9b90e-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="9b90e-117">Zabezpečené klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="9b90e-117">Secure Client Applications</span></span>](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 <span data-ttu-id="9b90e-118">Popisuje požadavky na zabezpečení pro klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="9b90e-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="9b90e-119">Zabezpečení přístupu ke kódu a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9b90e-119">Code Access Security and ADO.NET</span></span>](../../../../docs/framework/data/adonet/code-access-security.md)  
 <span data-ttu-id="9b90e-120">Popisuje, jak mohou certifikační autority přispět k ochraně kódu ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="9b90e-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="9b90e-121">Také popisuje, jak pracovat s částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="9b90e-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="9b90e-122">Ochrana osobních údajů a zabezpečení dat</span><span class="sxs-lookup"><span data-stu-id="9b90e-122">Privacy and Data Security</span></span>](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 <span data-ttu-id="9b90e-123">Popisuje možnosti šifrování pro aplikace ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="9b90e-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9b90e-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="9b90e-124">Related Sections</span></span>  
 [<span data-ttu-id="9b90e-125">SQL Server – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9b90e-125">SQL Server Security</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="9b90e-126">Popisuje SQL Server funkce zabezpečení z pohledu vývojáře.</span><span class="sxs-lookup"><span data-stu-id="9b90e-126">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="9b90e-127">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9b90e-127">Security Considerations</span></span>](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 <span data-ttu-id="9b90e-128">Popisuje zabezpečení pro Entity Framework aplikace.</span><span class="sxs-lookup"><span data-stu-id="9b90e-128">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="9b90e-129">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9b90e-129">Security</span></span>](../../../standard/security/index.md)  
 <span data-ttu-id="9b90e-130">Obsahuje odkazy na témata popisující všechny aspekty zabezpečení v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="9b90e-130">Contains links to topics describing all aspects of security in .NET.</span></span>  
  
 <span data-ttu-id="9b90e-131">[Nástroje zabezpečení](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9b90e-131">[Security Tools](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span></span>  
 <span data-ttu-id="9b90e-132">.NET Framework nástroje pro zabezpečení a správu zásad zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9b90e-132">.NET Framework tools for securing and administering security policy.</span></span>  
  
 <span data-ttu-id="9b90e-133">[Zdroje informací pro vytváření zabezpečených aplikací](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9b90e-133">[Resources for Creating Secure Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span></span>  
 <span data-ttu-id="9b90e-134">Obsahuje odkazy na témata týkající se vytváření zabezpečených aplikací.</span><span class="sxs-lookup"><span data-stu-id="9b90e-134">Provides links to topics for creating secure applications.</span></span>  
  
 [<span data-ttu-id="9b90e-135">Bibliografie k zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9b90e-135">Security Bibliography</span></span>](/visualstudio/ide/security-bibliography)  
 <span data-ttu-id="9b90e-136">Poskytuje odkazy na externí prostředky dostupné online a v tisku.</span><span class="sxs-lookup"><span data-stu-id="9b90e-136">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b90e-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b90e-137">See also</span></span>

- [<span data-ttu-id="9b90e-138">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9b90e-138">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
- [<span data-ttu-id="9b90e-139">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="9b90e-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

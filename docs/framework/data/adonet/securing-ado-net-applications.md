---
title: Zabezpečování aplikací
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: c1bdf4329665e4d29a47c26fb7dba8eb41c1cc3a
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980025"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="1f9f7-102">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1f9f7-102">Securing ADO.NET Applications</span></span>
<span data-ttu-id="1f9f7-103">Zápis zabezpečené aplikace ADO.NET zahrnuje víc než vyhnout se běžnému kódování nástrah, jako je třeba ověřování vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="1f9f7-104">Aplikace, která přistupuje k datům, má mnoho potenciálních bodů selhání, které může útočník zneužít k načítání citlivých dat, manipulaci s nimi nebo jejich zničení.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="1f9f7-105">Proto je důležité porozumět všem aspektům zabezpečení, a to od procesu modelování hrozeb během fáze návrhu vaší aplikace až po její případné nasazení a průběžnou údržbu.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
 <span data-ttu-id="1f9f7-106">.NET Framework poskytuje spoustu užitečných tříd, služeb a nástrojů pro zabezpečení a správu databázových aplikací.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="1f9f7-107">Modul CLR (Common Language Runtime) poskytuje typově bezpečné prostředí pro kód, který se má spustit v rámci, s použitím zabezpečení přístupu kódu (CAS) k omezení dalších oprávnění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="1f9f7-108">Následující postupy zabezpečení přístupu k datům omezují škodu, která může být způsobena potenciálním útočníkem.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
 <span data-ttu-id="1f9f7-109">Při práci s nespravovanými prostředky, jako jsou databáze, nechrání zabezpečený kód bezpečnostní otvory způsobené držiteli.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="1f9f7-110">Většina databází serveru, například SQL Server, má vlastní systémy zabezpečení, které zvyšují zabezpečení při správném implementaci.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="1f9f7-111">I když není správně nakonfigurovaný, může být i zdroj dat s robustním systémem zabezpečení obětí útoku.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1f9f7-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1f9f7-112">In This Section</span></span>  
 [<span data-ttu-id="1f9f7-113">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="1f9f7-113">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="1f9f7-114">Poskytuje doporučení pro navrhování zabezpečených aplikací ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="1f9f7-115">Zabezpečený přístup k datům</span><span class="sxs-lookup"><span data-stu-id="1f9f7-115">Secure Data Access</span></span>](secure-data-access.md)  
 <span data-ttu-id="1f9f7-116">Popisuje, jak pracovat s daty ze zabezpečeného zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="1f9f7-117">Zabezpečené klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="1f9f7-117">Secure Client Applications</span></span>](secure-client-applications.md)  
 <span data-ttu-id="1f9f7-118">Popisuje požadavky na zabezpečení pro klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="1f9f7-119">Zabezpečení přístupu ke kódu a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1f9f7-119">Code Access Security and ADO.NET</span></span>](code-access-security.md)  
 <span data-ttu-id="1f9f7-120">Popisuje, jak mohou certifikační autority přispět k ochraně kódu ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="1f9f7-121">Také popisuje, jak pracovat s částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="1f9f7-122">Ochrana osobních údajů a zabezpečení dat</span><span class="sxs-lookup"><span data-stu-id="1f9f7-122">Privacy and Data Security</span></span>](privacy-and-data-security.md)  
 <span data-ttu-id="1f9f7-123">Popisuje možnosti šifrování pro aplikace ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1f9f7-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="1f9f7-124">Related Sections</span></span>  
 [<span data-ttu-id="1f9f7-125">SQL Server – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="1f9f7-125">SQL Server Security</span></span>](./sql/sql-server-security.md)  
 <span data-ttu-id="1f9f7-126">Popisuje SQL Server funkce zabezpečení z pohledu vývojáře.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-126">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="1f9f7-127">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="1f9f7-127">Security Considerations</span></span>](./ef/security-considerations.md)  
 <span data-ttu-id="1f9f7-128">Popisuje zabezpečení pro Entity Framework aplikace.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-128">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="1f9f7-129">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="1f9f7-129">Security</span></span>](../../../standard/security/index.md)  
 <span data-ttu-id="1f9f7-130">Obsahuje odkazy na témata popisující všechny aspekty zabezpečení v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-130">Contains links to topics describing all aspects of security in .NET.</span></span>  
  
 <span data-ttu-id="1f9f7-131">[Nástroje zabezpečení](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1f9f7-131">[Security Tools](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span></span>  
 <span data-ttu-id="1f9f7-132">.NET Framework nástroje pro zabezpečení a správu zásad zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-132">.NET Framework tools for securing and administering security policy.</span></span>  
  
 <span data-ttu-id="1f9f7-133">[Zdroje informací pro vytváření zabezpečených aplikací](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1f9f7-133">[Resources for Creating Secure Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span></span>  
 <span data-ttu-id="1f9f7-134">Obsahuje odkazy na témata týkající se vytváření zabezpečených aplikací.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-134">Provides links to topics for creating secure applications.</span></span>  
  
 [<span data-ttu-id="1f9f7-135">Bibliografie k zabezpečení</span><span class="sxs-lookup"><span data-stu-id="1f9f7-135">Security Bibliography</span></span>](/visualstudio/ide/securing-applications)  
 <span data-ttu-id="1f9f7-136">Poskytuje odkazy na externí prostředky dostupné online a v tisku.</span><span class="sxs-lookup"><span data-stu-id="1f9f7-136">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f9f7-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f9f7-137">See also</span></span>

- [<span data-ttu-id="1f9f7-138">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1f9f7-138">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="1f9f7-139">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1f9f7-139">ADO.NET Overview</span></span>](ado-net-overview.md)

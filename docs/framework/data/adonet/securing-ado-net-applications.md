---
title: Zabezpečování aplikací
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: 1e08bb2386dff5d824d46aba652609ec5a373008
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374517"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="42684-102">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="42684-102">Securing ADO.NET applications</span></span>

<span data-ttu-id="42684-103">Zápis zabezpečené aplikace ADO.NET zahrnuje víc než vyhnout se běžnému kódování nástrah, jako je třeba ověřování vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="42684-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="42684-104">Aplikace, která přistupuje k datům, má mnoho potenciálních bodů selhání, které může útočník zneužít k načítání citlivých dat, manipulaci s nimi nebo jejich zničení.</span><span class="sxs-lookup"><span data-stu-id="42684-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="42684-105">Proto je důležité porozumět všem aspektům zabezpečení, a to od procesu modelování hrozeb během fáze návrhu vaší aplikace až po její případné nasazení a průběžnou údržbu.</span><span class="sxs-lookup"><span data-stu-id="42684-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
<span data-ttu-id="42684-106">.NET Framework poskytuje spoustu užitečných tříd, služeb a nástrojů pro zabezpečení a správu databázových aplikací.</span><span class="sxs-lookup"><span data-stu-id="42684-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="42684-107">Modul CLR (Common Language Runtime) poskytuje typově bezpečné prostředí pro kód, který se má spustit v rámci, s použitím zabezpečení přístupu kódu (CAS) k omezení dalších oprávnění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="42684-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="42684-108">Následující postupy zabezpečení přístupu k datům omezují škodu, která může být způsobena potenciálním útočníkem.</span><span class="sxs-lookup"><span data-stu-id="42684-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
<span data-ttu-id="42684-109">Při práci s nespravovanými prostředky, jako jsou databáze, nechrání zabezpečený kód bezpečnostní otvory způsobené držiteli.</span><span class="sxs-lookup"><span data-stu-id="42684-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="42684-110">Většina databází serveru, například SQL Server, má vlastní systémy zabezpečení, které zvyšují zabezpečení při správném implementaci.</span><span class="sxs-lookup"><span data-stu-id="42684-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="42684-111">I když není správně nakonfigurovaný, může být i zdroj dat s robustním systémem zabezpečení obětí útoku.</span><span class="sxs-lookup"><span data-stu-id="42684-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42684-112">V této části</span><span class="sxs-lookup"><span data-stu-id="42684-112">In this section</span></span>

 [<span data-ttu-id="42684-113">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="42684-113">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="42684-114">Poskytuje doporučení pro navrhování zabezpečených aplikací ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="42684-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="42684-115">Zabezpečený přístup k datům</span><span class="sxs-lookup"><span data-stu-id="42684-115">Secure Data Access</span></span>](secure-data-access.md)  
 <span data-ttu-id="42684-116">Popisuje, jak pracovat s daty ze zabezpečeného zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="42684-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="42684-117">Zabezpečené klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="42684-117">Secure Client Applications</span></span>](secure-client-applications.md)  
 <span data-ttu-id="42684-118">Popisuje požadavky na zabezpečení pro klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="42684-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="42684-119">Zabezpečení přístupu ke kódu a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="42684-119">Code Access Security and ADO.NET</span></span>](code-access-security.md)  
 <span data-ttu-id="42684-120">Popisuje, jak mohou certifikační autority přispět k ochraně kódu ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="42684-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="42684-121">Také popisuje, jak pracovat s částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="42684-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="42684-122">Ochrana osobních údajů a zabezpečení dat</span><span class="sxs-lookup"><span data-stu-id="42684-122">Privacy and Data Security</span></span>](privacy-and-data-security.md)  
 <span data-ttu-id="42684-123">Popisuje možnosti šifrování pro aplikace ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="42684-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="42684-124">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="42684-124">Related sections</span></span>

 [<span data-ttu-id="42684-125">Doprovodné materiály k zabezpečení datových sad a DataTable</span><span class="sxs-lookup"><span data-stu-id="42684-125">DataSet and DataTable security guidance</span></span>](dataset-datatable-dataview/security-guidance.md)  
 <span data-ttu-id="42684-126">Poskytuje bezpečnostní pokyny pro <xref:System.Data.DataSet> a <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="42684-126">Provides security guidance for <xref:System.Data.DataSet> and <xref:System.Data.DataTable>.</span></span>

 [<span data-ttu-id="42684-127">SQL Server – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="42684-127">SQL Server Security</span></span>](./sql/sql-server-security.md)  
 <span data-ttu-id="42684-128">Popisuje SQL Server funkce zabezpečení z pohledu vývojáře.</span><span class="sxs-lookup"><span data-stu-id="42684-128">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="42684-129">Otázky zabezpečení</span><span class="sxs-lookup"><span data-stu-id="42684-129">Security Considerations</span></span>](./ef/security-considerations.md)  
 <span data-ttu-id="42684-130">Popisuje zabezpečení pro Entity Framework aplikace.</span><span class="sxs-lookup"><span data-stu-id="42684-130">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="42684-131">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="42684-131">Security</span></span>](../../../standard/security/index.md)  
 <span data-ttu-id="42684-132">Obsahuje odkazy na články popisující všechny aspekty zabezpečení v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="42684-132">Contains links to articles describing all aspects of security in .NET.</span></span>  
  
 <span data-ttu-id="42684-133">[Nástroje zabezpečení](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="42684-133">[Security Tools](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span></span>  
 <span data-ttu-id="42684-134">.NET Framework nástroje pro zabezpečení a správu zásad zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="42684-134">.NET Framework tools for securing and administering security policy.</span></span>  
  
 <span data-ttu-id="42684-135">[Zdroje informací pro vytváření zabezpečených aplikací](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="42684-135">[Resources for Creating Secure Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span></span>  
 <span data-ttu-id="42684-136">Obsahuje odkazy na články pro vytváření zabezpečených aplikací.</span><span class="sxs-lookup"><span data-stu-id="42684-136">Provides links to articles for creating secure applications.</span></span>  
  
 [<span data-ttu-id="42684-137">Bibliografie k zabezpečení</span><span class="sxs-lookup"><span data-stu-id="42684-137">Security Bibliography</span></span>](/visualstudio/ide/securing-applications)  
 <span data-ttu-id="42684-138">Poskytuje odkazy na externí prostředky dostupné online a v tisku.</span><span class="sxs-lookup"><span data-stu-id="42684-138">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42684-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="42684-139">See also</span></span>

- [<span data-ttu-id="42684-140">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="42684-140">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="42684-141">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="42684-141">ADO.NET Overview</span></span>](ado-net-overview.md)

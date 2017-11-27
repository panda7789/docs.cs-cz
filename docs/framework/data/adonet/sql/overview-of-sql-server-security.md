---
title: "Přehled zabezpečení SQL serveru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d93d077153cd15534175c1e60e63a765ce893c71
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="overview-of-sql-server-security"></a><span data-ttu-id="51dae-102">Přehled zabezpečení SQL serveru</span><span class="sxs-lookup"><span data-stu-id="51dae-102">Overview of SQL Server Security</span></span>
<span data-ttu-id="51dae-103">Strategie obrany zabezpečení s překrývajícími se úrovní zabezpečení, je nejlepší způsob, jak čítač bezpečnostní hrozby.</span><span class="sxs-lookup"><span data-stu-id="51dae-103">A defense-in-depth strategy, with overlapping layers of security, is the best way to counter security threats.</span></span> <span data-ttu-id="51dae-104">SQL Server poskytuje zabezpečení architekturu, která je navržena k umožnění správce databáze a vývojářům vytvářet aplikace zabezpečené databáze a čítač hrozeb.</span><span class="sxs-lookup"><span data-stu-id="51dae-104">SQL Server provides a security architecture that is designed to allow database administrators and developers to create secure database applications and counter threats.</span></span> <span data-ttu-id="51dae-105">Každá verze nástroje SQL Server je vylepšený v dřívějších verzích systému SQL Server se zavedením nové funkce a funkce.</span><span class="sxs-lookup"><span data-stu-id="51dae-105">Each version of SQL Server has improved on previous versions of SQL Server with the introduction of new features and functionality.</span></span> <span data-ttu-id="51dae-106">V poli se však nedodává zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="51dae-106">However, security does not ship in the box.</span></span> <span data-ttu-id="51dae-107">Každá aplikace je jedinečné požadavky zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="51dae-107">Each application is unique in its security requirements.</span></span> <span data-ttu-id="51dae-108">Vývojáři muset vědět, která kombinace funkce a funkce jsou nejvhodnější pro čítače známé hrozby a předvídat hrozeb, které může způsobit v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="51dae-108">Developers need to understand which combination of features and functionality are most appropriate to counter known threats, and to anticipate threats that may arise in the future.</span></span>  
  
 <span data-ttu-id="51dae-109">Instance systému SQL Server obsahuje hierarchické kolekci entit, spouští se serverem.</span><span class="sxs-lookup"><span data-stu-id="51dae-109">A SQL Server instance contains a hierarchical collection of entities, starting with the server.</span></span> <span data-ttu-id="51dae-110">Každý server více databází, a každou databázi obsahuje kolekci zabezpečitelné objekty.</span><span class="sxs-lookup"><span data-stu-id="51dae-110">Each server contains multiple databases, and each database contains a collection of securable objects.</span></span> <span data-ttu-id="51dae-111">Každý Server SQL zabezpečitelné přidruženy *oprávnění* , lze udělit *hlavní*, což je jednotlivých, skupiny nebo proces udělen přístup k systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="51dae-111">Every SQL Server securable has associated *permissions* that can be granted to a *principal*, which is an individual, group or process granted access to SQL Server.</span></span> <span data-ttu-id="51dae-112">Zabezpečení systému SQL Server spravuje přístup k zabezpečenému entity prostřednictvím *ověřování* a *autorizace*.</span><span class="sxs-lookup"><span data-stu-id="51dae-112">The SQL Server security framework manages access to securable entities through *authentication* and *authorization*.</span></span>  
  
-   <span data-ttu-id="51dae-113">Ověřování je proces přihlášení k systému SQL Server, pomocí kterého objekt zabezpečení požaduje přístup odesláním přihlašovací údaje, které vyhodnotí server.</span><span class="sxs-lookup"><span data-stu-id="51dae-113">Authentication is the process of logging on to SQL Server by which a principal requests access by submitting credentials that the server evaluates.</span></span> <span data-ttu-id="51dae-114">Ověřování prokáže identity uživatele nebo procesu ověřovaného.</span><span class="sxs-lookup"><span data-stu-id="51dae-114">Authentication establishes the identity of the user or process being authenticated.</span></span>  
  
-   <span data-ttu-id="51dae-115">Autorizace je proces pro určení toho, že zabezpečitelné prostředky, ke kterým přístup objekt zabezpečení a operací, které jsou povoleny pro tyto prostředky.</span><span class="sxs-lookup"><span data-stu-id="51dae-115">Authorization is the process of determining which securable resources a principal can access, and which operations are allowed for those resources.</span></span>  
  
 <span data-ttu-id="51dae-116">Témata v této části se týkají Základy zabezpečení systému SQL Server, že poskytuje odkazy na kompletní dokumentaci v příslušné verzi systému SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="51dae-116">The topics in this section cover SQL Server security fundamentals, providing links to the complete documentation in the relevant version of SQL Server Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="51dae-117">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="51dae-117">In This Section</span></span>  
 [<span data-ttu-id="51dae-118">Ověřování v systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="51dae-118">Authentication in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 <span data-ttu-id="51dae-119">Popisuje přihlášení a ověřování v systému SQL Server a poskytuje odkazy na další zdroje.</span><span class="sxs-lookup"><span data-stu-id="51dae-119">Describes logins and authentication in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="51dae-120">Server a databázových rolí v systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="51dae-120">Server and Database Roles in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 <span data-ttu-id="51dae-121">Popisuje pevné role serveru a databáze, vlastní databázové role a integrované účty a poskytuje odkazy na další zdroje informací.</span><span class="sxs-lookup"><span data-stu-id="51dae-121">Describes fixed server and database roles, custom database roles, and built-in accounts and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="51dae-122">Vlastnictví a oddělení schéma uživatele v systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="51dae-122">Ownership and User-Schema Separation in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 <span data-ttu-id="51dae-123">Popisuje objekt oddělení vlastnictví a schéma uživatele a poskytuje odkazy na další zdroje.</span><span class="sxs-lookup"><span data-stu-id="51dae-123">Describes object ownership and  user-schema separation and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="51dae-124">Autorizace a oprávnění v systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="51dae-124">Authorization and Permissions in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 <span data-ttu-id="51dae-125">Popisuje udělení oprávnění pomocí Princip nejnižších nutných oprávnění a poskytuje odkazy na další zdroje.</span><span class="sxs-lookup"><span data-stu-id="51dae-125">Describes granting permissions using the principle of least privilege and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="51dae-126">Šifrování dat v systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="51dae-126">Data Encryption in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/data-encryption-in-sql-server.md)  
 <span data-ttu-id="51dae-127">Popisuje možnosti šifrování dat v systému SQL Server a poskytuje odkazy na další zdroje.</span><span class="sxs-lookup"><span data-stu-id="51dae-127">Describes data encryption options in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="51dae-128">CLR Integration zabezpečení v systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="51dae-128">CLR Integration Security in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/clr-integration-security-in-sql-server.md)  
 <span data-ttu-id="51dae-129">Obsahuje odkazy na zdroje zabezpečení integrace modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="51dae-129">Provides links to CLR integration security resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51dae-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="51dae-130">See Also</span></span>  
 [<span data-ttu-id="51dae-131">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="51dae-131">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="51dae-132">Zabezpečení SQL serveru</span><span class="sxs-lookup"><span data-stu-id="51dae-132">SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [<span data-ttu-id="51dae-133">Scénáře zabezpečení aplikací v systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="51dae-133">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="51dae-134">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="51dae-134">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

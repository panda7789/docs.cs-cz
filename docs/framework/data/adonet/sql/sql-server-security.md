---
title: Zabezpečení SQL serveru
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: eb9eb073eb2227ce98d4adb93b8f4b60575cf1b7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="sql-server-security"></a><span data-ttu-id="897a4-102">Zabezpečení SQL serveru</span><span class="sxs-lookup"><span data-stu-id="897a4-102">SQL Server Security</span></span>
<span data-ttu-id="897a4-103">Systému SQL Server obsahuje mnoho funkcí, které podporují vytváření aplikací pro zabezpečené databáze.</span><span class="sxs-lookup"><span data-stu-id="897a4-103">SQL Server has many features that support creating secure database applications.</span></span>  
  
 <span data-ttu-id="897a4-104">Společné aspekty zabezpečení, jako je krádež dat nebo vandalismu, platí bez ohledu na verzi systému SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="897a4-104">Common security considerations, such as data theft or vandalism, apply regardless of the version of SQL Server you are using.</span></span> <span data-ttu-id="897a4-105">Integritu dat by měly být považovány porušení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="897a4-105">Data integrity should also be considered as a security issue.</span></span> <span data-ttu-id="897a4-106">Pokud data nejsou chráněna, je možné, že by se mohly stát nemá, pokud je povoleno manipulaci s daty ad hoc a data jsou nechtěně nebo neoprávněnému změnit nesprávné hodnoty nebo odstraní celý.</span><span class="sxs-lookup"><span data-stu-id="897a4-106">If data is not protected, it is possible that it could become worthless if ad hoc data manipulation is permitted and the data is inadvertently or maliciously modified with incorrect values or deleted entirely.</span></span> <span data-ttu-id="897a4-107">Navíc často existují právní požadavky, které, musí být použito, jako je například správné úložiště důvěrné informace.</span><span class="sxs-lookup"><span data-stu-id="897a4-107">In addition, there are often legal requirements that must be adhered to, such as the correct storage of confidential information.</span></span> <span data-ttu-id="897a4-108">Ukládání některé druhy osobních údajů je proscribed zcela, v závislosti na právního, které se vztahují v konkrétní příslušnosti.</span><span class="sxs-lookup"><span data-stu-id="897a4-108">Storing some kinds of personal data is proscribed entirely, depending on the laws that apply in a particular jurisdiction.</span></span>  
  
 <span data-ttu-id="897a4-109">Každou verzi systému SQL Server má jiné bezpečnostní funkce, stejně jako jednotlivé verze Windows, s novější verze s rozšířené funkce přes předchozí.</span><span class="sxs-lookup"><span data-stu-id="897a4-109">Each version of SQL Server has different security features, as does each version of Windows, with later versions having enhanced functionality over earlier ones.</span></span> <span data-ttu-id="897a4-110">Je důležité si uvědomit, že funkce zabezpečení samostatně nemůže zaručit k aplikaci zabezpečené databáze.</span><span class="sxs-lookup"><span data-stu-id="897a4-110">It is important to understand that security features alone cannot guarantee a secure database application.</span></span> <span data-ttu-id="897a4-111">Každá databáze aplikace je jedinečné požadavky, prostředí pro spuštění, model nasazení, fyzické umístění a počet uživatelů.</span><span class="sxs-lookup"><span data-stu-id="897a4-111">Each database application is unique in its requirements, execution environment, deployment model, physical location, and user population.</span></span> <span data-ttu-id="897a4-112">Některé aplikace, které jsou v oboru místní může potřebovat pouze minimální zabezpečení, zatímco další místní aplikace nebo aplikace nasazené prostřednictvím Internetu může vyžadovat přísné bezpečnostní opatření a průběžné monitorování a vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="897a4-112">Some applications that are local in scope may need only minimal security whereas other local applications or applications deployed over the Internet may require stringent security measures and ongoing monitoring and evaluation.</span></span>  
  
 <span data-ttu-id="897a4-113">V době návrhu, ne jako chodím měli zvážit požadavky na zabezpečení aplikace databáze systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="897a4-113">The security requirements of a SQL Server database application should be considered at design time, not as an afterthought.</span></span> <span data-ttu-id="897a4-114">Vyhodnocení hrozby již v rané fázi v cyklu vývoje vám dává možnost omezit možné škody, bez ohledu na ohrožení zabezpečení související s je zjištěna.</span><span class="sxs-lookup"><span data-stu-id="897a4-114">Evaluating threats early in the development cycle gives you the opportunity to mitigate potential damage wherever a vulnerability is detected.</span></span>  
  
 <span data-ttu-id="897a4-115">I když je počáteční návrh aplikace zvuku, může vznikat nové hrozby jako zpracovaní systému.</span><span class="sxs-lookup"><span data-stu-id="897a4-115">Even if the initial design of an application is sound, new threats may emerge as the system evolves.</span></span> <span data-ttu-id="897a4-116">Tím, že vytvoříte více řádků obrany okolo vaší databáze, můžete minimalizovat škody si způsobilo porušení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="897a4-116">By creating multiple lines of defense around your database, you can minimize the damage inflicted by a security breach.</span></span> <span data-ttu-id="897a4-117">Vaše první linií obrany je snížit útoku podle nikdy k udělení více oprávnění, než jsou nezbytně nutné.</span><span class="sxs-lookup"><span data-stu-id="897a4-117">Your first line of defense is to reduce the attack surface area by never to granting more permissions than are absolutely necessary.</span></span>  
  
 <span data-ttu-id="897a4-118">Témata v této části stručně popisují funkce zabezpečení v systému SQL Server, které jsou relevantní pro vývojáře, s odkazy na související témata v SQL Server Books Online a dalším prostředkům, které poskytují podrobnější pokrytí.</span><span class="sxs-lookup"><span data-stu-id="897a4-118">The topics in this section briefly describe the security features in SQL Server that are relevant for developers, with links to relevant topics in SQL Server Books Online and other resources that provide more detailed coverage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="897a4-119">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="897a4-119">In This Section</span></span>  
 [<span data-ttu-id="897a4-120">Přehled zabezpečení SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="897a4-120">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 <span data-ttu-id="897a4-121">Popisuje funkce architektuře a zabezpečení systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="897a4-121">Describes the architecture and security features of SQL Server.</span></span>  
  
 [<span data-ttu-id="897a4-122">Scénáře zabezpečení aplikací na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="897a4-122">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 <span data-ttu-id="897a4-123">Obsahuje témata pojednávající o různé scénáře zabezpečení aplikací pro aplikace ADO.NET a SQL Server.</span><span class="sxs-lookup"><span data-stu-id="897a4-123">Contains topics discussing various application security scenarios for ADO.NET and SQL Server applications.</span></span>  
  
 [<span data-ttu-id="897a4-124">Zabezpečení SQL Serveru Express</span><span class="sxs-lookup"><span data-stu-id="897a4-124">SQL Server Express Security</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-express-security.md)  
 <span data-ttu-id="897a4-125">Popisuje důležité informace o zabezpečení pro SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="897a4-125">Describes security considerations for SQL Server Express.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="897a4-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="897a4-126">Related Sections</span></span>  
[<span data-ttu-id="897a4-127">Centrum zabezpečení pro databázový stroj systému SQL Server a databázi Azure SQL</span><span class="sxs-lookup"><span data-stu-id="897a4-127">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](/sql/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database)  
<span data-ttu-id="897a4-128">Popisuje důležité informace o zabezpečení pro SQL Server a databáze SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="897a4-128">Describes security considerations for SQL Server and Azure SQL Database.</span></span>

[<span data-ttu-id="897a4-129">Důležité informace o zabezpečení pro instalaci serveru SQL</span><span class="sxs-lookup"><span data-stu-id="897a4-129">Security Considerations for a SQL Server Installation</span></span>](/sql/sql-server/install/security-considerations-for-a-sql-server-installation)  
<span data-ttu-id="897a4-130">Popisuje aspekty zabezpečení, které je třeba zvážit před instalací systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="897a4-130">Describes security concerns to consider before installing SQL Server.</span></span>

## <a name="see-also"></a><span data-ttu-id="897a4-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="897a4-131">See Also</span></span>  
 [<span data-ttu-id="897a4-132">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="897a4-132">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="897a4-133">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="897a4-133">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  

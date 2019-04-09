---
title: Ověřování v SQL Serveru
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: f7fac0756da3bcc19ee6370468f0e0e65c428d35
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084034"
---
# <a name="authentication-in-sql-server"></a><span data-ttu-id="03c1b-102">Ověřování v SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="03c1b-102">Authentication in SQL Server</span></span>
<span data-ttu-id="03c1b-103">SQL Server podporuje dva režimy ověřování, režimu ověřování Windows a ve smíšeném režimu.</span><span class="sxs-lookup"><span data-stu-id="03c1b-103">SQL Server supports two authentication modes, Windows authentication mode and mixed mode.</span></span>  
  
-   <span data-ttu-id="03c1b-104">Ověřování Windows je výchozí a se často označuje jako integrované zabezpečení tento model zabezpečení systému SQL Server je těsně integrovaná se službami Windows.</span><span class="sxs-lookup"><span data-stu-id="03c1b-104">Windows authentication is the default, and is often referred to as integrated security because this SQL Server security model is tightly integrated with Windows.</span></span> <span data-ttu-id="03c1b-105">Určité účty uživatelů a skupin Windows jsou důvěryhodní k přihlášení k SQL serveru.</span><span class="sxs-lookup"><span data-stu-id="03c1b-105">Specific Windows user and group accounts are trusted to log in to SQL Server.</span></span> <span data-ttu-id="03c1b-106">Není potřeba k dispozici další přihlašovací údaje Windows, kteří již byl ověřen.</span><span class="sxs-lookup"><span data-stu-id="03c1b-106">Windows users who have already been authenticated do not have to present additional credentials.</span></span>  
  
-   <span data-ttu-id="03c1b-107">Ve smíšeném režimu podporuje ověřování Windows a SQL Server.</span><span class="sxs-lookup"><span data-stu-id="03c1b-107">Mixed mode supports authentication both by Windows and by SQL Server.</span></span> <span data-ttu-id="03c1b-108">Dvojice název a heslo uživatele zachovány v rámci SQL serveru.</span><span class="sxs-lookup"><span data-stu-id="03c1b-108">User name and password pairs are maintained within SQL Server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="03c1b-109">Doporučujeme používat ověřování Windows, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="03c1b-109">We recommend using Windows authentication wherever possible.</span></span> <span data-ttu-id="03c1b-110">Ověřování Windows k ověřování uživatelů v systému SQL Server používá řadu šifrované zprávy.</span><span class="sxs-lookup"><span data-stu-id="03c1b-110">Windows authentication uses a series of encrypted messages to authenticate users in SQL Server.</span></span> <span data-ttu-id="03c1b-111">Při přihlášení serveru SQL Server jsou používány, jsou předány přihlašovací jména systému SQL Server a šifrovaná hesla přes síť, což je méně bezpečné.</span><span class="sxs-lookup"><span data-stu-id="03c1b-111">When SQL Server logins are used, SQL Server login names and encrypted passwords are passed across the network, which makes them less secure.</span></span>  
  
 <span data-ttu-id="03c1b-112">Uživatelé s ověřováním Windows, se už přihlásili do Windows a není nutné samostatně přihlášení k SQL serveru.</span><span class="sxs-lookup"><span data-stu-id="03c1b-112">With Windows authentication, users are already logged onto Windows and do not have to log on separately to SQL Server.</span></span> <span data-ttu-id="03c1b-113">Následující `SqlConnection.ConnectionString` Určuje ověřování Windows, aniž by uživatelé museli zadat uživatelské jméno nebo heslo.</span><span class="sxs-lookup"><span data-stu-id="03c1b-113">The following `SqlConnection.ConnectionString` specifies Windows authentication without requiring users to provide a user name or password.</span></span>  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
>  <span data-ttu-id="03c1b-114">Přihlášení se liší od uživatele databáze.</span><span class="sxs-lookup"><span data-stu-id="03c1b-114">Logins are distinct from database users.</span></span> <span data-ttu-id="03c1b-115">Přihlašovací jména nebo skupiny Windows je nutné mapovat do databáze uživatelů nebo rolí v samostatné operaci.</span><span class="sxs-lookup"><span data-stu-id="03c1b-115">You must map logins or Windows groups to database users or roles in a separate operation.</span></span> <span data-ttu-id="03c1b-116">Pak udělíte oprávnění uživatelům nebo rolí pro přístup k objektům v databázi.</span><span class="sxs-lookup"><span data-stu-id="03c1b-116">You then grant permissions to users or roles to access database objects.</span></span>  
  
## <a name="authentication-scenarios"></a><span data-ttu-id="03c1b-117">Scénáře ověřování</span><span class="sxs-lookup"><span data-stu-id="03c1b-117">Authentication Scenarios</span></span>  
 <span data-ttu-id="03c1b-118">Ověřování Windows je obvykle nejlepší volbou v těchto situacích:</span><span class="sxs-lookup"><span data-stu-id="03c1b-118">Windows authentication is usually the best choice in the following situations:</span></span>  
  
-   <span data-ttu-id="03c1b-119">Je řadič domény.</span><span class="sxs-lookup"><span data-stu-id="03c1b-119">There is a domain controller.</span></span>  
  
-   <span data-ttu-id="03c1b-120">Aplikace a databáze jsou ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="03c1b-120">The application and the database are on the same computer.</span></span>  
  
-   <span data-ttu-id="03c1b-121">Používáte instanci systému SQL Server Express nebo LocalDB.</span><span class="sxs-lookup"><span data-stu-id="03c1b-121">You are using an instance of SQL Server Express or LocalDB.</span></span>  
  
 <span data-ttu-id="03c1b-122">Přihlášení serveru SQL Server se často používají v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="03c1b-122">SQL Server logins are often used in the following situations:</span></span>  
  
-   <span data-ttu-id="03c1b-123">Pokud máte pracovní skupiny.</span><span class="sxs-lookup"><span data-stu-id="03c1b-123">If you have a workgroup.</span></span>  
  
-   <span data-ttu-id="03c1b-124">Uživatelé připojovat z jiné, nedůvěryhodné domény.</span><span class="sxs-lookup"><span data-stu-id="03c1b-124">Users connect from different, non-trusted domains.</span></span>  
  
-   <span data-ttu-id="03c1b-125">Internetové aplikace, jako například [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="03c1b-125">Internet applications, such as [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03c1b-126">Zadání ověřování Windows nezakáže přihlášení serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="03c1b-126">Specifying Windows authentication does not disable SQL Server logins.</span></span> <span data-ttu-id="03c1b-127">Použít příkazu ALTER LOGIN zakázat [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkaz Zakázat přihlášení serveru SQL Server s vysokou úrovní oprávnění.</span><span class="sxs-lookup"><span data-stu-id="03c1b-127">Use the ALTER LOGIN DISABLE [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statement to disable highly-privileged SQL Server logins.</span></span>  
  
## <a name="login-types"></a><span data-ttu-id="03c1b-128">Typy přihlášení</span><span class="sxs-lookup"><span data-stu-id="03c1b-128">Login Types</span></span>  
 <span data-ttu-id="03c1b-129">SQL Server podporuje tři typy přihlášení:</span><span class="sxs-lookup"><span data-stu-id="03c1b-129">SQL Server supports three types of logins:</span></span>  
  
-   <span data-ttu-id="03c1b-130">Místní uživatelský účet Windows nebo důvěryhodné doméně účtu.</span><span class="sxs-lookup"><span data-stu-id="03c1b-130">A local Windows user account or trusted domain account.</span></span> <span data-ttu-id="03c1b-131">SQL Server závisí na Windows k ověření Windows uživatelské účty.</span><span class="sxs-lookup"><span data-stu-id="03c1b-131">SQL Server relies on Windows to authenticate the Windows user accounts.</span></span>  
  
-   <span data-ttu-id="03c1b-132">Skupiny Windows.</span><span class="sxs-lookup"><span data-stu-id="03c1b-132">Windows group.</span></span> <span data-ttu-id="03c1b-133">Udělení přístupu ke skupině Windows uděluje přístup ke všem přihlášení uživatele Windows, které jsou členy skupiny.</span><span class="sxs-lookup"><span data-stu-id="03c1b-133">Granting access to a Windows group grants access to all Windows user logins that are members of the group.</span></span>  
  
-   <span data-ttu-id="03c1b-134">Přihlašovací jméno SQL serveru.</span><span class="sxs-lookup"><span data-stu-id="03c1b-134">SQL Server login.</span></span> <span data-ttu-id="03c1b-135">SQL Server uchovává uživatelské jméno a hodnotu hash hesla v hlavní databázi pomocí interní ověřovacích metod ověření pokusů o přihlášení.</span><span class="sxs-lookup"><span data-stu-id="03c1b-135">SQL Server stores both the username and a hash of the password in the master database, by using internal authentication methods to verify login attempts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03c1b-136">SQL Server poskytuje přihlašovací údaje vytvořené z certifikáty nebo asymetrické klíče, které se používají pouze pro podepisování kódu.</span><span class="sxs-lookup"><span data-stu-id="03c1b-136">SQL Server provides logins created from certificates or asymmetric keys that are used only for code signing.</span></span> <span data-ttu-id="03c1b-137">Nelze použít pro připojení k SQL serveru.</span><span class="sxs-lookup"><span data-stu-id="03c1b-137">They cannot be used to connect to SQL Server.</span></span>  
  
## <a name="mixed-mode-authentication"></a><span data-ttu-id="03c1b-138">Ověřování ve smíšeném režimu</span><span class="sxs-lookup"><span data-stu-id="03c1b-138">Mixed Mode Authentication</span></span>  
 <span data-ttu-id="03c1b-139">Pokud je potřeba použít ve smíšeném režimu ověřování, musíte vytvořit přihlášení systému SQL Server, které jsou uloženy v systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="03c1b-139">If you must use mixed mode authentication, you must create SQL Server logins, which are stored in SQL Server.</span></span> <span data-ttu-id="03c1b-140">Potom je nutné zadat uživatelské jméno SQL serveru a heslo v době běhu.</span><span class="sxs-lookup"><span data-stu-id="03c1b-140">You then have to supply the SQL Server user name and password at run time.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="03c1b-141">SQL Server nainstaluje s přihlášením SQL serveru s názvem `sa` (zkratka "správce").</span><span class="sxs-lookup"><span data-stu-id="03c1b-141">SQL Server installs with a SQL Server login named `sa` (an abbreviation of "system administrator").</span></span> <span data-ttu-id="03c1b-142">Přiřaďte silné heslo, které `sa` přihlášení a nepoužívají `sa` přihlášení v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="03c1b-142">Assign a strong password to the `sa` login and do not use the `sa` login in your application.</span></span> <span data-ttu-id="03c1b-143">`sa` Přihlášení se mapuje `sysadmin` pevné role serveru, který má neodvolatelnou přihlašovací údaje pro správu na celý server.</span><span class="sxs-lookup"><span data-stu-id="03c1b-143">The `sa` login maps to the `sysadmin` fixed server role, which has irrevocable administrative credentials on the whole server.</span></span> <span data-ttu-id="03c1b-144">Neplatí žádné limity pro možné škody, pokud útočník získá přístup jako správce systému.</span><span class="sxs-lookup"><span data-stu-id="03c1b-144">There are no limits to the potential damage if an attacker gains access as a system administrator.</span></span> <span data-ttu-id="03c1b-145">Všichni členové Windows `BUILTIN\Administrators` skupinu (skupiny local Administrators) jsou členy `sysadmin` roli ve výchozím nastavení, ale můžete odebrat z této role.</span><span class="sxs-lookup"><span data-stu-id="03c1b-145">All members of the Windows `BUILTIN\Administrators` group (the local administrator's group) are members of the `sysadmin` role by default, but can be removed from that role.</span></span>  
  
 <span data-ttu-id="03c1b-146">SQL Server poskytuje mechanismy zásady hesla Windows pro přihlášení serveru SQL Server při spuštění [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="03c1b-146">SQL Server provides Windows password policy mechanisms for SQL Server logins when it is running on [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] or later versions.</span></span> <span data-ttu-id="03c1b-147">Zásady pro složitost hesla jsou navrženy pro odstraňovat útoky hrubou silou zvýšením počtu možných hesel.</span><span class="sxs-lookup"><span data-stu-id="03c1b-147">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> <span data-ttu-id="03c1b-148">SQL Server můžete použít stejné zásady složitosti a vypršení platnosti používané [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] to hesel použitých v SQL serveru.</span><span class="sxs-lookup"><span data-stu-id="03c1b-148">SQL Server can apply the same complexity and expiration policies used in [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] to passwords used inside SQL Server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="03c1b-149">Zřetězení řetězců připojení ze vstupu uživatele můžete nechat je zranitelný vůči útoku prostřednictvím injektáže řetězec připojení.</span><span class="sxs-lookup"><span data-stu-id="03c1b-149">Concatenating connection strings from user input can leave you vulnerable to a connection string injection attack.</span></span> <span data-ttu-id="03c1b-150">Použití <xref:System.Data.SqlClient.SqlConnectionStringBuilder> k vytváření syntakticky správný připojovací řetězce v době běhu.</span><span class="sxs-lookup"><span data-stu-id="03c1b-150">Use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="03c1b-151">Další informace najdete v tématu [tvůrci připojovacích řetězců](../../../../../docs/framework/data/adonet/connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="03c1b-151">For more information, see [Connection String Builders](../../../../../docs/framework/data/adonet/connection-string-builders.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="03c1b-152">Externí zdroje</span><span class="sxs-lookup"><span data-stu-id="03c1b-152">External Resources</span></span>  
 <span data-ttu-id="03c1b-153">Další informace najdete v následujících materiálech.</span><span class="sxs-lookup"><span data-stu-id="03c1b-153">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="03c1b-154">Prostředek</span><span class="sxs-lookup"><span data-stu-id="03c1b-154">Resource</span></span>|<span data-ttu-id="03c1b-155">Popis</span><span class="sxs-lookup"><span data-stu-id="03c1b-155">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="03c1b-156">Objekty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="03c1b-156">Principals</span></span>](/sql/relational-databases/security/authentication-access/principals-database-engine)|<span data-ttu-id="03c1b-157">Popisuje přihlášení a další hlavní služby zabezpečení v systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="03c1b-157">Describes logins and other security principals in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03c1b-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03c1b-158">See also</span></span>

- [<span data-ttu-id="03c1b-159">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="03c1b-159">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [<span data-ttu-id="03c1b-160">Scénáře zabezpečení aplikací na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="03c1b-160">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="03c1b-161">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="03c1b-161">Connecting to a Data Source</span></span>](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [<span data-ttu-id="03c1b-162">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="03c1b-162">Connection Strings</span></span>](../../../../../docs/framework/data/adonet/connection-strings.md)
- [<span data-ttu-id="03c1b-163">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="03c1b-163">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

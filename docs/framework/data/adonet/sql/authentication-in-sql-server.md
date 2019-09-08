---
title: Ověřování v SQL Serveru
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 49835ebf8ebe4d5bd200ed771477edc8af580b7d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794290"
---
# <a name="authentication-in-sql-server"></a><span data-ttu-id="474f9-102">Ověřování v SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="474f9-102">Authentication in SQL Server</span></span>
<span data-ttu-id="474f9-103">SQL Server podporuje dva režimy ověřování, režim ověřování systému Windows a smíšený režim.</span><span class="sxs-lookup"><span data-stu-id="474f9-103">SQL Server supports two authentication modes, Windows authentication mode and mixed mode.</span></span>  
  
- <span data-ttu-id="474f9-104">Ověřování systému Windows je výchozí a často se označuje jako integrované zabezpečení, protože tento model zabezpečení SQL Server je úzce integrovaný se systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="474f9-104">Windows authentication is the default, and is often referred to as integrated security because this SQL Server security model is tightly integrated with Windows.</span></span> <span data-ttu-id="474f9-105">Pro přihlášení k SQL Server jsou pro konkrétní účty uživatelů a skupin systému Windows důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="474f9-105">Specific Windows user and group accounts are trusted to log in to SQL Server.</span></span> <span data-ttu-id="474f9-106">Uživatelé systému Windows, kteří už byli ověřeni, nemusejí mít k dispozici další přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="474f9-106">Windows users who have already been authenticated do not have to present additional credentials.</span></span>  
  
- <span data-ttu-id="474f9-107">Smíšený režim podporuje ověřování jak v systému Windows, tak pomocí SQL Server.</span><span class="sxs-lookup"><span data-stu-id="474f9-107">Mixed mode supports authentication both by Windows and by SQL Server.</span></span> <span data-ttu-id="474f9-108">Páry uživatelské jméno a heslo se udržují v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="474f9-108">User name and password pairs are maintained within SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="474f9-109">Pokud je to možné, doporučujeme používat ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="474f9-109">We recommend using Windows authentication wherever possible.</span></span> <span data-ttu-id="474f9-110">Ověřování systému Windows používá k ověřování uživatelů v SQL Server řadu šifrovaných zpráv.</span><span class="sxs-lookup"><span data-stu-id="474f9-110">Windows authentication uses a series of encrypted messages to authenticate users in SQL Server.</span></span> <span data-ttu-id="474f9-111">Při SQL Server používání přihlašovacích jmen SQL Server přihlašovací jména a šifrovaná hesla se předávají přes síť, což snižuje jejich zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="474f9-111">When SQL Server logins are used, SQL Server login names and encrypted passwords are passed across the network, which makes them less secure.</span></span>  
  
 <span data-ttu-id="474f9-112">Při ověřování Windows se uživatelé už přihlásili k Windows a nemusíte se k SQL Server přihlašovat samostatně.</span><span class="sxs-lookup"><span data-stu-id="474f9-112">With Windows authentication, users are already logged onto Windows and do not have to log on separately to SQL Server.</span></span> <span data-ttu-id="474f9-113">`SqlConnection.ConnectionString` Toto Určuje ověřování systému Windows, aniž by uživatelé museli zadat uživatelské jméno nebo heslo.</span><span class="sxs-lookup"><span data-stu-id="474f9-113">The following `SqlConnection.ConnectionString` specifies Windows authentication without requiring users to provide a user name or password.</span></span>  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
> <span data-ttu-id="474f9-114">Přihlášení se liší od uživatelů databáze.</span><span class="sxs-lookup"><span data-stu-id="474f9-114">Logins are distinct from database users.</span></span> <span data-ttu-id="474f9-115">Přihlašovací jména nebo skupiny systému Windows je nutné namapovat na uživatele databáze nebo role v samostatné operaci.</span><span class="sxs-lookup"><span data-stu-id="474f9-115">You must map logins or Windows groups to database users or roles in a separate operation.</span></span> <span data-ttu-id="474f9-116">Pak uživatelům nebo rolím udělíte oprávnění pro přístup k objektům databáze.</span><span class="sxs-lookup"><span data-stu-id="474f9-116">You then grant permissions to users or roles to access database objects.</span></span>  
  
## <a name="authentication-scenarios"></a><span data-ttu-id="474f9-117">Scénáře ověřování</span><span class="sxs-lookup"><span data-stu-id="474f9-117">Authentication Scenarios</span></span>  
 <span data-ttu-id="474f9-118">Ověřování systému Windows je obvykle nejlepší volbou v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="474f9-118">Windows authentication is usually the best choice in the following situations:</span></span>  
  
- <span data-ttu-id="474f9-119">Existuje řadič domény.</span><span class="sxs-lookup"><span data-stu-id="474f9-119">There is a domain controller.</span></span>  
  
- <span data-ttu-id="474f9-120">Aplikace a databáze jsou ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="474f9-120">The application and the database are on the same computer.</span></span>  
  
- <span data-ttu-id="474f9-121">Používáte instanci SQL Server Express nebo LocalDB.</span><span class="sxs-lookup"><span data-stu-id="474f9-121">You are using an instance of SQL Server Express or LocalDB.</span></span>  
  
 <span data-ttu-id="474f9-122">Přihlašovací jména SQL Server se často používají v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="474f9-122">SQL Server logins are often used in the following situations:</span></span>  
  
- <span data-ttu-id="474f9-123">Máte-li pracovní skupinu.</span><span class="sxs-lookup"><span data-stu-id="474f9-123">If you have a workgroup.</span></span>  
  
- <span data-ttu-id="474f9-124">Uživatelé se připojují z různých nedůvěryhodných domén.</span><span class="sxs-lookup"><span data-stu-id="474f9-124">Users connect from different, non-trusted domains.</span></span>  
  
- <span data-ttu-id="474f9-125">Internetové aplikace, například ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="474f9-125">Internet applications, such as ASP.NET.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="474f9-126">Zadání ověřování systému Windows nezakáže SQL Server přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="474f9-126">Specifying Windows authentication does not disable SQL Server logins.</span></span> <span data-ttu-id="474f9-127">Pomocí příkazu ALTER LOGIN DISABLE příkaz Transact-SQL zakážete SQL Server přihlašovacích údajů s vysokou úrovní oprávnění.</span><span class="sxs-lookup"><span data-stu-id="474f9-127">Use the ALTER LOGIN DISABLE Transact-SQL statement to disable highly-privileged SQL Server logins.</span></span>  
  
## <a name="login-types"></a><span data-ttu-id="474f9-128">Typy přihlášení</span><span class="sxs-lookup"><span data-stu-id="474f9-128">Login Types</span></span>  
 <span data-ttu-id="474f9-129">SQL Server podporuje tři typy přihlášení:</span><span class="sxs-lookup"><span data-stu-id="474f9-129">SQL Server supports three types of logins:</span></span>  
  
- <span data-ttu-id="474f9-130">Místní uživatelský účet systému Windows nebo účet důvěryhodné domény.</span><span class="sxs-lookup"><span data-stu-id="474f9-130">A local Windows user account or trusted domain account.</span></span> <span data-ttu-id="474f9-131">SQL Server spoléhá na Windows k ověření uživatelských účtů systému Windows.</span><span class="sxs-lookup"><span data-stu-id="474f9-131">SQL Server relies on Windows to authenticate the Windows user accounts.</span></span>  
  
- <span data-ttu-id="474f9-132">Skupina systému Windows.</span><span class="sxs-lookup"><span data-stu-id="474f9-132">Windows group.</span></span> <span data-ttu-id="474f9-133">Udělení přístupu skupině systému Windows uděluje přístup všem uživatelským přihlašováním systému Windows, která jsou členy skupiny.</span><span class="sxs-lookup"><span data-stu-id="474f9-133">Granting access to a Windows group grants access to all Windows user logins that are members of the group.</span></span>  
  
- <span data-ttu-id="474f9-134">SQL Server přihlášení.</span><span class="sxs-lookup"><span data-stu-id="474f9-134">SQL Server login.</span></span> <span data-ttu-id="474f9-135">SQL Server ukládá uživatelské jméno i hodnotu hash hesla v hlavní databázi, a to pomocí metod interního ověřování pro ověření pokusů o přihlášení.</span><span class="sxs-lookup"><span data-stu-id="474f9-135">SQL Server stores both the username and a hash of the password in the master database, by using internal authentication methods to verify login attempts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="474f9-136">SQL Server poskytuje přihlášení vytvořená z certifikátů nebo asymetrických klíčů, které se používají jenom pro podepisování kódu.</span><span class="sxs-lookup"><span data-stu-id="474f9-136">SQL Server provides logins created from certificates or asymmetric keys that are used only for code signing.</span></span> <span data-ttu-id="474f9-137">Nelze je použít pro připojení k SQL Server.</span><span class="sxs-lookup"><span data-stu-id="474f9-137">They cannot be used to connect to SQL Server.</span></span>  
  
## <a name="mixed-mode-authentication"></a><span data-ttu-id="474f9-138">Ověřování ve smíšeném režimu</span><span class="sxs-lookup"><span data-stu-id="474f9-138">Mixed Mode Authentication</span></span>  
 <span data-ttu-id="474f9-139">Pokud je potřeba použít smíšený režim ověřování, musíte vytvořit SQL Server přihlašovacích údajů, které jsou uložené v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="474f9-139">If you must use mixed mode authentication, you must create SQL Server logins, which are stored in SQL Server.</span></span> <span data-ttu-id="474f9-140">Pak je nutné zadejte SQL Server uživatelské jméno a heslo v době běhu.</span><span class="sxs-lookup"><span data-stu-id="474f9-140">You then have to supply the SQL Server user name and password at run time.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="474f9-141">SQL Server se instaluje s přihlašovacím SQL Server `sa` s názvem (zkratka "správce systému").</span><span class="sxs-lookup"><span data-stu-id="474f9-141">SQL Server installs with a SQL Server login named `sa` (an abbreviation of "system administrator").</span></span> <span data-ttu-id="474f9-142">Přiřaďte `sa` přihlášení silné heslo a `sa` nepoužívejte přihlašovací údaje ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="474f9-142">Assign a strong password to the `sa` login and do not use the `sa` login in your application.</span></span> <span data-ttu-id="474f9-143">Přihlašovací údaje se mapují `sysadmin` na pevnou roli serveru, která má nevratná pověření pro správu na celém serveru. `sa`</span><span class="sxs-lookup"><span data-stu-id="474f9-143">The `sa` login maps to the `sysadmin` fixed server role, which has irrevocable administrative credentials on the whole server.</span></span> <span data-ttu-id="474f9-144">V případě, že útočník získá přístup jako správce systému, neexistují žádná omezení na potenciální škodu.</span><span class="sxs-lookup"><span data-stu-id="474f9-144">There are no limits to the potential damage if an attacker gains access as a system administrator.</span></span> <span data-ttu-id="474f9-145">Všichni členové skupiny Windows `BUILTIN\Administrators` (skupina místních správců) jsou ve výchozím nastavení členy `sysadmin` této role, ale je možné je z této role odebrat.</span><span class="sxs-lookup"><span data-stu-id="474f9-145">All members of the Windows `BUILTIN\Administrators` group (the local administrator's group) are members of the `sysadmin` role by default, but can be removed from that role.</span></span>  
  
 <span data-ttu-id="474f9-146">SQL Server poskytuje mechanismy zásad hesel Windows pro SQL Server přihlášení, když běží v [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] systému nebo novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="474f9-146">SQL Server provides Windows password policy mechanisms for SQL Server logins when it is running on [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] or later versions.</span></span> <span data-ttu-id="474f9-147">Zásady složitosti hesla jsou navržené tak, aby se zvýšil počet útoků hrubou silou, a to zvýšením počtu možných hesel.</span><span class="sxs-lookup"><span data-stu-id="474f9-147">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> <span data-ttu-id="474f9-148">SQL Server můžou použít stejné zásady složitosti a vypršení platnosti [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] používané v k heslům použitým v rámci SQL Server.</span><span class="sxs-lookup"><span data-stu-id="474f9-148">SQL Server can apply the same complexity and expiration policies used in [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] to passwords used inside SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="474f9-149">Zřetězení připojovacích řetězců ze vstupu uživatele může opustit útok prostřednictvím injektáže připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="474f9-149">Concatenating connection strings from user input can leave you vulnerable to a connection string injection attack.</span></span> <span data-ttu-id="474f9-150"><xref:System.Data.SqlClient.SqlConnectionStringBuilder> Použijte k vytvoření syntakticky platných připojovacích řetězců v době běhu.</span><span class="sxs-lookup"><span data-stu-id="474f9-150">Use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="474f9-151">Další informace najdete v tématu [tvůrci připojovacích řetězců](../connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="474f9-151">For more information, see [Connection String Builders](../connection-string-builders.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="474f9-152">Externí zdroje</span><span class="sxs-lookup"><span data-stu-id="474f9-152">External Resources</span></span>  
 <span data-ttu-id="474f9-153">Další informace najdete v následujících materiálech.</span><span class="sxs-lookup"><span data-stu-id="474f9-153">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="474f9-154">Resource</span><span class="sxs-lookup"><span data-stu-id="474f9-154">Resource</span></span>|<span data-ttu-id="474f9-155">Popis</span><span class="sxs-lookup"><span data-stu-id="474f9-155">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="474f9-156">Objekty</span><span class="sxs-lookup"><span data-stu-id="474f9-156">Principals</span></span>](/sql/relational-databases/security/authentication-access/principals-database-engine)|<span data-ttu-id="474f9-157">Popisuje přihlašovací údaje a další objekty zabezpečení v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="474f9-157">Describes logins and other security principals in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="474f9-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="474f9-158">See also</span></span>

- [<span data-ttu-id="474f9-159">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="474f9-159">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="474f9-160">Scénáře zabezpečení aplikací na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="474f9-160">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="474f9-161">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="474f9-161">Connecting to a Data Source</span></span>](../connecting-to-a-data-source.md)
- [<span data-ttu-id="474f9-162">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="474f9-162">Connection Strings</span></span>](../connection-strings.md)
- [<span data-ttu-id="474f9-163">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="474f9-163">ADO.NET Overview</span></span>](../ado-net-overview.md)

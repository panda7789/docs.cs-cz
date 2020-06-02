---
title: Ověřování v SQL Serveru
description: Přečtěte si o ověřování pomocí SQL Server pro ADO.NET, včetně režimu ověřování systému Windows a smíšeného režimu.
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: e9915598acfbdefb59069d6a9c6ef4b7c824e4c6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286543"
---
# <a name="authentication-in-sql-server"></a><span data-ttu-id="5ac31-103">Ověřování v SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="5ac31-103">Authentication in SQL Server</span></span>
<span data-ttu-id="5ac31-104">SQL Server podporuje dva režimy ověřování, režim ověřování systému Windows a smíšený režim.</span><span class="sxs-lookup"><span data-stu-id="5ac31-104">SQL Server supports two authentication modes, Windows authentication mode and mixed mode.</span></span>  
  
- <span data-ttu-id="5ac31-105">Ověřování systému Windows je výchozí a často se označuje jako integrované zabezpečení, protože tento model zabezpečení SQL Server je úzce integrovaný se systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="5ac31-105">Windows authentication is the default, and is often referred to as integrated security because this SQL Server security model is tightly integrated with Windows.</span></span> <span data-ttu-id="5ac31-106">Pro přihlášení k SQL Server jsou pro konkrétní účty uživatelů a skupin systému Windows důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="5ac31-106">Specific Windows user and group accounts are trusted to log in to SQL Server.</span></span> <span data-ttu-id="5ac31-107">Uživatelé systému Windows, kteří už byli ověřeni, nemusejí mít k dispozici další přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="5ac31-107">Windows users who have already been authenticated do not have to present additional credentials.</span></span>  
  
- <span data-ttu-id="5ac31-108">Smíšený režim podporuje ověřování jak v systému Windows, tak pomocí SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5ac31-108">Mixed mode supports authentication both by Windows and by SQL Server.</span></span> <span data-ttu-id="5ac31-109">Páry uživatelské jméno a heslo se udržují v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5ac31-109">User name and password pairs are maintained within SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5ac31-110">Pokud je to možné, doporučujeme používat ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5ac31-110">We recommend using Windows authentication wherever possible.</span></span> <span data-ttu-id="5ac31-111">Ověřování systému Windows používá k ověřování uživatelů v SQL Server řadu šifrovaných zpráv.</span><span class="sxs-lookup"><span data-stu-id="5ac31-111">Windows authentication uses a series of encrypted messages to authenticate users in SQL Server.</span></span> <span data-ttu-id="5ac31-112">Při SQL Server používání přihlašovacích jmen SQL Server přihlašovací jména a šifrovaná hesla se předávají přes síť, což snižuje jejich zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5ac31-112">When SQL Server logins are used, SQL Server login names and encrypted passwords are passed across the network, which makes them less secure.</span></span>  
  
 <span data-ttu-id="5ac31-113">Při ověřování Windows se uživatelé už přihlásili k Windows a nemusíte se k SQL Server přihlašovat samostatně.</span><span class="sxs-lookup"><span data-stu-id="5ac31-113">With Windows authentication, users are already logged onto Windows and do not have to log on separately to SQL Server.</span></span> <span data-ttu-id="5ac31-114">Toto `SqlConnection.ConnectionString` Určuje ověřování systému Windows, aniž by uživatelé museli zadat uživatelské jméno nebo heslo.</span><span class="sxs-lookup"><span data-stu-id="5ac31-114">The following `SqlConnection.ConnectionString` specifies Windows authentication without requiring users to provide a user name or password.</span></span>  
  
```csharp  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;"
```  
  
> [!NOTE]
> <span data-ttu-id="5ac31-115">Přihlášení se liší od uživatelů databáze.</span><span class="sxs-lookup"><span data-stu-id="5ac31-115">Logins are distinct from database users.</span></span> <span data-ttu-id="5ac31-116">Přihlašovací jména nebo skupiny systému Windows je nutné namapovat na uživatele databáze nebo role v samostatné operaci.</span><span class="sxs-lookup"><span data-stu-id="5ac31-116">You must map logins or Windows groups to database users or roles in a separate operation.</span></span> <span data-ttu-id="5ac31-117">Pak uživatelům nebo rolím udělíte oprávnění pro přístup k objektům databáze.</span><span class="sxs-lookup"><span data-stu-id="5ac31-117">You then grant permissions to users or roles to access database objects.</span></span>  
  
## <a name="authentication-scenarios"></a><span data-ttu-id="5ac31-118">Scénáře ověřování</span><span class="sxs-lookup"><span data-stu-id="5ac31-118">Authentication Scenarios</span></span>  
 <span data-ttu-id="5ac31-119">Ověřování systému Windows je obvykle nejlepší volbou v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="5ac31-119">Windows authentication is usually the best choice in the following situations:</span></span>  
  
- <span data-ttu-id="5ac31-120">Existuje řadič domény.</span><span class="sxs-lookup"><span data-stu-id="5ac31-120">There is a domain controller.</span></span>  
  
- <span data-ttu-id="5ac31-121">Aplikace a databáze jsou ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="5ac31-121">The application and the database are on the same computer.</span></span>  
  
- <span data-ttu-id="5ac31-122">Používáte instanci SQL Server Express nebo LocalDB.</span><span class="sxs-lookup"><span data-stu-id="5ac31-122">You are using an instance of SQL Server Express or LocalDB.</span></span>  
  
 <span data-ttu-id="5ac31-123">Přihlašovací jména SQL Server se často používají v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="5ac31-123">SQL Server logins are often used in the following situations:</span></span>  
  
- <span data-ttu-id="5ac31-124">Máte-li pracovní skupinu.</span><span class="sxs-lookup"><span data-stu-id="5ac31-124">If you have a workgroup.</span></span>  
  
- <span data-ttu-id="5ac31-125">Uživatelé se připojují z různých nedůvěryhodných domén.</span><span class="sxs-lookup"><span data-stu-id="5ac31-125">Users connect from different, non-trusted domains.</span></span>  
  
- <span data-ttu-id="5ac31-126">Internetové aplikace, například ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5ac31-126">Internet applications, such as ASP.NET.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ac31-127">Zadání ověřování systému Windows nezakáže SQL Server přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="5ac31-127">Specifying Windows authentication does not disable SQL Server logins.</span></span> <span data-ttu-id="5ac31-128">Pomocí příkazu ALTER LOGIN DISABLE příkaz Transact-SQL zakážete SQL Server přihlašovacích údajů s vysokou úrovní oprávnění.</span><span class="sxs-lookup"><span data-stu-id="5ac31-128">Use the ALTER LOGIN DISABLE Transact-SQL statement to disable highly-privileged SQL Server logins.</span></span>  
  
## <a name="login-types"></a><span data-ttu-id="5ac31-129">Typy přihlášení</span><span class="sxs-lookup"><span data-stu-id="5ac31-129">Login Types</span></span>  
 <span data-ttu-id="5ac31-130">SQL Server podporuje tři typy přihlášení:</span><span class="sxs-lookup"><span data-stu-id="5ac31-130">SQL Server supports three types of logins:</span></span>  
  
- <span data-ttu-id="5ac31-131">Místní uživatelský účet systému Windows nebo účet důvěryhodné domény.</span><span class="sxs-lookup"><span data-stu-id="5ac31-131">A local Windows user account or trusted domain account.</span></span> <span data-ttu-id="5ac31-132">SQL Server spoléhá na Windows k ověření uživatelských účtů systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5ac31-132">SQL Server relies on Windows to authenticate the Windows user accounts.</span></span>  
  
- <span data-ttu-id="5ac31-133">Skupina systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5ac31-133">Windows group.</span></span> <span data-ttu-id="5ac31-134">Udělení přístupu skupině systému Windows uděluje přístup všem uživatelským přihlašováním systému Windows, která jsou členy skupiny.</span><span class="sxs-lookup"><span data-stu-id="5ac31-134">Granting access to a Windows group grants access to all Windows user logins that are members of the group.</span></span>  
  
- <span data-ttu-id="5ac31-135">SQL Server přihlášení.</span><span class="sxs-lookup"><span data-stu-id="5ac31-135">SQL Server login.</span></span> <span data-ttu-id="5ac31-136">SQL Server ukládá uživatelské jméno i hodnotu hash hesla v hlavní databázi, a to pomocí metod interního ověřování pro ověření pokusů o přihlášení.</span><span class="sxs-lookup"><span data-stu-id="5ac31-136">SQL Server stores both the username and a hash of the password in the master database, by using internal authentication methods to verify login attempts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ac31-137">SQL Server poskytuje přihlášení vytvořená z certifikátů nebo asymetrických klíčů, které se používají jenom pro podepisování kódu.</span><span class="sxs-lookup"><span data-stu-id="5ac31-137">SQL Server provides logins created from certificates or asymmetric keys that are used only for code signing.</span></span> <span data-ttu-id="5ac31-138">Nelze je použít pro připojení k SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5ac31-138">They cannot be used to connect to SQL Server.</span></span>  
  
## <a name="mixed-mode-authentication"></a><span data-ttu-id="5ac31-139">Ověřování ve smíšeném režimu</span><span class="sxs-lookup"><span data-stu-id="5ac31-139">Mixed Mode Authentication</span></span>  
 <span data-ttu-id="5ac31-140">Pokud je potřeba použít smíšený režim ověřování, musíte vytvořit SQL Server přihlašovacích údajů, které jsou uložené v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5ac31-140">If you must use mixed mode authentication, you must create SQL Server logins, which are stored in SQL Server.</span></span> <span data-ttu-id="5ac31-141">Pak je nutné zadejte SQL Server uživatelské jméno a heslo v době běhu.</span><span class="sxs-lookup"><span data-stu-id="5ac31-141">You then have to supply the SQL Server user name and password at run time.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5ac31-142">SQL Server se instaluje s přihlašovacím SQL Server s názvem `sa` (zkratka "správce systému").</span><span class="sxs-lookup"><span data-stu-id="5ac31-142">SQL Server installs with a SQL Server login named `sa` (an abbreviation of "system administrator").</span></span> <span data-ttu-id="5ac31-143">Přiřaďte přihlášení silné heslo `sa` a nepoužívejte `sa` přihlašovací údaje ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5ac31-143">Assign a strong password to the `sa` login and do not use the `sa` login in your application.</span></span> <span data-ttu-id="5ac31-144">`sa`Přihlašovací údaje se mapují na `sysadmin` pevnou roli serveru, která má nevratná pověření pro správu na celém serveru.</span><span class="sxs-lookup"><span data-stu-id="5ac31-144">The `sa` login maps to the `sysadmin` fixed server role, which has irrevocable administrative credentials on the whole server.</span></span> <span data-ttu-id="5ac31-145">V případě, že útočník získá přístup jako správce systému, neexistují žádná omezení na potenciální škodu.</span><span class="sxs-lookup"><span data-stu-id="5ac31-145">There are no limits to the potential damage if an attacker gains access as a system administrator.</span></span> <span data-ttu-id="5ac31-146">Všichni členové `BUILTIN\Administrators` skupiny Windows (skupina místních správců) jsou `sysadmin` ve výchozím nastavení členy této role, ale je možné je z této role odebrat.</span><span class="sxs-lookup"><span data-stu-id="5ac31-146">All members of the Windows `BUILTIN\Administrators` group (the local administrator's group) are members of the `sysadmin` role by default, but can be removed from that role.</span></span>  
  
 <span data-ttu-id="5ac31-147">SQL Server poskytuje mechanismy zásad hesel Windows pro přihlášení SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5ac31-147">SQL Server provides Windows password policy mechanisms for SQL Server logins.</span></span> <span data-ttu-id="5ac31-148">Zásady složitosti hesla jsou navržené tak, aby se zvýšil počet útoků hrubou silou, a to zvýšením počtu možných hesel.</span><span class="sxs-lookup"><span data-stu-id="5ac31-148">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> <span data-ttu-id="5ac31-149">SQL Server můžou použít stejné zásady složitosti a vypršení platnosti jako hesla používaná v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5ac31-149">SQL Server can apply the same complexity and expiration policies to passwords used inside SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5ac31-150">Zřetězení připojovacích řetězců ze vstupu uživatele může opustit útok prostřednictvím injektáže připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="5ac31-150">Concatenating connection strings from user input can leave you vulnerable to a connection string injection attack.</span></span> <span data-ttu-id="5ac31-151">Použijte <xref:System.Data.SqlClient.SqlConnectionStringBuilder> k vytvoření syntakticky platných připojovacích řetězců v době běhu.</span><span class="sxs-lookup"><span data-stu-id="5ac31-151">Use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="5ac31-152">Další informace najdete v tématu [tvůrci připojovacích řetězců](../connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="5ac31-152">For more information, see [Connection String Builders](../connection-string-builders.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="5ac31-153">Externí zdroje</span><span class="sxs-lookup"><span data-stu-id="5ac31-153">External Resources</span></span>  
 <span data-ttu-id="5ac31-154">Další informace najdete v následujících materiálech.</span><span class="sxs-lookup"><span data-stu-id="5ac31-154">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="5ac31-155">Prostředek</span><span class="sxs-lookup"><span data-stu-id="5ac31-155">Resource</span></span>|<span data-ttu-id="5ac31-156">Popis</span><span class="sxs-lookup"><span data-stu-id="5ac31-156">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="5ac31-157">Objekty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5ac31-157">Principals</span></span>](/sql/relational-databases/security/authentication-access/principals-database-engine)|<span data-ttu-id="5ac31-158">Popisuje přihlašovací údaje a další objekty zabezpečení v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5ac31-158">Describes logins and other security principals in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ac31-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ac31-159">See also</span></span>

- [<span data-ttu-id="5ac31-160">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5ac31-160">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="5ac31-161">Scénáře zabezpečení aplikací na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="5ac31-161">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="5ac31-162">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="5ac31-162">Connecting to a Data Source</span></span>](../connecting-to-a-data-source.md)
- [<span data-ttu-id="5ac31-163">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="5ac31-163">Connection Strings</span></span>](../connection-strings.md)
- [<span data-ttu-id="5ac31-164">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5ac31-164">ADO.NET Overview</span></span>](../ado-net-overview.md)

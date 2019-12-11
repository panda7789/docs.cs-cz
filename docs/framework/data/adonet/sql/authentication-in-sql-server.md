---
title: Ověřování v SQL Serveru
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 0fb92f9e854e2a7a800335390d0195243a749b33
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959967"
---
# <a name="authentication-in-sql-server"></a><span data-ttu-id="d9632-102">Ověřování v SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="d9632-102">Authentication in SQL Server</span></span>
<span data-ttu-id="d9632-103">SQL Server supports two authentication modes, Windows authentication mode and mixed mode.</span><span class="sxs-lookup"><span data-stu-id="d9632-103">SQL Server supports two authentication modes, Windows authentication mode and mixed mode.</span></span>  
  
- <span data-ttu-id="d9632-104">Windows authentication is the default, and is often referred to as integrated security because this SQL Server security model is tightly integrated with Windows.</span><span class="sxs-lookup"><span data-stu-id="d9632-104">Windows authentication is the default, and is often referred to as integrated security because this SQL Server security model is tightly integrated with Windows.</span></span> <span data-ttu-id="d9632-105">Specific Windows user and group accounts are trusted to log in to SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d9632-105">Specific Windows user and group accounts are trusted to log in to SQL Server.</span></span> <span data-ttu-id="d9632-106">Windows users who have already been authenticated do not have to present additional credentials.</span><span class="sxs-lookup"><span data-stu-id="d9632-106">Windows users who have already been authenticated do not have to present additional credentials.</span></span>  
  
- <span data-ttu-id="d9632-107">Mixed mode supports authentication both by Windows and by SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d9632-107">Mixed mode supports authentication both by Windows and by SQL Server.</span></span> <span data-ttu-id="d9632-108">User name and password pairs are maintained within SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d9632-108">User name and password pairs are maintained within SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d9632-109">We recommend using Windows authentication wherever possible.</span><span class="sxs-lookup"><span data-stu-id="d9632-109">We recommend using Windows authentication wherever possible.</span></span> <span data-ttu-id="d9632-110">Windows authentication uses a series of encrypted messages to authenticate users in SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d9632-110">Windows authentication uses a series of encrypted messages to authenticate users in SQL Server.</span></span> <span data-ttu-id="d9632-111">When SQL Server logins are used, SQL Server login names and encrypted passwords are passed across the network, which makes them less secure.</span><span class="sxs-lookup"><span data-stu-id="d9632-111">When SQL Server logins are used, SQL Server login names and encrypted passwords are passed across the network, which makes them less secure.</span></span>  
  
 <span data-ttu-id="d9632-112">With Windows authentication, users are already logged onto Windows and do not have to log on separately to SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d9632-112">With Windows authentication, users are already logged onto Windows and do not have to log on separately to SQL Server.</span></span> <span data-ttu-id="d9632-113">The following `SqlConnection.ConnectionString` specifies Windows authentication without requiring users to provide a user name or password.</span><span class="sxs-lookup"><span data-stu-id="d9632-113">The following `SqlConnection.ConnectionString` specifies Windows authentication without requiring users to provide a user name or password.</span></span>  
  
```csharp  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;"
```  
  
> [!NOTE]
> <span data-ttu-id="d9632-114">Logins are distinct from database users.</span><span class="sxs-lookup"><span data-stu-id="d9632-114">Logins are distinct from database users.</span></span> <span data-ttu-id="d9632-115">You must map logins or Windows groups to database users or roles in a separate operation.</span><span class="sxs-lookup"><span data-stu-id="d9632-115">You must map logins or Windows groups to database users or roles in a separate operation.</span></span> <span data-ttu-id="d9632-116">You then grant permissions to users or roles to access database objects.</span><span class="sxs-lookup"><span data-stu-id="d9632-116">You then grant permissions to users or roles to access database objects.</span></span>  
  
## <a name="authentication-scenarios"></a><span data-ttu-id="d9632-117">Authentication Scenarios</span><span class="sxs-lookup"><span data-stu-id="d9632-117">Authentication Scenarios</span></span>  
 <span data-ttu-id="d9632-118">Windows authentication is usually the best choice in the following situations:</span><span class="sxs-lookup"><span data-stu-id="d9632-118">Windows authentication is usually the best choice in the following situations:</span></span>  
  
- <span data-ttu-id="d9632-119">There is a domain controller.</span><span class="sxs-lookup"><span data-stu-id="d9632-119">There is a domain controller.</span></span>  
  
- <span data-ttu-id="d9632-120">The application and the database are on the same computer.</span><span class="sxs-lookup"><span data-stu-id="d9632-120">The application and the database are on the same computer.</span></span>  
  
- <span data-ttu-id="d9632-121">You are using an instance of SQL Server Express or LocalDB.</span><span class="sxs-lookup"><span data-stu-id="d9632-121">You are using an instance of SQL Server Express or LocalDB.</span></span>  
  
 <span data-ttu-id="d9632-122">SQL Server logins are often used in the following situations:</span><span class="sxs-lookup"><span data-stu-id="d9632-122">SQL Server logins are often used in the following situations:</span></span>  
  
- <span data-ttu-id="d9632-123">If you have a workgroup.</span><span class="sxs-lookup"><span data-stu-id="d9632-123">If you have a workgroup.</span></span>  
  
- <span data-ttu-id="d9632-124">Users connect from different, non-trusted domains.</span><span class="sxs-lookup"><span data-stu-id="d9632-124">Users connect from different, non-trusted domains.</span></span>  
  
- <span data-ttu-id="d9632-125">Internet applications, such as ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d9632-125">Internet applications, such as ASP.NET.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9632-126">Specifying Windows authentication does not disable SQL Server logins.</span><span class="sxs-lookup"><span data-stu-id="d9632-126">Specifying Windows authentication does not disable SQL Server logins.</span></span> <span data-ttu-id="d9632-127">Use the ALTER LOGIN DISABLE Transact-SQL statement to disable highly-privileged SQL Server logins.</span><span class="sxs-lookup"><span data-stu-id="d9632-127">Use the ALTER LOGIN DISABLE Transact-SQL statement to disable highly-privileged SQL Server logins.</span></span>  
  
## <a name="login-types"></a><span data-ttu-id="d9632-128">Login Types</span><span class="sxs-lookup"><span data-stu-id="d9632-128">Login Types</span></span>  
 <span data-ttu-id="d9632-129">SQL Server supports three types of logins:</span><span class="sxs-lookup"><span data-stu-id="d9632-129">SQL Server supports three types of logins:</span></span>  
  
- <span data-ttu-id="d9632-130">A local Windows user account or trusted domain account.</span><span class="sxs-lookup"><span data-stu-id="d9632-130">A local Windows user account or trusted domain account.</span></span> <span data-ttu-id="d9632-131">SQL Server relies on Windows to authenticate the Windows user accounts.</span><span class="sxs-lookup"><span data-stu-id="d9632-131">SQL Server relies on Windows to authenticate the Windows user accounts.</span></span>  
  
- <span data-ttu-id="d9632-132">Windows group.</span><span class="sxs-lookup"><span data-stu-id="d9632-132">Windows group.</span></span> <span data-ttu-id="d9632-133">Granting access to a Windows group grants access to all Windows user logins that are members of the group.</span><span class="sxs-lookup"><span data-stu-id="d9632-133">Granting access to a Windows group grants access to all Windows user logins that are members of the group.</span></span>  
  
- <span data-ttu-id="d9632-134">SQL Server login.</span><span class="sxs-lookup"><span data-stu-id="d9632-134">SQL Server login.</span></span> <span data-ttu-id="d9632-135">SQL Server stores both the username and a hash of the password in the master database, by using internal authentication methods to verify login attempts.</span><span class="sxs-lookup"><span data-stu-id="d9632-135">SQL Server stores both the username and a hash of the password in the master database, by using internal authentication methods to verify login attempts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9632-136">SQL Server poskytuje přihlášení vytvořená z certifikátů nebo asymetrických klíčů, které se používají jenom pro podepisování kódu.</span><span class="sxs-lookup"><span data-stu-id="d9632-136">SQL Server provides logins created from certificates or asymmetric keys that are used only for code signing.</span></span> <span data-ttu-id="d9632-137">Nelze je použít pro připojení k SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d9632-137">They cannot be used to connect to SQL Server.</span></span>  
  
## <a name="mixed-mode-authentication"></a><span data-ttu-id="d9632-138">Ověřování ve smíšeném režimu</span><span class="sxs-lookup"><span data-stu-id="d9632-138">Mixed Mode Authentication</span></span>  
 <span data-ttu-id="d9632-139">Pokud je potřeba použít smíšený režim ověřování, musíte vytvořit SQL Server přihlašovacích údajů, které jsou uložené v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d9632-139">If you must use mixed mode authentication, you must create SQL Server logins, which are stored in SQL Server.</span></span> <span data-ttu-id="d9632-140">Pak je nutné zadejte SQL Server uživatelské jméno a heslo v době běhu.</span><span class="sxs-lookup"><span data-stu-id="d9632-140">You then have to supply the SQL Server user name and password at run time.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d9632-141">SQL Server se nainstaluje s přihlašovacím SQL Server s názvem `sa` (zkratka "správce systému").</span><span class="sxs-lookup"><span data-stu-id="d9632-141">SQL Server installs with a SQL Server login named `sa` (an abbreviation of "system administrator").</span></span> <span data-ttu-id="d9632-142">Přiřaďte k `sa` přihlášení silné heslo a nepoužívejte přihlášení `sa` ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d9632-142">Assign a strong password to the `sa` login and do not use the `sa` login in your application.</span></span> <span data-ttu-id="d9632-143">`sa` přihlašovací údaje se mapují k pevné roli serveru `sysadmin`, která má neodvolatelná pověření pro správu na celém serveru.</span><span class="sxs-lookup"><span data-stu-id="d9632-143">The `sa` login maps to the `sysadmin` fixed server role, which has irrevocable administrative credentials on the whole server.</span></span> <span data-ttu-id="d9632-144">V případě, že útočník získá přístup jako správce systému, neexistují žádná omezení na potenciální škodu.</span><span class="sxs-lookup"><span data-stu-id="d9632-144">There are no limits to the potential damage if an attacker gains access as a system administrator.</span></span> <span data-ttu-id="d9632-145">Všichni členové skupiny Windows `BUILTIN\Administrators` (skupina místních správců) jsou ve výchozím nastavení členy role `sysadmin`, ale je možné je z této role odebrat.</span><span class="sxs-lookup"><span data-stu-id="d9632-145">All members of the Windows `BUILTIN\Administrators` group (the local administrator's group) are members of the `sysadmin` role by default, but can be removed from that role.</span></span>  
  
 <span data-ttu-id="d9632-146">SQL Server poskytuje mechanismy zásad hesel Windows pro přihlášení SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d9632-146">SQL Server provides Windows password policy mechanisms for SQL Server logins.</span></span> <span data-ttu-id="d9632-147">Zásady složitosti hesla jsou navržené tak, aby se zvýšil počet útoků hrubou silou, a to zvýšením počtu možných hesel.</span><span class="sxs-lookup"><span data-stu-id="d9632-147">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> <span data-ttu-id="d9632-148">SQL Server můžou použít stejné zásady složitosti a vypršení platnosti jako hesla používaná v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d9632-148">SQL Server can apply the same complexity and expiration policies to passwords used inside SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d9632-149">Zřetězení připojovacích řetězců ze vstupu uživatele může opustit útok prostřednictvím injektáže připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="d9632-149">Concatenating connection strings from user input can leave you vulnerable to a connection string injection attack.</span></span> <span data-ttu-id="d9632-150">Použijte <xref:System.Data.SqlClient.SqlConnectionStringBuilder> k vytvoření syntakticky platných připojovacích řetězců v době běhu.</span><span class="sxs-lookup"><span data-stu-id="d9632-150">Use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="d9632-151">Další informace najdete v tématu [tvůrci připojovacích řetězců](../connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="d9632-151">For more information, see [Connection String Builders](../connection-string-builders.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="d9632-152">Externí prostředky</span><span class="sxs-lookup"><span data-stu-id="d9632-152">External Resources</span></span>  
 <span data-ttu-id="d9632-153">Další informace najdete v následujících materiálech.</span><span class="sxs-lookup"><span data-stu-id="d9632-153">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="d9632-154">Prostředek</span><span class="sxs-lookup"><span data-stu-id="d9632-154">Resource</span></span>|<span data-ttu-id="d9632-155">Popis</span><span class="sxs-lookup"><span data-stu-id="d9632-155">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="d9632-156">Objekty</span><span class="sxs-lookup"><span data-stu-id="d9632-156">Principals</span></span>](/sql/relational-databases/security/authentication-access/principals-database-engine)|<span data-ttu-id="d9632-157">Popisuje přihlašovací údaje a další objekty zabezpečení v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d9632-157">Describes logins and other security principals in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d9632-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9632-158">See also</span></span>

- [<span data-ttu-id="d9632-159">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d9632-159">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="d9632-160">Scénáře zabezpečení aplikací na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="d9632-160">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="d9632-161">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="d9632-161">Connecting to a Data Source</span></span>](../connecting-to-a-data-source.md)
- [<span data-ttu-id="d9632-162">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="d9632-162">Connection Strings</span></span>](../connection-strings.md)
- [<span data-ttu-id="d9632-163">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d9632-163">ADO.NET Overview</span></span>](../ado-net-overview.md)

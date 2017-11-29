---
title: "Zabezpečení v technologii LINQ to SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 27e40221c22a91bb2a8c40ec4bcfd663eb05aaef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="security-in-linq-to-sql"></a><span data-ttu-id="b1e19-102">Zabezpečení v technologii LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b1e19-102">Security in LINQ to SQL</span></span>
<span data-ttu-id="b1e19-103">Rizika zabezpečení jsou vždy k dispozici, při připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="b1e19-103">Security risks are always present when you connect to a database.</span></span> <span data-ttu-id="b1e19-104">I když technologie LINQ to SQL může zahrnovat některých nových způsobech pracovat s daty v systému SQL Server, neposkytuje žádné další bezpečnostní mechanismy.</span><span class="sxs-lookup"><span data-stu-id="b1e19-104">Although LINQ to SQL may include some new ways to work with data in SQL Server, it does not provide any additional security mechanisms.</span></span>  
  
## <a name="access-control-and-authentication"></a><span data-ttu-id="b1e19-105">Řízení přístupu a ověřování</span><span class="sxs-lookup"><span data-stu-id="b1e19-105">Access Control and Authentication</span></span>  
 <span data-ttu-id="b1e19-106">Technologie LINQ to SQL nemá vlastní mechanismy modelu nebo ověřování uživatele.</span><span class="sxs-lookup"><span data-stu-id="b1e19-106">LINQ to SQL does not have its own user model or authentication mechanisms.</span></span> <span data-ttu-id="b1e19-107">Používejte k řízení přístupu k databázi, databázových tabulek, zobrazení a uložených procedur, které jsou mapované na objektový model zabezpečení SQL serveru.</span><span class="sxs-lookup"><span data-stu-id="b1e19-107">Use SQL Server Security to control access to the database, database tables, views, and stored procedures that are mapped to your object model.</span></span> <span data-ttu-id="b1e19-108">Udělení přístupu minimální požadované uživatelům a vyžadovat silná hesla pro ověření uživatele.</span><span class="sxs-lookup"><span data-stu-id="b1e19-108">Grant the minimally required access to users and require strong passwords for user authentication.</span></span>  
  
## <a name="mapping-and-schema-information"></a><span data-ttu-id="b1e19-109">Mapování a informace o schématu</span><span class="sxs-lookup"><span data-stu-id="b1e19-109">Mapping and Schema Information</span></span>  
 <span data-ttu-id="b1e19-110">SQL CLR typ mapování a databáze informace o schématu v modelu objektu nebo externí mapování souboru je k dispozici pro všechny s přístupem k těmto souborům v systému souborů.</span><span class="sxs-lookup"><span data-stu-id="b1e19-110">SQL-CLR type mapping and database schema information in your object model or external mapping file is available for all with access to those files in the file system.</span></span> <span data-ttu-id="b1e19-111">Předpokládejme, že bude k dispozici všem, kdo má přístup k modelu objektu nebo externí mapování souboru informace o schématu. Abyste zabránili rozšiřujících přístupu k informace o schématu, použijte k zabezpečení zdrojové soubory a soubory mapování mechanismy zabezpečení souboru.</span><span class="sxs-lookup"><span data-stu-id="b1e19-111">Assume that schema information will be available to all who can access the object model or external mapping file.To prevent more widespread access to schema information, use file security mechanisms to secure source files and mapping files.</span></span>  
  
## <a name="connection-strings"></a><span data-ttu-id="b1e19-112">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="b1e19-112">Connection Strings</span></span>  
 <span data-ttu-id="b1e19-113">Použití hesel v připojovací řetězce je nutno kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="b1e19-113">Using passwords in connection strings should be avoided whenever possible.</span></span> <span data-ttu-id="b1e19-114">Jenom je připojovací řetězec ohrožení zabezpečení v sobě, ale připojovací řetězec může také přidat ve formátu prostého textu objektový model nebo externí mapování souboru při pomocí nástroje příkazového řádku Návrhář relací objektů nebo SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="b1e19-114">Not only is a connection string a security risk in its own right, but the connection string may also be added in clear text to the object model or external mapping file when using the Object Relational Designer or SQLMetal command-line tool.</span></span> <span data-ttu-id="b1e19-115">Každý, kdo má přístup k modelu objektu nebo externí mapování souboru prostřednictvím systému souborů by mohli zobrazit heslo připojení (Pokud je zahrnutý v připojovacím řetězci).</span><span class="sxs-lookup"><span data-stu-id="b1e19-115">Anyone with access to the object model or external mapping file via the file system could see the connection password (if it is included in the connection string).</span></span>  
  
 <span data-ttu-id="b1e19-116">Chcete-li minimalizovat těchto rizik, použít integrované zabezpečení pro důvěryhodné spojení s [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b1e19-116">To minimize such risks, use integrated security to make a trusted connection with [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b1e19-117">Pomocí tohoto přístupu nemáte uložit heslo v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="b1e19-117">By using this approach, you do not have to store a password in the connection string.</span></span> <span data-ttu-id="b1e19-118">Další informace najdete v tématu [zabezpečení SQL serveru](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md).</span><span class="sxs-lookup"><span data-stu-id="b1e19-118">For more information, see [SQL Server Security](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md).</span></span>  
  
 <span data-ttu-id="b1e19-119">Chybí integrované zabezpečení bude potřeba textové heslo v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="b1e19-119">In the absence of integrated security, a clear-text password will be needed in the connection string.</span></span> <span data-ttu-id="b1e19-120">Nejlepší způsob, jak pomoc se zabezpečením připojovací řetězec, ve vzestupném pořadí rizika, vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="b1e19-120">The best way to help secure your connection string, in increasing order of risk, is as follows:</span></span>  
  
-   <span data-ttu-id="b1e19-121">Použijte integrované zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b1e19-121">Use integrated security.</span></span>  
  
-   <span data-ttu-id="b1e19-122">Zabezpečené připojovací řetězce s hesly a minimalizovat předávání kolem připojovací řetězce.</span><span class="sxs-lookup"><span data-stu-id="b1e19-122">Secure connection strings with passwords and minimize passing around connection strings.</span></span>  
  
-   <span data-ttu-id="b1e19-123">Použití <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> třída místo připojovací řetězec, protože se omezuje trvání ohrožení.</span><span class="sxs-lookup"><span data-stu-id="b1e19-123">Use a <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> class instead of a connection string since it limits the duration of exposure.</span></span> <span data-ttu-id="b1e19-124">Technologie LINQ to SQL <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> může vytvořit instanci třídy pomocí <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="b1e19-124">The LINQ to SQL <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> class can be instantiated using a <xref:System.Data.SqlClient.SqlConnection>.</span></span>  
  
-   <span data-ttu-id="b1e19-125">Minimalizovat životnosti a touch bodů pro všechny řetězce připojení.</span><span class="sxs-lookup"><span data-stu-id="b1e19-125">Minimize lifetimes and touch points for all connection strings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1e19-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1e19-126">See Also</span></span>  
 [<span data-ttu-id="b1e19-127">Základní informace</span><span class="sxs-lookup"><span data-stu-id="b1e19-127">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="b1e19-128">Nejčastější dotazy</span><span class="sxs-lookup"><span data-stu-id="b1e19-128">Frequently Asked Questions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)

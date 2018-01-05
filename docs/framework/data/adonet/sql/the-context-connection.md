---
title: "Připojení kontextu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f3bb732644bf9373d847eb14b63e69a756cb3ac6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="the-context-connection"></a><span data-ttu-id="acb95-102">Připojení kontextu</span><span class="sxs-lookup"><span data-stu-id="acb95-102">The Context Connection</span></span>
<span data-ttu-id="acb95-103">Problém interních datových přístupu je docela běžný scénář.</span><span class="sxs-lookup"><span data-stu-id="acb95-103">The problem of internal data access is a fairly common scenario.</span></span> <span data-ttu-id="acb95-104">To znamená, že chcete na stejný server, na kterém common language runtime (CLR) uložené procedury nebo funkce provádí přistupuje.</span><span class="sxs-lookup"><span data-stu-id="acb95-104">That is, you wish to access the same server on which your common language runtime (CLR) stored procedure or function is executing.</span></span> <span data-ttu-id="acb95-105">Jednou z možností je vytvořit připojení pomocí <xref:System.Data.SqlClient.SqlConnection>, zadejte připojovací řetězec, který odkazuje na místním serveru a otevřete připojení.</span><span class="sxs-lookup"><span data-stu-id="acb95-105">One option is to create a connection using <xref:System.Data.SqlClient.SqlConnection>, specify a connection string that points to the local server, and open the connection.</span></span> <span data-ttu-id="acb95-106">To vyžaduje zadání pověření pro přihlášení.</span><span class="sxs-lookup"><span data-stu-id="acb95-106">This requires specifying credentials for logging in.</span></span> <span data-ttu-id="acb95-107">Připojení je v relaci k jiné databázi, než se uložená procedura nebo funkce, může mít různé `SET` možnosti, je v oddělené transakci, nezná dočasných tabulek, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="acb95-107">The connection is in a different database session than the stored procedure or function, it may have different `SET` options, it is in a separate transaction, it does not see your temporary tables, and so on.</span></span> <span data-ttu-id="acb95-108">Pokud vaše spravované uložené procedury nebo funkce kód je prováděna v procesu systému SQL Server, je to, protože někdo připojený k tomuto serveru a příkaz SQL pro vyvolání ho.</span><span class="sxs-lookup"><span data-stu-id="acb95-108">If your managed stored procedure or function code is executing in the SQL Server process, it is because someone connected to that server and executed a SQL statement to invoke it.</span></span> <span data-ttu-id="acb95-109">Budete ho zřejmě chtít uložená procedura nebo funkce, která má být spuštěn v kontextu tohoto připojení, spolu s jeho transakce `SET` možnosti a tak dále.</span><span class="sxs-lookup"><span data-stu-id="acb95-109">You probably want the stored procedure or function to execute in the context of that connection, along with its transaction, `SET` options, and so on.</span></span> <span data-ttu-id="acb95-110">Tomu se říká připojení kontextu.</span><span class="sxs-lookup"><span data-stu-id="acb95-110">This is called the context connection.</span></span>  
  
 <span data-ttu-id="acb95-111">Připojení kontextu umožňuje spustit příkazy jazyka Transact-SQL ve stejné oblasti, aby váš kód byl vyvolán na prvním místě.</span><span class="sxs-lookup"><span data-stu-id="acb95-111">The context connection lets you execute Transact-SQL statements in the same context that your code was invoked in the first place.</span></span> <span data-ttu-id="acb95-112">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="acb95-112">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="acb95-113">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="acb95-113">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="acb95-114">Kontextové připojení</span><span class="sxs-lookup"><span data-stu-id="acb95-114">The Context Connection</span></span>](http://go.microsoft.com/fwlink/?LinkId=115395)  
  
## <a name="see-also"></a><span data-ttu-id="acb95-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="acb95-115">See Also</span></span>  
 [<span data-ttu-id="acb95-116">Vytváření objektů serveru SQL Server 2005 ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="acb95-116">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="acb95-117">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="acb95-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

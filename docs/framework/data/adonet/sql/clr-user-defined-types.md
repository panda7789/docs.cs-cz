---
title: "Uživatelem definované typy CLR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e81cf54ed9dc516d88b8c7a97c8a5b33b8943d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="clr-user-defined-types"></a><span data-ttu-id="20f25-102">Uživatelem definované typy CLR</span><span class="sxs-lookup"><span data-stu-id="20f25-102">CLR User-Defined Types</span></span>
<span data-ttu-id="20f25-103">Microsoft SQL Server poskytuje podporu pro uživatelem definované typy (UDT) implementuje pomocí rozhraní Microsoft .NET Framework common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="20f25-103">Microsoft SQL Server provides support for user-defined types (UDTs) implemented with the Microsoft .NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="20f25-104">Modul CLR je integrován do systému SQL Server a tento mechanismus můžete rozšířit systém typů databáze.</span><span class="sxs-lookup"><span data-stu-id="20f25-104">The CLR is integrated into SQL Server, and this mechanism enables you to extend the type system of the database.</span></span> <span data-ttu-id="20f25-105">UDT zajistí možnosti rozšíření uživatele systém typů dat systému SQL Server, a také schopnost definovat strukturovaných komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="20f25-105">UDTs provide user extensibility of the SQL Server data type system, and also the ability to define complex structured types.</span></span>  
  
 <span data-ttu-id="20f25-106">UDT můžete zadat dvě klíčové výhody z hlediska architektury aplikaci.</span><span class="sxs-lookup"><span data-stu-id="20f25-106">UDTs can provide two key benefits from an application architecture perspective:</span></span>  
  
-   <span data-ttu-id="20f25-107">Silné zapouzdření (i v klientovi a serveru) mezi vnitřní stav a externí chování.</span><span class="sxs-lookup"><span data-stu-id="20f25-107">Strong encapsulation (both in the client and the server) between the internal state and the external behaviors.</span></span>  
  
-   <span data-ttu-id="20f25-108">Těsná integrace s jinými související s funkcí serveru.</span><span class="sxs-lookup"><span data-stu-id="20f25-108">Deep integration with other related server features.</span></span> <span data-ttu-id="20f25-109">Jakmile definujete vlastní UDT, můžete ji ve všech kontextech kde můžete použít typ systému v systému SQL Server, včetně definice sloupců a jako proměnné, parametry, výsledky funkce, kurzory, aktivační události a replikace.</span><span class="sxs-lookup"><span data-stu-id="20f25-109">Once you define your own UDT, you can use it in all contexts where you can use a system type in SQL Server, including column definitions, and as variables, parameters, function results, cursors, triggers, and replication.</span></span>  
  
 <span data-ttu-id="20f25-110">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="20f25-110">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="20f25-111">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="20f25-111">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="20f25-112">Uživatelem definované typy CLR</span><span class="sxs-lookup"><span data-stu-id="20f25-112">CLR User-Defined Types</span></span>](http://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="see-also"></a><span data-ttu-id="20f25-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="20f25-113">See Also</span></span>  
 [<span data-ttu-id="20f25-114">Vytváření objektů serveru SQL Server 2005 ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="20f25-114">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="20f25-115">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="20f25-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

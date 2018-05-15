---
title: Oracle distribuovaných transakcí
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 0e9dcb30eb1962071d7154d4bbf929871c8a12d2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="8eb4b-102">Oracle distribuovaných transakcí</span><span class="sxs-lookup"><span data-stu-id="8eb4b-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="8eb4b-103"><xref:System.Data.OracleClient.OracleConnection> Objekt automaticky využívá v existující distribuované transakce, pokud zjistí, že je aktivní transakce.</span><span class="sxs-lookup"><span data-stu-id="8eb4b-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="8eb4b-104">Automatický zápis do transakce nastane, když je připojení otevřené nebo načíst z fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="8eb4b-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="8eb4b-105">Můžete zakázat automatické zařazení ve stávajících transakcí zadáním</span><span class="sxs-lookup"><span data-stu-id="8eb4b-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="8eb4b-106">jako parametr s řetězcem připojení pro <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="8eb4b-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eb4b-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="8eb4b-107">See Also</span></span>  
 [<span data-ttu-id="8eb4b-108">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8eb4b-108">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="8eb4b-109">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="8eb4b-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

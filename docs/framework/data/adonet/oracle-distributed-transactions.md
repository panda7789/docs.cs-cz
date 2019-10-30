---
title: Distribuované transakce Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: edd06b94ce4157e90d334ee7feac2a449f7ee74b
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040483"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="881d9-102">Distribuované transakce Oracle</span><span class="sxs-lookup"><span data-stu-id="881d9-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="881d9-103">Objekt <xref:System.Data.OracleClient.OracleConnection> automaticky zařadí do existující distribuované transakce, pokud zjistí, že je transakce aktivní.</span><span class="sxs-lookup"><span data-stu-id="881d9-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="881d9-104">K automatickému zařazení transakce dochází, když je připojení otevřeno nebo načteno z fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="881d9-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="881d9-105">Automatické zařazení v existujících transakcích můžete zakázat zadáním</span><span class="sxs-lookup"><span data-stu-id="881d9-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```csharp  
Enlist=false  
```  
  
 <span data-ttu-id="881d9-106">jako parametr připojovacího řetězce pro <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="881d9-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="881d9-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="881d9-107">See also</span></span>

- [<span data-ttu-id="881d9-108">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="881d9-108">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="881d9-109">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="881d9-109">ADO.NET Overview</span></span>](ado-net-overview.md)

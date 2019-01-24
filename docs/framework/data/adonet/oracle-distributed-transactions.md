---
title: Distribuované transakce Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 8e7530621254881402570b59b47a22052b40f2b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713238"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="eebee-102">Distribuované transakce Oracle</span><span class="sxs-lookup"><span data-stu-id="eebee-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="eebee-103"><xref:System.Data.OracleClient.OracleConnection> Objekt automaticky využívá v existující distribuovanou transakci, pokud určí, že je aktivní transakce.</span><span class="sxs-lookup"><span data-stu-id="eebee-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="eebee-104">Automatický zápis do transakce nastane, pokud je připojení otevřené nebo načíst z fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="eebee-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="eebee-105">Automatické zařazení do existující transakce můžete zakázat tak, že zadáte</span><span class="sxs-lookup"><span data-stu-id="eebee-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="eebee-106">jako parametr řetězec připojení pro <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="eebee-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eebee-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eebee-107">See also</span></span>
- [<span data-ttu-id="eebee-108">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="eebee-108">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [<span data-ttu-id="eebee-109">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="eebee-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

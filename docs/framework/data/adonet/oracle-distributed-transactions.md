---
title: Distribuované transakce Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: a3b8a50b42b945a0cdc1cbfbc4cc9eab835e90e4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505396"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="50f69-102">Distribuované transakce Oracle</span><span class="sxs-lookup"><span data-stu-id="50f69-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="50f69-103"><xref:System.Data.OracleClient.OracleConnection> Objekt automaticky využívá v existující distribuovanou transakci, pokud určí, že je aktivní transakce.</span><span class="sxs-lookup"><span data-stu-id="50f69-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="50f69-104">Automatický zápis do transakce nastane, pokud je připojení otevřené nebo načíst z fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="50f69-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="50f69-105">Automatické zařazení do existující transakce můžete zakázat tak, že zadáte</span><span class="sxs-lookup"><span data-stu-id="50f69-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="50f69-106">jako parametr řetězec připojení pro <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="50f69-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50f69-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="50f69-107">See Also</span></span>  
 [<span data-ttu-id="50f69-108">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="50f69-108">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="50f69-109">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="50f69-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

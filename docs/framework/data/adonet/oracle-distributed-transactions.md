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
# <a name="oracle-distributed-transactions"></a>Distribuované transakce Oracle
<xref:System.Data.OracleClient.OracleConnection> Objekt automaticky využívá v existující distribuovanou transakci, pokud určí, že je aktivní transakce. Automatický zápis do transakce nastane, pokud je připojení otevřené nebo načíst z fondu připojení. Automatické zařazení do existující transakce můžete zakázat tak, že zadáte  
  
```  
Enlist=false  
```  
  
 jako parametr řetězec připojení pro <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="see-also"></a>Viz také  
 [Oracle a ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

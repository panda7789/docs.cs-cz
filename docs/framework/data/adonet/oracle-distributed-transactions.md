---
title: Distribuované transakce Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 4af1c98818f1929850c5ae78892c64993a93d4d2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771953"
---
# <a name="oracle-distributed-transactions"></a>Distribuované transakce Oracle
<xref:System.Data.OracleClient.OracleConnection> Objekt automaticky využívá v existující distribuovanou transakci, pokud určí, že je aktivní transakce. Automatický zápis do transakce nastane, pokud je připojení otevřené nebo načíst z fondu připojení. Automatické zařazení do existující transakce můžete zakázat tak, že zadáte  
  
```  
Enlist=false  
```  
  
 jako parametr řetězec připojení pro <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="see-also"></a>Viz také:

- [Oracle a ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)

---
title: "Oracle distribuovaných transakcí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 104befd25d30d050fee0a053a413b13fe6d1fc51
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="oracle-distributed-transactions"></a>Oracle distribuovaných transakcí
<xref:System.Data.OracleClient.OracleConnection> Objekt automaticky využívá v existující distribuované transakce, pokud zjistí, že je aktivní transakce. Automatický zápis do transakce nastane, když je připojení otevřené nebo načíst z fondu připojení. Můžete zakázat automatické zařazení ve stávajících transakcí zadáním  
  
```  
Enlist=false  
```  
  
 jako parametr s řetězcem připojení pro <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="see-also"></a>Viz také  
 [Oracle a ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)

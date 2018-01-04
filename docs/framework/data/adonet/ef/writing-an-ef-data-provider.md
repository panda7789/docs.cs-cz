---
title: "Zápis poskytovatele dat Entity Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a316ae288d677a0ad5bd602399e27389839ef092
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="writing-an-entity-framework-data-provider"></a>Zápis poskytovatele dat Entity Framework
Tato část popisuje, jak napsat [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele pro podporu zdroji dat jinými než [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zahrnuje zprostředkovatele, který podporuje [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
## <a name="introducing-the-entity-framework-provider-model"></a>Představení zprostředkovatele modelu Entity Framework  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Databáze je nezávislá a pomocí modelu zprostředkovatele ADO.NET pro připojení k různého typu zdroje dat můžete napsat zprostředkovatele.  
  
 Zprostředkovatel dat Entity Framework (vytvořen pomocí modelu zprostředkovatel ADO.NET Data Provider) provádí následující funkce:  
  
-   Mapuje typy zprostředkovatele Entity Data Model (EDM) primitivní typy.  
  
-   Zpřístupní funkce specifické pro zprostředkovatele.  
  
-   Generuje příkazy specifický pro zprostředkovatele pro danou DbQueryCommandTree pro podporu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dotazy.  
  
-   Vytvoří příkazy aktualizace specifický pro zprostředkovatele pro danou DbModificationCommandTree pro podporu aktualizací prostřednictvím [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
-   Zpřístupňuje mapování soubory pro definici schématu úložiště pro podporu generování modelu na základě databáze.  
  
-   Zveřejňuje metadata (tabulek a zobrazení, například) prostřednictvím konceptuálního modelu.  
  
 ![b42a7a5c & č. 45; 0ac0 & č. 45; 4911 & č. 45; 86be & č. 45; 0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")  
  
## <a name="sample"></a>Ukázka  
 Najdete v článku [zprostředkovatele Entity Framework ukázka](http://go.microsoft.com/fwlink/?LinkId=180616) ukázkové [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele, který podporuje zdroji dat jinými než [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Generování SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [Úpravy generování SQL](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [Specifikace manifestu zprostředkovatele](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a>Viz také  
 [Práce se zprostředkovateli dat](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)

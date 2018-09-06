---
title: Zápis zprostředkovatele dat Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 50c0555d84c5b5f180c8c49a8419e8a414a4befe
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43739448"
---
# <a name="writing-an-entity-framework-data-provider"></a>Zápis zprostředkovatele dat Entity Framework
Tato část popisuje, jak psát [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele pro podporu zdroje dat než SQL Server. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zahrnuje poskytovatele, který podporuje SQL Server.  
  
## <a name="introducing-the-entity-framework-provider-model"></a>Představení zprostředkovatele modelu Entity Framework  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nezávisí databáze a zprostředkovatele můžete napsat s využitím podle modelu poskytovatele ADO.NET pro připojení k různorodých zdrojů dat.  
  
 Zprostředkovatel dat Entity Framework (vytvořené pomocí modelu zprostředkovatele dat ADO.NET) provádí následující funkce:  
  
-   Primitivní typy Entity Data Model (EDM) se mapuje na poskytovatele typů.  
  
-   Zpřístupňuje funkce specifické pro zprostředkovatele.  
  
-   Generuje příkazy specifickým pro zprostředkovatele pro daného DbQueryCommandTree pro podporu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dotazy.  
  
-   Generuje příkazy specifickým pro zprostředkovatele aktualizace pro danou DbModificationCommandTree podporovat aktualizace prostřednictvím [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
-   Zpřístupňuje mapování souborů pro definici schématu úložiště pro podporu generování model založený na databázi.  
  
-   Poskytuje metadata (tabulek a zobrazení, například) prostřednictvím konceptuálního modelu.  
  
 ![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")  
  
## <a name="sample"></a>Ukázka  
 Najdete v článku [ukázka zprostředkovatele Entity Framework](https://go.microsoft.com/fwlink/?LinkId=180616) ukázku [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele, který podporuje zdroje dat než SQL Server.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Generování SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [Úpravy generování SQL](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [Specifikace manifestu zprostředkovatele](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a>Viz také  
 [Práce se zprostředkovateli dat](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)

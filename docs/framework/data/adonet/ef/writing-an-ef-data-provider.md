---
title: Zápis zprostředkovatele dat Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 6c5e6e2859b48db6c982862381d223a4c9deb2c5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248190"
---
# <a name="writing-an-entity-framework-data-provider"></a>Zápis zprostředkovatele dat Entity Framework
Tato část popisuje, jak napsat [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] poskytovatele pro podporu jiného zdroje dat než SQL Server. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obsahuje poskytovatele, který podporuje SQL Server.  
  
## <a name="introducing-the-entity-framework-provider-model"></a>Představení modelu poskytovatele Entity Framework  
 Je [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] nezávislá na databázi a můžete napsat poskytovatele pomocí modelu poskytovatele ADO.NET pro připojení k různorodé sadě zdrojů dat.  
  
 Poskytovatel dat Entity Framework (sestavený pomocí modelu Zprostředkovatel dat ADO.NET) provádí následující funkce:  
  
- Mapuje primitivní typy model EDM (Entity Data Model) (EDM) na typy poskytovatelů.  
  
- Zpřístupňuje funkce specifické pro poskytovatele.  
  
- Vygeneruje pro určitý DbQueryCommandTree příkazy specifické pro konkrétního zprostředkovatele [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] pro podporu dotazů.  
  
- Vygeneruje příkazy aktualizace specifické pro konkrétního poskytovatele pro daný DbModificationCommandTree pro podporu aktualizací [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]prostřednictvím.  
  
- Zpřístupňuje soubory mapování pro definici schématu úložiště, aby bylo možné podporovat generaci modelu založeného na databázi.  
  
- Zpřístupňuje metadata (například tabulky a zobrazení) prostřednictvím koncepčního modelu.  
  
 ![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")  
  
## <a name="sample"></a>Ukázka  
 Ukázku[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele, který podporuje jiný zdroj dat než SQL Server, najdete v tématu [poskytovatel ukázek Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) .  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Generování SQL](sql-generation.md)  
  
 [Úpravy generování SQL](modification-sql-generation.md)  
  
 [Specifikace manifestu zprostředkovatele](provider-manifest-specification.md)  
  
## <a name="see-also"></a>Viz také:

- [Práce se zprostředkovateli dat](working-with-data-providers.md)

---
title: Důležité informace o nasazení (rozhraní Entity Framework)
ms.date: 03/30/2017
ms.assetid: 3a847a22-4eb8-4565-b18b-453bbca070db
ms.openlocfilehash: 4456a466a7b76c68b3185bf586494f8591440844
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761256"
---
# <a name="deployment-considerations-entity-framework"></a>Důležité informace o nasazení (rozhraní Entity Framework)
Toto téma obsahuje informace o nasazení aplikace, které používají ADO.NET Entity Framework pro přístup k datům. Další informace o rozhraní Entity Framework najdete v tématu [Začínáme](../../../../../docs/framework/data/adonet/ef/getting-started.md).  
  
 Rozhraní Entity Framework poskytuje sadu nástrojů, které integrovat a usnadňují vývoj v sadě Visual Studio. Další informace najdete v tématu [nástrojů modelu ADO.NET Entity Data Model](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527). Toto téma nepopisuje použití určitých technologií nasazení aplikace rozhraní Entity Framework.  
  
 Visual Studio poskytuje zařízení pro distribuci a nasazení aplikací, jako je například ClickOnce – nasazení. Další informace najdete v tématu [nasazení aplikací a součástí](/visualstudio/deployment/deploying-applications-services-and-components) v dokumentaci sady Visual Studio.  
  
 Když nasadíte aplikaci používající rozhraní Entity Framework, platí následující aspekty:  
  
-   Rozhraní Entity Framework je součástí rozhraní .NET Framework od verze rozhraní .NET Framework 3.5 Service Pack 1 (SP1). Musí se ujistěte, že rozhraní .NET Framework 3.5 SP1 nebo novější verze nainstalovaný při nasazování aplikace rozhraní Entity Framework.  
  
-   Když konceptuálního modelu je generován průvodci Entity Data Model, vytvoří se připojovací řetězec v konfiguračním souboru aplikace. Soubory mapování a modelu lze vložit jako prostředky aplikace nebo může být zkopírován do výstupního adresáře. Ve výchozím nastavení jsou nasazeny jako prostředky embedded aplikace. Použití `Metadata Artifact Processing` vlastnost souboru Entity Designer vyberte jednu z těchto možností. Další informace najdete v tématu [postupy: kopírování modelu a mapování soubory do výstupního adresáře](http://msdn.microsoft.com/library/e2c9820f-1705-457e-9fdb-8b289f3179b4).  
  
-   Ujistěte se, že model a mapování informace (vyjádřeno v konceptuálního schématu definition language (CSDL), store schema definition language (SSDL) a specifikace jazyka mapování (MSL)) se nasazují společně s aplikace a v umístění Zadaný připojovací řetězec. Další informace najdete v tématu [připojovací řetězce](../../../../../docs/framework/data/adonet/ef/connection-strings.md).  
  
-   Když vložíte modelu a mapování informace jako prostředky aplikace, musíte znovu zkompiluje a znovu nasaďte aplikaci pokaždé, když dojde k aktualizaci konceptuálního modelu.  
  
-   Vzhledem k rozhraní Entity Framework je součástí rozhraní .NET Framework, můžete znovu distribuovat s vaší aplikací podle podmínek licenční smlouvy rozhraní .NET Framework.  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)  
 [Důležité informace o vývoji a nasazení](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)

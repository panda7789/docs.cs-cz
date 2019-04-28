---
title: Důležité informace o nasazení (rozhraní Entity Framework)
ms.date: 03/30/2017
ms.assetid: 3a847a22-4eb8-4565-b18b-453bbca070db
ms.openlocfilehash: 7ab3827a9f2072f6f4b0c34f3801ee5dff2821d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606625"
---
# <a name="deployment-considerations-entity-framework"></a>Důležité informace o nasazení (rozhraní Entity Framework)
Toto téma obsahuje informace o nasazení aplikace, které používají rozhraní ADO.NET Entity Framework pro přístup k datům. Další informace o rozhraní Entity Framework naleznete v tématu [Začínáme](../../../../../docs/framework/data/adonet/ef/getting-started.md).  
  
 Entity Framework poskytuje sadu nástrojů, které se integrují s usnadňují vývoj v sadě Visual Studio. Další informace najdete v tématu [ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)). Toto téma nepopisuje použití konkrétní technologie k nasazení aplikace založené na rozhraní Entity Framework.  
  
 Visual Studio poskytuje funkce pro distribuci a nasazování aplikací, jako je například nasazení ClickOnce. Další informace najdete v tématu [nasazení aplikací a součástí](/visualstudio/deployment/deploying-applications-services-and-components) v dokumentaci k sadě Visual Studio.  
  
 Když nasadíte aplikaci používající rozhraní Entity Framework, platí následující aspekty:  
  
- Entity Framework je součástí rozhraní .NET Framework počínaje .NET Framework 3.5 Service Pack 1 (SP1). Ujistěte se, že při nasazení aplikace založené na rozhraní Entity Framework je nainstalované rozhraní .NET Framework 3.5 SP1 nebo novější verze.  
  
- Když konceptuálního modelu je generován Průvodce datovým modelem Entity, vytvoří se připojovací řetězec v konfiguračním souboru aplikace. Modelu a souborů mapování, může být vložen jako prostředek aplikace nebo je možné zkopírovat do výstupního adresáře. Ve výchozím nastavení jsou nasazené jako prostředky vložené aplikace. Použití `Metadata Artifact Processing` vlastnost souboru návrháře entit vyberte jednu z těchto možností. Další informace najdete v tématu [jak: Kopírování modelu a mapování souborů do výstupního adresáře](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716709(v=vs.100)).  
  
- Ujistěte se, že modelu a mapování informace (vyjádřených v Konceptuální schéma definici jazyka (CSDL), store schema definition language (SSDL) a mapování specification language (MSL)) je nasazen spolu s aplikací a v umístění Zadaný připojovací řetězec. Další informace najdete v tématu [připojovací řetězce](../../../../../docs/framework/data/adonet/ef/connection-strings.md).  
  
- Při vložení modelu a mapování informace jako aplikace prostředků, musíte znovu zkompilovat a znovu nasadit aplikaci pokaždé, když dojde k aktualizaci koncepčního modelu.  
  
- Protože Entity Framework je součástí rozhraní .NET Framework, můžete znovu distribuovat s vaší aplikací podle licenční smlouvy rozhraní .NET Framework.  
  
## <a name="see-also"></a>Viz také:

- [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)
- [Důležité informace o vývoji a nasazení](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)

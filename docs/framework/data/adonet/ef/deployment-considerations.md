---
title: Požadavky na nasazení (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 3a847a22-4eb8-4565-b18b-453bbca070db
ms.openlocfilehash: 3e78fc413e50deda67aa8992179e500afa671f8d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251619"
---
# <a name="deployment-considerations-entity-framework"></a>Požadavky na nasazení (Entity Framework)
Toto téma poskytuje informace o nasazení aplikací, které používají Entity Framework ADO.NET pro přístup k datům. Další informace o Entity Framework najdete v tématu [Začínáme](getting-started.md).  
  
 Entity Framework poskytuje sadu nástrojů, které se integrují s a usnadňují vývoj v sadě Visual Studio. Další informace najdete v tématu [ADO.NET model EDM (Entity Data Model) Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)). Toto téma nepopisuje, jak používat konkrétní technologie k nasazení aplikace založené na Entity Framework.  
  
 Visual Studio poskytuje zařízení pro distribuci a nasazování aplikací, jako je například nasazení ClickOnce. Další informace naleznete v tématu [nasazování aplikací a součástí](/visualstudio/deployment/deploying-applications-services-and-components) v dokumentaci k sadě Visual Studio.  
  
 Když nasadíte aplikaci, která používá Entity Framework, platí následující požadavky:  
  
- Entity Framework je součástí .NET Framework počínaje verzí .NET Framework 3,5 Service Pack 1 (SP1). Je nutné zajistit, aby při nasazování aplikace založené na Entity Framework byla nainstalovaná verze .NET Framework 3,5 SP1 nebo novější.  
  
- Pokud je koncepční model generován průvodcem model EDM (Entity Data Model), je připojovací řetězec vytvořen v konfiguračním souboru aplikace. Soubory modelu a mapování lze vložit jako prostředky aplikace nebo je lze zkopírovat do výstupního adresáře. Ve výchozím nastavení jsou nasazeny jako prostředky vložené aplikace. `Metadata Artifact Processing` Pomocí vlastnosti entity Designer souboru vyberte jednu z těchto možností. Další informace najdete v tématu [jak: Kopírovat model a mapovat soubory do výstupního adresáře](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716709(v=vs.100)).  
  
- Zajistěte, aby byly informace o modelu a mapování (vyjádřené v jazyce CSDL (konceptuální schéma Definition Language), úložiště SSDL (Schema Definition Language) a specifikace jazyka MSL) nasazeny společně s aplikací a v umístění. určené připojovacím řetězcem. Další informace najdete v tématu [připojovací řetězce](connection-strings.md).  
  
- Při vložení modelu a mapování informací jako prostředků aplikace je nutné znovu zkompilovat a znovu nasadit aplikaci při každém aktualizaci koncepčního modelu.  
  
- Vzhledem k tomu, že Entity Framework je součástí .NET Framework, je možné ji znovu distribuovat s aplikací, kterou povoluje .NET Framework licenční smlouva.  
  
## <a name="see-also"></a>Viz také:

- [ADO.NET Entity Framework](index.md)
- [Důležité informace o vývoji a nasazení](development-and-deployment-considerations.md)

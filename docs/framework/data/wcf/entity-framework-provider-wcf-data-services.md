---
title: "Zprostředkovatel Entity Framework (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bc27663904371991855b2fe7d96b4a15827d1180
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="entity-framework-provider-wcf-data-services"></a>Zprostředkovatel Entity Framework (služby WCF Data Services)
Jako [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], ADO.NET Entity Framework je založena na Entity Data Model, který je typu modelu vztah entit. Rozhraní Entity Framework překládá operace u jeho implementace modelu Entity Data Model, který se nazývá *konceptuálního modelu*, do ekvivalentní operací zdroj dat a. Díky rozhraní Entity Framework poskytovatele ideální pro data služby, které jsou založeny na relační data a všechny databáze, který má zprostředkovatele dat, který podporuje rozhraní Entity Framework lze použít s [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Seznam zdrojů dat, které aktuálně podporují rozhraní Entity Framework najdete v tématu [poskytovatelů třetích stran pro rozhraní Entity Framework](http://go.microsoft.com/fwlink/?LinkId=143699).  
  
 V konceptuálním modelu kontejneru entit je kořenový adresář služby. Před data mohou být zpřístupněny službou data, je nutné zadat Koncepční model v rozhraní Entity Framework. Další informace najdete v tématu [postupy: vytvoření službu Data pomocí datového zdroje ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]podporuje model optimistickou metodu souběžného tím, že vám definovat token souběžnosti pro entitu. Tento token souběžnosti, která obsahuje jednu nebo více vlastností entity, se službou data používá k určení, zda data, která jsou požadována, aktualizovaných nebo odstraněných došlo ke změně. Pokud token hodnoty získané z eTag v žádosti se liší od aktuální hodnoty entity, je vyvolána výjimka službou data. K označení, že vlastnost je součástí token souběžnosti, musíte použít atribut `ConcurrencyMode="Fixed"` v datovém modelu definované [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] zprostředkovatele. Token souběžnosti nemůže obsahovat vlastnost klíče nebo navigační vlastnost. Další informace najdete v tématu [aktualizaci dat služby](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 Další informace o rozhraní Entity Framework najdete v tématu [Entity Framework přehled](../../../../docs/framework/data/adonet/ef/overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Zprostředkovatel reflexe](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)  
 [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)

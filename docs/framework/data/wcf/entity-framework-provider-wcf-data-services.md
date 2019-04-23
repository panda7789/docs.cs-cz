---
title: Zprostředkovatele Entity Framework (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: a09c81b2d0f052884e8e54c899653a6f0e038aff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086244"
---
# <a name="entity-framework-provider-wcf-data-services"></a>Zprostředkovatele Entity Framework (WCF Data Services)
Stejně jako [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], ADO.NET Entity Framework je založená na modelu Entity Data Model, který je typem relace entity model. Entity Framework překládá operací s jeho implementace modelu Entity Data Model, která je volána *koncepčního modelu*, do ekvivalentními operacemi proti datovému zdroji. Díky rozhraní Entity Framework poskytovatele ideální pro datové služby, které jsou založeny na relačních dat a všechny databáze, které má zprostředkovatele dat, který podporuje rozhraní Entity Framework lze použít s [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Seznam zdrojů dat, které aktuálně podporují rozhraní Entity Framework najdete v tématu [zprostředkovatelé třetí strany pro Entity Framework](https://go.microsoft.com/fwlink/?LinkId=143699).  
  
 Kontejner entit v konceptuálním modelu je kořen služby. Předtím, než se data můžou být vystavena s datovou službu, je nutné definovat konceptuálního modelu v Entity Framework. Další informace najdete v tématu [jak: Vytvoření datové služby pomocí zdroje dat rozhraní ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] podporuje model optimistického řízení souběžnosti tím, že vám k definování tokenem souběžnosti pro entitu. Tento token souběžnosti, který obsahuje jednu nebo více vlastností entity, používá k určení, zda došlo ke změně v datech, které jsou požadovány, aktualizovaných nebo odstraněných datové služby. Když token hodnoty získané ze značky eTag v požadavku se liší od aktuální hodnoty entity, je vyvolána výjimka datovou službou. K označení, že vlastnost je součástí tokenem souběžnosti, musíte použít atribut `ConcurrencyMode="Fixed"` v datovém modelu, který je definován [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] zprostředkovatele. Tokenem souběžnosti není možné zahrnout klíčová vlastnost nebo vlastnost navigace. Další informace najdete v tématu [aktualizace datové služby](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 Další informace o rozhraní Entity Framework najdete v tématu [přehled Entity Framework](../../../../docs/framework/data/adonet/ef/overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [Zprostředkovatel reflexe](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
- [Model EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md)

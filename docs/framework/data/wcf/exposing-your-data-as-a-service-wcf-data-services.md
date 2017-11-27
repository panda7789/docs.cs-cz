---
title: "Vystavení dat jako služba (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 122d05d5e4bd7690f32b22453dccbfaab2fb7f13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="exposing-your-data-as-a-service-wcf-data-services"></a>Vystavení dat jako služba (služby WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]se integruje s Visual Studio umožňují snadno definovat služby, která zveřejňuje data podle [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] kanály. Vytvoření datové služby, který zveřejňuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informační kanál zahrnuje následující základní kroky:  
  
1.  **Definování** **datový model**. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]nativně podporuje datové modely, které jsou založeny na [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md). Další informace najdete v tématu [postupy: vytvoření službu Data pomocí datového zdroje ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]také podporuje datové modely, které jsou založeny na common language runtime (CLR) objekty, které vrátit instanci třídy <xref:System.Linq.IQueryable%601> rozhraní. To umožňuje nasazení datové služby, které jsou založeny na seznamu, pole a kolekcí v rozhraní .NET Framework. Chcete-li povolit vytvářet, aktualizovat a odstraňovat operations přes tyto datové struktury, musíte také implementovat <xref:System.Data.Services.IUpdatable> rozhraní. Další informace najdete v tématu [postupy: vytvoření služby Data pomocí poskytovatele reflexe](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
     Pro pokročilejší scénáře [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zahrnuje sadu poskytovatelů, které umožňují definovat datový model na základě typu dat pozdní vazbu. Další informace najdete v tématu [vlastní Data poskytovatelé](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).  
  
2.  **Vytvořte službu data.** Službu nejzákladnější data zpřístupní třídu, která dědí z <xref:System.Data.Services.DataService%601> třídy s typem `T` který je obor názvů kvalifikovaný název kontejneru entit. Další informace najdete v tématu [definování datových služeb WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).  
  
3.  **Nakonfigurujte službu data.** Ve výchozím nastavení [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zakáže přístup k prostředkům, které jsou vystavené kontejner entity. <xref:System.Data.Services.DataServiceConfiguration> Rozhraní umožňuje konfigurovat přístup k prostředkům a služby operations, zadejte podporovanou verzi [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]a definování jiného chování celé služby, jako je například dávkování chování nebo maximální počet entit, které můžete Vrátí se odpověď o jedné. Další informace najdete v tématu [konfigurace službu Data](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 Příklad vytvoření jednoduché datové služby, který je založen na ukázková databáze Northwind, naleznete v části [rychlý Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Začínáme](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [Přehled](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

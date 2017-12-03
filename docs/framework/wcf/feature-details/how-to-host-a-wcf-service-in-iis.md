---
title: "Postupy: Hostování služby WCF v IIS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 934b5d16cdea7026e0e7874cf04ab53c8fbdf58e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>Postupy: Hostování služby WCF v IIS
Toto téma popisuje základní kroky potřebné pro vytvoření [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby, který je hostován v Internetové informační služby (IIS). Toto téma předpokládá se seznámíte se službou IIS a pochopit, jak vytvořit a spravovat aplikace služby IIS pomocí nástroje pro správu služby IIS. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Služba IIS najdete v části [Internetová informační služba](http://go.microsoft.com/fwlink/?LinkId=132449). A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba, která běží v prostředí služby IIS plně využívá funkce služby IIS, jako je recyklace procesů, nečinnosti vypnutí, monitorování stavu procesu a aktivace na základě zpráv. Tato možnost hostování vyžaduje, aby se služba IIS správně nakonfigurovaná, ale nevyžaduje, aby všechny hostování kódu zapsání jako součást aplikace. Můžete použít hostování IIS pouze s přenosového protokolu HTTP.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] interakci najdete v tématu [služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Konfigurace zabezpečení, najdete v části [zabezpečení](../../../../docs/framework/wcf/feature-details/security.md).  
  
 Zdroj kopírování tohoto příkladu, najdete v části [IIS hostování pomocí vloženého kódu](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).  
  
### <a name="to-create-a-service-hosted-by-iis"></a>Vytvoření služby hostované službou IIS  
  
1.  Zkontrolujte, zda je služba IIS nainstalovaná a spuštěná v počítači. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]instalace a konfigurace služby IIS najdete v části [instalace a konfigurace služby IIS 7.0](http://go.microsoft.com/fwlink/?LinkID=132128)  
  
2.  Vytvořte novou složku pro soubory aplikace s názvem "IISHostedCalcService", zajistěte, aby [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] má přístup k obsahu složky a vytvoření nové aplikace služby IIS, který je fyzicky umístěný v této aplikaci pomocí nástroje pro správu služby IIS adresář. Při vytváření alias pro použití adresáře aplikace "IISHostedCalc".  
  
3.  Vytvořte nový soubor s názvem "service.svc" v adresáři aplikace. Tento soubor upravit přidáním následující @ServiceHost elementu.  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>  
    ```  
  
4.  Vytvoření App_Code podadresáře v adresáři aplikace.  
  
5.  Vytvořte soubor kódu s názvem Service.cs v podadresáři App_Code.  
  
6.  Přidejte následující příkazy using do horní části souboru Service.cs.  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7.  Přidejte následující deklarace oboru názvů po použití příkazů.  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8.  Definování kontraktu služby uvnitř deklaraci oboru názvů, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. Implementujte kontrakt služby po službu smlouvy definice, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. Vytvořte soubor s názvem "Web.config" v adresáři aplikace a přidejte následující kód konfigurace do souboru. V době běhu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury používá informace vytvořit koncový bod, který klientské aplikace může komunikovat se službou.  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     Tento příklad explicitně určuje koncové body v konfiguračním souboru. Pokud jste ke službě nepřidávejte žádné koncové body, modul runtime přidá výchozí koncové body pro vás. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]výchozí koncové body, vazeb a chování najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
11. Pokud chcete mít jistotu, že služba je hostovaná správně, spusťte instanci Internet Explorer a přejděte na adresu URL služby:`http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>Příklad  
 Zde je, že úplný seznam všech kód pro služby IIS hostovanou službu kalkulačky.  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>Viz také  
 [Hostování v Internetové informační službě](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Služby hostování](../../../../docs/framework/wcf/hosting-services.md)  
 [Služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [Zabezpečení](../../../../docs/framework/wcf/feature-details/security.md)  
 [Hostování funkcí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)

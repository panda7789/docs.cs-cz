---
title: 'Postupy: Hostování služby WCF v IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: e9ff82d58f08d8c040984b37422a7048b9d4361d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878640"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>Postupy: Hostování služby WCF v IIS
Toto téma popisuje základní kroky potřebné k vytvoření služby Windows Communication Foundation (WCF), které je hostované v Internetové informační služby (IIS). Toto téma předpokládá se seznámíte se službou IIS a pochopit, jak vytvářet a spravovat aplikace služby IIS pomocí nástroje pro správu služby IIS. Další informace o službě IIS najdete v části [Internetová informační služba](https://go.microsoft.com/fwlink/?LinkId=132449). Služba WCF, která se spustí v prostředí služby IIS plně využívá funkce služby IIS, jako je například recyklace procesů, nečinnosti vypnutí, monitorování stavu procesu a aktivaci založenou na zprávách. Tato možnost hostování vyžaduje, aby byly správně konfigurovány služby IIS, ale nevyžaduje, že libovolný kód hostování se zapisují jako součást aplikace. Můžete použít hostování IIS pouze s přenos pomocí protokolu HTTP.  
  
 Další informace o interakci WCF a ASP.NET najdete v tématu [služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md). Další informace o konfiguraci zabezpečení najdete v tématu [zabezpečení](../../../../docs/framework/wcf/feature-details/security.md).  
  
 Pro zdrojovou kopii tohoto příkladu, naleznete v tématu [IIS hostování pomocí vloženého kódu](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).  
  
### <a name="to-create-a-service-hosted-by-iis"></a>Vytvoření služby hostované službou IIS.  
  
1. Zkontrolujte, zda je služba IIS na počítači nainstalovaná a spuštěná. Další informace o instalaci a konfiguraci služby IIS najdete v části [instalace a konfigurace služby IIS 7.0](https://go.microsoft.com/fwlink/?LinkID=132128)  
  
2. Vytvořte novou složku s názvem "IISHostedCalcService" souborů aplikace, ujistěte se, že technologie ASP.NET má přístup k obsahu složky a použít nástroj pro správu služby IIS k vytvoření nové aplikace služby IIS, který je fyzicky umístěný v adresáři této aplikace. Při vytváření aliasu pro použití aplikací adresáře "IISHostedCalc".  
  
3. Vytvořte nový soubor s názvem "service.svc" v adresáři aplikace. Tento soubor upravit přidáním následujícího kódu @ServiceHost elementu.  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>  
    ```  
  
4. Vytvoření App_Code podadresáře v adresáři aplikace.  
  
5. Vytvořte soubor kódu Service.cs v podadresáři App_Code.  
  
6. Přidejte následující příkazy using do horní části souboru Service.cs.  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. Přidejte následující deklarace oboru názvů po na pomocí příkazů.  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. Definování kontraktu služby uvnitř deklarace oboru názvů, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. Implementace kontraktu služby, po servisní smlouvy definice, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. Vytvořte soubor s názvem "Web.config" v adresáři aplikace a přidejte následující kód, konfigurace do souboru. Za běhu infrastruktura WCF používá informace k vytvoření koncového bodu, který můžou klienti komunikovat klientské aplikace.  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     Tento příklad explicitně určuje koncové body v konfiguračním souboru. Pokud nemůžete přidat žádné koncové body pro službu, modulu runtime přidá výchozí koncové body za vás. Další informace o výchozí koncové body, vazby a chování viz [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
11. Pokud chcete mít jistotu, že služba je hostována správně, spusťte instanci aplikace Internet Explorer a přejděte na adresu URL služby: `http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>Příklad  
 Zde je, že úplný výpis kódu pro IIS hostovanou službu kalkulačky.  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>Viz také:

- [Hostování v Internetové informační službě](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [Služby hostování](../../../../docs/framework/wcf/hosting-services.md)
- [Služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [Zabezpečení](../../../../docs/framework/wcf/feature-details/security.md)
- [Hostování funkcí systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)

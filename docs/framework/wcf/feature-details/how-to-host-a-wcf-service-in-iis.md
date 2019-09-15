---
title: 'Postupy: Hostování služby WCF v IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: ad1fb7d289dea3396b4edb4d3b3e9fb7fb1891e3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972412"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>Postupy: Hostování služby WCF v IIS
Toto téma popisuje základní kroky potřebné k vytvoření služby Windows Communication Foundation (WCF), která je hostovaná v Internetová informační služba (IIS). V tomto tématu se předpokládá, že jste obeznámeni se službou IIS a rozumíte tomu, jak pomocí nástroje pro správu služby IIS vytvářet a spravovat aplikace IIS. Další informace o službě IIS najdete v tématu [Internetová informační služba](https://go.microsoft.com/fwlink/?LinkId=132449). Služba WCF, která běží v prostředí služby IIS, má plně výhodu funkcí služby IIS, jako je recyklace procesů, nečinné vypnutí, monitorování stavu procesu a aktivace na základě zpráv. Tato možnost hostování vyžaduje, aby služba IIS byla správně nakonfigurovaná, ale nevyžaduje, aby se veškerý hostitelský kód napsal jako součást aplikace. Službu IIS můžete použít jenom s přenosem HTTP.  
  
 Další informace o tom, jak WCF a ASP.NET spolupracují, najdete v tématu [služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md). Další informace o konfiguraci zabezpečení najdete v tématu [zabezpečení](../../../../docs/framework/wcf/feature-details/security.md).  
  
 Zdrojovou kopii tohoto příkladu naleznete v tématu [hostování služby IIS pomocí vloženého kódu](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).  
  
### <a name="to-create-a-service-hosted-by-iis"></a>Vytvoření služby hostované službou IIS  
  
1. Ověřte, že je služba IIS v počítači nainstalovaná a spuštěná. Další informace o instalaci a konfiguraci služby IIS najdete v tématu [instalace a konfigurace služby iis 7,0](https://go.microsoft.com/fwlink/?LinkID=132128) .  
  
2. Vytvořte novou složku pro soubory aplikace nazvané "IISHostedCalcService", ujistěte se, že ASP.NET má přístup k obsahu složky, a pomocí nástroje pro správu služby IIS vytvořte novou aplikaci IIS, která je fyzicky umístěná v tomto adresáři aplikace. Při vytváření aliasu pro adresář aplikace použijte "IISHostedCalc".  
  
3. V adresáři aplikace vytvořte nový soubor s názvem Service. svc. Upravte tento soubor přidáním následujícího @ServiceHost elementu.  
  
   ```
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. Vytvořte podadresář App_Code v adresáři aplikace.  
  
5. V podadresáři App_Code vytvořte soubor kódu s názvem Service.cs.  
  
6. Do horní části souboru Service.cs přidejte následující příkazy using.  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. Po příkazech using přidejte následující deklaraci oboru názvů.  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. Definujte kontrakt služby uvnitř deklarace oboru názvů, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. Po definici kontraktu služby, jak je znázorněno v následujícím kódu, implementujte kontrakt služby.  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. Vytvořte soubor s názvem Web. config v adresáři aplikace a přidejte do souboru následující konfigurační kód. Infrastruktura WCF za běhu používá informace k vytvoření koncového bodu, se kterým můžou klientské aplikace komunikovat.  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     Tento příklad explicitně určuje koncové body v konfiguračním souboru. Pokud do služby nepřidáte žádné koncové body, modul runtime přidá pro vás výchozí koncové body. Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
11. Abyste se ujistili, že je služba hostovaná správně, otevřete instanci aplikace Internet Explorer a přejděte na adresu URL služby:`http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>Příklad  
 Následuje úplný seznam kódu pro službu IIS Hosted Kalkulačka.  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>Viz také:

- [Hostování v Internetové informační službě](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [Služby hostování](../../../../docs/framework/wcf/hosting-services.md)
- [Služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [Zabezpečení](../../../../docs/framework/wcf/feature-details/security.md)
- [Funkce hostování technologie Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)

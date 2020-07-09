---
title: 'Postupy: Hostování služby WCF v IIS'
description: Naučte se, jak vytvořit službu WCF, která je hostovaná ve službě Internetová informační služba (IIS). Službu IIS můžete použít jenom s přenosem HTTP.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 2ba0ae7adedc3bf0e0ca0cb92b4205edc968a5d8
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052010"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>Postupy: Hostování služby WCF v IIS
Toto téma popisuje základní kroky potřebné k vytvoření služby Windows Communication Foundation (WCF), která je hostovaná v Internetová informační služba (IIS). V tomto tématu se předpokládá, že jste obeznámeni se službou IIS a rozumíte tomu, jak pomocí nástroje pro správu služby IIS vytvářet a spravovat aplikace IIS. Další informace o službě IIS najdete v tématu [Internetová informační služba](https://www.iis.net/). Služba WCF, která běží v prostředí služby IIS, má plně výhodu funkcí služby IIS, jako je recyklace procesů, nečinné vypnutí, monitorování stavu procesu a aktivace na základě zpráv. Tato možnost hostování vyžaduje, aby služba IIS byla správně nakonfigurovaná, ale nevyžaduje, aby se veškerý hostitelský kód napsal jako součást aplikace. Službu IIS můžete použít jenom s přenosem HTTP.  
  
 Další informace o tom, jak WCF a ASP.NET spolupracují, najdete v tématu [služby WCF a ASP.NET](wcf-services-and-aspnet.md). Další informace o konfiguraci zabezpečení najdete v tématu [zabezpečení](security.md).  
  
 Zdrojovou kopii tohoto příkladu naleznete v tématu [hostování služby IIS pomocí vloženého kódu](../samples/iis-hosting-using-inline-code.md).  
  
### <a name="to-create-a-service-hosted-by-iis"></a>Vytvoření služby hostované službou IIS  
  
1. Ověřte, že je služba IIS v počítači nainstalovaná a spuštěná. Další informace o instalaci a konfiguraci služby IIS najdete v tématu [instalace a konfigurace služby iis 7,0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista) .  
  
2. Vytvořte novou složku pro soubory aplikace nazvané "IISHostedCalcService", ujistěte se, že ASP.NET má přístup k obsahu složky, a pomocí nástroje pro správu služby IIS vytvořte novou aplikaci IIS, která je fyzicky umístěná v tomto adresáři aplikace. Při vytváření aliasu pro adresář aplikace použijte "IISHostedCalc".  
  
3. V adresáři aplikace vytvořte nový soubor s názvem Service. svc. Upravte tento soubor přidáním následujícího @ServiceHost elementu.  
  
   ```aspx-csharp
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
  
10. Vytvořte soubor s názvem "Web.config" v adresáři aplikace a přidejte do souboru následující konfigurační kód. Infrastruktura WCF za běhu používá informace k vytvoření koncového bodu, se kterým můžou klientské aplikace komunikovat.  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]
  
     Tento příklad explicitně určuje koncové body v konfiguračním souboru. Pokud do služby nepřidáte žádné koncové body, modul runtime přidá pro vás výchozí koncové body. Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](../simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../samples/simplified-configuration-for-wcf-services.md).  
  
11. Abyste se ujistili, že je služba hostovaná správně, otevřete instanci aplikace Internet Explorer a přejděte na adresu URL služby:`http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>Příklad  
 Následuje úplný seznam kódu pro službu IIS Hosted Kalkulačka.  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)]
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)]
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>Viz také

- [Hostování v Internetové informační službě](hosting-in-internet-information-services.md)
- [Služby hostování](../hosting-services.md)
- [Služby WCF a ASP.NET](wcf-services-and-aspnet.md)
- [Zabezpečení](security.md)
- [Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))

---
title: 'Postupy: Konfigurace klienta základní Windows Communication Foundation'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
ms.openlocfilehash: 2866cbd5862bf55286fc771823488cf913863de2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855852"
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a>Postupy: Konfigurace klienta základní Windows Communication Foundation
Toto je pátý šesti úkolů, muset vytvořit základní aplikaci Windows Communication Foundation (WCF). Přehled všech šesti úkoly, naleznete v tématu [kurz Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.  
  
 Toto téma popisuje klientské konfigurační soubor, který se vygeneroval pomocí funkce Přidat odkaz na službu [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] nebo [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Konfigurace klienta se skládá z zadání koncového bodu, který klient používá pro přístup ke službě. Koncový bod má adresa, vazba a kontrakt a každý z nich musí být zadán právě konfigurace klienta.  
  
### <a name="to-configure-a-windows-communication-foundation-client"></a>Abyste mohli nakonfigurovat klienta Windows Communication Foundation  
  
1.  Z projektu GettingStartedClient otevřete vygenerovaný konfigurační soubor (App.config). V následujícím příkladu je zobrazení generovaného konfiguračního souboru. V části [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) části, vyhledejte [ \<koncový bod >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
        <startup>   
          <!-- specifies the version of WCF to use-->  
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />  
        </startup>  
        <system.serviceModel>  
            <bindings>  
                <!-- Uses wsHttpBinding-->  
                <wsHttpBinding>  
                    <binding name="WSHttpBinding_ICalculator" />  
                </wsHttpBinding>  
            </bindings>  
            <client>  
                <!-- specifies the endpoint to use when calling the service -->  
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"  
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"  
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">  
                    <identity>  
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />  
                    </identity>  
                </endpoint>  
            </client>  
        </system.serviceModel>  
    </configuration>   
    ```  
  
     Tento příklad konfiguruje koncového bodu, který klient používá pro přístup ke službě, která se nachází na následující adrese: http://localhost:8000/ServiceModelSamples/Service/CalculatorService  
  
     Určuje element koncového bodu, který `ServiceReference1.ICalculator` kontraktu služby se používá ke komunikaci mezi klienta WCF a službou. Kanál WCF se nakonfigurují poskytovaných systémem <xref:System.ServiceModel.WSHttpBinding>. Tato smlouva se vygeneroval pomocí přidat odkaz na službu v sadě Visual Studio. Je v podstatě kopií, která byla definována v projektu GettingStartedLib kontrakt. <xref:System.ServiceModel.WSHttpBinding> Vazbu určuje HTTP jako přenosu, interoperabilní zabezpečení a další podrobnosti o konfiguraci.  
  
2.  Další informace o tom, jak pomocí generovaného klienta s touto konfigurací najdete v tématu [postupy: používání klienta](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).  
  
## <a name="see-also"></a>Viz také  
 [Používání vazeb ke konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Nástroj metadat modelu služby (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Postupy: Vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Začínáme](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Vlastní hostování](../../../docs/framework/wcf/samples/self-host.md)

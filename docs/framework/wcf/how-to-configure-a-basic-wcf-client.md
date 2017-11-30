---
title: "Postupy: Konfigurace klienta základní Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
caps.latest.revision: "47"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1f4d6b5386e82a2052182ba3f4a929de13b27c22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a>Postupy: Konfigurace klienta základní Windows Communication Foundation
Toto je pátý šesti úkoly vyžadované pro vytvoření základní [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikace. Přehled všech šest úloh najdete v tématu [kurzu Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.  
  
 Toto téma disuccess konfiguračního souboru klienta, který byl vytvořen pomocí funkce Přidat odkaz na službu [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] nebo [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Konfigurace klienta se skládá z určení koncového bodu, který klient používá k přístupu ke službě. Koncový bod má adresy, vazby a kontraktu a každý z nich musí být zadán právě konfigurace klienta.  
  
### <a name="to-configure-a-windows-communication-foundation-client"></a>Abyste mohli nakonfigurovat klienta Windows Communication Foundation  
  
1.  Otevřete generovaný konfigurační soubor (App.config) z GettingStartedClient projektu. V následujícím příkladu je zobrazení generovaného konfiguračního souboru. V části [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) část, vyhledejte [ \<endpoint >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element.  
  
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
  
     Tento příklad konfiguruje koncového bodu, který klient používá k přístupu ke službě, který se nachází na následující adrese: http://localhost: 8000/ServiceModelSamples/Service/CalculatorService  
  
     Element koncového bodu určuje, že `ServiceReference1.ICalculator` kontrakt služby se používá ke komunikaci mezi klienta WCF a službou. Kanál WCF je nakonfigurován s poskytované systémem <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>. Tento kontrakt byl vytvořen pomocí přidat odkaz na službu v sadě Visual Studio. Je v podstatě kopií kontrakt, který byl definován v GettingStartedLib projektu. <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> Vazba určuje HTTP jako přenos, umožňuje vzájemnou spolupráci zabezpečení a další podrobnosti o konfiguraci.  
  
2.  [!INCLUDE[crabout](../../../includes/crabout-md.md)]Pomocí této konfigurace pomocí generovaného klienta najdete v tématu [postupy: používání klienta](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).  
  
## <a name="see-also"></a>Viz také  
 [Používání vazeb ke konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Nástroj ServiceModel Metadata Utility (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Postupy: vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Začínáme](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Vlastní hostování](../../../docs/framework/wcf/samples/self-host.md)

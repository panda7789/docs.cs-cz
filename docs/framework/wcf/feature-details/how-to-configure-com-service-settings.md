---
title: "Postupy: Konfigurace nastavení služby COM +"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1bdbdbae857685ddb447843fd704896de018b1c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-com-service-settings"></a>Postupy: Konfigurace nastavení služby COM +
Při aplikační rozhraní přidat nebo odebrat pomocí nástroje Konfigurace služby COM +, konfigurace webové služby je aktualizovat v rámci konfiguračního souboru aplikace. V modelu COM + hostované režimu, je umístěn soubor Application.config v kořenovém adresáři aplikace (%PROGRAMFILES%\ComPlus aplikace\\{appid} je výchozí nastavení). V některém z webových hostované režimy v souboru Web.config je umístěn v adresáři zadaný virtuální kořenový adresář.  
  
> [!NOTE]
>  Podepisování zpráv slouží jako ochrana proti manipulaci zpráv mezi klientem a serverem. Navíc zpráva nebo transport layer šifrování slouží k ochraně proti úniku informací z zpráv mezi klientem a serverem. Stejně jako u [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby, měli byste použít omezení k omezit počet souběžných volání, připojení, instancí a čekající operace. To pomáhá zabránit nadměrné spotřeby prostředků. Omezení chování se specifikuje prostřednictvím nastavení konfiguračního souboru služby.  
  
## <a name="example"></a>Příklad  
 Vezměte v úvahu komponenty, která implementuje rozhraní následující:  
  
```  
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 Pokud je součást vystavený jako webovou službu, na odpovídající kontrakt služby, který je vystaven, a klienti potřebovat tak, aby odpovídala, vypadá takto:  
  
```  
[ServiceContract(Session = true,  
Namespace = "http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7",  
Name = "IFinances")]  
public interface IFinancesContract : IDisposable  
{  
    [OperationContract]  
    string Debit(string accountNo, double amount);  
    [OperationContract]  
    string Credit(string accountNo, double amount);  
}  
```  
  
> [!NOTE]
>  Identifikátory IID je součástí počáteční obor názvů pro kontrakt.  
  
 Klientské aplikace, které používají tuto službu potřebovat tak, aby odpovídala tento kontrakt, společně s použitím vazby, který je kompatibilní s verze zadaná v konfiguraci aplikace.  
  
 Následující příklad kódu ukazuje výchozí konfigurační soubor. Probíhá [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] webové služby, to odpovídá schématu konfigurace modelu služby na úrovni standard a lze ho upravovat v stejným způsobem jako ostatní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služeb konfigurační soubory.  
  
 Typické úpravy by mělo zahrnovat:  
  
-   Změna adresa koncového bodu z výchozího formuláře ApplicationName/ComponentName/InterfaceName na více použitelné podoby.  
  
-   Úprava oboru názvů služby z výchozího formuláře "http://tempuri.org/InterfaceID" relevantnější formuláře.  
  
-   Změna koncový bod používat různé přenosové vazby.  
  
     V modelu COM +-hostované případě přenosu pojmenované kanály se používá ve výchozím nastavení, ale místo toho lze použít přenosu vypnout počítač jako TCP.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="comNonTransactionalBinding" />  
                <binding name="comTransactionalBinding" transactionFlow="true" />  
            </netNamedPipeBinding>  
        </bindings>  
        <comContracts>  
            <comContract contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"  
                name="IFinances" namespace="http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7"  
                requiresSession="true">  
                <exposedMethods>  
                    <add exposedMethod="Debit" />  
                    <add exposedMethod="Credit" />  
                </exposedMethods>  
            </comContract>  
        </comContracts>  
        <services>  
            <service name="{DCDB24CC-0B19-4534-95CD-FBBFF4D67DD9},{C942B840-AD54-4A44-B5F7-928130980AB9}">  
                <endpoint address="IFinances" binding="netNamedPipeBinding" bindingConfiguration="comNonTransactionalBinding"  
                    contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" />  
                <host>  
                    <baseAddresses>  
                        <add baseAddress="net.pipe://localhost/ServiceModelDocSampleApp/ServiceModelDocSample.esFinance" />  
                    </baseAddresses>  
                </host>  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Integrace s aplikacemi modelu COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)

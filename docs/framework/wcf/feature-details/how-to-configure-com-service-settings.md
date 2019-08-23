---
title: 'Postupy: Konfigurace nastavení služby modelu COM+'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
ms.openlocfilehash: 58845ab7b9da7377f4fdaa7da13e7c407226d63c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912209"
---
# <a name="how-to-configure-com-service-settings"></a>Postupy: Konfigurace nastavení služby modelu COM+
Při přidání nebo odebrání rozhraní aplikace pomocí nástroje pro konfiguraci služby COM+ se konfigurace webové služby aktualizuje v konfiguračním souboru aplikace. V hostovaném režimu modelu COM+ je soubor Application. config umístěn v kořenovém adresáři aplikace (výchozí je aplikace\\%ProgramFiles%\ComPlus {AppID}). V obou režimech hostovaných na webu je soubor Web. config umístěný v zadaném adresáři vroot.  
  
> [!NOTE]
> K ochraně proti manipulaci se zprávami mezi klientem a serverem se musí použít podepisování zpráv. K ochraně před zpřístupněním informací ze zpráv mezi klientem a serverem by se měla použít taky zpráva nebo šifrování transportní vrstvy. Stejně jako u služby Windows Communication Foundation (WCF) byste měli omezit počet souběžných volání, připojení, instancí a probíhajících operací pomocí omezování. To pomáhá zabránit vyšší spotřebě prostředků. Chování omezování se zadává prostřednictvím nastavení konfiguračního souboru služby.  
  
## <a name="example"></a>Příklad  
 Vezměte v úvahu komponentu, která implementuje toto rozhraní:  
  
```  
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 Pokud je tato součást vystavena jako webová služba, zobrazí se odpovídající kontrakt služby, který je vystavený a že klienti musí splňovat tyto požadavky:  
  
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
> IID Forms část počátečního oboru názvů pro kontrakt.  
  
 Klientské aplikace, které používají tuto službu, musí být v souladu s touto smlouvou, a to spolu s použitím vazby, která je kompatibilní s parametrem zadaným v konfiguraci aplikace.  
  
 Následující příklad kódu ukazuje výchozí konfigurační soubor. Jedná se o webovou službu Windows Communication Foundation (WCF), která odpovídá standardnímu schématu konfigurace služby Service Model a dá se upravit stejným způsobem jako ostatní konfigurační soubory služby WCF.  
  
 Mezi typické úpravy patří:  
  
- Změna adresy koncového bodu z výchozího formuláře ApplicationName/InterfaceName/Název_rozhraní na více použitelné formuláře.  
  
- Úprava oboru názvů služby z výchozího `http://tempuri.org/InterfaceID` formuláře na relevantnější formulář.  
  
- Změna koncového bodu na použití jiné vazby přenosu.  
  
     V případě hostovaného v modelu COM+ se ve výchozím nastavení používá přenos pojmenovaných kanálů, ale místo toho se dá použít přenos z počítače, jako je TCP.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Integrace s aplikacemi modelu COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)

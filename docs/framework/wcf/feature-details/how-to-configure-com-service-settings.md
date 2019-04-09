---
title: 'Postupy: Konfigurace nastavení služby modelu COM+'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
ms.openlocfilehash: dd5625fd3f2c0cc2e1e2a261b091a029cd4226ed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195836"
---
# <a name="how-to-configure-com-service-settings"></a>Postupy: Konfigurace nastavení služby modelu COM+
Když rozhraním aplikace přidá nebo odebere pomocí nástroje Konfigurace služby COM +, aktualizuje se konfigurace webové služby v konfiguračním souboru aplikace. V režimu hostovány COM +, souboru Application.config nachází v kořenovém adresáři aplikace (%PROGRAMFILES%\ComPlus aplikace\\{appid} je výchozí nastavení). V některém z webových hostované režimy v souboru Web.config je umístěn v adresáři zadaný virtuální kořenový adresář.  
  
> [!NOTE]
>  Podepisování zpráv by měla sloužit k ochraně proti padělání zpráv mezi klientem a serverem. Navíc by měla sloužit k ochraně proti zpřístupnění informací ze zpráv mezi klientem a serverem vrstvě šifrování zprávy nebo přenos. Stejně jako u služeb Windows Communication Foundation (WCF), měli byste použít omezení šířky pásma pro omezení počtu souběžných volání, připojení, instance a čekajících operací. To pomáhá zabránit typu over-pass-the spotřebu prostředků. Chování při omezování chování se specifikuje prostřednictvím nastavení konfiguračního souboru služby.  
  
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
  
 Pokud součást vystavena jako webové služby, odpovídající kontraktu služby, který je přístupný a že klienti by se musí odpovídat, vypadá takto:  
  
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
>  Identifikátor IID součástí počáteční obor názvů pro kontrakt.  
  
 Klientské aplikace, které používají tuto službu by bylo potřeba v souladu s touto smlouvou, spolu s využitím vazbu, která je kompatibilní s délkou zadanou v konfiguraci aplikace.  
  
 Následující příklad kódu ukazuje výchozí konfigurační soubor. Windows Communication Foundation (WCF) webové služby, to odpovídá schématu konfigurace model služeb standard služby a můžete upravit stejným způsobem jako ostatní konfigurační soubory služby WCF.  
  
 Typické změny bude zahrnovat:  
  
- Adresa koncového bodu z výchozí formulář ApplicationName/ComponentName/InterfaceName se mění na více použitelné podoby.  
  
- Úprava oboru názvů služby z výchozího `http://tempuri.org/InterfaceID` formuláře relevantnější formuláře.  
  
- Změna koncového bodu používat různé přenosové vazby.  
  
     V modelu COM +-hostované případu, přenos pojmenované kanály se používá ve výchozím nastavení, ale místo toho lze použít přenosu vypnout počítač např. TCP.  
  
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

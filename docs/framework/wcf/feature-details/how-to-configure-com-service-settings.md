---
title: 'Postupy: Konfigurace nastavení služby modelu COM+'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
ms.openlocfilehash: 8deb7be51cdf3273a57d6777b103123636a2d2f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637395"
---
# <a name="how-to-configure-com-service-settings"></a><span data-ttu-id="5f00d-102">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="5f00d-102">How to: Configure COM+ Service Settings</span></span>
<span data-ttu-id="5f00d-103">Když rozhraním aplikace přidá nebo odebere pomocí nástroje Konfigurace služby COM +, aktualizuje se konfigurace webové služby v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="5f00d-103">When an application interface is added or removed by using the COM+ Service Configuration tool, the Web service configuration is updated within the application's configuration file.</span></span> <span data-ttu-id="5f00d-104">V režimu hostovány COM +, souboru Application.config nachází v kořenovém adresáři aplikace (%PROGRAMFILES%\ComPlus aplikace\\{appid} je výchozí nastavení).</span><span class="sxs-lookup"><span data-stu-id="5f00d-104">In the COM+ hosted mode, the Application.config file is placed in the Application Root Directory (%PROGRAMFILES%\ComPlus Applications\\{appid} is the default).</span></span> <span data-ttu-id="5f00d-105">V některém z webových hostované režimy v souboru Web.config je umístěn v adresáři zadaný virtuální kořenový adresář.</span><span class="sxs-lookup"><span data-stu-id="5f00d-105">In either of the Web-hosted modes, the Web.config file is placed in the specified vroot directory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f00d-106">Podepisování zpráv by měla sloužit k ochraně proti padělání zpráv mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="5f00d-106">Message signing should be used to protect against tampering of messages between a client and a server.</span></span> <span data-ttu-id="5f00d-107">Navíc by měla sloužit k ochraně proti zpřístupnění informací ze zpráv mezi klientem a serverem vrstvě šifrování zprávy nebo přenos.</span><span class="sxs-lookup"><span data-stu-id="5f00d-107">Also, message or transport layer encryption should be used to protect against information disclosure from messages between a client and a server.</span></span> <span data-ttu-id="5f00d-108">Stejně jako u služeb Windows Communication Foundation (WCF), měli byste použít omezení šířky pásma pro omezení počtu souběžných volání, připojení, instance a čekajících operací.</span><span class="sxs-lookup"><span data-stu-id="5f00d-108">As with Windows Communication Foundation (WCF) services, you should use throttling to limit the number of concurrent calls, connections, instances, and pending operations.</span></span> <span data-ttu-id="5f00d-109">To pomáhá zabránit typu over-pass-the spotřebu prostředků.</span><span class="sxs-lookup"><span data-stu-id="5f00d-109">This helps prevent over-consumption of resources.</span></span> <span data-ttu-id="5f00d-110">Chování při omezování chování se specifikuje prostřednictvím nastavení konfiguračního souboru služby.</span><span class="sxs-lookup"><span data-stu-id="5f00d-110">Throttling behavior is specified through service configuration file settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f00d-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="5f00d-111">Example</span></span>  
 <span data-ttu-id="5f00d-112">Vezměte v úvahu komponenty, která implementuje rozhraní následující:</span><span class="sxs-lookup"><span data-stu-id="5f00d-112">Consider a component that implements the following interface:</span></span>  
  
```  
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 <span data-ttu-id="5f00d-113">Pokud součást vystavena jako webové služby, odpovídající kontraktu služby, který je přístupný a že klienti by se musí odpovídat, vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="5f00d-113">If the component is exposed as a Web service, the corresponding service contract that is exposed, and that clients would need to conform to, is as follows:</span></span>  
  
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
>  <span data-ttu-id="5f00d-114">Identifikátor IID součástí počáteční obor názvů pro kontrakt.</span><span class="sxs-lookup"><span data-stu-id="5f00d-114">IID forms part of the initial namespace for the contract.</span></span>  
  
 <span data-ttu-id="5f00d-115">Klientské aplikace, které používají tuto službu by bylo potřeba v souladu s touto smlouvou, spolu s využitím vazbu, která je kompatibilní s délkou zadanou v konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="5f00d-115">Client applications that use this service would need to conform to this contract, along with using a binding that is compatible with the one specified in the application configuration.</span></span>  
  
 <span data-ttu-id="5f00d-116">Následující příklad kódu ukazuje výchozí konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="5f00d-116">The following code example shows a default configuration file.</span></span> <span data-ttu-id="5f00d-117">Windows Communication Foundation (WCF) webové služby, to odpovídá schématu konfigurace model služeb standard služby a můžete upravit stejným způsobem jako ostatní konfigurační soubory služby WCF.</span><span class="sxs-lookup"><span data-stu-id="5f00d-117">Being a Windows Communication Foundation (WCF) Web service, this conforms to the standard service model configuration schema and can be edited in the same way as other WCF services configuration files.</span></span>  
  
 <span data-ttu-id="5f00d-118">Typické změny bude zahrnovat:</span><span class="sxs-lookup"><span data-stu-id="5f00d-118">Typical modifications would include:</span></span>  
  
- <span data-ttu-id="5f00d-119">Adresa koncového bodu z výchozí formulář ApplicationName/ComponentName/InterfaceName se mění na více použitelné podoby.</span><span class="sxs-lookup"><span data-stu-id="5f00d-119">Changing the endpoint address from the default ApplicationName/ComponentName/InterfaceName form to a more usable form.</span></span>  
  
- <span data-ttu-id="5f00d-120">Úprava oboru názvů služby z výchozího `http://tempuri.org/InterfaceID` formuláře relevantnější formuláře.</span><span class="sxs-lookup"><span data-stu-id="5f00d-120">Modifying the namespace of the service from the default `http://tempuri.org/InterfaceID` form to a more relevant form.</span></span>  
  
- <span data-ttu-id="5f00d-121">Změna koncového bodu používat různé přenosové vazby.</span><span class="sxs-lookup"><span data-stu-id="5f00d-121">Changing the endpoint to use a different transport binding.</span></span>  
  
     <span data-ttu-id="5f00d-122">V modelu COM +-hostované případu, přenos pojmenované kanály se používá ve výchozím nastavení, ale místo toho lze použít přenosu vypnout počítač např. TCP.</span><span class="sxs-lookup"><span data-stu-id="5f00d-122">In the COM+-hosted case, the named pipes transport is used by default, but an off-machine transport like TCP can be used instead.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5f00d-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f00d-123">See also</span></span>
- [<span data-ttu-id="5f00d-124">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="5f00d-124">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)

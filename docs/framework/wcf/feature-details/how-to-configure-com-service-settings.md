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
# <a name="how-to-configure-com-service-settings"></a><span data-ttu-id="5c24c-102">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="5c24c-102">How to: Configure COM+ Service Settings</span></span>
<span data-ttu-id="5c24c-103">Při přidání nebo odebrání rozhraní aplikace pomocí nástroje pro konfiguraci služby COM+ se konfigurace webové služby aktualizuje v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="5c24c-103">When an application interface is added or removed by using the COM+ Service Configuration tool, the Web service configuration is updated within the application's configuration file.</span></span> <span data-ttu-id="5c24c-104">V hostovaném režimu modelu COM+ je soubor Application. config umístěn v kořenovém adresáři aplikace (výchozí je aplikace\\%ProgramFiles%\ComPlus {AppID}).</span><span class="sxs-lookup"><span data-stu-id="5c24c-104">In the COM+ hosted mode, the Application.config file is placed in the Application Root Directory (%PROGRAMFILES%\ComPlus Applications\\{appid} is the default).</span></span> <span data-ttu-id="5c24c-105">V obou režimech hostovaných na webu je soubor Web. config umístěný v zadaném adresáři vroot.</span><span class="sxs-lookup"><span data-stu-id="5c24c-105">In either of the Web-hosted modes, the Web.config file is placed in the specified vroot directory.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5c24c-106">K ochraně proti manipulaci se zprávami mezi klientem a serverem se musí použít podepisování zpráv.</span><span class="sxs-lookup"><span data-stu-id="5c24c-106">Message signing should be used to protect against tampering of messages between a client and a server.</span></span> <span data-ttu-id="5c24c-107">K ochraně před zpřístupněním informací ze zpráv mezi klientem a serverem by se měla použít taky zpráva nebo šifrování transportní vrstvy.</span><span class="sxs-lookup"><span data-stu-id="5c24c-107">Also, message or transport layer encryption should be used to protect against information disclosure from messages between a client and a server.</span></span> <span data-ttu-id="5c24c-108">Stejně jako u služby Windows Communication Foundation (WCF) byste měli omezit počet souběžných volání, připojení, instancí a probíhajících operací pomocí omezování.</span><span class="sxs-lookup"><span data-stu-id="5c24c-108">As with Windows Communication Foundation (WCF) services, you should use throttling to limit the number of concurrent calls, connections, instances, and pending operations.</span></span> <span data-ttu-id="5c24c-109">To pomáhá zabránit vyšší spotřebě prostředků.</span><span class="sxs-lookup"><span data-stu-id="5c24c-109">This helps prevent over-consumption of resources.</span></span> <span data-ttu-id="5c24c-110">Chování omezování se zadává prostřednictvím nastavení konfiguračního souboru služby.</span><span class="sxs-lookup"><span data-stu-id="5c24c-110">Throttling behavior is specified through service configuration file settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c24c-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="5c24c-111">Example</span></span>  
 <span data-ttu-id="5c24c-112">Vezměte v úvahu komponentu, která implementuje toto rozhraní:</span><span class="sxs-lookup"><span data-stu-id="5c24c-112">Consider a component that implements the following interface:</span></span>  
  
```  
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 <span data-ttu-id="5c24c-113">Pokud je tato součást vystavena jako webová služba, zobrazí se odpovídající kontrakt služby, který je vystavený a že klienti musí splňovat tyto požadavky:</span><span class="sxs-lookup"><span data-stu-id="5c24c-113">If the component is exposed as a Web service, the corresponding service contract that is exposed, and that clients would need to conform to, is as follows:</span></span>  
  
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
> <span data-ttu-id="5c24c-114">IID Forms část počátečního oboru názvů pro kontrakt.</span><span class="sxs-lookup"><span data-stu-id="5c24c-114">IID forms part of the initial namespace for the contract.</span></span>  
  
 <span data-ttu-id="5c24c-115">Klientské aplikace, které používají tuto službu, musí být v souladu s touto smlouvou, a to spolu s použitím vazby, která je kompatibilní s parametrem zadaným v konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="5c24c-115">Client applications that use this service would need to conform to this contract, along with using a binding that is compatible with the one specified in the application configuration.</span></span>  
  
 <span data-ttu-id="5c24c-116">Následující příklad kódu ukazuje výchozí konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="5c24c-116">The following code example shows a default configuration file.</span></span> <span data-ttu-id="5c24c-117">Jedná se o webovou službu Windows Communication Foundation (WCF), která odpovídá standardnímu schématu konfigurace služby Service Model a dá se upravit stejným způsobem jako ostatní konfigurační soubory služby WCF.</span><span class="sxs-lookup"><span data-stu-id="5c24c-117">Being a Windows Communication Foundation (WCF) Web service, this conforms to the standard service model configuration schema and can be edited in the same way as other WCF services configuration files.</span></span>  
  
 <span data-ttu-id="5c24c-118">Mezi typické úpravy patří:</span><span class="sxs-lookup"><span data-stu-id="5c24c-118">Typical modifications would include:</span></span>  
  
- <span data-ttu-id="5c24c-119">Změna adresy koncového bodu z výchozího formuláře ApplicationName/InterfaceName/Název_rozhraní na více použitelné formuláře.</span><span class="sxs-lookup"><span data-stu-id="5c24c-119">Changing the endpoint address from the default ApplicationName/ComponentName/InterfaceName form to a more usable form.</span></span>  
  
- <span data-ttu-id="5c24c-120">Úprava oboru názvů služby z výchozího `http://tempuri.org/InterfaceID` formuláře na relevantnější formulář.</span><span class="sxs-lookup"><span data-stu-id="5c24c-120">Modifying the namespace of the service from the default `http://tempuri.org/InterfaceID` form to a more relevant form.</span></span>  
  
- <span data-ttu-id="5c24c-121">Změna koncového bodu na použití jiné vazby přenosu.</span><span class="sxs-lookup"><span data-stu-id="5c24c-121">Changing the endpoint to use a different transport binding.</span></span>  
  
     <span data-ttu-id="5c24c-122">V případě hostovaného v modelu COM+ se ve výchozím nastavení používá přenos pojmenovaných kanálů, ale místo toho se dá použít přenos z počítače, jako je TCP.</span><span class="sxs-lookup"><span data-stu-id="5c24c-122">In the COM+-hosted case, the named pipes transport is used by default, but an off-machine transport like TCP can be used instead.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5c24c-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c24c-123">See also</span></span>

- [<span data-ttu-id="5c24c-124">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="5c24c-124">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)

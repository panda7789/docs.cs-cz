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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7cbe038b55358ec8607d54b67861ef1743c2e301
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-configure-com-service-settings"></a><span data-ttu-id="a5d40-102">Postupy: Konfigurace nastavení služby COM +</span><span class="sxs-lookup"><span data-stu-id="a5d40-102">How to: Configure COM+ Service Settings</span></span>
<span data-ttu-id="a5d40-103">Při aplikační rozhraní přidat nebo odebrat pomocí nástroje Konfigurace služby COM +, konfigurace webové služby je aktualizovat v rámci konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="a5d40-103">When an application interface is added or removed by using the COM+ Service Configuration tool, the Web service configuration is updated within the application's configuration file.</span></span> <span data-ttu-id="a5d40-104">V modelu COM + hostované režimu, je umístěn soubor Application.config v kořenovém adresáři aplikace (%PROGRAMFILES%\ComPlus aplikace\\{appid} je výchozí nastavení).</span><span class="sxs-lookup"><span data-stu-id="a5d40-104">In the COM+ hosted mode, the Application.config file is placed in the Application Root Directory (%PROGRAMFILES%\ComPlus Applications\\{appid} is the default).</span></span> <span data-ttu-id="a5d40-105">V některém z webových hostované režimy v souboru Web.config je umístěn v adresáři zadaný virtuální kořenový adresář.</span><span class="sxs-lookup"><span data-stu-id="a5d40-105">In either of the Web-hosted modes, the Web.config file is placed in the specified vroot directory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5d40-106">Podepisování zpráv slouží jako ochrana proti manipulaci zpráv mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="a5d40-106">Message signing should be used to protect against tampering of messages between a client and a server.</span></span> <span data-ttu-id="a5d40-107">Navíc zpráva nebo transport layer šifrování slouží k ochraně proti úniku informací z zpráv mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="a5d40-107">Also, message or transport layer encryption should be used to protect against information disclosure from messages between a client and a server.</span></span> <span data-ttu-id="a5d40-108">Stejně jako u [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby, měli byste použít omezení k omezit počet souběžných volání, připojení, instancí a čekající operace.</span><span class="sxs-lookup"><span data-stu-id="a5d40-108">As with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services, you should use throttling to limit the number of concurrent calls, connections, instances, and pending operations.</span></span> <span data-ttu-id="a5d40-109">To pomáhá zabránit nadměrné spotřeby prostředků.</span><span class="sxs-lookup"><span data-stu-id="a5d40-109">This helps prevent over-consumption of resources.</span></span> <span data-ttu-id="a5d40-110">Omezení chování se specifikuje prostřednictvím nastavení konfiguračního souboru služby.</span><span class="sxs-lookup"><span data-stu-id="a5d40-110">Throttling behavior is specified through service configuration file settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5d40-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5d40-111">Example</span></span>  
 <span data-ttu-id="a5d40-112">Vezměte v úvahu komponenty, která implementuje rozhraní následující:</span><span class="sxs-lookup"><span data-stu-id="a5d40-112">Consider a component that implements the following interface:</span></span>  
  
```  
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 <span data-ttu-id="a5d40-113">Pokud je součást vystavený jako webovou službu, na odpovídající kontrakt služby, který je vystaven, a klienti potřebovat tak, aby odpovídala, vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="a5d40-113">If the component is exposed as a Web service, the corresponding service contract that is exposed, and that clients would need to conform to, is as follows:</span></span>  
  
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
>  <span data-ttu-id="a5d40-114">Identifikátory IID je součástí počáteční obor názvů pro kontrakt.</span><span class="sxs-lookup"><span data-stu-id="a5d40-114">IID forms part of the initial namespace for the contract.</span></span>  
  
 <span data-ttu-id="a5d40-115">Klientské aplikace, které používají tuto službu potřebovat tak, aby odpovídala tento kontrakt, společně s použitím vazby, který je kompatibilní s verze zadaná v konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="a5d40-115">Client applications that use this service would need to conform to this contract, along with using a binding that is compatible with the one specified in the application configuration.</span></span>  
  
 <span data-ttu-id="a5d40-116">Následující příklad kódu ukazuje výchozí konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="a5d40-116">The following code example shows a default configuration file.</span></span> <span data-ttu-id="a5d40-117">Probíhá [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] webové služby, to odpovídá schématu konfigurace modelu služby na úrovni standard a lze ho upravovat v stejným způsobem jako ostatní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služeb konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="a5d40-117">Being a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web service, this conforms to the standard service model configuration schema and can be edited in the same way as other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services configuration files.</span></span>  
  
 <span data-ttu-id="a5d40-118">Typické úpravy by mělo zahrnovat:</span><span class="sxs-lookup"><span data-stu-id="a5d40-118">Typical modifications would include:</span></span>  
  
-   <span data-ttu-id="a5d40-119">Změna adresa koncového bodu z výchozího formuláře ApplicationName/ComponentName/InterfaceName na více použitelné podoby.</span><span class="sxs-lookup"><span data-stu-id="a5d40-119">Changing the endpoint address from the default ApplicationName/ComponentName/InterfaceName form to a more usable form.</span></span>  
  
-   <span data-ttu-id="a5d40-120">Úprava oboru názvů služby z výchozího formuláře "http://tempuri.org/InterfaceID" relevantnější formuláře.</span><span class="sxs-lookup"><span data-stu-id="a5d40-120">Modifying the namespace of the service from the default "http://tempuri.org/InterfaceID" form to a more relevant form.</span></span>  
  
-   <span data-ttu-id="a5d40-121">Změna koncový bod používat různé přenosové vazby.</span><span class="sxs-lookup"><span data-stu-id="a5d40-121">Changing the endpoint to use a different transport binding.</span></span>  
  
     <span data-ttu-id="a5d40-122">V modelu COM +-hostované případě přenosu pojmenované kanály se používá ve výchozím nastavení, ale místo toho lze použít přenosu vypnout počítač jako TCP.</span><span class="sxs-lookup"><span data-stu-id="a5d40-122">In the COM+-hosted case, the named pipes transport is used by default, but an off-machine transport like TCP can be used instead.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a5d40-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5d40-123">See Also</span></span>  
 [<span data-ttu-id="a5d40-124">Integrace s aplikacemi modelu COM +</span><span class="sxs-lookup"><span data-stu-id="a5d40-124">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)

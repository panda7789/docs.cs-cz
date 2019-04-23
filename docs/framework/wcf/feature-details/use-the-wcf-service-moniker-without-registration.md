---
title: 'Postupy: Použití monikeru služby Windows Communication Foundation bez registrace'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: be4798663d0b39301ec496df45a4a7a5bf9c88e5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203974"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a><span data-ttu-id="74c21-102">Postupy: Použití monikeru služby Windows Communication Foundation bez registrace</span><span class="sxs-lookup"><span data-stu-id="74c21-102">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>
<span data-ttu-id="74c21-103">K připojení a komunikovat se službou Windows Communication Foundation (WCF), musí mít klientská aplikace WCF podrobnosti adresu služby, konfigurace vazby a kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="74c21-103">To connect to and communicate with a Windows Communication Foundation (WCF) service, a WCF client application must have the details of the service address, the binding configuration, and the service contract.</span></span>  
  
 <span data-ttu-id="74c21-104">Monikeru služby WCF obvykle získá požadované smlouvy prostřednictvím předchozí registrace typů požadovaný atribut, ale můžou nastat případy, kdy to není proveditelné.</span><span class="sxs-lookup"><span data-stu-id="74c21-104">The WCF service moniker typically obtains the required contract through prior registration of the required attribute types, but there might be cases where this is not feasible.</span></span> <span data-ttu-id="74c21-105">Zástupný název místo registrace, můžete získat definici kontraktu ve formě dokumentem definice jazyka WSDL (Web Services) prostřednictvím `wsdl` parametr nebo prostřednictvím výměny metadat prostřednictvím použití `mexAddress` parametr.</span><span class="sxs-lookup"><span data-stu-id="74c21-105">In place of registration, the moniker can obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document, through the use of the `wsdl` parameter or through Metadata Exchange, through the use of the `mexAddress` parameter.</span></span>  
  
 <span data-ttu-id="74c21-106">To umožňuje scénáře, jako je distribuce tabulky aplikace Excel, kde některé z hodnot buňky se počítají prostřednictvím interakce webové služby.</span><span class="sxs-lookup"><span data-stu-id="74c21-106">This enables scenarios such as the distribution of an Excel spreadsheet where some of the cell values are calculated through Web service interactions.</span></span> <span data-ttu-id="74c21-107">V tomto scénáři nemusí být možné zaregistrovat sestavení kontraktu služby ve všech klientech, které může otevřít dokument.</span><span class="sxs-lookup"><span data-stu-id="74c21-107">In this scenario, it might not be feasible to register the service contract assembly on all clients that might open the document.</span></span> <span data-ttu-id="74c21-108">`wsdl` Parametr nebo `mexAddress` parametr povoluje samostatná řešení.</span><span class="sxs-lookup"><span data-stu-id="74c21-108">The `wsdl` parameter or the `mexAddress` parameter enables a self-contained solution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74c21-109">Vzájemné ověřování musí použít pro ochranu před žádostí a odpovědí, manipulaci nebo falšování identity.</span><span class="sxs-lookup"><span data-stu-id="74c21-109">Mutual authentication must be used to protect against request and response tampering or spoofing.</span></span> <span data-ttu-id="74c21-110">Konkrétně je důležité pro klienty být jistí, že je koncový bod výměny metadat, který odpovídá určené důvěryhodná strana.</span><span class="sxs-lookup"><span data-stu-id="74c21-110">Specifically, it is important for clients to be assured that the Metadata Exchange endpoint that is responding is the intended trusted party.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74c21-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="74c21-111">Example</span></span>  
 <span data-ttu-id="74c21-112">Tento příklad ukazuje použití monikeru služby s kontraktem MEX.</span><span class="sxs-lookup"><span data-stu-id="74c21-112">This example shows the use of the service moniker with a MEX contract.</span></span> <span data-ttu-id="74c21-113">Služba s tímto kontraktem je vystavena s wsHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="74c21-113">A service with the following contract is exposed with a wsHttpBinding.</span></span>  
  
```  
using System.ServiceModel;  
  
...  
  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Demo")]  
public interface IAffiliate  
{  
    [OperationContract]  
    bool NewAffiliate(string ID, string company, string fullname, string accountsCode);  
    [OperationContract]  
    bool RemoveAffiliate(string ID);  
    [OperationContract]  
    double RevenueCheckMonthly(ref string ID);  
    [OperationContract]  
    double RevenueCheckTotal(ref string ID);  
}  
```  
  
 <span data-ttu-id="74c21-114">Lze použít k vytvoření klienta WCF pro vzdálené služby řetězce monikeru následující příklad.</span><span class="sxs-lookup"><span data-stu-id="74c21-114">To construct a WCF client for the remote service the following example moniker string can be used.</span></span>  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 <span data-ttu-id="74c21-115">Při spuštění klientské aplikace, klient provádí `WS-MetadataExchange` za poskytnutý `mexAddress`.</span><span class="sxs-lookup"><span data-stu-id="74c21-115">During the execution of the client application, the client performs a `WS-MetadataExchange` with the provided `mexAddress`.</span></span> <span data-ttu-id="74c21-116">To může vrátit adresy, vazby a podrobnosti o kontraktu pro celou řadou služeb.</span><span class="sxs-lookup"><span data-stu-id="74c21-116">This might return the address, binding and contract details for a number of services.</span></span> <span data-ttu-id="74c21-117">`address`, `contract`, `contractNamespace`, `binding` a `bindingNamespace` parametry slouží k identifikaci určené služby.</span><span class="sxs-lookup"><span data-stu-id="74c21-117">The `address`, `contract`, `contractNamespace`, `binding` and `bindingNamespace` parameters are used to identify the intended service.</span></span> <span data-ttu-id="74c21-118">Jakmile tyto parametry pravá složená závorka, zástupný název vytvoří klienta WCF s definicí příslušné smlouvy a volání je pak možné provádět pomocí klienta WCF stejně jako u typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="74c21-118">Once those parameters have been matched, the moniker constructs a WCF client with the appropriate contract definition and calls can then be made using the WCF client, as with the typed contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74c21-119">Pokud je moniker je poškozený nebo pokud služba není dostupná, volání `GetObject` vrátí chyba s oznámením "Neplatná syntaxe".</span><span class="sxs-lookup"><span data-stu-id="74c21-119">If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error saying "Invalid Syntax".</span></span> <span data-ttu-id="74c21-120">Pokud se zobrazí tato chyba, ujistěte se, že zástupný název, který používáte, je správná a služba není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="74c21-120">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74c21-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74c21-121">See also</span></span>

- [<span data-ttu-id="74c21-122">Postupy: Registrace a konfigurace Monikeru služby</span><span class="sxs-lookup"><span data-stu-id="74c21-122">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)

---
title: 'Postupy: Použití monikeru služby Windows Communication Foundation bez registrace'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: f69314948a0e0a69e49ec148f94572f17d0b8e3c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595047"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a><span data-ttu-id="8af1d-102">Postupy: Použití monikeru služby Windows Communication Foundation bez registrace</span><span class="sxs-lookup"><span data-stu-id="8af1d-102">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>
<span data-ttu-id="8af1d-103">Chcete-li se připojit ke službě Windows Communication Foundation (WCF) a komunikovat s ní, musí mít klientská aplikace WCF podrobné informace o adrese služby, konfiguraci vazby a kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="8af1d-103">To connect to and communicate with a Windows Communication Foundation (WCF) service, a WCF client application must have the details of the service address, the binding configuration, and the service contract.</span></span>  
  
 <span data-ttu-id="8af1d-104">Moniker služby WCF obvykle získá požadovanou kontrakt prostřednictvím předchozí registrace požadovaných typů atributů, ale v některých případech mohou nastat případy, kdy to není proveditelné.</span><span class="sxs-lookup"><span data-stu-id="8af1d-104">The WCF service moniker typically obtains the required contract through prior registration of the required attribute types, but there might be cases where this is not feasible.</span></span> <span data-ttu-id="8af1d-105">Místo registrace může moniker získat definici kontraktu ve formě dokumentu WSDL (Web Services Definition Language), prostřednictvím použití `wsdl` parametru nebo prostřednictvím výměny metadat prostřednictvím `mexAddress` parametru.</span><span class="sxs-lookup"><span data-stu-id="8af1d-105">In place of registration, the moniker can obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document, through the use of the `wsdl` parameter or through Metadata Exchange, through the use of the `mexAddress` parameter.</span></span>  
  
 <span data-ttu-id="8af1d-106">To umožňuje scénáře, jako je například distribuce excelové tabulky, kde se některé hodnoty buňky vypočítávají prostřednictvím interakcí webové služby.</span><span class="sxs-lookup"><span data-stu-id="8af1d-106">This enables scenarios such as the distribution of an Excel spreadsheet where some of the cell values are calculated through Web service interactions.</span></span> <span data-ttu-id="8af1d-107">V tomto scénáři nemusí být možné zaregistrovat sestavení kontraktu služby na všech klientech, kteří můžou dokument otevřít.</span><span class="sxs-lookup"><span data-stu-id="8af1d-107">In this scenario, it might not be feasible to register the service contract assembly on all clients that might open the document.</span></span> <span data-ttu-id="8af1d-108">`wsdl`Parametr nebo `mexAddress` parametr umožňuje samostatně obsažené řešení.</span><span class="sxs-lookup"><span data-stu-id="8af1d-108">The `wsdl` parameter or the `mexAddress` parameter enables a self-contained solution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8af1d-109">Vzájemné ověřování se musí použít k ochraně proti manipulaci s žádostmi a falšování nebo falšování identity.</span><span class="sxs-lookup"><span data-stu-id="8af1d-109">Mutual authentication must be used to protect against request and response tampering or spoofing.</span></span> <span data-ttu-id="8af1d-110">Konkrétně je důležité, aby klienti měli jistotu, že koncový bod výměny metadat, který odpovídá, je zamýšlená důvěryhodná strana.</span><span class="sxs-lookup"><span data-stu-id="8af1d-110">Specifically, it is important for clients to be assured that the Metadata Exchange endpoint that is responding is the intended trusted party.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8af1d-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="8af1d-111">Example</span></span>  
 <span data-ttu-id="8af1d-112">Tento příklad ukazuje použití monikeru služby se smlouvou MEX.</span><span class="sxs-lookup"><span data-stu-id="8af1d-112">This example shows the use of the service moniker with a MEX contract.</span></span> <span data-ttu-id="8af1d-113">Služba s následujícím kontraktem se zveřejňuje s wsHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="8af1d-113">A service with the following contract is exposed with a wsHttpBinding.</span></span>  
  
```csharp
using System.ServiceModel;  
  
// ...
  
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
  
 <span data-ttu-id="8af1d-114">Chcete-li vytvořit klienta WCF pro vzdálenou službu, lze použít následující vzorový řetězec monikeru.</span><span class="sxs-lookup"><span data-stu-id="8af1d-114">To construct a WCF client for the remote service the following example moniker string can be used.</span></span>  
  
```
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 <span data-ttu-id="8af1d-115">Během provádění klientské aplikace provede klient `WS-MetadataExchange` s poskytnutou součástí `mexAddress` .</span><span class="sxs-lookup"><span data-stu-id="8af1d-115">During the execution of the client application, the client performs a `WS-MetadataExchange` with the provided `mexAddress`.</span></span> <span data-ttu-id="8af1d-116">To může vracet adresu, vazbu a podrobnosti o kontraktu pro určitý počet služeb.</span><span class="sxs-lookup"><span data-stu-id="8af1d-116">This might return the address, binding and contract details for a number of services.</span></span> <span data-ttu-id="8af1d-117">`address` `contract` `contractNamespace` `binding` `bindingNamespace` K identifikaci zamýšlené služby se používají parametry,, a.</span><span class="sxs-lookup"><span data-stu-id="8af1d-117">The `address`, `contract`, `contractNamespace`, `binding` and `bindingNamespace` parameters are used to identify the intended service.</span></span> <span data-ttu-id="8af1d-118">Jakmile se tyto parametry shodují, moniker vytvoří klienta WCF s příslušnou definicí kontraktu a volání se pak dá pomocí klienta WCF použít jako se zadaným kontraktem.</span><span class="sxs-lookup"><span data-stu-id="8af1d-118">Once those parameters have been matched, the moniker constructs a WCF client with the appropriate contract definition and calls can then be made using the WCF client, as with the typed contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8af1d-119">Pokud je moniker poškozený nebo pokud není služba k dispozici, volání `GetObject` vrátí chybu s názvem neplatná syntaxe.</span><span class="sxs-lookup"><span data-stu-id="8af1d-119">If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error saying "Invalid Syntax".</span></span> <span data-ttu-id="8af1d-120">Pokud se zobrazí tato chyba, ujistěte se, že moniker, který používáte, je správný a služba je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8af1d-120">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8af1d-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="8af1d-121">See also</span></span>

- [<span data-ttu-id="8af1d-122">Postupy: Registrace a konfigurace monikeru služby</span><span class="sxs-lookup"><span data-stu-id="8af1d-122">How to: Register and Configure a Service Moniker</span></span>](how-to-register-and-configure-a-service-moniker.md)

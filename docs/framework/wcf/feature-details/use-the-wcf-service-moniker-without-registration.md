---
title: 'Postupy: použití Monikeru služby Windows Communication Foundation bez registrace'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: fd61528770b16b13430be3691aef19c1cc743e9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497968"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a><span data-ttu-id="a0c35-102">Postupy: použití Monikeru služby Windows Communication Foundation bez registrace</span><span class="sxs-lookup"><span data-stu-id="a0c35-102">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>
<span data-ttu-id="a0c35-103">Pro připojení k a komunikovat se službou Windows Communication Foundation (WCF), musí mít klientské aplikace WCF podrobnosti o adresu služby, konfigurace vazeb a kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="a0c35-103">To connect to and communicate with a Windows Communication Foundation (WCF) service, a WCF client application must have the details of the service address, the binding configuration, and the service contract.</span></span>  
  
 <span data-ttu-id="a0c35-104">Monikeru služby WCF obvykle získá požadované kontrakt prostřednictvím předchozí registrace požadovaný atribut typy, ale můžou nastat případy, kdy to není možné.</span><span class="sxs-lookup"><span data-stu-id="a0c35-104">The WCF service moniker typically obtains the required contract through prior registration of the required attribute types, but there might be cases where this is not feasible.</span></span> <span data-ttu-id="a0c35-105">Přezdívka místo registrace, můžete získat definici kontraktu ve formě dokumentem definice jazyka WSDL (Web Services) prostřednictvím `wsdl` parametr nebo prostřednictvím Metadata Exchange prostřednictvím použití `mexAddress` parametr.</span><span class="sxs-lookup"><span data-stu-id="a0c35-105">In place of registration, the moniker can obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document, through the use of the `wsdl` parameter or through Metadata Exchange, through the use of the `mexAddress` parameter.</span></span>  
  
 <span data-ttu-id="a0c35-106">To umožňuje scénáře, jako je rozdělení tabulky aplikace Excel, kde některé hodnoty buněk se počítá pomocí interakce webové služby.</span><span class="sxs-lookup"><span data-stu-id="a0c35-106">This enables scenarios such as the distribution of an Excel spreadsheet where some of the cell values are calculated through Web service interactions.</span></span> <span data-ttu-id="a0c35-107">V tomto scénáři nemusí být vhodný k registraci sestavení kontraktu služby ve všech klientech, které může otevřít dokument.</span><span class="sxs-lookup"><span data-stu-id="a0c35-107">In this scenario, it might not be feasible to register the service contract assembly on all clients that might open the document.</span></span> <span data-ttu-id="a0c35-108">`wsdl` Parametr nebo `mexAddress` parametr povoluje samostatná řešení.</span><span class="sxs-lookup"><span data-stu-id="a0c35-108">The `wsdl` parameter or the `mexAddress` parameter enables a self-contained solution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0c35-109">Vzájemné ověřování musí použít také k ochraně proti požadavku a odpovědi manipulaci nebo falšování identity.</span><span class="sxs-lookup"><span data-stu-id="a0c35-109">Mutual authentication must be used to protect against request and response tampering or spoofing.</span></span> <span data-ttu-id="a0c35-110">Konkrétně je důležité, aby klienti mohli být jistí, že koncový bod metadat systému Exchange, který odpovídá je určený důvěryhodná strana.</span><span class="sxs-lookup"><span data-stu-id="a0c35-110">Specifically, it is important for clients to be assured that the Metadata Exchange endpoint that is responding is the intended trusted party.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0c35-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0c35-111">Example</span></span>  
 <span data-ttu-id="a0c35-112">Tento příklad ukazuje použití monikeru služby s MEX kontrakt.</span><span class="sxs-lookup"><span data-stu-id="a0c35-112">This example shows the use of the service moniker with a MEX contract.</span></span> <span data-ttu-id="a0c35-113">Služba je následující kontrakt je vystaven s wsHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="a0c35-113">A service with the following contract is exposed with a wsHttpBinding.</span></span>  
  
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
  
 <span data-ttu-id="a0c35-114">Lze použít k vytvoření klienta WCF pro službu vzdáleného následující příklad Přezdívka řetězec.</span><span class="sxs-lookup"><span data-stu-id="a0c35-114">To construct a WCF client for the remote service the following example moniker string can be used.</span></span>  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 <span data-ttu-id="a0c35-115">Během provádění klientská aplikace, klient provede `WS-MetadataExchange` poskytnutým `mexAddress`.</span><span class="sxs-lookup"><span data-stu-id="a0c35-115">During the execution of the client application, the client performs a `WS-MetadataExchange` with the provided `mexAddress`.</span></span> <span data-ttu-id="a0c35-116">To může vrátit adresy, vazby a podrobnosti smlouvy pro několik služeb.</span><span class="sxs-lookup"><span data-stu-id="a0c35-116">This might return the address, binding and contract details for a number of services.</span></span> <span data-ttu-id="a0c35-117">`address`, `contract`, `contractNamespace`, `binding` a `bindingNamespace` parametry slouží k identifikaci zamýšlené služby.</span><span class="sxs-lookup"><span data-stu-id="a0c35-117">The `address`, `contract`, `contractNamespace`, `binding` and `bindingNamespace` parameters are used to identify the intended service.</span></span> <span data-ttu-id="a0c35-118">Jakmile tyto parametry byly spárovány, přezdívka vytvoří klienta WCF s definicí příslušné smlouvy a volání pak lze pomocí klienta WCF, stejně jako u typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="a0c35-118">Once those parameters have been matched, the moniker constructs a WCF client with the appropriate contract definition and calls can then be made using the WCF client, as with the typed contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0c35-119">Pokud Přezdívka je poškozený nebo pokud služba není dostupná, volání `GetObject` vrátí chyba s oznámením "Neplatná syntaxe".</span><span class="sxs-lookup"><span data-stu-id="a0c35-119">If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error saying "Invalid Syntax".</span></span> <span data-ttu-id="a0c35-120">Pokud se zobrazí tato chyba, ujistěte se, kterou používáte Přezdívka je správný a služba není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a0c35-120">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c35-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0c35-121">See Also</span></span>  
 [<span data-ttu-id="a0c35-122">Postupy: Registrace a konfigurace monikeru služby</span><span class="sxs-lookup"><span data-stu-id="a0c35-122">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)

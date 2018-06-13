---
title: 'Postupy: použití Monikeru služby s kontrakty Metadata Exchange'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 6265860c2e1efb2f74a0243157a223a33889629a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491247"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="5954b-102">Postupy: použití Monikeru služby s kontrakty Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="5954b-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="5954b-103">Po vývoj některé nové služby WCF, můžete rozhodnout, že chcete být schopni volání tyto služby ze skriptu nebo aplikace Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="5954b-103">After developing some new WCF services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="5954b-104">Jedno z těchto metod bude generovat sestavení klienta WCF, registraci sestavení modelu COM, který nainstaluje sestavení v mezipaměti GAC a pak odkazovat typy modelu COM z kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5954b-104">One method would be to generate a WCF client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="5954b-105">Když distribuujete aplikace, budete muset distribuovat také sestavení klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="5954b-105">When you distribute the application, you will have to distribute the WCF Client assembly as well.</span></span> <span data-ttu-id="5954b-106">Uživatel pak bude mít k registraci sestavení klienta WCF u modelu COM a jeho následné uložení do mezipaměti GAC.</span><span class="sxs-lookup"><span data-stu-id="5954b-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> <span data-ttu-id="5954b-107">Zprostředkovatel komunikace s objekty WCF COM také umožňuje provádět stejné volání služby bez nutnosti spoléhat se na sestavení klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="5954b-107">WCF COM Interop also allows you to make the same service calls without relying on a WCF client assembly.</span></span> <span data-ttu-id="5954b-108">Monikeru služby WCF můžete volat libovolnou službu WCF z jakéhokoli jazyka kompatibilní COM (Visual Basic, VBScript, Visual Basic for Applications (VBA) a tak dále) tak, že zadáte exchange (Mex) koncový bod metadat identifikátor URI, který monikeru služby se používá k extrakci typu informace o službě.</span><span class="sxs-lookup"><span data-stu-id="5954b-108">The WCF moniker allows you to call any WCF service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="5954b-109">Toto téma popisuje, jak volat ukázku získávání spuštění WCF pomocí Přezdívka WCF, který určuje koncový bod Mex.</span><span class="sxs-lookup"><span data-stu-id="5954b-109">This topic describes how to call the Getting Started WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5954b-110">Ve skutečnosti instance typů front definovaných sestavením klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="5954b-110">The types defined by the WCF client assembly are never actually instantiated.</span></span> <span data-ttu-id="5954b-111">Sestavení se používá pouze pro metadata.</span><span class="sxs-lookup"><span data-stu-id="5954b-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="5954b-112">Použití monikeru služby s adresou Mex</span><span class="sxs-lookup"><span data-stu-id="5954b-112">Using the service moniker with a Mex address</span></span>  
  
1.  <span data-ttu-id="5954b-113">Sestavit ukázku Začínáme a aplikaci Internet Explorer a přejděte do jeho adresa URL (http://localhost/ServiceModelSamples/Service.svc) zajistit, že služba funguje.</span><span class="sxs-lookup"><span data-stu-id="5954b-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2.  <span data-ttu-id="5954b-114">Vytvořte skript jazyka Visual Basic nebo Visual Basic aplikaci, která obsahuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="5954b-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  <span data-ttu-id="5954b-115">Spuštění aplikace Visual Basic nebo skriptu.</span><span class="sxs-lookup"><span data-stu-id="5954b-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5954b-116">Služby, ke kterému se připojujete musí vystavit koncový bod Mex pro Přezdívka moct číst metadata ze služby.</span><span class="sxs-lookup"><span data-stu-id="5954b-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="5954b-117">Další informace najdete v tématu [postupy: publikování metadat služby promocí konfigurační soubor](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="5954b-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5954b-118">Pokud Přezdívka je poškozený nebo pokud služba není dostupná, volání `GetObject` se vrátí chyba s oznámením "Neplatnou syntaxi."</span><span class="sxs-lookup"><span data-stu-id="5954b-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="5954b-119">Pokud se zobrazí tato chyba, ujistěte se, kterou používáte Přezdívka je správný a služba není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5954b-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5954b-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="5954b-120">See Also</span></span>  
 [<span data-ttu-id="5954b-121">Postupy: Použití monikeru služby Windows Communication Foundation bez registrace</span><span class="sxs-lookup"><span data-stu-id="5954b-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [<span data-ttu-id="5954b-122">Postupy: Použití monikeru služby u kontraktů WSDL</span><span class="sxs-lookup"><span data-stu-id="5954b-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)

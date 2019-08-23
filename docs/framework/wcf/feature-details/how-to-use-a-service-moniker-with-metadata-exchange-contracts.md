---
title: 'Postupy: Použití monikeru služby u kontraktů Metadata Exchange'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 00aa1bbde95c0636391f213f830fc67b2dedf459
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968795"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="4d3b5-102">Postupy: Použití monikeru služby u kontraktů Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="4d3b5-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="4d3b5-103">Po vývoji některých nových služeb WCF se můžete rozhodnout, že chcete být schopni tyto služby volat ze skriptu nebo aplikace Visual Basic 6,0.</span><span class="sxs-lookup"><span data-stu-id="4d3b5-103">After developing some new WCF services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="4d3b5-104">Jednou z metod by bylo generovat sestavení klienta WCF, zaregistrovat sestavení v modelu COM, nainstalovat sestavení v globální mezipaměti sestavení (GAC) a pak odkazovat na typy modelu COM z kódu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4d3b5-104">One method would be to generate a WCF client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="4d3b5-105">Při distribuci aplikace budete muset distribuovat i sestavení klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="4d3b5-105">When you distribute the application, you will have to distribute the WCF Client assembly as well.</span></span> <span data-ttu-id="4d3b5-106">Uživatel pak bude muset zaregistrovat sestavení klienta WCF pomocí modelu COM a umístit ho do mezipaměti GAC.</span><span class="sxs-lookup"><span data-stu-id="4d3b5-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> <span data-ttu-id="4d3b5-107">Zprostředkovatel komunikace s objekty WCF COM také umožňuje provádět stejná volání služby, aniž by se museli spoléhat na sestavení klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="4d3b5-107">WCF COM Interop also allows you to make the same service calls without relying on a WCF client assembly.</span></span> <span data-ttu-id="4d3b5-108">Moniker WCF umožňuje volat libovolnou službu WCF z jakéhokoli jazyka kompatibilního s COM (Visual Basic, VBScript, jazyk Visual Basic for Application (VBA) atd.) zadáním identifikátoru URI koncového bodu (MEX) metadat, který používá moniker služby k extrakci typu. informace o službě.</span><span class="sxs-lookup"><span data-stu-id="4d3b5-108">The WCF moniker allows you to call any WCF service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="4d3b5-109">Toto téma popisuje, jak volat ukázku Začínáme WCF pomocí monikeru WCF, který určuje koncový bod mex.</span><span class="sxs-lookup"><span data-stu-id="4d3b5-109">This topic describes how to call the Getting Started WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d3b5-110">Typy definované sestavením klienta WCF nejsou ve skutečnosti vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="4d3b5-110">The types defined by the WCF client assembly are never actually instantiated.</span></span> <span data-ttu-id="4d3b5-111">Sestavení se používá pouze pro metadata.</span><span class="sxs-lookup"><span data-stu-id="4d3b5-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="4d3b5-112">Použití monikeru služby s adresou MEX</span><span class="sxs-lookup"><span data-stu-id="4d3b5-112">Using the service moniker with a Mex address</span></span>  
  
1. <span data-ttu-id="4d3b5-113">Sestavte Začínáme Sample a pomocí Internet Exploreru přejděte na jeho adresu URL http://localhost/ServiceModelSamples/Service.svc) (abyste zajistili, že služba funguje.</span><span class="sxs-lookup"><span data-stu-id="4d3b5-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2. <span data-ttu-id="4d3b5-114">Vytvořte skript Visual Basic nebo Visual Basic aplikaci, která obsahuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="4d3b5-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3. <span data-ttu-id="4d3b5-115">Spusťte Visual Basic aplikaci nebo skript.</span><span class="sxs-lookup"><span data-stu-id="4d3b5-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4d3b5-116">Služba, kterou voláte, musí vystavit koncový bod mex pro moniker, aby bylo možné číst metadata ze služby.</span><span class="sxs-lookup"><span data-stu-id="4d3b5-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="4d3b5-117">Další informace najdete v tématu [jak: Publikování metadat pro službu pomocí konfiguračního souboru](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="4d3b5-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4d3b5-118">Pokud je moniker poškozený nebo pokud není služba k dispozici, volání vrátí chybu `GetObject` s názvem neplatná syntaxe.</span><span class="sxs-lookup"><span data-stu-id="4d3b5-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="4d3b5-119">Pokud se zobrazí tato chyba, ujistěte se, že moniker, který používáte, je správný a služba je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="4d3b5-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d3b5-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d3b5-120">See also</span></span>

- [<span data-ttu-id="4d3b5-121">Postupy: Použít moniker služby Windows Communication Foundation bez registrace</span><span class="sxs-lookup"><span data-stu-id="4d3b5-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)
- [<span data-ttu-id="4d3b5-122">Postupy: Použití monikeru služby u kontraktů WSDL</span><span class="sxs-lookup"><span data-stu-id="4d3b5-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)

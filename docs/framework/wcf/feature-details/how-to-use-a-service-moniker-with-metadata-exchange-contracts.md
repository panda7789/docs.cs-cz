---
title: 'Postupy: Použití monikeru služby u kontraktů Metadata Exchange'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 367cbd4a2bfbde3d4ab0a74eeeaf5d5f5662ec27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972897"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="01aec-102">Postupy: Použití monikeru služby u kontraktů Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="01aec-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="01aec-103">Po vývoj některé nové služby WCF, může rozhodnout, že chcete mít možnost volat tyto služby ze skriptu nebo aplikace v jazyce Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="01aec-103">After developing some new WCF services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="01aec-104">Jednu metodu bude generovat sestavení klienta WCF, zaregistrovat sestavení s modelem COM, instalaci sestavení v GAC a pak odkazování na typy modelu COM z kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="01aec-104">One method would be to generate a WCF client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="01aec-105">Pokud distribuujete aplikaci, budete muset distribuovat na klienta WCF sestavení.</span><span class="sxs-lookup"><span data-stu-id="01aec-105">When you distribute the application, you will have to distribute the WCF Client assembly as well.</span></span> <span data-ttu-id="01aec-106">Uživatel pak muset zaregistrovat sestavení klienta WCF s modelem COM a jeho následné uložení do mezipaměti GAC.</span><span class="sxs-lookup"><span data-stu-id="01aec-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> <span data-ttu-id="01aec-107">Komunikace s objekty COM WCF také umožňuje provádět stejné volání služby bez nutnosti spoléhat se na sestavení klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="01aec-107">WCF COM Interop also allows you to make the same service calls without relying on a WCF client assembly.</span></span> <span data-ttu-id="01aec-108">Monikeru služby WCF umožňuje volat libovolnou službu WCF z jakéhokoli jazyka kompatibilního s modelu COM (Visual Basic, VBScript, Visual Basic for Applications (VBA) a tak dále) tak, že zadáte identifikátor URI, který používá monikeru služby k extrakci typů exchange (Mex) koncových bodů metadat informace o službě.</span><span class="sxs-lookup"><span data-stu-id="01aec-108">The WCF moniker allows you to call any WCF service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="01aec-109">Toto téma popisuje, jak volat získávání WCF spuštění ukázky použití monikeru služby WCF, který určuje koncový bod Mex.</span><span class="sxs-lookup"><span data-stu-id="01aec-109">This topic describes how to call the Getting Started WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01aec-110">Typy definované v sestavení klienta WCF se nikdy skutečně vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="01aec-110">The types defined by the WCF client assembly are never actually instantiated.</span></span> <span data-ttu-id="01aec-111">Sestavení se používá jenom pro metadata.</span><span class="sxs-lookup"><span data-stu-id="01aec-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="01aec-112">Použití monikeru služby u adresa MEX.</span><span class="sxs-lookup"><span data-stu-id="01aec-112">Using the service moniker with a Mex address</span></span>  
  
1. <span data-ttu-id="01aec-113">Ukázka Začínáme vytvářet a používat prohlížeč Internet Explorer a přejděte na její adresu URL (http://localhost/ServiceModelSamples/Service.svc) zajistit, služba funguje.</span><span class="sxs-lookup"><span data-stu-id="01aec-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2. <span data-ttu-id="01aec-114">Vytvořte skript jazyka Visual Basic nebo Visual Basic aplikací, který obsahuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="01aec-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3. <span data-ttu-id="01aec-115">Spuštění aplikace Visual Basic nebo skriptu.</span><span class="sxs-lookup"><span data-stu-id="01aec-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="01aec-116">Na službu, kterou voláte musí vystavit koncový bod Mex pro moniker bude moct číst metadata ze služby.</span><span class="sxs-lookup"><span data-stu-id="01aec-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="01aec-117">Další informace najdete v tématu [jak: Publikování metadat služby promocí konfiguračního souboru](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="01aec-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="01aec-118">Pokud je moniker je poškozený nebo pokud služba není dostupná, volání `GetObject` vrátí chyba s oznámením "Neplatnou syntaxi."</span><span class="sxs-lookup"><span data-stu-id="01aec-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="01aec-119">Pokud se zobrazí tato chyba, ujistěte se, že zástupný název, který používáte, je správná a služba není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="01aec-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01aec-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01aec-120">See also</span></span>

- [<span data-ttu-id="01aec-121">Postupy: Použití Monikeru služby Windows Communication Foundation bez registrace</span><span class="sxs-lookup"><span data-stu-id="01aec-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)
- [<span data-ttu-id="01aec-122">Postupy: Použití Monikeru služby u kontraktů WSDL</span><span class="sxs-lookup"><span data-stu-id="01aec-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)

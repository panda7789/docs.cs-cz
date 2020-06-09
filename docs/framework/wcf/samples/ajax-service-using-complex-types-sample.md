---
title: Ukázka služby AJAX využívající komplexní typy
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: 4227446e8844accd06490d8e7cf933da43d875a6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575911"
---
# <a name="ajax-service-using-complex-types-sample"></a><span data-ttu-id="3905a-102">Ukázka služby AJAX využívající komplexní typy</span><span class="sxs-lookup"><span data-stu-id="3905a-102">AJAX Service Using Complex Types Sample</span></span>

<span data-ttu-id="3905a-103">Tato ukázka předvádí, jak použít Windows Communication Foundation (WCF) k vytvoření ASP.NET asynchronního JavaScriptu a jazyka XML (AJAX), který vytváří instance komplexních typů a odesílá je mezi službami a klientem jako JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="3905a-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that creates instances of complex types and sends them between service and client as JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="3905a-104">Ke službě AJAX můžete přistupovat pomocí kódu jazyka JavaScript z klienta webového prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="3905a-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="3905a-105">Tato ukázka sestaví na [základní ukázce služby AJAX](basic-ajax-service.md) .</span><span class="sxs-lookup"><span data-stu-id="3905a-105">This sample builds on the [Basic AJAX Service](basic-ajax-service.md) sample.</span></span>

<span data-ttu-id="3905a-106">Podpora AJAX ve WCF je optimalizovaná pro použití s ASP.NET AJAX prostřednictvím <xref:System.Web.UI.ScriptManager> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3905a-106">AJAX support in WCF is optimized for use with ASP.NET AJAX through the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="3905a-107">Příklad použití WCF s ASP.NET AJAX naleznete v [ukázkách AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="3905a-107">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3905a-108">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="3905a-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="3905a-109">Služba v následující ukázce je služba WCF bez kódu specifického pro AJAX.</span><span class="sxs-lookup"><span data-stu-id="3905a-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span> <span data-ttu-id="3905a-110">Vzhledem k tomu <xref:System.ServiceModel.Web.WebGetAttribute> , že atribut není použit, je použit výchozí příkaz HTTP ("post").</span><span class="sxs-lookup"><span data-stu-id="3905a-110">Because the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="3905a-111">Služba obsahuje jednu operaci, `DoMath` která vrací komplexní typ s názvem `MathResult` .</span><span class="sxs-lookup"><span data-stu-id="3905a-111">The service has one operation, `DoMath`, which returns a complex type named `MathResult`.</span></span> <span data-ttu-id="3905a-112">Komplexní typ je standardní typ kontraktu dat, který také neobsahuje kód specifický pro AJAX.</span><span class="sxs-lookup"><span data-stu-id="3905a-112">The complex type is a standard data contract type, which also contains no AJAX-specific code.</span></span>

```csharp
[DataContract]
public class MathResult
{
    [DataMember]
    public double sum;
    [DataMember]
    public double difference;
    [DataMember]
    public double product;
    [DataMember]
    public double quotient;
}
```

<span data-ttu-id="3905a-113">Vytvořte koncový bod AJAX ve službě pomocí nástroje <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> , stejně jako v ukázce základní služby AJAX.</span><span class="sxs-lookup"><span data-stu-id="3905a-113">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>

<span data-ttu-id="3905a-114">Webová stránka klienta ComplexTypeClientPage. aspx obsahuje kód ASP.NET a JavaScriptu pro vyvolání služby, když uživatel klikne na tlačítko **provést výpočet** na stránce.</span><span class="sxs-lookup"><span data-stu-id="3905a-114">The client Web page ComplexTypeClientPage.aspx contains ASP.NET and JavaScript code to invoke the service when the user clicks the **Perform calculation** button on the page.</span></span> <span data-ttu-id="3905a-115">Kód pro vyvolání služby vytvoří tělo JSON a pošle ho pomocí HTTP POST, podobně jako [Služba AJAX s použitím ukázky http post](ajax-service-using-http-post.md) .</span><span class="sxs-lookup"><span data-stu-id="3905a-115">The code to invoke the service constructs a JSON body and sends it using HTTP POST, similar to the [AJAX Service Using HTTP POST](ajax-service-using-http-post.md) sample.</span></span>

<span data-ttu-id="3905a-116">Po úspěšném volání služby můžete přistupovat k jednotlivým datovým členům (, a `sum` `difference` `product` `quotient` ) na výsledný objekt JavaScriptu.</span><span class="sxs-lookup"><span data-stu-id="3905a-116">After the service call succeeds, you can access the individual data members (`sum`, `difference`, `product` and `quotient`) on the resulting JavaScript object.</span></span>

```javascript
function onSuccess(mathResult){
     document.getElementById("sum").value = mathResult.sum;
     document.getElementById("difference").value = mathResult.difference;
     document.getElementById("product").value = mathResult.product;
     document.getElementById("quotient").value = mathResult.quotient;
}
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3905a-117">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="3905a-117">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="3905a-118">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3905a-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="3905a-119">Sestavte řešení ComplexTypeAjaxService. sln, jak je popsáno v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3905a-119">Build the solution ComplexTypeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="3905a-120">Přejděte na adresu `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (v prohlížeči z adresáře projektu neotevírejte ComplexTypeClientPage. aspx).</span><span class="sxs-lookup"><span data-stu-id="3905a-120">Navigate to `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (do not open ComplexTypeClientPage.aspx in the browser from the project directory).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3905a-121">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="3905a-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3905a-122">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="3905a-122">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="3905a-123">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="3905a-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3905a-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3905a-124">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`

## <a name="see-also"></a><span data-ttu-id="3905a-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="3905a-125">See also</span></span>

- [<span data-ttu-id="3905a-126">Základní služba AJAX</span><span class="sxs-lookup"><span data-stu-id="3905a-126">Basic AJAX Service</span></span>](basic-ajax-service.md)

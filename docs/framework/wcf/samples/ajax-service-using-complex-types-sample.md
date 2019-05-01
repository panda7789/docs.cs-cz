---
title: Ukázka služby AJAX využívající komplexní typy
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: cde7e48d0f0c44d68266d60399ac197d322a42cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002882"
---
# <a name="ajax-service-using-complex-types-sample"></a><span data-ttu-id="0e933-102">Ukázka služby AJAX využívající komplexní typy</span><span class="sxs-lookup"><span data-stu-id="0e933-102">AJAX Service Using Complex Types Sample</span></span>
<span data-ttu-id="0e933-103">Tato ukázka demonstruje použití Windows Communication Foundation (WCF) k vytvoření služby ASP.NET asynchronní JavaScript a XML (AJAX), který vytváří instance komplexních typů a odešle je mezi službou a klienta jako JSON JavaScript Object Notation ().</span><span class="sxs-lookup"><span data-stu-id="0e933-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that creates instances of complex types and sends them between service and client as JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="0e933-104">Služby AJAX můžete přistupovat pomocí kódu jazyka JavaScript z webového prohlížeče klienta.</span><span class="sxs-lookup"><span data-stu-id="0e933-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="0e933-105">Tato ukázka je založena na [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="0e933-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="0e933-106">Podpora pro AJAX ve službě WCF je optimalizovaná pro použití s technologií ASP.NET AJAX prostřednictvím <xref:System.Web.UI.ScriptManager> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0e933-106">AJAX support in WCF is optimized for use with ASP.NET AJAX through the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="0e933-107">Příklad použití WCF pomocí ASP.NET AJAX, najdete v článku [AJAX ukázky](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="0e933-107">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0e933-108">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="0e933-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0e933-109">Tato služba v následujícím příkladu je služba WCF se žádný kód specifický pro AJAX.</span><span class="sxs-lookup"><span data-stu-id="0e933-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span> <span data-ttu-id="0e933-110">Vzhledem k tomu, <xref:System.ServiceModel.Web.WebGetAttribute> atribut není použit, je použit výchozí příkaz protokolu HTTP (dále jen "příspěvek").</span><span class="sxs-lookup"><span data-stu-id="0e933-110">Because the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="0e933-111">Služba má jednu operaci `DoMath`, který vrátí komplexní typ s názvem `MathResult`.</span><span class="sxs-lookup"><span data-stu-id="0e933-111">The service has one operation, `DoMath`, which returns a complex type named `MathResult`.</span></span> <span data-ttu-id="0e933-112">Komplexní typ je typ kontraktu dat standardní, která také obsahuje žádný kód specifický pro AJAX.</span><span class="sxs-lookup"><span data-stu-id="0e933-112">The complex type is a standard data contract type, which also contains no AJAX-specific code.</span></span>  

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

 <span data-ttu-id="0e933-113">Vytvořit koncový bod AJAX na službě s použitím <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, stejně jako v ukázce základní služba AJAX.</span><span class="sxs-lookup"><span data-stu-id="0e933-113">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="0e933-114">Klient ComplexTypeClientPage.aspx webová stránka obsahuje kód technologie ASP.NET a jazyka JavaScript se vyvolat službu, když uživatel klikne **výpočet** tlačítko na stránce.</span><span class="sxs-lookup"><span data-stu-id="0e933-114">The client Web page ComplexTypeClientPage.aspx contains ASP.NET and JavaScript code to invoke the service when the user clicks the **Perform calculation** button on the page.</span></span> <span data-ttu-id="0e933-115">Kód se vyvolat službu vytvoří text JSON a odešle ji pomocí HTTP POST, podobně jako [AJAX služba využívající HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="0e933-115">The code to invoke the service constructs a JSON body and sends it using HTTP POST, similar to the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
 <span data-ttu-id="0e933-116">Po úspěšném volání služby se zobrazí jednotlivé datové členy (`sum`, `difference`, `product` a `quotient`) na výsledný JavaScript objektu.</span><span class="sxs-lookup"><span data-stu-id="0e933-116">After the service call succeeds, you can access the individual data members (`sum`, `difference`, `product` and `quotient`) on the resulting JavaScript object.</span></span>  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0e933-117">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="0e933-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0e933-118">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0e933-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0e933-119">Sestavte řešení ComplexTypeAjaxService.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0e933-119">Build the solution ComplexTypeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="0e933-120">Přejděte na `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (neotevírejte ComplexTypeClientPage.aspx v prohlížeči z adresáře projektu).</span><span class="sxs-lookup"><span data-stu-id="0e933-120">Navigate to `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (do not open ComplexTypeClientPage.aspx in the browser from the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0e933-121">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="0e933-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0e933-122">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="0e933-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0e933-123">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="0e933-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0e933-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="0e933-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a><span data-ttu-id="0e933-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e933-125">See also</span></span>

- [<span data-ttu-id="0e933-126">Základní služba AJAX</span><span class="sxs-lookup"><span data-stu-id="0e933-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)

---
title: Ukázka služby AJAX využívající komplexní typy
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b821a252e202f0fef719e1545b38b4423237d0c7
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="ajax-service-using-complex-types-sample"></a><span data-ttu-id="60ceb-102">Ukázka služby AJAX využívající komplexní typy</span><span class="sxs-lookup"><span data-stu-id="60ceb-102">AJAX Service Using Complex Types Sample</span></span>
<span data-ttu-id="60ceb-103">Tento příklad ukazuje, jak používat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] k vytvoření služby ASP.NET asynchronní JavaScript a XML (AJAX), který vytváří instance komplexních typů a odešle je mezi službou a klienta jako JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="60ceb-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that creates instances of complex types and sends them between service and client as JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="60ceb-104">Služby AJAX můžete přistupovat pomocí kódu jazyka JavaScript z webového prohlížeče klienta.</span><span class="sxs-lookup"><span data-stu-id="60ceb-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="60ceb-105">Tato ukázka je založena na [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="60ceb-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="60ceb-106">Podpora jazyka AJAX v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je optimalizovaný pro použití s pomocí prvku ASP.NET AJAX <xref:System.Web.UI.ScriptManager> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="60ceb-106">AJAX support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is optimized for use with ASP.NET AJAX through the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="60ceb-107">Příklad použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pomocí prvku ASP.NET AJAX, najdete v článku [AJAX ukázky](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="60ceb-107">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see the [AJAX Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="60ceb-108">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="60ceb-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="60ceb-109">Služba v následující ukázce je [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby s žádné kódu pro konkrétní jazyk AJAX.</span><span class="sxs-lookup"><span data-stu-id="60ceb-109">The service in the following sample is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with no AJAX-specific code.</span></span> <span data-ttu-id="60ceb-110">Protože <xref:System.ServiceModel.Web.WebGetAttribute> atribut není použit, bude použita výchozí akce HTTP (dále jen "příspěvek").</span><span class="sxs-lookup"><span data-stu-id="60ceb-110">Because the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="60ceb-111">Služba obsahuje jednu operaci `DoMath`, která vrací komplexního typu s názvem `MathResult`.</span><span class="sxs-lookup"><span data-stu-id="60ceb-111">The service has one operation, `DoMath`, which returns a complex type named `MathResult`.</span></span> <span data-ttu-id="60ceb-112">Komplexní typ je standardní datového typu kontrakt, který také obsahuje žádné kódu pro konkrétní jazyk AJAX.</span><span class="sxs-lookup"><span data-stu-id="60ceb-112">The complex type is a standard data contract type, which also contains no AJAX-specific code.</span></span>  

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

 <span data-ttu-id="60ceb-113">Vytvoření AJAX koncový bod služby pomocí <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, jen jako ukázka základní služba AJAX.</span><span class="sxs-lookup"><span data-stu-id="60ceb-113">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="60ceb-114">Klient ComplexTypeClientPage.aspx webová stránka obsahuje kód ASP.NET a JavaScript pro vyvolání službu, když uživatel klikne **provádění výpočtu** tlačítko na stránce.</span><span class="sxs-lookup"><span data-stu-id="60ceb-114">The client Web page ComplexTypeClientPage.aspx contains ASP.NET and JavaScript code to invoke the service when the user clicks the **Perform calculation** button on the page.</span></span> <span data-ttu-id="60ceb-115">Kód k vyvolání služby vytvoří text JSON a odešle ji pomocí HTTP POST, podobně jako [AJAX služby pomocí HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="60ceb-115">The code to invoke the service constructs a JSON body and sends it using HTTP POST, similar to the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
 <span data-ttu-id="60ceb-116">Po úspěšné volání služby, můžete přístup k jednotlivé datové členy (`sum`, `difference`, `product` a `quotient`) na výsledný JavaScript objektu.</span><span class="sxs-lookup"><span data-stu-id="60ceb-116">After the service call succeeds, you can access the individual data members (`sum`, `difference`, `product` and `quotient`) on the resulting JavaScript object.</span></span>  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="60ceb-117">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="60ceb-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="60ceb-118">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="60ceb-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="60ceb-119">Sestavte řešení ComplexTypeAjaxService.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="60ceb-119">Build the solution ComplexTypeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="60ceb-120">Přejděte na http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (neotevírejte ComplexTypeClientPage.aspx v prohlížeči z adresáře projektu).</span><span class="sxs-lookup"><span data-stu-id="60ceb-120">Navigate to http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (do not open ComplexTypeClientPage.aspx in the browser from the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="60ceb-121">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="60ceb-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="60ceb-122">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="60ceb-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="60ceb-123">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="60ceb-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="60ceb-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="60ceb-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a><span data-ttu-id="60ceb-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="60ceb-125">See Also</span></span>  
 [<span data-ttu-id="60ceb-126">Základní služba AJAX</span><span class="sxs-lookup"><span data-stu-id="60ceb-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)

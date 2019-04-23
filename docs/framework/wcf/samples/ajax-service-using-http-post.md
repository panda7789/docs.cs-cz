---
title: Služba AJAX, která používá HTTP POST
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: 2bc1722056af4fc71f5f93d92ecd12accd99548f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772125"
---
# <a name="ajax-service-using-http-post"></a>Služba AJAX, která používá HTTP POST
Tato ukázka předvádí, jak použít Windows Communication Foundation (WCF) k vytvoření [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] asynchronní JavaScript a XML (AJAX) služby, která používá HTTP POST. Služby AJAX je ten, který se dostanete pomocí základního kódu jazyka JavaScript z webového prohlížeče klienta. Tato ukázka je založena na [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázka; jediným rozdílem mezi dvěma vzorky se používá HTTP POST místo HTTP GET.  
  
 Podpora pro AJAX ve Windows Communication Foundation (WCF) je optimalizovaná pro použití s technologií ASP.NET AJAX prostřednictvím `ScriptManager` ovládacího prvku. Příklad použití WCF pomocí ASP.NET AJAX, najdete v článku [Ajax ukázky](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Tato služba v následujícím příkladu je služba WCF se žádný kód specifický pro AJAX.  
  
 Pokud <xref:System.ServiceModel.Web.WebInvokeAttribute> atribut se používá u určité operace, nebo <xref:System.ServiceModel.Web.WebGetAttribute> atribut není použit, je použit výchozí příkaz protokolu HTTP (dále jen "příspěvek"). Požadavky POST jsou obtížnější k sestavení kompletních než požadavky GET, ale neukládají do mezipaměti; Použijte požadavky POST pro všechny operace, kde není vhodné ukládání do mezipaměti.  

```csharp
[ServiceContract(Namespace = "PostAjaxService")]  
public interface ICalculator  
{
    [WebInvoke]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}
```

 Vytvořit koncový bod AJAX na službě s použitím <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, stejně jako v ukázce základní služba AJAX.  
  
 Na rozdíl od požadavků GET nejde vyvolat příspěvek služby z prohlížeče. Například, že přejdete na `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` způsobí chybu, protože služba příspěvek očekává `n1` a `n2` parametry se mají odeslat v textu zprávy ve formátu JSON a ne v adrese URL.  
  
 Klient PostAjaxClientPage.aspx webová stránka obsahuje kód technologie ASP.NET se vyvolat službu pokaždé, když uživatel klikne jedno z tlačítek operace na stránce. Služba odpoví stejným způsobem jako v [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázku s požadavek GET.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Zajistěte, aby pokyny k instalaci [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Sestavte řešení PostAjaxService.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Přejděte na `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (neotevírejte PostAjaxClientPage.aspx v prohlížeči z adresáře projektu).

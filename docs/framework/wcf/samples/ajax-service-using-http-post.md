---
title: Služba AJAX, která používá HTTP POST
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: f904a26d87a21a931035b45261dbcd970f7d63a1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804105"
---
# <a name="ajax-service-using-http-post"></a>Služba AJAX, která používá HTTP POST
Tento příklad ukazuje, jak pomocí služby Windows Communication Foundation (WCF) můžete vytvořit [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] asynchronní JavaScript a XML (AJAX) službu, která používá HTTP POST. Služby AJAX je ten, který lze přistupovat pomocí základního kódu jazyka JavaScript z webového prohlížeče klienta. Tato ukázka je založena na [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázku; jediným rozdílem mezi dvěma vzorky je použití HTTP POST namísto metody GET protokolu HTTP.  
  
 Podpora jazyka AJAX ve Windows Communication Foundation (WCF) je optimalizovaný pro použití s pomocí prvku ASP.NET AJAX `ScriptManager` ovládacího prvku. Příklad WCF pomocí prvku ASP.NET AJAX, najdete v článku [Ajax ukázky](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Služba v následující ukázce je služby WCF s žádné kódu pro konkrétní jazyk AJAX.  
  
 Pokud <xref:System.ServiceModel.Web.WebInvokeAttribute> atribut se používá u určité operace, nebo <xref:System.ServiceModel.Web.WebGetAttribute> atribut není použit, bude použita výchozí akce HTTP (dále jen "příspěvek"). Požadavky POST jsou těžší vytvořit než požadavky GET, ale nejsou v mezipaměti; pomocí požadavků POST pro všechny operace, kde není vhodná ukládání do mezipaměti.  

```csharp
[ServiceContract(Namespace = "PostAjaxService")]  
public interface ICalculator  
{
    [WebInvoke]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}
```

 Vytvoření AJAX koncový bod služby pomocí <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, jen jako ukázka základní služba AJAX.  
  
 Na rozdíl od požadavky GET nemohou vyvolat POST služby z prohlížeče. Například přejdete na http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 skončí chybou, protože služba POST očekává `n1` a `n2` parametry pro odeslání v textu zprávy – ve formátu JSON – a ne v adrese URL.  
  
 Klient PostAjaxClientPage.aspx webová stránka obsahuje kód ASP.NET k vyvolání služby vždy, když uživatel klikne na jednu operaci tlačítek na stránce. Služba odpovídá stejným způsobem jako v [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázku s požadavek GET.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že provádíte pokynů pro instalaci [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení PostAjaxService.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Přejděte na http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (neotevírejte PostAjaxClientPage.aspx v prohlížeči z adresáře projektu).  
  
## <a name="see-also"></a>Viz také

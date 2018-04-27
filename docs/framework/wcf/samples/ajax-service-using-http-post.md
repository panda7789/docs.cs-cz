---
title: Služba AJAX, která používá HTTP POST
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1446fadeb249d91f0eb3e65b1155f00090441a5a
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="ajax-service-using-http-post"></a>Služba AJAX, která používá HTTP POST
Tento příklad ukazuje, jak používat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vytvořit [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] asynchronní JavaScript a XML (AJAX) službu, která používá HTTP POST. Služby AJAX je ten, který lze přistupovat pomocí základního kódu jazyka JavaScript z webového prohlížeče klienta. Tato ukázka je založena na [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázku; jediným rozdílem mezi dvěma vzorky je použití HTTP POST namísto metody GET protokolu HTTP.  
  
 Podpora jazyka AJAX v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] je optimalizovaný pro použití s pomocí prvku ASP.NET AJAX `ScriptManager` ovládací prvek. Příklad použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pomocí prvku ASP.NET AJAX, najdete v článku [Ajax ukázky](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Služba v následující ukázce je [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby s žádné kódu pro konkrétní jazyk AJAX.  
  
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
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že provádíte pokynů pro instalaci [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení PostAjaxService.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Přejděte na http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (neotevírejte PostAjaxClientPage.aspx v prohlížeči z adresáře projektu).  
  
## <a name="see-also"></a>Viz také

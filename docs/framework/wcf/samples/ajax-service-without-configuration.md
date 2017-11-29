---
title: "Služba AJAX bez konfigurace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 32879c2b618f3e22960a7828d29601f502a55585
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ajax-service-without-configuration"></a>Služba AJAX bez konfigurace
Tento příklad ukazuje, jak používat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vytvořit základní služby ASP.NET asynchronní JavaScript a XML (AJAX) (služba, který je přístupný pomocí kódu jazyka JavaScript z webového prohlížeče klienta) bez použití nastavení konfigurace. Služba používá speciální syntaxe v souboru .svc automaticky povolení koncového bodu AJAX.  
  
 Podpora jazyka AJAX v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je optimalizovaný pro použití s pomocí prvku ASP.NET AJAX `ScriptManager` ovládací prvek. Příklad použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pomocí prvku ASP.NET AJAX, najdete v článku [Ajax ukázky](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Tato ukázka je založen na AJAX služby pomocí HTTP POST. Jak je popsáno v [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázce <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> se používá k hostování služby.  
  
```  
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```  
  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>automaticky přidá <xref:System.ServiceModel.Description.WebScriptEndpoint> ke službě. Pokud potřebujete provést ke koncovému bodu, žádné změny konfigurace \<systému. ServiceModel > části lze úplně odebrat ze souboru Web.config pro službu. Soubor Web.config obsahuje některá nastavení ASP.NET, které jsou používány ConfigFreeClientPage.aspx. Pokud je tento není tento případ, může odebrat celý soubor Web.config.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že můžete provádět pokynů pro instalaci v [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení ConfigFreeAjaxService.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Přejděte na http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (neotevírejte ConfigFreeClientPage.aspx v prohlížeči z v adresáři projektu).  
  
> [!NOTE]
>  Při spuštění této ukázce, Zkontrolujte prosím, že anonymní ověřování a ověřování systému Windows nejsou povolené současně ServiceModelSamples složky ve službě IIS. Pokud tomu tak je, zakažte ověřování systému Windows. Po spuštění vzorového povolit ověřování systému Windows a spusťte "příkaz iisreset".  
  
## <a name="see-also"></a>Viz také  
 [Základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md)

---
title: Služba AJAX bez konfigurace
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: f12b0fad97c9f43397f3b202800943e6d061aa53
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45509663"
---
# <a name="ajax-service-without-configuration"></a>Služba AJAX bez konfigurace
Tento příklad ukazuje, jak pomocí Windows Communication Foundation (WCF) bez použití jakékoli konfigurace základní technologie ASP.NET asynchronní JavaScript a XML (AJAX) službu (služba, obsahujících pomocí kódu jazyka JavaScript z webového prohlížeče klienta) nastavení. Služba používá speciální syntaxe v souboru SVC automaticky povolení koncového bodu AJAX.  
  
 Podpora pro AJAX ve službě WCF je optimalizovaná pro použití s technologií ASP.NET AJAX prostřednictvím `ScriptManager` ovládacího prvku. Příklad použití WCF pomocí ASP.NET AJAX, najdete v článku [Ajax ukázky](https://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Tato ukázka staví na AJAX služba využívající HTTP POST. Jak je popsáno v [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázce <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> slouží jako hostitel služby.  

```svc
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```

 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automaticky přidá <xref:System.ServiceModel.Description.WebScriptEndpoint> ke službě. Pokud má být provedeno do koncového bodu, je nutné žádné změny konfigurace `<system.ServiceModel>` části je úplně odebrat ze souboru Web.config pro službu. Soubor Web.config obsahuje některá nastavení technologie ASP.NET, které jsou používány ConfigFreeClientPage.aspx. V případě, které nebyly tento případ, může odebrat celý soubor Web.config.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Zajistěte, aby pokyny k instalaci v [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení ConfigFreeAjaxService.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Přejděte na http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (neotevírejte ConfigFreeClientPage.aspx v prohlížeči z adresáře projektu).  
  
> [!NOTE]
>  Při spuštění této ukázky, ujistěte se, že anonymní ověřování a ověřování Windows nejsou současně povoleno ServiceModelSamples složky ve službě IIS. Pokud je to tento případ, zakažte ověřování Windows. Po spuštění ukázky, povolit ověřování Windows a spusťte "příkaz iisreset".  
  
## <a name="see-also"></a>Viz také  
 [Základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md)

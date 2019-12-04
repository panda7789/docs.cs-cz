---
title: Služba AJAX bez konfigurace
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: bf80f00bbca370c973dab9f20024284a465be521
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716201"
---
# <a name="ajax-service-without-configuration"></a>Služba AJAX bez konfigurace

Tato ukázka předvádí, jak použít Windows Communication Foundation (WCF) k vytvoření základní služby JavaScriptu (ASP.NET Asynchronous JavaScript and XML) (služba, ke které máte přístup pomocí kódu jazyka JavaScript z klienta webového prohlížeče) bez použití jakékoli konfigurace. možnost. Služba používá k automatickému povolení koncového bodu AJAX speciální syntaxi v souboru. svc.

Podpora AJAX ve WCF je optimalizovaná pro použití s ASP.NET AJAX prostřednictvím ovládacího prvku `ScriptManager`. Příklad použití WCF s ASP.NET AJAX naleznete v [ukázkách AJAX](ajax.md).

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

 Tato ukázka sestaví na základě služby AJAX pomocí HTTP POST. Jak je popsáno v ukázce [základní služby AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) , <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> slouží k hostování služby.

```text
<%ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"
%>
```

<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> do služby automaticky přidá <xref:System.ServiceModel.Description.WebScriptEndpoint>. Pokud není nutné provést žádné změny v konfiguraci koncového bodu, může být oddíl `<system.ServiceModel>` zcela odebrán ze souboru Web. config služby. Soubor Web. config obsahuje některá nastavení ASP.NET, která jsou používána souborem ConfigFreeClientPage. aspx. V případě, že se nejednalo o tento případ, mohl by být odebrán celý soubor Web. config.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Postupujte podle pokynů pro instalaci v [části Postup instalace pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Sestavte řešení ConfigFreeAjaxService. sln, jak je popsáno v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Přejděte na `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (neotevírejte ConfigFreeClientPage. aspx v prohlížeči z adresáře projektu).

> [!NOTE]
> Při spuštění této ukázky Prosím zajistěte, aby anonymní ověřování a ověřování systému Windows nebylo pro složku ServiceModelSamples ve službě IIS povoleno současně. V takovém případě prosím zakažte ověřování systému Windows. Po spuštění ukázky povolte ověřování systému Windows a spusťte příkaz iisreset.

## <a name="see-also"></a>Viz také:

- [Základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md)

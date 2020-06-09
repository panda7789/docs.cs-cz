---
title: Služba AJAX bez konfigurace
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: ab3731ab6aeb80e0e46228b8bf702b0fe5c6e6e9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575898"
---
# <a name="ajax-service-without-configuration"></a>Služba AJAX bez konfigurace

Tato ukázka předvádí, jak použít Windows Communication Foundation (WCF) k vytvoření základní služby JavaScriptu (ASP.NET Asynchronous JavaScript and XML) (služba, ke které máte přístup pomocí kódu jazyka JavaScript z klienta webového prohlížeče) bez použití nastavení konfigurace. Služba používá k automatickému povolení koncového bodu AJAX speciální syntaxi v souboru. svc.

Podpora AJAX ve WCF je optimalizovaná pro použití s ASP.NET AJAX prostřednictvím `ScriptManager` ovládacího prvku. Příklad použití WCF s ASP.NET AJAX naleznete v [ukázkách AJAX](ajax.md).

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

 Tato ukázka sestaví na základě služby AJAX pomocí HTTP POST. Jak je popsáno v ukázce [základní služby AJAX](basic-ajax-service.md) , <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> slouží k hostování služby.

```text
<%ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"
%>
```

<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>automaticky přidá <xref:System.ServiceModel.Description.WebScriptEndpoint> ke službě. Pokud není potřeba provést žádné změny v konfiguraci koncového bodu, bude `<system.ServiceModel>` možné oddíl úplně odebrat ze souboru Web. config služby. Soubor Web. config obsahuje některá nastavení ASP.NET, která jsou používána souborem ConfigFreeClientPage. aspx. V případě, že se nejednalo o tento případ, mohl by být odebrán celý soubor Web. config.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Postupujte podle pokynů pro instalaci v [části Postup instalace pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).

2. Sestavte řešení ConfigFreeAjaxService. sln, jak je popsáno v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).

3. Přejděte na `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (neotevírejte ConfigFreeClientPage. aspx v prohlížeči z adresáře projektu).

> [!NOTE]
> Při spuštění této ukázky Prosím zajistěte, aby anonymní ověřování a ověřování systému Windows nebylo pro složku ServiceModelSamples ve službě IIS povoleno současně. V takovém případě prosím zakažte ověřování systému Windows. Po spuštění ukázky povolte ověřování systému Windows a spusťte příkaz iisreset.

## <a name="see-also"></a>Viz také

- [Základní služba AJAX](basic-ajax-service.md)

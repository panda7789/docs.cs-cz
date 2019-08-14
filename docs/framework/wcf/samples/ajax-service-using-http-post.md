---
title: Služba AJAX, která používá HTTP POST
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: c5e5de34573fbfc8a5c6e9607d10881941a9bed5
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972025"
---
# <a name="ajax-service-using-http-post"></a>Služba AJAX, která používá HTTP POST

Tato ukázka předvádí, jak použít Windows Communication Foundation (WCF) k vytvoření služby ASP.NET Asynchronous JavaScript a XML (AJAX), která používá HTTP POST. Služba AJAX je ta, ke které můžete přistupovat pomocí základního kódu JavaScriptu z klienta webového prohlížeče. Tato ukázka sestaví na [základní ukázce služby AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) . Jediným rozdílem mezi těmito dvěma ukázkami je použití HTTP POST místo HTTP GET.

Podpora AJAX v Windows Communication Foundation (WCF) je optimalizovaná pro použití s ASP.NET AJAX prostřednictvím `ScriptManager` ovládacího prvku. Příklad použití WCF s ASP.NET AJAX naleznete v [ukázkách AJAX](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

Služba v následující ukázce je služba WCF bez kódu specifického pro AJAX.

Pokud je <xref:System.ServiceModel.Web.WebGetAttribute> atribut použit pro operaci, nebo atribut není použit, je použita výchozí operace HTTP ("post"). <xref:System.ServiceModel.Web.WebInvokeAttribute> Žádosti POST jsou těžší vytvořit než požadavky GET, ale nejsou ukládány do mezipaměti. pro všechny operace, u kterých není ukládání do mezipaměti vhodné, použijte požadavky POST.

```csharp
[ServiceContract(Namespace = "PostAjaxService")]
public interface ICalculator
{
    [WebInvoke]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

Vytvořte koncový bod AJAX ve službě pomocí nástroje <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, stejně jako v ukázce základní služby AJAX.

Na rozdíl od požadavků GET nelze vyvolat POST Services z prohlížeče. Například při přechodu na výsledky dojde `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` k chybě, protože post Service `n1` očekává odeslání parametrů a `n2` v těle zprávy ve formátu JSON, a ne v adrese URL.

Klientská webová stránka PostAjaxClientPage. aspx obsahuje kód ASP.NET k vyvolání služby vždy, když uživatel klikne na stránku s jedním z těchto tlačítek operace. Služba reaguje stejným způsobem jako v ukázce [základní služby AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) s požadavkem Get.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`

## <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli postup instalace s pokyny [pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Sestavte řešení PostAjaxService. sln, jak je popsáno v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Přejděte na `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` adresu (v prohlížeči z adresáře projektu neotevírejte PostAjaxClientPage. aspx).

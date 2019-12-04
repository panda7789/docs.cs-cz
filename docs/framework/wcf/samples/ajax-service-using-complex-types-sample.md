---
title: Ukázka služby AJAX využívající komplexní typy
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: be8db36be7ed1639d839113174fdb95505466534
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716240"
---
# <a name="ajax-service-using-complex-types-sample"></a>Ukázka služby AJAX využívající komplexní typy

Tato ukázka předvádí, jak použít Windows Communication Foundation (WCF) k vytvoření ASP.NET asynchronního JavaScriptu a jazyka XML (AJAX), který vytváří instance komplexních typů a odesílá je mezi službami a klientem jako JavaScript Object Notation (JSON). Ke službě AJAX můžete přistupovat pomocí kódu jazyka JavaScript z klienta webového prohlížeče. Tato ukázka sestaví na [základní ukázce služby AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) .

Podpora AJAX ve WCF je optimalizovaná pro použití s ASP.NET AJAX prostřednictvím ovládacího prvku <xref:System.Web.UI.ScriptManager>. Příklad použití WCF s ASP.NET AJAX naleznete v [ukázkách AJAX](ajax.md).

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

Služba v následující ukázce je služba WCF bez kódu specifického pro AJAX. Vzhledem k tomu, že atribut <xref:System.ServiceModel.Web.WebGetAttribute> není použit, je použit výchozí příkaz HTTP ("POST"). Služba obsahuje jednu operaci, `DoMath`, která vrací komplexní typ s názvem `MathResult`. Komplexní typ je standardní typ kontraktu dat, který také neobsahuje kód specifický pro AJAX.

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

Vytvořte ve službě koncový bod AJAX pomocí <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, stejně jako v ukázce základní služby AJAX.

Webová stránka klienta ComplexTypeClientPage. aspx obsahuje kód ASP.NET a JavaScriptu pro vyvolání služby, když uživatel klikne na tlačítko **provést výpočet** na stránce. Kód pro vyvolání služby vytvoří tělo JSON a pošle ho pomocí HTTP POST, podobně jako [Služba AJAX s použitím ukázky http post](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) .

Po úspěšném volání služby můžete přistupovat k jednotlivým datovým členům (`sum`, `difference`, `product` a `quotient`) na výsledný objekt JavaScriptu.

```javascript
function onSuccess(mathResult){
     document.getElementById("sum").value = mathResult.sum;
     document.getElementById("difference").value = mathResult.difference;
     document.getElementById("product").value = mathResult.product;
     document.getElementById("quotient").value = mathResult.quotient;
}
```

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Sestavte řešení ComplexTypeAjaxService. sln, jak je popsáno v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Přejděte na `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (neotevírejte ComplexTypeClientPage. aspx v prohlížeči z adresáře projektu).

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`

## <a name="see-also"></a>Viz také:

- [Základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md)

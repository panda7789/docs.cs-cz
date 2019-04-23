---
title: Ukázka služby AJAX využívající komplexní typy
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: cde7e48d0f0c44d68266d60399ac197d322a42cc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342216"
---
# <a name="ajax-service-using-complex-types-sample"></a>Ukázka služby AJAX využívající komplexní typy
Tato ukázka demonstruje použití Windows Communication Foundation (WCF) k vytvoření služby ASP.NET asynchronní JavaScript a XML (AJAX), který vytváří instance komplexních typů a odešle je mezi službou a klienta jako JSON JavaScript Object Notation (). Služby AJAX můžete přistupovat pomocí kódu jazyka JavaScript z webového prohlížeče klienta. Tato ukázka je založena na [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) vzorku.  
  
 Podpora pro AJAX ve službě WCF je optimalizovaná pro použití s technologií ASP.NET AJAX prostřednictvím <xref:System.Web.UI.ScriptManager> ovládacího prvku. Příklad použití WCF pomocí ASP.NET AJAX, najdete v článku [AJAX ukázky](ajax.md).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Tato služba v následujícím příkladu je služba WCF se žádný kód specifický pro AJAX. Vzhledem k tomu, <xref:System.ServiceModel.Web.WebGetAttribute> atribut není použit, je použit výchozí příkaz protokolu HTTP (dále jen "příspěvek"). Služba má jednu operaci `DoMath`, který vrátí komplexní typ s názvem `MathResult`. Komplexní typ je typ kontraktu dat standardní, která také obsahuje žádný kód specifický pro AJAX.  

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

 Vytvořit koncový bod AJAX na službě s použitím <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, stejně jako v ukázce základní služba AJAX.  
  
 Klient ComplexTypeClientPage.aspx webová stránka obsahuje kód technologie ASP.NET a jazyka JavaScript se vyvolat službu, když uživatel klikne **výpočet** tlačítko na stránce. Kód se vyvolat službu vytvoří text JSON a odešle ji pomocí HTTP POST, podobně jako [AJAX služba využívající HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) vzorku.  
  
 Po úspěšném volání služby se zobrazí jednotlivé datové členy (`sum`, `difference`, `product` a `quotient`) na výsledný JavaScript objektu.  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Sestavte řešení ComplexTypeAjaxService.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Přejděte na `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (neotevírejte ComplexTypeClientPage.aspx v prohlížeči z adresáře projektu).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a>Viz také:

- [Základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md)

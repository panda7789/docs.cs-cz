---
title: Ukázka služby AJAX využívající komplexní typy
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b821a252e202f0fef719e1545b38b4423237d0c7
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="ajax-service-using-complex-types-sample"></a>Ukázka služby AJAX využívající komplexní typy
Tento příklad ukazuje, jak používat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] k vytvoření služby ASP.NET asynchronní JavaScript a XML (AJAX), který vytváří instance komplexních typů a odešle je mezi službou a klienta jako JavaScript Object Notation (JSON). Služby AJAX můžete přistupovat pomocí kódu jazyka JavaScript z webového prohlížeče klienta. Tato ukázka je založena na [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázka.  
  
 Podpora jazyka AJAX v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je optimalizovaný pro použití s pomocí prvku ASP.NET AJAX <xref:System.Web.UI.ScriptManager> ovládací prvek. Příklad použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pomocí prvku ASP.NET AJAX, najdete v článku [AJAX ukázky](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Služba v následující ukázce je [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby s žádné kódu pro konkrétní jazyk AJAX. Protože <xref:System.ServiceModel.Web.WebGetAttribute> atribut není použit, bude použita výchozí akce HTTP (dále jen "příspěvek"). Služba obsahuje jednu operaci `DoMath`, která vrací komplexního typu s názvem `MathResult`. Komplexní typ je standardní datového typu kontrakt, který také obsahuje žádné kódu pro konkrétní jazyk AJAX.  

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

 Vytvoření AJAX koncový bod služby pomocí <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, jen jako ukázka základní služba AJAX.  
  
 Klient ComplexTypeClientPage.aspx webová stránka obsahuje kód ASP.NET a JavaScript pro vyvolání službu, když uživatel klikne **provádění výpočtu** tlačítko na stránce. Kód k vyvolání služby vytvoří text JSON a odešle ji pomocí HTTP POST, podobně jako [AJAX služby pomocí HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) ukázka.  
  
 Po úspěšné volání služby, můžete přístup k jednotlivé datové členy (`sum`, `difference`, `product` a `quotient`) na výsledný JavaScript objektu.  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení ComplexTypeAjaxService.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Přejděte na http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (neotevírejte ComplexTypeClientPage.aspx v prohlížeči z adresáře projektu).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a>Viz také  
 [Základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md)

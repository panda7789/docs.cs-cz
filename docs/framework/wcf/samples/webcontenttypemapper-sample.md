---
title: WebContentTypeMapper – ukázka
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 540e5e775cf7b2a5a5b585d98772415653fa833a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143561"
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper – ukázka
Tato ukázka ukazuje, jak mapovat nové typy obsahu na formáty textu zprávy Windows Communication Foundation (WCF).  
  
 Prvek <xref:System.ServiceModel.Description.WebHttpEndpoint> se zapojuje do kodéru webové zprávy, který umožňuje WCF přijímat JSON, XML nebo nezpracované binární zprávy ve stejném koncovém bodě. Kodér určuje formát těla zprávy pohledem na typ obsahu HTTP požadavku. Tato ukázka <xref:System.ServiceModel.Channels.WebContentTypeMapper> zavádí třídu, která umožňuje uživateli řídit mapování mezi typem obsahu a formátem těla.  
  
 WCF poskytuje sadu výchozí mapování pro typy obsahu. Například `application/json` mapuje na JSON a `text/xml` mapuje na XML. Jakýkoli typ obsahu, který není mapován na JSON nebo XML, je mapován na nezpracovaný binární formát.  
  
 V některých scénářích (například nabízená řešení API) vývojář služby neřídí typ obsahu vrácený klientem. Klienti mohou například vrátit JSON jako `text/javascript` namísto `application/json`. V takovém případě musí vývojář služby poskytnout <xref:System.ServiceModel.Channels.WebContentTypeMapper> typ, který je odvozen od správného zpracování daného typu obsahu, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp  
public class JsonContentTypeMapper : WebContentTypeMapper  
{  
    public override WebContentFormat  
               GetMessageFormatForContentType(string contentType)  
    {  
        if (contentType == "text/javascript")  
        {  
            return WebContentFormat.Json;  
        }  
        else  
        {  
            return WebContentFormat.Default;  
        }  
    }  
}  
```  
  
 Typ musí přepsat <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> metodu. Metoda musí `contentType` vyhodnotit argument a vrátit jednu z následujících hodnot: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, nebo <xref:System.ServiceModel.Channels.WebContentFormat.Default>. Vrácení <xref:System.ServiceModel.Channels.WebContentFormat.Default> odloží na výchozí mapování kodéru webových zpráv. V předchozím ukázkovém `text/javascript` kódu je typ obsahu mapován na JSON a všechna ostatní mapování zůstanou nezměněna.  
  
 Chcete-li `JsonContentTypeMapper` třídu použít, použijte ve svém souboru Web.config následující:  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Chcete-li ověřit požadavek na používání jsonContentTypeMapper, odeberte atribut contentTypeMapper z výše uvedeného konfiguračního souboru. Při pokusu o odeslání `text/javascript` obsahu JSON se nenačte stránka klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Vytvořte řešení WebContentTypeMapperSample.sln, jak je popsáno v [části Vytváření ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Přejděte `http://localhost/ServiceModelSamples/JCTMClientPage.htm` na (neotevírejte soubor JCTMClientPage.htm v prohlížeči z adresáře projektu).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  

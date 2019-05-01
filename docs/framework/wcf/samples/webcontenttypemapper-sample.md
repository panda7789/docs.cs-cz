---
title: WebContentTypeMapper – ukázka
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 381fc4a3084b1a2620384a04de85b9085e02ae16
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006287"
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper – ukázka
Tato ukázka předvádí, jak namapovat nové typy obsahu formáty text zpráv Windows Communication Foundation (WCF).  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint> Element připojí kodér zprávy webové, což umožňuje WCF JSON, XML nebo Nezpracovaná binární zprávy na stejný koncový bod. Kodér Určuje formát těla zprávy pomocí protokolu HTTP content-type žádosti. Tato ukázka představuje <xref:System.ServiceModel.Channels.WebContentTypeMapper> třídu, která umožňuje uživateli řídit mapování typu obsahu a formát těla zprávy.  
  
 WCF obsahuje sadu výchozích mapování pro typy obsahu. Například `application/json` mapuje do formátu JSON a `text/xml` mapuje na XML. Jakýkoli typ obsahu, který není namapovaný na XML nebo JSON se mapuje na nezpracovaná binární formát.  
  
 V některých případech (například stylu push API) služby pro vývojáře neřídí typ obsahu vrácených klienta. Například klienti může vrátit JSON jako `text/javascript` místo `application/json`. V takovém případě vývojářem služeb, musíte zadat typ, který je odvozen od <xref:System.ServiceModel.Channels.WebContentTypeMapper> zpracování daného typu obsahu správně, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
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
  
 Typ musí přepsat <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> metody. Metoda se musí vyhodnotit `contentType` argument a návratové jednu z následujících hodnot: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, nebo <xref:System.ServiceModel.Channels.WebContentFormat.Default>. Vrací <xref:System.ServiceModel.Channels.WebContentFormat.Default> odloží k výchozímu mapování kodéru zpráv Web. V předchozí ukázce kódu `text/javascript` obsahu typu je mapována do formátu JSON a jiných mapováních zůstanou beze změny.  
  
 Použít `JsonContentTypeMapper` třídy, použijte tuto v souboru Web.config:  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Chcete-li ověřit požadavky pro použití JsonContentTypeMapper, odeberte atribut contentTypeMapper z výše uvedených konfiguračního souboru. Na stránce klienta se nepodaří načíst při pokusu o použití `text/javascript` odeslat obsah JSON.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Sestavte řešení WebContentTypeMapperSample.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Přejděte na `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (neotevírejte JCTMClientPage.htm v prohlížeči z adresáře projektu).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  

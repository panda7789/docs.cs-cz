---
title: WebContentTypeMapper – ukázka
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 89f13599e23f3e60ae4d9bc973debc436f46c147
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806965"
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper – ukázka
Tento příklad znázorňuje způsob namapování nové typy obsahu do formáty text zpráv Windows Communication Foundation (WCF).  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint> Element připojí kodér zpráv Web, který umožňuje WCF k přijetí JSON, XML nebo Nezpracovaná binární zprávy se stejný koncový bod. Kodér formátu textu zprávy určuje prohlížením hlavičku HTTP content-type požadavku. Tato ukázka představuje <xref:System.ServiceModel.Channels.WebContentTypeMapper> třídy, která umožňuje uživateli řídit mapování mezi typu obsahu a formátu textu.  
  
 WCF poskytuje sadu výchozích mapování pro typy obsahu. Například `application/json` mapy do formátu JSON a `text/xml` se mapuje na XML. Jakýkoli typ obsahu, který není mapován na XML nebo JSON je namapována na nezpracovaná binární formát.  
  
 V některých případech (například nabízené stylu API) služba vývojáře neřídí obsahu typ vrácený klientem. Například klienti může vrátit formát JSON jako `text/javascript` místo `application/json`. V takovém případě vývojáře služby musíte zadat typ, který je odvozen od <xref:System.ServiceModel.Channels.WebContentTypeMapper> pro zpracování obsahu daného typu správně, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Typ musí přepsat <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> metoda. Metoda se musí vyhodnotit `contentType` argument a návratové jeden z následujících hodnot: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, nebo <xref:System.ServiceModel.Channels.WebContentFormat.Default>. Vrácení <xref:System.ServiceModel.Channels.WebContentFormat.Default> odkládat údaje k výchozímu mapování kodér zpráv Web. V předchozím ukázkovém kódu `text/javascript` obsahu typu je namapovaná na JSON a všechny ostatní mapování zůstanou beze změny.  
  
 Chcete-li použít `JsonContentTypeMapper` třídy, použijte následující v souboru Web.config:  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Pokud chcete ověřit pomocí JsonContentTypeMapper požadavek, odeberte atribut contentTypeMapper z výše uvedených konfiguračního souboru. Stránku Klient nepodaří načíst při pokusu o použití `text/javascript` odeslat obsah JSON.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení WebContentTypeMapperSample.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Přejděte na http://localhost/ServiceModelSamples/JCTMClientPage.htm (neotevírejte JCTMClientPage.htm v prohlížeči z v adresáři projektu).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
  
## <a name="see-also"></a>Viz také

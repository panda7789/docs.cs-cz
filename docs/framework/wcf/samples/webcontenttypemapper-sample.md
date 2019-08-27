---
title: WebContentTypeMapper – ukázka
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 1b15651859fd17673caf898df02c2b74a85d7612
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038544"
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper – ukázka
Tato ukázka předvádí, jak namapovat nové typy obsahu na Windows Communication Foundation (WCF) formáty textu zprávy.  
  
 Prvek <xref:System.ServiceModel.Description.WebHttpEndpoint> se připojí v kodéru webové zprávy, který umožňuje WCF přijímat zprávy JSON, XML nebo RAW v rámci stejného koncového bodu. Kodér určí formát textu zprávy na základě typu obsahu HTTP žádosti. Tato ukázka zavádí <xref:System.ServiceModel.Channels.WebContentTypeMapper> třídu, která umožňuje uživateli řídit mapování mezi typem obsahu a formátem textu.  
  
 WCF poskytuje sadu výchozích mapování pro typy obsahu. Například `application/json` mapuje na JSON a `text/xml` mapuje na XML. Jakýkoli typ obsahu, který není namapován na JSON nebo XML, je namapován na nezpracovaný binární formát.  
  
 V některých scénářích (například rozhraní API pro nabízené oznámení) vývojář služby neřídí typ obsahu vrácený klientem. Například klienti mohou vracet JSON jako `text/javascript` `application/json`místo. V tomto případě musí vývojář služby poskytnout typ, který je odvozen z <xref:System.ServiceModel.Channels.WebContentTypeMapper> pro správné zpracování daného typu obsahu, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Typ musí přepsat <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> metodu. Metoda musí vyhodnotit `contentType` argument a vracet jednu z následujících hodnot: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>nebo <xref:System.ServiceModel.Channels.WebContentFormat.Default>. Vrácení <xref:System.ServiceModel.Channels.WebContentFormat.Default> se odloží na výchozí mapování kodéru webových zpráv. V předchozím ukázkovém kódu `text/javascript` je typ obsahu namapován na JSON a všechna ostatní mapování zůstanou beze změny.  
  
 Chcete-li `JsonContentTypeMapper` použít třídu, použijte následující v souboru Web. config:  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Chcete-li ověřit požadavek na použití JsonContentTypeMapper, odeberte z výše uvedeného konfiguračního souboru atribut contentTypeMapper. Při pokusu `text/javascript` o odeslání obsahu JSON se stránka klienta nenačte.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Sestavte řešení WebContentTypeMapperSample. sln, jak je popsáno v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Přejděte na `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (neotevírejte JCTMClientPage. htm v prohlížeči z adresáře projektu).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  

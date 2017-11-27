---
title: "Chování publikování metadat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fbccca0bb5db7fa12b5237d19b833e9fe11da0e9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="metadata-publishing-behavior"></a>Chování publikování metadat
Ukázka chování publikování metadat ukazuje, jak k ovládání funkcí publikování metadat služby. Aby se zabránilo neúmyslnému zveřejnění metadata potenciálně citlivých služby, výchozí konfiguraci pro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zakáže publikování metadat služby. Toto chování je ve výchozím nastavení zabezpečení, ale také znamená, že nelze použít metadata importovat nástroj (například Svcutil.exe) ke generování kódu klienta pro volání služby, pokud není výslovně povolena chování publikování metadat služby v konfiguraci požadován.  
  
> [!IMPORTANT]
>  Tato ukázka pro přehlednost, ukazuje, jak vytvořit koncový bod publikování zabezpečená metadat. Tyto koncové body jsou potenciálně dostupné pro anonymní neověřené spotřebitelů a musí dát pozor před nasazením těchto koncových bodů a zajistit tak veřejně předání metadata služby příslušné. Najdete v článku [koncový bod metadat zabezpečení vlastní](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) ukázku pro vzorku, který zabezpečuje koncový bod metadat.  
  
 Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje `ICalculator` kontrakt služby. V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Pro službu, která zveřejňuje metadata <xref:System.ServiceModel.Description.ServiceMetadataBehavior> musí být nastaveny na službu. Když toto chování je k dispozici, můžete publikovat metadata nakonfigurováním koncový bod ke zveřejnění <xref:System.ServiceModel.Description.IMetadataExchange> kontrakt jako implementaci protokolu WS-MetadataExchange (MEX). V zájmu usnadnění tento kontrakt nebyla zadána konfigurace zkrácený název "IMetadataExchange". Této ukázce se používá `mexHttpBinding`, což je pro vaše pohodlí standardní vazby, která je ekvivalentní `wsHttpBinding` s režim zabezpečení nastavený na `None`. Relativní adresu "mex" se používá v koncovém bodě, který v případě přeložit proti služby základní adresu výsledkem koncový bod adresy http://localhost/servicemodelsamples/service.svc/mex. Konfigurace chování obrázku:  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- The serviceMetadata behavior publishes metadata through   
           the IMetadataExchange contract. When this behavior is   
           present, you can expose this contract through an endpoint   
           as shown below. Setting httpGetEnabled to true publishes   
           the service's WSDL at the <baseaddress>?wsdl, for example,  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Následující obrázek znázorňuje MEX koncový bod.  
  
```xml  
<!-- the MEX endpoint is exposed at   
     http://localhost/servicemodelsamples/service.svc/mex   
     To expose the IMetadataExchange contract, you   
     must enable the serviceMetadata behavior as demonstrated                           
     previously. -->  
<endpoint address="mex"  
          binding="mexHttpBinding"  
          contract="IMetadataExchange" />  
```  
  
 Nastaví Tato ukázka <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost `true`, který taky zpřístupňuje metadata služby pomocí metody GET protokolu HTTP. Chcete-li povolit koncový bod metadat HTTP GET, musí mít službu základní adresu HTTP. Řetězec dotazu `?wsdl` se používá na základní adresa služby přístup k metadatům. Například zobrazíte WSDL pro službu ve webovém prohlížeči použijete http://localhost/servicemodelsamples/service.svc?wsdl adresu. Alternativně můžete toto chování vystavit metadat prostřednictvím protokolu HTTPS, nastavením <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> k `true`. To vyžaduje základní adresu HTTPS.  
  
 Pro přístup k použití pro koncový bod služby MEX [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 Tím se vygeneruje na základě metadat služby klienta.  
  
 Chcete-li získat přístup k metadatům pro službu pomocí metody GET protokolu HTTP, přejděte v prohlížeči na http://localhost/servicemodelsamples/service.svc?wsdl.  
  
 Pokud odeberete toto chování a pokuste se spustit službu, dojde k výjimce. K této chybě dojde, protože bez chování, koncový bod nakonfigurovaný s `IMetadataExchange` nemá žádnou implementaci kontraktu.  
  
 Pokud nastavíte `HttpGetEnabled` k `false`, uvidíte na stránce nápovědy CalculatorService místo zobrazuje metadata služby.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
  
## <a name="see-also"></a>Viz také

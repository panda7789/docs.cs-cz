---
title: Chování publikování metadat
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: dade6d1a53fd99b994fb3c027db4e51392bfdcda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144393"
---
# <a name="metadata-publishing-behavior"></a>Chování publikování metadat
Ukázka chování publikování metadat ukazuje, jak řídit funkce publikování metadat služby. Chcete-li zabránit neúmyslnému zveřejnění potenciálně citlivých metadat služby, výchozí konfigurace pro služby WCF (Windows Communication Foundation) zakáže publikování metadat. Toto chování je ve výchozím nastavení zabezpečené, ale také znamená, že nelze použít nástroj pro import metadat (například Svcutil.exe) ke generování klientského kódu potřebného k volání služby, pokud není v konfiguraci explicitně povoleno chování publikování metadat služby.  
  
> [!IMPORTANT]
> Pro přehlednost tato ukázka ukazuje, jak vytvořit koncový bod publikování nezabezpečených metadat. Tyto koncové body jsou potenciálně k dispozici anonymní matné neověřené spotřebitele a je třeba dbát na to před nasazením těchto koncových bodů, aby bylo zajištěno, že je vhodné veřejně zveřejnit metadata služby. Viz [ukázka ukázně vlastních zabezpečených metadat](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) koncového bodu pro ukázku, která zabezpečuje koncový bod metadat.  
  
 Ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), `ICalculator` který implementuje servisní smlouvy. V této ukázce je klient konzolovou aplikací (.exe) a služba je hostována internetovou informační službou (IIS).  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Pro službu vystavit metadata, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> musí být nakonfigurován ve službě. Pokud je toto chování k dispozici, můžete publikovat metadata <xref:System.ServiceModel.Description.IMetadataExchange> konfigurací koncového bodu vystavit smlouvy jako implementace protokolu WS-MetadataExchange (MEX). Pro pohodlí, tato smlouva byla dána zkrácený název konfigurace "IMetadataExchange". Tato ukázka `mexHttpBinding`používá , což je standardní vazba pohodlí, která je ekvivalentní `wsHttpBinding` s režimem zabezpečení nastavena na `None`. V koncovém bodě se používá relativní adresa "mex", která při vyřešení oproti základní `http://localhost/servicemodelsamples/service.svc/mex`adrese služeb vede k adrese koncového bodu . Následující ukazuje konfiguraci chování:  
  
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
  
 Následující ukazuje koncový bod MEX.  
  
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
  
 Tato ukázka <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> nastaví vlastnost `true`, která také zveřejňuje metadata služby pomocí HTTP GET. Chcete-li povolit koncový bod metadat HTTP GET, musí mít služba základní adresu HTTP. Řetězec `?wsdl` dotazu se používá na základní adresu služby pro přístup k metadatům. Chcete-li například zobrazit WSDL pro službu ve webovém prohlížeči, použijte adresu `http://localhost/servicemodelsamples/service.svc?wsdl`. Toto chování můžete také použít k vystavení metadat <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> `true`přes protokol HTTPS nastavením na . To vyžaduje základní adresu HTTPS.  
  
 Chcete-li získat přístup ke koncovému bodu MEX služby, použijte [nástroj ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 Tím se vygeneruje klient na základě metadat služby.  
  
 Chcete-li získat přístup k metadatům služby `http://localhost/servicemodelsamples/service.svc?wsdl`pomocí protokolu HTTP GET, přejděte do prohlížeče.  
  
 Pokud toto chování odeberete a pokusíte se otevřít službu, získáte výjimku. K této chybě dochází, protože bez chování `IMetadataExchange` koncový bod nakonfigurovaný se smlouvou nemá žádnou implementaci.  
  
 Pokud nastavíte `HttpGetEnabled` na `false`, zobrazí se místo zobrazení metadat služby na stránce nápovědy Služby.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  

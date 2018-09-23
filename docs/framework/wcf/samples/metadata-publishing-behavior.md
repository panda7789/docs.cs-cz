---
title: Chování publikování metadat
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: c3e26454cc9b29620d80a86df7d7aee131e18200
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2018
ms.locfileid: "46703470"
---
# <a name="metadata-publishing-behavior"></a>Chování publikování metadat
Ukázka chování publikování metadat ukazuje, jak řídit funkce publikování metadat služby. Pokud chcete zabránit neúmyslnému zveřejnění metadat služby potenciálně citlivých, výchozí konfigurace pro služby Windows Communication Foundation (WCF) zakáže publikování metadat. Toto chování je ve výchozím nastavení zabezpečený, ale také znamená, že nemůžete použít metadat importovat nástroj (například Svcutil.exe) ke generování kódu klienta, který je potřeba volat službu, není-li v konfiguraci není explicitně povoleno chování publikování metadat služby.  
  
> [!IMPORTANT]
>  Pro přehlednost Tato ukázka ukazuje, jak vytvořit koncový bod publikování metadat zabezpečená. Tyto koncové body jsou potenciálně dostupné pro anonymní neověřené uživatele a musí tak, aby byl veřejně pocházejí metadata služby odpovídající věnovat pozornost před nasazením tyto koncové body. Zobrazit [koncový bod metadat Zabezpečte vlastní](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) Vzorový příklad, který zajišťuje zabezpečení koncových bodů metadat.  
  
 Vzorek je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje `ICalculator` kontrakt služby. V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Pro službu, která zpřístupňují metadata a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> musí být nakonfigurovaná na službu. Když toto chování je k dispozici, můžete publikovat metadat nakonfigurováním zveřejnit koncový bod <xref:System.ServiceModel.Description.IMetadataExchange> kontrakt jako implementaci protokolu WS-MetadataExchange (MEX). Pro zjednodušení této smlouvy se předala zkrácený konfigurační název "IMetadataExchange". Této ukázce se používá `mexHttpBinding`, což je usnadnění standardní vazbu, která je ekvivalentní `wsHttpBinding` s režimem zabezpečení nastaveno `None`. Relativní adresa "mex" se používá koncový bod, který se při vyřešení proti základní služby adresu výsledkem adresy koncového bodu z http://localhost/servicemodelsamples/service.svc/mex. Následuje ukázka konfigurace chování:  
  
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
  
 Následuje ukázka koncového bodu MEX.  
  
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
  
 Tato ukázka nastaví <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost `true`, což také poskytuje metadata služby pomocí HTTP GET. Pokud chcete povolit koncový bod metadat HTTP GET, služba musí mít základní adresu HTTP. Řetězec dotazu `?wsdl` se používá na základní adresu služby pro přístup k metadatům. Například pokud chcete zobrazit WSDL pro služby ve webovém prohlížeči použijete adresu http://localhost/servicemodelsamples/service.svc?wsdl. Alternativně můžete použít toto chování ke zveřejnění metadat prostřednictvím protokolu HTTPS tak, že nastavíte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> k `true`. To vyžaduje základní adresu HTTPS.  
  
 Pro přístup k použití koncového bodu služby MEX [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 Tím se vytvoří klienta na základě metadat služby.  
  
 Chcete-li získat přístup k metadatům služby pomocí HTTP GET, přejděte v prohlížeči na http://localhost/servicemodelsamples/service.svc?wsdl.  
  
 Pokud odeberete toto chování a pokusu o otevření služby, obdržíte výjimku. K této chybě dochází, protože bez chování, koncový bod nakonfigurovaný s `IMetadataExchange` smlouvy nemá žádnou implementaci.  
  
 Pokud nastavíte `HttpGetEnabled` k `false`, zobrazí se stránka nápovědy CalculatorService místo zobrazení metadat služby.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
  
## <a name="see-also"></a>Viz také

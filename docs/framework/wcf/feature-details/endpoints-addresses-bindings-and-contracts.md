---
title: 'Koncové body: adresy, vazby a kontrakty'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 3e78e7cf0c5acde53d7ee23294fd52134414e860
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207523"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a>Koncové body: adresy, vazby a kontrakty
Veškerá komunikace se službou Windows Communication Foundation (WCF) nastane prostřednictvím *koncové body* služby. Koncové body poskytují klientům přístup k funkcím, které nabízí služba WCF.  
  
 Každý koncový bod se skládá ze čtyř vlastností:  
  
-   Adresa, která určuje, kde můžete najít koncový bod.  
  
-   Vazba, která určuje, jak klient může komunikovat s koncovým bodem.  
  
-   Smlouvy, které jsou uvedeny operace, které jsou k dispozici.  
  
-   Sada chování, které určují místní implementace podrobnosti koncového bodu.  
  
 Toto téma popisuje strukturu tohoto koncového bodu a vysvětluje, jak je reprezentován v objektovém modelu WCF.  
  
## <a name="the-structure-of-an-endpoint"></a>Struktura koncový bod  
 Každý koncový bod se skládá z následujících akcí:  
  
-   Adresa: Adresa jednoznačně identifikuje koncový bod a říká potenciál příjemce služby, kde se nachází. Je zastoupena v objektový model WCF pomocí <xref:System.ServiceModel.EndpointAddress> třídy. <xref:System.ServiceModel.EndpointAddress> Třída obsahuje:  
  
    -   A <xref:System.ServiceModel.EndpointAddress.Uri%2A> vlastnost, která představuje adresu služby.  
  
    -   <xref:System.ServiceModel.EndpointAddress.Identity%2A> Vlastnost, která představuje zabezpečení identity služby a kolekce hlaviček volitelnou zprávu. Záhlaví volitelnou zprávu se používají k zajištění další a další podrobné informace o adresách k identifikaci a k interakci s koncovým bodem.  
  
     Další informace najdete v tématu [zadání adresy koncového bodu](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
-   Vazby: Vazba Určuje, jak se ke komunikaci s koncovým bodem. Sem patří:  
  
    -   Protokol přenos, který se má použít (například protokol TCP nebo HTTP).  
  
    -   Kódování pro zprávy (například text nebo binární).  
  
    -   Nezbytné požadavky na zabezpečení (například protokol SSL nebo SOAP zabezpečení zpráv).  
  
     Další informace najdete v tématu [vazby WCF – přehled](../../../../docs/framework/wcf/bindings-overview.md). Vazbu v objektovém modelu WCF reprezentována abstraktní základní třída <xref:System.ServiceModel.Channels.Binding>. Pro většinu scénářů uživatelé mohou používat jednu z vazeb poskytovaných systémem. Další informace najdete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
-   Kontrakty: Kontrakt popisuje, jaké funkce zpřístupňuje koncový bod do klienta. Určuje kontrakt:  
  
    -   Jaké operace lze volat pro klienta.  
  
    -   Formulář zprávy.  
  
    -   Typ vstupních parametrů nebo data potřebná pro volání operace.  
  
    -   Jaký typ odpověď nebo zpracování zpráv klienta můžete očekávat.  
  
     Další informace o definování kontraktu, naleznete v tématu [navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
-   Chování: Chování koncového bodu můžete použít k úpravě místní chování koncového bodu služby. Chování koncového bodu dosáhnout účastí průběhu sestavování WCFruntime. Příklad chování koncového bodu je <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> vlastnost, která vám umožní určit jinou adresu naslouchání, než adresu SOAP nebo webové služby WSDL (Description Language). Další informace najdete v tématu [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).  
  
## <a name="defining-endpoints"></a>Definování koncových bodů  
 Můžete zadat koncový bod služby buď imperativně promocí kódu nebo deklarativně prostřednictvím konfigurace. Další informace najdete v tématu [jak: Vytvoření koncového bodu služby v konfiguraci](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) a [jak: Vytvoření koncového bodu služby v kódu](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 Tato část vysvětluje účel, adresy, vazby a koncové body ukazuje postup při konfiguraci vazby a koncový bod; a ukazuje, jak používat `ClientVia` chování a `ListenUri` vlastnost.  
  
 [Adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 Popisuje, jak se řeší koncových bodů WCF.  
  
 [Vazby](../../../../docs/framework/wcf/feature-details/bindings.md)  
 Popisuje, jak vazby se používají k určení přenosu, kódování a podrobnosti protokolu pro klienty a služby musí komunikovat mezi sebou.  
  
 [Kontrakty](../../../../docs/framework/wcf/feature-details/contracts.md)  
 Popisuje, jak definovat metody služby smluv.  
  
 [Postupy: Vytvoření koncového bodu služby v konfiguraci](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 Popisuje postup vytvoření koncového bodu služby v konfiguraci.  
  
 [Postupy: Vytvoření koncového bodu služby v kódu](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 Popisuje postup vytvoření koncového bodu služby v kódu.  
  
 [Postupy: Ověření zkompilovaného kódu služby pomocí nástroje Svcutil.exe](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 Popisuje, jak detekovat chyby v implementacemi služeb a konfigurace bez hostování pomocí služby [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace služeb](../../../../docs/framework/wcf/configuring-services.md)
- [Rozšiřování vazeb](../../../../docs/framework/wcf/extending/extending-bindings.md)

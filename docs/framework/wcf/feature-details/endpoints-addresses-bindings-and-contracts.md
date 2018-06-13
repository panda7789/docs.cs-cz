---
title: 'Koncové body: adresy, vazby a kontrakty'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 0909d1d10ab8932f27f7ca6cba6207d57fa4f4cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493745"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a>Koncové body: adresy, vazby a kontrakty
Veškerá komunikace se službou Windows Communication Foundation (WCF) dojde k prostřednictvím *koncové body* služby. Koncové body poskytují klientům přístup k funkce nabízené službou WCF.  
  
 Každý koncový bod se skládá ze čtyř vlastností:  
  
-   Adresa, která určuje, kde můžete najít koncový bod.  
  
-   Vazba, která určuje, jak klient může komunikovat s koncovým bodem.  
  
-   Kontrakt, který identifikuje operace, které jsou k dispozici.  
  
-   Sada chování, které určují místní implementace podrobnosti koncového bodu.  
  
 Toto téma popisuje tuto strukturu koncový bod a vysvětluje, jak je reprezentována v objektový model WCF.  
  
## <a name="the-structure-of-an-endpoint"></a>Struktura koncový bod  
 Každý koncový bod se skládá z následujících akcí:  
  
-   Adresa: Adresa jednoznačně identifikuje koncový bod a říká potenciální příjemcům služby, kde se nachází. Je zobrazena v objektový model WCF pomocí <xref:System.ServiceModel.EndpointAddress> třídy. <xref:System.ServiceModel.EndpointAddress> Třída obsahuje:  
  
    -   A <xref:System.ServiceModel.EndpointAddress.Uri%2A> vlastnosti, která představuje adresu služby.  
  
    -   <xref:System.ServiceModel.EndpointAddress.Identity%2A> Vlastnosti, která představuje identitu zabezpečení služby a kolekci hlaviček volitelné zprávy. Záhlaví volitelné zpráv slouží k poskytnutí dalších a podrobnější informace o přidělování k vaší identifikaci nebo interakci s koncovým bodem.  
  
     Další informace najdete v tématu [zadání adresy koncového bodu](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
-   Vazba: Vazba Určuje, jak ke komunikaci s koncovým bodem. Sem patří:  
  
    -   Přenosový protokol použít (například protokol TCP nebo HTTP).  
  
    -   Kódování pro zprávy (například textu nebo binárních).  
  
    -   Požadavky na nezbytné zabezpečení (například protokol SSL nebo SOAP zabezpečení zpráv).  
  
     Další informace najdete v tématu [vazby WCF – přehled](../../../../docs/framework/wcf/bindings-overview.md). Vazba je reprezentována v objektový model WCF abstraktní základní třída <xref:System.ServiceModel.Channels.Binding>. Pro většinu scénářů uživatelé mohou používat jednu z vazby poskytované systémem. Další informace najdete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
-   Kontrakty: Kontrakt popisuje, jaké funkce koncový bod vystavuje klienta. Kontrakt určuje:  
  
    -   Jaké operace lze volat klientem.  
  
    -   Formulář zprávy.  
  
    -   Typ vstupní parametry nebo data potřebná k operaci volat.  
  
    -   Jaký typ zpracování nebo odpovědi zprávy klienta můžete očekávat.  
  
     Další informace o definování kontraktu najdete v tématu [navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
-   Chování: Koncový bod chování můžete použít k přizpůsobení chování místní koncový bod služby. Koncový bod chování dosáhnout účastí procesu vytváření WCFruntime. Je například chování koncového bodu <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> vlastnosti, která umožňuje zadat adresu odlišnou naslouchání adresu protokolu SOAP nebo webové služby popis Language (WSDL). Další informace najdete v tématu [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).  
  
## <a name="defining-endpoints"></a>Definování koncové body  
 Zadaný koncový bod služby buď imperativní pomocí kódu nebo deklarativně pomocí konfigurace. Další informace najdete v tématu [postupy: vytvoření koncového bodu služby v konfiguraci](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) a [postupy: vytvoření koncového bodu služby v kódu](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 Tato část popisuje účel vazby, koncových bodů a adresy; ukazuje, jak nakonfigurovat vazbu a koncový bod; a ukazuje, jak používat `ClientVia` chování a `ListenUri` vlastnost.  
  
 [Adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 Popisuje, jak popisuje koncových bodů WCF.  
  
 [Vazby](../../../../docs/framework/wcf/feature-details/bindings.md)  
 Popisuje, jak vazby slouží k zadání přenosu, kódování a podrobnosti protokolu povinné pro klienty a služby pro komunikaci mezi sebou.  
  
 [Kontrakty](../../../../docs/framework/wcf/feature-details/contracts.md)  
 Popisuje, jak definovat kontrakty metody služby.  
  
 [Postupy: Vytvoření koncového bodu služby v konfiguraci](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 Popisuje postup vytvoření koncového bodu služby v konfiguraci.  
  
 [Postupy: Vytvoření koncového bodu služby v kódu](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 Popisuje postup vytvoření koncového bodu služby v kódu.  
  
 [Postupy: Ověření zkompilovaného kódu služby pomocí nástroje Svcutil.exe](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 Popisuje, jak detekovat chyby v implementace služby a konfigurace bez hostování služby pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace služeb](../../../../docs/framework/wcf/configuring-services.md)  
 [Rozšíření vazeb](../../../../docs/framework/wcf/extending/extending-bindings.md)

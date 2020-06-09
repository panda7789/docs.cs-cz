---
title: 'Koncové body: adresy, vazby a kontrakty'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 3ac7f0b165b99a1ed3702628958f7d4c7702f5b1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593513"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a>Koncové body: adresy, vazby a kontrakty

Veškerá komunikace se službou Windows Communication Foundation (WCF) probíhá prostřednictvím *koncových bodů* služby. Koncové body poskytují klientům přístup k funkcím, které nabízí služba WCF.

Každý koncový bod se skládá ze čtyř vlastností:

- Adresa, která indikuje, kde lze koncový bod najít.

- Vazba, která určuje, jak klient může komunikovat s koncovým bodem.

- Kontrakt, který identifikuje dostupné operace.

- Sada chování, která určuje podrobnosti o místní implementaci koncového bodu.

Toto téma popisuje tuto strukturu koncových bodů a vysvětluje, jak je znázorněno v objektovém modelu WCF.

## <a name="the-structure-of-an-endpoint"></a>Struktura koncového bodu

Každý koncový bod se skládá z následujících možností:

- Adresa: Adresa jednoznačně identifikuje koncový bod a oznamuje potenciálním příjemcům služby, kde se nachází. Je reprezentovaná v objektovém modelu WCF <xref:System.ServiceModel.EndpointAddress> třídou. <xref:System.ServiceModel.EndpointAddress>Třída obsahuje:

  - <xref:System.ServiceModel.EndpointAddress.Uri%2A>Vlastnost, která představuje adresu služby.

  - <xref:System.ServiceModel.EndpointAddress.Identity%2A>Vlastnost, která představuje identitu zabezpečení služby a kolekci volitelných záhlaví zpráv. Volitelná záhlaví zpráv slouží k poskytnutí dalších a podrobnějších informací o adresách k identifikaci nebo interakci s koncovým bodem.

  Další informace najdete v tématu [určení adresy koncového bodu](../specifying-an-endpoint-address.md).

- Binding: Vazba určuje, jak komunikovat s koncovým bodem. Sem patří:

  - Transportní protokol, který se má použít (například TCP nebo HTTP).

  - Kódování, které má být použito pro zprávy (například text nebo Binary).

  - Nezbytné požadavky na zabezpečení (například zabezpečení SSL nebo SOAP zprávy).

  Další informace najdete v tématu [Přehled vazeb WCF](../bindings-overview.md). Vazba je reprezentovaná v objektovém modelu WCF abstraktní základní třídou <xref:System.ServiceModel.Channels.Binding> . Ve většině scénářů můžou uživatelé použít jednu z vazeb poskytovaných systémem. Další informace najdete v tématu o [vazbách poskytovaných systémem](../system-provided-bindings.md).

- Smlouvy: kontrakt obsahuje popis funkcí, které koncový bod zpřístupňuje klientovi. Kontrakt Určuje:

  - Které operace může klient volat.

  - Forma zprávy

  - Typ vstupních parametrů nebo dat vyžadovaných pro volání operace.

  - Jaký typ zprávy pro zpracování nebo odpověď může klient očekávat.

  Další informace o definování kontraktu najdete v tématu [Navrhování kontraktů služby](../designing-service-contracts.md).

- Chování: k přizpůsobení místního chování koncového bodu služby můžete použít chování koncového bodu. Chování koncového bodu dosahuje tím, že se účastní procesu vytváření modulu runtime WCF. Příkladem chování koncového bodu je <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> vlastnost, která umožňuje zadat jinou naslouchající adresu než adresa SOAP nebo Web Services Description Language (WSDL). Další informace najdete v tématu [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).

## <a name="defining-endpoints"></a>Definování koncových bodů

Můžete určit koncový bod pro službu buď imperativně pomocí kódu, nebo deklarativně prostřednictvím konfigurace. Další informace najdete v tématech [Postupy: Vytvoření koncového bodu služby v konfiguraci](how-to-create-a-service-endpoint-in-configuration.md) a [Postupy: Vytvoření koncového bodu služby v kódu](how-to-create-a-service-endpoint-in-code.md).

## <a name="in-this-section"></a>V tomto oddílu

Tato část vysvětluje účel vazeb, koncových bodů a adres; ukazuje, jak nakonfigurovat vazbu a koncový bod. a ukazuje, jak používat `ClientVia` chování a `ListenUri` vlastnost.

[Adresa](endpoint-addresses.md)\
Popisuje způsob adresování koncových bodů ve službě WCF.

[Vazeb](bindings.md)\
Popisuje způsob, jakým se používají vazby k určení přenosu, kódování a podrobností protokolu požadovaných pro komunikaci mezi klienty a službami.

[Financovan](contracts.md)\
Popisuje, jak kontrakty definují metody služby.

[Postupy: Vytvoření koncového bodu služby v konfiguraci](how-to-create-a-service-endpoint-in-configuration.md)\
Popisuje postup vytvoření koncového bodu služby v konfiguraci.

[Postupy: Vytvoření koncového bodu služby v kódu](how-to-create-a-service-endpoint-in-code.md)\
Popisuje postup vytvoření koncového bodu služby v kódu.

[Postupy: použití Svcutil. exe k ověření kódu zkompilované služby](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)\
V této části najdete popis postupu při detekci chyb v implementacích a konfiguracích služby bez hostování služby pomocí nástroje pro nástroj pro [metadata ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).

## <a name="see-also"></a>Viz také

- [Konfigurace služeb](../configuring-services.md)
- [Rozšíření vazeb](../extending/extending-bindings.md)

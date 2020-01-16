---
title: Konfigurace Internetové informační služby 7.0 pro službu Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 41eedcf78d8ca6f10fcd0380e43420dcc1b328f1
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964509"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a>Konfigurace Internetové informační služby 7.0 pro službu Windows Communication Foundation

Internetová informační služba (IIS) 7,0 má modulární návrh, který umožňuje selektivní instalaci požadovaných součástí. Tento návrh je založený na nové technologii komponenty založené na manifestech, kterou přináší Windows Vista. Existuje více než 40 samostatných součástí služby IIS 7,0, které je možné nainstalovat nezávisle. IT profesionálům umožňuje snadno přizpůsobit instalaci podle potřeby. Toto téma popisuje, jak nakonfigurovat službu IIS 7,0 pro použití s Windows Communication Foundation (WCF) a určit, které součásti jsou nutné.

## <a name="minimal-installation-installing-was"></a>Minimální instalace: Instalace byla
 Minimální instalací celého balíčku služby IIS 7,0 je instalace aktivační služby procesů systému Windows (WAS). WAS je samostatná funkce, která je jedinou funkcí ze služby IIS 7,0, která je dostupná pro všechny operační systémy Windows Vista (Home Basic, Home Premium, Business a Ultimate a Enterprise).

 V Ovládacích panelech klikněte na **programy** a potom klikněte na **zapnout nebo vypnout funkce systému Windows** , které jsou uvedené v části **programy a funkce**. v seznamu se zobrazí tato součást jako na následujícím obrázku.

 ![Zapnout nebo vypnout funkce dialogového okna](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")

 Tato funkce má následující dílčí komponenty:

- Prostředí .NET

- Rozhraní API pro konfiguraci

- Model procesu

 Pokud vyberete kořenový uzel, bude ve výchozím nastavení kontrolován pouze dílčí uzel **modelu procesu** . Počítejte s tím, že při instalaci, kterou nainstalujete, byla nainstalována pouze aplikace, protože není k dispozici podpora webového serveru.

 Pokud chcete zajistit, aby WCF nebo aplikace ASP.NET fungovaly, zaškrtněte políčko **prostředí .NET** . To znamená, že všechny komponenty byly potřebné k tomu, aby služba WCF a ASP.NET správně fungovala. Tyto součásti jsou automaticky kontrolovány po instalaci kterékoli z těchto součástí.

## <a name="iis-70-default-installation"></a>IIS 7,0: výchozí instalace
 Zaškrtnutím funkce **Internetová informační služba** se některé dílčí uzly automaticky zkontrolují, jak je znázorněno na následujícím obrázku.

 ![Výchozí nastavení pro funkce IIS 7,0](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")

 Toto je výchozí instalace služby IIS 7,0. V rámci této instalace můžete použít službu IIS 7,0 pro obsluhu statického obsahu (například stránky HTML a další obsah). Nemůžete ale spouštět aplikace ASP.NET nebo CGI ani hostitelské služby WCF.

## <a name="iis-70-installation-with-aspnet-support"></a>IIS 7,0: instalace s podporou ASP.NET
 Abyste mohli ASP.NET pracovat na IIS 7,0, musíte nainstalovat ASP.NET. Po kontrole **ASP.NET**by měla obrazovka vypadat jako na následujícím obrázku.

 ![Asp.NET – požadovaná nastavení](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")

 Toto je minimální prostředí pro aplikace WCF a ASP.NET, aby fungovalo ve službě IIS 7,0.

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a>IIS 7,0: instalace se součástmi kompatibility IIS 6,0
 Při instalaci IIS 7,0 na systém se sadou Visual Studio 2005 nebo některé jiné skripty nebo nástroje pro automatizaci (například Adsutil. vbs), které konfigurují virtuální aplikace, které používají službu IIS 6,0 API, se ujistěte, že jste zkontrolovali **Nástroje pro skriptování**služby iis na 6,0. Tím se automaticky zkontroluje ostatní poduzly **kompatibility správy**služby IIS 6,0. Následující ilustrace znázorňuje obrazovku po dokončení:

 ![Nastavení kompatibility správy služby IIS 6,0](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")

 V rámci této instalace máte vše potřebné k používání funkcí IIS 7,0, ASP.NET a WCF a ukázek, které jsou k dispozici na webu.

## <a name="request-limits"></a>Omezení počtu požadavků
 V systému Windows Vista se službou IIS 7 byla změněna výchozí hodnota `maxUri` a nastavení `maxQueryStringSize`. Ve výchozím nastavení umožňuje filtrování požadavků ve službě IIS 7,0 délku adresy URL 4096 znaků a délka řetězce dotazu 2048 znaků. Chcete-li změnit tyto výchozí hodnoty, přidejte do souboru App. config následující kód XML.

```xml
 <system.webServer>
    <security>
        <requestFiltering>
            <requestLimits maxUrl="8192" maxQueryString="8192" />
        </requestFiltering>
    </security>
 </system.webServer>
 ```

## <a name="see-also"></a>Viz také:

- [Architektura aktivace WAS](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [Konfigurace WAS pro použití s WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [Postupy: Instalace a konfigurace aktivačních komponent WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- [Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))

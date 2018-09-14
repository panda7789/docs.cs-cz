---
title: Konfigurace Internetové informační služby 7.0 pro službu Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 13fd068f7a058a0fbf4e15fc99a8de91671fb2d5
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521352"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a>Konfigurace Internetové informační služby 7.0 pro službu Windows Communication Foundation

Internetové informační služby (IIS) 7.0 má modulárního návrhu, který vám umožní selektivně nainstalovat součásti, které jsou požadovány. Tento návrh vychází nové technologie řízené manifestu componentization zavedené v [!INCLUDE[wv](../../../../includes/wv-md.md)]. Existuje více než 40 samostatné funkce součásti služby IIS 7.0, který je možné nainstalovat nezávisle na sobě. To umožňuje odborníkům v oblasti IT snadno instalaci podle potřeby přizpůsobit. Toto téma popisuje, jak nakonfigurovat Internetové informační služby 7.0 pro použití s Windows Communication Foundation (WCF) a určit, jaké součásti jsou potřeba.

## <a name="minimal-installation-installing-was"></a>Při minimální instalaci: Při instalaci služby WAS
 Minimální instalaci celý balíček služby IIS 7.0 je instalace služby Aktivace procesu Windows (WAS). BYL samostatná funkce a je pouze funkci pomocí služby IIS 7.0, která je k dispozici pro všechny [!INCLUDE[wv](../../../../includes/wv-md.md)] operační systémy (Home Basic, Home Premium, firmy a Ultimate a Enterprise).

 V Ovládacích panelech klikněte na **programy** a potom klikněte na tlačítko **Windows zapnout nebo vypnout funkce** které je uvedené v části **programy a funkce**, WAS komponenta je zobrazena ve seznam jako na následujícím obrázku.

 ![Funkce zapnout nebo vypnout dialogového okna](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")

 Tato funkce má následující dílčí součásti:

-   Prostředí .NET

-   Rozhraní API pro konfiguraci

-   Model procesu

 Pokud vyberete kořenový uzel WAS, pouze **Model procesu** podřízený uzel je ve výchozím nastavení zaškrtnuto. Mějte prosím na paměti, že v této instalaci pouze instalujete WAS, protože neexistuje žádná podpora pro webový server.

 Chcete-li WCF nebo libovolné pracovní aplikace technologie ASP.NET, zkontrolujte **prostředí .NET** zaškrtávací políčko. To znamená, že všechny součásti WAS se vyžadují, aby WCF a ASP.NET pracovat dobře. Tyto kontroluje automaticky po instalaci některé z těchto komponent.

## <a name="iis-70-default-installation"></a>Služby IIS 7.0: Výchozí instalaci
 Kontrolou **Internetová informační služba** funkce, některé dílčí uzly automaticky zkontrolovány, jak je znázorněno na následujícím obrázku.

 ![Výchozí nastavení pro funkce služby IIS 7.0](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")

 Toto je výchozí instalaci IIS 7.0. Této instalace můžete použít služby IIS 7.0 na statický obsah služby (například stránky HTML a další obsah). Nelze však spustit aplikace ASP.NET a CGI nebo hostovat služby WCF.

## <a name="iis-70-installation-with-aspnet-support"></a>Služby IIS 7.0: Instalace s podporou technologie ASP.NET
 Je nutné nainstalovat technologie ASP.NET, aby práce ve službě IIS 7.0 ASP.NET. Po kontrole **ASP.NET**, vaše obrazovka by měla vypadat jako na následujícím obrázku.

 ![Asp.NET požadovaná nastavení](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")

 Toto je minimální prostředí pro spolupráci ve službě IIS 7.0 aplikací WCF a ASP.NET.

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a>Služby IIS 7.0: Instalace pomocí součásti služby IIS 6.0 kompatibility
 Při instalaci služby IIS 7.0 v systému Visual Studio 2005 nebo některé jiné skripty pro automatizaci nebo nástroje (například Adsutil.vbs), které konfigurují virtuální aplikace, které používají rozhraní API metabáze služby IIS 6.0, ujistěte se, že zkontrolujete služby IIS 6.0 **nástroje pro skriptování**. To automaticky kontroluje ostatní uzly dílčí služby IIS 6.0 **Kompatibilita správy**. Následující obrázek znázorňuje obrazovky, po dokončení:

 ![Nastavení kompatibility služby IIS 6.0 správu](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")

 Díky této instalace máte vše, co je potřeba používat funkce služby IIS 7.0, technologii ASP.NET a WCF a ukázky, které jsou k dispozici na webu.

## <a name="request-limits"></a>Omezení počtu požadavků
 Na [!INCLUDE[wv](../../../../includes/wv-md.md)] se službou IIS 7 výchozí hodnotu z `maxUri` a `maxQueryStringSize` nastavení se změnily. Ve výchozím nastavení filtrování požadavků ve službě IIS 7.0 umožňuje délka adresy URL počet 4 096 znaků a délku řetězce dotazu 2 048 znaků. Chcete-li změnit tyto výchozí hodnoty do souboru App.config přidejte následující kód XML.

 `<system.webServer>`

 `<security>`

 `<requestFiltering>`

 `<requestLimits maxUrl="8192" maxQueryString="8192" />`

 `</requestFiltering>`

 `</security>`

 `</system.webServer>`

## <a name="see-also"></a>Viz také

- [Architektura aktivace WAS](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [Konfigurace WAS pro použití s WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [Postupy: Instalace a konfigurace aktivačních komponent WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- [Hostování funkcí systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)

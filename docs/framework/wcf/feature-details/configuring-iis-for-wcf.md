---
title: "Konfigurace Internetové informační služby 7.0 pro službu Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 185fa5e641a1834a7c5f7906b5e5cf84dacaa9f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a>Konfigurace Internetové informační služby 7.0 pro službu Windows Communication Foundation
Internetové informační služby (IIS) 7.0 má modulární návrh, který vám umožní selektivně nainstalovat komponenty, které jsou požadovány. Tento návrh vychází z technologie nové řízené manifest componentization byla zavedená v [!INCLUDE[wv](../../../../includes/wv-md.md)]. Existuje více než 40 samostatné funkce součástí [!INCLUDE[iisver](../../../../includes/iisver-md.md)] který lze nainstalovat nezávisle. To umožňuje odborníkům v oblasti IT snadno instalaci podle potřeby přizpůsobit. Toto téma popisuje postup konfigurace [!INCLUDE[iisver](../../../../includes/iisver-md.md)] pro použití s [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a určit, které součásti jsou vyžadovány.  
  
## <a name="minimal-installation-installing-was"></a>Minimální instalaci: Instalace WAS  
 Minimální instalaci celek [!INCLUDE[iisver](../../../../includes/iisver-md.md)] balíčku je instalace služby Aktivace procesů systému Windows (WAS). BYL je samostatná funkce a je funkce jen ze [!INCLUDE[iisver](../../../../includes/iisver-md.md)] která je k dispozici pro všechny [!INCLUDE[wv](../../../../includes/wv-md.md)] operační systémy (Home Basic, Home Premium, obchodní a Ultimate a Enterprise).  
  
 Z ovládacích panelů, klikněte na tlačítko **programy** a pak klikněte na **Windows zapnout nebo vypnout funkce** který je uveden v části **programy a funkce**, komponentu WAS se zobrazí v seznam jako na následujícím obrázku.  
  
 ![Funkce zapnout nebo vypnout dialogové okno](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")  
  
 Tato funkce má následující dílčí součásti:  
  
-   Prostředí .NET  
  
-   Rozhraní API pro konfiguraci  
  
-   Model procesu  
  
 Pokud vyberete kořenového uzlu služby WAS, jenom **Model procesu** dílčí je zaškrtnuto políčko ve výchozím nastavení. Upozorňujeme, že k této instalaci pouze instalujete WAS, protože neexistuje žádná podpora pro webový server.  
  
 Chcete-li [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nebo jakoukoli [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace fungovat, zkontrolujte **prostředí .NET** zaškrtávací políčko. To znamená, že všechny WAS součásti nutné k [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] fungovat správně. Tyto jsou automaticky zkontrolovány po instalaci některé z těchto součástí.  
  
## <a name="iis-70-default-installation"></a>Služby IIS 7.0: Výchozí instalace  
 Kontrolou **Internetová informační služba** funkce, některé dílčí uzly jsou automaticky zkontrolovány, jak je znázorněno na následujícím obrázku.  
  
 ![Výchozí nastavení pro funkce služby IIS 7.0](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")  
  
 Toto je výchozí instalace [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. V této instalace, můžete použít [!INCLUDE[iisver](../../../../includes/iisver-md.md)] do služby statický obsah (například stránky HTML a jiný obsah). Však nelze spustit [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] nebo aplikace CGI nebo hostitele [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.  
  
## <a name="iis-70-installation-with-aspnet-support"></a>Služba IIS 7.0: Instalace s podporou technologie ASP.NET  
 Je nutné nainstalovat [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aby [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pracovní ve službě IIS 7.0. Po zkontrolování **ASP.NET**, obrazovky by měl vypadat jako na následujícím obrázku.  
  
 ![Asp.NET požadované nastavení](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")  
  
 Toto je minimální prostředí pro obě [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace pro práci v [!INCLUDE[iisver](../../../../includes/iisver-md.md)].  
  
## <a name="iis-70-installation-with-iis-60-compatibility-components"></a>Služby IIS 7.0: Instalace se součásti služby IIS 6.0 kompatibility  
 Při instalaci [!INCLUDE[iisver](../../../../includes/iisver-md.md)] v systému Visual Studio 2005 nebo některé jiné skripty pro automatizaci nebo nástrojích (například Adsutil.vbs), která konfigurovat virtuální aplikace, které používají [!INCLUDE[iis601](../../../../includes/iis601-md.md)] metabáze rozhraní API, ujistěte se, že můžete kontrolovat [!INCLUDE[iis601](../../../../includes/iis601-md.md)]  **Nástroje pro skriptování**. Toto automaticky kontroluje do dalších dílčí uzlů [!INCLUDE[iis601](../../../../includes/iis601-md.md)] **Kompatibilita správy**. Následující obrázek znázorňuje obrazovky po dokončení.  
  
 ![Nastavení kompatibility služby IIS 6.0 správy](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")  
  
 Díky této instalace, budete mít všechno, co je potřeba použít [!INCLUDE[iisver](../../../../includes/iisver-md.md)], [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkce a ukázky k dispozici na webu.  
  
## <a name="request-limits"></a>Omezení požadavků  
 Na [!INCLUDE[wv](../../../../includes/wv-md.md)] se službou IIS 7 výchozí hodnota z `maxUri` a `maxQueryStringSize` došlo ke změně nastavení. Ve výchozím nastavení umožňuje filtrování požadavků ve službě IIS 7.0 délka adresy URL počet 4 096 znaků a délku řetězce dotazu 2048 znaků. Chcete-li změnit tato výchozí nastavení do souboru App.config přidejte následující kód XML.  
  
 `<system.webServer>`  
  
 `<security>`  
  
 `<requestFiltering>`  
  
 `<requestLimits maxUrl="8192" maxQueryString="8192" />`  
  
 `</requestFiltering>`  
  
 `</security>`  
  
 `</system.webServer>`  
  
## <a name="see-also"></a>Viz také  
 [Architektura aktivace WAS](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)  
 [Konfigurace WAS pro použití s WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [Postupy: instalace a konfigurace aktivačních komponent WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)  
 [Hostování funkcí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)

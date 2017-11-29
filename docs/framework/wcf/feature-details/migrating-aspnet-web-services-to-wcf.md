---
title: "Migrace webových služeb ASP.NET na WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e2051de2c0cef9a31337b320c347bb7d85dbadae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>Migrace webových služeb ASP.NET na WCF
Technologie ASP.NET poskytuje knihovny tříd rozhraní .NET Framework a nástroje pro vytváření webových služeb, jakož i zařízení pro hostování služeb v rámci Internetové informační služby (IIS). [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]poskytuje knihovny tříd rozhraní .NET Framework, nástroje a hostování zařízení pro povolení softwaru entity na komunikaci pomocí žádné protokoly, včetně těch, které používá webové služby.  Migrace webových služeb ASP.NET pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] umožňuje využívat nové funkce a vylepšení, které jsou jedinečné pro vaše aplikace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]má několik výhod, které jsou relativní vzhledem k webových služeb ASP.NET důležité. ASP.NET – webové služby nástroje jsou výhradně pro vytváření webových služeb, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje nástroje, které lze použít při softwaru entit musí být provedeny na vzájemnou komunikaci. Tím se sníží počet technologie, které vývojáři je potřeba znát, aby bylo možné ošetřit scénáře komunikace jiný software, které pak bude snížit náklady na prostředky pro vývoj softwaru, jakož i čas na dokončení softwaru projekty vývoje.  
  
 I pro projekty vývoje webové služby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporuje více webové protokoly služby, než webových služeb ASP.NET podpory. Tyto další protokoly zadejte pro složitější řešení zahrnující, mimo jiné spolehlivé relace a transakce.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]podporuje více protokolů pro přenos zpráv, než webových služeb ASP.NET. Webových služeb ASP.NET podporují pouze odesílání zpráv pomocí protokol HTTP (Hypertext Transfer). [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]podporuje odesílání zpráv pomocí protokolu HTTP, stejně jako protokolu TCP (Transmission Control), pojmenované kanály a Microsoft služby Řízení front zpráv (MSMQ). Důležitější, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] můžete rozšířit pro zajištění podpory další přenosové protokoly. Proto softwaru vyvinuté pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dokáže se přizpůsobit fungují společně s širší rozsah další software, tedy zvýšení návratnosti investice potenciální.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]poskytuje mnohem širší zařízení pro nasazení a Správa aplikací, než poskytuje webových služeb ASP.NET. Kromě konfigurace systém, který má také ASP.NET, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nabízí editor konfigurací, trasování aktivit odesílatelé k příjemce a zpět přes libovolný počet prostředníci, prohlížeč sledování, protokolování zpráv, valná počet výkonu čítače a podpora pro Windows Management Instrumentation.  
  
 Zadané tyto potenciální výhody [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] relativně k webových služeb ASP.NET, pokud používáte, nebo se s pomocí webových služeb ASP.NET máte několik možností:  
  
-   Pokračovat v používání webových služeb ASP.NET, a ukončí toto výhody proffered podle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
-   Zabezpečení pomocí webových služeb ASP.NET tak, aby přijetí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] někdy v budoucnu. Témata v této části popisují, jak chcete maximalizovat perspektiv bude možné použít nové aplikace ASP.NET – webové služby spolu s budoucí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace. Témata v této části také popisují, jak vytvářet nové ASP.NET – webové služby tak, aby bylo snazší jejich migrace na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Ale pokud zabezpečení služby je důležité, nebo spolehlivost nebo transakci záruky, pokud jsou požadované, nebo pokud vlastní správy zařízení bude muset být vytvořená a pak jedná se o lepší možnost přijmout [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]je určená pro přesněji takových scénářů.  
  
-   Přijmout [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pro nový vývoj přitom dál spravovat vaše existující aplikace ASP.NET – webové služby. Tato volba je velmi pravděpodobně optimální. Vrací výhod [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], při Reserve Sparing Table náklady na změnu existujících aplikací používat. V tomto scénáři nové [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace může existovat společně se stávajícími aplikacemi ASP.NET. Nové [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace budou moci používat existující webových služeb ASP.NET, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] slouží k programu nové provozní funkce do existující aplikace ASP.NET základě [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] režim kompatibility ASP.NET.  
  
-   Přijmout [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a migraci stávajících aplikací ASP.NET – webové služby pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Můžete se rozhodnout tuto možnost k rozšíření stávajících aplikací s funkcí poskytovaných [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], nebo pro funkci existujících služeb ASP.NET Web v rámci nové výkonnější [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace.  
  
> [!NOTE]
>  Musí dát pozor, pokud [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba je hostována službou IIS se odinstaluje 5.x a ASP.NET. Když [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba je hostována službou IIS 5.x, kód pro službu, mohou být požadována, pokud technologie ASP.NET je odinstalován. Při odinstalaci ASP.NET na operační systém, který je spuštěna služba IIS 5.x a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je odinstalován, soubor s příponou .svc považuje textového souboru a jeho obsah, včetně zdrojového kódu, je vrácen do žadatel.  
  
 V této části popisují tyto možnosti podrobně, porovná webové služby ASP.NET do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a poskytuje pokyny o tom, jak migrovat kódu webové služby ASP.NET do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="see-also"></a>Viz také  
 [Očekávání přechodu služby Windows Communication Foundation: usnadnění budoucí migrace](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)  
 [Očekávání přechodu služby Windows Communication Foundation: usnadnění budoucí integrace](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)  
 [Přijetí WCF](../../../../docs/framework/wcf/feature-details/adopting-wcf.md)  
 [Porovnání webových služeb ASP.NET na WCF na základě účelu a používaných standardů](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)  
 [Porovnání webových služeb ASP.NET na WCF z hlediska vývojových požadavků](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)

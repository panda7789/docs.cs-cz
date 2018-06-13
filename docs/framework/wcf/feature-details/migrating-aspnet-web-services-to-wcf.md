---
title: Migrace webových služeb ASP.NET na WCF
ms.date: 03/30/2017
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
ms.openlocfilehash: 7d43c66952d17a91e38ae1b086478b9416321b8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494559"
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>Migrace webových služeb ASP.NET na WCF
Technologie ASP.NET poskytuje knihovny tříd rozhraní .NET Framework a nástroje pro vytváření webových služeb, jakož i zařízení pro hostování služeb v rámci Internetové informační služby (IIS). Windows Communication Foundation (WCF) poskytuje knihovny tříd rozhraní .NET Framework, nástroje a hostování zařízení pro povolení softwaru entity na komunikaci pomocí žádné protokoly, včetně těch, které používá webové služby.  Migrace webových služeb ASP.NET na WCF umožňuje aplikacím využívat nové funkce a vylepšení, které jsou jedinečné pro WCF.  
  
 WCF má několik výhod, které jsou relativní vzhledem k webových služeb ASP.NET důležité. ASP.NET – webové služby nástroje jsou výhradně pro vytváření webových služeb, WCF poskytuje nástroje, které lze použít při softwaru entit musí být provedeny na vzájemnou komunikaci. Tím se sníží počet technologie, které vývojáři je potřeba znát, aby bylo možné ošetřit scénáře komunikace jiný software, které pak bude snížit náklady na prostředky pro vývoj softwaru, jakož i čas na dokončení softwaru projekty vývoje.  
  
 I pro projekty vývoje webové služby WCF podporuje další protokoly webové služby, než podpora rozhraní ASP.NET Web services. Tyto další protokoly zadejte pro složitější řešení zahrnující, mimo jiné spolehlivé relace a transakce.  
  
 WCF podporuje více protokolů pro přenos zpráv, než webových služeb ASP.NET. Webových služeb ASP.NET podporují pouze odesílání zpráv pomocí protokol HTTP (Hypertext Transfer). WCF podporuje odesílání zpráv pomocí protokolu HTTP, stejně jako protokolu TCP (Transmission Control), pojmenované kanály a Microsoft služby Řízení front zpráv (MSMQ). Důležitější, WCF lze rozšířit pro podporu dalších přenosové protokoly. Proto může být software vyvinuté pomocí WCF přizpůsobena fungují společně s širší rozsah další software, a tím zvýšit potenciální návratnost investic.  
  
 WCF obsahuje mnohem širší zařízení pro nasazení a Správa aplikací než webových služeb ASP.NET. Kromě konfigurace systém, který má také ASP.NET, WCF nabízí editor konfigurací, trasování aktivit z odesílatelé k příjemce a zpět prostřednictvím libovolný počet prostředníci, prohlížeč sledování, protokolování zpráv, valná počet čítače výkonu, a Podpora rozhraní Windows Management Instrumentation.  
  
 Zadané tyto výhody využít WCF relativně k rozhraní ASP.NET Web services, pokud používáte, nebo se s pomocí webových služeb ASP.NET máte několik možností:  
  
-   Pokračujte v používání webových služeb ASP.NET, a ukončí toto výhody proffered službou WCF.  
  
-   Zabezpečení pomocí webových služeb ASP.NET tak, aby přijetí WCF někdy v budoucnu. Témata v této části popisují, jak chcete maximalizovat perspektiv bude možné použít nové aplikace ASP.NET – webové služby spolu s budoucí aplikace WCF. Témata v této části také popisují, jak vytvářet nové ASP.NET – webové služby tak, aby bylo snazší jejich migrací do WCF. Ale pokud zabezpečení služby je důležité, nebo spolehlivost nebo transakci záruky, pokud jsou požadované, nebo pokud vlastní správy zařízení bude muset být vytvořená a potom jedná se o lepší možnost přijmout WCF. WCF je určená pro přesněji takových scénářů.  
  
-   Přijmout pro nový vývoj přitom dál spravovat vaše existující aplikace ASP.NET – webové služby WCF. Tato volba je velmi pravděpodobně optimální. Výhody služby WCF, bude vrácen při Reserve Sparing Table náklady na změnu existujících aplikací používat. V tomto scénáři mohou koexistovat nové aplikace WCF se stávajícími aplikacemi ASP.NET. Nové aplikace WCF, bude moci používat existující webových služeb ASP.NET a WCF umožňuje programu nové provozní funkce do existující aplikace ASP.NET na základě režim kompatibility WCF ASP.NET.  
  
-   Přijetí WCF a migraci stávajících aplikací ASP.NET – webové služby pro WCF. Můžete se rozhodnout tuto možnost k rozšíření stávajících aplikací pomocí funkce poskytované službou WCF a reprodukujte funkce stávajících webových služeb ASP.NET v rámci nové, výkonnější aplikace WCF.  
  
> [!NOTE]
>  Musí dát pozor, pokud je služby WCF hostované službou IIS se odinstaluje 5.x a ASP.NET. Když je služba WCF hostované službou IIS 5.x, kód pro službu, mohou být požadována, pokud technologie ASP.NET je odinstalován. Při odinstalaci ASP.NET na operační systém, který je spuštěna služba IIS 5.x a WCF se odinstaluje, soubor s příponou .svc považuje za textového souboru a jeho obsah, včetně zdrojového kódu, je vrácen do žadatel.  
  
 V této části popisují tyto možnosti podrobně, porovná webových služeb ASP.NET na WCF a obsahuje pokyny k migraci kódu webové služby ASP.NET na WCF.  
  
## <a name="see-also"></a>Viz také  
 [Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí migrace](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)  
 [Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí integrace](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)  
 [Přijetí Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/adopting-wcf.md)  
 [Porovnání webových služeb ASP.NET se službou WCF na základě účelu a používaných standardů](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)  
 [Porovnání webových služeb ASP.NET s technologií WCF z hlediska vývojových požadavků](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)

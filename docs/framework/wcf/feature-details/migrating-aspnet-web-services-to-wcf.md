---
title: Migrace webových služeb ASP.NET na WCF
ms.date: 03/30/2017
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
ms.openlocfilehash: 6fb96dc431008936658bb941f16373037e712f51
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736205"
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>Migrace webových služeb ASP.NET na WCF
Technologie ASP.NET poskytuje nástroje a knihovny tříd rozhraní .NET Framework pro vytváření webových služeb, stejně jako zařízení pro hostování služby v rámci Internetové informační služby (IIS). Windows Communication Foundation (WCF) poskytuje knihovny tříd rozhraní .NET Framework, nástroje a hostingové zařízení umožňující použití softwaru entity na komunikaci pomocí žádné protokoly, včetně těch, které používají webové služby.  Migrace webových služeb ASP.NET na WCF umožňuje vašim aplikacím, abyste mohli využívat nové funkce a vylepšení, které jsou jedinečné pro WCF.  
  
 WCF má několik výhod důležité vzhledem k webové služby ASP.NET. Nástroje služby pro ASP.NET Web jsou výhradně pro vytváření webových služeb, WCF poskytuje nástroje, které se dá použít při softwarové entity se musí provádět komunikovat mezi sebou. Tím se sníží počet technologie, které jsou potřeba vědět, aby bylo možné ošetřit scénáře komunikace jiný software, které bude zase snížit náklady na prostředky pro vývoj softwaru, jakož i čas k dokončení softwaru vývojáře vývojové projekty.  
  
 I pro webové služby vývojové projekty WCF podporuje další protokoly webové služby, než rozhraní ASP.NET Web služby podpory. Tyto další protokoly poskytují pro složitější řešení zahrnující, mimo jiné spolehlivé relace a transakce.  
  
 WCF podporuje více protokolů pro přenos zpráv, než webové služby ASP.NET. Webových služeb ASP.NET se podporují jenom odesílání zpráv s použitím protokol HTTP (Hypertext Transfer). WCF podporuje odesílání zpráv pomocí protokolu HTTP, jakož i protokolu TCP (Transmission Control), pojmenované kanály a Microsoft Message Queuing (MSMQ). Důležitější, WCF je možné rozšířit na podporu dalších přenosové protokoly. Proto může být software vyvinutý pomocí technologie WCF přizpůsobena fungují společně s širší dalšího softwaru, čímž roste potenciální návratnost investic.  
  
 WCF poskytuje mnohem bohatší zařízení pro nasazení a správu aplikací než webové služby ASP.NET. Kromě konfigurace systému, která má také technologie ASP.NET, WCF, nabízí editor konfigurací, trasování činnosti z odesílatelů příjemců a zpět prostřednictvím libovolný počet prostředníci, prohlížeče trasování, protokolování zpráv, rozsáhlé počet čítačů výkonu, a Podpora pro Windows Management Instrumentation.  
  
 Zadaný tyto výhody služby WCF vzhledem k rozhraní ASP.NET Web services, pokud používáte nebo zvažuje použít webových služeb ASP.NET s máte několik možností:  
  
-   Nadále používat webových služeb ASP.NET a připadají výhody proffered službou WCF.  
  
-   Dál používejte webových služeb ASP.NET s tak přijetí WCF někdy v budoucnu. Témata v této části popisují, jak maximalizovat perspektivami bude možné použít nové aplikace ASP.NET Web service společně s budoucí aplikace WCF. Témata v této části popisují, jak vytvářet nové webové služby tak, aby bylo snazší migrace do WCF. Ale pokud zabezpečení služeb je důležité, nebo spolehlivost nebo transakce záruky, které jsou požadovány, nebo pokud vlastní správy zařízení budou muset sestavit, pak je lepší volbou přijmout WCF. WCF je určená pro přesně takové scénáře.  
  
-   Přijmout pro vývoj nových projektů, zatímco i nadále bude udržovat vaše stávající technologie ASP.NET webové aplikace služby WCF. Tato volba je velmi pravděpodobné, že optimální. Výhody služby WCF, bude vrácen při Reserve Sparing Table náklady na úpravy existujících aplikací používat. V tomto scénáři můžete nové aplikace WCF existovat vedle sebe se stávajícími aplikacemi ASP.NET. Nové aplikace WCF budete moct používat existující webové služby ASP.NET a WCF je možné program nové možnosti provozní do stávajících aplikací ASP.NET tím, že režim kompatibility WCF ASP.NET.  
  
-   Přijmout WCF a migrace existujících aplikací služby technologie ASP.NET na WCF. Můžete tuto možnost k vylepšení stávajících aplikací pomocí funkce poskytované službou WCF a reprodukovat funkce stávajících webových služeb ASP.NET v rámci nové, výkonnější aplikace WCF.  
  
> [!NOTE]
>  Třeba dávat pozor, pokud je služba WCF hostovaná ve službě IIS se odinstaluje 5.x a ASP.NET. Když je služby WCF hostované službou IIS 5.x kód služby, mohou být požadována Pokud odinstalaci technologie ASP.NET. Při odinstalaci technologie ASP.NET v operačním systému, na kterém běží služba IIS 5.x a WCF se odinstaluje, považuje za soubor s příponou .svc textový soubor a obsah, včetně zdrojového kódu, je vrácena žadateli.  
  
 Tato část popisuje tyto možnosti podrobně, porovná webových služeb ASP.NET na WCF a obsahuje pokyny, jak migrace kódu webové služby ASP.NET na WCF.  
  
## <a name="see-also"></a>Viz také:
- [Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí migrace](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
- [Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí integrace](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
- [Přijetí Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/adopting-wcf.md)
- [Porovnání webových služeb ASP.NET se službou WCF na základě účelu a používaných standardů](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
- [Porovnání webových služeb ASP.NET s technologií WCF z hlediska vývojových požadavků](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)

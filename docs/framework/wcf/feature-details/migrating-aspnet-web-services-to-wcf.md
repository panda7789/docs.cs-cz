---
title: Migrace webových služeb ASP.NET na WCF
ms.date: 03/30/2017
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
ms.openlocfilehash: fa707a4246d5bc9940417072c098b2973140f878
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598798"
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>Migrace webových služeb ASP.NET na WCF
ASP.NET poskytuje .NET Framework knihovny tříd a nástroje pro vytváření webových služeb a také zařízení pro hostování služeb v rámci služby Internetová informační služba (IIS). Windows Communication Foundation (WCF) poskytuje .NET Framework knihoven tříd, nástrojů a hostitelských prostředí pro umožnění komunikace softwarových entit pomocí libovolných protokolů, včetně těch, které používá webová služba.  Migrace webových služeb ASP.NET do WCF umožňuje vašim aplikacím využívat nové funkce a vylepšení, které jsou jedinečné pro službu WCF.  
  
 Služba WCF má vzhledem k ASP.NET webovým službám několik důležitých výhod. I když jsou nástroje webové služby ASP.NET výhradně pro vytváření webových služeb, služba WCF poskytuje nástroje, které lze použít, pokud je třeba, aby mohly komunikovat s jinými softwarovými entitami. Tím se sníží počet technologií, které vývojáři potřebuje k tomu, aby pokryly různé scénáře komunikace softwaru. tím se sníží náklady na prostředky vývoje softwaru a také čas potřebný k dokončení projektů vývoje softwaru.  
  
 I v případě projektů vývoje webové služby podporuje WCF více protokolů webové služby než podpora webových služeb ASP.NET. Tyto další protokoly poskytují složitější řešení zahrnující mimo jiné i spolehlivé relace a transakce.  
  
 Služba WCF podporuje další protokoly pro přenos zpráv, než ASP.NET webové služby. Webové služby ASP.NET podporují posílání zpráv jenom pomocí protokolu HTTP (Hypertext Transfer Protocol). Služba WCF podporuje odesílání zpráv pomocí protokolu HTTP a také protokolu TCP (Transmission Control Protocol), pojmenovaných kanálů a služby Microsoft řízení front zpráv (MSMQ). Důležitější je, že WCF se dá rozšířit na podporu dalších přenosových protokolů. Software vyvinutý pomocí WCF se proto dá přizpůsobit tak, aby spolupracoval s širší škálou jiného softwaru, což zvyšuje potenciální návratnost investic.  
  
 Služba WCF nabízí mnohem rozsáhlejší možnosti pro nasazování a správu aplikací než ASP.NET webové služby. Kromě konfiguračního systému, který ASP.NET má také, WCF nabízí Editor konfigurací, trasování aktivity od odesílatelů a zpětně prostřednictvím libovolného počtu zprostředkovatelů, prohlížeče trasování, protokolování zpráv, rozsáhlého počtu čítačů výkonu a podporu rozhraní WMI (Windows Management Instrumentation).  
  
 Vzhledem k tomu, že tyto potenciální výhody WCF souvisí s ASP.NET webovými službami, pokud používáte nebo zvažujete použití webových služeb ASP.NET, máte několik možností:  
  
- Můžete dál používat webové služby ASP.NET a forego výhody proffered službou WCF.  
  
- Používejte webové služby ASP.NET s úmyslem přijmout WCF v určitou dobu v budoucnu. Témata v této části vysvětlují, jak maximalizovat potenciální zákazníky, aby mohli používat nové aplikace webové služby ASP.NET spolu s budoucími aplikacemi WCF. Témata v této části také vysvětlují, jak vytvořit nové webové služby ASP.NET, aby je bylo snazší migrovat do WCF. Pokud je však důležité zabezpečení služeb, nebo jsou vyžadovány spolehlivost či transakce, nebo pokud bude nutné vytvořit vlastní zařízení správy, je lepší volbou WCF přijmout. WCF je navržené pro tyto scénáře přesně.  
  
- Přijímají WCF pro nový vývoj a přitom nadále udržuje stávající aplikace webové služby ASP.NET. Tato volba je velmi pravděpodobně optimální. Přináší výhody služby WCF, a přitom převede náklady na změnu stávajících aplikací, které ji používají. V tomto scénáři můžou nové aplikace WCF existovat společně s existujícími ASP.NET aplikacemi. Nové aplikace WCF budou moci používat stávající webové služby ASP.NET a WCF lze použít k naprogramování nových provozních funkcí do stávajících aplikací ASP.NET, a to na základě režimu kompatibility WCF ASP.NET.  
  
- Přijme WCF a migruje stávající aplikace webové služby ASP.NET do WCF. Tuto možnost můžete zvolit, chcete-li vylepšit existující aplikace pomocí funkcí poskytovaných službou WCF nebo reprodukování funkcí stávajících webových služeb ASP.NET v rámci nových, výkonnějších aplikací WCF.  
  
> [!NOTE]
> Pokud je služba WCF hostována službou IIS 5. x a ASP.NET je odinstalována, je nutné provést péči. Pokud je služba WCF hostována službou IIS 5. x, může být kód pro službu požadován, pokud je ASP.NET odinstalována. Když se ASP.NET odinstaluje v operačním systému, na kterém běží IIS 5. x a služba WCF se odinstaluje, považuje se soubor s příponou. svc za textový soubor a obsah, včetně jakéhokoliv zdrojového kódu, se vrátí žadateli.  
  
 Tato část podrobně popisuje tyto možnosti, porovnává webové služby v ASP.NET s WCF a poskytuje pokyny k migraci kódu služby ASP.NET Web Services do WCF.  
  
## <a name="see-also"></a>Viz také

- [Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí migrace](anticipating-adopting-wcf-migration.md)
- [Očekávání přechodu na Windows Communication Foundation: Usnadnění budoucí integrace](anticipating-adopting-the-wcf-easing-future-integration.md)
- [Přijetí Windows Communication Foundation](adopting-wcf.md)
- [Porovnání webových služeb ASP.NET se službou WCF na základě účelu a používaných standardů](comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
- [Porovnání webových služeb ASP.NET s technologií WCF z hlediska vývojových požadavků](comparing-aspnet-web-services-to-wcf-based-on-development.md)

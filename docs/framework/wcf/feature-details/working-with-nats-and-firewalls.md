---
title: Práce s překlady adres (NAT) a bránami firewall
ms.date: 03/30/2017
helpviewer_keywords:
- firewalls [WCF]
- NATs [WCF]
ms.assetid: 74db0632-1bf0-428b-89c8-bd53b64332e7
ms.openlocfilehash: b8be10740c8e92d3dac7094f07b3372e8d78a3d9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743869"
---
# <a name="working-with-nats-and-firewalls"></a>Práce s překlady adres (NAT) a bránami firewall
Klient a server síťového připojení často nemají přímou a otevřenou cestu pro komunikaci. Pakety se filtrují, směrují, analyzují a transformují na počítačích koncových bodů a na zprostředkujících počítačích v síti. Překlad síťových adres (NAT) a bran firewall jsou běžné příklady mezilehlých aplikací, které se můžou účastnit síťové komunikace.  
  
 Přenosy Windows Communication Foundation (WCF) a vzory výměny zpráv (MEPs) reagují odlišně na přítomnost zařízení NAT a bran firewall. Toto téma popisuje, jak funkce NAT a brány firewall fungují v běžných topologiích sítě. Doporučení pro konkrétní kombinace přenosů WCF a MEPs jsou pokaždé, když se aplikace lépe šíří na zařízení NAT a brány firewall v síti.  
  
## <a name="how-nats-affect-communication"></a>Jak NAT ovlivňují komunikaci  
 Služba NAT byla vytvořena za účelem umožnění sdílení jedné externí IP adresy několika počítači. Překlad adres (NAT) přemapování portů mapuje interní IP adresu a port pro připojení k externí IP adrese s novým číslem portu. Nové číslo portu umožňuje, aby překlad adres (NAT) koreluje návratový provoz s původní komunikací. Spousta domácích uživatelů teď má IP adresu, která se dá soukromě směrovat a spoléhat na překlad adres (NAT), aby poskytovala globální směrování paketů.  
  
 Překlad adres (NAT) neposkytuje hranici zabezpečení. Běžné konfigurace NAT ale zabraňují přímému adresování vnitřních počítačů. Obě tyto operace chrání interní počítače před některými nežádoucími připojeními a ztěžuje tak psaní serverových aplikací, které musí asynchronně odesílat data zpátky klientovi. Překlad adres (NAT) přepíše adresy v paketech, aby vypadal jako připojení pocházející z počítače NAT. Tím dojde k selhání serveru při pokusu o otevření připojení zpět ke klientovi. Pokud server používá vnímanou adresu klienta, neproběhne úspěšně, protože adresu klienta nelze veřejně směrovat. Pokud server používá adresu NAT, připojení se nepovede, protože na tomto počítači nenaslouchá žádná aplikace.  
  
 Některá zařízení NAT podporují konfiguraci pravidel předávání a umožňují tak externím počítačům připojit se k určitému internímu počítači. Pokyny pro konfiguraci pravidel předávání se liší v různých protokolech NAT a vyžadují, aby koncoví uživatelé změnili konfiguraci překladu adres (NAT) pro většinu aplikací. Mnoho koncových uživatelů buď nemůže, nebo nechce měnit konfiguraci překladu adres (NAT) pro konkrétní aplikaci.  
  
## <a name="how-firewalls-affect-communication"></a>Vliv bran firewall na komunikaci  
 *Brána firewall* je softwarové nebo hardwarové zařízení, které používá pravidla pro provoz procházející při rozhodování o tom, jestli se má povolit nebo odepřít pasáž. Můžete nakonfigurovat brány firewall pro kontrolu příchozích a/nebo odchozích datových proudů provozu. Brána firewall poskytuje hranici zabezpečení sítě na hraniční síti nebo hostiteli koncového bodu. Obchodní uživatelé tradičně udržují své servery za bránou firewall, aby nedocházelo k škodlivým útokům. Vzhledem k tomu, že zavedení osobní brány firewall v [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]se významně zvýšilo i počet domácích uživatelů za bránou firewall. To je pravděpodobně tím, že jeden nebo oba konce připojení mají bránu firewall prověřování paketů.  
  
 Brány firewall se výrazně liší v souvislosti s jejich složitostí a schopností při prověřování paketů. Jednoduché brány firewall používají pravidla založená na zdrojových a cílových adresách a portech v paketech. Inteligentní brány firewall také prozkoumají obsah paketů, aby bylo možné provést rozhodnutí. Tyto brány firewall přicházejí v mnoha různých konfiguracích a často se používají pro specializované aplikace.  
  
 Běžnou konfigurací pro bránu firewall pro domácí uživatele je zakázat příchozí připojení, pokud se předtím nevytvořilo odchozí připojení k tomuto počítači. Běžnou konfigurací brány firewall pro firmy uživatele je zakázat příchozí připojení na všech portech, s výjimkou výslovně identifikované skupiny. Příkladem je brána firewall, která zakazuje připojení na všech portech s výjimkou portů 80 a 443 pro poskytování služby HTTP a HTTPS. Spravované brány firewall existují pro domácí i firemní uživatele, kteří můžou na počítači povolit důvěryhodného uživatele nebo procesy, aby změnili konfiguraci brány firewall. Spravované brány firewall jsou běžnější pro domácí uživatele, u kterých neexistuje podniková zásada řízení využití sítě.  
  
## <a name="using-teredo"></a>Pomocí Teredo  

 Teredo je přechodová technologie IPv6, která umožňuje přímou adresovatelnost počítačů za překladem adres (NAT). Teredo spoléhá na použití serveru, který může být veřejně a globálně směrován pro inzerování potenciálních připojení. Server Teredo uděluje klientovi aplikace a serveru společný bod schůzky, na kterém mohou informace o připojení systému Exchange. Počítače pak vyžádají dočasnou adresu Teredo a pakety se procházejí tunelem přes stávající síť. Podpora Teredo v rámci WCF vyžaduje povolení podpory IPv6 a Teredo v operačním systému. [!INCLUDE[wxp](../../../../includes/wxp-md.md)] a novější operační systémy podporují technologii Teredo. Systém Windows Vista a novější operační systémy podporují protokol IPv6 ve výchozím nastavení a vyžadují, aby uživatel povolil technologii Teredo. [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] a Windows Server 2003 vyžadují, aby uživatel povolil protokol IPv6 i Teredo. Další informace najdete v tématu [Přehled technologie Teredo](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-xp/bb457011(v%3dtechnet.10)).  
  
## <a name="choosing-a-transport-and-message-exchange-pattern"></a>Výběr modelu přenosu a výměny zpráv  
 Výběr přenosu a MEP je proces se třemi kroky:  
  
1. Analyzujte adresovatelnost počítačů koncového bodu. Podnikové servery obvykle mají přímou adresovatelnost, zatímco koncoví uživatelé mají většinou své adresy blokované pomocí zařízení NAT. Pokud jsou oba koncové body za překladem adres (NAT), například ve scénářích peer-to-peer mezi koncovými uživateli, budete možná potřebovat technologii, jako je Teredo, aby se zajistila adresovatelnost.  
  
2. Proveďte analýzu protokolů a omezení portů počítačů koncového bodu. Podnikové servery jsou obvykle za silnými branami firewall, které blokují mnoho portů. Port 80 se ale často otevírá pro povolení přenosu HTTP a je otevřený port 443 pro povolení přenosu HTTPS. Koncovým uživatelům je méně pravděpodobné, že mají omezení portů, ale mohou být za bránou firewall, která povoluje pouze odchozí připojení. Některé brány firewall umožňují správu aplikací na koncovém bodu pro selektivní otevřená připojení.  
  
3. Vypočítá přenosy a MEPs, které omezení adresování a portů povoluje sítě.  
  
 Běžnou topologií pro aplikace typu klient-server je to, aby klienti, kteří jsou za překladem adres (NAT) bez Teredo, měli jenom odchozí bránu firewall a server, který je přímo adresovatelný pomocí silné brány firewall. V tomto scénáři přenos TCP s MEP a přenosem HTTP s MEP funguje dobře. Běžnou topologií pro aplikace peer-to-peer je mít oba koncové body za NAT a brány firewall. V tomto scénáři a ve scénářích, kde je síťová topologie neznámá, zvažte následující doporučení:  
  
- Nepoužívejte duální přenosy. Dvojí přenos otevírá více připojení, což snižuje pravděpodobnost úspěšného připojení.  
  
- Podpora vytváření zpětných kanálů přes původní připojení. Pomocí back-Channel, například v duplexní TCP, se otevírá méně připojení, což zvyšuje pravděpodobnost úspěšného připojení.  
  
- Využívejte dostupnou službu pro registraci koncových bodů nebo přenosů dat. Použití globálně dosažitelné služby připojení, jako je třeba server Teredo, významně zvyšuje pravděpodobnost úspěšného připojení, když je síťová topologie omezující nebo neznámá.  
  
 Následující tabulky prozkoumají jednosměrná, požadavek-odpověď a duplexní MEPs a standardní TCP, TCP s Teredo a standardní a duální přenosy HTTP ve službě WCF.  
  
|Adresovatelnosti|Server Direct|Server Direct s procházením NAT|Překlad adres serveru|NAT serveru pomocí průchodu NAT|  
|--------------------|-------------------|--------------------------------------|----------------|-----------------------------------|  
|Klient Direct|Jakýkoli přenos a MEP|Jakýkoli přenos a MEP|Není podporováno.|Není podporováno.|  
|Klient Direct s procházením NAT|Jakýkoli přenos a MEP.|Jakýkoli přenos a MEP.|Není podporováno.|TCP s Teredo a jakýmkoli MEP. Systém Windows Vista nabízí možnost konfigurace pro podporu protokolu HTTP s technologií Teredo na úrovni počítače.|  
|NAT klienta|Jakýkoli neduální přenos a MEP. Duplexní MEP vyžaduje přenos TCP.|Jakýkoli neduální přenos a MEP. Duplexní MEP vyžaduje přenos TCP.|Není podporováno.|Není podporováno.|  
|NAT klienta s procházením NAT|Jakýkoli neduální přenos a MEP. Duplexní MEP vyžaduje přenos TCP.|Všechny s výjimkou duálních HTTP a všech MEP. Duplexní MEP vyžaduje přenos TCP. Duální přenos TCP vyžaduje Teredo. Systém Windows Vista nabízí možnost konfigurace pro podporu protokolu HTTP s technologií Teredo na úrovni počítače.|Není podporováno.|TCP s Teredo a jakýmkoli MEP. Systém Windows Vista nabízí možnost konfigurace pro podporu protokolu HTTP s technologií Teredo na úrovni počítače.|  
  
|Omezení brány firewall|Otevřený Server|Server se spravovanou bránou firewall|Server s bránou firewall pouze s protokolem HTTP|Server s bránou firewall jenom pro odchozí připojení|  
|---------------------------|-----------------|----------------------------------|-------------------------------------|-----------------------------------------|  
|Otevřeného klienta|Jakýkoli přenos a MEP.|Jakýkoli přenos a MEP.|Jakýkoli přenos HTTP a MEP.|Není podporováno.|  
|Klient se spravovanou bránou firewall|Jakýkoli neduální přenos a MEP. Duplexní MEP vyžaduje přenos TCP.|Jakýkoli neduální přenos a MEP. Duplexní MEP vyžaduje přenos TCP.|Jakýkoli přenos HTTP a MEP.|Není podporováno.|  
|Klient s bránou firewall jenom HTTP|Jakýkoli přenos HTTP a MEP.|Jakýkoli přenos HTTP a MEP.|Jakýkoli přenos HTTP a MEP.|Není podporováno.|  
|Klient s bránou firewall jenom pro odchozí připojení|Jakýkoli neduální přenos a MEP. Duplexní MEP vyžaduje přenos TCP.|Jakýkoli neduální přenos a MEP. Duplexní MEP vyžaduje přenos TCP.|Jakýkoli přenos HTTP a jakékoli neduplexní MEP.|Není podporováno.|

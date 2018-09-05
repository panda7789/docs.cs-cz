---
title: Práce s překlady adres (NAT) a bránami firewall
ms.date: 03/30/2017
helpviewer_keywords:
- firewalls [WCF]
- NATs [WCF]
ms.assetid: 74db0632-1bf0-428b-89c8-bd53b64332e7
ms.openlocfilehash: 9cecca0905baa4c0769359caf1fe1b477bf4d6bd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518922"
---
# <a name="working-with-nats-and-firewalls"></a>Práce s překlady adres (NAT) a bránami firewall
Klient a server připojení k síti často nemají přímý a otevřít cestu pro komunikaci. Pakety jsou filtrované, směrovat, analyzovat a transformovat na počítačích koncový bod a zprostředkující počítače v síti. Síť překlady adres (NAT) a brány firewall jsou běžné příklady zprostředkující aplikace, které se mohou účastnit síťové komunikace.  
  
 Windows Communication Foundation (WCF) přenosů a zpráv exchange vzory (MEPs) react jinak na přítomnost NAT a brány firewall. Toto téma popisuje, jak zařízení NAT a brány firewall fungovat v běžných síťové topologie. Doporučení pro konkrétní kombinace přenosy WCF a MEPs, která jsou uvedena měli robustnější vašich aplikací do zařízení NAT a brány firewall v síti.  
  
## <a name="how-nats-affect-communication"></a>Vliv komunikace zařízení NAT.  
 NAT byl vytvořen pro povolení několika počítačů sdílet jednu externí IP adresu. NAT přemapování portu mapuje interní IP adresa a port pro připojení na externí IP adresu se nové číslo portu. Nové číslo portu umožňuje NAT pro korelaci zpětný provoz s původní komunikace. Mnoho domácí uživatelé teď mají IP adresu, která je jenom soukromě směrovatelné a využívají NAT poskytnout globální směrování paketů.  
  
 NAT neposkytuje hranice zabezpečení. Však obvyklé konfigurace překladu adres zabránit interní počítače přímo se zákazníky a vyřešené. To současně chrání interní počítače z některých nežádoucí připojení a zpřístupňuje je obtížné je napsat serverových aplikací, které musí asynchronně posílat data zpět do klienta. Překlad síťových adres přepíše adresy v paketech, aby se zdá, že připojení jsou pocházející z počítače NAT. To způsobí, že server selhání při pokusu o otevření připojení zpět do klienta. Pokud server používá adresu vnímaná klienta, nezdaří se, protože adresa klienta nelze směrovat veřejně. Pokud server používá adresu NAT, není schopna připojit, protože na tomto počítači nenaslouchá žádná aplikace.  
  
 Některá zařízení NAT podporují konfiguraci pravidla, aby měly externí počítače k připojení k počítači s konkrétní vnitřní předávání. Pokyny ke konfiguraci pravidla pro předávání se liší podle různých zařízení NAT a s dotazem, koncovým uživatelům změnit jejich NAT konfigurace se nedoporučuje pro většinu aplikací. Mnoho koncových uživatelů nemůžete nebo nechcete změnit jejich konfigurace překladu adres pro konkrétní aplikaci.  
  
## <a name="how-firewalls-affect-communication"></a>Vliv komunikaci brány firewall  
 A *brány firewall* je softwarová nebo hardwarová zařízení, které platí pravidla pro provoz procházející rozhodnout, jestli se má povolit nebo odepřít průchod. Můžete nakonfigurovat bránu firewall, aby prozkoumat příchozích a/nebo odchozích toků provozu. Brána firewall poskytuje hranice zabezpečení sítě na buď hranici sítě nebo na hostiteli koncový bod. Podnikoví uživatelé mají tradičně udržovat své servery za bránou firewall, aby se zabránilo útoky se zlými úmysly. Od uvedení osobní bránu firewall v [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)], počet domácí uživatelé za bránou firewall má výrazně se zvýšil také. To je pravděpodobné, že jedna nebo obou koncích připojení máte bránu firewall, kontrola paketů.  
  
 Brány firewall liší z hlediska jejich složitost a možnosti pro zkoumání paketů. Brány firewall jednoduché použití pravidel na základě zdrojových a cílových adres a portů v paketech. Inteligentní brány firewall můžete také zkontrolovat obsah pakety rozhodnutí. Těmito bránami firewall se dělí na mnoha různých konfigurací a často se používají pro speciální aplikace.  
  
 Běžnou konfigurací brány firewall domácí uživatel je zakázat příchozí připojení, pokud bylo navázáno odchozí připojení k tomuto počítači dříve. Běžnou konfigurací brány firewall obchodní uživatele je zakázat příchozí připojení na všech portech kromě skupiny určeno. Příkladem je brána firewall, která zakazuje připojení na všech portech kromě porty 80 a 443 pro poskytování služeb HTTP a HTTPS. Existují spravované brány firewall pro domácí a obchodní uživatele, které umožňují důvěryhodné uživatel nebo proces na počítači, chcete-li změnit konfiguraci brány firewall. Spravované brány firewall, jsou mnohem běžnější pro domácí uživatele tam, kde není žádná podnikové zásady řízení využití sítě.  
  
## <a name="using-teredo"></a>Použití Teredo  
 Teredo je přechodovou technologií IPv6, který umožňuje přímé adresovatelnosti počítačů za zařízením NAT. Teredo spoléhá na použití serveru, který je veřejně a globálně směrovat do inzerovat potenciální připojení. Teredo server poskytuje aplikace klientem a serverem společný bod schůzky výměně informací o připojení. Na počítačích, vyžádejte dočasné adresy Teredo a pakety jsou tunelovým propojením přes existující síť. Podpora Teredo ve službě WCF vyžaduje povolení podpory IPv6 a Teredo v operačním systému. [!INCLUDE[wxp](../../../../includes/wxp-md.md)] a novější operační systémy podporují Teredo. [!INCLUDE[wv](../../../../includes/wv-md.md)] a novější operační systémy podporovat protokol IPv6 ve výchozím nastavení pouze vyžaduje, aby uživatel chcete technologii Teredo povolit. [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] bude uživatel muset povolit protokol IPv6 a Teredo. Další informace najdete v tématu [Teredo přehled](https://go.microsoft.com/fwlink/?LinkId=87571).  
  
## <a name="choosing-a-transport-and-message-exchange-pattern"></a>Výběr vzoru výměny zpráv a přenosu  
 Výběr přenosu a MEP je třech krocích:  
  
1.  Analýza adresovatelnosti počítače koncový bod. Enterprise serverů často mají přímé adresovatelnosti koncoví uživatelé běžně mají jejich adresovatelnosti blokovaná zařízení NAT. Pokud jsou oba koncové body za službou NAT, například ve scénářích peer-to-peer mezi koncovým uživatelům, musíte technologie, jako je poskytnout adresovatelnosti Teredo.  
  
2.  Analyzujte protokol a port omezení počítače koncový bod. Enterprise serverů jsou obvykle firewall silné tento blok mnoho portů. Ale port 80 je často otevřete tak, aby povolovala přenosy pomocí protokolu HTTP a port 443 je otevřený tak, aby povolovala přenosy HTTPS. Koncoví uživatelé jsou méně pravděpodobné, že mají omezení portu, ale mohou být za bránou firewall, která povoluje jenom odchozí připojení. Některé brány firewall povolit správu pomocí aplikace pro koncový bod a selektivně otevřené připojení.  
  
3.  Výpočetní přenosy a MEPs, které umožňují omezení adresovatelnosti a portu sítě.  
  
 Běžné topologie pro aplikace typu klient server je, aby klienti, kteří jsou za službou NAT bez Teredo se jako pouze odchozí brána firewall a server, který je přímo adresovatelnými silné firewall. V tomto scénáři, přenosu protokolu TCP s duplexní MEP a přenos pomocí protokolu HTTP s požadavek odpověď MEP fungovat dobře. Běžné topologie peer-to-peer aplikací se oba koncové body za zařízeními NAT nebo branami firewall. V tomto scénáři a ve scénářích, kde Neznámý topologii sítě zvažte tato doporučení:  
  
-   Nepoužívejte duální přenosy. Duální přenosu Otevře další připojení, což snižuje riziko připojení úspěšně.  
  
-   Podporu o kanály zpět prostřednictvím původní připojení. Používání back kanálů, jako v duplexním TCP, otevře se méně připojení, což zvyšuje šance připojení úspěšně.  
  
-   Dostupné služby pro registraci koncových bodů nebo předávání provoz využívejte. Pomocí globálně dostupné připojení služby, jako je například Teredo server, se značně zvyšuje šance úspěšně připojit v případě topologie sítě je omezující nebo neznámý.  
  
 Zkontrolujte následující tabulky jednosměrný požadavek odpověď a duplexní MEPs a standardní TCP TCP s Teredo, a přenáší standardní a duální HTTP ve službě WCF.  
  
|Adresovatelnost|Server přímo|Server s přímým přístupem pomocí přecházení NAT|Server překladu adres|Server překladu adres pomocí přecházení NAT|  
|--------------------|-------------------|--------------------------------------|----------------|-----------------------------------|  
|Klient s přímým přístupem|Všechny přenosu a MEP|Všechny přenosu a MEP|Není podporováno.|Není podporováno.|  
|Klient s přímým přístupem pomocí přecházení NAT|Přenos a MEP.|Přenos a MEP.|Není podporováno.|TCP s Teredo a jakékoli MEP. [!INCLUDE[wv](../../../../includes/wv-md.md)] nabízí možnost konfiguraci celého počítače pro podporu protokolu HTTP s Teredo.|  
|Klient NAT|Bez možností přenosu a MEP. Duplexní MEP vyžaduje přenos pomocí protokolu TCP.|Bez možností přenosu a MEP. Duplexní MEP vyžaduje přenos pomocí protokolu TCP.|Není podporováno.|Není podporováno.|  
|Klient NAT s přecházení NAT|Bez možností přenosu a MEP. Duplexní MEP vyžaduje přenos pomocí protokolu TCP.|Vše kromě duální HTTP a žádné MEP. Duplexní MEP vyžaduje přenos pomocí protokolu TCP. Duální přenosu protokolu TCP vyžaduje Teredo. [!INCLUDE[wv](../../../../includes/wv-md.md)] nabízí možnost konfiguraci celého počítače pro podporu protokolu HTTP s Teredo.|Není podporováno.|TCP s Teredo a jakékoli MEP. [!INCLUDE[wv](../../../../includes/wv-md.md)] nabízí možnost konfiguraci celého počítače pro podporu protokolu HTTP s Teredo.|  
  
|Omezení brány firewall|Otevřete server|Server brány firewall na spravovaných|Server s bránou firewall jen HTTP|Server s pouze odchozí brány firewall|  
|---------------------------|-----------------|----------------------------------|-------------------------------------|-----------------------------------------|  
|Otevřít klienta|Přenos a MEP.|Přenos a MEP.|Přenos pomocí protokolu HTTP a MEP.|Není podporováno.|  
|Klient s spravované brány firewall|Bez možností přenosu a MEP. Duplexní MEP vyžaduje přenos pomocí protokolu TCP.|Bez možností přenosu a MEP. Duplexní MEP vyžaduje přenos pomocí protokolu TCP.|Přenos pomocí protokolu HTTP a MEP.|Není podporováno.|  
|Klient s jen HTTP brány firewall|Přenos pomocí protokolu HTTP a MEP.|Přenos pomocí protokolu HTTP a MEP.|Přenos pomocí protokolu HTTP a MEP.|Není podporováno.|  
|Klient s pouze odchozí brány firewall|Bez možností přenosu a MEP. Duplexní MEP vyžaduje přenos pomocí protokolu TCP.|Bez možností přenosu a MEP. Duplexní MEP vyžaduje přenos pomocí protokolu TCP.|Žádné přenos pomocí protokolu HTTP a žádné neduplexní MEP.|Není podporováno.|

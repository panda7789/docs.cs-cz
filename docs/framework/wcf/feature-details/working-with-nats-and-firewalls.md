---
title: "Práce s překlady adres (NAT) a bránami firewall"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- firewalls [WCF]
- NATs [WCF]
ms.assetid: 74db0632-1bf0-428b-89c8-bd53b64332e7
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a8fd5058179d9e7974e725d69bb2bf0740ab7f00
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="working-with-nats-and-firewalls"></a>Práce s překlady adres (NAT) a bránami firewall
Klient a server připojení k síti často nemají přímou a otevřete cestu pro komunikaci. Pakety jsou filtrovány, směrovat, analyzovat a transformovat na počítačích, koncový bod a zprostředkující počítače v síti. Sítě překlady adres (NAT) a brány firewall jsou běžných příkladů zprostředkující aplikací, které se můžou zapojit síťové komunikace.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]přenosy a zpráva, že exchange vzory (MEPs) reagovat jinak na přítomnost zařízení NAT a brány firewall. Toto téma popisuje, jak zařízení NAT a brány firewall funkce společné síťové topologie. Doporučení pro konkrétní kombinace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přenosy MEPs jsou zadané a který pomoci zajistit robustnější aplikace na zařízení NAT a brány firewall v síti.  
  
## <a name="how-nats-affect-communication"></a>Vliv komunikace zařízení NAT.  
 NAT byl vytvořen, aby několik počítačů sdílet jednu externí IP adresu. NAT se port přemapování mapuje interní IP adresu a port pro připojení na externí IP adresu s nové číslo portu. Nové číslo portu umožňuje NAT ke korelaci návratový provoz s původní komunikace. Mnoho domácí uživatelé teď mají IP adresu, která je jenom soukromě směrovatelné a spoléhají na NAT zajistit globální směrování paketů.  
  
 Zařízení NAT neposkytuje hranice zabezpečení. Ale obvyklé konfigurace NAT zabránit interní počítače přímo adresovaném. To chrání interní počítače z některé nežádoucí připojení i ztěžuje zápis serverových aplikací, které musíte asynchronně odesílat data zpět do klienta. Překlad síťových adres přepíše adresy v paketech, aby bylo působí jako jsou v počítači NAT pocházející připojení. To způsobí, že server dojde k chybě při jeho pokusu o otevření připojení zpět do klienta. Pokud server používá dosahovaný adresa klienta, se nezdaří, protože adresu klienta nelze směrovat veřejně. Pokud server používá adresu NAT, se nepodaří připojit, protože žádná aplikace naslouchá na tomto počítači.  
  
 Některé zařízení NAT podporují konfiguraci předávání pravidla povolit externí počítače pro připojení k interní konkrétní počítač. Pokyny ke konfiguraci pravidla pro předávání se liší podle různých zařízení NAT a s dotazem, koncovým uživatelům změnit jejich NAT konfigurace se nedoporučuje pro většinu aplikací. Mnoho koncoví uživatelé nemůžete nebo nechcete změnit jejich konfiguraci NAT pro konkrétní aplikace.  
  
## <a name="how-firewalls-affect-communication"></a>Vliv komunikace brány firewall  
 A *brány firewall* je softwarová nebo hardwarová zařízení, které platí pravidla pro provoz procházející můžete rozhodnout, jestli chcete povolit nebo odepřít průchod. Můžete nakonfigurovat bránu firewall, aby zkontrolujte datové proudy příchozích nebo odchozích přenosů. Brána firewall poskytuje hranice zabezpečení sítě na obou hranici sítě nebo na hostiteli koncový bod. Podnikoví uživatelé mají tradičně uchovávají své servery za bránou firewall, aby se zabránilo útoky se zlými úmysly. Od uvedení osobní bránu firewall v [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)], výrazně zlepšila také počet domácí uživatele za bránou firewall. To je pravděpodobné, že jedna nebo obou konců připojení mít bránu firewall zkoumání paketů.  
  
 Brány firewall se výrazně liší z hlediska jejich složitost a možnost kontroly paketů. Jednoduché brány firewall použít pravidla na základě zdrojové a cílové adresy a porty v paketech. Inteligentní brány firewall můžete také zkontrolovat obsah paketů při rozhodování. Tyto brány firewall mají mnoho různých konfigurací a se často používají pro speciální aplikace.  
  
 Obvyklé konfigurace brány firewall domácí uživatel je zakázat příchozí připojení, pokud byl proveden odchozí připojení k tomuto počítači dříve. Obvyklé konfigurace brány firewall obchodní uživatele je zakázat příchozí připojení na všech portech kromě skupinu konkrétně identifikovat. Příkladem je bránu firewall, která znemožňuje připojení na všech portech s výjimkou porty 80 a 443 o poskytování služeb HTTP a HTTPS. Spravované brány firewall pro domácí i obchodní uživatele, které umožňují důvěryhodné uživatel nebo proces na počítači, chcete-li změnit konfiguraci brány firewall neexistují. Spravované brány firewall jsou častější pro domácí uživatele tam, kde nejsou žádné podnikové zásady řízení využití sítě.  
  
## <a name="using-teredo"></a>Použití Teredo  
 Teredo je přechodové technologie IPv6, která umožňuje přímé adresovatelnosti počítačů za adres (NAT) Teredo spoléhá na použití serveru, které se dají veřejně a globálně směrovat inzerovat potenciální připojení. Teredo server aplikace klient a server poskytuje společný bod schůzku výměně informací o připojení. Na počítačích pak požádat o dočasnou adresu Teredo a pakety se tunneled přes existující síť. Podpora Teredo v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vyžaduje povolení podpory protokolu IPv6 a Teredo v operačním systému. [!INCLUDE[wxp](../../../../includes/wxp-md.md)]a novější operační systémy podporují Teredo. [!INCLUDE[wv](../../../../includes/wv-md.md)]a novější operační systémy podporovat protokol IPv6 ve výchozím nastavení a vyžadují jenom uživateli aktivaci Teredo. [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] vyžadovat, aby uživatel povolit protokol IPv6 a Teredo. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Teredo přehled](http://go.microsoft.com/fwlink/?LinkId=87571).  
  
## <a name="choosing-a-transport-and-message-exchange-pattern"></a>Výběr vzorce výměny zpráv a přenosu  
 Výběr přenosu a MEP je proces třech krocích:  
  
1.  Analýza adresovatelnosti počítačů koncový bod. Když koncoví uživatelé běžně má jejich adresovatelnosti blokována zařízení NAT. mít servery Enterprise přímé adresovatelnosti běžně. Pokud oba koncové body jsou za zařízení NAT, jako třeba ve scénářích peer-to-peer mezi koncovým uživatelům, musíte technologie, jako je například Teredo zajistit adresovatelnosti.  
  
2.  Analýza protokol a port pro omezení počítačů koncový bod. Podnikové servery jsou obvykle za silné brány firewall tomto bloku mnoho porty. Ale port 80 je často otevřený pro povolení komunikace HTTP a port 443 je otevřete tak, aby povolovala přenosy HTTPS. Koncoví uživatelé jsou méně pravděpodobné, že mají omezení portu, ale mohou být za bránou firewall, která umožňuje pouze odchozí připojení. Některé brány firewall povolit správu aplikací v koncovém bodě selektivně otevřít připojení.  
  
3.  Výpočetní přenosy a MEPs, které umožňují omezení adresovatelnosti a portů sítě.  
  
 Běžné topologie pro aplikace, klient server je do mají klienti, kteří jsou za serverem NAT bez Teredo se jako pouze odchozí brána firewall a server, který je přímo adresovatelné s silné brány firewall. V tomto scénáři, přenos TCP s duplexní MEP a přenosového protokolu HTTP s požadavek odpověď MEP fungovat správně. Běžné topologie pro aplikace peer-to-peer je mít oba koncové body za zařízení NAT a brány firewall. V tomto scénáři a ve scénářích, kde Neznámý síťové topologie zvažte následující doporučení:  
  
-   Nepoužívejte duální přenosy. Duální přenosu Otevře další připojení, což snižuje riziko připojení úspěšně.  
  
-   Podporovat stanovením kanály zpět přes původní připojení. Použití kanálů zpět, například v duplexní TCP, otevře méně připojení, což zvyšuje šance připojení úspěšně.  
  
-   Použít dosažitelný služby pro registraci koncových bodů nebo předávání provoz. Pomocí globálně dostupné připojení služby, jako je například Teredo server, se značně zvyšuje šance připojující úspěšně po omezující nebo neznámé síťové topologie.  
  
 V následujících tabulkách zkontrolujte jednosměrné, požadavku a odpovědi a duplexní MEPs a standardní TCP, TCP s Teredo a standard a duální přenosy HTTP v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
|Adresovatelnosti|Přímý server|Server přímé s NAT traversal|Server NAT|Server NAT s NAT traversal|  
|--------------------|-------------------|--------------------------------------|----------------|-----------------------------------|  
|Přímé klienta|Všechny přenosu a MEP|Všechny přenosu a MEP|Není podporováno.|Není podporováno.|  
|Přímé s NAT traversal klienta|Přenos a MEP.|Přenos a MEP.|Není podporováno.|TCP s Teredo a všechny MEP. [!INCLUDE[wv](../../../../includes/wv-md.md)]má parametr konfigurace celého systému pro podporu protokolu HTTP s Teredo.|  
|Klient NAT|Bez duální přenosu a MEP. Duplexní MEP vyžaduje přenos TCP.|Bez duální přenosu a MEP. Duplexní MEP vyžaduje přenos TCP.|Není podporováno.|Není podporováno.|  
|Klient NAT s NAT traversal|Bez duální přenosu a MEP. Duplexní MEP vyžaduje přenos TCP.|Všechny ale duální HTTP a všechny MEP. Duplexní MEP vyžaduje přenos TCP. Duální přenos TCP vyžaduje Teredo. [!INCLUDE[wv](../../../../includes/wv-md.md)]má parametr konfigurace celého systému pro podporu protokolu HTTP s Teredo.|Není podporováno.|TCP s Teredo a všechny MEP. [!INCLUDE[wv](../../../../includes/wv-md.md)]má parametr konfigurace celého systému pro podporu protokolu HTTP s Teredo.|  
  
|Omezení brány firewall|Otevřete na serveru|Server s spravované brány firewall|Server s jen HTTP brány firewall|Server s odchozího brány firewall|  
|---------------------------|-----------------|----------------------------------|-------------------------------------|-----------------------------------------|  
|Otevřete klienta|Přenos a MEP.|Přenos a MEP.|Přenos HTTP a MEP.|Není podporováno.|  
|Klient s spravované brány firewall|Bez duální přenosu a MEP. Duplexní MEP vyžaduje přenos TCP.|Bez duální přenosu a MEP. Duplexní MEP vyžaduje přenos TCP.|Přenos HTTP a MEP.|Není podporováno.|  
|Klient s jen HTTP brány firewall|Přenos HTTP a MEP.|Přenos HTTP a MEP.|Přenos HTTP a MEP.|Není podporováno.|  
|Klient s odchozího brány firewall|Bez duální přenosu a MEP. Duplexní MEP vyžaduje přenos TCP.|Bez duální přenosu a MEP. Duplexní MEP vyžaduje přenos TCP.|Všechny přenos HTTP a všechny MEP duplexní režim.|Není podporováno.|

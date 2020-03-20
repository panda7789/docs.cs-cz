---
title: Řešení ReliableSecureProfile
ms.date: 03/30/2017
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
ms.openlocfilehash: 9ddd0d78396bba6712650620e6b46c62f13337e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144211"
---
# <a name="reliable-secure-profile"></a>Řešení ReliableSecureProfile

Tato ukázka ukazuje, jak sestavit WCF a [spolehlivý zabezpečený profil (RSP)](http://www.ws-i.org/Profiles/ReliableSecureProfile-1.0.html). Tato ukázka ukazuje implementaci kanálu [vytvořit připojení,](http://docs.oasis-open.org/ws-rx/wsmc/200702/wsmc-1.0-spec-cs-01.pdf) který může být složen spolu s spolehlivé zasílání zpráv a volitelně zabezpečený kanál pro vytvoření spolehlivé zabezpečené vazby založené na specifikaci RSP.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a>Diskuse  
 Tato ukázka ukazuje spolehlivé asynchronní obousměrné zprávy výměny scénář. Služba má duplexní smlouvy a klient implementuje duplexní kontrakt zpětného volání. Klient iniciuje požadavek na službu, pro kterou se očekává odpověď na samostatné připojení. Zpráva požadavku je odeslána spolehlivě. Klient nechce otevřít koncový bod naslouchání na jeho konci. Proto dotazuje službu s požadavky "Make Connection" pro službu odeslat zpět odpověď na zadní kanál této žádosti "Make Connection". Tato ukázka ukazuje, jak mít zabezpečené spolehlivé duplexní komunikace přes HTTP bez klienta vystavení naslouchání koncového bodu (a vytvoření výjimky brány firewall).  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Otevřete řešení **ReliableSecureProfile.**  
  
2. Klepněte pravým tlačítkem myši na projekt **služby** v **Průzkumníku řešení**, vyberte **možnost Ladění**, Spustit **novou instanci** z kontextové nabídky. To spustí hostitele služby.  
  
3. Klepněte pravým tlačítkem myši na projekt **klienta** v **Průzkumníku řešení**, vyberte **možnost Ladění**, Spustit **novou instanci** z kontextové nabídky. Tím se spustí klient.  
  
4. Do výzvy v okně klientské konzole zadejte libovolný řetězec a klepněte na tlačítko ENTER. To odešle vstupní řetězec do služby, která vypočítá hash tohoto řetězce.  
  
5. Zobrazit výsledek v oknech klienta při volání služby zpět operace smlouvy zpětného volání duplexní zobrazit výsledek v okně klientské konzole. Je úmyslné zpoždění ve službě simulovat dlouhotrvající operace zpracování dat.  
  
6. Sledování provozu HTTP (pomocí online nástrojů pro sledování sítě, jako je Sledování sítě, Šumař a tak dále) ukazuje, že mezi klientem a službou je vytvořena sekvence komunikace, jak je stanoveno spolehlivým zabezpečeným profilem, a jak klient dotazuje službu s požadavky 'Make Connection'. Když se služba chystá odeslat zpět zpracovu odpověď, použije zadní kanál poslední žádosti "Vytvořit připojení" k odeslání výsledků zpět.  
  
7. Chcete-li službu zavřít, stiskněte klávesu ENTER v okně servisní konzole. Stisknutím klávesy ENTER v okně klientské konzole zavřete klienta.

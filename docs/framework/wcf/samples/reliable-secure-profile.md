---
title: Řešení ReliableSecureProfile
ms.date: 03/30/2017
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
ms.openlocfilehash: d7cfc028c5cf1ba5cfba009cd29c89f07c64fd9c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044804"
---
# <a name="reliable-secure-profile"></a>Řešení ReliableSecureProfile
Tato ukázka předvádí, jak vytvořit WCF a [spolehlivý zabezpečený profil](https://go.microsoft.com/fwlink/?LinkId=178140) (RSP). Tato ukázka předvádí implementaci kanálu [připojení](https://go.microsoft.com/fwlink/?LinkId=178141) , který se může skládat společně s spolehlivým zasíláním zpráv, a volitelně také zabezpečený kanál pro vytvoření spolehlivé zabezpečené vazby na základě specifikace RSP.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a>Účely  
 Tato ukázka předvádí spolehlivý asynchronní scénář obousměrné výměny zpráv. Služba má duplexní smlouvu a klient implementuje kontrakt předuplexního zpětného volání. Klient inicializuje požadavek na službu, pro kterou je odpověď očekávána v samostatném připojení. Zpráva požadavku bude spolehlivě odeslána. Klient nechce na svém konci otevřít koncový bod naslouchání. Proto dotazuje službu pomocí žádostí o vytvoření připojení, aby mohla služba odeslat zpět odpověď na zadní kanál této žádosti o vytvoření připojení. Tato ukázka předvádí, jak zajistit zabezpečenou spolehlivou duplexovou komunikaci přes protokol HTTP bez toho, aby klient vystavoval koncový bod naslouchání (a vytvořil výjimku brány firewall).  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Otevřete řešení **ReliableSecureProfile** .  
  
2. Klikněte pravým tlačítkem na projekt **služby** v **Průzkumník řešení**, vyberte **ladit**, **spustit novou instanci** z kontextové nabídky. Tím se spustí hostitel služby.  
  
3. Klikněte pravým tlačítkem na projekt **klienta** v **Průzkumník řešení**, vyberte **ladit**, **začněte novou instanci** z kontextové nabídky. Tím spustíte klienta.  
  
4. Do příkazového řádku v okně konzoly klienta zadejte libovolný řetězec a klikněte na ENTER. Tím se vstupní řetězec pošle službě, která vypočítá hodnotu hash tohoto řetězce.  
  
5. Zobrazí výsledek v klientských oknech, když služba zavolá zpět operaci produplexního zpětného volání, aby zobrazila výsledek v okně konzoly klienta. Došlo k úmyslnému zpoždění služby, aby se simulovala dlouhodobá operace zpracování dat.  
  
6. Monitorování přenosů HTTP (pomocí kteréhokoli nástroje pro monitorování sítě online, jako je Sledování sítě, Fiddler a tak dále) ukazuje, že je mezi klientem a službou navázáná sekvence komunikace, jak je vydaná spolehlivým zabezpečeným profilem a jak klient nástroje Provede dotazování služby pomocí žádostí o připojení. Jakmile bude služba připravena odeslat zpět zpracovanou odpověď, použije back-Channel poslední žádosti o vytvoření připojení k odeslání výsledků.  
  
7. Pokud chcete službu zavřít, stiskněte klávesu ENTER v okně konzoly služby. Chcete-li ukončit klienta, stiskněte klávesu ENTER v okně konzoly klienta.

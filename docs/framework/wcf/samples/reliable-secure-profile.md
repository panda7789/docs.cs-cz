---
title: Řešení ReliableSecureProfile
ms.date: 03/30/2017
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
ms.openlocfilehash: e1895da0805a5282fc328b0c8d48d7042a1e5784
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767484"
---
# <a name="reliable-secure-profile"></a>Řešení ReliableSecureProfile
Tato ukázka předvádí, jak sestavit WCF a [spolehlivý zabezpečený profil](https://go.microsoft.com/fwlink/?LinkId=178140) (RSP). Tato ukázka předvádí, provádění [vytvořit připojení](https://go.microsoft.com/fwlink/?LinkId=178141) kanál, který se může skládat spolu s spolehlivé zasílání zpráv a volitelně zabezpečeného kanálu k vytvoření spolehlivé zabezpečené vazby na základě RSP specifikace.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a>Diskuse  
 Tato ukázka předvádí scénář spolehlivý asynchronní obousměrný zprávy exchange. Služba má duplexního kontraktu a klient implementuje tento kontrakt duplexního zpětného volání. Klient zahájí požadavek na službu, pro kterou se očekává odpověď na samostatné spojení. Zprávy s požadavkem je odeslána spolehlivě. Klient nechce otevřete koncový bod naslouchající na jeho konci. Díky tomu se dotazuje na službu s vytvořit připojení žádosti o službu má být zaslán zpět odpověď na používající back channel tohoto požadavku vytvořit připojení. Tato ukázka předvádí, jak vám má zabezpečené spolehlivou duplexní komunikaci přes protokol HTTP bez klienta vystavuje koncový bod naslouchající (a vytváření výjimku brány firewall).  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Otevřít **ReliableSecureProfile** řešení.  
  
2. Klikněte pravým tlačítkem myši **služby** projekt **Průzkumníka řešení**vyberte **ladění**, **zahájit novou instanci** v místní nabídce. Tím se spustí služby hostitele.  
  
3. Klikněte pravým tlačítkem myši **klienta** projekt **Průzkumníka řešení**vyberte **ladění**, **zahájit novou instanci** v místní nabídce. Tím se spustí klienta.  
  
4. Zadejte libovolný řetězec v příkazovém řádku v okně konzoly klienta a klikněte na ENTER. Tím se odešle vstupního řetězce ke službě, která vypočítá hodnotu hash tohoto řetězce.  
  
5. Zobrazte výsledek v systému windows klienta při volání služby zpět operace kontraktu duplexního zpětného volání pro zobrazení výsledků v okně konzoly klienta. Na službu pro simulaci dlouho běžící operace zpracování dat není k záměrné prodlevě.  
  
6. Monitorování přenos pomocí protokolu HTTP (podle těchto online sítě monitorování nástroje, jako je sledování sítě, Fiddler a tak dále) ukazuje, že pořadí pro komunikaci se naváže mezi klientem a službou za podmínek stanovených spolehlivý zabezpečený profil a jak klienta dotazuje službu s žádostmi o vytvořit připojení. Když služba dostane připravení odeslat zpět zpracovaných odpověď, používá používající back channel poslední žádosti vytvořit připojení má být zaslán zpět výsledky.  
  
7. V okně konzoly služby službu zavřete stisknutím klávesy ENTER. Stisknutím klávesy ENTER zavřete klienta v okně konzoly klienta.

---
title: Řešení ReliableSecureProfile
ms.date: 03/30/2017
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 65523fcc1d08bd48a432e6cf599dfcb73ade8747
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805743"
---
# <a name="reliable-secure-profile"></a>Řešení ReliableSecureProfile
Tento příklad ukazuje, jak vytvořit WCF a [spolehlivé profil zabezpečení](http://go.microsoft.com/fwlink/?LinkId=178140) (konfigurace). Tento příklad znázorňuje implementaci [vytvořit připojení](http://go.microsoft.com/fwlink/?LinkId=178141) kanál, který může být složené, společně s spolehlivé zasílání zpráv a volitelně zabezpečený kanál vytvořit spolehlivá zabezpečené vazby podle specifikace konfigurace.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a>Diskusní  
 Tento příklad znázorňuje scénáři exchange spolehlivé asynchronní obousměrný zprávu. Služba má duplexního kontraktu a implementuje kontrakt duplexní zpětné volání klienta. Klient inicializuje požadavek na službu, pro kterou je očekáván odpověď na samostatné připojení. Spolehlivě je odeslána zpráva požadavku. Klient nechce otevřete koncový bod naslouchání v jeho koncem. Proto dotazuje službu s vytvořit připojení žádosti o službu má být zaslán zpět odpověď na používající back channel tohoto požadavku vytvořit připojení. Tento příklad ukazuje, jak tak, aby měl zabezpečené spolehlivé duplexní komunikace přes protokol HTTP bez klienta vystavení naslouchání koncového bodu (a vytváření výjimku brány firewall).  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Otevřete **ReliableSecureProfile** řešení.  
  
2.  Klikněte pravým tlačítkem **služby** projektu v **Průzkumníku řešení**, vyberte **ladění**, **spustit novou instanci** v místní nabídce. Tím se spustí až hostitele služby.  
  
3.  Klikněte pravým tlačítkem **klienta** projektu v **Průzkumníku řešení**, vyberte **ladění**, **spustit novou instanci** v místní nabídce. To spuštění klienta.  
  
4.  Zadejte do libovolného řetězce v řádku v okně konzoly klienta a stiskněte ENTER. Vstupní řetězec tím se odešle do služby, která vypočítá hodnotu hash tento řetězec.  
  
5.  Zobrazení výsledek na klienta windows, když služba zpětným voláním operace zpětného duplexní kontrakt zobrazíte výsledek na okna konzoly klienta. Na službu, kterou chcete simulovat dlouhotrvající operace zpracování dat je úmyslné zpoždění.  
  
6.  Monitorování provoz HTTP (podle online sítě monitorování nástroje, například sledování sítě, Fiddler a tak dále) ukázáno, že pořadí pro komunikaci mezi klientem a službu podle stanovených spolehlivé profil zabezpečení a jak klienta dotazuje službu s požadavky vytvořit připojení. Když služba získá připravené má být zaslán zpět zpracování odpovědi, používá používající back channel poslední žádosti vytvořit připojení má být zaslán zpět výsledky.  
  
7.  V okně konzoly služby službu zavřete stisknutím klávesy ENTER. Stiskněte klávesu ENTER na okna konzoly klienta zavřít klienta.

---
title: Poradce při potížích s kurzy Nadace komunikace systému Windows
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 73aa0f5784784cb788a7532f8e22cbe925429c41
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249614"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>Poradce při potížích s kurzy Nadace komunikace systému Windows

Tento článek obsahuje řešení nejčastějších problémů a chyb, kterým můžete čelit při postupujte podle pokynů v [kurzu: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).
  
## <a name="common-problems"></a>Běžné problémy

**Nelze najít soubory projektu na pevném disku**

 Visual Studio ukládá soubory projektu do *jazyka C:\Users\\&lt;user&gt;name \source\repos*.  

**Nemohu najít soubor *App.config* generovaný *Svcutil.exe*.**

 V sadě Visual Studio zobrazí okno **Přidat existující položku** ve výchozím nastavení pouze soubory s následujícími rozšířeními:

- *.cs*
- *.resx*
- *.nastavení*
- *Xsd*
- *.wsdl*

Chcete-li zobrazit všechny typy souborů, vyberte v rozevíracím seznamu v pravém dolním rohu okna **Přidat existující položku** položku **Všechny soubory (\*.\*).**  
  
## <a name="common-errors"></a>Běžné chyby

### <a name="compile-the-service-application"></a>Kompilace aplikace služby

**Chyba BC30420 'Sub Main' nebyl nalezen v 'GettingStartedHost.Module1'.**

Vstupní bod je nesprávný pro aplikaci jazyka Visual Basic. Proveďte následující změnu:

   1. V okně **Průzkumník řešení** vyberte složku **GettingStartedHost** a pak v místní nabídce vyberte **Vlastnosti.**
    a. V okně **GettingStartedHost** vyberte pro **objekt Startup**ze seznamu **položku Service.Program** (nebo vstupní bod pro konkrétní aplikaci).
    b. V hlavní nabídce vyberte **Soubor** > **Uložit vše**.

### <a name="run-the-service-application"></a>Spuštění aplikace služby

**HTTP nelze zaregistrovat adresu\/URL 'http: /+:8000/GettingStarted/CalculatorService'. Proces nemá přístupová práva k tomuto oboru názvů.**

 Chcete-li získat správný přístup, spusťte proces hostování služby WCF (Windows Communication Foundation) s oprávněními správce:

- Pro Visual Studio: Vyberte program Sady Visual Studio v nabídce **Start** a v místní nabídce vyberte **Další** > **spuštění jako správce.**
- Pro okno konzoly: V nabídce **Start** vyberte **Příkazový řádek** a v místní nabídce vyberte **Další** > **spuštění jako správce.**
- Pro Průzkumníka Windows: Vyberte spustitelný soubor a v místní nabídce vyberte **Spustit jako správce.**

### <a name="compile-the-client-application"></a>Kompilace klientské aplikace

**'CalculatorClient', neobsahuje definici\<pro ' název metody>' a žádná metoda rozšíření '\<metoda>' přijetí první argument typu 'CalculatorClient' by mohl být nalezen (chybí vám using směrnice nebo odkaz na sestavení?)**  

Pouze ty metody, které `ServiceOperationAttribute` označíte atributem jsou veřejně vystaveny. Pokud vyneche `ServiceOperationAttribute` atribut z `ICalculator` metody v rozhraní, zobrazí se tato chybová zpráva během kompilace.  

**Typ nebo název oboru názvů CalculatorClient nebyl nalezen (chybí vám direktiva using nebo odkaz na sestavení?)**

 Tato chyba se zobrazí, pokud nepřidáte soubor *generatedProxy.cs* (nebo *generatedProxy.vb)* do klientského projektu, když jste je vygenerovali pomocí nástroje *Svcutil.exe.*  

### <a name="run-the-client-application"></a>Spuštění klientské aplikace

**Neošetřená výjimka: System.ServiceModel.EndpointNotFoundException: Nelze\/se připojit k 'http: /localhost:8000/GettingStarted/CalculatorService'. Kód chyby Protokolu TCP 10061: Nebylo možné provést žádné připojení, protože cílový počítač jej aktivně odmítl.**

K této chybě dochází, pokud spustíte klientskou aplikaci bez předchozího spuštění služby. Nejprve spusťte hostitelskou aplikaci ke spuštění služby a potom spusťte klientskou aplikaci.

### <a name="use-the-svcutilexe-tool"></a>Použití nástroje Svcutil.exe

**'Svcutil' není rozpoznán jako interní nebo externí příkaz, funkční program nebo dávkový soubor.**

 *Svcutil.exe* musí být v cestě systému. Nejjednodušším řešením je použití příkazového řádku sady Visual Studio. V nabídce **Start** vyberte>adresář **verze sady Visual Studio \<** a pak vyberte **Příkazový řádek pro vývojáře pro verzi \<VS>**. Tento příkazový řádek nastaví systémovou cestu do správného umístění pro všechny nástroje dodávané jako součást sady Visual Studio.  
  
### <a name="run-the-service-and-client-applications"></a>Spuštění služeb a klientských aplikací

**System.ServiceModel.Security.SecurityNegotiationException: SOAP vyjednávání zabezpečení\/s 'http: /localhost:8000/GettingStarted/CalculatorService' pro cíl 'http:\//localhost:8000/GettingStarted/CalculatorService' se nezdařilo**  

K této chybě dochází v počítači přilehlém k doméně, který nemá připojení k síti. Připojte počítač k síti nebo vypněte zabezpečení služby i klienta.

Vypnutí zabezpečení:

- Pro službu nahraďte kód, který vytvoří `WSHttpBinding` následující kód:  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- Pro klienta aktualizujte v konfiguračním souboru prvek ** \<>zabezpečení** pod elementem ** \<>vazbou** následujícím způsobem:  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator">
      <security mode="None" />
    </binding
    ```  

## <a name="see-also"></a>Viz také  
 [Začínáme s aplikacemi WCF](getting-started-tutorial.md)  
 [Rychlý start řešení potíží wcf](wcf-troubleshooting-quickstart.md)  
 [Poradce při potížích s instalací](troubleshooting-setup-issues.md)

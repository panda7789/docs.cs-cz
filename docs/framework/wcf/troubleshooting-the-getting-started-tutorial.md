---
title: Řešení potíží s Get začít kurzy Windows Communication Foundation
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 8089e0fee262d07be591069982b1aacfbeae2521
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791466"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>Řešení potíží s Get začít kurzy Windows Communication Foundation

Tento článek obsahuje nejčastější problémy a chyby může být setkáte, pokud budete postupovat podle kroků v řešení [kurzu: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md). 
  
## <a name="common-problems"></a>Běžné problémy

**Nemůžu najít soubory projektu na pevném disku.**

 Uloží soubory projektu v sadě Visual Studio *C:\Users\\&lt;uživatelské jméno&gt;\source\repos*.  

**Nemůžu najít *App.config* soubor generovaný nástrojem *Svcutil.exe*.**

 V sadě Visual Studio **přidat existující položku** okně zobrazí pouze soubory s těmito příponami ve výchozím nastavení: 
- *.cs* 
- *resx* 
- *.settings*
- *.xsd* 
- *.wsdl*

Chcete-li zobrazit všechny typy souborů, vyberte **všechny soubory (\*.\*)**  v rozevíracím seznamu v pravém horním rohu **přidat existující položku** okna.  
  
## <a name="common-errors"></a>Běžné chyby

### <a name="compile-the-service-application"></a>Zkompilujte aplikaci služby 

**Chyba BC30420 'Sub Main' nebyla nalezena v "GettingStartedHost.Module1".**

Vstupní bod není pro aplikaci Visual Basic. Proveďte následující změnu:

   1. V **Průzkumníka řešení** okna, vyberte **GettingStartedHost** složku a pak vyberte **vlastnosti** z místní nabídky.
    a. V **GettingStartedHost** okně pro **spouštěcí objekt**vyberte **Service.Program** (nebo vstupní bod pro konkrétní aplikaci) ze seznamu. 
    b. V hlavní nabídce vyberte **souboru** > **Uložit vše**.

### <a name="run-the-service-application"></a>Spuštění služby aplikace 

**Protokol HTTP nemohl zaregistrovat adresu URL: http:\// +: 8000/GettingStarted/CalculatorService ". Váš proces nemá přístupová práva k tomuto oboru názvů.** 

 Pro přístup zahájíte proces hostování služby Windows Communication Foundation (WCF) s oprávněními správce:
- For Visual Studio: Vyberte program sady Visual Studio **Start** nabídky a pak vyberte **Další** > **spustit jako správce** z místní nabídky.
- Okna konzoly: Vyberte **příkazového řádku** v **Start** nabídky a pak vyberte **Další** > **spustit jako správce** ze zástupce nabídka.
- Pro aplikaci Windows Explorer: Vybrat spustitelný soubor a pak vyberte **spustit jako správce** z místní nabídky.

### <a name="compile-the-client-application"></a>Kompilace klientské aplikace

**'CalculatorClient' neobsahuje definici pro '\<název metody > "a žádná metoda rozšíření '\<název metody >' přijímala první argument typu 'CalculatorClient' nebyla nalezena. (nechybí using – direktiva nebo odkaz na sestavení?)**  

Pouze těch metod, které označíte s `ServiceOperationAttribute` atribut jsou veřejně přístupné. Vynecháte-li `ServiceOperationAttribute` atribut z metody v `ICalculator` rozhraní, zobrazí tato chybová zpráva při kompilaci.  

**Typ nebo obor názvů 'CalculatorClient' nebyl nalezen. (nechybí using – direktiva nebo odkaz na sestavení?)**

 Tato chyba se zobrazí, pokud nepřidáte *generatedProxy.cs* (nebo *generatedProxy.vb*) soubor do projektu klienta při generování s *Svcutil.exe* nástroj .  

### <a name="run-the-client-application"></a>Spuštění klientské aplikace

**Neošetřená výjimka: System.ServiceModel.EndpointNotFoundException: Nelze se připojit k "http:\//localhost:8000/GettingStarted/CalculatorService". Kód chyby TCP 10061: Protože cílový počítač aktivně odmítl může nevytváří žádné připojení.**

K této chybě dochází, pokud spuštění klientské aplikace bez první spuštění služby. Nejprve spustit hostitelskou aplikaci spustit službu a pak spusťte klientskou aplikaci.

### <a name="use-the-svcutilexe-tool"></a>Použití nástroje Svcutil.exe
   
**'Svcutil' nebyl rozpoznán jako vnitřního ani vnějšího příkazu, spustitelného programu nebo dávkového souboru.**

 *Svcutil.exe* musí být v systémové cestě. Nejjednodušším řešením je použít příkazový řádek sady Visual Studio. Z **Start** nabídku, vyberte **sady Visual Studio \<verze >** adresář a potom vyberte **Developer Command Prompt for VS \<verze >**. Tento příkazový řádek nastaví systémové cesty na správné umístění pro všechny nástroje dodávané jako součást sady Visual Studio.  
  
### <a name="run-the-service-and-client-applications"></a>Spuštění služeb a klientských aplikací

**System.ServiceModel.Security.SecurityNegotiationException: Vyjednávání zabezpečení SOAP s "http:\//localhost:8000/GettingStarted/CalculatorService" pro cíl "http:\//localhost:8000/GettingStarted/CalculatorService ' se nezdařilo**  

K této chybě dochází v počítači připojeném k doméně, která nemá připojení k síti. Připojení počítače k síti nebo vypněte zabezpečení pro službu a klienta. 

Chcete-li vypnout zabezpečení:

- Pro službu, nahraďte kód, který vytvoří `WSHttpBinding` následujícím kódem:  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- Aktualizace klienta v konfiguračním souboru  **\<zabezpečení >** element v rámci  **\<vazby >** element následujícím způsobem:  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator" security mode="None" />
    ```  

## <a name="see-also"></a>Viz také:  
 [Začínáme s aplikací služby WCF](getting-started-tutorial.md)  
 [Řešení problémů s WCF – úvodní příručka](wcf-troubleshooting-quickstart.md)  
 [Řešení problémů s instalací](troubleshooting-setup-issues.md)

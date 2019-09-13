---
title: Řešení potíží s výukou Začínáme s Windows Communication Foundation
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 10a2f8f718d802a7aab067b882f0d5cf3dc28dca
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928579"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>Řešení potíží s výukou Začínáme s Windows Communication Foundation

Tento článek popisuje řešení nejběžnějších problémů a chyb, se kterými se můžete setkat, když provedete kroky [v tomto kurzu: Začněte s Windows Communication Foundation aplikacemi](getting-started-tutorial.md). 
  
## <a name="common-problems"></a>Běžné problémy

**Nemohu najít soubory projektu na mém pevném disku.**

 Visual Studio ukládá soubory projektu v *C:\Users\\&lt;uživatelské jméno&gt;\source\repos*.  

**Nejde najít soubor *App. config* vygenerovaný *Svcutil. exe*.**

 V aplikaci Visual Studio okno **Přidat existující položku** zobrazí ve výchozím nastavení pouze soubory s následujícími příponami: 

- *.cs* 
- *. resx* 
- *.settings*
- *.xsd* 
- *.wsdl*

Chcete-li zobrazit všechny typy souborů, vyberte možnost **všechny\*soubory (\*.)** v rozevíracím seznamu v pravém dolním rohu okna **Přidat existující položku** .  
  
## <a name="common-errors"></a>Běžné chyby

### <a name="compile-the-service-application"></a>Kompilovat aplikaci služby 

**Chyba BC30420 procedura Sub Main nebyla v souboru GettingStartedHost. Module1 nalezena.**

Vstupní bod je pro Visual Basic aplikaci nesprávný. Proveďte následující změnu:

   1. V okně **Průzkumník řešení** vyberte složku **GettingStartedHost** a potom v místní nabídce vyberte možnost **vlastnosti** .
    a. V okně **GettingStartedHost** pro **spouštěcí objekt**vyberte ze seznamu možnost **Service. program** (nebo vstupní bod pro konkrétní aplikaci). 
    b. V hlavní nabídce vyberte **soubor** > **Uložit vše**.

### <a name="run-the-service-application"></a>Spuštění aplikace služby 

**Protokol HTTP nemohl zaregistrovat adresu URL ' http\/:/+: 8000/soubor GettingStarted/CalculatorService '. Váš proces nemá přístupová práva k tomuto oboru názvů.** 

 Pro řádný přístup spusťte proces hostující službu Windows Communication Foundation (WCF) s oprávněními správce:

- Pro Visual Studio: V nabídce **Start** vyberte program Visual Studio a v místní nabídce vyberte **Další** > **Spustit jako správce** .
- Pro okno konzoly: V nabídce **Start** vyberte **příkazový řádek** a v místní nabídce vyberte **Další** > **Spustit jako správce** .
- Pro Průzkumníka Windows: Vyberte spustitelný soubor a v místní nabídce vyberte **Spustit jako správce** .

### <a name="compile-the-client-application"></a>Kompilace klientské aplikace

**' CalculatorClient ' neobsahuje definici pro '\<název metody > ' a nebyla nalezena žádná\<metoda rozšíření > ' přijetí prvního argumentu typu ' CalculatorClient ' (nechybí Direktiva using nebo odkaz na sestavení?)**  

Pouze ty metody, které označíte pomocí `ServiceOperationAttribute` atributu, jsou veřejně vystavené. Vynecháte `ServiceOperationAttribute` -li atribut z metody `ICalculator` v rozhraní, zobrazí se tato chybová zpráva během kompilace.  

**Typ nebo název oboru názvů ' CalculatorClient ' nebyl nalezen (nechybí Direktiva using nebo odkaz na sestavení?)**

 Tato chyba se zobrazí, pokud nepřidáte soubor *generatedProxy.cs* (nebo *generatedProxy. vb*) do klientského projektu, když jste ho vygenerovali pomocí nástroje *Svcutil. exe* .  

### <a name="run-the-client-application"></a>Spuštění klientské aplikace

**Neošetřená výjimka: System.ServiceModel.EndpointNotFoundException: Nepovedlo se připojit k http\/:/localhost: 8000/soubor GettingStarted/CalculatorService. Kód chyby TCP 10061: Nebylo možné vytvořit připojení, protože cílový počítač ho aktivně odmítl.**

K této chybě dojde, pokud spouštíte klientskou aplikaci bez toho, aby se služba nejdřív spouštěla. Nejdřív spusťte hostitelskou aplikaci, která spustí službu, a pak spusťte klientskou aplikaci.

### <a name="use-the-svcutilexe-tool"></a>Použití nástroje Svcutil. exe
   
**' Svcutil ' není rozpoznán jako interní nebo externí příkaz, spustitelný program nebo dávkový soubor.**

 *Svcutil. exe* musí být v systémové cestě. Nejjednodušším řešením je použití příkazového řádku sady Visual Studio. V nabídce **Start** vyberte adresář **> verze sady Visual \<Studio** a potom vyberte **Developer Command Prompt pro > verze vs \<** . Tento příkazový řádek nastaví cestu systému ke správným umístěním pro všechny nástroje dodávané jako součást sady Visual Studio.  
  
### <a name="run-the-service-and-client-applications"></a>Spuštění služby a klientských aplikací

**System.ServiceModel.Security.SecurityNegotiationException: Vyjednávání zabezpečení SOAP s http:\//localhost: 8000/soubor GettingStarted/CalculatorService pro cíl http:\//localhost: 8000/soubor GettingStarted/CalculatorService se nezdařilo.**  

K této chybě dochází na počítači připojeném k doméně, který nemá síťové připojení. Připojte počítač k síti nebo vypněte zabezpečení pro službu i klienta. 

Vypnutí zabezpečení:

- Pro službu nahraďte kód, který vytvoří `WSHttpBinding` , následující kód:  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- Pro klienta aktualizujte  **\<** v konfiguračním souboru element Security > pod  **\<prvkem vazby >** následujícím způsobem:  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator" security mode="None" />
    ```  

## <a name="see-also"></a>Viz také:  
 [Začínáme s aplikacemi WCF](getting-started-tutorial.md)  
 [Rychlý Start pro řešení potíží WCF](wcf-troubleshooting-quickstart.md)  
 [Řešení potíží s instalací](troubleshooting-setup-issues.md)

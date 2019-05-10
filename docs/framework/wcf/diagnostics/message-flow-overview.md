---
title: Tok zpráv – přehled
ms.date: 03/30/2017
ms.assetid: fb0899e1-84cc-4d90-b45b-dc5a50063943
ms.openlocfilehash: 009dd05ab299b92ee5f5cafd1c2131a2e6eb0132
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650246"
---
# <a name="message-flow-overview"></a>Tok zpráv – přehled
V distribuovaném systému obsahující propojených služeb je potřeba určit příčinnou vztahy mezi službami. Je důležité pochopit různé součásti, které byly součástí tok požadavku pro podporu důležitých scénářů, jako je stav monitorování, řešení problémů a analýzu kořenových příčin. Chcete-li povolit trasování korelace různých služeb v rozhraní .NET Framework 4 přidali jsme podporu prostřednictvím následujících funkcí:

- Analytické trasování: Vysoký výkon a nízkou úroveň podrobností funkce trasování pomocí Event Tracing for Windows (ETW).

- Aktivita začátku do konce modelu pro služby WCF/WF: Tato funkce podporuje korelace trasování vygenerovaná <xref:System.ServiceModel> a <xref:System.Workflow.ComponentModel> obory názvů.

- Trasování událostí pro Windows Sledování pracovního postupu: Tato funkce používá sledování záznamů vygenerovaných službami WF poskytnout přehled o aktuálním stavu a průběhu pracovního postupu.

 Chyby přihlášení sledování nebo sledování záznamů lze použít k vyhledání vad kódu nebo nesprávně vytvořený zprávy. Vlastnost ID korelace uzlu v záhlaví zprávy události. je možné určit neškodné aktivity. Pokud chcete povolit trasování toku zpráv podle ID aktivity, naleznete v tématu [Konfigurace trasování toku zpráv](../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md). Toto téma ukazuje, jak povolit trasování toku zpráv v projektu vytvořeného v tomto kurzu Začínáme.

### <a name="to-enable-message-flow-tracing-in-the-getting-started-tutorial"></a>Chcete-li povolit trasování toku zpráv v kurzu Začínáme

1. Otevřete Prohlížeč událostí kliknutím **Start**, **spustit**a zadat `eventvwr.exe`.

2. Pokud jste ještě nepovolili analytické trasování, rozbalte **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **serveru aplikace** . Vyberte **zobrazení**, **zobrazit analytické a ladit protokoly**. Klikněte pravým tlačítkem na **analytické** a vyberte **povolit protokol**. Prohlížeč událostí zůstat otevřeno, takže lze zobrazit trasování.

3. Otevřete ukázku v vytvoří [kurz Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md) v sadě Visual Studio 2012. Všimněte si, že spustíte Visual Studio 2012 jako správce tak, že můžete vytvořit službu. Pokud máte nainstalované Ukázky WCF, můžete otevřít [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který obsahuje dokončený projekt vytvořený v tomto kurzu.

4. Klikněte pravým tlačítkem myši **služby** projektu a vyberte **přidat**, **nová položka**. Vyberte **konfiguračního souboru aplikace** a klikněte na tlačítko **OK**.

5. Přidejte následující kód do souboru App.Config vytvořili v předchozím kroku.

    ```xml
    <system.serviceModel>
      <diagnostics>
        <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>
      </diagnostics>
    </system.serviceModel>
    ```

6. Serverová aplikace spusťte bez ladění stisknutím kombinace kláves CTRL + F5. Spusťte klientský projekt kliknutím pravým tlačítkem myši **klienta** projekt a výběrem **ladění**, **spustit novou instanci**.

7. Pokud chcete trasovat události z klienta na server, přidejte následující do konfiguračního souboru aplikace v klientském projektu.

    ```xml
    <diagnostics>
      <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>
    </diagnostics>
    ```

8. V souboru Program.cs v klientovi přidejte následující příkaz Using.

    ```csharp
    using System.Diagnostics;
    ```

9. V hlavní metodě v souboru program.cs v projektu klienta nastavte trasování identifikátor GUID mohly rozšířit v protokolu událostí.

    ```csharp
    Guid guid = Guid.NewGuid();
    Trace.CorrelationManager.ActivityId = guid;
    ```

10. Aktualizovat a zkontrolovat **analytické** protokolu.  Hledejte události s ID 220 události.  Vyberte událost a klikněte na tlačítko **podrobnosti** kartě v podokně náhledu. Tato událost bude obsahovat ID korelace pro volání aktivity.

    ```xml
    <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" />
    ```

    > [!NOTE]
    >  Všechny události se stejným GUID v ID se vztahují k jedné žádosti. To lze použít ke korelaci zprávy z konkrétního klienta pro konkrétní službu. Pokud klient volá jinou službu, pak stejného klienta může být identifikován ID aktivity.

11. V některých případech můžete změnit ID z původní GUID na nové ID aktivity. V takovém případě je vygenerován událost přenosu. Toto ID události je 499 a události bude obsahovat následující data v záhlaví.

    ```xml
    <Event xmlns="http://schemas.microsoft.com/win/2004/08/events/event">
        <System>
            <Provider Name="Microsoft-Windows-Application Server-Applications" Guid="{c651f5f6-1c0d-492e-8ae1-b4efd7c9d503}" />
            <EventID>499</EventID>
            ...
            <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" RelatedActivityID="{85FC0930-9C49-42DA-804B-A7368104BD1B}" />
            ...
       </System>
    </Event>
    ```

    > [!NOTE]
    >  Událost přenosu zaznamenává změny active ID činnosti z identifikátor GUID specifikovaný jako mít podle ID na identifikátor GUID. Po událost přenosu je vygenerován, bude obsahovat všechny události nový identifikátor GUID jako ID.

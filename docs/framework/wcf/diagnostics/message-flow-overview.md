---
title: Tok zpráv – přehled
ms.date: 03/30/2017
ms.assetid: fb0899e1-84cc-4d90-b45b-dc5a50063943
ms.openlocfilehash: aea0ca4c5a8574f6039cd055561ce7da0099841b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809791"
---
# <a name="message-flow-overview"></a>Tok zpráv – přehled
V distribuované systému obsahující vzájemně propojené služby je potřeba určit příčinnou vztahy mezi službami. Je důležité pochopit různé součásti, které byly součástí toku požadavků na podporu kritické scénáře, jako je stav monitorování, řešení potíží a příčina analýzy. Chcete-li povolit korelace trasování mezi různé služby, v rozhraní .NET Framework 4 jsme doplnili podporu prostřednictvím následujících funkcí:  
  
-   Analytické trasování: vysoký výkon a nízkou podrobností trasování funkci pomocí události trasování událostí pro Windows (ETW).  
  
-   Začátku do konce aktivity modelu pro služby WCF Vestavěné: Tato funkce podporuje korelace trasování, které jsou generované <xref:System.ServiceModel> a <xref:System.Workflow.ComponentModel> obory názvů.  
  
-   Sledování WF trasování událostí pro Windows: Tato funkce používá sledování záznamy vygenerované WF služby poskytovat přehled o aktuálním stavu a průběhu pracovního postupu.  
  
 Chyby přihlášení pro sledování nebo záznam trasování můžete použít k vyhledání míry výskytu závad kódu nebo nesprávně vytvořený zprávy. Vlastnost ID korelace uzlu v záhlaví zprávy události slouží k určení chybující aktivity. Chcete-li povolit trasování toku zpráv podle ID aktivity, přečtěte si téma [Konfigurace trasování toku zpráv](../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md). Toto téma ukazuje, jak povolit trasování toku zpráv v projektu vytvořili v kurzu Začínáme.  
  
### <a name="to-enable-message-flow-tracing-in-the-getting-started-tutorial"></a>Chcete-li povolit trasování toku zpráv v tomto kurzu Začínáme  
  
1.  Otevřete Prohlížeč událostí kliknutím **spustit**, **spustit**a zadáním `eventvwr.exe`.  
  
2.  Pokud jste nepovolili analytické trasování, rozbalte položku **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **serveru aplikace – aplikace** . Vyberte **zobrazení**, **ukazují analytické a ladicí protokoly**. Klikněte pravým tlačítkem na **analytické** a vyberte **povolit protokol**. Ponechte prohlížeče událostí otevřete tak, aby trasování je možné zobrazit.  
  
3.  Otevřete ukázku vytvořené v [kurzu Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md) v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]. Všimněte si, že je nutné spustit [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] jako správce, aby bylo možné vytvořit službu. Pokud máte Ukázky WCF nainstalován, můžete otevřít [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který obsahuje dokončený projekt vytvořený v tomto kurzu.  
  
4.  Klikněte pravým tlačítkem myši **služby** projektu a vyberte **přidat**, **novou položku**. Vyberte **konfigurační soubor aplikace** a klikněte na tlačítko **OK**.  
  
5.  Přidejte následující kód do souboru App.Config vytvořili v předchozím kroku.  
  
    ```xml  
    <system.serviceModel>  
      <diagnostics>  
        <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>  
      </diagnostics>  
    </system.serviceModel>  
    ```  
  
6.  Aplikace serveru spusťte bez ladění stisknutím kombinace kláves CTRL + F5. Spusťte projekt klienta tak, že kliknete pravým tlačítkem **klienta** projekt a výběrem **ladění**, **spustit novou instanci**.  
  
7.  Pokud chcete trasovat události od klienta k serveru, přidejte následující konfigurační soubor aplikace v projektu klienta.  
  
    ```xml  
    <diagnostics>  
      <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>  
    </diagnostics>  
    ```  
  
8.  V souboru Program.cs v klientovi přidejte následující příkaz Using.  
  
    ```  
    using System.Diagnostics;  
    ```  
  
9. V metodě hlavní v souboru program.cs v projektu klienta nastavte identifikátor GUID trasování mohly rozšířit v protokolu událostí.  
  
    ```  
    Guid guid = Guid.NewGuid();  
    Trace.CorrelationManager.ActivityId = guid;  
    ```  
  
10. Aktualizujte a zkontrolujte **analytické** protokolu.  Podívejte se na událost s ID 220 událostí.  Vyberte události a klikněte na **podrobnosti** kartě v podokně náhledu. Tato událost bude obsahovat ID korelace volání aktivity.  
  
    ```xml  
    <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" />  
    ```  
  
    > [!NOTE]
    >  Všechny události se stejným identifikátorem GUID v ID se vztahují na jednu žádost. To můžete použít ke korelaci zprávy z konkrétního klienta ke konkrétní službě. Pokud klient volá jinou službu, pak stejného klienta může být identifikován aktivity.  
  
11. V některých případech může změnit ID z původní GUID na nové aktivity. V takovém případě jsou vydávány událost přenosu. Toto ID události je 499 a události bude obsahovat následující data v hlavičce.  
  
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
    >  Událost přenosu zaznamenává změnu active aktivity z zadaný jako ID na identifikátor GUID zadány jako RelatedActivityID identifikátor GUID. Po událost přenosu je vygenerované, všechny události bude obsahovat identifikátor GUID nového ID.

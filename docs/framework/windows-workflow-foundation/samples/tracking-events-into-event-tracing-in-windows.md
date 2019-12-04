---
title: Sledování událostí ve službě Event Tracking ve Windows
ms.date: 03/30/2017
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
ms.openlocfilehash: fe50476eedef505258c2e6818e75a32c06ed6fa6
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715929"
---
# <a name="tracking-events-into-event-tracing-in-windows"></a>Sledování událostí ve službě Event Tracking ve Windows

Tato ukázka předvádí, jak povolit sledování programovací model Windows Workflow Foundation (WF) ve službě pracovního postupu a jak vygenerovat události sledování v trasování událostí pro Windows (ETW). K vygenerování záznamů sledování pracovního postupu v ETW používá ukázka účastník sledování ETW (<xref:System.Activities.Tracking.EtwTrackingParticipant>).

Pracovní postup v ukázce obdrží požadavek, přiřadí převrácenou vstupní data do vstupní proměnné a vrátí vrácenou zpět klientovi. Pokud jsou vstupní data 0, dojde k dělení nulou s výjimkou, která je Neošetřená, což způsobí přerušení pracovního postupu. Je-li povoleno sledování, je záznam sledování chyb generován do trasování událostí pro Windows, což může pomoct později vyřešit chybu. Účastník sledování ETW je nakonfigurovaný s profilem sledování, aby se mohl přihlásit k odběru sledování záznamů. Profil sledování je definován v souboru Web. config a poskytuje se jako parametr konfigurace účastníkovi sledování ETW. Účastník sledování ETW je nakonfigurovaný v souboru Web. config služby pracovního postupu a používá se pro službu jako chování služby. V této ukázce zobrazíte události sledování v protokolu událostí pomocí Prohlížeč událostí.

## <a name="workflow-tracking-details"></a>Podrobnosti sledování pracovního postupu

Programovací model Windows Workflow Foundation poskytuje sledovací infrastrukturu pro sledování provádění instance pracovního postupu. Modul runtime sledování vytvoří instanci pracovního postupu pro vygenerování událostí souvisejících s životním cyklem pracovního postupu, událostí z aktivit pracovního postupu a vlastními událostmi. Následující tabulka podrobně popisuje primární součásti infrastruktury sledování.

|Součást|Popis|
|---------------|-----------------|
|Sledování – modul runtime|Poskytuje infrastrukturu pro vygenerování záznamů sledování.|
|Sledování účastníků|Přistupuje k záznamům sledování. [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] lodí se sledováním účastníka, který zapisuje záznamy sledování jako události trasování událostí pro Windows (ETW).|
|Profil sledování|Mechanismus filtrování, který umožňuje sledování účastníka přihlásit k odběru podmnožiny sledovacích záznamů emitovaných z instance pracovního postupu.|

Následující tabulka podrobně popisuje záznamy sledování, které modul runtime pracovního postupu generuje.

|Záznam sledování|Popis|
|---------------------|-----------------|
|Záznamy sledování instance pracovního postupu.|Popisuje životní cyklus instance pracovního postupu. Například záznam instance je generován při spuštění nebo dokončení pracovního postupu.|
|Záznamy sledování stavu aktivity.|Podrobnosti provádění aktivity. Tyto záznamy označují stav aktivity pracovního postupu, například když je naplánována aktivita nebo když se aktivita dokončí nebo když je vyvolána chyba.|
|Záznam opětovného pokračování záložky|Vygenerováno pokaždé, když je obnovena záložka v instanci pracovního postupu.|
|Vlastní záznamy sledování.|Autor pracovního postupu může vytvořit vlastní záznamy sledování a vygenerovat je v rámci vlastní aktivity.|
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|Tento záznam se vygeneruje, když aktivita plánuje jinou aktivitu.|
|<xref:System.Activities.Tracking.FaultPropagationRecord>|Tento záznam je generován při šíření chyby z aktivity.|
|<xref:System.Activities.Tracking.CancelRequestedRecord>|Tento záznam se vygeneruje, když se aktivita zruší jinou aktivitou.|

Účastník sledování se přihlásí k odběru podmnožiny vygenerovaných záznamů sledování pomocí sledování profilů. Profil sledování obsahuje sledovací dotazy, které umožňují přihlášení k odběru konkrétního typu záznamu sledování. Sledování profilů lze zadat v kódu nebo v konfiguraci.

#### <a name="to-use-this-sample"></a>Použití této ukázky

1. Pomocí sady Visual Studio 2010 otevřete soubor řešení EtwTrackingParticipantSample. sln.

2. Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.

3. Pokud chcete řešení spustit, stiskněte klávesu F5.

    Ve výchozím nastavení naslouchá služba na portu 53797 (http://localhost:53797/SampleWorkflowService.xamlx).

4. Pomocí Průzkumníka souborů otevřete testovacího klienta WCF.

    Testovací klient služby WCF (WcfTestClient. exe) se nachází ve složce \<instalační složka sady Visual Studio 2010 > složce \Common7\IDE\.

    Výchozí instalační složka sady Visual Studio 2010 je C:\Program Files\Microsoft Visual Studio 10,0.

5. V testovacím klientovi WCF vyberte **Přidat službu** z nabídky **soubor** .

    Do vstupního pole přidejte adresu koncového bodu. Výchozí hodnota je `http://localhost:53797/SampleWorkflowService.xamlx`.

6. Otevřete aplikaci Prohlížeč událostí.

    Před vyvoláním služby spusťte Prohlížeč událostí v nabídce **Start** vyberte **spustit** a zadejte `eventvwr.exe`. Zajistěte, aby protokol událostí naslouchal sledování událostí vydaných ze služby pracovního postupu.

7. Ve stromovém zobrazení Prohlížeč událostí přejděte do části **Prohlížeč událostí**, **protokoly aplikací a služeb**a **Microsoft**. Klikněte pravým tlačítkem myši na **Microsoft** a vyberte **Zobrazit** a pak **Zobrazte protokoly o analýze a ladění** , aby se aktivovaly protokoly pro analýzu a ladění.

    Zajistěte, aby byla zaškrtnuta možnost **Zobrazit protokoly o analýze a ladění** .

8. Ve stromovém zobrazení v Prohlížeč událostí přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikační server – aplikace**. Klikněte pravým tlačítkem na možnost **analytické** a vyberte **Povolit protokol** pro povolení **analytického** protokolu.

9. Otestujte službu pomocí testovacího klienta WCF dvojitým kliknutím na `GetData`.

    Tím se otevře metoda `GetData`. Požadavek akceptuje jeden parametr a zajistí, že hodnota je 0, což je výchozí hodnota.

     Klikněte na **vyvolat**.

10. Sledujte události vydávané z pracovního postupu.

    Přepněte zpět na Prohlížeč událostí a přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikační server – aplikace**. Klikněte pravým tlačítkem na možnost **analytické** a vyberte **aktualizovat**.

    Události pracovního postupu se zobrazí v prohlížeči událostí. Všimněte si, že se zobrazují události spuštění pracovního postupu a že jeden z nich je Neošetřená výjimka, která odpovídá chybě v pracovním postupu. Kromě toho je vyvolána událost upozornění z aktivity pracovního postupu, která indikuje, že aktivita vyvolává chybu.

11. Opakujte kroky 9 a 10 se vstupem dat s výjimkou 0, aby nedošlo k žádné chybě.

Sledování profilů vám umožní přihlásit se k odběru událostí vygenerovaných modulem runtime při změně stavu instance pracovního postupu. V závislosti na požadavcích na monitorování můžete vytvořit profil, který je velmi hrubý, který se přihlásí k odběru malé sady změn stavu vysoké úrovně v pracovním postupu. Na druhé straně můžete vytvořit velmi přesný profil, jehož výstup bude dostatečně bohatý, aby bylo možné provést pozdější opětovné vytvoření provádění. Ukázka demonstruje události emitované z modulu runtime pracovního postupu do ETW pomocí `HealthMonitoring Tracking Profile`, který generuje malou sadu událostí. Jiný profil, který generuje další události sledování pracovního postupu, je také k dispozici v souboru Web. config s názvem `Troubleshooting Tracking Profile`. Po instalaci [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] je v souboru Machine. config nakonfigurován výchozí profil s prázdným názvem. Tento profil se používá v konfiguraci chování sledování trasování událostí pro Windows, pokud není zadaný název profilu ani název prázdného profilu.

Profil sledování stavu vygeneruje záznamy instancí pracovního postupu a záznamy šíření chyb aktivity. Tento profil je vytvořen přidáním následujícího profilu sledování do konfiguračního souboru Web. config.

```xml
<tracking>
  <profiles>
    <trackingProfile name="HealthMonitoring Tracking Profile">
      <workflow activityDefinitionId="*">
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Started"/>
              <state name="Completed"/>
              <state name="Aborted"/>
              <state name="UnhandledException"/>
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```

 Profil se dá změnit tak, že změníte konfiguraci `EtwTrackingParticipant` na následující.

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <etwTracking profileName="HealthMonitoring Tracking Profile"/>
    </behavior>
  </serviceBehaviors>
</behaviors>
```

#### <a name="to-clean-up-optional"></a>Vyčištění (volitelné)

1. Otevřete Prohlížeč událostí.

2. Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikační server – aplikace**. Klikněte pravým tlačítkem na možnost **analytické** a vyberte možnost **zakázat protokol**.

3. Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikační server – aplikace**. Klikněte pravým tlačítkem na možnost **analytické** a vyberte možnost **Vymazat protokol**.

4. Kliknutím na možnost **Vymazat** vymažte události.

## <a name="known-issue"></a>Známý problém

> [!NOTE]
> Došlo k známému problému Prohlížeč událostí, kde se nemusí podařit dekódovat události ETW. Může se zobrazit chybová zpráva, která vypadá nějak takto:
>
> Popis ID události \<ID > ze zdrojového serveru Microsoft-Windows-Application Server – aplikace se nenašly. Buď není v místním počítači nainstalována komponenta, která vyvolává tuto událost, nebo je instalace poškozena. Součást můžete nainstalovat nebo opravit v místním počítači.
>
> Pokud k této chybě dojde, klikněte v podokně akce na aktualizovat. Událost by se teď měla dekódovat správně.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`

## <a name="see-also"></a>Viz také:

- [Ukázky monitorování technologie AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)

---
title: Sledování událostí ve službě Event Tracking ve Windows
ms.date: 03/30/2017
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
ms.openlocfilehash: 6384c74aa245db490d04fa95f37bd860dfb9bad9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166527"
---
# <a name="tracking-events-into-event-tracing-in-windows"></a>Sledování událostí ve službě Event Tracking ve Windows
Tento příklad ukazuje, jak povolit sledování služby pracovních postupů Windows Workflow Foundation (WF) a generovat sledování událostí v trasování událostí pro Windows (ETW). Vygenerovat pracovní postup do ETW sledování záznamů, ukázka používá účastník sledování ETW (<xref:System.Activities.Tracking.EtwTrackingParticipant>).

 Pracovní postup v ukázce obdrží žádost, přiřadí je vstupní proměnná převrácenou hodnotu druhé vstupní data a vrátí vzájemné zpět klientovi. Když jsou vstupní data 0, dělení nulovou výjimkou výskytu, která je neošetřená, který způsobí, že pracovní postup pro přerušení. S povoleným sledováním, je k trasování událostí pro Windows, které může pomoct vyřešit chybu později vyzařovaného záznamem sledování chyb. Účastník sledování ETW konfigurován pomocí sledování profil přihlásit k odběru sledování záznamů. Profil sledování je definované v souboru Web.config a zadat jako parametr konfigurace pro sledování účastníka trasování událostí pro Windows. Účastník sledování ETW konfigurován v souboru Web.config služby pracovního postupu a platí pro službu jako chování služby. V této ukázce zobrazit události sledování do protokolu událostí v prohlížeči událostí.

## <a name="workflow-tracking-details"></a>Podrobnosti o sledování pracovního postupu
 Windows Workflow Foundation poskytuje sledování infrastruktury pro sledování spuštění instance pracovního postupu. Modul runtime sledování vytvoří instanci pracovního postupu ke generování událostí souvisejících s životního cyklu pracovního postupu, události z aktivit pracovního postupu a vlastní události. Následující tabulka obsahuje podrobnosti o primární součásti sledování infrastruktury.

|Součást|Popis|
|---------------|-----------------|
|Sledování modulu runtime|Poskytuje infrastrukturu pro vydávání záznamy sledování.|
|Sledování účastníci|Přistupuje k sledování záznamů. [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] se dodává s účastníkem sledování, která zapíše záznamy sledování jako události trasování událostí pro Windows (ETW).|
|Profil sledování Tracking profile|Filtrování mechanismus, který umožňuje sledování účastník přihlásit pouze podmnožinu záznamů sledování vyzařováno instance pracovního postupu.|

 Následující tabulka obsahuje podrobnosti o sledování záznamů, které generuje modul runtime pracovního postupu.

|Záznam sledování|Popis|
|---------------------|-----------------|
|Pracovní postup instance sledování záznamů.|Popisuje životního cyklu instance pracovního postupu. Například záznam instance je vygenerován při spuštění pracovního postupu nebo dokončení.|
|Záznamy sledování stavu aktivity.|Podrobnosti provádění aktivity. Tyto záznamy ukazují stav pracovního postupu aktivity, jako je například kdy je naplánováno aktivitu nebo při dokončení aktivity nebo kdy je vyvolána chyba.|
|Záložku obnovení záznamů.|Pokaždé, když obnovení záložku v instanci pracovního postupu, protože ho.|
|Vlastní sledování záznamů.|Autor pracovního postupu můžete vytvořit vlastní záznamy sledování a generovat vlastní aktivity.|
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|Tento záznam je vygenerován, když aktivita naplánuje jiné aktivity.|
|<xref:System.Activities.Tracking.FaultPropagationRecord>|Tento záznam je vygenerován při chybu je rozšířena z aktivity.|
|<xref:System.Activities.Tracking.CancelRequestedRecord>|Tento záznam je vygenerován při zrušení aktivitu pomocí další aktivity.|

 Účastník sledování přihlásí pro podmnožinu emitovaný sledování záznamů pomocí sledování profilů. Profil sledování obsahuje sledování dotazy, které umožňují přihlášení k odběru pro sledování konkrétní typ záznamu. Sledování profily se dá nastavit v kódu nebo v konfiguraci.

#### <a name="to-use-this-sample"></a>Pro fungování této ukázky

1.  Pomocí sady Visual Studio 2010, otevřete soubor řešení EtwTrackingParticipantSample.sln.

2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.

3.  Abyste mohli spustit řešení, stiskněte klávesu F5.

     Ve výchozím nastavení, služba naslouchá na portu 53797 (http://localhost:53797/SampleWorkflowService.xamlx).

4.  Pomocí [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], otevřete testovací klient WCF.

     Testovací klient WCF (WcfTestClient.exe) se nachází v \<instalační složky sady Visual Studio 2010 > \Common7\IDE\ složky.

     Výchozí instalační složku sady Visual Studio 2010 je C:\Program Files\Microsoft Visual Studio 10.0.

5.  Testovací klient WCF, vyberte **přidat službu** z **souboru** nabídky.

     Přidáte adresu koncového bodu do vstupního pole. Výchozí hodnota je `http://localhost:53797/SampleWorkflowService.xamlx`.

6.  Otevřete Prohlížeč událostí aplikace.

     Před vyvoláním služby, spusťte Prohlížeč událostí z **Start** nabídce vyberte možnost **spustit** a do pole zadejte `eventvwr.exe`. Ujistěte se, že v protokolu událostí naslouchá ke sledování vyzařováno služby pracovního postupu událostí.

7.  Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, a **Microsoft**. Klikněte pravým tlačítkem na **Microsoft** a vyberte **zobrazení** a potom **zobrazit protokoly ladění a analýzu** povolit analytické a ladit protokoly

     Ujistěte se, **zobrazit protokoly ladění a analýzu** zaškrtnutá možnost.

8.  Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**,  **Aplikace Server-**. Klikněte pravým tlačítkem na **analytické** a vyberte **povolit protokol** povolit **analytické** protokolu.

9. Test pomocí testovacího klienta WCF na něj poklikejte `GetData`.

     Tím se otevře `GetData` metody. Požadavek přijímá jeden parametr a zajišťuje, že hodnota je 0, což je výchozí hodnota.

     Klikněte na tlačítko **vyvolat**.

10. Sledujte události vyzařovaného z pracovního postupu.

     Přepněte zpět do prohlížeče událostí a přejděte do **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**,  **Aplikace Server-**. Klikněte pravým tlačítkem na **analytické** a vyberte **aktualizovat**.

     Události pracovního postupu se zobrazí v prohlížeči událostí. Všimněte si, že se zobrazují události spuštění pracovního postupu a že jeden z nich je neošetřená výjimka, která odpovídá chybě v pracovním postupu. Navíc upozorňovací událost je vygenerován z aktivity pracovního postupu, který označuje, že aktivita způsobující chybu.

11. Opakujte kroky 9 a 10 se vstupem dat než 0, tak, že je vyvolána žádná chyba.

 Sledování profily umožňují přihlášení k odběru událostí, které jsou emitovány modulem runtime při změně stavu instance pracovního postupu. V závislosti na vašich požadavků na monitorování můžete vytvořit profil, který je velmi hrubou, který se přihlásí k odběru malou sadu změn stavu vysoké úrovně v pracovním postupu. Na druhé straně můžete vytvořit profil velmi přesné, jejichž výstupem je bohaté dostatečně k rekonstrukci spuštění později. Ukázce události generované z modulu runtime pracovního postupu pomocí trasování událostí pro Windows `HealthMonitoring Tracking Profile`, který vysílá malou sadu událostí. Jiný profil, který vysílá další pracovní postup sledování událostí je také k dispozici v souboru Web.config, který je pojmenován `Troubleshooting Tracking Profile`. Když [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] je nainstalovaný, výchozí profil s prázdným názvem je nakonfigurovaný v souboru Machine.config. Tento profil používá trasování událostí pro Windows Sledování konfiguraci chování, když je zadán žádný název profilu nebo název prázdný profil.

 Monitorování profilu sledování stavu vysílá aktivity chyby šíření hodnoty záznamů a záznamů instance pracovního postupu. Tento profil se vytvoří tak, že přidáte následující sledovacího profilu pro konfigurační soubor Web.config.

```xml
<<tracking>
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

 Profil, který lze změnit pomocí změny `EtwTrackingParticipant` konfigurace pro následující.

```xml
<behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="HealthMonitoring Tracking Profile"/>
        </behavior>
      </serviceBehaviors>
    </behaviors>
```

#### <a name="to-clean-up-optional"></a>Chcete-li vyčistit (volitelné)

1.  Otevřete Prohlížeč událostí.

2.  Přejděte do **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikace Aplikace serveru**. Klikněte pravým tlačítkem na **analytické** a vyberte **zakázat protokol**.

3.  Přejděte do **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikace Aplikace serveru**. Klikněte pravým tlačítkem na **analytické** a vyberte **vymazat protokol**.

4.  Zvolte **vymazat** možnost pro vymazání událostí.

## <a name="known-issue"></a>Známý problém

> [!NOTE]
>  V prohlížeči událostí, kde může dojít k selhání k dekódování událostí trasování událostí pro Windows je známý problém. Může zobrazit chybová zpráva, která vypadá nějak takto.
>
>  Popis pro ID události \<id > ze zdroje aplikace Microsoft Windows Server – aplikace nebyla nalezena. Součást, která vyvolá tuto událost není nainstalována na místním počítači nebo že je poškozená instalace. Můžete nainstalovat nebo opravit součásti v místním počítači.
>
>  Pokud dojde k této chybě, klikněte na tlačítko Aktualizovat v podokně Akce. Události by měl nyní správně dekódovat.

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`  
  
## <a name="see-also"></a>Viz také:

- [Ukázky AppFabric monitorování](https://go.microsoft.com/fwlink/?LinkId=193959)

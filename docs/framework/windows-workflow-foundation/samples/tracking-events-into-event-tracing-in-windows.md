---
title: "Sledování událostí do událostí trasování v systému Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 03fe4d3805d79188777404de201316441b3f8831
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="tracking-events-into-event-tracing-in-windows"></a>Sledování událostí do událostí trasování v systému Windows
Tento příklad ukazuje, jak povolit [!INCLUDE[wf](../../../../includes/wf-md.md)] sledování v rámci pracovního postupu služby a emitování sledování událostí v trasování událostí pro Windows (ETW). Pro vydávání pracovní postup sledování záznamů do trasování událostí pro Windows, používá ukázku účastník sledování ETW (<xref:System.Activities.Tracking.EtwTrackingParticipant>).  
  
 Pracovní postup v ukázce přijme požadavek, přiřadí vzájemné vstupních dat vstupní proměnné a vrátí vzájemných zpět klientovi. Když jsou vstupní data 0, dělení nulové výjimkou výskytu, která je neošetřená, dojde k přerušení pracovního postupu. S povoleno sledování, je sledovat záznam chyby vygenerované do trasování událostí pro Windows, které mohou pomoci při odstraňování chyba později. Trasování událostí pro Windows Sledování účastník je nakonfigurovaný s profil sledování k odběru sledování záznamů. Profil sledování je definován v souboru Web.config a zadat jako parametr konfigurace sledování účastníkům trasování událostí pro Windows. Trasování událostí pro Windows Sledování účastník je nakonfigurovaný v souboru Web.config služby pracovního postupu a jsou použity pro službu jako chování služby. V této ukázce zobrazit události sledování v protokolu událostí pomocí prohlížeče událostí.  
  
## <a name="workflow-tracking-details"></a>Podrobnosti sledování pracovního postupu  
 [!INCLUDE[wf2](../../../../includes/wf2-md.md)]poskytuje sledování infrastruktury ke sledování provádění instanci pracovního postupu. Modul runtime sledování vytvoří instanci pracovního postupu pro vydávání události související s životního cyklu pracovního postupu, události z aktivit pracovního postupu a vlastních událostí. V následující tabulce jsou primární součásti sledování infrastruktury.  
  
|Součást|Popis|  
|---------------|-----------------|  
|Sledování runtime|Poskytuje infrastrukturu pro vydávání sledování záznamů.|  
|Sledování účastníků|Přistupuje ke sledování záznamů. [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]se dodává s účastníkem sledování, která zapisuje sledování záznamů jako události trasování událostí pro Windows (ETW).|  
|Sledování profilu|Filtrační mechanismus, který umožňuje účastníkem sledování k odběru pro podmnožinu sledování záznamy vygenerované z instance pracovního postupu.|  
  
 V následující tabulce jsou záznamy sledování, které vysílá modulu runtime pracovního postupu.  
  
|Sledování záznamu|Popis|  
|---------------------|-----------------|  
|Záznamy sledování instance pracovního postupu.|Popisuje životní cyklus k instanci pracovního postupu. Například je záznam instance vygenerované při spuštění pracovního postupu nebo dokončení.|  
|Záznamy o sledování stavu aktivity.|Podrobnosti o provádění aktivity. Tyto záznamy označují stav aktivity pracovního postupu, jako je například naplánovaného aktivitu nebo po dokončení aktivity nebo když je vyvolána chybu.|  
|BOOKMARK – obnovení záznamu.|Vygenerované vždy, když je obnoveno záložku v rámci instance pracovního postupu.|  
|Vlastní sledování záznamy.|Autor pracovního postupu můžete vytvořit vlastní sledování záznamů a posílat je v rámci vlastní aktivity.|  
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|Tento záznam je vygenerované při aktivitu plány jiné aktivity.|  
|<xref:System.Activities.Tracking.FaultPropagationRecord>|Tento záznam je vygenerované při šíření chybu z aktivity.|  
|<xref:System.Activities.Tracking.CancelRequestedRecord>|Tento záznam jsou vydávány, když aktivita je zrušeno pomocí jiné aktivity.|  
  
 Sledování účastník odběratel pro podmnožinu záznamy emitovaného sledování pomocí sledování profilů. Profil sledování obsahuje dotazy pro sledování, které umožňují přihlášení k odběru pro typ záznamu konkrétní sledování. Sledování profily mohou být zadané v kódu nebo v konfiguraci.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení EtwTrackingParticipantSample.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Pokud chcete spustit řešení, stisknutím klávesy F5.  
  
     Ve výchozím nastavení služba naslouchá na portu 53797 (http://localhost:53797/SampleWorkflowService.xamlx).  
  
4.  Pomocí [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], otevřete testovacího klienta WCF.  
  
     Testovacího klienta WCF (WcfTestClient.exe) se nachází v \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] instalační složka > \Common7\IDE\ složky.  
  
     Výchozí hodnota [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] instalační složka je C:\Program Files\Microsoft Visual Studio 10.0.  
  
5.  V testu klienta WCF, vyberte **přidat službu** z **souboru** nabídky.  
  
     Přidáte adresa koncového bodu do vstupního pole. Výchozí hodnota je http://localhost:53797/SampleWorkflowService.xamlx.  
  
6.  Otevřete Prohlížeč událostí aplikace.  
  
     Před vyvoláním služby, spusťte Prohlížeč událostí z **spustit** nabídce vyberte možnost **spustit** a zadejte `eventvwr.exe`. Ujistěte se, že v protokolu událostí naslouchá pro sledování události vygenerované ze služby pracovního postupu.  
  
7.  Ve stromovém zobrazení prohlížeče událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, a **Microsoft**. Klikněte pravým tlačítkem na **Microsoft** a vyberte **zobrazení** a potom **zobrazit protokoly pro ladění a** povolit analýzy a protokoly pro ladění  
  
     Ujistěte se, že **zobrazit protokoly pro ladění a** zaškrtnutá možnost.  
  
8.  Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**,  **Aplikace serveru – aplikace**. Klikněte pravým tlačítkem na **analytické** a vyberte **povolit protokol** povolit **analytické** protokolu.  
  
9. Testování služby pomocí testovacího klienta WCF dvojitým kliknutím na soubor `GetData`.  
  
     Tím se otevře `GetData` metoda. Požadavek přijímá jeden parametr a zajišťuje, že hodnota 0, který je výchozí.  
  
     Klikněte na tlačítko **vyvolání**.  
  
10. Pozorovat, jaké události vygenerované z pracovního postupu.  
  
     Přepněte zpět do prohlížeče událostí a přejděte do **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**,  **Aplikace serveru – aplikace**. Klikněte pravým tlačítkem na **analytické** a vyberte **aktualizovat**.  
  
     Pracovní postup události se zobrazí v prohlížeči událostí. Všimněte si, že se zobrazují události spuštění pracovního postupu a že jeden z nich je nezpracovanou výjimku, která odpovídá na chybu v pracovním postupu. Navíc upozorňovací událost nevydává aktivita pracovního postupu, který označuje, že je aktivity vyvolání chybu.  
  
11. Opakujte kroky 9 a 10 se vstupem dat než 0, tak, aby se žádná chyba.  
  
 Sledování profily umožňují přihlásit k odběru událostí, které jsou při změně stavu instance pracovního postupu vygenerované modulem runtime. V závislosti na vašich požadavků na monitorování, můžete vytvořit profil, který je velmi hrubým, který jako odběratel u malého podrobný stav změn v pracovním postupu. Na druhé straně můžete vytvořit profil velmi přesná, jejíž výstup je dostatečně bohaté k rekonstrukci spuštění později. Ukázka ukazuje události vygenerované z modulu runtime pracovního postupu pomocí trasování událostí pro Windows `HealthMonitoring Tracking Profile`, který vysílá malého událostí. Jiný profil, který vysílá další pracovního postupu pro sledování událostí je také součástí souboru Web.config, který je pojmenován `Troubleshooting Tracking Profile`. Když [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] je nainstalovaná, výchozí profil s prázdným názvem je nakonfigurován v souboru Machine.config. Tento profil je používán trasování událostí pro Windows sledování Konfigurace chování, když je zadán žádný název profilu nebo název prázdný profil.  
  
 Sledování profil sledování stavu vysílá záznamy instance pracovního postupu a záznamy šíření selhání aktivity. Tento profil se vytváří přidáním následující profil sledování do konfiguračního souboru Web.config.  
  
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
  
 Profil můžete změnit změnou `EtwTrackingParticipant` konfigurace pro následující.  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="HealthMonitoring Tracking Profile"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
#### <a name="to-clean-up-optional"></a>Vyčistěte (volitelné)  
  
1.  Otevřete Prohlížeč událostí.  
  
2.  Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikace Aplikace serveru**. Klikněte pravým tlačítkem na **analytické** a vyberte **zakázat protokol**.  
  
3.  Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikace Aplikace serveru**. Klikněte pravým tlačítkem na **analytické** a vyberte **vymazat protokol**.  
  
4.  Vyberte **vymazat** možnost Vymazat události.  
  
## <a name="known-issue"></a>Známý problém  
  
> [!NOTE]
>  V prohlížeči událostí, kde může dojít k selhání dekódovat události trasování událostí není známý problém. Může zobrazit chybovou zprávu, která vypadá takto.  
>   
>  Popis k ID události \<id > ze zdroje aplikaci Microsoft Windows Server – aplikace nebyla nalezena. Buď není nainstalována součást, který vyvolává tuto událost v místním počítači nebo je poškozená instalace. Můžete nainstalovat nebo opravit součásti v místním počítači.  
>   
>  Pokud dojde k této chybě, klikněte na tlačítko Aktualizovat v podokně Akce. Události by měl nyní dekódovat správně.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky monitorování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)

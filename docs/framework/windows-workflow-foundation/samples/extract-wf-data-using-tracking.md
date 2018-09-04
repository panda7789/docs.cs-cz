---
title: Extrahování dat WF pomocí sledování
ms.date: 03/30/2017
ms.assetid: e30c68f5-8c6a-495a-bd20-667a4364c68e
ms.openlocfilehash: ef8118df2c5834e32c40760ef31f75660893d89b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501580"
---
# <a name="extract-wf-data-using-tracking"></a>Extrahování dat WF pomocí sledování
Tento příklad ukazuje, jak používat pracovní postup sledování extrahovat z aktivit pracovního postupu proměnné a argumenty. Také ukazuje přidání poznámek k sledování záznamů a extrakce dat datové části v rámci vlastní sledování záznamů. Ukázka používá trasování událostí pro Windows (ETW) účastník sledování extrahovat data z pracovního postupu.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Windows Workflow Foundation (WF) poskytuje sledování získejte lepší informace o spuštění instance pracovního postupu. Modul runtime sledování vysílá pracovního postupu při provádění pracovního postupu pro sledování záznamů. Spolu s pracovní postup sledování záznamů může být extrahována data v rámci instance pracovního postupu z pracovního postupu. Následujícím seznamu jsou uvedeny typy dat, která může být extrahována ze sledování záznamů:  
  
1.  Proměnné pracovního postupu v rámci aktivity a při provádění aktivity sledování záznamů.  
  
     Extrahovat proměnné pracovního postupu, jsou proměnné extrahovaným zadaný v profilu. Proměnné extrahovaným je možné zadat jenom při `ActivityStateQueries`. Následující příklad kódu ukazuje profilu sledování použitou k extrakci proměnné pracovního postupu z aktivity.  
  
    ```xml  
    <activityStateQuery activityName="StockPriceService">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <variables>  
              <variable name="symbol"/>  
         </variables>  
    </activityStateQuery>  
    ```  
  
2.  Argumenty aktivity a stav aktivity sledování záznamů.  
  
     Argumenty definují způsob, jak data toky nebo z aktivity. Argumenty, které mají být extrahovány jsou určeny pomocí <xref:System.Activities.Tracking.ActivityStateQuery>. Následující příklad kódu je sledování profil, který extrahuje `Value` argument.  
  
    ```xml  
    <activityStateQuery activityName="GetStockPrice">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <arguments>  
              <argument name="Value"/>  
         </arguments>  
    </activityStateQuery>  
    ```  
  
3.  Poznámky jsou páry klíč/hodnota, které lze přidat do jakékoli sledování záznam, který je vygenerován.  
  
     Poznámky slouží jako mechanismus pro označení pro sledování záznamů. Poznámky jsou přidány do sledování záznamů prostřednictvím profilu sledování. Poznámky můžete přidat do libovolného typu dotazu sledování pracovního postupu. Následující příklad kódu je sledování profil, který ukazuje, jak mohou být přidány poznámky se záznamem sledování.  
  
    ```xml  
    <workflowInstanceQuery>  
         <states>  
              <state name="Started"/>  
         </states>  
         <annotations>  
              <annotation name="StockPriceWorkflow" value="Begin"/>  
         </annotations>  
    </workflowInstanceQuery>  
    ```  
  
4.  Z uživatelem definované aktivit jsou vydávány vlastní sledování záznamů.  
  
     Vlastní sledování záznamů bude přenášet data datové části definované v rámci této aktivity. Přihlášení k odběru vlastní sledování záznamů v sledování profilu umožňuje extrakce datové části v rámci záznamem sledování. Vlastní sledování záznamů může být extrahována pomocí vlastní <xref:System.Activities.Tracking.TrackingQuery>. Následující příklad kódu je sledování profil, který extrahuje záznamu vlastní sledování spolu s její datové části.  
  
    ```xml  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 Ukázce extrakce proměnné, argumenty, vlastní záznamy a přidání poznámky pomocí profil zadaný v souboru Web.config. Sledování je zapnutá služba pracovního postupu ukázkové tak, že přidáte `<etwTracking>` prvek chování. Následující kód například umožňuje sledování `ExtractWorkflowVariables` profil sledování tracking profile.  
  
```xml  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení WFStockPriceApplication.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte klávesu F5.  
  
     Okno prohlížeče se otevře a zobrazí výpisu adresáře pro aplikaci.  
  
4.  V prohlížeči klikněte na tlačítko StockPriceService.xamlx.  
  
5.  Prohlížeč zobrazí na stránce StockPriceService, který obsahuje místní službě WSDL adresu. Zkopírujte tuto adresu.  
  
     Následující příklad ukazuje adresu místní službě WSDL. `http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  Před vyvoláním služby, spusťte Prohlížeč událostí a ujistěte se, že v protokolu událostí naslouchá ke sledování vyzařováno služby pracovního postupu událostí.  
  
7.  Z **Start** nabídce vyberte možnost **nástroje pro správu** a potom **Prohlížeč událostí**.  
  
8.  Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, a **Microsoft**. Klikněte pravým tlačítkem na **Microsoft** a vyberte **zobrazení** a potom **zobrazit protokoly ladění a analýzu**.  
  
     Ujistěte se, **zobrazit protokoly ladění a analýzu** zaškrtnutá možnost.  
  
9. Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**,  **Aplikace Server-**. Klikněte pravým tlačítkem na **analytické** a vyberte **povolit protokol**.  
  
10. Pomocí [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], otevřete testovací klient WCF.  
  
     Testovací klient WCF (WcfTestClient.exe) se nachází v \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] instalační složka > \Common7\IDE\ složky.  
  
     Výchozí hodnota [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] instalační složka je C:\Program Files\Microsoft Visual Studio 10.0.  
  
11. Testovací klient WCF, vyberte **přidat službu** z **souboru** nabídky.  
  
     Přidáte místní službě WSDL adresu, kterou jste si zkopírovali do vstupního pole.  
  
12. Testovací klient WCF, dvakrát klikněte na panel `GetStockPrice`.  
  
     Tím se otevře `GetStockPrice` metody. Požadavek přijímá jeden parametr. Použijte hodnotu **Contoso**.  
  
13. Klikněte na tlačítko **vyvolat**.  
  
14. Přepněte zpět do prohlížeče událostí a přejděte do **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**,  **Aplikace Server-**. Klikněte pravým tlačítkem na **analytické** a vyberte **aktualizovat**. Pracovní postup události jsou události ID rozsahy 100 199.  
  
     Události obsahují poznámky, proměnné, argumenty a vlastní záznamy sledování, které mohou být zobrazeny v události prohlížeč.  
  
## <a name="cleaning-up-in-the-event-viewer"></a>Čištění v události prohlížeč  
 Analytický kanál v protokolu událostí je možné vymazat události prohlížeč následujícím způsobem.  
  
#### <a name="to-clean-up-optional"></a>Chcete-li vyčistit (volitelné)  
  
1.  Otevřete Prohlížeč událostí.  
  
2.  Přejděte do **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikace Aplikace serveru**. Klikněte pravým tlačítkem na **analytické** a vyberte **zakázat protokol**.  
  
3.  Přejděte do **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikace Aplikace serveru**. Klikněte pravým tlačítkem na **analytické** a vyberte **vymazat protokol**.  
  
     Zvolte **vymazat** možnost pro vymazání událostí.  
  
## <a name="known-issue"></a>Známý problém  
  
> [!NOTE]
>  V prohlížeči událostí, kde může dojít k selhání k dekódování událostí trasování událostí pro Windows je známý problém. Může zobrazit chybová zpráva, která vypadá nějak takto.  
>   
>  `The description for Event ID <id> from source Microsoft-Windows-Application Server-Applications cannot be found. Either the component that raises this event is not installed on your local computer or the installation is corrupted. You can install or repair the component on the local computer.`  
>   
>  Pokud dojde k této chybě, klikněte na tlačítko **aktualizovat** v podokně Akce. Události by měl nyní správně dekódovat.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky AppFabric monitorování](https://go.microsoft.com/fwlink/?LinkId=193959)

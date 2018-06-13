---
title: Extrahovat Data WF pomocí sledování
ms.date: 03/30/2017
ms.assetid: e30c68f5-8c6a-495a-bd20-667a4364c68e
ms.openlocfilehash: 22b147521d4ce0c72fadfb7adc81e05f10ce52b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519870"
---
# <a name="extract-wf-data-using-tracking"></a>Extrahovat Data WF pomocí sledování
Tento příklad znázorňuje způsob použití sledování extrahovat proměnné pracovního postupu a argumenty z aktivit pracovního postupu. Také ukazuje přidání poznámky do sledování záznamů a extrahování dat datové části v rámci vlastní sledování záznamů. Příklad používá účastník sledování trasování událostí pro Windows (ETW) extrahovat data z pracovního postupu.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Windows Workflow Foundation (WF) poskytuje sledování, aby mohl získat přehled o provádění instanci pracovního postupu. Modul runtime sledování vysílá pracovní postup sledování záznamů během spouštění pracovního postupu. Společně s pracovním sledování záznamů můžete extrahovat data v rámci instance pracovního postupu z pracovního postupu. V následujícím seznamu jsou uvedeny typy dat, které mohou být extrahovány z sledování záznamů:  
  
1.  Proměnné pracovního postupu v rámci aktivity a sledování záznamů během provádění aktivity.  
  
     K extrakci proměnné pracovního postupu, jsou proměnné extrahovat zadán v profilu. Proměnné extrahovat lze zadat pouze s `ActivityStateQueries`. Následující příklad kódu ukazuje profil sledování použitou k extrakci proměnné pracovního postupu z aktivity.  
  
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
  
     Argumenty definovat data způsob toky nebo zrušení aktivity. Argumenty, které mají být extrahovány jsou určeny pomocí <xref:System.Activities.Tracking.ActivityStateQuery>. Následující příklad kódu je sledování profil, který extrahuje `Value` argument.  
  
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
  
3.  Poznámky jsou páry klíč/hodnota, které mohou být přidány do jakékoli sledování záznam, který je vygenerované.  
  
     Poznámky sloužit jako označování mechanismus pro sledování záznamů. Poznámky jsou přidány do sledování záznamů prostřednictvím profil sledování. Poznámky můžete přidat do libovolného typu sledování dotazu pracovního postupu. Následující příklad kódu je sledování profil, který ukazuje, jak lze přidat poznámky k záznamu sledování.  
  
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
  
4.  Vlastní sledování záznamy jsou vygenerované z uživatelem definované aktivit.  
  
     Vlastní sledování záznamů přenášet datové části definované v rámci této aktivity. Odběr pro vlastní sledování záznamy v profilu sledování umožňuje extrahování datové části v rámci záznamu sledování. Vlastní sledování záznamy lze extrahovat s vlastní <xref:System.Activities.Tracking.TrackingQuery>. Následující příklad kódu je sledování profil, který extrahuje záznam vlastní sledování spolu s jeho datové části.  
  
    ```xml  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 Ukázka ukazuje extrahování proměnné, argumenty, vlastní záznamy a přidávat poznámky pomocí profil zadaný v souboru Web.config. Je povoleno sledování ukázkový pracovní postup služby přidáním `<etwTracking>` chování elementu. Následující kód například umožňuje sledování `ExtractWorkflowVariables` sledovacího profilu.  
  
```xml  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení WFStockPriceApplication.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Pokud chcete spustit řešení, stisknutím klávesy F5.  
  
     Okno Prohlížeč otevře a ukazuje výpis pro aplikaci adresáře.  
  
4.  V prohlížeči klikněte na tlačítko StockPriceService.xamlx.  
  
5.  Prohlížeč zobrazí stránku StockPriceService, který obsahuje službu místní adresu WSDL. Zkopírujte tuto adresu.  
  
     Následující příklad ukazuje adresu WSDL místní služby. `http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  Před vyvoláním služby, spusťte Prohlížeč událostí a zkontrolujte, zda protokol událostí naslouchá pro sledování události vygenerované ze služby pracovního postupu.  
  
7.  Z **spustit** nabídce vyberte možnost **nástroje pro správu** a potom **Prohlížeč událostí**.  
  
8.  Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, a **Microsoft**. Klikněte pravým tlačítkem na **Microsoft** a vyberte **zobrazení** a potom **zobrazit protokoly pro ladění a**.  
  
     Ujistěte se, že **zobrazit protokoly pro ladění a** zaškrtnutá možnost.  
  
9. Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**,  **Aplikace serveru – aplikace**. Klikněte pravým tlačítkem na **analytické** a vyberte **povolit protokol**.  
  
10. Pomocí [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], otevřete testovacího klienta WCF.  
  
     Testovacího klienta WCF (WcfTestClient.exe) se nachází v \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] instalační složka > \Common7\IDE\ složky.  
  
     Výchozí hodnota [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] instalační složka je C:\Program Files\Microsoft Visual Studio 10.0.  
  
11. V testu klienta WCF, vyberte **přidat službu** z **souboru** nabídky.  
  
     Přidejte místní služba WSDL adresu, kterou jste zkopírovali dříve do vstupního pole.  
  
12. V testu klienta WCF, klikněte dvakrát na `GetStockPrice`.  
  
     Tím se otevře `GetStockPrice` metoda. Požadavek přijímá jeden parametr. Použijte hodnotu **Contoso**.  
  
13. Klikněte na tlačítko **vyvolání**.  
  
14. Přepněte zpět do prohlížeče událostí a přejděte do **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**,  **Aplikace serveru – aplikace**. Klikněte pravým tlačítkem na **analytické** a vyberte **aktualizovat**. Pracovní postup události jsou události ID rozsahy 100 199.  
  
     Události obsahovat poznámky, proměnné, argumentů a vlastní sledování záznamů, které se dají zobrazit události prohlížeč.  
  
## <a name="cleaning-up-in-the-event-viewer"></a>Čištění události prohlížeč  
 Analytické kanál v protokolu událostí může být vyčištěna události prohlížeč pomocí následujícího postupu.  
  
#### <a name="to-clean-up-optional"></a>Vyčistěte (volitelné)  
  
1.  Otevřete Prohlížeč událostí.  
  
2.  Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikace Aplikace serveru**. Klikněte pravým tlačítkem na **analytické** a vyberte **zakázat protokol**.  
  
3.  Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikace Aplikace serveru**. Klikněte pravým tlačítkem na **analytické** a vyberte **vymazat protokol**.  
  
     Vyberte **vymazat** možnost Vymazat události.  
  
## <a name="known-issue"></a>Známý problém  
  
> [!NOTE]
>  V prohlížeči událostí, kde může dojít k selhání dekódovat události trasování událostí není známý problém. Může zobrazit chybovou zprávu, která vypadá takto.  
>   
>  `The description for Event ID <id> from source Microsoft-Windows-Application Server-Applications cannot be found. Either the component that raises this event is not installed on your local computer or the installation is corrupted. You can install or repair the component on the local computer.`  
>   
>  Pokud dojde k této chybě, klikněte na tlačítko **aktualizovat** v podokně Akce. Události by měl nyní dekódovat správně.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky monitorování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)

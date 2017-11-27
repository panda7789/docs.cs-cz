---
title: "Sledování pomocí textového souboru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a2725c34b79b8c9dd05a9f9a071ef52e29527e02
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="tracking-using-a-text-file"></a>Sledování pomocí textového souboru
Tento příklad ukazuje, jak rozšířit sledování v [!INCLUDE[wf](../../../../includes/wf-md.md)] tak, že vytvoříte vlastní sledování účastník. Sledování členové jsou třídy rozhraní .NET Framework, které dostanou záznamy sledování z modulu runtime, jak budou vygenerované. Můžete vytvořit účastník sledování přenos sledování události, které chcete podle toho, která je vyžadována pro váš scénář. Například účastník sledování ETW (trasování událostí pro Windows) k dispozici jako součást [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Sledování účastník v této ukázce zapíše záznamy ve formátu XML do textového souboru.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 K optimalizaci užitečnost a odolnost vaší sledování účastník, musí být vyplněna některé další kroky k správně propojit účastník sledování modulu runtime. Následující tabulka popisuje třídy používané v této ukázce vytvoření sledování člena, který je v souladu s osvědčenými postupy.  
  
|Třída|Popis|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> se používá k definování konfigurační oddíl slouží ke konfiguraci sledování účastník textového souboru. To umožňuje uživatelům zadat cílové umístění souboru protokolu pomocí standardní soubory konfigurace rozhraní .NET Framework.|  
|`TextFileTrackingBehavior`|Chování v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] povolit uživatelům vložit rozšíření do modulu runtime. Toto chování účastník sledování přidá do služby při spuštění služby.|  
|`TextFileTrackingParticipant`|Sledování člena, který přijímá sledování účastníky v době běhu a ukládá je do souboru protokolu ve formátu XML.|  
  
## <a name="behavior-extension-elements-configuration"></a>Konfigurace chování rozšíření elementy  
 Jeden krok je potřebný k použití elementu rozšíření chování výše popsané pomocí rozhraní .NET Framework konfigurační soubory. Následující konfigurace musí být umístěny v konfiguračních souborech, kde má být použita rozšíření.  
  
```xml  
<system.serviceModel>  
    <extensions>  
      <behaviorExtensions>  
        <add name="textFileTracking" type="Microsoft.Samples.TextFileTracking.TextFileTrackingExtensionElement, WFStockPriceApplication, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
…  
  </system.serviceModel>  
```  
  
> [!NOTE]
>  Naleznete v souboru Web.config v ukázce použití kompletní příklad konfigurace elementů rozšíření chování.  
  
## <a name="custom-tracking-records"></a>Vlastní sledování záznamů  
 Soubor GetStockPrices.cs ukazuje, jak vytvořit vlastní sledování záznamy uvnitř <xref:System.Activities.CodeActivity>. Při spuštění ukázky, vyhledejte tento záznam.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení WFStockPriceApplication.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
     Okno Prohlížeč otevře a ukazuje výpis pro aplikaci adresáře.  
  
4.  V prohlížeči klikněte na tlačítko StockPriceService.xamlx.  
  
5.  Prohlížeč zobrazí **StockPriceService** stránky, který obsahuje adresu wsdl místní služby. Zkopírujte tuto adresu.  
  
     Příkladem adresu wsdl místní služby je http://localhost:53797/StockPriceService.xamlx?wsdl.  
  
6.  Pomocí [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], přejděte na vaše [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] složky (%SystemDrive%\Program Files\Microsoft Visual Studio 10.0 je výchozí instalační složku). Vyhledejte Common7\IDE\ podsložky.  
  
7.  Poklikejte na soubor WcfTestClient.exe ke spuštění testovacího klienta WCF.  
  
8.  V testu klienta WCF, vyberte **přidat služby...** z **souboru** nabídky.  
  
9. Vložte adresu URL, které jste právě zkopírovali, do textového pole.  
  
10. Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
11. Testování služby pomocí testovacího klienta WCF.  
  
    1.  V testu klienta WCF, klikněte dvakrát na **GetStockPrice()** pod **IStockPriceService** uzlu.  
  
         **GetStockPrice()** metoda se zobrazí v pravém podokně se jeden parametr.  
  
    2.  Zadejte ve společnosti Contoso jako hodnotu parametru.  
  
    3.  Klikněte na tlačítko **vyvolání**.  
  
12. Viz sledovaných události do souboru protokolu, který je umístěný v adresáři data aplikací v umístění % APPDATA%\trackingRecords.log.  
  
    > [!NOTE]
    >  Data aplikací % je proměnná prostředí, který se přeloží na %SystemDrive%\Users\\< uživatelské jméno\>\AppData\Roaming v [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], nebo Windows Server 2008.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky monitorování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)

---
title: Sledování pomocí textového souboru
ms.date: 03/30/2017
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
ms.openlocfilehash: 19b4d544bc1d1c5bc9ebfa51b4ba28eb82c525d0
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45674595"
---
# <a name="tracking-using-a-text-file"></a>Sledování pomocí textového souboru
Tato ukázka předvádí, jak rozšířit tak, že vytvoříte vlastní sledování účastník sledování ve Windows Workflow Foundation (WF). Sledování účastníci se tříd rozhraní .NET Framework, které přijímají sledování záznamů z modulu runtime, jako jsou emitovány. Můžete vytvořit sledování účastník přenést událostí sledování k libovolným cíl je povinné pro váš scénář. Například je účastník sledování ETW (událost trasování pro Windows) poskytuje jako součást [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Účastník sledování v této ukázce zapíše záznamy ve formátu XML do textového souboru.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 K optimalizaci užitečnost a odolnosti sledování účastník, je třeba provést některé další kroky správně propojí účastník sledování modulu runtime. Následující tabulka popisuje třídy používané k vytvoření účastníkem sledování, která je v souladu s osvědčenými postupy v tomto příkladu.  
  
|Třída|Popis|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> se používá k definování konfiguračního oddílu použít ke konfiguraci sledování účastník textového souboru. To umožňuje uživatelům zadat cíl protokolu pomocí standardní konfigurační soubory rozhraní .NET Framework.|  
|`TextFileTrackingBehavior`|Chování ve službě WCF umožňují uživatelům vložení rozšíření do modulu runtime. Toto chování přidá účastník sledování ve službě při spuštění služby.|  
|`TextFileTrackingParticipant`|Účastník sledování, který přijímá sledování účastníci za běhu a uloží je do souboru protokolu ve formátu XML.|  
  
## <a name="behavior-extension-elements-configuration"></a>Chování rozšíření elementy konfigurace  
 Dalším krokem je nutné použít rozšíření elementu chování výše popsaný pomocí konfiguračních souborů rozhraní .NET Framework. Následující konfigurace musí být umístěn v konfiguračních souborech, ve kterém se má použít rozšíření.  
  
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
>  Naleznete v souboru Web.config v ukázce Úplný příklad použití chování rozšíření elementů konfigurace.  
  
## <a name="custom-tracking-records"></a>Vlastní sledování záznamů  
 Soubor GetStockPrices.cs ukazuje, jak vytvořit vlastní záznamy sledování v rámci <xref:System.Activities.CodeActivity>. Vyhledejte tento záznam při spuštění ukázky.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení WFStockPriceApplication.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
     Okno prohlížeče se otevře a zobrazí výpisu adresáře pro aplikaci.  
  
4.  V prohlížeči klikněte na tlačítko StockPriceService.xamlx.  
  
5.  Prohlížeč zobrazí **StockPriceService** stránky, který obsahuje adresu místní služby wsdl. Zkopírujte tuto adresu.  
  
     Příkladem adresy místní služby wsdl je http://localhost:53797/StockPriceService.xamlx?wsdl.  
  
6.  Pomocí [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], přejděte na stránku vaší [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] složky (výchozí instalační složka je %SystemDrive%\Program Files\Microsoft Visual Studio 10.0). Vyhledejte podsložku Common7\IDE\.  
  
7.  Poklikejte na soubor WcfTestClient.exe a spustit klienta testu WCF.  
  
8.  Testovací klient WCF, vyberte **přidat službu...** z **souboru** nabídky.  
  
9. Vložte adresu URL, které jste zkopírovali do textového pole.  
  
10. Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
11. Test pomocí testovacího klienta WCF.  
  
    1.  Testovací klient WCF, dvakrát klikněte na panel **GetStockPrice()** pod **IStockPriceService** uzlu.  
  
         **GetStockPrice()** metoda se zobrazí v pravém podokně s jedním parametrem.  
  
    2.  Zadejte ve společnosti Contoso jako hodnotu parametru.  
  
    3.  Klikněte na tlačítko **vyvolat**.  
  
12. Zobrazte sledované události do souboru protokolu, který je umístěný v adresáři data vaší aplikace v umístění % APPDATA%\trackingRecords.log.  
  
    > [!NOTE]
    >  % APPDATA % je proměnná prostředí, který se přeloží %SystemDrive%\Users\\< uživatelské jméno\>\AppData\Roaming v [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], nebo Windows Server 2008.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky AppFabric monitorování](https://go.microsoft.com/fwlink/?LinkId=193959)

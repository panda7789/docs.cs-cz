---
title: "Rozšířené filtry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d81590f-e036-4f96-824a-4a187f462764
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 357b57bb39ca31b48d21cb83209a72d0b3d12a62
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-filters"></a>Rozšířené filtry
Tento příklad znázorňuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] směrování služby. Služba směrování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] komponenty, která usnadňuje do aplikace zahrnout směrovač podle obsahu. Tato ukázka přizpůsobuje standardní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázka kalkulačku komunikovat pomocí služby směrování. Tento příklad ukazuje, jak definovat na základě obsahu směrování logiku prostřednictvím filtry zpráv a zpráva filtru tabulky.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedFilters`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 V následující tabulce jsou filtry zpráv, které jsou přidány do tabulky filtru zpráv služby směrování.  
  
|Filtr|Pravidlo|Priorita|  
|------------|----------|--------------|  
|Pokud (mají záhlaví)|Zaokrouhlení|2|  
|Pokud (vám ukázal, na Ep2)|Regulární|1|  
|Pokud (vám ukázal, se Adresa2)|Zaokrouhlení|1|  
|Pokud (RoundRobin1)|Regulární|0|  
|Pokud (RoundRobin2)|Zaokrouhlení|0|  
  
 Filtry zpráv a zpráva filtru tabulky lze vytvořit a konfigurovat pomocí kódu nebo v konfiguračním souboru aplikace. Tato ukázka můžete najít filtry zpráv a zpráva filtru tabulky definované prostřednictvím kódu v souboru RoutingService\routing.cs nebo definována v konfiguračním souboru aplikace v souboru RoutingService\App.config. Následující odstavce popisují, jak vytváří filtry zpráv a zpráva filtru tabulky pro tato ukázka prostřednictvím kódu.  
  
 První, <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> hledá vlastní hlavičky. Všimněte si, že <xref:System.ServiceModel.WSHttpBinding> výsledků ve verzi obálky pomocí protokolu SOAP 1.2, takže příkaz jazyka XPath je definována pro používání oboru názvů SOAP 1.2. Správce výchozí obor názvů pro <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s již definuje předponu pro obor názvů SOAP 1.2, /s12, který může být použit. Výchozí obor názvů správce nemá vlastní obor názvů, který klient používá k definování skutečné hodnoty hlavičky, takže tuto předponu musí být definován. Všechny zprávy, které se zobrazí s touto hlavičkou odpovídat tomuto filtru.  
  
```  
XPathMessageContext namespaceManager = new XPathMessageContext();  
namespaceManager.AddNamespace("custom", "http://my.custom.namespace/");  
  
XPathMessageFilter xpathFilter = new XPathMessageFilter("/s12:Envelope/s12:Header/custom:RoundingCalculator = 1", namespaceManager);  
```  
  
 Druhý filtr je <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, který odpovídá jakékoli zprávy, která byla obdržena ve `calculatorEndpoint`. Název koncového bodu je definován, když je vytvořen objekt koncový bod služby.  
  
```  
EndpointNameMessageFilter endpointNameFilter = new EndpointNameMessageFilter("calculatorEndpoint");  
```  
  
 Je třetí filtr <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>. To odpovídá všechny zprávy, které vám ukázal, na koncový bod s adresou, která odpovídá předpona adresy (nebo části front) zadaný. V tomto příkladu je předpona adresy definovaný jako "http://localhost/routingservice/router/rounding/". To znamená, že tento filtr se splní všechny příchozí zprávy, které jsou určeny k "http://localhost/routingservice/router/rounding/ *". V takovém případě je zprávy, které se zobrazí v koncovém bodě zaokrouhlení kalkulačky, který má na adresu "http://localhost/routingservice/router/rounding/calculator".  
  
```  
PrefixEndpointAddressMessageFilter prefixAddressFilter = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://localhost/routingservice/router/rounding/"));  
```  
  
 Poslední dva filtry zpráv jsou vlastní <xref:System.ServiceModel.Dispatcher.MessageFilter>s. V tomto příkladu se používá filtr zpráv "RoundRobin". Tento filtr zpráv se vytvoří v zadaný soubor RoutingService\RoundRobinMessageFilter.cs. Tyto filtry, pokud je nastavena na stejnou skupinu alternativní mezi sestav, aby odpovídaly zprávy a, že nechcete, tak, aby pouze jeden z nich odpovídá `true` najednou.  
  
```  
RoundRobinMessageFilter roundRobinFilter1 = new RoundRobinMessageFilter("group1");  
  
RoundRobinMessageFilter roundRobinFilter2 = new RoundRobinMessageFilter("group1");  
```  
  
 Potom všechny tyto zprávy jsou přidány do <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>. Při tom priority zadávají k ovlivnění pořadí, ve kterém tabulku filtru zpráv provede filtry. Tím vyšší je priorita, tím dříve filtr je provedeno; nižší prioritu, novější spouští filtr. Proto filtr důležitostí 2 spouští před filtrem v priority 1. Výchozí úroveň priority, pokud není zadaný žádný je 0. Tabulku filtru zpráv zpracuje všechny filtry na úrovni Zadaná priorita před přesunutím do další nejnižší úroveň priority. Pokud je nalezena shoda s konkrétní prioritou, pak tabulku filtru zpráv nebude dále pokusu o vyhledání shody další nižší prioritou.  
  
> [!NOTE]
>  Když tento příklad ukazuje způsob použití priority filtru zpráv, obecně je další původce a lepší návrhu k návrhu a konfigurovat filtry tak, aby nevyžadují stanovení priorit, aby správně fungoval.  
  
 První filtr, který se má přidat je filtr XPath a jeho priorita je nastavena na hodnotu 2. Toto je první filtr zpráv, které provádí. Pokud najde vlastní hlavičky, bez ohledu na to, co by bylo výsledky ostatní filtry, zpráva se směruje na koncový bod zaokrouhlení kalkulačky.  
  
 Priorita 1 přidá dva filtry. Opakujte tyto spustí jenom v případě filtr XPath důležitostí 2 neodpovídá zprávy. Dva různé způsoby, jak určit, kdy byla zpráva řešit při jeho vám ukázal, se zobrazí tyto dva filtry. Vzhledem k tomu, že dva filtry efektivně zkontrolujte, zda zpráva dorazila po uplynutí v některém z dva koncové body, jejich spuštěním na stejné úrovni s prioritou protože udělají ne pomocí obou vrátit `true` ve stejnou dobu.  
  
 Nakonec s prioritou 0 (nejnižší priorita) spustit RoundRobin zpráva filtry. Protože filtry jsou nakonfigurované se stejným názvem skupiny, pouze jedna z nich odpovídá najednou. Protože všechny zprávy s vlastní hlavička již byla směrován a všechny ty řešit konkrétní virtualizované koncových bodů, jsou zprávy zpracovávaných filtry zpráv RoundRobin jen zprávy, které byla provedena na výchozí koncový bod směrovač bez vlastní hlavička. Protože tyto zprávy přepínač na zprávu pro každé volání, polovinu operace přejděte ke koncovému bodu regulární kalkulačky a druhá polovina přejděte ke koncovému bodu zaokrouhlení kalkulačky.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete AdvancedFilters.sln.  
  
2.  Chcete-li otevřít **Průzkumníku řešení**, vyberte **Průzkumníku řešení** z **zobrazení** nabídky.  
  
3.  Stiskněte klávesu F5 nebo CTRL + SHIFT + B v [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].  
  
    1.  Pokud chcete automaticky spouštěné projekty potřebné po stisknutí klávesy F5, klikněte pravým tlačítkem na řešení a vyberte **vlastnosti**. Vyberte **spouštěný projekt** pod uzlem **společných vlastností** v levém podokně. Vyberte **více projektů po spuštění** přepínač a nastavte všechny projekty, které chcete mít **spustit** akce.  
  
    2.  Pokud vytvoříte projekt pomocí kombinace kláves CTRL + SHIFT + B, je nutné spustit následující aplikace:  
  
        1.  Klient kalkulačky (. / CalculatorClient/bin/client.exe)  
  
        2.  Službu kalkulačky (. / CalculatorService/bin/service.exe)  
  
        3.  Směrovací služba provádí kalkulačky (. / RoundingCalcService/bin/service.exe)  
  
        4.  RoutingService (. / RoutingService/bin/RoutingService.exe)  
  
4.  V okně konzoly klienta kalkulačky stisknutím klávesy ENTER spusťte službu klienta. Klient vrátí seznam koncových bodů cílové lze vybírat.  
  
5.  Zvolte cílový koncový bod zadáním jeho odpovídající písmeno a stiskněte klávesu ENTER.  
  
6.  V dalším kroku klienta zeptá, pokud chcete přidat vlastní hlavičku. Stiskněte klávesu Y Ano nebo N pro žádný, stiskněte klávesu ENTER.  
  
7.  V závislosti na vybrané možnosti, které jste nastavili měli byste vidět jiné výstupy.  
  
    1.  Toto je výstup vrácena, pokud jste přidali vlastní záhlaví zprávy.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    2.  Toto je výstup vrácena, pokud jste si zvolili koncový bod zaokrouhlení kalkulačky bez vlastní hlavičky.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    3.  Toto je výstup vrácena, pokud jste si zvolili koncový bod regulární kalkulačky bez vlastní hlavičky.  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68. 46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
    4.  Toto je výstup vrácena, pokud jste si zvolili směrovače výchozí koncový bod bez vlastní hlavičky.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.14285714285714  
        ```  
  
8.  Službu kalkulačky a službu kalkulačky zaokrouhlení vytiskne také protokolu operací vyvolat do svých příslušných konzoly windows.  
  
9. V okně konzoly klienta zadejte `quit` a stiskněte klávesu ENTER ukončíte.  
  
10. Stisknutím klávesy ENTER v oknech konzoly služby ukončení služby.  
  
## <a name="configurable-via-code-or-appconfig"></a>Konfigurovat pomocí kódu nebo App.config  
 Ukázka lodě, umožňují použít soubor App.config k definování chování směrovače. Můžete taky změnit název souboru RoutingService\App.config na jinou tak, aby nebyla rozpoznána a zrušte komentář u volání metody `ConfigureRouterViaCode()` v RoutingService\routing.cs. Buď metoda výsledkem stejné chování z směrovači.  
  
### <a name="scenario"></a>Scénář  
 Tento příklad znázorňuje směrovač, který funguje jako směrovač založená na obsahu umožňuje více typů nebo implementace služby mají být exponovány prostřednictvím jeden koncový bod.  
  
### <a name="real-world-scenario"></a>Scénář skutečných  
 Contoso chce k virtualizaci všech svých služeb vystavit pouze jeden koncový bod veřejně přes která nabízejí přístup k několika různých typů služeb. V takovém případě využívají službu směrování na základě obsahu směrování možnosti k určení, kde by měly být odeslány příchozí požadavky.  
  
## <a name="see-also"></a>Viz také  
 [Ukázky trvalosti a hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)

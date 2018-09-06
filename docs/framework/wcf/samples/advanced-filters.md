---
title: Rozšířené filtry
ms.date: 03/30/2017
ms.assetid: 8d81590f-e036-4f96-824a-4a187f462764
ms.openlocfilehash: 7022384e8abe93f4276eec48785b3243ed926438
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042592"
---
# <a name="advanced-filters"></a>Rozšířené filtry
Tato ukázka předvádí, směrovací služba Windows Communication Foundation (WCF). Směrovací služba je komponenta WCF, který umožňuje snadno do aplikace zahrnout směrovač založené na obsahu. Tato ukázka se přizpůsobí standardní vzorek Kalkulačka WCF na komunikaci pomocí směrovací službou. Tento příklad ukazuje, jak definovat směrování logiky založené na obsahu prostřednictvím filtry zpráv a tabulky filtru zpráv.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedFilters`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 V následující tabulce jsou uvedeny filtry zpráv, které jsou přidány do tabulky filtru zpráva směrovací služby.  
  
|Filtr|Pravidlo|Priorita|  
|------------|----------|--------------|  
|Pokud (má hlavičky)|Zaokrouhlení|2|  
|Pokud (se zobrazila na Ep2)|Pravidelné|1|  
|Pokud (zobrazila s Adresa2)|Zaokrouhlení|1|  
|Pokud (RoundRobin1)|Pravidelné|0|  
|Pokud (RoundRobin2)|Zaokrouhlení|0|  
  
 Filtry zpráv a zpráva filtru tabulky lze vytvořit a nakonfigurovat prostřednictvím kódu nebo konfiguračního souboru aplikace. Pro tuto ukázku můžete najít filtry zpráv a tabulky filtru zprávy prostřednictvím kódu v souboru RoutingService\routing.cs definované nebo definované v konfiguračním souboru aplikace v souboru RoutingService\App.config. Následující odstavce popisují způsob vytvoření filtry zpráv a zpráva filtr tabulky pro tuto ukázku prostřednictvím kódu.  
  
 Nejprve je potřeba <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> hledá vlastní hlavičce. Všimněte si, že <xref:System.ServiceModel.WSHttpBinding> výsledků ve verzi obálky pomocí protokolu SOAP 1.2, takže příkaz jazyka XPath je definována používání oboru názvů SOAP 1.2. Výchozí obor názvů správce pro <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s již definuje předponu pro obor názvů SOAP 1.2, /s12, který můžete použít. Výchozí obor názvů Správce však nemá vlastní obor názvů, který klient používá k definování skutečné hodnoty hlavičky, aby tuto předponu musí být definovaný. Všechny zprávy, které se zobrazí s touto hlavičkou odpovídat tomuto filtru.  
  
```  
XPathMessageContext namespaceManager = new XPathMessageContext();  
namespaceManager.AddNamespace("custom", "http://my.custom.namespace/");  
  
XPathMessageFilter xpathFilter = new XPathMessageFilter("/s12:Envelope/s12:Header/custom:RoundingCalculator = 1", namespaceManager);  
```  
  
 Je druhý filtr <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, který odpovídá jakékoli zprávy, který uživateli přišel na `calculatorEndpoint`. Název koncového bodu je definován, když je vytvořen objekt koncový bod služby.  
  
```  
EndpointNameMessageFilter endpointNameFilter = new EndpointNameMessageFilter("calculatorEndpoint");  
```  
  
 Je třetí filtr <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>. To odpovídá jakékoli zprávy, která se zobrazila v koncovém bodu s adresou, která odpovídá předponu adresy (nebo přední části), za předpokladu. V tomto příkladu je definována předpona adresy jako "http://localhost/routingservice/router/rounding/". To znamená, že příchozí zprávy, které jsou určeny k "http://localhost/routingservice/router/rounding/*" odpovídajících tomuto filtru. V takovém případě je zprávy, které se zobrazí v koncovém bodě zaokrouhlení kalkulačky, který má na adresu "http://localhost/routingservice/router/rounding/calculator".  
  
```  
PrefixEndpointAddressMessageFilter prefixAddressFilter = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://localhost/routingservice/router/rounding/"));  
```  
  
 Poslední dva filtry zpráv jsou vlastní <xref:System.ServiceModel.Dispatcher.MessageFilter>s. V tomto příkladu se používá filtr zpráv "RoundRobin". Tomuto filtru zprávy se vytvoří v zadané RoutingService\RoundRobinMessageFilter.cs souboru. Tyto filtry, pokud je nastavena na stejnou skupinu střídavě vytváření sestav, které musí odpovídat zprávy a že tomu tak není, tak, aby pouze jeden z nich odpovídá `true` najednou.  
  
```  
RoundRobinMessageFilter roundRobinFilter1 = new RoundRobinMessageFilter("group1");  
  
RoundRobinMessageFilter roundRobinFilter2 = new RoundRobinMessageFilter("group1");  
```  
  
 Potom všechny tyto zprávy jsou přidány do <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>. Přitom priority jsou určeny k ovlivnění pořadí, ve kterém tabulky filtru zprávy spustí filtry. Vyšší je priorita, tím dříve filtru je spuštěn; Čím nižší prioritu, pozdější spuštění filtru. Proto filtr s prioritou 2 spouští před filtrem s prioritou 1. Výchozí úroveň priority, pokud není zadaný žádný je 0. Tabulka Filtr zpráv spustí všechny filtry na úrovni uvedenou prioritou daný před přechodem na další úroveň nejnižší prioritu. Pokud je nalezena shoda s konkrétní prioritou, pak tabulky filtru zprávy nepokračuje pokusu o nalezení shody další nižší prioritou.  
  
> [!NOTE]
>  Přestože tento příklad ukazuje způsob použití priority filtru zpráv, obecně je výkonnější a lepší návrh na návrhu a konfigurace filtry tak, aby nevyžadují stanovení priority správně fungovat.  
  
 Filtr XPath je první filtr, aby se přidají a jeho priorita nastavena na 2. Toto je první filtr zpráv, který se spustí. Pokud najde vlastní hlavičky, bez ohledu na to, co by být výsledky další filtry, zpráva se směruje do koncového bodu zaokrouhlení kalkulačku.  
  
 S prioritou 1 jsou přidány dva filtry. Znovu tyto spustí jenom v případě filtr XPath s prioritou 2 neodpovídá zprávu. Zobrazit tyto dva filtry k určení, kde byl vyřešen zprávy, když jsme si ukázali, a dvěma různými způsoby. Protože dva filtry efektivně zkontrolujte, zda byla zpráva doručena dva koncové body, bylo možné spouštět na stejné úrovni priority protože ne obě možnosti současně vrátit `true` ve stejnou dobu.  
  
 A konečně s prioritou 0 (nejnižší prioritu), spusťte RoundRobin zprávy filtry. Protože jsou nakonfigurované filtry se stejným názvem skupiny, pouze jeden z nich odpovídá najednou. Protože byl směrovány všechny zprávy s vlastní hlavičky, všechny ty řešit ke konkrétním koncovým bodům virtualizované, zprávy zpracovává filtry RoundRobin zpráv jsou jen zprávy, které byly určena výchozí koncový bod směrovače bez vlastní záhlaví. Protože tyto zprávy se přepnout na zprávu pro každé volání, polovinu operací přejděte ke koncovému bodu regulární kalkulačky a ta druhá půlka přejděte ke koncovému bodu zaokrouhlení kalkulačky.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete AdvancedFilters.sln.  
  
2.  Chcete-li otevřít **Průzkumníku řešení**vyberte **Průzkumníku řešení** z **zobrazení** nabídky.  
  
3.  V sadě Visual Studio stiskněte klávesu F5 nebo CTRL + SHIFT + B.  
  
    1.  Pokud chcete automaticky spouštět nezbytné projektů při stisknutí klávesy F5, klikněte pravým tlačítkem na řešení a vyberte **vlastnosti**. Vyberte **spouštěný projekt** pod uzlem **společné vlastnosti** v levém podokně. Vyberte **více projektů po spuštění** přepínač a nastavte všechny projekty, které mají mít **Start** akce.  
  
    2.  Pokud při vytváření projektu pomocí kombinace kláves CTRL + SHIFT + B, je nutné spustit v následujících aplikacích:  
  
        1.  Kalkulačka klienta (. / CalculatorClient/bin/client.exe)  
  
        2.  Kalkulačka služby (. / CalculatorService/bin/service.exe)  
  
        3.  Směrovací služba kalkulačky (. / RoundingCalcService/bin/service.exe)  
  
        4.  Službu RoutingService (. / RoutingService/bin/RoutingService.exe)  
  
4.  V okně konzoly klienta Kalkulačka stisknutím klávesy ENTER klienta. Klient vrátí seznam hodnot cílové koncové body lze vybírat.  
  
5.  Zvolte cílový koncový bod tak, že zadáte jeho odpovídající písmeno a stiskněte klávesu ENTER.  
  
6.  V dalším kroku klienta vás zeptá, zda chcete přidat vlastní hlavičku. Stiskněte klávesu A Ano nebo Ne, N stiskněte klávesu ENTER.  
  
7.  V závislosti na výběrech, které jste provedli měli byste vidět jiné výstupy.  
  
    1.  Zde je, že výstup vrátí, pokud jste přidali vlastní hlavičky zprávy.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    2.  Zde je, že výstup vrátí, pokud jste zvolili koncový bod zaokrouhlení Kalkulačka bez vlastní hlavičku.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    3.  Zde je, že výstup vrátí, pokud jste zvolili koncový bod regulární Kalkulačka bez vlastní hlavičku.  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68. 46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
    4.  Zde je, že výstup vrátí, pokud jste zvolili směrovač výchozí koncový bod bez vlastní hlavičku.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.14285714285714  
        ```  
  
8.  Kalkulačka služba a služba zaokrouhlení Kalkulačka také vytiskne protokolu operací vyvolat a jejich odpovídajících konzoly windows.  
  
9. V okně konzoly klienta zadejte `quit` a stisknutím klávesy ENTER ukončete.  
  
10. Stisknutím klávesy ENTER v oknech konzoly služby k ukončení služby.  
  
## <a name="configurable-via-code-or-appconfig"></a>Konfigurovat pomocí kódu nebo souboru App.config  
 Ukázka lodí umožňují definovat chování ve směrovači použít soubor App.config. Můžete také změnit název souboru RoutingService\App.config na jiný tak, aby nebyl rozpoznán a zrušte komentář u volání metod, které `ConfigureRouterViaCode()` v RoutingService\routing.cs. Některé z metod má za následek stejné chování směrovače.  
  
### <a name="scenario"></a>Scénář  
 Tato ukázka předvádí, směrovač fungujícího jako směrovač založené na obsahu umožňuje více typů nebo implementaci služeb zpřístupní prostřednictvím jeden koncový bod.  
  
### <a name="real-world-scenario"></a>Reálné scénáře  
 Contoso chce, aby se k virtualizaci všech svých služeb vystavit pouze jeden koncový bod veřejně přes který nabízejí přístup k více různých typů služeb. V tomto případě využívat Služba směrování založené na obsahu směrování schopnosti určit, které by měla být odeslána příchozí požadavky.  
  
## <a name="see-also"></a>Viz také  
 [Hostování AppFabric a ukázky trvalosti](https://go.microsoft.com/fwlink/?LinkId=193961)

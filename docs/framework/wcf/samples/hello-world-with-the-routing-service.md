---
title: Hello World se směrovací službou
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 37d2eaffa1ca5a4cce27c4950d00987828a61196
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006600"
---
# <a name="hello-world-with-the-routing-service"></a>Hello World se směrovací službou
Tato ukázka předvádí, směrovací služba Windows Communication Foundation (WCF). Směrovací služba je komponenta WCF, která umožňuje snadno do aplikace zahrnout směrovač založené na obsahu. Tato ukázka se přizpůsobí standardní kalkulačky Ukázky WCF na komunikaci pomocí služby směrování. V této ukázce je Kalkulačka klient nakonfigurovaný pro odesílání zpráv do koncového bodu určeného směrovače. Směrovací služba je nakonfigurována tak, aby přijímal všechny zprávy odeslané do ní a předávají do koncového bodu, který odpovídá službu kalkulačky. Proto jsou zpráv odeslaných z klienta přijatých směrovač a přesměrovala do aktuální Kalkulačka služby. Zprávy ze služby Kalkulačka odesílají zpět do směrovač, který je zase předá zpět do klienta kalkulačky.

### <a name="to-use-this-sample"></a>Pro fungování této ukázky

1. Using Visual Studio 2012, open HelloRoutingService.sln.

2. Stiskněte klávesu F5 nebo CTRL + SHIFT + B.

    > [!NOTE]
    >  Pokud stisknete klávesu F5, spustí se automaticky Kalkulačka klienta. Pokud stisknete CTRL + SHIFT + B (sestavení), je nutné spustit následující aplikace sami.
    >
    > 1. Kalkulačka klienta (./CalculatorClient/bin/client.exe
    > 2. Kalkulačka služby (. / CalculatorService/bin/service.exe)
    > 3. Služba směrování (. / RoutingService/bin/RoutingService.exe)

3. Stisknutím klávesy ENTER klienta.

     Byste měli vidět následující výstup:

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a>Konfigurovat pomocí kódu nebo souboru App.Config
 Ukázka lodí umožňují definovat chování ve směrovači použít soubor App.config. Můžete také změnit název souboru App.config na něco jiného, tak, aby nebyl rozpoznán a zrušte komentář u volání metod, které ConfigureRouterViaCode(). Některé z metod má za následek stejné chování směrovače.

### <a name="scenario"></a>Scénář
 Tato ukázka předvádí, směrovač, který funguje jako základní zprávy odeslané. Směrovací služba funguje jako uzel transparentní proxy server nakonfigurovaný tak, aby předávání zpráv přímo do předkonfigurovaného sadu cílové koncové body.

### <a name="real-world-scenario"></a>Reálné scénáře
 Contoso chce zvýšit flexibilitu, které se má v pojmenování, adresy, konfigurace a zabezpečení svých služeb. Provedete to tak, že umístit základní zprávy odeslané před jejich služby tak, aby fungoval jako veřejný internetový koncový bod. To umožňuje umístit další zabezpečení před jejich skutečné služby a usnadňují implementace řešení nebo Správa verzí služby škálované později.

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a>Viz také:

- [Hostování AppFabric a ukázky trvalosti](https://go.microsoft.com/fwlink/?LinkId=193961)

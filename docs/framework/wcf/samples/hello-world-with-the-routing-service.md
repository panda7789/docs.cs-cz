---
title: Hello World se směrovací službou
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 86a2981e8b861da9d5ccf0a34fe037f3ef419aab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183637"
---
# <a name="hello-world-with-the-routing-service"></a>Hello World se směrovací službou
Tato ukázka ukazuje službu směrování WCF (Windows Communication Foundation). Služba Směrování je součást WCF, která usnadňuje zahrnutí směrovače založeného na obsahu do aplikace. Tento příklad přizpůsobí standardní WCF ukázka kalkulačky komunikovat pomocí služby směrování. V této ukázce je klient kalkulačky nakonfigurován tak, aby odesílá zprávy do koncového bodu vystaveného směrovačem. Služba směrování je nakonfigurována tak, aby přijímala všechny zprávy, které jí byly odeslány, a přeposílala je do koncového bodu, který odpovídá službě Kalkulačka. Tak zprávy odeslané od klienta jsou přijímány routerem a přesměrovány na skutečnou službu Kalkulačka. Zprávy ze služby Kalkulačka jsou odesílány zpět na router, který je zase předá zpět klientovi Kalkulačky.

### <a name="to-use-this-sample"></a>Chcete-li použít tento vzorek

1. Pomocí Visual Studia 2012 otevřete HelloRoutingService.sln.

2. Stiskněte klávesu F5 nebo CTRL+SHIFT+B.

    > [!NOTE]
    > Pokud stisknete klávesu F5, klient kalkulačky se automaticky spustí. Pokud stisknete kombinaci kláves CTRL+SHIFT+B (sestavení), musíte začít sledovat aplikace sami.
    >
    > 1. Klient kalkulačky (./CalculatorClient/bin/client.exe
    > 2. Kalkulačka služby (./CalculatorService/bin/service.exe)
    > 3. Služba směrování (./RoutingService/bin/RoutingService.exe)

3. Stisknutím klávesy ENTER spusťte klienta.

     Měl by se zobrazit následující výstup:

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a>Konfigurovatelné pomocí kódu nebo App.Config
 Ukázkové informace jsou konfigurované tak, aby k definování chování směrovače používaly soubor App.config. Můžete také změnit název souboru App.config na něco jiného tak, aby nebyl rozpoznán a odkomentovat volání metody ConfigureRouterViaCode(). Obě metody má za následek stejné chování ze směrovače.

### <a name="scenario"></a>Scénář
 Tato ukázka ukazuje směrovač, který funguje jako základní čerpadlo zpráv. Služba směrování funguje jako transparentní uzel proxy nakonfigurovaný tak, aby předával zprávy přímo předem nakonfigurované sadě cílových koncových bodů.

### <a name="real-world-scenario"></a>Scénář reálného světa
 Společnost Contoso chce zvýšit flexibilitu, kterou má při pojmenovávání, adresování, konfiguraci a zabezpečení svých služeb. Chcete-li to provést, umístí základní čerpadlo zpráv před své služby, aby působily jako veřejný koncový bod. To jim umožňuje umístit další zabezpečení před jejich skutečné služby a usnadnit implementaci škálovaných řešení nebo služby správy verzí později.

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a>Viz také

- [Ukázky hostování a perzistence appfabric](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))

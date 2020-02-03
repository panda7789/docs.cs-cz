---
title: Hello World se směrovací službou
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: ae0615c8cf2fa33f3bb363f77c0d06440b6afc13
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743719"
---
# <a name="hello-world-with-the-routing-service"></a>Hello World se směrovací službou
Tato ukázka demonstruje směrovací službu Windows Communication Foundation (WCF). Směrovací služba je součást WCF, která usnadňuje zahrnutí směrovače založeného na obsahu do vaší aplikace. Tato ukázka přizpůsobuje standardní ukázku kalkulačky WCF pro komunikaci pomocí směrovací služby. V této ukázce je klient kalkulačky nakonfigurovaný tak, aby odesílal zprávy na koncový bod vystavený směrovačem. Směrovací služba je nakonfigurovaná tak, aby přijímala všechny odeslané zprávy, a přesměruje je do koncového bodu, který odpovídá službě kalkulačky. Tedy zprávy odesílané z klienta obdrží směrovač a znovu přesměrovány do skutečné služby kalkulačky. Zprávy ze služby kalkulačky se odesílají zpět do směrovače, který je zase předává do klienta kalkulačky.

### <a name="to-use-this-sample"></a>Použití této ukázky

1. Pomocí sady Visual Studio 2012 otevřete HelloRoutingService. sln.

2. Stiskněte klávesu F5 nebo CTRL + SHIFT + B.

    > [!NOTE]
    > Když stisknete klávesu F5, spustí se automaticky klient kalkulačky. Stisknete-li kombinaci kláves CTRL + SHIFT + B (sestavení), je nutné spustit následující aplikace sami.
    >
    > 1. Klient kalkulačky (./CalculatorClient/bin/client.exe
    > 2. Služba kalkulačky (./CalculatorService/bin/service.exe)
    > 3. Směrovací služba (./RoutingService/bin/RoutingService.exe)

3. Stisknutím klávesy ENTER spusťte klienta.

     Měl by se zobrazit následující výstup:

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a>Konfigurovatelné prostřednictvím kódu nebo souboru App. config
 Ukázková plavidla konfigurovaná pro použití souboru App. config k definování chování směrovače. Můžete také změnit název souboru App. config na něco jiného, aby nebyl rozpoznán a odkomentovat volání metody ConfigureRouterViaCode (). Kterákoli z metod má za následek stejné chování jako směrovač.

### <a name="scenario"></a>Scénář
 Tato ukázka demonstruje směrovač, který působí jako základní čerpadlo zpráv. Směrovací služba funguje jako transparentní proxy uzel, který je nakonfigurován tak, aby předával zprávy přímo do předem nakonfigurované sady cílových koncových bodů.

### <a name="real-world-scenario"></a>Scénář reálného světa
 Společnost Contoso chce zvýšit flexibilitu, kterou má při pojmenování, adresování, konfiguraci a zabezpečení svých služeb. K tomu přistupují základní čerpadlo zpráv před svými službami, aby fungovaly jako veřejný koncový bod. Díky tomu mohou být před svými skutečnými službami zavedeny další zabezpečení a snadněji implementují škálovaná řešení nebo správu verzí služeb později.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a>Viz také

- [Hostování technologie AppFabric a ukázky trvalosti](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))

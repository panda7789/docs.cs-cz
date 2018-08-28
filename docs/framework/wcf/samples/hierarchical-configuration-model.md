---
title: Model hierarchické konfigurace
ms.date: 03/30/2017
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
ms.openlocfilehash: ce0bc69424495594e0ee9c6b950a5fa9c4d5f993
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2018
ms.locfileid: "43000098"
---
# <a name="hierarchical-configuration-model"></a>Model hierarchické konfigurace
Tento příklad ukazuje, jak implementovat hierarchii konfigurační soubory pro služby. Profil také ukazuje, jak vazby, chování služby a chování koncového bodu se dědí z vyšší úrovně v hierarchii.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Jednou z funkcí vyvinutý pro službu WCF v [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] je zvýšení model hierarchické konfigurace. Příkladem model hierarchické konfigurace může být definováno Machine.config -> Rootweb.config -> souboru Web.config. V [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], tyto vazby a chování, které jsou definovány v vyšší úrovně v hierarchii konfigurace se přidají do vaší služby bez explicitní konfigurace. Tato ukázka předvádí, jak je možné pro zjednodušení konfigurace služby pomocí konfigurační prvky, které jsou definované na úrovni aplikace nebo počítače.  
  
 Tento příklad se skládá z devíti služeb, definovaný ve třech úrovních hierarchie. `Service1` je v kořenovém adresáři. `Service2` a `Service3` dědit výchozími prvky z `Service1`. `Service4`, `Service5`, `Service6` a `Service7` jsou definované na třetí úrovni hierarchie dědění výchozími prvky z `Service3`. Nakonec `Service10` a `Service11` jsou na čtvrtou úrovně v hierarchii.  
  
 Implementovat všechny služby `IDesc` kontraktu. Tady je definice `IDesc` rozhraní, které zobrazuje metod v tomto rozhraní zpřístupněny. `IDesc` Rozhraní je definováno v souborech Service1.cs.  
  
```csharp  
// Define a service contract  
[ServiceContract(Namespace="http://Microsoft.Samples.ConfigHierarchicalModel")]  
public interface IDesc  
{  
    [OperationContract]  
    List<string> ListEndpoints();  
    [OperationContract]  
    List<string> ListServiceBehaviors();  
    [OperationContract]  
    List<string> ListEndpointBehaviors();  
}  
```  
  
 Implementace těchto metod prostřednictvím služeb je jednoduché. `ListEndpoints` Iteruje přes všechny koncové body služby a vrátí seznam všech koncových bodů, které má služba. `ListServiceBehaviors` Iteruje přes všechny chování, které jsou přidány do služby a vrátí seznam všech chování služby související se službou. `ListEndpointBehaviors` chová podobným způsobem jako `ListServiceBehaviors`, ale místo toho vrátí seznam chování koncového bodu.  
  
 Tato implementace umožňuje vystavuje klienta vědět, kolik koncových bodů služby a které chování služby a chování koncového bodu se přidaly do služby. Klienta, která je implementovaná jako součást vzorku přidá odkaz na službu pro všechny služby v řešení a zobrazuje tyto prvky pro každé z nich služeb.  
  
## <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
#### <a name="to-run-the-client"></a>A spusťte tak klienta  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor ConfigHierarchicalModel.sln.  
  
2.  Klientský projekt ještě nemáte nastavené jako počáteční projekt, postupujte podle těchto kroků.  
  
    1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na řešení a pak vyberte **vlastnosti**.  
  
    2.  V **společné vlastnosti**vyberte **spouštěný projekt**a potom klikněte na tlačítko **jeden spouštěný projekt**.  
  
    3.  Z **jeden spouštěný projekt** rozevíracího seznamu, vyberte **klienta**.  
  
    4.  Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
3.  Chcete-li ukázku sestavit, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
4.  Pokud chcete spustit klienta, stiskněte Ctrl + F5.  
  
> [!NOTE]
>  Pokud tyto kroky nefungují, ujistěte se, že vaše prostředí je správně nastavený, pomocí následujících kroků:  
>   
> 1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
> 2.  Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](building-the-samples.md).  
> 3.  Spusťte ukázku v jedné nebo více konfigurací počítače, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky správy AppFabric](http://go.microsoft.com/fwlink/?LinkId=193960)

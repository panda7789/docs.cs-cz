---
title: Model hierarchické konfigurace
ms.date: 03/30/2017
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
ms.openlocfilehash: 233a8d4ba36835ab26e0c4a8cd044cf60d497a0b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806627"
---
# <a name="hierarchical-configuration-model"></a>Model hierarchické konfigurace
Tento příklad znázorňuje implementaci hierarchie konfigurační soubory pro služby. Také ukazuje, jak vazby, chování služby a chování koncový bod se dědí z vyšší úrovně v hierarchii.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Jedna z funkcí vytvořených pro WCF v [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] vylepšením ve model hierarchické konfigurace. Příkladem hierarchické konfigurace modelu může být definováno Machine.config -> Rootweb.config -> souboru Web.config. V [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], tyto vazby a chování, které jsou definovány v horní úrovně v hierarchii konfigurace se přidají k vašim službám s žádné explicitní konfigurací. Tento příklad ukazuje, jak je možné ke zjednodušení konfigurace služby podle konfigurace – elementy definované na počítači nebo na úrovni aplikace.  
  
 Tato ukázka obsahuje devět služby, které jsou definované v tři úrovně hierarchie. `Service1` je v kořenovém adresáři. `Service2` a `Service3` dědění výchozí elementy ze `Service1`. `Service4`, `Service5`, `Service6` a `Service7` jsou definovány na třetí úrovni v hierarchii, dědění výchozí elementy ze `Service3`. Nakonec `Service10` a `Service11` jsou čtvrtý úrovně v hierarchii.  
  
 Všechny služby implementovat `IDesc` kontrakt. Toto je definice `IDesc` rozhraní, které zobrazuje metody v tomto rozhraní. `IDesc` Rozhraní je definováno v Service1.cs.  
  
```  
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
  
 Implementace tyto metody službami je jednoduchá. `ListEndpoints` iteruje všechny koncové body služby a vrátí seznam všech koncových bodů, které má služba. `ListServiceBehaviors` iteruje všechny chování přidali do služby a vrátí seznam všech chování služby spojené s touto službou. `ListEndpointBehaviors` chová podobným způsobem jako pro `ListServiceBehaviors`, ale místo toho vrátí seznam chování koncový bod.  
  
 Tato implementace umožňuje klientovi vědět, kolik koncových bodů služby je vystavení a které chování služby a koncového bodu chování přidané do služby. Klientovi, který byl implementován jako součást ukázka přidá odkaz na službu ke všem službám v řešení a zobrazuje tyto prvky pro každé z nich služeb.  
  
## <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
#### <a name="to-run-the-client"></a>Spuštění klienta  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor ConfigHierarchicalModel.sln.  
  
2.  Projektu klienta nebude již nastavena jako spuštění projektu, postupujte podle těchto kroků.  
  
    1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na řešení a pak vyberte **vlastnosti**.  
  
    2.  V **společných vlastností**, vyberte **spouštěný projekt**a potom klikněte na **jeden projekt po spuštění**.  
  
    3.  Z **jeden projekt po spuštění** rozevíracího seznamu, vyberte **klienta**.  
  
    4.  Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
3.  Chcete-li sestavit ukázku, stiskněte CTRL + SHIFT + B.  
  
4.  Spuštění klienta, stiskněte Ctrl + F5.  
  
> [!NOTE]
>  Pokud tyto kroky nefungují, ujistěte se, že vaše prostředí správně nastavený, pomocí následujících kroků.  
>   
>  1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
> 2.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
> 3.  Spustit ukázku v jedné nebo více konfigurací počítače, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky správy AppFabric](http://go.microsoft.com/fwlink/?LinkId=193960)

---
title: Datové vazby v klientovi Windows Forms
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: 38991390f2d0dd272b8d07041b61e6cf16db0cae
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="data-binding-in-a-windows-forms-client"></a>Datové vazby v klientovi Windows Forms
Tento příklad znázorňuje způsob vytvoření vazby na data vrácená službou Windows Communication Foundation (WCF) v aplikaci Windows Forms.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto článku.  
  
 Tento příklad znázorňuje služba, která implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi. Ukázka se skládá z klienta aplikace Windows Forms (.exe) a služby WCF hostované Internetové informační služby (IIS).  
  
 Kontrakt je definována `IWeatherService` rozhraní, která zpřístupňuje operace s názvem `GetWeatherData`. Tato operace přijímá pole města a vrátí pole `WeatherData` objekty, které představují maximální a minimální prognózy teploty pro města.  
  
 Datové vazby v klientovi v aplikaci Windows Forms dojde. A `DataGridView` je definována v Návrháři formulářů Windows, což je grafické znázornění dat. Zprostředkovatel s názvem `BindingSource` se také vytvoří. Zdroj dat `BindingSource` je nastaven na data pole vrácené službou. Účelem `BindingSource` je poskytnout úroveň dereference mezi data a data zobrazení. Všechny interakce s daty, jako je například navigace, řazení, filtrování a aktualizace, se provádí pomocí volání `BindingSource` součásti. K provedení vazby dat k `DataGridView`, `datasource` z `DataGridView` pak nastavena na `BindingSource` objektu. Všechna data vrácená ze služby WCF se následně zobrazí graficky uživateli.  Pokaždé, když uživatel klikne na tlačítko, vrácená data se automaticky aktualizuje v vázaného na data `DataGridView`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
  
## <a name="see-also"></a>Viz také

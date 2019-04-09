---
title: Datové vazby v klientovi Windows Forms
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: e3f4134544076bc7e8d21da67172551f6f64c16c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167086"
---
# <a name="data-binding-in-a-windows-forms-client"></a>Datové vazby v klientovi Windows Forms
Tento příklad ukazuje, jak svázat s daty vrácenými službou Windows Communication Foundation (WCF) v aplikaci Windows Forms.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto článku.  
  
 V této ukázce je služba, která implementuje kontrakt, který definuje vzor komunikace požadavek odpověď. Ukázka se skládá z klientské aplikace Windows Forms (.exe) a služby WCF hostované v Internetové informační služby (IIS).  
  
 Smlouva je definován `IWeatherService` rozhraní, které uvádí operace s názvem `GetWeatherData`. Tato operace přijímá pole města a vrátí pole `WeatherData` objekty, které představují vysoké a nízké předpokládaných teploty pro město.  
  
 Nastane, datové vazby v klientovi v aplikaci Windows Forms. A `DataGridView` je definován v Návrháři formulářů Windows, což je grafická reprezentace data. Zprostředkovatel s názvem `BindingSource` se vytvoří také. Zdroj dat `BindingSource` nastavená na pole dat vrácených službou. Účelem `BindingSource` je zajistit určitou úroveň dereference mezi daty a data zobrazení. Všechny interakce s daty, jako je například navigace, řazení, filtrování a aktualizace, se provádí pomocí volání `BindingSource` komponenty. K provedení vazby dat k `DataGridView`, `datasource` z `DataGridView` je nastaven na `BindingSource` objektu. Všechna data vrácená ze služby WCF se následně zobrazí graficky uživateli.  Pokaždé, když uživatel klikne na tlačítko, vrácená data se automaticky aktualizuje v vázaného na data `DataGridView`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  

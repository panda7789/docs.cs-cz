---
title: Datové vazby v klientovi Windows Forms
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: 5a21721536542d2c338dfdad444e128087a18f57
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953564"
---
# <a name="data-binding-in-a-windows-forms-client"></a>Datové vazby v klientovi Windows Forms
Tento příklad ukazuje, jak vytvořit propojení s daty vrácenými službou Windows Communication Foundation (WCF) v model Windows Forms aplikaci.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto článku.  
  
 Tato ukázka demonstruje službu, která implementuje kontrakt definující způsob komunikace požadavek-odpověď. Ukázka se skládá z klientské model Windows Forms aplikace (. exe) a služby WCF hostované službou Internetová informační služba (IIS).  
  
 Kontrakt je definován `IWeatherService` rozhraním, které zveřejňuje operaci s názvem `GetWeatherData`. Tato operace přijme pole měst a vrátí pole `WeatherData` objektů, které reprezentují vysokou a nízkou předpokládanou teplotu pro město.  
  
 Datová vazba probíhá na klientovi v aplikaci model Windows Forms. A `DataGridView` je definován v Návrháři model Windows Forms, což je grafické znázornění dat. Vytvoří se také zprostředkovatel `BindingSource` s názvem. Zdroj `BindingSource` dat je nastaven na datové pole vrácené službou. Účelem `BindingSource` je poskytnout vrstvu indirekce mezi daty a zobrazením dat. Veškerá interakce s daty, jako je navigace, řazení, filtrování a aktualizace, se provádí s voláním `BindingSource` komponenty. Chcete-li provést datovou `DataGridView`vazbu na `datasource` ,, `DataGridView` a pak nastavte na `BindingSource` objekt. Všechna data vrácená ze služby WCF se pak graficky zobrazují pro uživatele.  Pokaždé, když uživatel klikne na tlačítko, vrácená data se automaticky aktualizují v datové vazbě `DataGridView`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  

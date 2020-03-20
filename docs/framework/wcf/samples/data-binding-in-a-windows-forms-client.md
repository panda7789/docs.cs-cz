---
title: Datové vazby v klientovi Windows Forms
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: d538e8a525f8d07e9ac9f57d4b10119907602d90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145043"
---
# <a name="data-binding-in-a-windows-forms-client"></a>Datové vazby v klientovi Windows Forms
Tato ukázka ukazuje, jak vázat na data vrácená službou WCF (Windows Communication Foundation) v aplikaci Windows Forms.  
  
> [!NOTE]
> Postup instalace a sestavení pokyny pro tuto ukázku jsou umístěny na konci tohoto článku.  
  
 Tato ukázka ukazuje službu, která implementuje smlouvu, která definuje vzor komunikace požadavek odpověď. Ukázka se skládá z klientské aplikace Windows Forms (.exe) a služby WCF hostované Internetovou informační službou (IIS).  
  
 Kontrakt je definován `IWeatherService` rozhraním, které zveřejňuje `GetWeatherData`operaci s názvem . Tato operace přijme pole měst a vrátí `WeatherData` pole objektů, které představují vysokou a nízkou předpokládanou teplotu pro město.  
  
 K datové vazbě dochází na straně klienta v aplikaci Windows Forms. A `DataGridView` je definována v návrháři windows forms, což je grafické znázornění dat. Je také `BindingSource` vytvořen zprostředkovatel s názvem. Zdroj dat `BindingSource` je nastaven na datové pole vrácené službou. Účelem `BindingSource` je poskytnout vrstvu dereference mezi daty a zobrazení dat. Veškerá interakce s daty, jako je navigace, řazení, filtrování a aktualizace, `BindingSource` se provádí pomocí volání komponenty. Chcete-li provést `DataGridView`datové `datasource` vazby `DataGridView` na , `BindingSource` je pak nastavena na objekt. Všechna data vrácená ze služby WCF se pak graficky zobrazí uživateli.  Pokaždé, když uživatel klepne na tlačítko, vrácená data `DataGridView`se automaticky aktualizují v datové vazbě .  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  

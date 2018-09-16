---
title: Ukázka kompenzovatelná aktivita
ms.date: 03/30/2017
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
ms.openlocfilehash: 3bf1d120cd700830a98f53495f7e9989ffec73db
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45678253"
---
# <a name="compensable-activity-sample"></a>Ukázka kompenzovatelná aktivita
Tato ukázka předvádí, jak používat `CompensableActivity` aktivity k definování práce, která musí být provedeno pro danou akci během normálního provádění a práci, kterou je potřeba udělat, aby se nahradit tuto akci v případě potřeby později.  První část vzorek ukazuje, jak kompenzovatelná pracovní jednotky je možné definovat ve Windows Workflow Foundation (WF) pomocí `CompensableActivity` aktivity a jak jsou provedeny v úspěšného spuštění.  Druhá část vzorek ukazuje, jak stejné jednotky kompenzovatelná pracovní automaticky postará o kompenzaci při dosažení neočekávané události a zrušení instance pracovního postupu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Pomocí sady Visual Studio 2010, otevřete CompensableActivity.sln.  
  
2.  Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.  
  
3.  Stisknutím klávesy F5 spusťte aplikaci.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`
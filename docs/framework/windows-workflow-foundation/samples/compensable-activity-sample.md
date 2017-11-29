---
title: "Ukázka compensable aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b8d7fb5650a8927016e0deebc07a68a8145496db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="compensable-activity-sample"></a>Ukázka compensable aktivity
Tento příklad znázorňuje způsob použití `CompensableActivity` aktivity k definování práce, kterou je třeba udělat pro danou akci během normálního spouštění a práci, kterou je potřeba provést odpovídajícím způsobem této akce v případě potřeby později.  První část vzorku ukazuje, jak lze definovat compensable pracovní jednotky v [!INCLUDE[wf](../../../../includes/wf-md.md)] pomocí `CompensableActivity` aktivity a jak jsou spouštěny v spuštění úspěšné.  Druhá část vzorku ukazuje, jak funkce stejné compensable pracovních jednotek automaticky postará o kompenzaci když je dosaženo neočekávané události a zrušení instance pracovního postupu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Pomocí sady Visual Studio 2010, otevřete CompensableActivity.sln.  
  
2.  Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.  
  
3.  Spusťte aplikaci stisknutím klávesy F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`  
  
## <a name="see-also"></a>Viz také

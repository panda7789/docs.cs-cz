---
title: "Ukázka vlastních kompenzace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4ace7d38a456bb9d7f5dd59776b9ae5843b7b651
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="custom-compensation-sample"></a>Ukázka vlastních kompenzace
Tento příklad ukazuje způsob použití <xref:System.Activities.Statements.CompensableActivity> a její obslužnou rutinu kompenzace k definování vlastní kompenzace logiku. Scénář modelován v této ukázce je agentura pronájem vůz.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Kroky simulated jsou:  
  
1.  Žádosti uživatelů vůz pronájem uvozovky pro dané datum.  
  
2.  Budou kontaktovány tři vůz společnosti a jsou dostupné tři uvozovky.  
  
3.  Uživatel vybere jednu nabídku vůz a pokračuje k seřazení s platební karty.  
  
4.  Aplikace zruší další dva vůz uvozovky.  
  
5.  Aplikace účtuje poplatek služby, který je nevratný pro neprémiové účty Pokud zrušení stane 10 dní nebo méně před datem rezervace.  
  
6.  Aplikace účtuje poplatek pronájem vůz.  
  
7.  Aplikace čeká na datum rezervace nebo dokud zákazník se rozhodli zrušit rezervace, nastane dříve.  
  
8.  Pokud zákazník zruší rezervace, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> kompenzace vlastní logiky spouští podle následujícího postupu:  
  
    1.  Pokud zákazník má účet neprémiové a je menší než 10 dní před datem rezervace, pak je stále účtovat poplatek služby; aplikace, jinak hodnota náhrad poplatek služby.  
  
    2.  Zbytek compensable aktivity (vůz pořadí + vůz pořadí poplatek) jsou spouštěny podle logiky kompenzace výchozí, což je odpovídajícím způsobem v obráceném pořadí spouštění.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete CustomCompensation.sln řešení. Je umístěn v adresáři \WF\Basic\Compensation\CustomCompensation.  
  
2.  Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
3.  Stisknutím kombinace kláves CTRL + F5 a spusťte aplikaci.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`
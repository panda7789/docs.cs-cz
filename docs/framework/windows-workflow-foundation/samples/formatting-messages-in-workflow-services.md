---
title: "Formátování zprávy v služeb pracovních postupů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 726ce98f3fe11bbc3cd13d90cdae335c0741efe6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="formatting-messages-in-workflow-services"></a>Formátování zprávy v služeb pracovních postupů
Tento příklad ukazuje, jak jiného uživatele je možné použít typy v zasílání zpráv aktivity (WF služby). Ukázka služby je služba schválení jednoduché náklady a zveřejňuje tří typů operací. `ApproveExpense`datový typ smlouvy trvá a ukazuje, jak používat známé typy. Vrátí operaci `true` nebo `false` založenou na velikosti náklady. `ApprovePO`Typ třídy XmlSerializer provede a vrátí `true` nebo `false` založenou na velikosti náklady.`ApprovedVendor` načte typ kontrakt zprávy a vrátí `true` nebo `false` dodavatele je v seznamu schválených dodavatelů nebo pokud požadavek pochází z finančního oddělení (finančního oddělení můžete použít jakéhokoli dodavatele).  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Načtení projektu řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a sestavte projekt.  
  
2.  Nejprve spusťte službu, vygenerovaných \FormatterService\bin\debug\ [základní adresář řešení]  
  
3.  Druhý spusťte klientskou aplikaci vygenerovaných \FormatterClient\bin\debug [základní adresář řešení].  
  
4.  Klient zavolá tří typů operací ve službě a zobrazí výsledky. Po dokončení stiskněte klávesu ENTER ukončíte klienta a pak službu.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`
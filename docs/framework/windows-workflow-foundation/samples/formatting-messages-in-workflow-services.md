---
title: Formátování zprávy v služeb pracovních postupů
ms.date: 03/30/2017
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
ms.openlocfilehash: eac9f7042dbcbd31f9a8c7d5e56c7b7d2ab62156
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513783"
---
# <a name="formatting-messages-in-workflow-services"></a>Formátování zprávy v služeb pracovních postupů
Tento příklad ukazuje, jak jiného uživatele je možné použít typy v zasílání zpráv aktivity (WF služby). Ukázka služby je služba schválení jednoduché náklady a zveřejňuje tří typů operací. `ApproveExpense` datový typ smlouvy trvá a ukazuje, jak používat známé typy. Vrátí operaci `true` nebo `false` založenou na velikosti náklady. `ApprovePO` Typ třídy XmlSerializer provede a vrátí `true` nebo `false` založenou na velikosti náklady.`ApprovedVendor` načte typ kontrakt zprávy a vrátí `true` nebo `false` dodavatele je v seznamu schválených dodavatelů nebo pokud požadavek pochází z finančního oddělení (finančního oddělení můžete použít jakéhokoli dodavatele).  
  
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
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`
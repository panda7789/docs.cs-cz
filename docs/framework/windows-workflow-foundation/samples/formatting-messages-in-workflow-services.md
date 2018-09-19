---
title: Formátování zpráv ve službách pracovních postupů
ms.date: 03/30/2017
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
ms.openlocfilehash: eb9a6b3a83a28154dc968bd4c1c41d34028bdd41
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003032"
---
# <a name="formatting-messages-in-workflow-services"></a>Formátování zpráv ve službách pracovních postupů
Tento příklad ukazuje, jak různé uživatelské typy mohou být použity v zasílání zpráv aktivity (WF služby). Ukázka service je služba schválení jednoduché výdajů a zpřístupňuje tří operací. `ApproveExpense` přijímá typ kontraktu dat a ukazuje způsob použití známých typů. Operace vrátí `true` nebo `false` na základě doby, výdajů. `ApprovePO` Typ XmlSerializer, který přijímá a vrací `true` nebo `false` na základě doby, výdajů.`ApprovedVendor` Typ kontraktu zprávy přijímá a vrací `true` nebo `false` Pokud dodavatel je v seznamu schválených dodavatelů nebo pokud žádost pochází z finančního oddělení (finančního oddělení můžete použít libovolného dodavatele).  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Načítání řešení projektu v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a sestavte projekt.  
  
2.  První spuštění služby, vygenerované v \FormatterService\bin\debug\ [základní adresář řešení]  
  
3.  Za druhé spuštění klientské aplikace vygenerované v \FormatterClient\bin\debug [základní adresář řešení].  
  
4.  Klient volá tří typů operací ve službě a zobrazí výsledky. Jakmile budete hotovi, stisknutím klávesy ENTER ukončete klienta a pak službu.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`
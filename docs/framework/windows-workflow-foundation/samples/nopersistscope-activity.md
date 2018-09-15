---
title: Aktivita NoPersistScope
ms.date: 03/30/2017
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
ms.openlocfilehash: 6543756594b6734aec39bf22c5ab6215605341b1
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45649546"
---
# <a name="nopersistscope-activity"></a>Aktivita NoPersistScope
Tento příklad ukazuje, jak pracovat s neserializovatelná a uvolnitelné stav v rámci pracovního postupu. Je důležité, že pracovní postupy se nepokoušejte se zachovat neserializovatelná stavu a je také důležité kvůli uvolnitelné objekty na vyčištění po se používají v pracovním postupu.  
  
## <a name="demonstrates"></a>Demonstruje  
 `NoPersistScope` vlastní aktivity a návrháře.  
  
## <a name="using-the-nopersistzone-activity"></a>Použití aktivity NoPersistZone  
 Po spuštění ukázkového pracovního postupu, volá se, vlastní aktivita `CreateTextWriter` vytvoří objekt typu <xref:System.IO.TextWriter> a uloží jej do proměnné pracovního postupu. <xref:System.IO.TextWriter> je <xref:System.IDisposable> objektu. To <xref:System.IO.TextWriter>, používá k zápisu do souboru s názvem "out.txt' v adresáři, ve kterém běží vzorku, který je nakonfigurován <xref:System.Activities.Statements.WriteLine> aktivitu jako jeho vypisuje jakýkoli text, který zadáte v konzole.  
  
 Echo logiky běží v rámci `NoPersistScope` aktivity (kód, pro který je také součástí této ukázce), které brání je trvalá pracovního postupu. Pokud zadáte `unload` konzole, pokusí zachovat instance pracovního postupu hostitele ale tato operace vyprší časový limit, protože pracovní postup pořád v rámci `NoPersistScope`. Pracovní postup také využívá vlastní aktivity volá `Dispose` k uvolnění <xref:System.IO.TextWriter> objekt po dokončení pracovního postupu se jeho použití. `Dispose` Aktivity je umístěn v rámci <xref:System.Activities.Statements.TryCatch.Finally%2A> bloku <xref:System.Activities.Statements.TryCatch> aktivity, ve kterém <xref:System.IO.TextWriter> proměnná je deklarovaná k zajištění, že poběží i v případě, že výjimky se budou objevovat během provádění bloku Try.  
  
 Můžete zadat `exit` k dokončení instance pracovního postupu a ukončit program.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete řešení NoPersistZone.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B nebo vyberte **sestavit řešení** z **sestavení** nabídky.  
  
3.  Po sestavení byla úspěšná, stiskněte klávesu F5 nebo vyberte **spustit ladění** z **ladění** nabídky také můžete stisknutím kláves CTRL + F5 nebo vyberte **spustit bez ladění** z **Ladění** nabídky spustit bez ladění.  
  
#### <a name="to-cleanup-optional"></a>Vyčistit (volitelné)  
  
1.  Pokud chcete odebrat Store instanci SQL, spusťte Cleanup.cmd.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`
---
title: NoPersistScope aktivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f0dae84428f079dc3efb0c7ee620fa8c6ff87a8f
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="nopersistscope-activity"></a>NoPersistScope aktivity
Tento příklad ukazuje, jak k manipulaci s neserializovatelných a na jedno použití stavu v pracovním postupu. Je důležité, aby pracovní postupy Nepokoušejte se zachovat neserializovatelných stavu a je také důležité pro uvolnitelné objekty, které chcete vymazat, jakmile se používají v pracovním postupu.  
  
## <a name="demonstrates"></a>Demonstruje  
 `NoPersistScope`vlastní aktivity a návrháři.  
  
## <a name="using-the-nopersistzone-activity"></a>Pomocí aktivity NoPersistZone  
 Pokud ukázkový pracovní postup běží, vlastní aktivity volat `CreateTextWriter` vytvoří objekt typu <xref:System.IO.TextWriter> a ukládá je do proměnné pracovního postupu. <xref:System.IO.TextWriter>je <xref:System.IDisposable> objektu. To <xref:System.IO.TextWriter>, je používána k zápisu do souboru s názvem 'out.txt' v adresáři, ve kterém běží ukázku, která je nakonfigurována <xref:System.Activities.Statements.WriteLine> aktivitu jako ho vrátí jakýkoli text, kterou zadáte v konzole.  
  
 Echo logiku běží v rámci `NoPersistScope` aktivity (kód, pro který je také součástí této ukázce), což zabraňuje pracovního postupu byly trvalé. Pokud zadáte v `unload` v konzole, hostitel pokusí uložit instanci pracovního postupu, ale vyprší tuto operaci, protože pracovní postup pořád v rámci `NoPersistScope`. Pracovní postup také využívá vlastní aktivity volá `Dispose` k uvolnění <xref:System.IO.TextWriter> objektu až po dokončení pracovního postupu pomocí ho. `Dispose` Aktivity je umístěn v rámci <xref:System.Activities.Statements.TryCatch.Finally%2A> blokovat z <xref:System.Activities.Statements.TryCatch> činnosti, ve kterých <xref:System.IO.TextWriter> proměnné je deklarovaná zajistit, aby byl spouštěn i v případě, že k během provádění bloku Try by mělo dojít k výjimce.  
  
 Můžete zadat v `exit` dokončit k instanci pracovního postupu a ukončení programu.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete řešení NoPersistZone.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B nebo vyberte **sestavit řešení** z **sestavení** nabídky.  
  
3.  Po sestavení proběhla úspěšně, stiskněte klávesu F5, nebo vyberte **spustit ladění** z **ladění** nabídky můžete alternativně stiskněte klávesy CTRL + F5 nebo vybrat **spustit bez ladění** z **Ladění** nabídku spustit bez ladění.  
  
#### <a name="to-cleanup-optional"></a>Pro čištění (volitelné)  
  
1.  Chcete-li odebrat úložiště Instance SQL, spusťte Cleanup.cmd.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`
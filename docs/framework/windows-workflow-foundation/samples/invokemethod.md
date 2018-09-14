---
title: InvokeMethod
ms.date: 03/30/2017
ms.assetid: 04988eb3-65f8-456d-b1bd-509f5d05a57c
ms.openlocfilehash: 861e0cf160aec9814abcf8c27c37ce13a5d88b2a
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "44778613"
---
# <a name="invokemethod"></a>InvokeMethod
Tento příklad ukazuje různé způsoby použití <xref:System.Activities.Statements.InvokeMethod> aktivity k vyvolání metody dané třídy.  
  
 Metoda patří do třídy a představuje omezením sadu operací. <xref:System.Activities.Statements.InvokeMethod> Aktivity vám dává možnost volání metod na objekty nebo typy, předat parametry a načtení návratové hodnoty. Metody lze vyvolat synchronně nebo asynchronně.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Tento příklad používá <xref:System.Activities.Statements.InvokeMethod> aktivita k provedení následujících scénářů:  
  
1.  Vyvolejte metodu instance bez parametrů.  
  
2.  Vyvolat metodu instance se dvěma parametry (<xref:System.String> a <xref:System.Int32>).  
  
3.  Vyvolat metodu instance se dvěma parametry (<xref:System.String> a <xref:System.Int32>) a pole parametrů typu <xref:System.String>[].  
  
4.  Vyvolat metodu instance se dvěma parametry typu <xref:System.Int32> a výsledek typu <xref:System.Int32>. V tomto scénáři je výsledná hodnota vázán na proměnnou a použít v jiné aktivitě. Zobrazí se v konzole pomocí <xref:System.Activities.Statements.WriteLine> aktivity.  
  
5.  Volání statické metody se dvěma parametry typu <xref:System.String> a <xref:System.Int32>.  
  
6.  Vyvolat metodu instance s jeden parametr obecného typu <xref:System.String>.  
  
7.  Volání statické metody se dvěma parametry obecného typu <xref:System.String> a <xref:System.Int32>.  
  
8.  Vyvolat metodu instance, která má jeden parametr předaný prostřednictvím odkazu typu <xref:System.String>. V tomto scénáři vazbu parametru odkazu na proměnnou (`outParam`) a použít v jiné aktivitě. Zobrazí se v konzole pomocí <xref:System.Activities.Statements.WriteLine> aktivity.  
  
9. Vyvolejte metodu asynchronní instance.  
  
10. Vyvolání dva různé způsoby ve stejné instanci objektu pomocí dvou <xref:System.Activities.Statements.InvokeMethod> aktivity.  
  
11. Store hodnotu v instanci objektu.  
  
12. Načtení hodnoty z instance objektu.  
  
## <a name="to-use-this-sample"></a>Pro fungování této ukázky  
 Tato ukázka je k dispozici ve dvou verzích. První verzi tento příklad ukazuje použití <xref:System.Activities.Statements.InvokeMethod> prostřednictvím kódu C# kód, pomocí programovacího modelu Windows Workflow Foundation (WF) a nachází se ve složce CodedWorkflow\CS. Druhá verze ukazuje použití <xref:System.Activities.Statements.InvokeMethod> pomocí XAML a nachází se ve složce DesignerWorkflow\CS.  
  
#### <a name="to-run-the-coded-workflow-sample"></a>Ke spuštění ukázky programové pracovního postupu  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení InvokeMethodUsage.sln ve složce CodedWorkflow\CS.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
#### <a name="to-run-the-designer-workflow-sample"></a>Ke spuštění ukázky Návrháře pracovního postupu  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení InvokeMethodUsage.sln ve složce DesignerWorkflow\CS.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`
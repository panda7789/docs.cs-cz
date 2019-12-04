---
title: Vytvoření a spuštění instance pracovního postupu
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: d895cfa9e924ecf4d1571cf67f1c1e7069e25da5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715194"
---
# <a name="creating-and-running-a-workflow-instance"></a>Vytvoření a spuštění instance pracovního postupu

V této ukázce se dozvíte, jak spustit instanci pracovního postupu. Ukazuje, jak ho spustit synchronně a asynchronně.

## <a name="demonstrates"></a>Demonstruje

<xref:System.Activities.WorkflowInvoker><xref:System.Activities.WorkflowApplication>.

## <a name="discussion"></a>Účely

První část ukázky používá <xref:System.Activities.WorkflowInvoker.Invoke%2A>. Toto je nejzákladnější způsob, jak spustit pracovní postup. Pracovní postupy spouštěné pomocí <xref:System.Activities.WorkflowInvoker.Invoke%2A> jsou spouštěny synchronně.

Druhá část ukázky používá třídu <xref:System.Activities.WorkflowApplication>. <xref:System.Activities.WorkflowApplication> vám umožní mít větší kontrolu nad každou instancí, včetně možnosti pracovat se spuštěným pracovním postupem a spustit pracovní postup asynchronně.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a>Viz také:

- [Použití WorkflowInvoker a WorkflowApplication](../using-workflowinvoker-and-workflowapplication.md)

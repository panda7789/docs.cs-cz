---
title: Vytvoření a spuštění instance pracovního postupu
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: fe00ebec8d81e77ff982a36419f1b0a988fcd4ab
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016051"
---
# <a name="creating-and-running-a-workflow-instance"></a>Vytvoření a spuštění instance pracovního postupu

V této ukázce se dozvíte, jak spustit instanci pracovního postupu. Ukazuje, jak ho spustit synchronně a asynchronně.

## <a name="demonstrates"></a>Demonstruje

<xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.

## <a name="discussion"></a>Účely

První část ukázkového použití <xref:System.Activities.WorkflowInvoker.Invoke%2A>. Toto je nejzákladnější způsob, jak spustit pracovní postup. Spuštěné pracovní postupy jsou spouštěny synchronně. <xref:System.Activities.WorkflowInvoker.Invoke%2A>

Druhá část ukázky používá <xref:System.Activities.WorkflowApplication> třídu. <xref:System.Activities.WorkflowApplication>umožňuje mít větší kontrolu nad každou instancí, včetně možnosti pracovat se spuštěným pracovním postupem a asynchronním spuštěním pracovního postupu.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a>Viz také:

- [Použití WorkflowInvoker a WorkflowApplication](../using-workflowinvoker-and-workflowapplication.md)

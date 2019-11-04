---
title: 'Postupy: povolení trvalosti pro pracovní postupy a služby pracovních postupů'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 5d0eeb8ad40f2f4f3349ab48487316014a561a1b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460889"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a>Postupy: povolení trvalosti pro pracovní postupy a služby pracovních postupů

Toto téma popisuje, jak povolit trvalost pro pracovní postupy a služby pracovních postupů.

## <a name="enable-persistence-for-workflows"></a>Povolit trvalost pro pracovní postupy

Úložiště instancí můžete přidružit k aplikaci **WorkflowApplication** pomocí vlastnosti <xref:System.Activities.WorkflowApplication.InstanceStore%2A> třídy <xref:System.Activities.WorkflowApplication>. Metoda <xref:System.Activities.WorkflowApplication.Persist%2A> ukládá nebo ukládá pracovní postup do úložiště instancí přidruženého k aplikaci. Metoda <xref:System.Activities.WorkflowApplication.Unload%2A> ukládá pracovní postup do úložiště instance a poté uvolní instanci z paměti. Metoda **Load** načte pracovní postup do paměti pomocí dat pracovního postupu uložených v úložišti trvalosti instance.

Metoda **trvalosti** provádí následující kroky:

1. Pozastaví Plánovač pracovních postupů a počká, dokud pracovní postup nevstoupí do stavu nečinnosti.

2. Zachovává nebo ukládá pracovní postup do úložiště trvalosti.

3. Obnoví Scheduler pracovního postupu.

 Metoda **Unload** provede následující kroky:

1. Pozastaví Plánovač pracovních postupů a počká, dokud pracovní postup nevstoupí do stavu nečinnosti.

2. Zachovává nebo ukládá pracovní postup do úložiště trvalosti.

3. Odstraní instanci pracovního postupu v paměti.

Metody **trvalého** i zrušení **zatížení** budou blokovat, pokud je pracovní postup v zóně bez trvalého uložení, dokud pracovní postup neukončí zónu bez trvalého uložení. Metoda pokračuje v operaci trvalého nebo odnačtení po dokončení zóny bez trvalého uložení. Pokud se zóna No-repersistent nedokončila před vypršením časového limitu, nebo pokud proces trvalosti trvá příliš dlouho, bude vyvolána výjimka TimeoutException.

## <a name="enable-persistence-for-workflow-services-in-code"></a>Povolení trvalosti pro služby pracovních postupů v kódu

Člen **DurableInstancingOptions** třídy <xref:System.ServiceModel.WorkflowServiceHost> má vlastnost s názvem **InstanceStore** , kterou můžete použít k přidružení úložiště instancí k **hostiteli**služby.

```csharp
// wsh is an instance of WorkflowServiceHost class
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();
```

Když je **hostitel WorkflowServiceHost** otevřený, trvalost se automaticky povolí, pokud **DurableInstancingOptions. InstanceStore** nemá hodnotu null.

Chování služby obvykle poskytuje konkrétní úložiště instancí, které se má použít s hostitelem služby pracovního postupu pomocí vlastnosti **InstanceStore** . Například SqlWorkflowInstanceStoreBehavior vytvoří instanci třídy **SqlWorkflowInstanceStore**, nakonfiguruje ji a přiřadí ji k **DurableInstancingOptions. InstanceStore**.

## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a>Povolení trvalosti pro služby pracovních postupů pomocí konfiguračního souboru aplikace

Trvalost lze povolit pomocí konfiguračního souboru aplikace přidáním následujícího kódu do souboru App. config nebo Web. config:

```xml
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="myBehavior">
          <sqlWorkflowInstanceStore connectionString="Data Source=myDatabaseServer;Initial Catalog=myPersistenceDatabase" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```

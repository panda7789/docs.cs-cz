---
title: 'Postupy: Povolení trvalosti pro pracovní postupy a služby pracovních postupů'
description: Přečtěte si, jak nakonfigurovat úložiště instancí pracovních postupů SQL, aby se povolilo uchovávání pracovních postupů a služeb pracovních postupů programově a pomocí konfiguračního souboru.
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 31fe6e3f06989e9a42254747565342cf97e4b9f1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421511"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a>Postupy: Povolení trvalosti pro pracovní postupy a služby pracovních postupů

Toto téma popisuje, jak povolit trvalost pro pracovní postupy a služby pracovních postupů.

## <a name="enable-persistence-for-workflows"></a>Povolit trvalost pro pracovní postupy

Úložiště instancí můžete přidružit k aplikaci **WorkflowApplication** pomocí <xref:System.Activities.WorkflowApplication.InstanceStore%2A> vlastnosti <xref:System.Activities.WorkflowApplication> třídy. <xref:System.Activities.WorkflowApplication.Persist%2A>Metoda ukládá nebo ukládá pracovní postup do úložiště instancí přidruženého k aplikaci. <xref:System.Activities.WorkflowApplication.Unload%2A>Metoda uchovává pracovní postup do úložiště instance a poté uvolní instanci z paměti. Metoda **Load** načte pracovní postup do paměti pomocí dat pracovního postupu uložených v úložišti trvalosti instance.

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

Člen **DurableInstancingOptions** <xref:System.ServiceModel.WorkflowServiceHost> třídy má vlastnost s názvem **InstanceStore** , kterou můžete použít k přidružení úložiště instancí k **hostiteli**služby.

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

---
title: 'Postupy: Povolení trvalosti pro pracovní postupy a služby pracovních postupů'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 6a2a8d73298e14f92f376b97b9637db91532e937
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761426"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a>Postupy: Povolení trvalosti pro pracovní postupy a služby pracovních postupů
Toto téma popisuje postup povolení trvalosti pro pracovní postupy a služby pracovních postupů.  
  
## <a name="enable-persistence-for-workflows"></a>Povolení trvalosti pro pracovní postupy  
 Můžete přidružit ukládání instance s **WorkflowApplication** pomocí <xref:System.Activities.WorkflowApplication.InstanceStore%2A> vlastnost <xref:System.Activities.WorkflowApplication> třídy. <xref:System.Activities.WorkflowApplication.Persist%2A> Metoda uloží nebo nevyřeší pracovního postupu do úložiště instancí přidružené k aplikaci. <xref:System.Activities.WorkflowApplication.Unload%2A> Metoda uchovává pracovního postupu do úložiště instancí a poté uvolní instanci z paměti. **Zatížení** metoda načte do paměti pomocí pracovního postupu data uložená v úložišti stálost instance pracovního postupu.  
  
 **Trvalého** metoda provede následující kroky:  
  
1. Plánovač pracovní postup se pozastaví a počká, dokud pracovního postupu přejde do stavu nečinnosti.  
  
2. Opakuje nebo uloží pracovní postup do trvalého úložiště.  
  
3. Obnoví Plánovač pracovního postupu.  
  
 **Uvolnění** metoda provede následující kroky:  
  
1. Plánovač pracovní postup se pozastaví a počká, dokud pracovního postupu přejde do stavu nečinnosti.  
  
2. Opakuje nebo uloží pracovní postup do trvalého úložiště.  
  
3. Uvolní instanci pracovního postupu v paměti.  
  
 Oba **trvalého** a **uvolnění** metody budou blokovat, zatímco pracovní postup je v zóně no-persist až do ukončení pracovního postupu no-persist zóny. Metoda pokračuje zachovat nebo uvolnit operaci po dokončení bez dočasného zóny. Zóna no-persist nedokončí předtím, než uplyne časový limit, nebo pokud proces trvalého trvá příliš dlouho, bude vyvolána výjimka TimeoutException.  
  
## <a name="enable-persistence-for-workflow-services-in-code"></a>Povolení trvalosti pro pracovní postup služby v kódu  
 **DurableInstancingOptions** člena <xref:System.ServiceModel.WorkflowServiceHost> třída nemá vlastnost s názvem **třídy InstanceStore** , můžete přidružit ukládání instance s **hostitele služby pracovního postupu** .  
  
```  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
```  
  
 Když **hostitele služby pracovního postupu** je otevřen, je automaticky povolena trvalost Pokud **DurableInstancingOptions.InstanceStore** nemá hodnotu null.  
  
 Obvykle, chování služby poskytuje úložiště konkrétní instance pro použití s hostitele služby pracovního postupu pomocí **třídy InstanceStore** vlastnost. Například, SqlWorkflowInstanceStoreBehavior vytvoří instanci **SqlWorkflowInstanceStore**, nakonfiguruje a přiřadí ji k **DurableInstancingOptions.InstanceStore**.  
  
## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a>Povolení trvalosti pro pracovní postup služby pomocí konfiguračního souboru aplikace  
 Trvalost se dá nastavit pomocí konfiguračního souboru aplikace tak, že přidáte následující kód do souboru app.config nebo web.config:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="myBehavior">  
          <SqlWorkflowInstanceStore connectionString="Data Source=myDatatbaseServer;Initial Catalog=myPersistenceDatabase">  
        </behavior>  
      </serviceBehaviors>  
    <behaviors>  
  </system.serviceModel>  
</configuration>  
```

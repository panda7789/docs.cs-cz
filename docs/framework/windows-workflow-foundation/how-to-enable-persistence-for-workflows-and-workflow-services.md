---
title: 'Postupy: povolení trvalosti pro pracovní postupy a služeb pracovních postupů'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 35158c45217e764bc2e27dac26f8d680e5897fa9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514415"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a>Postupy: povolení trvalosti pro pracovní postupy a služeb pracovních postupů
Toto téma popisuje, jak povolit trvalost pro pracovní postupy a služeb pracovních postupů.  
  
## <a name="enable-persistence-for-workflows"></a>Zapnout stálost pro pracovní postupy  
 Můžete přidružit ukládání instance s **WorkflowApplication** pomocí <xref:System.Activities.WorkflowApplication.InstanceStore%2A> vlastnost <xref:System.Activities.WorkflowApplication> třídy. <xref:System.Activities.WorkflowApplication.Persist%2A> Metoda uloží nebo potrvají pracovního postupu do instance úložiště přidružené k aplikaci. <xref:System.Activities.WorkflowApplication.Unload%2A> Metoda potrvají pracovního postupu do úložiště instance a poté uvolní instanci z paměti. **Zatížení** metoda načte do paměti pomocí pracovního postupu data uložená v úložišti trvalost instance pracovního postupu.  
  
 **Zachovat** metoda provede následující kroky:  
  
1.  Pozastaví Plánovač pracovního postupu a čeká na pracovním postupu vstupuje do stavu nečinnosti.  
  
2.  Potrvají nebo uloží do úložiště trvalosti pracovního postupu.  
  
3.  Obnoví Plánovač pracovního postupu.  
  
 **Uvolnění** metoda provede následující kroky:  
  
1.  Pozastaví Plánovač pracovního postupu a čeká na pracovním postupu vstupuje do stavu nečinnosti.  
  
2.  Potrvají nebo uloží do úložiště trvalosti pracovního postupu.  
  
3.  Uvolní instanci pracovního postupu v paměti.  
  
 Obě **zachovat** a **uvolnění** metody bude blokovat, když pracovní postup je v zóně no-persist až do konce zóny no-persist pracovního postupu. Metoda pokračuje v operaci zachovat nebo uvolnění po dokončení ne zachovat zóny. Pokud zóna no-persist nedokončí předtím, než uplyne časový limit, nebo pokud proces trvalost trvá příliš dlouho, bude vyvolána TimeoutException.  
  
## <a name="enable-persistence-for-workflow-services-in-code"></a>Zapnout stálost pro pracovní postup služby v kódu  
 **DurableInstancingOptions** členem <xref:System.ServiceModel.WorkflowServiceHost> třída má vlastnost s názvem **InstanceStore** používané pro přidružení ukládání instance s **hostitele služby pracovního postupu** .  
  
```  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
```  
  
 Když **hostitele služby pracovního postupu** je otevřené, je automaticky povolena trvalost Pokud **DurableInstancingOptions.InstanceStore** není null.  
  
 Obvykle chování služby poskytuje konkrétní instance úložiště pro použití s hostitele služby pracovního postupu pomocí **InstanceStore** vlastnost. Například SqlWorkflowInstanceStoreBehavior vytvoří instanci **SqlWorkflowInstanceStore**, nakonfiguruje jej a přiřadí ji k **DurableInstancingOptions.InstanceStore**.  
  
## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a>Zapnout stálost pro pracovní postup služby pomocí konfiguračního souboru aplikace  
 Trvalost můžete povolit pomocí konfiguračního souboru aplikace přidáním následující kód do souboru app.config nebo web.config:  
  
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

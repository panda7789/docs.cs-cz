---
title: "Použití poznámky v dotazech."
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3a6edccba458bfd3629cab851c5d818a69d26173
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="using-annotation-in-queries"></a>Použití poznámky v dotazech.
Anotace umožňují libovolně značku sledování záznamů s hodnotou, kterou lze nakonfigurovat po čas sestavení. Například můžete několik záznamů sledování napříč několika pracovní postupy pro označené "Poštovní Server" == "E-mailu Server1". To umožňuje snadno vyhledat všechny záznamy s touto značkou při dotazování sledování záznamy později.  
  
## <a name="adding-annotations"></a>Přidávání poznámek  
 Komentáře lze přidat do dotazu sledování, jak je znázorněno v následujícím příkladu.  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <annotations>  
    <annotation name="MailServer" value="Mail Server1"/>  
  </annotations>  
</activityStateQuery>  
```  
  
> [!NOTE]
>  Tyto sledování elementy dotazu lze použít k vytvoření profilu sledování. Profil sledování lze vytvořit buď v konfiguraci nebo pomocí kódu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [\<Účastníci >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)  
 [Pracovní postup sledování a trasování](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

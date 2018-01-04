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
ms.workload: dotnet
ms.openlocfilehash: e871533afc1a472bb5ee05e3e13275bdfb1acc8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-annotation-in-queries"></a><span data-ttu-id="c25ad-102">Použití poznámky v dotazech.</span><span class="sxs-lookup"><span data-stu-id="c25ad-102">Using Annotation in Queries</span></span>
<span data-ttu-id="c25ad-103">Anotace umožňují libovolně značku sledování záznamů s hodnotou, kterou lze nakonfigurovat po čas sestavení.</span><span class="sxs-lookup"><span data-stu-id="c25ad-103">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="c25ad-104">Například můžete několik záznamů sledování napříč několika pracovní postupy pro označené "Poštovní Server" == "E-mailu Server1".</span><span class="sxs-lookup"><span data-stu-id="c25ad-104">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="c25ad-105">To umožňuje snadno vyhledat všechny záznamy s touto značkou při dotazování sledování záznamy později.</span><span class="sxs-lookup"><span data-stu-id="c25ad-105">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
## <a name="adding-annotations"></a><span data-ttu-id="c25ad-106">Přidávání poznámek</span><span class="sxs-lookup"><span data-stu-id="c25ad-106">Adding Annotations</span></span>  
 <span data-ttu-id="c25ad-107">Komentáře lze přidat do dotazu sledování, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c25ad-107">An annotation can be added to a tracking query as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="c25ad-108">Tyto sledování elementy dotazu lze použít k vytvoření profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="c25ad-108">These tracking query elements can be used to create a tracking profile.</span></span> <span data-ttu-id="c25ad-109">Profil sledování lze vytvořit buď v konfiguraci nebo pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="c25ad-109">A tracking profile can be created either in configuration or using code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c25ad-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="c25ad-110">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [<span data-ttu-id="c25ad-111">\<Účastníci ></span><span class="sxs-lookup"><span data-stu-id="c25ad-111">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)  
 [<span data-ttu-id="c25ad-112">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="c25ad-112">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="c25ad-113">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="c25ad-113">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

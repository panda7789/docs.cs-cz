---
title: Použití poznámek v dotazech
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
ms.openlocfilehash: 728408e744bc1eca62158fab1a7a17e985fe3b6c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947287"
---
# <a name="using-annotation-in-queries"></a><span data-ttu-id="9bd5c-102">Použití poznámek v dotazech</span><span class="sxs-lookup"><span data-stu-id="9bd5c-102">Using Annotation in Queries</span></span>
<span data-ttu-id="9bd5c-103">Anotace umožňují libovolně značku sledování záznamů s hodnotou, kterou lze nakonfigurovat po čas sestavení.</span><span class="sxs-lookup"><span data-stu-id="9bd5c-103">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="9bd5c-104">Můžete například chtít, aby několik sledovacích záznamů v několika pracovních postupech bylo označeno jako "poštovní server" = = "pošta Server1".</span><span class="sxs-lookup"><span data-stu-id="9bd5c-104">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="9bd5c-105">To umožňuje snadno vyhledat všechny záznamy s touto značkou při dotazování sledování záznamy později.</span><span class="sxs-lookup"><span data-stu-id="9bd5c-105">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
## <a name="adding-annotations"></a><span data-ttu-id="9bd5c-106">Přidávání poznámek</span><span class="sxs-lookup"><span data-stu-id="9bd5c-106">Adding Annotations</span></span>  
 <span data-ttu-id="9bd5c-107">Komentáře lze přidat do dotazu sledování, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9bd5c-107">An annotation can be added to a tracking query as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="9bd5c-108">Tyto sledování elementy dotazu lze použít k vytvoření profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="9bd5c-108">These tracking query elements can be used to create a tracking profile.</span></span> <span data-ttu-id="9bd5c-109">Profil sledování lze vytvořit buď v konfiguraci nebo pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="9bd5c-109">A tracking profile can be created either in configuration or using code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bd5c-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9bd5c-110">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="9bd5c-111">\<Účastníci ></span><span class="sxs-lookup"><span data-stu-id="9bd5c-111">\<participants></span></span>](participants.md)
- [<span data-ttu-id="9bd5c-112">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="9bd5c-112">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9bd5c-113">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="9bd5c-113">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)

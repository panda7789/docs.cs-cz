---
title: Použití poznámek v dotazech
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
ms.openlocfilehash: fd2d98852ca44e3485ddcf4be29d505b39011698
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59208641"
---
# <a name="using-annotation-in-queries"></a><span data-ttu-id="4ad1d-102">Použití poznámek v dotazech</span><span class="sxs-lookup"><span data-stu-id="4ad1d-102">Using Annotation in Queries</span></span>
<span data-ttu-id="4ad1d-103">Anotace umožňují libovolně značku sledování záznamů s hodnotou, kterou lze nakonfigurovat po čas sestavení.</span><span class="sxs-lookup"><span data-stu-id="4ad1d-103">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="4ad1d-104">Například chtít několik sledování záznamů napříč několika pracovních úloh a být s klíčovým slovem "Poštovního serveru" == "Pošty Server1".</span><span class="sxs-lookup"><span data-stu-id="4ad1d-104">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="4ad1d-105">To umožňuje snadno vyhledat všechny záznamy s touto značkou při dotazování sledování záznamy později.</span><span class="sxs-lookup"><span data-stu-id="4ad1d-105">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
## <a name="adding-annotations"></a><span data-ttu-id="4ad1d-106">Přidávání poznámek</span><span class="sxs-lookup"><span data-stu-id="4ad1d-106">Adding Annotations</span></span>  
 <span data-ttu-id="4ad1d-107">Komentáře lze přidat do dotazu sledování, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4ad1d-107">An annotation can be added to a tracking query as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="4ad1d-108">Tyto sledování elementy dotazu lze použít k vytvoření profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="4ad1d-108">These tracking query elements can be used to create a tracking profile.</span></span> <span data-ttu-id="4ad1d-109">Profil sledování lze vytvořit buď v konfiguraci nebo pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="4ad1d-109">A tracking profile can be created either in configuration or using code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ad1d-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ad1d-110">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="4ad1d-111">\<participants></span><span class="sxs-lookup"><span data-stu-id="4ad1d-111">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)
- [<span data-ttu-id="4ad1d-112">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="4ad1d-112">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4ad1d-113">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="4ad1d-113">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

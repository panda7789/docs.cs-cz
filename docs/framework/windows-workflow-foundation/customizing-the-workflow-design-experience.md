---
title: "Přizpůsobení prostředí návrhu pracovních postupů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9916e30812e167e108a1ca9b958aa6d15fbd1f41
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="d702c-102">Přizpůsobení prostředí návrhu pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="d702c-102">Customizing the Workflow Design Experience</span></span>
<span data-ttu-id="d702c-103">Scénáře pro navrhování vlastních aktivit a opětovného hostování [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] byly značně zjednodušené [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d702c-103">The scenarios for designing custom activities and for rehosting the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] have been greatly simplified in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span> <span data-ttu-id="d702c-104">Vývoj a nasazení je teď jednodušší a flexibilnější.</span><span class="sxs-lookup"><span data-stu-id="d702c-104">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="d702c-105">Změny klíče infrastruktury je, že nový návrháře programovací model aktivita je založena na [!INCLUDE[avalon1](../../../includes/avalon1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d702c-105">The key infrastructural change is that the new activity designer programming model is built upon [!INCLUDE[avalon1](../../../includes/avalon1-md.md)].</span></span> <span data-ttu-id="d702c-106">To vám umožňuje definovat deklarativně návrháře aktivit a opětovným hostováním [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] v ostatních aplikacích s srovnávacích snadné.</span><span class="sxs-lookup"><span data-stu-id="d702c-106">This gives you the ability to define activity designers declaratively and to rehost the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in other applications with comparative easy.</span></span> <span data-ttu-id="d702c-107">Při opětovném hostování, editor vlastního výrazu mohou být vytvořeny pro podporu technologie IntelliSense nebo doméně zjednodušené výraz.</span><span class="sxs-lookup"><span data-stu-id="d702c-107">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="d702c-108">Integrace s [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] se stal plynulejší s použitím služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="d702c-108">The integration with [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] has become more seamless with use of workflow services.</span></span> <span data-ttu-id="d702c-109">Ke zvýšení návrhu čas dojde v Návrháři opětovné hostování nástroje pracovní postup můžete použít Návrháře vlastních aktivit a položka stromu modelu.</span><span class="sxs-lookup"><span data-stu-id="d702c-109">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d702c-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d702c-110">In This Section</span></span>  
 [<span data-ttu-id="d702c-111">Pomocí Návrháře vlastních aktivit a šablony</span><span class="sxs-lookup"><span data-stu-id="d702c-111">Using Custom Activity Designers and Templates</span></span>](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md)  
 <span data-ttu-id="d702c-112">Popisuje, jak vytvořit novou vlastní aktivitu návrháři a šablony.</span><span class="sxs-lookup"><span data-stu-id="d702c-112">Describes how to create new custom activity designers and templates.</span></span>  
  
 [<span data-ttu-id="d702c-113">Opětovného hostování návrháře pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="d702c-113">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 <span data-ttu-id="d702c-114">Popisuje, jak znovu hostitele [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] mimo [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] a jak zobrazit chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="d702c-114">Describes how to re-host the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] outside of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] and how to display validation errors.</span></span>  
  
 [<span data-ttu-id="d702c-115">Pomocí vlastního výrazu editoru</span><span class="sxs-lookup"><span data-stu-id="d702c-115">Using a Custom Expression Editor</span></span>](../../../docs/framework/windows-workflow-foundation/using-a-custom-expression-editor.md)  
 <span data-ttu-id="d702c-116">Popisuje, jak implementovat vlastní výraz editor pro použití s návrháři pracovní postup opětovné hostování nástroje mimo [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d702c-116">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d702c-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="d702c-117">Reference</span></span>  
 <xref:System.Activities.Presentation.ActivityDesigner>  
  
## <a name="see-also"></a><span data-ttu-id="d702c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="d702c-118">See Also</span></span>  
 [<span data-ttu-id="d702c-119">Rozšíření modelu Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="d702c-119">Extending Windows Workflow Foundation</span></span>](../../../docs/framework/windows-workflow-foundation/extend.md)  
 [<span data-ttu-id="d702c-120">Návrhář</span><span class="sxs-lookup"><span data-stu-id="d702c-120">Designer</span></span>](../../../docs/framework/windows-workflow-foundation/samples/designer.md)  
 [<span data-ttu-id="d702c-121">Návrháři vlastních aktivit</span><span class="sxs-lookup"><span data-stu-id="d702c-121">Custom Activity Designers</span></span>](../../../docs/framework/windows-workflow-foundation/samples/custom-activity-designers.md)  
 [<span data-ttu-id="d702c-122">Návrhář opětovného hostování</span><span class="sxs-lookup"><span data-stu-id="d702c-122">Designer ReHosting</span></span>](../../../docs/framework/windows-workflow-foundation/samples/designer-rehosting.md)

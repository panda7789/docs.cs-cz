---
title: Přizpůsobení prostředí pro návrh pracovního postupu
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 27be398d874747b65ae051224070d3f40f1fbbb0
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715141"
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="df340-102">Přizpůsobení prostředí pro návrh pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="df340-102">Customizing the Workflow Design Experience</span></span>

<span data-ttu-id="df340-103">Scénáře pro návrh vlastní aktivity a pro opětovné hostování Návrhář postupu provádění Windows byly významně zjednodušené v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="df340-103">The scenarios for designing custom activities and for rehosting the Windows Workflow Designer have been greatly simplified in .NET Framework 4.</span></span> <span data-ttu-id="df340-104">Vývoj a nasazení jsou teď jednodušší a pružnější.</span><span class="sxs-lookup"><span data-stu-id="df340-104">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="df340-105">Změnou Key infrastrukturyu je, že nový programovací model návrháře aktivit je sestavený po Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="df340-105">The key infrastructural change is that the new activity designer programming model is built upon Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="df340-106">Díky tomu je možné definovat návrháře aktivit deklarativně a znovu hostovat Návrhář postupu provádění v jiných aplikacích se srovnávacími možnostmi.</span><span class="sxs-lookup"><span data-stu-id="df340-106">This gives you the ability to define activity designers declaratively and to rehost the Workflow Designer in other applications with comparative easy.</span></span> <span data-ttu-id="df340-107">Při opětovném hostování je možné vytvořit Editor vlastního výrazu pro podporu technologie IntelliSense nebo zjednodušené domény výrazů.</span><span class="sxs-lookup"><span data-stu-id="df340-107">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="df340-108">Integrace se službou Windows Communication Foundation (WCF) se s využitím služeb pracovních postupů vyhladí.</span><span class="sxs-lookup"><span data-stu-id="df340-108">The integration with Windows Communication Foundation (WCF) has become more seamless with use of workflow services.</span></span> <span data-ttu-id="df340-109">Návrháři vlastních aktivit a stromové položky modelu lze použít ke zlepšení doby návrhu v prostředích pro přehostování návrháře pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="df340-109">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="df340-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="df340-110">In This Section</span></span>

 [<span data-ttu-id="df340-111">Použití vlastních návrhářů a šablon aktivity</span><span class="sxs-lookup"><span data-stu-id="df340-111">Using Custom Activity Designers and Templates</span></span>](using-custom-activity-designers-and-templates.md)

 <span data-ttu-id="df340-112">Popisuje, jak vytvořit nové návrháře a šablony vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="df340-112">Describes how to create new custom activity designers and templates.</span></span>

 [<span data-ttu-id="df340-113">Změna hostování Návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="df340-113">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)

 <span data-ttu-id="df340-114">Popisuje, jak znovu hostovat Návrhář postupu provádění systému Windows mimo sadu Visual Studio a jak zobrazit chyby ověřování.</span><span class="sxs-lookup"><span data-stu-id="df340-114">Describes how to re-host the Windows Workflow Designer outside of Visual Studio and how to display validation errors.</span></span>

 [<span data-ttu-id="df340-115">Použití editoru vlastních výrazů</span><span class="sxs-lookup"><span data-stu-id="df340-115">Using a Custom Expression Editor</span></span>](using-a-custom-expression-editor.md)

 <span data-ttu-id="df340-116">Popisuje, jak implementovat Editor vlastního výrazu pro použití s Návrháři pracovního postupu, kteří se znovu hostují mimo sadu Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="df340-116">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of Visual Studio 2010.</span></span>

## <a name="reference"></a><span data-ttu-id="df340-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="df340-117">Reference</span></span>

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a><span data-ttu-id="df340-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df340-118">See also</span></span>

- [<span data-ttu-id="df340-119">Rozšíření Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="df340-119">Extending Windows Workflow Foundation</span></span>](extend.md)
- [<span data-ttu-id="df340-120">Návrhář</span><span class="sxs-lookup"><span data-stu-id="df340-120">Designer</span></span>](./samples/designer.md)
- [<span data-ttu-id="df340-121">Návrháři vlastních aktivit</span><span class="sxs-lookup"><span data-stu-id="df340-121">Custom Activity Designers</span></span>](./samples/custom-activity-designers.md)
- [<span data-ttu-id="df340-122">Změna hostování návrháře</span><span class="sxs-lookup"><span data-stu-id="df340-122">Designer ReHosting</span></span>](./samples/designer-rehosting.md)

---
title: Přizpůsobení prostředí pro návrh pracovního postupu
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 41be55391ae9481f6c2e4feb76443f7fb676b69d
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141925"
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="498c7-102">Přizpůsobení prostředí pro návrh pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="498c7-102">Customizing the Workflow Design Experience</span></span>

<span data-ttu-id="498c7-103">Scénáře pro návrh vlastní aktivity a pro opětovné hostování [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] byly významně zjednodušeny v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="498c7-103">The scenarios for designing custom activities and for rehosting the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] have been greatly simplified in .NET Framework 4.</span></span> <span data-ttu-id="498c7-104">Vývoj a nasazení jsou teď jednodušší a pružnější.</span><span class="sxs-lookup"><span data-stu-id="498c7-104">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="498c7-105">Změnou Key infrastrukturyu je, že nový programovací model návrháře aktivit je sestavený po Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="498c7-105">The key infrastructural change is that the new activity designer programming model is built upon Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="498c7-106">Díky tomu je možné definovat návrháře aktivit deklarativně a znovu hostovat [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] v jiných aplikacích se srovnávacími možnostmi.</span><span class="sxs-lookup"><span data-stu-id="498c7-106">This gives you the ability to define activity designers declaratively and to rehost the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in other applications with comparative easy.</span></span> <span data-ttu-id="498c7-107">Při opětovném hostování je možné vytvořit Editor vlastního výrazu pro podporu technologie IntelliSense nebo zjednodušené domény výrazů.</span><span class="sxs-lookup"><span data-stu-id="498c7-107">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="498c7-108">Integrace se službou Windows Communication Foundation (WCF) se s využitím služeb pracovních postupů vyhladí.</span><span class="sxs-lookup"><span data-stu-id="498c7-108">The integration with Windows Communication Foundation (WCF) has become more seamless with use of workflow services.</span></span> <span data-ttu-id="498c7-109">Návrháři vlastních aktivit a stromové položky modelu lze použít ke zlepšení doby návrhu v prostředích pro přehostování návrháře pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="498c7-109">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="498c7-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="498c7-110">In This Section</span></span>

 [<span data-ttu-id="498c7-111">Použití vlastních návrhářů a šablon aktivity</span><span class="sxs-lookup"><span data-stu-id="498c7-111">Using Custom Activity Designers and Templates</span></span>](using-custom-activity-designers-and-templates.md)

 <span data-ttu-id="498c7-112">Popisuje, jak vytvořit nové návrháře a šablony vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="498c7-112">Describes how to create new custom activity designers and templates.</span></span>

 [<span data-ttu-id="498c7-113">Změna hostování Návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="498c7-113">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)

 <span data-ttu-id="498c7-114">Popisuje, jak znovu hostovat [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] mimo sadu Visual Studio a jak zobrazit chyby ověřování.</span><span class="sxs-lookup"><span data-stu-id="498c7-114">Describes how to re-host the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] outside of Visual Studio and how to display validation errors.</span></span>

 [<span data-ttu-id="498c7-115">Použití editoru vlastních výrazů</span><span class="sxs-lookup"><span data-stu-id="498c7-115">Using a Custom Expression Editor</span></span>](using-a-custom-expression-editor.md)

 <span data-ttu-id="498c7-116">Popisuje, jak implementovat Editor vlastního výrazu pro použití s Návrháři pracovního postupu, kteří se znovu hostují mimo sadu Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="498c7-116">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of Visual Studio 2010.</span></span>

## <a name="reference"></a><span data-ttu-id="498c7-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="498c7-117">Reference</span></span>

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a><span data-ttu-id="498c7-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="498c7-118">See also</span></span>

- [<span data-ttu-id="498c7-119">Rozšíření Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="498c7-119">Extending Windows Workflow Foundation</span></span>](extend.md)
- [<span data-ttu-id="498c7-120">Návrhář</span><span class="sxs-lookup"><span data-stu-id="498c7-120">Designer</span></span>](./samples/designer.md)
- [<span data-ttu-id="498c7-121">Návrháři vlastních aktivit</span><span class="sxs-lookup"><span data-stu-id="498c7-121">Custom Activity Designers</span></span>](./samples/custom-activity-designers.md)
- [<span data-ttu-id="498c7-122">Změna hostování návrháře</span><span class="sxs-lookup"><span data-stu-id="498c7-122">Designer ReHosting</span></span>](./samples/designer-rehosting.md)

---
title: Ovládací prvky
description: Přečtěte si, jak přidat a umístit ovládací prvky Windows Form. Můžete také manipulovat s ovládacími prvky v návrháři a napsat kód pro dynamické přidávání ovládacích prvků v době běhu.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls
- controls [Windows Forms]
- Windows Forms controls, about Windows Forms controls
ms.assetid: f050de8f-4ebd-4042-94b8-edf9a1dbd52a
ms.openlocfilehash: 9ca4a2a1205663ae0ff4537a58cc1991a15da5d8
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324032"
---
# <a name="windows-forms-controls"></a><span data-ttu-id="895e6-104">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="895e6-104">Windows Forms controls</span></span>

<span data-ttu-id="895e6-105">Při návrhu a úpravách uživatelského rozhraní aplikací model Windows Forms budete muset ovládací prvky přidat, Zarovnat a umístit.</span><span class="sxs-lookup"><span data-stu-id="895e6-105">As you design and modify the user interface of your Windows Forms applications, you will need to add, align, and position controls.</span></span> <span data-ttu-id="895e6-106">Ovládací prvky jsou objekty, které jsou obsaženy v objektech formuláře.</span><span class="sxs-lookup"><span data-stu-id="895e6-106">Controls are objects that are contained within form objects.</span></span> <span data-ttu-id="895e6-107">Každý typ ovládacího prvku má svou vlastní sadu vlastností, metod a událostí, které je vhodné pro určitý účel.</span><span class="sxs-lookup"><span data-stu-id="895e6-107">Each type of control has its own set of properties, methods, and events that make it suitable for a particular purpose.</span></span> <span data-ttu-id="895e6-108">Můžete manipulovat s ovládacími prvky v návrháři a napsat kód pro dynamické přidávání ovládacích prvků v době běhu.</span><span class="sxs-lookup"><span data-stu-id="895e6-108">You can manipulate controls in the designer and write code to add controls dynamically at run time.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="895e6-109">V této části</span><span class="sxs-lookup"><span data-stu-id="895e6-109">In this section</span></span>

<span data-ttu-id="895e6-110">[Vkládání ovládacích prvků na model Windows Forms](putting-controls-on-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="895e6-110">[Putting Controls on Windows Forms](putting-controls-on-windows-forms.md)</span></span>\
<span data-ttu-id="895e6-111">Obsahuje odkazy související s vložením ovládacích prvků do formulářů.</span><span class="sxs-lookup"><span data-stu-id="895e6-111">Provides links related to putting controls on forms.</span></span>

<span data-ttu-id="895e6-112">[Uspořádání ovládacích prvků na model Windows Forms](how-to-align-multiple-controls-on-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="895e6-112">[Arranging Controls on Windows Forms](how-to-align-multiple-controls-on-windows-forms.md)</span></span>\
<span data-ttu-id="895e6-113">Články související s uspořádáním ovládacích prvků na formulářích.</span><span class="sxs-lookup"><span data-stu-id="895e6-113">Articles related to arranging controls on forms.</span></span>

<span data-ttu-id="895e6-114">[Popisování jednotlivých ovládacích prvků model Windows Forms a poskytování jejich zástupců](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)</span><span class="sxs-lookup"><span data-stu-id="895e6-114">[Labeling Individual Windows Forms Controls and Providing Shortcuts to Them](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)</span></span>\
<span data-ttu-id="895e6-115">Popisuje použití klávesových zkratek, textových popisků ovládacích prvků a modifikačních kláves.</span><span class="sxs-lookup"><span data-stu-id="895e6-115">Describes the uses of keyboard shortcuts, text labels on controls, and modifier keys.</span></span>

<span data-ttu-id="895e6-116">[Ovládací prvky pro použití na model Windows Forms](controls-to-use-on-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="895e6-116">[Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md)</span></span>\
<span data-ttu-id="895e6-117">Uvádí ovládací prvky, které pracují s model Windows Forms a základní věci, které můžete s každým ovládacím prvkem provádět.</span><span class="sxs-lookup"><span data-stu-id="895e6-117">Lists the controls that work with Windows Forms, and basic things you can accomplish with each control.</span></span>

<span data-ttu-id="895e6-118">[Vývoj vlastních ovládacích prvků model Windows Forms s .NET Framework](developing-custom-windows-forms-controls.md)</span><span class="sxs-lookup"><span data-stu-id="895e6-118">[Developing Custom Windows Forms Controls with the .NET Framework](developing-custom-windows-forms-controls.md)</span></span>\
<span data-ttu-id="895e6-119">Poskytuje informace a ukázky na pozadí, které uživatelům usnadňují vývoj vlastních model Windows Formsch ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="895e6-119">Provides background information and samples to help users develop custom Windows Forms controls.</span></span>

<span data-ttu-id="895e6-120">[Vývoj ovládacích prvků model Windows Forms v době návrhu](developing-windows-forms-controls-at-design-time.md)</span><span class="sxs-lookup"><span data-stu-id="895e6-120">[Developing Windows Forms Controls at Design Time](developing-windows-forms-controls-at-design-time.md)</span></span>\
<span data-ttu-id="895e6-121">Popisuje techniky pro vytváření vlastních ovládacích prvků prostřednictvím návrhu a dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="895e6-121">Describes techniques for creating custom controls through design and inheritance.</span></span>

## <a name="related-sections"></a><span data-ttu-id="895e6-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="895e6-122">Related sections</span></span>

<span data-ttu-id="895e6-123">[Klientské aplikace](../../develop-client-apps.md)</span><span class="sxs-lookup"><span data-stu-id="895e6-123">[Client Applications](../../develop-client-apps.md)</span></span>\
<span data-ttu-id="895e6-124">Poskytuje přehled vývoje aplikací určených pro systém Windows.</span><span class="sxs-lookup"><span data-stu-id="895e6-124">Provides an overview of developing Windows-based applications.</span></span>

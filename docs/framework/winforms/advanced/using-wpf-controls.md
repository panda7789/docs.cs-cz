---
title: Používání ovládacích prvků WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9883e9d31fc9e3e2ec3ca06b4fc830bcdc338ae
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460692"
---
# <a name="use-wpf-controls-in-windows-forms-apps"></a><span data-ttu-id="ea2ad-102">Použití ovládacích prvků WPF v aplikacích model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ea2ad-102">Use WPF controls in Windows Forms apps</span></span>

<span data-ttu-id="ea2ad-103">V aplikacích založených na model Windows Forms můžete použít ovládací prvky Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="ea2ad-103">You can use Windows Presentation Foundation (WPF) controls in Windows Forms-based applications.</span></span> <span data-ttu-id="ea2ad-104">I když se jedná o dvě různé technologie zobrazení, fungují hladce.</span><span class="sxs-lookup"><span data-stu-id="ea2ad-104">Although these are two different view technologies, they interoperate smoothly.</span></span>

<span data-ttu-id="ea2ad-105">Návrhář formulářů v aplikaci Visual Studio poskytuje prostředí pro vizuální návrh pro hostování Windows Presentation Foundationch ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="ea2ad-105">The Windows Forms Designer in Visual Studio provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="ea2ad-106">Ovládací prvek WPF je hostován speciálním model Windows Forms ovládacím prvkem s názvem <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="ea2ad-106">A WPF control is hosted by a special Windows Forms control that's named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="ea2ad-107">Tento ovládací prvek umožňuje ovládacímu prvku WPF podílet se na rozložení formuláře a přijímat zprávy klávesnice a myši.</span><span class="sxs-lookup"><span data-stu-id="ea2ad-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="ea2ad-108">V době návrhu můžete ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> uspořádat stejným způsobem jako kterýkoli model Windows Forms ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="ea2ad-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>

<span data-ttu-id="ea2ad-109">Můžete také použít ovládací prvky model Windows Forms v aplikacích založených na WPF.</span><span class="sxs-lookup"><span data-stu-id="ea2ad-109">You can also use Windows Forms controls in WPF-based applications.</span></span> <span data-ttu-id="ea2ad-110">Další informace najdete v tématu [Návrh XAML v aplikaci Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="ea2ad-110">For more information, see [Design XAML in Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).</span></span>

## <a name="see-also"></a><span data-ttu-id="ea2ad-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea2ad-111">See also</span></span>

- [<span data-ttu-id="ea2ad-112">WPF a model Windows Forms spolupráce</span><span class="sxs-lookup"><span data-stu-id="ea2ad-112">WPF and Windows Forms interoperation</span></span>](../../wpf/advanced/wpf-and-windows-forms-interoperation.md)

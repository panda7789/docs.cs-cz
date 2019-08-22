---
title: Používání ovládacích prvků WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5ea92b24a2ca30c0ad137d83c8f521a952ad0c6b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658489"
---
# <a name="use-wpf-controls-in-windows-forms-apps"></a><span data-ttu-id="7c051-102">Použití ovládacích prvků WPF v aplikacích model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7c051-102">Use WPF controls in Windows Forms apps</span></span>

<span data-ttu-id="7c051-103">V aplikacích založených na model Windows Forms můžete použít ovládací prvky Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="7c051-103">You can use Windows Presentation Foundation (WPF) controls in Windows Forms-based applications.</span></span> <span data-ttu-id="7c051-104">I když se jedná o dvě různé technologie zobrazení, fungují hladce.</span><span class="sxs-lookup"><span data-stu-id="7c051-104">Although these are two different view technologies, they interoperate smoothly.</span></span>

<span data-ttu-id="7c051-105">Návrhář formulářů v aplikaci Visual Studio poskytuje prostředí pro vizuální návrh pro hostování Windows Presentation Foundationch ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="7c051-105">The Windows Forms Designer in Visual Studio provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="7c051-106">Ovládací prvek WPF je hostován speciálním ovládacím prvkem model Windows Forms s názvem <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="7c051-106">A WPF control is hosted by a special Windows Forms control that's named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="7c051-107">Tento ovládací prvek umožňuje ovládacímu prvku WPF podílet se na rozložení formuláře a přijímat zprávy klávesnice a myši.</span><span class="sxs-lookup"><span data-stu-id="7c051-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="7c051-108">V době návrhu můžete <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek uspořádat stejným způsobem jako jakýkoli ovládací prvek model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7c051-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>

<span data-ttu-id="7c051-109">Můžete také použít ovládací prvky model Windows Forms v aplikacích založených na WPF.</span><span class="sxs-lookup"><span data-stu-id="7c051-109">You can also use Windows Forms controls in WPF-based applications.</span></span> <span data-ttu-id="7c051-110">Další informace najdete v tématu [Návrh XAML v aplikaci Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="7c051-110">For more information, see [Design XAML in Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).</span></span>

## <a name="see-also"></a><span data-ttu-id="7c051-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c051-111">See also</span></span>

- [<span data-ttu-id="7c051-112">WPF a model Windows Forms spolupráce</span><span class="sxs-lookup"><span data-stu-id="7c051-112">WPF and Windows Forms interoperation</span></span>](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

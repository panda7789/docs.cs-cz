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
# <a name="use-wpf-controls-in-windows-forms-apps"></a>Použití ovládacích prvků WPF v aplikacích model Windows Forms

V aplikacích založených na model Windows Forms můžete použít ovládací prvky Windows Presentation Foundation (WPF). I když se jedná o dvě různé technologie zobrazení, fungují hladce.

Návrhář formulářů v aplikaci Visual Studio poskytuje prostředí pro vizuální návrh pro hostování Windows Presentation Foundationch ovládacích prvků. Ovládací prvek WPF je hostován speciálním model Windows Forms ovládacím prvkem s názvem <xref:System.Windows.Forms.Integration.ElementHost>. Tento ovládací prvek umožňuje ovládacímu prvku WPF podílet se na rozložení formuláře a přijímat zprávy klávesnice a myši. V době návrhu můžete ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> uspořádat stejným způsobem jako kterýkoli model Windows Forms ovládací prvek.

Můžete také použít ovládací prvky model Windows Forms v aplikacích založených na WPF. Další informace najdete v tématu [Návrh XAML v aplikaci Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).

## <a name="see-also"></a>Viz také:

- [WPF a model Windows Forms spolupráce](../../wpf/advanced/wpf-and-windows-forms-interoperation.md)

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
ms.openlocfilehash: 5e05ec7fc503565333a4d05662a4e40d8d1193af
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197463"
---
# <a name="use-wpf-controls-in-windows-forms-apps"></a>Použití ovládacích prvků WPF v aplikacích model Windows Forms

V aplikacích založených na model Windows Forms můžete použít ovládací prvky Windows Presentation Foundation (WPF). I když se jedná o dvě různé technologie zobrazení, fungují hladce.

Návrhář formulářů v aplikaci Visual Studio poskytuje prostředí pro vizuální návrh pro hostování Windows Presentation Foundationch ovládacích prvků. Ovládací prvek WPF je hostován speciálním model Windows Forms ovládacím prvkem s názvem <xref:System.Windows.Forms.Integration.ElementHost>. Tento ovládací prvek umožňuje ovládacímu prvku WPF podílet se na rozložení formuláře a přijímat zprávy klávesnice a myši. V době návrhu můžete ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> uspořádat stejným způsobem jako kterýkoli model Windows Forms ovládací prvek.

Můžete také použít ovládací prvky model Windows Forms v aplikacích založených na WPF. Další informace najdete v tématu [Návrh XAML v aplikaci Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).

## <a name="see-also"></a>Viz také:

- [WPF a model Windows Forms spolupráce](../../wpf/advanced/wpf-and-windows-forms-interoperation.md)

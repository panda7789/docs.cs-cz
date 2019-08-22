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
# <a name="use-wpf-controls-in-windows-forms-apps"></a>Použití ovládacích prvků WPF v aplikacích model Windows Forms

V aplikacích založených na model Windows Forms můžete použít ovládací prvky Windows Presentation Foundation (WPF). I když se jedná o dvě různé technologie zobrazení, fungují hladce.

Návrhář formulářů v aplikaci Visual Studio poskytuje prostředí pro vizuální návrh pro hostování Windows Presentation Foundationch ovládacích prvků. Ovládací prvek WPF je hostován speciálním ovládacím prvkem model Windows Forms s názvem <xref:System.Windows.Forms.Integration.ElementHost>. Tento ovládací prvek umožňuje ovládacímu prvku WPF podílet se na rozložení formuláře a přijímat zprávy klávesnice a myši. V době návrhu můžete <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek uspořádat stejným způsobem jako jakýkoli ovládací prvek model Windows Forms.

Můžete také použít ovládací prvky model Windows Forms v aplikacích založených na WPF. Další informace najdete v tématu [Návrh XAML v aplikaci Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).

## <a name="see-also"></a>Viz také:

- [WPF a model Windows Forms spolupráce](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

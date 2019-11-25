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
# <a name="customizing-the-workflow-design-experience"></a>Přizpůsobení prostředí pro návrh pracovního postupu

Scénáře pro návrh vlastní aktivity a pro opětovné hostování [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] byly významně zjednodušeny v .NET Framework 4. Vývoj a nasazení jsou teď jednodušší a pružnější. Změnou Key infrastrukturyu je, že nový programovací model návrháře aktivit je sestavený po Windows Presentation Foundation (WPF). Díky tomu je možné definovat návrháře aktivit deklarativně a znovu hostovat [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] v jiných aplikacích se srovnávacími možnostmi. Při opětovném hostování je možné vytvořit Editor vlastního výrazu pro podporu technologie IntelliSense nebo zjednodušené domény výrazů. Integrace se službou Windows Communication Foundation (WCF) se s využitím služeb pracovních postupů vyhladí. Návrháři vlastních aktivit a stromové položky modelu lze použít ke zlepšení doby návrhu v prostředích pro přehostování návrháře pracovních postupů.

## <a name="in-this-section"></a>V tomto oddílu

 [Použití vlastních návrhářů a šablon aktivity](using-custom-activity-designers-and-templates.md)

 Popisuje, jak vytvořit nové návrháře a šablony vlastní aktivity.

 [Změna hostování Návrháře postupu provádění](rehosting-the-workflow-designer.md)

 Popisuje, jak znovu hostovat [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] mimo sadu Visual Studio a jak zobrazit chyby ověřování.

 [Použití editoru vlastních výrazů](using-a-custom-expression-editor.md)

 Popisuje, jak implementovat Editor vlastního výrazu pro použití s Návrháři pracovního postupu, kteří se znovu hostují mimo sadu Visual Studio 2010.

## <a name="reference"></a>Odkaz

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a>Viz také:

- [Rozšíření Windows Workflow Foundation](extend.md)
- [Návrhář](./samples/designer.md)
- [Návrháři vlastních aktivit](./samples/custom-activity-designers.md)
- [Změna hostování návrháře](./samples/designer-rehosting.md)

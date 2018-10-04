---
title: Kustomizace možností návrhu pracovního postupu
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: ed4ccb45e4470eb03cec856e865d4b50220816e3
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48777536"
---
# <a name="customizing-the-workflow-design-experience"></a>Kustomizace možností návrhu pracovního postupu

Scénáře pro návrh vlastní aktivity a změna hostování [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] byly výrazně zjednodušené [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]. Vývoj a nasazení jsou teď jednodušší a flexibilnější. Změny klíče infrastruktury je, že nové návrháře programovací model aktivity je postavená na Windows Presentation Foundation (WPF). To vám dává možnost definovat deklarativně návrháři aktivit a opětovným hostováním [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] v ostatních aplikacích s srovnávací snadné. Při opětovném hostování, editoru vlastních výrazů mohou být vytvořeny pro podporu technologie IntelliSense nebo doméně jednodušší výraz. Integrace s Windows Communication Foundation (WCF) se stal bezproblémové s využitím služeb pracovních postupů. Ke zvýšení návrhu v Návrháři postupu provádění se změněným hostováním prostředí čas můžete použít vlastní návrháři aktivit a položka stromu modelu.

## <a name="in-this-section"></a>V tomto oddílu

 [Použití vlastních návrhářů a šablon aktivity](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md)

 Popisuje, jak vytvořit novou vlastní aktivitu návrhářů a šablon.

 [Změna hostování Návrháře postupu provádění](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)

 Popisuje, jak znovu hostovat [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] mimo aplikaci Visual Studio a jak zobrazit chyby ověření.

 [Použití editoru vlastních výrazů](../../../docs/framework/windows-workflow-foundation/using-a-custom-expression-editor.md)

 Popisuje, jak implementovat editoru vlastních výrazů pomocí návrháře postupu provádění se změněným hostováním mimo sadu Visual Studio 2010.

## <a name="reference"></a>Odkaz

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a>Viz také

- [Rozšíření Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/extend.md)
- [Návrhář](../../../docs/framework/windows-workflow-foundation/samples/designer.md)
- [Návrháři vlastních aktivit](../../../docs/framework/windows-workflow-foundation/samples/custom-activity-designers.md)
- [Změna hostování návrháře](../../../docs/framework/windows-workflow-foundation/samples/designer-rehosting.md)
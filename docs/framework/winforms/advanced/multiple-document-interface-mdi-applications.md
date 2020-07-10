---
title: Aplikace MDI (Multiple-Document Interface)
description: Přečtěte si, jak model Windows Forms aplikace MDI (Multiple Document Interface) umožňují zobrazit více dokumentů současně s každým dokumentem zobrazeným ve vlastním okně.
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 0912a989ac1710d72c9db1cceb0e695f0ca85dee
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174650"
---
# <a name="multiple-document-interface-mdi-applications"></a>Aplikace MDI (Multiple-Document Interface)
Aplikace MDI (Multiple Document Interface) umožňují zobrazit více dokumentů současně s každým dokumentem zobrazeným ve vlastním okně. Aplikace MDI mají často položku nabídky okna s podnabídkami pro přepínání mezi okny nebo dokumenty.  
  
> [!NOTE]
> Existují rozdíly v chování mezi formuláři MDI a okny rozhraní s jedním dokumentem (SDI) v model Windows Forms. `Opacity`Vlastnost nemá vliv na vzhled podřízených formulářů MDI. Kromě toho <xref:System.Windows.Forms.Form.CenterToParent%2A> metoda nemá vliv na chování podřízených formulářů MDI.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytváření nadřazených formulářů MDI](how-to-create-mdi-parent-forms.md)  
 Poskytuje pokyny pro vytvoření kontejneru pro více dokumentů v rámci aplikace MDI.  
  
 [Postupy: Vytváření podřízených formulářů MDI](how-to-create-mdi-child-forms.md)  
 Poskytuje pokyny pro vytvoření jednoho nebo více oken, které pracují v nadřazeném formuláři MDI.  
  
 [Postupy: Určení podřízeného prvku aktivního MDI](how-to-determine-the-active-mdi-child.md)  
 Poskytuje pokyny k ověření podřízeného okna, které má fokus (a odeslání obsahu do schránky).  
  
 [Postupy: Odesílání dat do aktivního podřízeného MDI](how-to-send-data-to-the-active-mdi-child.md)  
 Poskytuje pokyny pro přenos informací do aktivního podřízeného okna.  
  
 [Postupy: Uspořádání podřízených formulářů MDI](how-to-arrange-mdi-child-forms.md)  
 Poskytuje pokyny pro dělení, kaskádové nebo uspořádávání podřízených oken aplikace MDI.

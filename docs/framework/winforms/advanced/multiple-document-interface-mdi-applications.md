---
title: Aplikace MDI (Multiple-Document Interface)
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 0ce7c66946d03d566b21473711cb6b3315885236
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61952045"
---
# <a name="multiple-document-interface-mdi-applications"></a>Aplikace MDI (Multiple-Document Interface)
Aplikace rozhraní více dokumentů (MDI) umožňují zobrazit více dokumentů současně, s každého dokumentu zobrazí v samostatném okně. Aplikace MDI mají často položky nabídky okna s podnabídky pro přepínání mezi windows nebo dokumenty.  
  
> [!NOTE]
>  Existují některé rozdíly v chování mezi formulářů MDI a interface jednoho dokumentu (SDI) systému windows ve Windows Forms. `Opacity` Vlastnost nemá vliv na vzhled podřízené formuláře MDI. Kromě toho <xref:System.Windows.Forms.Form.CenterToParent%2A> metoda nemá vliv na chování podřízené formuláře MDI.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytváření nadřazených formulářů MDI](how-to-create-mdi-parent-forms.md)  
 Poskytuje pokyny pro vytvoření kontejneru pro více dokumentů v rámci aplikace MDI.  
  
 [Postupy: Vytváření podřízených formulářů MDI](how-to-create-mdi-child-forms.md)  
 Poskytuje pokyny pro vytváření jeden nebo více oken, které působí v rámci nadřazený formulář MDI.  
  
 [Postupy: Určení podřízeného prvku aktivního MDI](how-to-determine-the-active-mdi-child.md)  
 Poskytuje pokyny pro ověření, který má právě fokus, podřízené okno (a odesílat její obsah do schránky.).  
  
 [Postupy: Odesílání dat do aktivního podřízeného MDI](how-to-send-data-to-the-active-mdi-child.md)  
 Poskytuje pokyny pro přenos informací na aktivní podřízené okno.  
  
 [Postupy: Uspořádání podřízených formulářů MDI](how-to-arrange-mdi-child-forms.md)  
 Poskytuje pokyny pro dělení do bloků, CSS a uspořádání podřízených oken MDI aplikace.

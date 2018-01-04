---
title: Aplikace MDI (Multiple-Document Interface)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 74735afcb1d6be319ad5d497615a3b725a4d5574
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="multiple-document-interface-mdi-applications"></a>Aplikace MDI (Multiple-Document Interface)
Aplikace rozhraní více dokumentů (MDI) umožňují zobrazit více dokumentů ve stejnou dobu, s každý dokument zobrazí v samostatném okně. Aplikace MDI mají často položku nabídky okno s dílčích pro přepínání mezi windows nebo dokumenty.  
  
> [!NOTE]
>  Existují určité rozdíly chování mezi MDI formuláře a systému windows (SDI) rozhraní s jedním dokumentem ve Windows Forms. `Opacity` Vlastnost nemá vliv na vzhled podřízených formulářů MDI. Kromě toho <xref:System.Windows.Forms.Form.CenterToParent%2A> – metoda neovlivňuje chování podřízených formulářů MDI.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytváření nadřazených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 Poskytuje pokyny pro vytváření kontejneru pro více dokumentů v rámci aplikace MDI.  
  
 [Postupy: Vytváření podřízených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 Poskytuje pokyny pro vytvoření jednoho nebo více windows, které fungují v rámci nadřazené formuláře MDI.  
  
 [Postupy: Určení podřízeného prvku aktivního MDI](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 Poskytuje pokyny pro ověření podřízeného okna, který má právě fokus, (a odesílat její obsah do schránky).  
  
 [Postupy: Odesílání dat do aktivního podřízeného MDI](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 Poskytuje pokyny pro přenos informací do okna aktivních podřízených.  
  
 [Postupy: Uspořádání podřízených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)  
 Poskytuje pokyny pro dlaždice, kaskádových nebo uspořádání podřízených oken MDI aplikace.

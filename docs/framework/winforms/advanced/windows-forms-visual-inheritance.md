---
title: "Vizuální dědění Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inheritance
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 857eb737-3602-4d49-bd8b-f70d33ace345
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 177b3034e9afc71a8ecc899364cc4911ef42a1a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-visual-inheritance"></a>Vizuální dědění Windows Forms
V některých případech může rozhodnout, že projekt vyžaduje formuláře podobně jako ten, který jste vytvořili v předchozím projektu. Nebo můžete chtít vytvořit základní formulář s nastavení jako vodoznak nebo určitých rozložení ovládacích prvků, který pak použijete znovu v rámci projektu, přičemž při každém opakování obsahující úpravy původní šablony formuláře. Dědičnost formulářů umožňuje vytvořit základní formulář a dědí při zachování aktivují původní nastavení, je nutné provést změny.  
  
 Odvozené třídy forms můžete vytvořit prostřednictvím kódu programu, nebo pomocí nástroje pro výběr dědičnost vizuálních prvků.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Dědění v modelu Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 Poskytuje pokyny pro vytváření zděděné formuláře v kódu.  
  
 [Postupy: Dědění formulářů pomocí dialogového okna Výběr dědičnosti](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)  
 Poskytuje pokyny pro vytvoření zděděné formuláře pomocí nástroje pro výběr dědičnosti.  
  
 [Účinky úpravy vzhledu základního formuláře](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 Poskytuje pokyny pro změnu ovládacích prvků ve formuláři základní a jejich vlastnosti.  
  
 [Návod: Demonstrace vizuálního dědění](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 Popisuje postup vytvoření základního formuláře Windows a jeho kompilace do knihovny tříd. Budete importovat této knihovny tříd do jiného projektu a vytvořit nový formulář, který dědí ze základní formulář.  
  
 [Postupy: Používání modifikátorů a vlastností GenerateMember](../../../../docs/framework/winforms/advanced/how-to-use-the-modifiers-and-generatemember-properties.md)  
 Poskytuje pokyny pro použití `GenerateMember` a `Modifiers` vlastnosti, které jsou relevantní, když Návrhář formulářů Windows vygeneruje členské proměnné pro součást.  
  
## <a name="related-sections"></a>Související oddíly  
 [Základní informace o dědičnosti (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 Popisuje, jak k definování tříd jazyka Visual Basic, které slouží jako základ pro jiné třídy.  
  
 [class](~/docs/csharp/language-reference/keywords/class.md)  
 Popisuje postup C# tříd, ve kterých je povolena jedna dědičnost.  
  
 [Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 Jsou uvedeny běžné problémy, které nastat u obslužné rutiny událostí v zděděné součásti

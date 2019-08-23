---
title: Vizuální dědění Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inheritance
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 857eb737-3602-4d49-bd8b-f70d33ace345
ms.openlocfilehash: 11a90615938da9e7dda5e05c55546918ccde137d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957106"
---
# <a name="windows-forms-visual-inheritance"></a>Vizuální dědění Windows Forms
V některých případech se můžete rozhodnout, že projekt volá pro formulář podobný tomu, který jste vytvořili v předchozím projektu. Nebo můžete chtít vytvořit základní formulář s nastavením, jako je například vodoznak nebo určité rozložení ovládacích prvků, které pak použijete v rámci projektu, přičemž každá iterace obsahuje změny původní šablony formuláře. Dědičnost formulářů umožňuje vytvořit základní formulář a pak z něj dědit a provádět úpravy a přitom zachovat libovolná původní nastavení, která potřebujete.  
  
 Formuláře odvozené třídy můžete vytvořit programově nebo pomocí výběru dědičnosti vizuálního rozhraní.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Zdědit model Windows Forms](how-to-inherit-windows-forms.md)  
 Poskytuje pokyny pro vytváření zděděných formulářů v kódu.  
  
 [Postupy: Dědění formulářů pomocí dialogového okna pro výběr dědičnosti](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)  
 Poskytuje pokyny pro vytváření zděděných formulářů pomocí výběru dědičnosti.  
  
 [Účinky úpravy vzhledu základního formuláře](effects-of-modifying-base-form-appearance.md)  
 Poskytuje pokyny pro změnu základního ovládacího prvku formuláře a jejich vlastností.  
  
 [Návod: Demonstrace vizuálního dědění](walkthrough-demonstrating-visual-inheritance.md)  
 Popisuje, jak vytvořit základní formulář Windows a zkompilovat ho do knihovny tříd. Tuto knihovnu tříd naimportujete do jiného projektu a vytvoříte nový formulář, který bude dědit ze základního formuláře.  
  
 [Postupy: Použití modifikátorů a vlastností GenerateMember](how-to-use-the-modifiers-and-generatemember-properties.md)  
 Poskytuje pokyny pro použití `GenerateMember` vlastností a `Modifiers` , které jsou relevantní, pokud Návrhář formulářů generuje členskou proměnnou pro komponentu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Základy dědičnosti (Visual Basic)](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 Popisuje, jak definovat Visual Basic třídy, které slouží jako základ pro jiné třídy.  
  
 [class](../../../csharp/language-reference/keywords/class.md)  
 Popisuje C# přístup tříd, ve kterých je povolena jednoduchá dědičnost.  
  
 [Řešení potíží se zděděnými obslužnými rutinami událostí v Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 Zobrazí běžné problémy, které vznikají u obslužných rutin událostí ve zděděných součástech.

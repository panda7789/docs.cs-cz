---
title: Vlastnosti v ovládacích prvcích Windows Forms, jež podporují pokyny pro usnadnění přístupu
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
ms.openlocfilehash: b466dcf42561d8ced7b224215538a807c94b174b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a>Vlastnosti v ovládacích prvcích Windows Forms, jež podporují pokyny pro usnadnění přístupu
Ovládací prvky na standardní sada nástrojů pro Windows Forms podporují řadu s pokyny, včetně vystavení fokus klávesnice a vystavení prvky obrazovky.  
  
## <a name="planning-ahead-for-accessibility"></a>Plánování předem pro usnadnění přístupu  
 Ovládací prvky vlastnosti můžete použít pro podporu další pokyny pro usnadnění přístupu, jak je znázorněno v následující tabulce. Kromě toho používejte nabídky k poskytování přístupu k součástí programu.  
  
|Vlastnost ovládacího prvku|Důležité informace týkající se usnadnění přístupu|  
|----------------------|--------------------------------------|  
|AccessibleDescription|Popis se hlásí k usnadnění, jako jsou třeba čtečky obrazovky. Usnadnění jsou specializované programy a zařízení, které pomáhají osoby s postižením efektivněji využívat počítače.|  
|AccessibleName|Název, který bude ohlášena pomůcek pro usnadnění.|  
|AccessibleRole|Popisuje použití elementu v uživatelském rozhraní.|  
|Pořadové číslo prvku|Vytvoří rozumný navigační cesta pomocí formuláře. Je důležité pro ovládací prvky bez vnitřní štítků, jako je například textová pole, jejich přidružené popisek bezprostředně je předcházet v pořadí.|  
|Text|Vytváření přístupových klíčů pomocí znaku "&". Použití přístupových klíčů je součástí poskytnout zdokumentovaných klávesnice přístup k vlastnostem.|  
|Velikost písma|Pokud není upravit velikost písma, pak je potřeba ho nastavit na 10 bodů nebo větší. Jakmile je nastavena velikost písma formuláře, všechny ovládací prvky přidán do formuláře po tomto datu bude mít stejnou velikost.|  
|ForeColor|Pokud je tato vlastnost nastavená na výchozí hodnoty, bude uživatelské předvolby barvu použít na formuláři.|  
|Barva pozadí|Pokud je tato vlastnost nastavená na výchozí hodnoty, bude uživatelské předvolby barvu použít na formuláři.|  
|BackgroundImage|Tuto vlastnost nezadáte tak čitelnost textu.|  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vytvoření přístupné aplikace Windows](../../../../docs/framework/winforms/advanced/walkthrough-creating-an-accessible-windows-based-application.md)

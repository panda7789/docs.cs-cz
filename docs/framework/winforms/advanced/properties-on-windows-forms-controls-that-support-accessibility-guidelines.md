---
title: Vlastnosti v ovládacích prvcích Windows Forms, jež podporují pokyny pro usnadnění přístupu
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
ms.openlocfilehash: b3f10fe472e449d39385facdbc716cba9b3f7382
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640492"
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a>Vlastnosti v ovládacích prvcích Windows Forms, jež podporují pokyny pro usnadnění přístupu
Ovládací prvky na standardní panel nástrojů pro Windows Forms podporují řadu přístupnosti včetně vystavení fokus klávesnice a jestli vystavuje prvky na obrazovce.  
  
## <a name="planning-ahead-for-accessibility"></a>Pro usnadnění přístupu budete plánovat předem  
 Ovládací prvky vlastnosti slouží k podpoře jiných přístupnosti, jak je znázorněno v následující tabulce. Kromě toho používejte nabídky a zajistit tak přístup k funkcím programu.  
  
|Vlastnosti ovládacího prvku|Důležité informace týkající se usnadnění přístupu|  
|----------------------|--------------------------------------|  
|AccessibleDescription|Popis se hlásí k usnadnění například čtečky obrazovky. Usnadnění jsou specializované programy a zařízení, která pomůže uživatelům s postižením používání počítačů efektivněji.|  
|AccessibleName|Název, který se ohlásí usnadnění.|  
|AccessibleRole|Popisuje použití prvku v uživatelském rozhraní.|  
|TabIndex|Vytvoří navigační cestu rozumné pomocí formuláře. Je důležité pro ovládací prvky bez vnitřní popisky, jako je například textová pole, jejich přidružené popisek bezprostředně předcházet je v pořadí.|  
|Text|Vytváření přístupových klíčů pomocí znaku "&". Pomocí přístupových klíčů je součástí poskytuje zdokumentovaných klávesnici přístup k funkcím.|  
|Velikost písma|Pokud není měnitelné velikost písma, pak ho měli byste nastavit 10 bodů nebo větší. Jakmile je nastavit velikost písma formuláře, všechny ovládací prvky do formuláře přidán po tomto datu bude mít stejnou velikost.|  
|Barva popředí|Pokud je tato vlastnost nastavena na výchozí hodnotu, se barva předvolby uživatele používat ve formuláři.|  
|Barva pozadí|Pokud je tato vlastnost nastavena na výchozí hodnotu, se barva předvolby uživatele používat ve formuláři.|  
|BackgroundImage|Tuto vlastnost nechte prázdnou čitelnost textu.|  
  
## <a name="see-also"></a>Viz také:

- [Návod: Vytvoření přístupné aplikace založené na Windows](walkthrough-creating-an-accessible-windows-based-application.md)

---
title: Zachycení myši ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: dfe983b9e407eddb9bed3bcc1a767cdeff38f2ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538405"
---
# <a name="mouse-capture-in-windows-forms"></a>Zachycení myši ve Windows Forms
*Zachycení myši* údaj udává, kdy ovládacího prvku trvá příkaz Všechny myši vstup. V případě, že zachycení myši ovládacího prvku obdrží vstup z myši, zda je ukazatel je v rámci svých hranic.  
  
## <a name="setting-mouse-capture"></a>Nastavení zachycení myši  
 V systému Windows Forms myši zachyceny ovládacího prvku, když uživatel stiskne tlačítko myši v ovládacím prvku a uvolnění myši v ovládacím prvku když uživatel uvolní tlačítko myši.  
  
 <xref:System.Windows.Forms.Control.Capture%2A> Vlastnost <xref:System.Windows.Forms.Control> třída určuje, zda má ovládacího prvku zaznamenány myši. Pokud chcete zjistit, kdy ovládací prvek ztratí zachycení myši, zpracování <xref:System.Windows.Forms.Control.MouseCaptureChanged> událostí.  
  
 Pouze okno popředí můžete zaznamenat myši. Pokud okno pozadí se pokusí zaznamenat myš, okno přijímá zprávy pouze pro události myši, které dojít, když ukazatel myši nachází v viditelné části okna. Navíc i v případě zachycení myši okno popředí uživatele stále můžete pomocí tlačítka Další okno, převedení do popředí. Při zachytávání myši nefungují klávesové zkratky.  
  
## <a name="see-also"></a>Viz také  
 [Vstup z myši v aplikaci Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)

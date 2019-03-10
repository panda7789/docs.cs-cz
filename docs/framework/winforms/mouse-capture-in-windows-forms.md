---
title: Zachycení myši ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: afb58df99ea30f5e7e6ab5b9156af195d273c44d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712705"
---
# <a name="mouse-capture-in-windows-forms"></a>Zachycení myši ve Windows Forms
*Zachycení myši* odkazuje na příkaz všechny vstup myši pořízením ovládacího prvku. Když ovládací prvek zachytí myš, zda ukazatel je v rámci jeho okrajů přijímá vstup z myši.  
  
## <a name="setting-mouse-capture"></a>Zachycení myši nastavení  
 Ve Windows Forms myši nezachytává ovládacího prvku, když uživatel stiskne tlačítko myši v ovládacím prvku a uvolní se ukazatel myši ovládacím prvkem, když uživatel uvolní tlačítko myši.  
  
 <xref:System.Windows.Forms.Control.Capture%2A> Vlastnost <xref:System.Windows.Forms.Control> třída určuje, zda ovládací prvek zachytí myš. Pokud chcete zjistit, kdy ovládací prvek ztratí zachycení myši, zpracovat <xref:System.Windows.Forms.Control.MouseCaptureChanged> událostí.  
  
 Pouze okno v popředí, můžete zachytit ukazatel myši. Když se pokusí oknem v pozadí pro zachycení myši, v okně přijímá zprávy pouze pro události myši, ke kterým dochází, když ukazatel myši nachází v viditelnou část okna. Navíc i v případě, že okno v popředí zachytí myš, stále kliknutí další okno, přináší na popředí. Když ukazatel myši je zachycena, nebude fungovat klávesové zkratky.  
  
## <a name="see-also"></a>Viz také:
- [Vstup z myši v aplikaci Windows Forms](mouse-input-in-a-windows-forms-application.md)

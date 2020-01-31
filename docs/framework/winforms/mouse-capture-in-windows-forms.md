---
title: Zachycení myši
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: 10583f074831b16dce3c713b4ac9a76c7005c9f5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741016"
---
# <a name="mouse-capture-in-windows-forms"></a>Zachycení myši ve Windows Forms
*Zachycení myši* odkazuje na to, že ovládací prvek provede příkaz pro všechny vstupy myši. Když ovládací prvek zachytí myš, dostane vstup z myši bez ohledu na to, zda je ukazatel v rámci jeho ohraničení.  
  
## <a name="setting-mouse-capture"></a>Nastavení zachycení myši  
 V model Windows Forms je myš zachycena ovládacím prvkem, když uživatel stiskne tlačítko myši na ovládacím prvku a myš je uvolněna ovládacím prvkem, když uživatel uvolní tlačítko myši.  
  
 Vlastnost <xref:System.Windows.Forms.Control.Capture%2A> třídy <xref:System.Windows.Forms.Control> určuje, zda ovládací prvek zachytil myš. Chcete-li zjistit, kdy ovládací prvek ztratí zachycení myši, zpracujte událost <xref:System.Windows.Forms.Control.MouseCaptureChanged>.  
  
 Myš může zachytit pouze okno v popředí. Když se okno na pozadí pokusí zachytit myš, okno obdrží zprávy pouze pro události myši, ke kterým dojde, když je ukazatel myši v viditelné části okna. I když je v okně popředí zachycena myš, uživatel může stále kliknout na jiné okno a přemístit ho do popředí. Když je myš zachycena, klávesové zkratky nefungují.  
  
## <a name="see-also"></a>Viz také:

- [Vstup z myši v aplikaci Windows Forms](mouse-input-in-a-windows-forms-application.md)

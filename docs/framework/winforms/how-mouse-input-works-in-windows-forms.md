---
title: "Jak funguje vstup myši ve Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, mouse input
- mouse [Windows Forms], input
ms.assetid: 48fc5240-75a6-44bf-9fce-6aa21b49705a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 20de05b5df3737ccc525cb50c81b51bcba766287
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-mouse-input-works-in-windows-forms"></a>Jak funguje vstup myši ve Windows Forms
Přijímání a zpracování vstup z myši, je důležitou součástí každé aplikací systému Windows. Můžete zpracování událostí myši k provedení akce v aplikaci nebo použít informace o umístění myši provést přístupů testování nebo jiné akce. Kromě toho můžete změnit způsob ovládacích prvků ve vaší aplikaci zpracovávat vstup z myši. Toto téma popisuje tyto události myši ve podrobností a získání a nastavení systému pro myši. Další informace o dostupných pomocí myši dat jsou vyvolány události a pořadí, ve kterém události kliknutí myší, najdete v části [události myši ve Windows Forms](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).  
  
## <a name="mouse-location-and-hit-testing"></a>Umístění myši a stiskněte klávesu testování  
 Pokud se uživatel přesune myš, operační systém přesune ukazatel myši. Ukazatele myši obsahuje jeden pixelů, názvem aktivního bodu, který operační systém sleduje a rozpozná jako pozici ukazatele. Když uživatel přesune myši nebo stiskne tlačítko myši, <xref:System.Windows.Forms.Control> obsahující <xref:System.Windows.Forms.Cursor.HotSpot%2A> vyvolá událost odpovídající myší. Můžete získat aktuální pozici myši s <xref:System.Windows.Forms.MouseEventArgs.Location%2A> vlastnost <xref:System.Windows.Forms.MouseEventArgs> při zpracování události myši nebo pomocí <xref:System.Windows.Forms.Cursor.Position%2A> vlastnost <xref:System.Windows.Forms.Cursor> – třída. Lze následně použít informace o umístění myši provést testování stiskněte klávesu a proveďte akci, na základě umístění myši. Testování podle funkce je založená na několik ovládacích prvků ve Windows Forms, jako <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.MonthCalendar> a <xref:System.Windows.Forms.DataGridView> ovládací prvky. Použít s událost odpovídající myší, <xref:System.Windows.Forms.Control.MouseHover> například vstupů do testování je velmi užitečné pro určení, kdy aplikace by měla odpovídat určité akci.  
  
## <a name="mouse-events"></a>Události myši  
 Primární způsob reakce na vstup z myši je zpracování událostí myši. Následující tabulka ukazuje událostí myši a popisuje, když jsou vyvolány.  
  
|Události myši|Popis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.Click>|K této události dochází při uvolnění tlačítka myši, obvykle před <xref:System.Windows.Forms.Control.MouseUp> událostí. Obslužná rutina pro tuto událost přijme argument typu <xref:System.EventArgs>. Zpracujte tuto událost, pokud potřebujete zjistit při kliknutí.|  
|<xref:System.Windows.Forms.Control.MouseClick>|K této události dojde, když uživatel klikne ovládacího prvku pomocí myši. Obslužná rutina pro tuto událost přijme argument typu <xref:System.Windows.Forms.MouseEventArgs>. Zpracujte tuto událost, pokud potřebujete získat informace o myši při kliknutí.|  
|<xref:System.Windows.Forms.Control.DoubleClick>|Tato událost nastane při poklepání na ovládací prvek. Obslužná rutina pro tuto událost přijme argument typu <xref:System.EventArgs>. Zpracujte tuto událost, pokud potřebujete zjistit, když dojde k poklikejte na soubor.|  
|<xref:System.Windows.Forms.Control.MouseDoubleClick>|K této události dochází při poklepání ovládacího prvku pomocí myši. Obslužná rutina pro tuto událost přijme argument typu <xref:System.Windows.Forms.MouseEventArgs>. Zpracujte tuto událost, pokud potřebujete získat informace o myš, když dojde k poklikejte na soubor.|  
|<xref:System.Windows.Forms.Control.MouseDown>|K této události dojde, pokud je ukazatel myši nad ovládacího prvku a uživatel stiskne tlačítko myši. Obslužná rutina pro tuto událost přijme argument typu <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseEnter>|K této události dojde, když ukazatel myši zadá oblasti klienta nebo ohraničení ovládacího prvku, v závislosti na typu ovládacího prvku. Obslužná rutina pro tuto událost přijme argument typu <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseHover>|K této události dojde, když ukazatel myši zastaví a postavená na ovládací prvek. Obslužná rutina pro tuto událost přijme argument typu <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseLeave>|Tato událost nastane, když ukazatel myši opustí oblasti klienta nebo ohraničení ovládacího prvku, v závislosti na typu ovládacího prvku. Obslužná rutina pro tuto událost přijme argument typu <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseMove>|K této události dojde, pokud se ukazatel myši přesune i když je prostřednictvím ovládacího prvku. Obslužná rutina pro tuto událost přijme argument typu <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseUp>|K této události dojde, pokud je ukazatel myši nad ovládacího prvku a uživatel uvolní tlačítko myši. Obslužná rutina pro tuto událost přijme argument typu <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseWheel>|K této události dojde, když uživatel otočí kolečka myši, když má právě fokus, ovládacího prvku. Obslužná rutina pro tuto událost přijme argument typu <xref:System.Windows.Forms.MouseEventArgs>. Můžete použít <xref:System.Windows.Forms.MouseEventArgs.Delta%2A> vlastnost <xref:System.Windows.Forms.MouseEventArgs> k určení, jak daleko je přesunut myši oblasti.|  
  
## <a name="changing-mouse-input-and-detecting-system-settings"></a>Změna vstup z myši a zjišťování nastavení systému  
 Můžete zjišťovat a změnit způsob ovládacího prvku zpracovává vstup z myši odvozování z ovládacího prvku a pomocí <xref:System.Windows.Forms.Control.GetStyle%2A> a <xref:System.Windows.Forms.Control.SetStyle%2A> metody. <xref:System.Windows.Forms.Control.SetStyle%2A> Metoda přebírá bitovou kombinaci <xref:System.Windows.Forms.ControlStyles> hodnoty k určení, zda ovládací prvek bude mít standard, klikněte na tlačítko nebo dvakrát kliknout na chování nebo pokud ovládací prvek zpracuje vlastní zpracování myši. Kromě toho <xref:System.Windows.Forms.SystemInformation> třídy obsahuje vlastnosti, které popisují možnosti myši a určete, jak myš komunikuje s operačním systémem. Následující tabulka shrnuje tyto vlastnosti.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>|Získá dimenze, v pixelech, oblasti, ve kterém uživatel musí kliknout na dvakrát pro operační systém, které je třeba zvážit dva klikne poklikejte na soubor.|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A>|Získá maximální počet milisekund, po které může uplynout mezi první kliknutí a druhý klikněte na tlačítko pro operační systém vzít v úvahu akce myši poklikejte na soubor.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtons%2A>|Získá počet tlačítka myši.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtonsSwapped%2A>|Získá hodnotu označující, zda byla prohodily funkce tlačítek vlevo a vpravo myši.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverSize%2A>|Získá dimenze, v pixelech obdélníku, ve kterém má ukazatel myši setrvá po dobu ukazování myši, než se vygeneruje zpráva při přechodu myší.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverTime%2A>|Získá dobu v milisekundách, která má ukazatel myši zůstat v obdélníku hover, než se vygeneruje zpráva při přechodu myší.|  
|<xref:System.Windows.Forms.SystemInformation.MousePresent%2A>|Získá hodnotu označující, zda je nainstalována myši.|  
|<xref:System.Windows.Forms.SystemInformation.MouseSpeed%2A>|Získá hodnotu označující, aktuální rychlost myši, z 1 až 20 číslic.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelPresent%2A>|Získá hodnotu označující, zda je nainstalována s kolečko myši.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollDelta%2A>|Získá množství rozdílová hodnota přírůstku rotaci kolečka myši.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollLines%2A>|Získá počet řádků posunu při kolečka myši otočen.|  
  
## <a name="see-also"></a>Viz také  
 [Vstup z myši ve Windows Forms aplikace](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 [Zachycení myši ve Windows Forms](../../../docs/framework/winforms/mouse-capture-in-windows-forms.md)  
 [Ukazatele myši ve Windows Forms](../../../docs/framework/winforms/mouse-pointers-in-windows-forms.md)

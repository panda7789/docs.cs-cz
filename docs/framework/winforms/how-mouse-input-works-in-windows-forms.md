---
title: Jak funguje vstup myši ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, mouse input
- mouse [Windows Forms], input
ms.assetid: 48fc5240-75a6-44bf-9fce-6aa21b49705a
ms.openlocfilehash: c9193ffa9ef34f1e43a92feec230fa2282264147
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203012"
---
# <a name="how-mouse-input-works-in-windows-forms"></a>Jak funguje vstup myši ve Windows Forms
Příjem a zpracování vstup z myši je důležitou součástí každé aplikace Windows. Můžete zpracovávat události myši k provedení akce ve vaší aplikaci nebo pomocí myši umístění informace o provedení volání testování nebo jiné akce. Kromě toho můžete změnit způsob, jakým ovládací prvky ve vaší aplikaci zpracovávat vstup z myši. Toto téma popisuje tyto události myši ve podrobností a získání a nastavení systému pro myš. Další informace o datech pomocí myši k dispozici jsou vyvolány události a pořadí, ve kterém události kliknutí myší, přečtěte si téma [události myši ve Windows Forms](mouse-events-in-windows-forms.md).  
  
## <a name="mouse-location-and-hit-testing"></a>Kurzor myši a spuštění testu  
 Když se uživatel přesune ukazatel myši, operační systém přesune ukazatel myši. Ukazatel myši obsahuje jeden pixel, volá aktivního bodu, který sleduje operačního systému a rozpozná jako pozici ukazatele. Když uživatel pohybuje ukazatelem myši nebo stiskne tlačítko myši, <xref:System.Windows.Forms.Control> obsahující <xref:System.Windows.Forms.Cursor.HotSpot%2A> vyvolává událost odpovídající myší. Můžete získat aktuální pozice myši s <xref:System.Windows.Forms.MouseEventArgs.Location%2A> vlastnost <xref:System.Windows.Forms.MouseEventArgs> při zpracování události myši nebo pomocí <xref:System.Windows.Forms.Cursor.Position%2A> vlastnost <xref:System.Windows.Forms.Cursor> třídy. Lze následně použít informace o umístění myši k provedení spuštění testu a provést akci na základě umístění myši. Možnost spuštění testu je založená na několik ovládacích prvků ve Windows Forms, jako <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.MonthCalendar> a <xref:System.Windows.Forms.DataGridView> ovládací prvky. Použít s událostí myši odpovídající <xref:System.Windows.Forms.Control.MouseHover> například spuštění testu je velmi užitečné pro určení, kdy má vaše aplikace provést konkrétní akce.  
  
## <a name="mouse-events"></a>Události myši  
 Primárním způsob, jak reagovat na vstup z myši se pro zpracování událostí myši. Následující tabulka zobrazuje události myši a popisuje, když jsou vyvolány.  
  
|Události myši|Popis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.Click>|K této události dochází, když se uvolní tlačítko myši, obvykle před <xref:System.Windows.Forms.Control.MouseUp> událostí. Obslužné rutiny pro tuto událost přijme argument typu <xref:System.EventArgs>. Zpracujte tuto událost, pokud je potřeba jenom určit, kdy dojde k kliknutí.|  
|<xref:System.Windows.Forms.Control.MouseClick>|Když uživatel klikne ovládací prvek pomocí myši, dojde k této události. Obslužné rutiny pro tuto událost přijme argument typu <xref:System.Windows.Forms.MouseEventArgs>. Zpracujte tuto událost, pokud je potřeba získat informace o myši při kliknutí výskytu.|  
|<xref:System.Windows.Forms.Control.DoubleClick>|Tato událost se vyvolá při poklepání na ovládací prvek. Obslužné rutiny pro tuto událost přijme argument typu <xref:System.EventArgs>. Zpracujte tuto událost, pokud je potřeba jenom určit, kdy dojde k poklepání.|  
|<xref:System.Windows.Forms.Control.MouseDoubleClick>|Když uživatel dvakrát klikne ovládací prvek pomocí myši, dojde k této události. Obslužné rutiny pro tuto událost přijme argument typu <xref:System.Windows.Forms.MouseEventArgs>. Zpracujte tuto událost, pokud je potřeba získat informace o myši, dojde-li k poklepání.|  
|<xref:System.Windows.Forms.Control.MouseDown>|Když je ukazatel myši nad ovládací prvek a uživatel stiskne tlačítko myši, dojde k této události. Obslužné rutiny pro tuto událost přijme argument typu <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseEnter>|Při vstupu ukazatele myši do oblasti klienta nebo ohraničení ovládacího prvku, v závislosti na typu ovládacího prvku dojde k této události. Obslužné rutiny pro tuto událost přijme argument typu <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseHover>|Tato událost nastane, pokud ukazatel myši zastaví a postavená na ovládací prvek. Obslužné rutiny pro tuto událost přijme argument typu <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseLeave>|Tato událost nastane, pokud ukazatel myši opustí ohraničení nebo klientské oblasti ovládacího prvku, v závislosti na typu ovládacího prvku. Obslužné rutiny pro tuto událost přijme argument typu <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseMove>|Tato událost nastane, pokud ukazatel myši pohybuje, zatímco je nad ovládací prvek. Obslužné rutiny pro tuto událost přijme argument typu <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseUp>|Když je ukazatel myši nad ovládací prvek a uživatel uvolní tlačítko myši, dojde k této události. Obslužné rutiny pro tuto událost přijme argument typu <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseWheel>|Tato událost nastane, pokud uživatel otáčí kolečkem myši, zatímco ovládací prvek má fokus. Obslužné rutiny pro tuto událost přijme argument typu <xref:System.Windows.Forms.MouseEventArgs>. Můžete použít <xref:System.Windows.Forms.MouseEventArgs.Delta%2A> vlastnost <xref:System.Windows.Forms.MouseEventArgs> k určení, jak daleko se posunul myši.|  
  
## <a name="changing-mouse-input-and-detecting-system-settings"></a>Změna vstup z myši a zjišťování nastavení systému  
 Můžete zjišťovat a změnit tak, jak ovládací prvek zpracovává vstup z myši odvozený z ovládacího prvku a použitím <xref:System.Windows.Forms.Control.GetStyle%2A> a <xref:System.Windows.Forms.Control.SetStyle%2A> metody. <xref:System.Windows.Forms.Control.SetStyle%2A> Metoda přijímá bitová kombinace hodnot <xref:System.Windows.Forms.ControlStyles> hodnoty určující, zda bude mít ovládací standard klepněte nebo klikněte dvakrát na chování nebo pokud ovládací prvek bude zpracovávat své vlastní zpracování myši. Kromě toho <xref:System.Windows.Forms.SystemInformation> třída obsahuje vlastnosti, které popisují funkce myší a určení způsobu interakce myši v operačním systému. V následující tabulce najdete souhrn těchto vlastností.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>|Získá dimenzí, v pixelech, oblasti, ve které musí uživatel kliknout dvakrát pro operační systém vzít v úvahu dvě kliknutí dvojím kliknutím.|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A>|Získá maximální počet milisekund, po které může uplynout mezi prvním kliknutí a druhý klikněte na tlačítko pro operační systém vzít v úvahu dvakrát klikněte na akci myši.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtons%2A>|Získá počet tlačítka myši.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtonsSwapped%2A>|Získá hodnotu označující, zda byla Prohodit funkce tlačítka myši doleva a doprava.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverSize%2A>|Získá dimenzí, v pixelech obdélník, ve kterém má ukazatel myši setrvá dobu myši při najetí myší, než se vygeneruje zpráva myši při najetí myší.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverTime%2A>|Získá čas v milisekundách, která má ukazatel myši setrvá ve obdélník hover předtím, než se vygeneruje zpráva myši při najetí myší.|  
|<xref:System.Windows.Forms.SystemInformation.MousePresent%2A>|Získá hodnotu označující, zda je nainstalována myši.|  
|<xref:System.Windows.Forms.SystemInformation.MouseSpeed%2A>|Získá hodnotu určující aktuální rychlost myši, od 1 do 20.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelPresent%2A>|Získá hodnotu označující, zda je nainstalována myš s kolečkem myši.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollDelta%2A>|Získá množství rozdílová hodnota přírůstku otáčení kolečka myši.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollLines%2A>|Získá počet řádků posunu otáčí kolečkem myši.|  
  
## <a name="see-also"></a>Viz také:

- [Vstup z myši v aplikaci Windows Forms](mouse-input-in-a-windows-forms-application.md)
- [Zachycení myši ve Windows Forms](mouse-capture-in-windows-forms.md)
- [Ukazatele myši ve Windows Forms](mouse-pointers-in-windows-forms.md)

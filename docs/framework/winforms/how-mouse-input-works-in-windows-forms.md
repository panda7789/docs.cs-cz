---
title: Jak funguje vstup myši
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, mouse input
- mouse [Windows Forms], input
ms.assetid: 48fc5240-75a6-44bf-9fce-6aa21b49705a
ms.openlocfilehash: 1164974e65ca1e96c0650569626ad4140baf004e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739634"
---
# <a name="how-mouse-input-works-in-windows-forms"></a>Jak funguje vstup myši ve Windows Forms
Přijímání a zpracování vstupu myši je důležitou součástí každé aplikace systému Windows. Události myši lze zpracovávat k provedení akce v aplikaci nebo můžete použít informace o poloze myši k provádění testování přístupů nebo jiných akcí. Kromě toho můžete změnit způsob, jakým ovládací prvky v aplikaci zpracovávají vstupy z myši. V tomto tématu jsou popsány tyto události myši podrobněji a jak získat a změnit nastavení systému pro myš. Další informace o datech dodaných s událostmi myši a pořadí, ve kterém jsou události kliknutí myši vyvolány, naleznete [v tématu události myši v model Windows Forms](mouse-events-in-windows-forms.md).  
  
## <a name="mouse-location-and-hit-testing"></a>Umístění myši a testování přístupů  
 Když uživatel přesune myš, operační systém přesune ukazatel myši. Ukazatel myši obsahuje jeden pixel, který se označuje jako aktivní bod, který operační systém sleduje a rozpoznává jako pozici ukazatele. Když uživatel přesune myš nebo stiskne tlačítko myši, <xref:System.Windows.Forms.Control> obsahující <xref:System.Windows.Forms.Cursor.HotSpot%2A> vyvolá příslušnou událost myši. Aktuální polohu myši můžete získat pomocí vlastnosti <xref:System.Windows.Forms.MouseEventArgs.Location%2A> <xref:System.Windows.Forms.MouseEventArgs> při zpracování události myši nebo pomocí vlastnosti <xref:System.Windows.Forms.Cursor.Position%2A> třídy <xref:System.Windows.Forms.Cursor>. Můžete následně použít informace o poloze myši k provedení testování shody a pak provést akci na základě polohy myši. Funkce testování přístupů je integrována do několika ovládacích prvků v model Windows Forms, jako jsou například <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.MonthCalendar> a <xref:System.Windows.Forms.DataGridView> ovládací prvky. V případě použití s příslušnou událostí myši <xref:System.Windows.Forms.Control.MouseHover> například testování shody je velmi užitečné pro určení, kdy by měla aplikace provádět určitou akci.  
  
## <a name="mouse-events"></a>Události myši  
 Hlavním způsobem, jak reagovat na vstup myši, je zpracování událostí myši. Následující tabulka ukazuje události myši a popisuje, kdy jsou vyvolány.  
  
|Událost myši|Popis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.Click>|Tato událost nastane, když se uvolní tlačítko myši, obvykle před událostí <xref:System.Windows.Forms.Control.MouseUp>. Obslužná rutina pro tuto událost obdrží argument typu <xref:System.EventArgs>. Zpracujte tuto událost, pokud potřebujete určit, kdy dojde k kliknutí.|  
|<xref:System.Windows.Forms.Control.MouseClick>|K této události dojde, když uživatel klikne na ovládací prvek pomocí myši. Obslužná rutina pro tuto událost obdrží argument typu <xref:System.Windows.Forms.MouseEventArgs>. Zpracuje tuto událost, pokud potřebujete získat informace o myši, když dojde k kliknutí.|  
|<xref:System.Windows.Forms.Control.DoubleClick>|Tato událost nastane při dvojitém kliknutí na ovládací prvek. Obslužná rutina pro tuto událost obdrží argument typu <xref:System.EventArgs>. Zpracujte tuto událost, pokud potřebujete určit, kdy dojde k dvojitému kliknutí.|  
|<xref:System.Windows.Forms.Control.MouseDoubleClick>|K této události dojde, když uživatel dvakrát klikne na ovládací prvek pomocí myši. Obslužná rutina pro tuto událost obdrží argument typu <xref:System.Windows.Forms.MouseEventArgs>. Zpracuje tuto událost, pokud potřebujete získat informace o ukazateli myši, když dojde k dvojitému kliknutí.|  
|<xref:System.Windows.Forms.Control.MouseDown>|K této události dojde, když je ukazatel myši nad ovládacím prvkem a uživatel stiskne tlačítko myši. Obslužná rutina pro tuto událost obdrží argument typu <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseEnter>|K této události dojde, když ukazatel myši vstoupí do oblasti ohraničení nebo klienta ovládacího prvku, v závislosti na typu ovládacího prvku. Obslužná rutina pro tuto událost obdrží argument typu <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseHover>|Tato událost nastane, když se ukazatel myši zastaví a umístí nad ovládací prvek. Obslužná rutina pro tuto událost obdrží argument typu <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseLeave>|Tato událost nastane, pokud ukazatel myši opustí ohraničení nebo klientskou oblast ovládacího prvku, v závislosti na typu ovládacího prvku. Obslužná rutina pro tuto událost obdrží argument typu <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseMove>|Tato událost nastane, když se ukazatel myši pohybuje, zatímco se nachází nad ovládacím prvkem. Obslužná rutina pro tuto událost obdrží argument typu <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseUp>|K této události dojde, když je ukazatel myši nad ovládacím prvkem a uživatel uvolní tlačítko myši. Obslužná rutina pro tuto událost obdrží argument typu <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseWheel>|Tato událost nastane, pokud uživatel otáčí kolečkem myši v době, kdy má ovládací prvek fokus. Obslužná rutina pro tuto událost obdrží argument typu <xref:System.Windows.Forms.MouseEventArgs>. Vlastnost <xref:System.Windows.Forms.MouseEventArgs.Delta%2A> <xref:System.Windows.Forms.MouseEventArgs> můžete použít k určení, jak daleko se myš posouvá.|  
  
## <a name="changing-mouse-input-and-detecting-system-settings"></a>Změna vstupu myši a detekce nastavení systému  
 Můžete detekovat a měnit způsob, jakým ovládací prvek zpracovává vstup z myši odvozený od ovládacího prvku a pomocí <xref:System.Windows.Forms.Control.GetStyle%2A> a <xref:System.Windows.Forms.Control.SetStyle%2A>ch metod. Metoda <xref:System.Windows.Forms.Control.SetStyle%2A> přebírá bitovou kombinaci hodnot <xref:System.Windows.Forms.ControlStyles>, aby bylo možné určit, zda ovládací prvek bude mít standardní kliknutí nebo dvakrát kliknout na chování, nebo zda bude ovládací prvek zpracovávat vlastní zpracování myši. Kromě toho třída <xref:System.Windows.Forms.SystemInformation> obsahuje vlastnosti, které popisují funkce myši a určují, jak ukazatel myši komunikuje s operačním systémem. Tyto vlastnosti jsou shrnuté v následující tabulce.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>|Získá dimenze v pixelech, ve kterých musí uživatel kliknout dvakrát, aby mohl operační systém považovat dvě kliknutí na dvakrát kliknout.|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A>|Získá maximální počet milisekund, které mohou uplynout mezi prvním kliknutím a druhým kliknutím na operační systém, aby bylo možné poklepat na akci myši.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtons%2A>|Získá počet tlačítek myši.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtonsSwapped%2A>|Získá hodnotu, která označuje, zda byly záměna funkcí levého a pravého tlačítka myši.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverSize%2A>|Získá v pixelech obdélník, ve kterém má ukazatel myši zůstat v době, kdy se má vygenerovat zpráva při přechodu myší.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverTime%2A>|Získá čas (v milisekundách), po který musí ukazatel myši zůstat v obdélníku s ukazatelem myši, aby se vygenerovala zpráva o přetažení myší.|  
|<xref:System.Windows.Forms.SystemInformation.MousePresent%2A>|Načte hodnotu, která označuje, jestli je nainstalovaná myš.|  
|<xref:System.Windows.Forms.SystemInformation.MouseSpeed%2A>|Načte hodnotu, která označuje aktuální rychlost myši, od 1 do 20.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelPresent%2A>|Načte hodnotu, která označuje, jestli je nainstalovaná myš s kolečkem myši.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollDelta%2A>|Získá velikost rozdílové hodnoty přírůstku jednoduchého otočení myši.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollLines%2A>|Získá počet řádků, které se mají posunout při otočení kolečka myši.|  
  
## <a name="see-also"></a>Viz také

- [Vstup z myši v aplikaci Windows Forms](mouse-input-in-a-windows-forms-application.md)
- [Zachycení myši ve Windows Forms](mouse-capture-in-windows-forms.md)
- [Ukazatele myši ve Windows Forms](mouse-pointers-in-windows-forms.md)

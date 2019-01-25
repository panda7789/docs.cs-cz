---
title: Uživatelský vstup ve formulářové aplikaci Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, user input
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
ms.openlocfilehash: a47a35cffb99648737245031a558db884024c011
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684077"
---
# <a name="user-input-in-a-windows-forms-application"></a>Uživatelský vstup ve formulářové aplikaci Windows
Ve Windows Forms uživatelský vstup přijde na aplikace ve formě zpráv Windows. Řadu přepisovatelné metody zpracování těchto zpráv na úrovni aplikace, formuláře a řídit. Tyto metody přijímat zprávy myši a klávesnice, vyvolají události, které může být zpracována pro získání informací o myši nebo klávesnice vstup. V mnoha případech bude schopná zpracovat veškerý vstup uživatele jednoduše tak, že zpracování těchto událostí aplikace Windows Forms. V jiných případech může aplikace potřebovat k přepsání metod, které zpracovávají zprávy, aby se zachytily určité zprávy předtím, než je přijatých aplikací, formulář nebo ovládací prvek.  
  
## <a name="mouse-and-keyboard-events"></a>Události klávesnice a myši  
 Všechny ovládací prvky Windows Forms dědí sadu události týkající se myši a klávesnice. Například může zpracovat ovládacího prvku <xref:System.Windows.Forms.Control.KeyPress> může zpracovávat události a určit kód znaku klávesy, která byla stisknuta v okamžiku nebo ovládacího prvku <xref:System.Windows.Forms.Control.MouseClick> událostí k určení umístění myši klikněte na tlačítko. Další informace o události myši a klávesnice, naleznete v tématu [použití událostí klávesnice](../../../docs/framework/winforms/using-keyboard-events.md) a [události myši ve Windows Forms](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).  
  
## <a name="methods-that-process-user-input-messages"></a>Metody, které zpracovávají zprávy o zadávání uživatele  
 Formuláře a ovládací prvky mají přístup k <xref:System.Windows.Forms.IMessageFilter> rozhraní a sada přepisovatelné metody, které zpracovávají zprávy Windows v různých fázích fronty zpráv. Tyto metody, které mají <xref:System.Windows.Forms.Message> parametr, který zapouzdřuje detailech zpráv Windows. Můžete implementovat nebo přepsat tyto metody zkontrolujte zprávy a poté využívat zprávy nebo předat do další příjemci ve frontě zpráv. Následující tabulka představuje metody, které zpracovávat všechny zprávy Windows ve Windows Forms.  
  
|Metoda|Poznámky|  
|------------|-----------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|Tato metoda zachycuje ve frontě (označované také jako publikované) Windows zprávy na úrovni aplikace.|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|Tato metoda zachycuje Windows zpráv na úrovni formuláře a ovládací prvek předtím, než byla zpracována.|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|Tato metoda zpracovává zprávy Windows na úrovni formuláře a ovládací prvek.|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|Tato metoda provádí výchozí zpracování zpráv Windows na úrovni formuláře a ovládací prvek. To poskytuje funkci minimální okna.|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|Tato metoda zachycuje zpráv na úrovni formuláře a ovládací prvek po jejich zpracování. <xref:System.Windows.Forms.ControlStyles.EnableNotifyMessage> Bit stylu musí být nastaven pro tuto metodu, která se má volat.|  
  
 Klávesnice a myši zprávy jsou zpracovány také další sadu přepisovatelné metody, které jsou specifické pro tyto typy zpráv. Další informace najdete v tématu [jak funguje vstup klávesnice](../../../docs/framework/winforms/how-keyboard-input-works.md) a [jak funguje myši vstup ve Windows Forms](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md).  
  
## <a name="see-also"></a>Viz také:
- [Uživatelský vstup ve Windows Forms](../../../docs/framework/winforms/user-input-in-windows-forms.md)
- [Vstup z klávesnice v aplikaci Windows Forms](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)
- [Vstup z myši v aplikaci Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)

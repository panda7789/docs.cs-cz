---
title: Vstup uživatele v aplikaci model Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, user input
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
ms.openlocfilehash: 8e82276f14519c4ef54948744c93014232bdff52
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734804"
---
# <a name="user-input-in-a-windows-forms-application"></a>Uživatelský vstup v aplikaci Windows Forms
V model Windows Forms se vstup uživatele odesílá do aplikací ve formě zpráv Windows. Řada přepsatelné metody zpracovává tyto zprávy na úrovni aplikace, formuláře a ovládacího prvku. Když tyto metody dostanou zprávy myši a klávesnice, vyvolávají události, které mohou být zpracovány za účelem získání informací o vstupu myši nebo klávesnice. V mnoha případech model Windows Forms aplikace budou moci zpracovat všechny vstupy uživatelů pouhým zpracováním těchto událostí. V jiných případech může aplikace potřebovat přepsat jednu z metod, které zpracovávají zprávy, aby bylo možné zachytit konkrétní zprávu předtím, než ji obdrží aplikace, formulář nebo ovládací prvek.  
  
## <a name="mouse-and-keyboard-events"></a>Události myši a klávesnice  
 Všechny ovládací prvky model Windows Forms dědí sadu událostí souvisejících se vstupem myši a klávesnicí. Například ovládací prvek může zpracovat událost <xref:System.Windows.Forms.Control.KeyPress> pro určení kódu znaku, který byl stisknut, nebo ovládací prvek může zpracovat událost <xref:System.Windows.Forms.Control.MouseClick> a určit umístění kliknutí myší. Další informace o událostech myši a klávesnice najdete v tématu [použití událostí klávesnice](using-keyboard-events.md) a [událostí myši v model Windows Forms](mouse-events-in-windows-forms.md).  
  
## <a name="methods-that-process-user-input-messages"></a>Metody, které zpracovávají zprávy vstupu uživatele  
 Formuláře a ovládací prvky mají přístup k rozhraní <xref:System.Windows.Forms.IMessageFilter> a sadě přepsatelné metody, které zpracovávají zprávy systému Windows v různých bodech fronty zpráv. Všechny tyto metody mají parametr <xref:System.Windows.Forms.Message>, který zapouzdřuje podrobnosti nízké úrovně zpráv Windows. Můžete implementovat nebo přepsat tyto metody pro kontrolu zprávy a potom buď tuto zprávu spotřebovat, nebo předat dalšímu příjemci ve frontě zpráv. Následující tabulka uvádí metody, které zpracovávají všechny zprávy systému Windows v model Windows Forms.  
  
|Metoda|Poznámky:|  
|------------|-----------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|Tato metoda zachycuje zprávy ve frontě (známé také jako zaslané) zprávy systému Windows na úrovni aplikace.|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|Tato metoda zachycuje zprávy systému Windows na úrovni formuláře a ovládacího prvku před zpracováním.|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|Tato metoda zpracovává zprávy systému Windows ve formuláři a na úrovni ovládacího prvku.|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|Tato metoda provádí výchozí zpracování zpráv systému Windows na úrovni formuláře a ovládacího prvku. To poskytuje minimální funkčnost okna.|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|Tato metoda zachycuje zprávy na úrovni formuláře a ovládacího prvku po jejich zpracování. Pro volání této metody musí být nastaven bit stylu <xref:System.Windows.Forms.ControlStyles.EnableNotifyMessage>.|  
  
 Zprávy klávesnice a myši jsou zpracovávány také pomocí další sady přepsatelné metody, které jsou specifické pro tyto typy zpráv. Další informace najdete v tématu [Jak funguje vstup z klávesnice](how-keyboard-input-works.md) a [Jak funguje vstup z myši v model Windows Forms](how-mouse-input-works-in-windows-forms.md).  
  
## <a name="see-also"></a>Viz také

- [Uživatelský vstup ve Windows Forms](user-input-in-windows-forms.md)
- [Vstup z klávesnice v aplikaci Windows Forms](keyboard-input-in-a-windows-forms-application.md)
- [Vstup z myši v aplikaci Windows Forms](mouse-input-in-a-windows-forms-application.md)

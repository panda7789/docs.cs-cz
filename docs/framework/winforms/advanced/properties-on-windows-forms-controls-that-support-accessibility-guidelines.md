---
title: Vlastnosti přístupnosti ovládacích prvků
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
ms.openlocfilehash: 73d81f5b5f656ed5ef90bdd9b6fe1b3293123f97
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743433"
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a>Vlastnosti v ovládacích prvcích Windows Forms, jež podporují pokyny pro usnadnění přístupu
Ovládací prvky standardní sady nástrojů pro model Windows Forms podporují řadu pokynů pro usnadnění, včetně zpřístupnění fokusu klávesnice a vystavení prvků obrazovky.  
  
## <a name="planning-ahead-for-accessibility"></a>Plánování před přístupností  
 Vlastnosti ovládacích prvků lze použít k podpoře dalších pokynů pro usnadnění, jak je znázorněno v následující tabulce. Kromě toho byste měli použít nabídky k poskytnutí přístupu k funkcím programu.  
  
|Vlastnost ovládacího prvku|Pokyny pro usnadnění přístupu|  
|----------------------|--------------------------------------|  
|AccessibleDescription|Popis je hlášený jako pomůcky pro usnadnění přístupu, jako jsou čtečky obrazovky. Pomůcky pro usnadnění přístupu jsou specializované programy a zařízení, které lidem s postižením můžou efektivněji používat počítače.|  
|Přístupný|Název, který bude hlášen k pomůckám přístupnosti.|  
|AccessibleRole|Popisuje použití prvku v uživatelském rozhraní.|  
|TabIndex|Vytvoří navigační cestu rozumné prostřednictvím formuláře. Je důležité, aby ovládací prvky bez vnitřních popisků, jako jsou textová pole, měly jejich přidružené popisky přímo před nimi v pořadí prvků.|  
|Text|K vytvoření přístupových klíčů použijte znak "&". Používání přístupových klíčů je součástí poskytování dokumentovaného přístupu k funkcím na klávesnici.|  
|Velikost písma|Pokud velikost písma není přizpůsobitelná, měla by být nastavena na 10 bodů nebo větší. Jakmile je nastavena velikost písma formuláře, budou mít všechny ovládací prvky přidané do formuláře stejnou velikost.|  
|ForeColor|Pokud je tato vlastnost nastavená na výchozí hodnotu, použijí se ve formuláři předvolby pro barvy uživatele.|  
|BackColor|Pokud je tato vlastnost nastavená na výchozí hodnotu, použijí se ve formuláři předvolby pro barvy uživatele.|  
|BackgroundImage|Pokud chcete, aby byl text čitelnější, nechte tuto vlastnost prázdnou.|  
  
## <a name="see-also"></a>Viz také:

- [Návod: Vytvoření přístupné aplikace Windows](walkthrough-creating-an-accessible-windows-based-application.md)

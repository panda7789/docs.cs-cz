---
title: FontDialog – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 26bfb561c1050438b78c4ae0a3e6e8da32458cdd
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725035"
---
# <a name="fontdialog-component-overview-windows-forms"></a>FontDialog – přehled komponenty (Windows Forms)
Windows Forms <xref:System.Windows.Forms.FontDialog> komponenta je předem nakonfigurované dialogovému oknu, což je standardní Windows **písmo** dialogové okno používá k vystavení písma, které jsou nainstalovány v systému. Použití v rámci vaší aplikace založené na Windows jako jednoduchým řešením pro výběr písma namísto dialogové okno Vlastní konfigurace.  
  
 Ve výchozím nastavení, dialogové okno zobrazuje pole se seznamem pro písmo, styl písma a velikosti. Zaškrtněte políčka pro efekty, jako jsou přeškrtnutí a podtržení; rozevírací seznam pro skript PowerShell workflow a vzorky vzhled písma. (Skript odkazuje na jiný znak skripty, které jsou k dispozici pro dané písmo, například hebrejštinu a japonština.) Chcete-li zobrazit dialogové okno písmo, zavolejte <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.  
  
## <a name="key-properties"></a>Vlastnosti klíče  
 Komponenta má několik vlastností, které konfigurace její vzhled. Vlastnosti nastavené možnosti dialogového okna jsou <xref:System.Windows.Forms.FontDialog.Font%2A> a <xref:System.Windows.Forms.FontDialog.Color%2A>. <xref:System.Windows.Forms.FontDialog.Font%2A> Vlastnost nastaví písmo, styl, velikost, skriptů a efekty; například `Arial, 10pt, style=Italic, Strikeout`.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.FontDialog>
- [Komponenta FontDialog](fontdialog-component-windows-forms.md)

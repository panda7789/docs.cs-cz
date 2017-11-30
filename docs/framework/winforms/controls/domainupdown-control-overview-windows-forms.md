---
title: "DomainUpDown – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0692677b8ef596bb31b1869480603573a9ec98d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="domainupdown-control-overview-windows-forms"></a>DomainUpDown – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.DomainUpDown> ovládací prvek je v podstatě kombinací textového pole a pár tlačítka pro přesun nahoru nebo dolů v seznamu. Ovládací prvek zobrazí a nastaví textový řetězec ze seznamu voleb. Uživatele můžete vybrat řetězec, klikněte na tlačítka pro přesouvání v seznamu nahoru a dolů, stisknutím klávesy se šipkami nahoru a dolů nebo zadáním řetězec, který odpovídá položku v seznamu. Je možné použití tohoto ovládacího prvku pro výběr položek z abecedně seřazený seznam názvů.  
  
> [!NOTE]
>  Seřadit seznamu, nastavte <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> vlastnost `true`.  
  
 Funkce tohoto ovládacího prvku je velmi podobný pole se seznamem nebo pole se seznamem, ale zabírají velmi málo místa.  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Klíčové vlastnosti ovládacího prvku jsou <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, a <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. <xref:System.Windows.Forms.DomainUpDown.Items%2A> Vlastnost obsahuje seznam objektů, jejichž hodnoty text se zobrazí v ovládacím prvku. Pokud <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> je nastaven na `false`, ovládacího prvku automaticky dokončení text, že uživatel nezadá a odpovídá hodnotě v seznamu. Pokud <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> je nastaven na `true`, posouvání za poslední položky se dostanete na první položku v seznamu a naopak. Klíče metody ovládacího prvku <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> a <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Tento ovládací prvek zobrazí pouze textové řetězce. Pokud chcete ovládacího prvku, který zobrazí číselné hodnoty, použijte <xref:System.Windows.Forms.NumericUpDown> ovládacího prvku. Další informace najdete v tématu [– Přehled ovládacího prvku NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DomainUpDown>  
 [DomainUpDown – ovládací prvek](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)

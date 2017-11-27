---
title: "DomainUpDown – ovládací prvek (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 37cec82876edadfed5cda338ca12775ad19ae732
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="domainupdown-control-windows-forms"></a>DomainUpDown – ovládací prvek (Windows Forms)
Windows Forms <xref:System.Windows.Forms.DomainUpDown> řízení vypadá jako kombinace textového pole a pár tlačítka pro přesun nahoru nebo dolů v seznamu. Ovládací prvek zobrazí a nastaví textový řetězec ze seznamu voleb. Uživatele můžete vybrat řetězec, klikněte na tlačítka pro přesouvání v seznamu nahoru a dolů, stisknutím klávesy se šipkami nahoru a dolů nebo zadáním řetězec, který odpovídá položku v seznamu. Je možné použití tohoto ovládacího prvku pro výběr položek z abecedně seřazený seznam názvů. (Seřadíte seznam nastavit <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> vlastnost `true`.) Funkce tohoto ovládacího prvku je velmi podobný pole se seznamem nebo pole se seznamem, ale zabírají velmi málo místa.  
  
 Klíčové vlastnosti ovládacího prvku jsou <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, a <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. <xref:System.Windows.Forms.DomainUpDown.Items%2A> Vlastnost obsahuje seznam objektů, jejichž hodnoty text se zobrazí v ovládacím prvku. Pokud <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> je nastaven na `false`, ovládacího prvku automaticky dokončení text, že uživatel nezadá a odpovídá hodnotě v seznamu. Pokud <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> je nastaven na `true`, posouvání za poslední položky se dostanete na první položku v seznamu a naopak. Klíče metody ovládacího prvku <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> a <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Tento ovládací prvek zobrazí pouze textové řetězce. Pokud chcete ovládacího prvku, který zobrazí číselné hodnoty, použijte <xref:System.Windows.Forms.NumericUpDown> ovládacího prvku. Další informace najdete v tématu [NumericUpDown – ovládací prvek](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md) .  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled ovládacího prvku DomainUpDown](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)  
 Představuje obecné koncepty <xref:System.Windows.Forms.DomainUpDown> řízení, které umožňuje uživatelům procházet a vyberte ze seznamu textové řetězce.  
  
 [Postupy: Přidání položky do Windows Forms DomainUpDown – ovládací prvky prostřednictvím kódu programu](../../../../docs/framework/winforms/controls/how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 Popisuje, jak zadat textového řetězce <xref:System.Windows.Forms.DomainUpDown> by měl zobrazit ovládací prvek.  
  
 [Postupy: odebrání položek z rozhraní Windows Forms DomainUpDown – ovládací prvky](../../../../docs/framework/winforms/controls/how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 Popisuje postup odstranění položek z <xref:System.Windows.Forms.DomainUpDown> ovládací prvek v kódu.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.DomainUpDown>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy.  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy...  
  
## <a name="related-sections"></a>Související oddíly  
 [Ovládací prvky, které můžete použít v aplikaci Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 Poskytuje úplný seznam Windows Forms – ovládací prvky, odkazy na informace o jejich používání.

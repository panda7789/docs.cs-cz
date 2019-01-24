---
title: 'Postupy: Změna vzhledu ovládacího prvku DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, customizing
- DataRepeater, changing run time appearance
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
ms.openlocfilehash: e5508329ba716b53eff0c9e1bfe13e190fa1fd85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716632"
---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a>Postupy: Změna vzhledu ovládacího prvku DataRepeater (Visual Studio)
Můžete změnit vzhled <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek v době návrhu nastavením vlastností nebo za běhu pomocí manipulace <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> událostí.  
  
 Vlastnosti, které jste nastavili v době návrhu, když je vybrána oddíl šablony položky ovládacího prvku se opakuje pro každý <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> v době běhu. Vlastnosti související s vzhled <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> samotný ovládací prvek bude viditelný v době běhu je ponecháno pouze pokud je součást kontejneru zjištěných (např. Pokud <xref:System.Windows.Forms.Control.Padding%2A> je nastavena na hodnotu velké).  
  
 V době běhu, vzhled související vlastnosti lze nastavit na základě podmínek. Například v aplikaci pro plánování, můžete změnit barvu pozadí položky upozornit uživatele, pokud je položka po datu splatnosti. V <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> obslužná rutina události, pokud nastavíte vlastnost v podmíněném příkazu, jako `If…Then`, je třeba použít také `Else` klauzule k určení vzhledu, pokud podmínka splněna není.  
  
### <a name="to-change-the-appearance-at-design-time"></a>Chcete-li změnit vzhled v době návrhu  
  
1.  V Návrháři formulářů Windows, vyberte oblast šablony (horního) položky <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
2.  V okně Vlastnosti vyberte vlastnosti a změňte hodnotu. Společné vlastnosti, které ovlivňují vzhled zahrnují <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, a <xref:System.Windows.Forms.Control.ForeColor%2A>.  
  
### <a name="to-change-the-appearance-at-run-time"></a>Změna vzhledu za běhu  
  
1.  V editoru kódu, v případě rozevíracího seznamu, klikněte na tlačítko **DrawItem**.  
  
2.  V <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> obslužná rutina události, přidejte kód pro nastavení vlastnosti:  
  
     [!code-csharp[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="example"></a>Příklad  
 Pro některé běžné úpravy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> zahrnují ovládací prvek zobrazení řádků se Alternující barvy a změna barvy na základě podmínky pro pole. Následující příklad ukazuje, jak provádět tyto úpravy. Tento příklad předpokládá, že máte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek, který je vázán na tabulky produktů v databázi Northwind.  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-csharp[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 Všimněte si, že pro obě tyto úpravy, je nutné zadat kód pro nastavení vlastností pro obě strany podmínky. Pokud nezadáte `Else` podmínku, zobrazí se neočekávané výsledky v době běhu.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>
- [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [Postupy: Zobrazení vázaných dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [Postupy: Zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)
- [Postupy: Zobrazení položek záhlaví v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)

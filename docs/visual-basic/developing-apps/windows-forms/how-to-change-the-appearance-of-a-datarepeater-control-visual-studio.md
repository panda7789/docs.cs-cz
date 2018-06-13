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
ms.openlocfilehash: 9863d9343ffcecc1e4aae7f6bc16dae39ef76385
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590118"
---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a>Postupy: Změna vzhledu ovládacího prvku DataRepeater (Visual Studio)
Můžete změnit vzhled <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku v době návrhu nastavením vlastnosti nebo v době běhu zpracování <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> událostí.  
  
 Vlastnosti, které můžete nastavit v době návrhu, když je vybrána sekce šablony ovládacího prvku bude opakovat pro každý <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> za běhu. Vlastnosti týkající se vzhledu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> vlastní ovládací prvek se nebude zobrazovat v době běhu je ponechán pouze pokud je část kontejneru zjištěných (například pokud <xref:System.Windows.Forms.Control.Padding%2A> je nastavena na hodnotu velké).  
  
 V době běhu vlastnosti týkající se vzhledu můžete nastavena na základě podmínky. Například v aplikaci pro plánování, můžete změnit barvu pozadí položky upozornit uživatele, pokud je položka po splatnosti. V <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> obslužnou rutinu události, je-li například nastavení vlastnosti v podmíněného příkazu `If…Then`, je třeba použít také `Else` klauzule určit vzhled, když není splněna podmínka.  
  
### <a name="to-change-the-appearance-at-design-time"></a>Chcete-li změnit vzhled v době návrhu  
  
1.  V Návrháři formulářů vyberte oblast šablony (velká) položky <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
2.  V okně vlastností vyberte vlastnosti a změňte hodnotu. Společné vlastnosti, které ovlivňují vzhled zahrnují <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, a <xref:System.Windows.Forms.Control.ForeColor%2A>.  
  
### <a name="to-change-the-appearance-at-run-time"></a>Změna vzhledu za běhu  
  
1.  V editoru kódu, události rozevíracího seznamu, klikněte na tlačítko **DrawItem**.  
  
2.  V <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> obslužné rutiny události, přidat kód pro nastavení vlastností:  
  
     [!code-csharp[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="example"></a>Příklad  
 Pro některé běžné úpravy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení obsahují zobrazení řádků v střídavých barvy a změna barvy pole na základě podmínky. Následující příklad ukazuje, jak provést tyto úpravy. Tento příklad předpokládá, že máte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek, který je vázána k tabulce produktů v databázi Northwind.  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-csharp[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 Všimněte si, že pro obě tyto úpravy, je nutné zadat kód pro nastavení vlastností pro obě strany podmínky. Pokud nezadáte `Else` podmínky, zobrazí se neočekávaným výsledkům v době běhu.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>  
 [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [Postupy: Zobrazení vázaných dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Postupy: Zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [Postupy: Zobrazení záhlaví položek v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)

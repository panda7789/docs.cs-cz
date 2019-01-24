---
title: 'Postupy: Zákaz přidávání a odstraňování položek DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, disabling delete
- DataRepeater, disabling add
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
ms.openlocfilehash: 3a304132d0514da4c19811be2536c9516e2838f0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618539"
---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a>Postupy: Zákaz přidávání a odstraňování položek DataRepeater (Visual Studio)
Ve výchozím nastavení, můžete přidávat a odstraňovat položky v uživatelů <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Uživatele můžete přidat novou položku stisknutím kombinace kláves CTRL + N při <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> má právě fokus, nebo kliknutím **AddNewItem** tlačítko <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku. Uživatelé, mohou odstranit položku stisknutím kombinace kláves ODSTRANĚNY při <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> má právě fokus, nebo kliknutím **DeleteItem** tlačítko <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku.  
  
 Můžete zakázat přidávání nebo odstraňování v době návrhu nebo v době běhu.  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a>Chcete-li zakázat přidávání a odstraňování v době návrhu  
  
1.  V Návrháři formulářů Windows, vyberte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
    > [!NOTE]
    >  Musíte vybrat dolní části ovládacího prvku. Pokud jste vybrali v části šablony položky, zobrazí se různé sady vlastností.  
  
2.  V okně Vlastnosti nastavte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> vlastnost **False**.  
  
3.  Nastavte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> vlastnost **False**.  
  
4.  V Návrháři formulářů Windows, vyberte <xref:System.Windows.Forms.BindingNavigator> ovládací prvek a potom klikněte na tlačítko **AddNewItem** (tlačítko se symbolem plus na něj).  
  
5.  V okně Vlastnosti nastavte <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> vlastnost **False**.  
  
6.  V Návrháři formulářů Windows, vyberte <xref:System.Windows.Forms.BindingNavigator> ovládací prvek a potom klikněte na tlačítko **DeleteItem** (tlačítko s černým symbolem X na něj).  
  
7.  V okně Vlastnosti nastavte <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> vlastnost **False**.  
  
8.  V panelu komponent, vyberte <xref:System.Windows.Forms.BindingSource> ke kterému <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> je vázán.  
  
9. V okně Vlastnosti nastavte <xref:System.Windows.Forms.BindingSource.AllowNew%2A> vlastnost **False**.  
  
10. V Návrháři formulářů Windows, dvakrát klikněte **DeleteItem** tlačítko k otevření editoru kódu.  
  
11. V rozevíracím seznamu událostí vyberte `BindingNavigatorDeleteItem_EnabledChanged` událostí.  
  
12. Přidejte následující kód, který `BindingNavigatorDeleteItem_EnabledChanged` obslužné rutiny události:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  Tento krok je nezbytný, protože <xref:System.Windows.Forms.BindingSource> vám umožní **DeleteItem** tlačítko pokaždé, když se změní aktuální záznam.  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a>Chcete-li zakázat přidávání a odstraňování v době běhu  
  
1.  V Návrháři formulářů Windows klikněte dvakrát na formuláři se otevřít Editor kódu.  
  
2.  Přidejte následující kód, který `Form_Load` události:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  Přidejte následující kód, který `BindingNavigatorDeleteItem_EnabledChanged` obslužné rutiny události:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  Tento krok je nezbytný, protože <xref:System.Windows.Forms.BindingSource> vám umožní **DeleteItem** tlačítko pokaždé, když se změní aktuální záznam.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)

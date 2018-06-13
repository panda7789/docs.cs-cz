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
ms.openlocfilehash: e3d0d2a8d422054e269ee92df1fdfcb5acb96eac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590796"
---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a>Postupy: Zákaz přidávání a odstraňování položek DataRepeater (Visual Studio)
Ve výchozím nastavení, můžete přidávat a odstraňovat položky v uživatelů <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Uživatele můžete přidat novou položku stisknutím kombinace kláves CTRL + N při <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> má právě fokus, nebo pomocí kliknutím **AddNewItem** na tlačítko <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku. Uživatelé odstranit položku stisknutím klávesy odstranit při <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> má právě fokus, nebo pomocí kliknutím na tlačítko **DeleteItem** na tlačítko <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku.  
  
 Přidání nebo odstranění v době návrhu nebo v době běhu můžete zakázat.  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a>Chcete-li zakázat přidávání a odstraňování v době návrhu  
  
1.  V Návrháři formulářů Windows, vyberte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.  
  
    > [!NOTE]
    >  Je třeba vybrat v dolní části ovládacího prvku. Pokud vyberete oddíl šablony položky, zobrazí se jinou sadu vlastností.  
  
2.  V okně vlastnosti nastavit <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> vlastnost **False**.  
  
3.  Nastavte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> vlastnost **False**.  
  
4.  V Návrháři formulářů Windows, vyberte <xref:System.Windows.Forms.BindingNavigator> řízení a klikněte **AddNewItem** (tlačítko se znaménkem plus na něm).  
  
5.  V okně vlastnosti nastavit <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> vlastnost **False**.  
  
6.  V Návrháři formulářů Windows, vyberte <xref:System.Windows.Forms.BindingNavigator> řízení a klikněte **DeleteItem** (tlačítko s červeným symbolem X na něm).  
  
7.  V okně vlastnosti nastavit <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> vlastnost **False**.  
  
8.  Na hlavním panelu součást vyberte <xref:System.Windows.Forms.BindingSource> ke kterému <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> je vázána.  
  
9. V okně vlastnosti nastavit <xref:System.Windows.Forms.BindingSource.AllowNew%2A> vlastnost **False**.  
  
10. V Návrháři formulářů Windows, klikněte dvakrát na **DeleteItem** tlačítko otevřete Editor kódu.  
  
11. Vyberte v rozevíracím seznamu události `BindingNavigatorDeleteItem_EnabledChanged` událostí.  
  
12. Přidejte následující kód, který `BindingNavigatorDeleteItem_EnabledChanged` obslužné rutiny události:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  Tento krok je nezbytný, protože <xref:System.Windows.Forms.BindingSource> povolí **DeleteItem** tlačítko pokaždé, když se změní na aktuální záznam.  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a>Chcete-li zakázat přidávání a odstraňování za běhu  
  
1.  V Návrháři formulářů poklepejte na formulář pro otevření editoru kódu.  
  
2.  Přidejte následující kód, který `Form_Load` událostí:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  Přidejte následující kód, který `BindingNavigatorDeleteItem_EnabledChanged` obslužné rutiny události:  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  Tento krok je nezbytný, protože <xref:System.Windows.Forms.BindingSource> povolí **DeleteItem** tlačítko pokaždé, když se změní na aktuální záznam.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Řešení potíží s ovládacím prvkem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)

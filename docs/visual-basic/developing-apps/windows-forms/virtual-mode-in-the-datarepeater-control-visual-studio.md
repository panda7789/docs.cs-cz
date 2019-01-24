---
title: Virtuální režim ovládacího prvku DataRepeater (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- virtual data binding [Visual Basic]
- DataRepeater
- DataRepeater, virtual mode
ms.assetid: 5fb805dc-2d8b-4139-b1e3-86e4c2667221
ms.openlocfilehash: 3988c16746606de9f20f9a66b87539b6cea04758
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700803"
---
# <a name="virtual-mode-in-the-datarepeater-control-visual-studio"></a>Virtuální režim ovládacího prvku DataRepeater (Visual Studio)
Pokud chcete zobrazit velké množství tabulková data v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek, může zvýšit výkon tím, že nastavíte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> vlastnost `True` a explicitní Správa ovládacího prvku interakce s jeho zdrojovými daty. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Ovládací prvek obsahuje několik událostí, které dokáže zpracovat k interakci se zdroji dat a zobrazit data podle potřeby v době běhu.  
  
## <a name="how-virtual-mode-works"></a>Jak funguje virtuální režim  
 Nejběžnější scénář pro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> je ovládací prvek pro vazbu podřízené ovládací prvky <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> na datový zdroj v době návrhu a umožňují <xref:System.Windows.Forms.BindingSource> k předávání dat vpřed a zpět, podle potřeby. Při použití virtuálního režimu ovládací prvky, které nejsou vázány na zdroj dat a data předávána vpřed a zpět do podkladového zdroje dat v době běhu.  
  
 Při <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> je nastavena na `True`, vytvoříte tak, že přidáte ovládací prvky z uživatelského rozhraní **nástrojů** nepřidávat vázané ovládací prvky z **zdroje dat** okna.  
  
 Jsou vyvolány události na základě jednotlivých ovládacích a je nutné přidat kód pro zpracování dat zobrazení. Když je nový <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> je přesunut do oblasti zobrazení, <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> událost je aktivována jednou pro každý ovládací prvek a je třeba zadat hodnoty pro každý ovládací prvek <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> obslužné rutiny události.  
  
 Tímto uživatelem, při změně dat v jednom z ovládacích prvků <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> událost se vyvolá, a je nutné ověřit data a uložit do zdroje dat.  
  
 Pokud uživatel přidá nová položka, <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> událost se vyvolá. Vytvoří nový záznam ve zdroji dat pomocí obslužné rutiny této události. Pokud chcete zabránit nežádoucí změny, musíte také monitorovat <xref:System.Windows.Forms.Control.KeyDown> událost pro každý ovládací prvek a volání <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> Pokud uživatel stiskne klávesu ESC.  
  
 Pokud zdroj dat změny, můžete aktualizovat <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku pomocí volání <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> metody. Obě metody musí být volána v pořadí.  
  
 A konečně, je nutné implementovat obslužné rutiny událostí pro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> událost, která nastane, když se odstraní položka a volitelně pro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems> a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems> události, ke kterým dochází pokaždé, když uživatel odstraní položku stisknutím klávesy DELETE.  
  
## <a name="implementing-virtual-mode"></a>Implementace virtuálního režimu  
 Tady je postup, které jsou nutné k implementaci virtuálním režimu.  
  
#### <a name="to-implement-virtual-mode"></a>Implementace virtuálního režimu  
  
1.  Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení z **sady Visual Basic PowerPack** kartu **nástrojů** do ovládacího prvku formulář nebo kontejneru. Nastavte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> vlastnost `True`.  
  
2.  Přetáhněte ovládací prvky z **nástrojů** do šablony oblast položky (horní oblasti) <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Budete potřebovat jeden ovládací prvek pro každé pole ve zdroji dat, který chcete zobrazit.  
  
3.  Implementujte obslužnou rutinu pro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> událostí k poskytnutí hodnot pro každý ovládací prvek. Tato událost je aktivována, když je nový <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> je přesunut do oblasti zobrazení. Kód bude vypadat podobně jako v následujícím příkladu, který je pro zdroj dat s názvem `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_1.cs)]  
  
4.  Implementujte obslužnou rutinu pro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> na ukládání dat události. Tato událost je aktivována, když uživatel potvrdí změny podřízeným ovládacím prvkem <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>. Kód bude vypadat podobně jako v následujícím příkladu, který je pro zdroj dat s názvem `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_2.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_2.cs)]  
  
5.  Implementujte obslužnou rutinu pro každý ovládací prvek podřízené <xref:System.Windows.Forms.Control.KeyDown> události a monitorování klávesu ESC. Volání <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> metody, aby se zabránilo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> vyvolání události. Kód bude vypadat podobně jako v následujícím příkladu.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_3.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_3.cs)]  
  
6.  Implementujte obslužnou rutinu pro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> událostí. Tato událost je aktivována, když uživatel přidá novou položku do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Kód bude vypadat podobně jako v následujícím příkladu, který je pro zdroj dat s názvem `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_4.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_4.cs)]  
  
7.  Implementujte obslužnou rutinu pro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> událostí. Když uživatel odstraní existující položky dojde k této události. Kód bude vypadat podobně jako v následujícím příkladu, který je pro zdroj dat s názvem `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_5.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_5.cs)]  
  
8.  Pro úroveň kontroly ověřování, implementujte obslužné rutiny pro <xref:System.Windows.Forms.Control.Validating> události podřízených ovládacích prvků. Kód bude vypadat podobně jako v následujícím příkladu.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_6.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_6.cs)]  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>
- [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)

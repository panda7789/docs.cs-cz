---
title: "Virtuální režim ovládacího prvku DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- virtual data binding [Visual Basic]
- DataRepeater
- DataRepeater, virtual mode
ms.assetid: 5fb805dc-2d8b-4139-b1e3-86e4c2667221
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4c85ce4541e32991bfa09b1436385281d27ad355
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="virtual-mode-in-the-datarepeater-control-visual-studio"></a>Virtuální režim ovládacího prvku DataRepeater (Visual Studio)
Pokud chcete zobrazit velké množství tabulková data v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení, může zlepšit výkon nastavením <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> vlastnost `True` a explicitně správě interakci ovládacího prvku se zdrojem dat. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Ovládací prvek obsahuje několik událostí, které může zpracovat pracovat se zdroj dat a zobrazit data jako za běhu.  
  
## <a name="how-virtual-mode-works"></a>Jak funguje virtuální režim  
 Nejběžnější scénáře <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> je ovládací prvek pro vazbu podřízených ovládacích prvků <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> k data zdroje v době návrhu a povolit <xref:System.Windows.Forms.BindingSource> k předávání dat a zpět, podle potřeby. Při použití virtuálního režimu ovládací prvky nejsou vázány na zdroj dat a data jsou předána a zpět na podkladový zdroj dat za běhu.  
  
 Při <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> je nastavena na `True`, vytvoříte tak, že přidáte ovládacích prvků z uživatelského rozhraní **sada nástrojů** místo přidávání vázané ovládací prvky z **zdroje dat** okno.  
  
 Události jsou vyvolány na základě jednotlivých ovládacích a je nutné přidat kód pro zpracování dat zobrazení. Pokud nový <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> přesunut do zobrazení oblasti <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> událost se vyvolá jednou pro každý ovládací prvek a je nutné zadat hodnoty pro každý ovládací prvek v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> obslužné rutiny události.  
  
 Pokud je uživatel, změnit data v jedné z ovládacích prvků <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> událost se vyvolá, a je nutné ověřit data a uložit do zdroje dat.  
  
 Pokud uživatel přidá novou položku, <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> událost se vyvolá. Vytvořit nový záznam ve zdroji dat pomocí obslužné rutiny této události. Aby se zabránilo neúmyslnému změny, je třeba rovněž sledovat <xref:System.Windows.Forms.Control.KeyDown> událostí pro každý ovládací prvek a volání <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> Pokud stisknutí klávesy ESC.  
  
 Pokud se zdroji dat, můžete aktualizovat <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení voláním <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> metody. Obě metody musí být voláno v pořadí.  
  
 Nakonec musí implementovat obslužné rutiny pro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> událost, ke které dojde při odstranění položky a volitelně pro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems> a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems> události, ke kterým dochází vždy, když uživatel odstraní položku stisknutím klávesy odstranit.  
  
## <a name="implementing-virtual-mode"></a>Implementace virtuálního režimu  
 Tady jsou kroky, které jsou nutné k implementaci virtuální režim.  
  
#### <a name="to-implement-virtual-mode"></a>Implementace virtuálního režimu  
  
1.  Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řídit z **PowerPacks jazyka Visual Basic** ve **sada nástrojů** do ovládacího prvku formuláře nebo kontejneru. Nastavte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> vlastnost `True`.  
  
2.  Přetáhněte ovládací prvky z **sada nástrojů** na oblast šablony položky (horní oblasti) z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Budete potřebovat jeden ovládací prvek pro každé pole v zdroje dat, které chcete zobrazit.  
  
3.  Implementujte obslužnou rutinu pro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> událostí zadat hodnoty pro každý ovládací prvek. Tato událost se vyvolá, když nový <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> přesunut do zobrazení oblasti. Kód bude vypadat podobně jako následující příklad, který je pro zdroj dat s názvem `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_1.cs)]  
  
4.  Implementujte obslužnou rutinu pro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> na ukládání dat události. Tato událost se vyvolá, když uživatel potvrdí změny na podřízené ovládacího prvku <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>. Kód bude vypadat podobně jako následující příklad, který je pro zdroj dat s názvem `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_2.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_2.cs)]  
  
5.  Implementujte obslužnou rutinu pro každý ovládací prvek podřízené <xref:System.Windows.Forms.Control.KeyDown> události a monitorování klávesy ESC. Volání <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> metoda, aby se zabránilo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> vyvolání události. Kód bude vypadat podobně jako v následujícím příkladu.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_3.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_3.cs)]  
  
6.  Implementujte obslužnou rutinu pro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> událostí. Tato událost se vyvolá, když uživatel přidá novou položku do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku. Kód bude vypadat podobně jako následující příklad, který je pro zdroj dat s názvem `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_4.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_4.cs)]  
  
7.  Implementujte obslužnou rutinu pro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> událostí. K této události dojde, když uživatel odstraní existující položku. Kód bude vypadat podobně jako následující příklad, který je pro zdroj dat s názvem `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_5.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_5.cs)]  
  
8.  Pro úroveň kontroly ověřování, implementujte obslužné rutiny pro <xref:System.Windows.Forms.Control.Validating> události podřízených ovládacích prvků. Kód bude vypadat podobně jako v následujícím příkladu.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_6.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_6.cs)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>  
 [Úvod do ovládacího prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)

---
title: "Postupy: Vytvoření vazby ovládacích prvků Windows Forms ke komponentě BindingSource pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18e89d0a236d3b370c521b73dfb640a09137a5dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a>Postupy: Vytvoření vazby ovládacích prvků Windows Forms ke komponentě BindingSource pomocí Návrháře
Po přidání ovládacích prvků do svého formuláře a určit uživatelské rozhraní pro aplikace, můžete vázat ovládacích prvků na zdroj dat tak, aby v době běhu, uživatelé mohou změnit a uložit data týkající se aplikace.  
  
 Vytvoření vazby na ovládací prvek nebo řadu ovládacích prvků ve Windows Forms nejsnáze pomocí <xref:System.Windows.Forms.BindingSource> ovládací prvek jako most mezi ovládacími prvky na formuláři a zdroj dat.  
  
 Jeden nebo více ovládacích prvků na formuláři mohou být vázány na data. v následujícím postupu <xref:System.Windows.Forms.TextBox> ovládací prvek vázán ke zdroji dat.  
  
 K dokončení postupu se předpokládá, že vytvoříte vazbu ke zdroji dat, který je odvozený z databáze. Další informace o vytvoření zdroje dat z jiných úložišť dat najdete v tématu [přidat nové zdroje dat](/visualstudio/data-tools/add-new-data-sources).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-bind-a-control-at-design-time"></a>K vytvoření vazby ovládacího prvku v době návrhu  
  
1.  Přetáhněte <xref:System.Windows.Forms.TextBox> ovládací prvek na formuláři.  
  
2.  V **vlastnosti** okno:  
  
    1.  Rozbalte **(datové vazby)** uzlu.  
  
    2.  Klikněte na šipku vedle položky <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost.  
  
         **DataSource** otevře editor typů uživatelského rozhraní.  
  
         Pokud zdroj dat byl dříve nakonfigurován pro projekt nebo formulář, se zobrazí.  
  
3.  Klikněte na tlačítko **přidat zdroj dat projektu** vytvořte zdroj dat a připojte se k datům.  
  
4.  Na **Průvodce konfigurací zdroje dat** úvodní stránce, klikněte na tlačítko **Další**.  
  
5.  Na **zvolte typ zdroje dat** vyberte **databáze**.  
  
6.  Na **vybrat datové připojení** vyberte datové připojení ze seznamu dostupných připojení. Pokud požadovaný datové připojení není k dispozici vyberte **nové připojení** k vytvoření nové datové připojení.  
  
7.  Vyberte **Ano, uložte připojení** uložení připojovací řetězec v konfiguračním souboru aplikace.  
  
8.  Vyberte objekty databáze zařazení do vaší aplikace. V takovém případě vyberte pole v tabulce, která chcete <xref:System.Windows.Forms.TextBox> k zobrazení.  
  
9. Pokud chcete, nahradí výchozí název datové sady.  
  
10. Klikněte na tlačítko **Dokončit**.  
  
11. V **vlastnosti** okně klikněte na šipku vedle položky <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost znovu. V **DataSource** editor typů uživatelského rozhraní, vyberte název pole, které chcete vytvořit vazbu <xref:System.Windows.Forms.TextBox> k.  
  
     **DataSource** typ uživatelského rozhraní editoru zavře a sadu dat <xref:System.Windows.Forms.BindingSource> a konkrétní, datové připojení se přidají do svého formuláře tabulku adaptéru.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [Přidat nové zdroje dat](/visualstudio/data-tools/add-new-data-sources)  
 [Okno zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)

---
title: "Postupy: Vytváření vyhledávacích tabulek s komponentou Windows Forms BindingSource"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 27c1c6cd0e617c0940a734e7e16a3ec5d12f920d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a>Postupy: Vytváření vyhledávacích tabulek s komponentou Windows Forms BindingSource
Vyhledávací tabulky je tabulka dat, která má sloupec, který zobrazí data z záznamy související tabulky. V následujících postupech <xref:System.Windows.Forms.ComboBox> řízení se používá k zobrazení pole s relace cizího klíče z nadřazené do podřízené tabulky.  
  
 Pomoc při vizualizovat tyto dvě tabulky a tuto relaci, tady je příklad nadřazenou a podřízenou tabulku:  
  
 CustomersTable (nadřazenou tabulkou)  
  
|CustomerID|JménoZákazníka|  
|----------------|------------------|  
|712|Paul Koch|  
|713|Johnstonův Tamare|  
  
 OrdersTable (podřízené tabulky)  
  
|OrderID|OrderDate|CustomerID|  
|-------------|---------------|----------------|  
|903|12. února 2004|712|  
|904|13. února 2004|713|  
  
 V tomto scénáři jedna tabulka, CustomersTable, ukládá informace, které chcete zobrazit a uložit. Ale ušetřit místo, v tabulce ponechá data, která přidává přehlednost. Jiné tabulky, OrdersTable, obsahuje pouze týkající se vzhledu informace o zákazníkovi, který je ekvivalentní které datu objednávky a pořadí ID číslo ID Neexistuje žádné zmínky názvů zákazníků.  
  
 Čtyři důležité vlastnosti jsou nastaveny na [ComboBox – ovládací prvek](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md) řízení se vytvořit vyhledávací tabulku.  
  
-   <xref:System.Windows.Forms.ComboBox.DataSource%2A> Vlastnost obsahuje název tabulky.  
  
-   <xref:System.Windows.Forms.ListControl.DisplayMember%2A> Vlastnost obsahuje sloupce dat z této tabulky, které chcete zobrazit pro ovládací prvek text (název zákazníka).  
  
-   <xref:System.Windows.Forms.ListControl.ValueMember%2A> Vlastnost obsahuje sloupce dat této tabulky s uložené informace (číslo ID v nadřazené tabulce).  
  
-   <xref:System.Windows.Forms.ListControl.SelectedValue%2A> Vlastnost poskytuje vyhledávací hodnota pro podřízené tabulky, na základě <xref:System.Windows.Forms.ListControl.ValueMember%2A>.  
  
 Následující postupy ukazují, jak Rozvrhněte svůj formulář jako vyhledávací tabulky a vytvoření vazby dat k ovládacím prvkům v něm. Úspěšné dokončení postupů, musíte mít k datovému zdroji prostřednictvím nadřazené a podřízené tabulky, které mají relaci cizího klíče, jak je uvedeno nahoře.  
  
### <a name="to-create-the-user-interface"></a>Vytvoření uživatelského rozhraní  
  
1.  Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.ComboBox> ovládací prvek na formuláři.  
  
     Tento ovládací prvek zobrazí sloupce z tabulky nadřazené.  
  
2.  Přetáhněte další ovládací prvky a zobrazte detaily z podřízené tabulky. Formát dat v tabulce měli určit ovládacích prvků, které zvolíte. Další informace najdete v tématu [ovládacích prvků Windows Forms podle funkce](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md).  
  
3.  Přetažení <xref:System.Windows.Forms.BindingNavigator> na formuláři ovládací prvek; to vám umožní procházení dat v podřízené tabulce.  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a>Připojte se k datům a navázat jej na ovládací prvky  
  
1.  Vyberte <xref:System.Windows.Forms.ComboBox> a klikněte na inteligentní úloh glyfy k zobrazení dialogového okna inteligentní úlohu.  
  
2.  Vyberte **používat data vázaný položky**.  
  
3.  Klikněte na šipku vedle položky **zdroj dat** rozevíracího seznamu. Pokud zdroj dat byl dříve nakonfigurován pro projekt nebo formuláře, zobrazí se; jinak proveďte následující kroky (Tento příklad používá zákazníci a objednávky tabulky ukázková databáze Northwind a odkazuje na ně v závorkách).  
  
    1.  Klikněte na tlačítko **přidat zdroj dat projektu** vytvořte zdroj dat a připojte se k datům.  
  
    2.  Na **Průvodce konfigurací zdroje dat** úvodní stránce, klikněte na tlačítko **Další**.  
  
    3.  Vyberte **databáze** na **zvolte typ zdroje dat** stránky.  
  
    4.  Vybrat datové připojení ze seznamu dostupných připojení na **vybrat datové připojení** stránky. Pokud není k dispozici připojení k požadovaným datům, vyberte **nové připojení** k vytvoření nové datové připojení.  
  
    5.  Klikněte na tlačítko **Ano, uložte připojení** uložení připojovací řetězec v konfiguračním souboru aplikace.  
  
    6.  Vyberte objekty databáze zařazení do vaší aplikace. V takovém případě vyberte nadřazenou tabulkou a podřízenou tabulku (například Zákazníci a objednávky) s relace cizího klíče.  
  
    7.  Pokud chcete, nahradí výchozí název datové sady.  
  
    8.  Klikněte na tlačítko **Dokončit**.  
  
4.  V **zobrazení člen** rozevíracího seznamu, vyberte název sloupce (například kontakt) má být zobrazen v poli se seznamem.  
  
5.  V **hodnotu člena** rozevíracího seznamu vyberte sloupec (například CustomerID) k provedení operace vyhledávání v podřízené tabulce.  
  
6.  V **vybraná hodnota** rozevíracího pole, přejděte na **zdroje dat projektu** a datové jste právě vytvořili, který obsahuje nadřazenou a podřízenou tabulkou. Vyberte stejnou vlastnost podřízené tabulky, který je členem hodnotu v nadřazené tabulce (například Orders.CustomerID). Odpovídající <xref:System.Windows.Forms.BindingSource> , sadu dat a tabulka adaptér součásti bude vytvořen a přidán do formuláře.  
  
7.  Vytvoření vazby <xref:System.Windows.Forms.BindingNavigator> řídit k <xref:System.Windows.Forms.BindingSource> podřízené tabulky (například `OrdersBindingSource`).  
  
8.  Vytvoření vazby ovládacích prvků jiné než <xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku na podrobnosti o pole z podřízené tabulky <xref:System.Windows.Forms.BindingSource> (například `OrdersBindingSource`), kterou chcete zobrazit.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.BindingSource>  
 [BindingSource – komponenta](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [ComboBox – ovládací prvek](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)  
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)

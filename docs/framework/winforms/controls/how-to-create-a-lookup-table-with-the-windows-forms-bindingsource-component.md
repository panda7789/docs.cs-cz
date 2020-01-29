---
title: Vytvoření vyhledávací tabulky pomocí komponenty BindingSource
ms.date: 03/30/2017
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
ms.openlocfilehash: ccf2bfa6cf3f56a38b55f8c87004c42a46172891
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736810"
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a>Postupy: Vytváření vyhledávacích tabulek s komponentou Windows Forms BindingSource
Vyhledávací tabulka je tabulka dat, která má sloupec, který zobrazuje data ze záznamů v tabulce v relaci. V následujících postupech se pro zobrazení pole s relací cizího klíče z nadřazeného objektu na podřízenou tabulku používá ovládací prvek <xref:System.Windows.Forms.ComboBox>.  
  
 Tady je příklad nadřazené a podřízené tabulky, která vám umožní vizualizovat tyto dvě tabulky a tuto relaci:  
  
 Zákazníci (nadřazená tabulka)  
  
|ID|customerName|  
|----------------|------------------|  
|712|Paul Koch|  
|713|Tamara Johnston|  
  
 Orders (podřízená tabulka)  
  
|Seskup|OrderDate|ID|  
|-------------|---------------|----------------|  
|903|12. února 2004|712|  
|904|13. února 2004|713|  
  
 V tomto scénáři jedna tabulka, zákazníci, ukládá skutečné informace, které chcete zobrazit a uložit. Pokud ale chcete ušetřit místo, tabulka opustí data, která zvyšují přehlednost. Druhá tabulka, Orders, obsahuje jenom informace o tom, které ID zákazníka jsou ekvivalentní k tomuto datu a ID objednávky. Neexistují žádné zmínky o názvech zákazníků.  
  
 V ovládacím prvku [ComboBox](combobox-control-windows-forms.md) jsou nastaveny čtyři důležité vlastnosti pro vytvoření vyhledávací tabulky.  
  
- Vlastnost <xref:System.Windows.Forms.ComboBox.DataSource%2A> obsahuje název tabulky.  
  
- Vlastnost <xref:System.Windows.Forms.ListControl.DisplayMember%2A> obsahuje datový sloupec této tabulky, který chcete zobrazit pro text ovládacího prvku (jméno zákazníka).  
  
- Vlastnost <xref:System.Windows.Forms.ListControl.ValueMember%2A> obsahuje datový sloupec v tabulce s uloženými informacemi (číslo ID v nadřazené tabulce).  
  
- Vlastnost <xref:System.Windows.Forms.ListControl.SelectedValue%2A> poskytuje hodnotu vyhledávání pro podřízenou tabulku na základě <xref:System.Windows.Forms.ListControl.ValueMember%2A>.  
  
 Níže uvedené postupy vám ukážou, jak rozvrhnout formulář jako vyhledávací tabulku a vytvořit z nich data s ovládacími prvky. Aby bylo možné úspěšně dokončit postupy, musíte mít zdroj dat s nadřazenými a podřízenými tabulkami, které mají relaci cizího klíče, jak je uvedeno výše.  
  
### <a name="to-create-the-user-interface"></a>Vytvoření uživatelského rozhraní  
  
1. Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.ComboBox> do formuláře.  
  
     Tento ovládací prvek zobrazí sloupec z nadřazené tabulky.  
  
2. Přetáhněte další ovládací prvky pro zobrazení podrobností z podřízené tabulky. Formát dat v tabulce by měl určovat, které ovládací prvky si zvolíte. Další informace naleznete v tématu [model Windows Forms Controls by Function](windows-forms-controls-by-function.md).  
  
3. Přetáhněte ovládací prvek <xref:System.Windows.Forms.BindingNavigator> do formuláře. To vám umožní procházet data v podřízené tabulce.  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a>Připojení k datům a jejich svázání s ovládacími prvky  
  
1. Vyberte <xref:System.Windows.Forms.ComboBox> a kliknutím na Inteligentní panel glyf zobrazíte dialogové okno Inteligentní panel.  
  
2. Vyberte možnost **použít položky vázané na data**.  
  
3. Klikněte na šipku vedle rozevíracího seznamu **zdroj dat** . Pokud byl zdroj dat dříve nakonfigurován pro projekt nebo formulář, zobrazí se. v opačném případě proveďte následující kroky (Tento příklad používá tabulky Zákazníci a objednávky ukázkové databáze Northwind a odkazuje na ně v závorkách).  
  
    1. Kliknutím na **Přidat zdroj dat projektu** se můžete připojit k datům a vytvořit zdroj dat.  
  
    2. Na úvodní stránce **Průvodce konfigurací zdroje dat** klikněte na tlačítko **Další**.  
  
    3. Vyberte možnost **databáze** na stránce **Vybrat typ zdroje dat** .  
  
    4. Vyberte datové připojení ze seznamu dostupných připojení na stránce **Vyberte datové připojení** . Pokud požadované datové připojení není k dispozici, vyberte **nové připojení** a vytvořte nové datové připojení.  
  
    5. Klikněte na tlačítko **Ano, uložit připojení** pro uložení připojovacího řetězce do konfiguračního souboru aplikace.  
  
    6. Vyberte databázové objekty, které chcete přenést do aplikace. V takovém případě vyberte nadřazenou tabulku a podřízenou tabulku (například zákazníci a objednávky) se vztahem cizího klíče.  
  
    7. Pokud chcete, nahraďte výchozí název datové sady.  
  
    8. Klikněte na **Dokončit**.  
  
4. V rozevíracím seznamu **Zobrazit člena** vyberte název sloupce (například kontakt), který se má zobrazit v poli se seznamem.  
  
5. V rozevíracím seznamu **člen hodnoty** vyberte sloupec (například CustomerID) k provedení operace vyhledávání v podřízené tabulce.  
  
6. V rozevíracím seznamu **Vybraná hodnota** přejděte na **zdroje dat projektu** a datovou sadu, kterou jste právě vytvořili, která obsahuje nadřazené a podřízené tabulky. Vyberte stejnou vlastnost podřízené tabulky, která je členem hodnoty nadřazené tabulky (například Orders. CustomerID). Budou vytvořeny příslušné <xref:System.Windows.Forms.BindingSource>, datové sady a součásti adaptéru tabulky a přidány do formuláře.  
  
7. Navažte ovládací prvek <xref:System.Windows.Forms.BindingNavigator> na <xref:System.Windows.Forms.BindingSource> podřízené tabulky (například `OrdersBindingSource`).  
  
8. Navažte ovládací prvky kromě <xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.BindingNavigator> řízení na pole podrobností z <xref:System.Windows.Forms.BindingSource> podřízené tabulky (například `OrdersBindingSource`), kterou chcete zobrazit.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingSource>
- [Komponenta BindingSource](bindingsource-component.md)
- [Ovládací prvek ComboBox](combobox-control-windows-forms.md)
- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)

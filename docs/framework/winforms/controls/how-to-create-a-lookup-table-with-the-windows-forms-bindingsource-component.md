---
title: 'Postupy: Vytvoření vyhledávací tabulky s komponentou Windows Forms BindingSource'
ms.date: 03/30/2017
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
ms.openlocfilehash: 481774e9127531bb38df0cc71ac8e7eab76da695
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321897"
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a>Postupy: Vytvoření vyhledávací tabulky s komponentou Windows Forms BindingSource
Vyhledávací tabulka je tabulka dat, která má sloupec, který zobrazuje data ze záznamů v související tabulce. V následujících postupech <xref:System.Windows.Forms.ComboBox> ovládacího prvku se používá k zobrazení pole relace cizího klíče z nadřazené do podřízené tabulky.  
  
 Pomáhají vizualizovat tyto dvě tabulky a tento vztah, tady je příklad nadřazené a podřízené tabulky:  
  
 CustomersTable (nadřazené tabulky)  
  
|ID zákazníka|Zákazníka|  
|----------------|------------------|  
|712|Paul Koch|  
|713|Tamara Johnston|  
  
 OrdersTable (podřízenou tabulku)  
  
|ID objednávky|OrderDate|ID zákazníka|  
|-------------|---------------|----------------|  
|903|12. února 2004|712|  
|904|13. února 2004|713|  
  
 V tomto scénáři jedné tabulky, CustomersTable, ukládá informace, které chcete zobrazit a uložte. Ale pro úsporu místa, v tabulce ponechá si data, která se přidá na srozumitelnosti. Dalších table OrdersTable, obsahuje pouze vzhled související informace o zákazníkovi, který je ekvivalentní k které data objednávky a pořadí ID. identifikační číslo Není k dispozici žádnou zmínku o názvy zákazníků.  
  
 Čtyři důležité vlastnosti jsou nastaveny na [ovládacího prvku ComboBox](combobox-control-windows-forms.md) ovládacího prvku k vytvoření vyhledávací tabulky.  
  
-   <xref:System.Windows.Forms.ComboBox.DataSource%2A> Vlastnosti obsahuje název tabulky.  
  
-   <xref:System.Windows.Forms.ListControl.DisplayMember%2A> Vlastnost obsahuje sloupce dat této tabulky, kterou chcete zobrazit pro ovládací prvek text (jméno zákazníka).  
  
-   <xref:System.Windows.Forms.ListControl.ValueMember%2A> Vlastnost obsahuje sloupce dat této tabulky s uložené informace (číslo ID nadřazené tabulky).  
  
-   <xref:System.Windows.Forms.ListControl.SelectedValue%2A> Vlastnost obsahuje hodnotu vyhledávání pro podřízené tabulky, na základě <xref:System.Windows.Forms.ListControl.ValueMember%2A>.  
  
 Následující postupy ukazují, jak Rozvrhněte svůj formulář jako vyhledávací tabulky a vytvoření vazby dat k ovládacím prvkům v něm. Pro úspěšné dokončení procedury, musí mít zdroj dat s nadřazenými a podřízenými tabulkami, které existuje vztah cizího klíče, jak již bylo zmíněno dříve.  
  
### <a name="to-create-the-user-interface"></a>Vytvoření uživatelského rozhraní  
  
1. Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.ComboBox> ovládací prvek na formuláři.  
  
     Tento ovládací prvek zobrazí sloupec z nadřazené tabulky.  
  
2. Přetáhněte jiných ovládacích prvků pro zobrazení podrobností z podřízené tabulky. Formát dat v tabulce byste určit, jaké ovládací prvky, které zvolíte. Další informace najdete v tématu [ovládacích prvků Windows Forms podle funkce](windows-forms-controls-by-function.md).  
  
3. Přetáhněte <xref:System.Windows.Forms.BindingNavigator> ovládací prvek do formuláře; to vám umožní procházet data v podřízené tabulce.  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a>Připojte se k datům a svázat ovládací prvky  
  
1. Vyberte <xref:System.Windows.Forms.ComboBox> a klikněte na inteligentní úloh glyfů pro zobrazení dialogového okna inteligentních úlohu.  
  
2. Vyberte **položky vázané na data použijte**.  
  
3. Klikněte na šipku vedle položky **zdroj dat** rozevíracího seznamu. Pokud zdroj dat byl dříve nakonfigurován pro projekt nebo formuláře, zobrazí se; v opačném případě proveďte následující kroky (Tento příklad používá tabulky Zákazníci a objednávky v ukázkové databázi Northwind a odkazuje na ně v závorkách).  
  
    1.  Klikněte na tlačítko **přidat zdroj dat projektu** vytvořit zdroj dat a připojte se k datům.  
  
    2.  Na **Průvodce konfigurací zdroje dat** úvodní stránka, klikněte na tlačítko **Další**.  
  
    3.  Vyberte **databáze** na **zvolte typ zdroje dat** stránky.  
  
    4.  Vybrat datové připojení ze seznamu dostupných připojení na **vyberte datové připojení** stránky. Pokud požadované datové připojení není k dispozici, vyberte **nové připojení** k vytvoření nové datové připojení.  
  
    5.  Klikněte na tlačítko **Ano, uložit připojení** uložit připojovací řetězec do konfiguračního souboru aplikace.  
  
    6.  Vyberte databázové objekty do vaší aplikace. V tomto případě vyberte tabulky nadřazené a podřízené tabulky (například Zákazníci a objednávky) se vztahu cizího klíče.  
  
    7.  Nahraďte výchozí název datové sady, chcete-li.  
  
    8.  Klikněte na tlačítko **Dokončit**.  
  
4. V **členem zobrazení** rozevíracího seznamu vyberte název sloupce (například jméno kontaktu) který se má zobrazit v poli se seznamem.  
  
5. V **člen s hodnotou** rozevíracího seznamu vyberte sloupce (například ID zákazníka) k provedení této operace vyhledávání v podřízené tabulce.  
  
6. V **vybraná hodnota** rozevíracího seznamu, přejděte na **zdroje dat projektu** a datovou sadu jste právě vytvořili, který obsahuje nadřazené a podřízené tabulky. Vyberte stejnou vlastnost u podřízené tabulky, který je členem hodnotu nadřazené tabulky (například Orders.CustomerID). Odpovídající <xref:System.Windows.Forms.BindingSource> sadu dat a tabulka adaptér součásti bude vytvořen a přidán do formuláře.  
  
7. Vytvoření vazby <xref:System.Windows.Forms.BindingNavigator> ovládací prvek <xref:System.Windows.Forms.BindingSource> podřízené tabulky (například `OrdersBindingSource`).  
  
8. Jiné než vytvoření vazby ovládacích prvků <xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku pro pole podrobnosti z podřízené tabulky <xref:System.Windows.Forms.BindingSource> (například `OrdersBindingSource`), který chcete zobrazit.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingSource>
- [BindingSource – komponenta](bindingsource-component.md)
- [Ovládací prvek ComboBox](combobox-control-windows-forms.md)
- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)

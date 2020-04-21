---
title: Vylepšení usnadnění přístupu k formulářům Systému Windows
description: Informace o způsobech, jakými se soubory .NET Core Windows Forms pokoušejí zlepšit přístupnost ve srovnání s rozhraním .NET Framework Windows Forms.
ms.date: 04/20/2020
helpviewer_keywords:
- Windows Forms accessibility
- accessibility
author: M-Lipin
ms.openlocfilehash: 30eb8b3bd0aaf646ea23f4f036e822f9bba78dc4
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739750"
---
# <a name="accessibility-improvements-in-windows-forms-controls-for-net-core-30"></a>Vylepšení usnadnění v ovládacích prvcích Windows Forms pro rozhraní .NET Core 3.0

Windows Forms pokračuje ve zlepšování způsobu, jakým funguje s technologiemi usnadnění, aby lépe podporovaly zákazníky windows forms. Mezi tato vylepšení patří následující změny:

- Změny v různých oblastech interakce s klientskými aplikacemi usnadnění přístupu, včetně Předčítání.
- Změny v hierarchii Přístupné (zlepšení navigace prostřednictvím stromu automatizace uživatelského rozhraní).
- Změny v navigaci pomocí klávesnice.

> [!IMPORTANT]
> Změny usnadnění provedené v rozhraní .NET Framework 4.7.1 až .NET Framework 4.8 jsou zahrnuty v rozhraní .NET Core 3.0 a vyšší a jsou ve výchozím nastavení povoleny. Rozhraní .NET Framework podporovalo přepínače kompatibility, které umožňovala aplikacím odhlásit se z nového chování usnadnění přístupu. Na druhou stranu .NET Core nepodporuje tato nastavení a neumožňuje aplikacím odhlásit se z chování usnadnění přístupu.
  
Počínaje rozhraním .NET Core 3.0 využívají aplikace Windows Forms všechny nové funkce usnadnění (zavedené v rozhraní .NET Framework 4.7.1 - 4.8) bez další konfigurace.

## <a name="listbox-accessibility-support"></a>Podpora přístupnosti listboxu

Následující změny platí <xref:System.Windows.Forms.ListBox> pro ovládací prvek:

- Povolená podpora automatizace uživatelského rozhraní pro `ListBox` řízení.
- Vylepšená `ListBox` podpora usnadnění <xref:System.Windows.Automation.ScrollItemPattern> `ListBox` přidáním položek a vylepšením vyvolání a zpracování událostí usnadnění a navigace předčítání mezi položkami (navigace pomocí caps lock není správná a nevrhá navigaci mimo ovládací prvek neúmyslně).

## <a name="checkedlistbox-accessibility-support"></a>Podpora přístupnosti checkedListBox

Následující změny platí <xref:System.Windows.Forms.CheckedListBox> pro ovládací prvek:

- Opravené `CheckedListBox` hranice poskytované vlastnostmi usnadnění pro položky.
- Vylepšeno `ListBox` `CheckedListBox` celkově a přístupnost: opravené hodnoty vlastností a model událostí.

## <a name="combobox-accessibility-support"></a>Podpora přístupnosti služby ComboBox

Následující změny platí <xref:System.Windows.Forms.ComboBox> pro ovládací prvek:

- Byl aktualizován proces `ComboBox` získávání objektů usnadnění pro položky, aby bylo možné generovat ID položek namísto <xref:System.Object.GetHashCode%2A> získávání kódů hash z položek, což může být nebezpečné v případě, že je funkce přepsána.

## <a name="datagridview-accessibility-support"></a>Podpora usnadnění zobrazení Datové hovado

Následující změny platí <xref:System.Windows.Forms.DataGridView> pro ovládací prvek:

- Opraveno `DataGridView.Bounds` pomocí vlastností usnadnění pro sloupce, řádky, buňky a odpovídající záhlaví, lepší výkon výpočtu ohraničovacího obdélníku. Všechny hranice usnadnění jsou reprezentovány správně s přihlédnutím k hranice celého ovládacího prvku, spolu s jeho výřez.
- Opravená `Value.IsReadOnly` hodnota vlastnosti poskytující přístupné klientské aplikace. Vlastnost nyní zobrazuje `IsReadOnly` správný stav buněk.
- Byl opraven <xref:System.Windows.Forms.DataGridView.CellParsing> problém se vyvoláním událostí pro první změnu buňky. Hodnotu buňky lze změnit bez `DataGridView` problémů, včetně první interakce ovládacího prvku.
- Vylepšený `DataGridView` kontrast barev pozadí při použití motivů Windows S vysokým kontrastem. Při `DataGridView` použití motivů HC#1, HC#2 a HC Black se změnila výchozí zadní barva.

## <a name="propertygrid-accessibility-support"></a>Podpora přístupnosti propertygrid

Následující změny platí <xref:System.Windows.Forms.PropertyGrid> pro ovládací prvek:

- Opraveno `PropertyGrid.Bounds` vlastnostmi usnadnění pro položky mřížky, lepším výkonem výpočtu ohraničovacího obdélníku. Prozatím jsou všechny hranice přístupnosti správně reprezentovány s přihlédnutím k hranicím celého ovládacího prvku spolu s jeho výřezem.
- Opraveny přístupné názvy a popisy dílčích ovládacích prvků, aby neobsahovaly názvy typů ovládacích prvků a aby se zabránilo dvojitému oznámení pro názvy typů ovládacích prvků.

## <a name="toolstrip-accessibility-support"></a>Podpora usnadnění funkce ToolStrip

Následující změny platí <xref:System.Windows.Forms.ToolStrip> pro ovládací prvek:

- Vylepšená `ToolStrip`navigace `MenuStrip`přes `StatusStrip` , a položky. Opravena `ToolStrip` `MenuStrip` navigace a navigace s klávesou Shift, zpětné smyčkování položek nabídky při stisknutí šipky nahoru s ouchou, která přejde na dolní prvek nabídky.
- Vylepšená `MenuStrip` přístupná navigace, opravené typy ovládacích prvku pro podnabídky pro podnabídky pro podnabídky typu Menu místo "MenuItem".

## <a name="printpreviewcontrol-and-printpreviewdialog-accessibility-support"></a>Podpora přístupnosti PrintPreviewControl a PrintPreviewDialog

Pro ovládací prvky tisku platí následující změny:

- Vylepšená přístupná navigace (včetně navigace předčítání) prostřednictvím položek nabídky.
- Vylepšená podpora motivů s vysokým kontrastem a větší kontrastní prvek ovládacího prvku.

## <a name="stringcollectioneditor-accessibility-support"></a>Podpora usnadnění editoru StringCollectionEditor

Návrhář Windows Forms teď používá editor kolekce řetězců s vylepšenou podporou usnadnění přístupu.

## <a name="monthcalendar-accessibility-support-available-in-net-core-31"></a>Podpora přístupnosti MonthCalendar (k dispozici v rozhraní .NET Core 3.1)

Následující změny platí <xref:System.Windows.Forms.MonthCalendar> pro ovládací prvek:

- Přidáni zprostředkovatelé serveru `MonthCalendar` Automatizace uživatelského rozhraní k řízení, přidán vzor mřížky automatizace uživatelského rozhraní a zprostředkovatelé vzorů tabulky.
- Změněný typ ovládacího prvku přístupný `MonthCalendar` v _tabulce_ na typ ovládacího prvku _přístupného kalendářem_ s výjimkou případu, kdy má ovládací prvek předchozí ovládací prvek popisků, který definuje `MonthCalendar` název přístupný ovládacímu prvku, v tomto konkrétním případě přístupný typ ovládacího prvku se stane _tabulkou_.
- Vylepšené oznámení vybraného data `MonthCalendar` řízení.
- Vylepšená `MonthCalendar` podpora ovládání pro programy pro čtení z obrazovky a další nástroje pro usnadnění přístupu. V tuto chvíli mohou uživatelé procházet ovládací prvky a pracovat s těmito prvky pomocí zadávání pouze pomocí klávesnice. V programovém přepychu použijte k navigaci přes ovládací prvky klávesy CAPS + Enter klávesy CAPS +Enter.
- Vylepšená navigace `MonthCalendar` pomocí podřízených prvků pomocí zaostřovacího obdélníku: modrý obdélník zaostření pro Předčítání.
- Vylepšená přístupnost pro `MonthCalendar` akci testu `MonthCalendar` přístupů pro ovládací prvky, která umožňuje získání podřízeného přístupného prvku pomocí poskytnutých souřadnic.

## <a name="tooltips-accessibility-available-in-net-core-31"></a>Usnadnění přístupu k popisům (k dispozici v rozhraní .NET Core 3.1)

- Přidána možnost oznámit text popisku aplikacemi pro čtení z obrazovky, jako jsou NVDA a Předčítání. Aplikace pro čtení z obrazovky nyní může oznámit text klávesnice nebo popisku myši libovolného ovládacího prvku Windows Forms, který byl nakonfigurován tak, aby zobrazoval popisky.

## <a name="ui-automation-support-for-datagridview-propertygrid-listbox-combobox-toolstrip-and-other-controls"></a>Podpora automatizace uživatelského rozhraní pro ovládací prvky DataGridView, PropertyGrid, ListBox, ComboBox, ToolStrip a další ovládací prvky

Podpora automatizace uživatelského rozhraní je povolena pro ovládací prvky za běhu, ale nepoužívá se během návrhu. Přehled automatizace uživatelského rozhraní najdete v tématu [Přehled automatizace uživatelského rozhraní](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview).

## <a name="see-also"></a>Viz také

- [Doporučené postupy pro usnadnění přístupu](../ui-automation/accessibility-best-practices.md).

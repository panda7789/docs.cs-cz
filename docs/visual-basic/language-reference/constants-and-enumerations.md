---
title: Konstanty a výčty
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- constants [Visual Basic]
- constants [Visual Basic], list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
ms.openlocfilehash: 60cd1ddac9bca685ddc5778e7d289710245a183e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374483"
---
# <a name="constants-and-enumerations-visual-basic"></a>Konstanty a výčty (Visual Basic)

Visual Basic poskytuje řadu předdefinovaných konstant a výčtů pro vývojáře. Konstanty ukládají hodnoty, které zůstávají v průběhu provádění aplikace konstantní. Výčty poskytují pohodlný způsob práce se sadami souvisejících konstant a k přidružení konstantních hodnot k názvům.  
  
## <a name="constants"></a>Konstanty  
  
### <a name="conditional-compilation-constants"></a>Konstanty podmíněné kompilace  

 Následující tabulka uvádí předdefinované konstanty, které jsou k dispozici pro podmíněnou kompilaci.  
  
|**Trvalé**|**Popis**|  
|---|---|  
|`CONFIG`|Řetězec, který odpovídá aktuálnímu nastavení pole **Konfigurace aktivního řešení** v **Configuration Manager**.|  
|`DEBUG`|`Boolean`Hodnota, kterou lze nastavit v dialogovém okně **Vlastnosti projektu** . Ve výchozím nastavení definuje konfigurace ladění pro projekt `DEBUG` . Pokud `DEBUG` je definován, <xref:System.Diagnostics.Debug> metody třídy generují výstup do okna **výstup** . Pokud není definován, <xref:System.Diagnostics.Debug> metody třídy nejsou zkompilovány a není vygenerován žádný výstup ladění.|  
|`TARGET`|Řetězec představující typ výstupu pro projekt nebo nastavení možnosti příkazového řádku pro **cíl** . Možné hodnoty `TARGET` jsou:<br /><br /> – "winexe" pro aplikaci pro Windows.<br />– "exe" pro konzolovou aplikaci.<br />– "knihovna" pro knihovnu tříd.<br />– "modul" pro modul.<br />-Možnost- **target** lze nastavit v integrovaném vývojovém prostředí sady Visual Studio. Další informace najdete v tématu [-target (Visual Basic)](../reference/command-line-compiler/target.md).|  
|`TRACE`|`Boolean`Hodnota, kterou lze nastavit v dialogovém okně **Vlastnosti projektu** . Ve výchozím nastavení jsou definovány všechny konfigurace pro projekt `TRACE` . Pokud `TRACE` je definován, <xref:System.Diagnostics.Trace> metody třídy generují výstup do okna **výstup** . Pokud není definován, <xref:System.Diagnostics.Trace> metody třídy nejsou zkompilovány a `Trace` není vygenerován žádný výstup.|  
|`VBC_VER`|Číslo představující Visual Basic verze, v *Hlavní*. *vedlejší* formát|  
  
### <a name="print-and-display-constants"></a>Tisk a zobrazení konstant  

 Při volání funkcí Print a Display můžete v kódu místo skutečných hodnot použít následující konstanty.  
  
|**Trvalé**|**Popis**|  
|---|---|  
|`vbCrLf`|Kombinace znaků pro návrat na začátek řádku nebo odřádkování|  
|`vbCr`|Znak návratu na začátek řádku.|  
|`vbLf`|Znak odřádkování.|  
|`vbNewLine`|Znak nového řádku|  
|`vbNullChar`|Znak null|  
|`vbNullString`|Není stejný jako řetězec s nulovou délkou (""); používá se pro volání externích procedur.|  
|`vbObjectError`|Číslo chyby. Uživatelsky definovaná čísla chyb by měla být větší než tato hodnota. Příklad:<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|Znak tabulátoru.|  
|`vbBack`|Znak BACKSPACE.|  
|`vbFormFeed`|Nepoužívá se v systému Microsoft Windows.|  
|`vbVerticalTab`|Neužitečné v systému Microsoft Windows.|  
  
## <a name="enumerations"></a>Výčty  

 V následující tabulce jsou uvedeny a popsány výčty poskytované Visual Basic.  
  
|Výčet|Description|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|Určuje styl okna, který se má použít pro vyvolaný program při volání <xref:Microsoft.VisualBasic.Interaction.Shell%2A> funkce.|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|Označuje, jak přehrát zvuky při volání metod zvuku.|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|Určuje typ role, která se má ověřit při volání <xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A> metody.|  
|<xref:Microsoft.VisualBasic.CallType>|Určuje typ procedury, která se vyvolá při volání <xref:Microsoft.VisualBasic.Interaction.CallByName%2A> funkce.|  
|<xref:Microsoft.VisualBasic.CompareMethod>|Označuje způsob porovnávání řetězců při volání funkcí porovnání.|  
|<xref:Microsoft.VisualBasic.DateFormat>|Určuje, jak se mají zobrazovat data při volání <xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A> funkce.|  
|<xref:Microsoft.VisualBasic.DateInterval>|Určuje, jak určit a formátovat časové intervaly při volání funkcí souvisejících s datem.|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|Určuje, co se má provést, když adresář, který se má odstranit, obsahuje soubory nebo adresáře.|  
|<xref:Microsoft.VisualBasic.DueDate>|Určuje, kdy jsou platby splatné při volání finančních metod.|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|Označuje, zda jsou textová pole oddělena nebo pevná šířka.|  
|<xref:Microsoft.VisualBasic.FileAttribute>|Určuje atributy souboru, které se mají použít při volání funkcí přístupu k souborům.|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|Označuje první den v týdnu, který má být použit při volání funkcí souvisejících s datem.|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|Označuje první týden v roce, který má být použit při volání funkcí souvisejících s datem.|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|Určuje, které tlačítko bylo stisknuto na okně se zprávou, které vrátila <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkce.|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|Určuje, která tlačítka se mají zobrazit při volání <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkce.|  
|<xref:Microsoft.VisualBasic.OpenAccess>|Určuje, jak otevřít soubor při volání funkcí přístupu k souborům.|  
|<xref:Microsoft.VisualBasic.OpenMode>|Určuje, jak otevřít soubor při volání funkcí přístupu k souborům.|  
|<xref:Microsoft.VisualBasic.OpenShare>|Určuje, jak otevřít soubor při volání funkcí přístupu k souborům.|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|Určuje, jestli se má soubor trvale odstranit, nebo umístit do koše.|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|Určuje, zda mají být prohledány všechny nebo pouze adresáře nejvyšší úrovně.|  
|<xref:Microsoft.VisualBasic.TriState>|Označuje `Boolean` hodnotu, nebo zda má být při volání funkcí formátování čísel použito výchozí nastavení.|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|Určuje, co se má udělat, pokud uživatel klikne na **Zrušit** během operace.|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|Určuje, zda se má při kopírování, odstraňování a přesouvání souborů nebo adresářů zobrazovat dialogové okno průběhu.|  
|<xref:Microsoft.VisualBasic.VariantType>|Určuje typ objektu variant vráceného <xref:Microsoft.VisualBasic.Information.VarType%2A> funkcí.|  
|<xref:Microsoft.VisualBasic.VbStrConv>|Určuje, který typ převodu má být proveden při volání <xref:Microsoft.VisualBasic.Strings.StrConv%2A> funkce.|  
  
## <a name="see-also"></a>Viz také

- [Reference jazyka Visual Basic](index.md)
- [Přehled konstant](../programming-guide/language-features/constants-enums/constants-overview.md)
- [Přehled výčtů](../programming-guide/language-features/constants-enums/enumerations-overview.md)

---
title: Konstanty a výčty
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- constants [Visual Basic]
- constants [Visual Basic], list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
ms.openlocfilehash: e47fd1c606f7d4cd0cf2fa6398beaa183ed95076
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838153"
---
# <a name="constants-and-enumerations-visual-basic"></a>Konstanty a výčty (Visual Basic)

Visual Basic poskytuje řadu předdefinovaných konstant a výčtů pro vývojáře. Konstanty ukládají hodnoty, které zůstávají v průběhu provádění aplikace konstantní. Výčty poskytují pohodlný způsob práce se sadami souvisejících konstant a k přidružení konstantních hodnot k názvům.  
  
## <a name="constants"></a>Konstanty  
  
### <a name="conditional-compilation-constants"></a>Konstanty podmíněné kompilace  

 Následující tabulka uvádí předdefinované konstanty, které jsou k dispozici pro podmíněnou kompilaci.  
  
|**Změnil**|**Popis**|  
|---|---|  
|`CONFIG`|Řetězec, který odpovídá aktuálnímu nastavení pole **Konfigurace aktivního řešení** v **Configuration Manager**.|  
|`DEBUG`|Hodnota `Boolean`, kterou lze nastavit v dialogovém okně **Vlastnosti projektu** . Ve výchozím nastavení konfigurace ladění pro projekt definuje `DEBUG`. Pokud je definována `DEBUG`, metody třídy <xref:System.Diagnostics.Debug> generují výstup do okna **výstup** . Pokud není definován, <xref:System.Diagnostics.Debug> metody třídy nejsou zkompilovány a není vygenerován žádný výstup ladění.|  
|`TARGET`|Řetězec představující typ výstupu pro projekt nebo nastavení možnosti **/target** příkazového řádku. Možné hodnoty `TARGET` jsou:<br /><br /> – "winexe" pro aplikaci pro Windows.<br />– "exe" pro konzolovou aplikaci.<br />– "knihovna" pro knihovnu tříd.<br />– "modul" pro modul.<br />-Možnost **/target** lze nastavit v integrovaném vývojovém prostředí sady Visual Studio. Další informace najdete v tématu [-target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`TRACE`|Hodnota `Boolean`, kterou lze nastavit v dialogovém okně **Vlastnosti projektu** . Ve výchozím nastavení všechny konfigurace pro projekt definují `TRACE`. Pokud je definována `TRACE`, metody třídy <xref:System.Diagnostics.Trace> generují výstup do okna **výstup** . Pokud není definován, <xref:System.Diagnostics.Trace> metody třídy nejsou kompilovány a není vygenerován žádný `Trace` výstup.|  
|`VBC_VER`|Číslo představující Visual Basic verze, v *Hlavní*. *vedlejší* formát|  
  
### <a name="print-and-display-constants"></a>Tisk a zobrazení konstant  

 Při volání funkcí Print a Display můžete v kódu místo skutečných hodnot použít následující konstanty.  
  
|**Změnil**|**Popis**|  
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
  
|Výčet|Popis|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|Určuje styl okna, který se má použít pro vyvolaný program při volání funkce <xref:Microsoft.VisualBasic.Interaction.Shell%2A>.|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|Označuje, jak přehrát zvuky při volání metod zvuku.|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|Určuje typ role, která se má ověřit při volání metody <xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>.|  
|<xref:Microsoft.VisualBasic.CallType>|Určuje typ procedury, která se vyvolá při volání funkce <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>.|  
|<xref:Microsoft.VisualBasic.CompareMethod>|Označuje způsob porovnávání řetězců při volání funkcí porovnání.|  
|<xref:Microsoft.VisualBasic.DateFormat>|Určuje, jak se mají zobrazovat data při volání funkce <xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>.|  
|<xref:Microsoft.VisualBasic.DateInterval>|Určuje, jak určit a formátovat časové intervaly při volání funkcí souvisejících s datem.|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|Určuje, co se má provést, když adresář, který se má odstranit, obsahuje soubory nebo adresáře.|  
|<xref:Microsoft.VisualBasic.DueDate>|Určuje, kdy jsou platby splatné při volání finančních metod.|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|Označuje, zda jsou textová pole oddělena nebo pevná šířka.|  
|<xref:Microsoft.VisualBasic.FileAttribute>|Určuje atributy souboru, které se mají použít při volání funkcí přístupu k souborům.|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|Označuje první den v týdnu, který má být použit při volání funkcí souvisejících s datem.|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|Označuje první týden v roce, který má být použit při volání funkcí souvisejících s datem.|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|Určuje, které tlačítko bylo stisknuto na okně se zprávou, které vrátila funkce <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>.|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|Určuje, která tlačítka se zobrazí při volání funkce <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>.|  
|<xref:Microsoft.VisualBasic.OpenAccess>|Určuje, jak otevřít soubor při volání funkcí přístupu k souborům.|  
|<xref:Microsoft.VisualBasic.OpenMode>|Určuje, jak otevřít soubor při volání funkcí přístupu k souborům.|  
|<xref:Microsoft.VisualBasic.OpenShare>|Určuje, jak otevřít soubor při volání funkcí přístupu k souborům.|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|Určuje, jestli se má soubor trvale odstranit, nebo umístit do koše.|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|Určuje, zda mají být prohledány všechny nebo pouze adresáře nejvyšší úrovně.|  
|<xref:Microsoft.VisualBasic.TriState>|Označuje `Boolean` hodnotu nebo, zda má být při volání funkcí formátování čísel použito výchozí nastavení.|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|Určuje, co se má udělat, pokud uživatel klikne na **Zrušit** během operace.|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|Určuje, zda se má při kopírování, odstraňování a přesouvání souborů nebo adresářů zobrazovat dialogové okno průběhu.|  
|<xref:Microsoft.VisualBasic.VariantType>|Určuje typ objektu variant vrácený funkcí <xref:Microsoft.VisualBasic.Information.VarType%2A>.|  
|<xref:Microsoft.VisualBasic.VbStrConv>|Určuje, který typ převodu má být proveden při volání funkce <xref:Microsoft.VisualBasic.Strings.StrConv%2A>.|  
  
## <a name="see-also"></a>Viz také:

- [Referenční příručka jazyka Visual Basic](../../visual-basic/language-reference/index.md)
- [Přehled konstant](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Přehled výčtů](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)

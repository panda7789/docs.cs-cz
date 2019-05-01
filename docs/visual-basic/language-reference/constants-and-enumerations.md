---
title: Konstanty a výčty (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- constants [Visual Basic]
- constants [Visual Basic], list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
ms.openlocfilehash: 0a9c01269e12c2d84be4f30c236c439012a88153
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013904"
---
# <a name="constants-and-enumerations-visual-basic"></a>Konstanty a výčty (Visual Basic)
Visual Basic poskytuje řadu předdefinovaných konstanty a výčty pro vývojáře. Konstanty ukládání hodnot, které zůstávají neměnný po celou dobu spuštění aplikace. Výčty poskytují pohodlný způsob pro práci se sadami související s konstantami a přidružení konstantních hodnot s názvy.  
  
## <a name="constants"></a>Konstanty  
  
### <a name="conditional-compilation-constants"></a>Konstanty pro podmíněnou kompilaci  
 V následující tabulce jsou uvedeny předdefinované konstanty, které jsou dostupné pro podmíněnou kompilaci.  
  
|**Konstanty**|**Popis**|  
|---|---|  
|`CONFIG`|Řetězec, který odpovídá aktuální nastavení **aktivní konfigurace řešení** pole **nástroje Configuration Manager**.|  
|`DEBUG`|A `Boolean` hodnotu, která je možné nastavit v **vlastnosti projektu** dialogové okno. Ve výchozím nastavení, konfiguraci ladění pro projekt definuje `DEBUG`. Když `DEBUG` je definován, <xref:System.Diagnostics.Debug> metody třídy generovat výstup do **výstup** okna. Pokud není definované, <xref:System.Diagnostics.Debug> metody třídy nejsou zkompilovány a nebude vygenerován žádný výstup ladění.|  
|`TARGET`|Řetězec představující typ výstupu pro projekt, nebo nastavení příkazového řádku **/target** možnost. Možné hodnoty `TARGET` jsou:<br /><br /> -"winexe" pro aplikace Windows.<br />-řetězec "exe" pro konzolové aplikace.<br />-"library" pro knihovnu tříd.<br />-"modul" pro modul.<br />– **/Target** možnost může být nastavena v integrovaném vývojovém prostředí sady Visual Studio. Další informace najdete v tématu [/Target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`TRACE`|A `Boolean` hodnotu, která je možné nastavit v **vlastnosti projektu** dialogové okno. Ve výchozím nastavení, všechny konfigurace projektu definovat `TRACE`. Když `TRACE` je definován, <xref:System.Diagnostics.Trace> metody třídy generovat výstup do **výstup** okna. Pokud není definované, <xref:System.Diagnostics.Trace> třídy, metody nejsou zkompilovány ale žádné `Trace` výstup vygenerován.|  
|`VBC_VER`|Číslo, které představuje verzi jazyka Visual Basic v *hlavní*. *vedlejší* formátu. Číslo verze pro [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)] je 8.0.|  
  
### <a name="print-and-display-constants"></a>Tisk a zobrazení konstanty  
 Při volání tisku a zobrazit funkce, můžete ve svém kódu místo skutečných hodnot použít následující konstanty.  
  
|**Konstanty**|**Popis**|  
|---|---|  
|`vbCrLf`|Návrat na začátek řádku kombinaci znaků návrat a odřádkování.|  
|`vbCr`|Návratový znak.|  
|`vbLf`|Znak odřádkování.|  
|`vbNewLine`|Znak nového řádku.|  
|`vbNullChar`|Znak null.|  
|`vbNullString`|Není stejný jako řetězec nulové délky (""); použít pro volání externí procedury.|  
|`vbObjectError`|Číslo chyby. Uživatelem definované chybové čísla musí být větší než tato hodnota. Příklad:<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|Znak tabulátoru.|  
|`vbBack`|Znak Backspace.|  
|`vbFormFeed`|Nepoužívá se v Microsoft Windows.|  
|`vbVerticalTab`|V Microsoft Windows nejsou moc užitečná.|  
  
## <a name="enumerations"></a>Výčty  
 Následující tabulka uvádí a popisuje výčty poskytované jazyka Visual Basic.  
  
|Výčet|Popis|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|Určuje styl okna pro vyvolaný program budete používat při volání <xref:Microsoft.VisualBasic.Interaction.Shell%2A> funkce.|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|Určuje, jak má-li přehrát zvuky, při volání metody zvuku.|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|Určuje typ role ke kontrole při volání <xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A> metody.|  
|<xref:Microsoft.VisualBasic.CallType>|Určuje typ volané při volání procedury <xref:Microsoft.VisualBasic.Interaction.CallByName%2A> funkce.|  
|<xref:Microsoft.VisualBasic.CompareMethod>|Určuje, jak porovnat řetězce při volání funkce porovnání.|  
|<xref:Microsoft.VisualBasic.DateFormat>|Určuje, jak zobrazit data při volání <xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A> funkce.|  
|<xref:Microsoft.VisualBasic.DateInterval>|Určuje, jak určit a formátování časové intervaly při volání funkce související s datem.|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|Určuje, co by mělo být provedeno, když adresář, který má být odstraněn obsahuje soubory nebo adresáře.|  
|<xref:Microsoft.VisualBasic.DueDate>|Určuje způsob platby při volání metody finanční.|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|Určuje, zda jsou oddělené textová pole nebo pevnou šířkou.|  
|<xref:Microsoft.VisualBasic.FileAttribute>|Určuje atributy souborů pro použití při volání funkcí přístup k souborům.|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|Určuje první den v týdnu, kdy chcete použít při volání funkce související s datem.|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|Určuje první týden v roce určený při volání funkce související s datem.|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|Indikuje stisknutí tlačítka, které na okno se zprávou, vrácený <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkce.|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|Označuje tlačítek, která se zobrazí při volání <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkce.|  
|<xref:Microsoft.VisualBasic.OpenAccess>|Určuje, jak otevřít soubor při volání funkcí přístup k souborům.|  
|<xref:Microsoft.VisualBasic.OpenMode>|Určuje, jak otevřít soubor při volání funkcí přístup k souborům.|  
|<xref:Microsoft.VisualBasic.OpenShare>|Určuje, jak otevřít soubor při volání funkcí přístup k souborům.|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|Určuje, zda soubor trvale odstraněn nebo umístit do složky Koš.|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|Určuje, jestli se má hledat ve všech nebo jenom na nejvyšší úrovni adresáře.|  
|<xref:Microsoft.VisualBasic.TriState>|Označuje `Boolean` hodnotu nebo výchozí hodnota určuje, zda má být použit při volání funkcí formátování čísel.|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|Určuje, co by mělo být provedeno v případě, že uživatel klikne **zrušit** během operace.|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|Určuje, jestli se má zobrazit dialogové okno průběhu při kopírování, odstraňování, přesouvání souborů či adresářů.|  
|<xref:Microsoft.VisualBasic.VariantType>|Určuje typ objektu variant, vrátí <xref:Microsoft.VisualBasic.Information.VarType%2A> funkce.|  
|<xref:Microsoft.VisualBasic.VbStrConv>|Určuje, jaký typ převodu se provede při volání <xref:Microsoft.VisualBasic.Strings.StrConv%2A> funkce.|  
  
## <a name="see-also"></a>Viz také:

- [Referenční příručka jazyka Visual Basic](../../visual-basic/language-reference/index.md)
- [Visual Basic](../../visual-basic/index.md)
- [Přehled konstant](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Přehled výčtů](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)

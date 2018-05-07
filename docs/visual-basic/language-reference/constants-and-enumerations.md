---
title: Konstanty a výčty (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- constants [Visual Basic]
- constants [Visual Basic], list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
ms.openlocfilehash: fcc3329d6e02a77bf54b5b9f08fddba1bc95ff54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="constants-and-enumerations-visual-basic"></a>Konstanty a výčty (Visual Basic)
Visual Basic poskytuje řadu předdefinovaných konstanty a výčty pro vývojáře. Konstanty ukládat hodnoty, které zůstat konstantní po spuštění aplikace. Výčty poskytují pohodlný způsob pro práci se sadami související konstanty a přidružení konstantních hodnot k názvy.  
  
## <a name="constants"></a>Konstanty  
  
### <a name="conditional-compilation-constants"></a>Konstanty Podmíněná kompilace  
 Následující tabulka uvádí předdefinované konstanty, které jsou k dispozici pro Podmíněná kompilace.  
  
|**Konstantní**|**Popis**|  
|---|---|  
|`CONFIG`|Řetězec, který odpovídá aktuální nastavení **aktivní konfigurace řešení** pole **nástroje Configuration Manager**.|  
|`DEBUG`|A `Boolean` hodnotu, která může být nastavena v **vlastnosti projektu** dialogové okno. Ve výchozím nastavení, konfiguraci ladění pro projekt definuje `DEBUG`. Když `DEBUG` je definován <xref:System.Diagnostics.Debug> metody třídy generovat výstup do **výstup** okno. Pokud není definován, <xref:System.Diagnostics.Debug> metody třídy nejsou kompilovány a nevygeneruje žádný výstup ladění.|  
|`TARGET`|Řetězec představující výstupní typ pro projekt nebo nastavení příkazového řádku **/target** možnost. Možné hodnoty `TARGET` jsou:<br /><br /> -"winexe" pro aplikaci systému Windows.<br />-"exe" pro konzolové aplikace.<br />-"library" pro knihovny tříd.<br />-"module" pro modul.<br />-Na **/target** možnost může být nastaven v integrovaném vývojovém prostředí sady Visual Studio. Další informace najdete v tématu [/Target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`TRACE`|A `Boolean` hodnotu, která může být nastavena v **vlastnosti projektu** dialogové okno. Ve výchozím nastavení, zadejte všechny konfigurace pro projekt `TRACE`. Když `TRACE` je definován <xref:System.Diagnostics.Trace> metody třídy generovat výstup do **výstup** okno. Pokud není definován, <xref:System.Diagnostics.Trace> třídy nejsou kompilovány metody a ne `Trace` nevygeneruje výstup.|  
|`VBC_VER`|Číslo, které představuje verzi jazyka Visual Basic, v *hlavní*. *méně závažné* formátu. Číslo verze pro [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)] je 8.0.|  
  
### <a name="print-and-display-constants"></a>Tiskové a zobrazení konstanty  
 Při volání tisku a zobrazit funkce, můžete použít následující konstanty ve vašem kódu místo skutečných hodnot.  
  
|**Konstantní**|**Popis**|  
|---|---|  
|`vbCrLf`|Kombinace znaků CR znak vrátit/konce řádku.|  
|`vbCr`|Návratový znak.|  
|`vbLf`|Znaky konce řádku.|  
|`vbNewLine`|Znak nového řádku.|  
|`vbNullChar`|Znak hodnoty Null.|  
|`vbNullString`|Není stejný jako řetězec nulové délky (""); použít pro volání externí procedur.|  
|`vbObjectError`|Číslo chyby. Uživatelem definované chybové čísla musí být větší než tato hodnota. Příklad:<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|Znak tabulátoru.|  
|`vbBack`|BACKSPACE znak.|  
|`vbFormFeed`|Nepoužívá se v systému Windows.|  
|`vbVerticalTab`|Není užitečné v systému Windows.|  
  
## <a name="enumerations"></a>Výčty  
 Následující tabulka uvádí a popisuje výčty poskytované jazyka Visual Basic.  
  
|Výčet|Popis|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|Určuje styl okna používat pro programu vyvolaná při volání <xref:Microsoft.VisualBasic.Interaction.Shell%2A> funkce.|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|Určuje, jak k přehrání zvuků při volání metody zvuk.|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|Určuje typ role ke kontrole při volání metody <xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A> metoda.|  
|<xref:Microsoft.VisualBasic.CallType>|Určuje typ volanou při volání procedury <xref:Microsoft.VisualBasic.Interaction.CallByName%2A> funkce.|  
|<xref:Microsoft.VisualBasic.CompareMethod>|Určuje, jak porovnat řetězce při volání funkce porovnání.|  
|<xref:Microsoft.VisualBasic.DateFormat>|Určuje, jak zobrazit data při volání metody <xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A> funkce.|  
|<xref:Microsoft.VisualBasic.DateInterval>|Určuje, jak určit a formátu časových intervalů při volání funkcí souvisejících s datem.|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|Určuje, co se má provést při adresáře, který má být odstraněn obsahuje soubory a adresáře.|  
|<xref:Microsoft.VisualBasic.DueDate>|Určuje způsob platby při volání metody finanční.|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|Určuje, jestli jsou oddělené textových polí nebo pevnou šířkou.|  
|<xref:Microsoft.VisualBasic.FileAttribute>|Určuje atributy souborů pro použití při volání přístup k souborům funkcí.|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|Označuje první den v týdnu pro použití při volání funkcí souvisejících s datem.|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|Označuje první týden v roce pro použití při volání funkcí souvisejících s datem.|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|Určuje, které tlačítko došlo ke stisknutí tlačítka v okně se zprávou, vrácený <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkce.|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|Označuje tlačítek, která se zobrazí při volání metody <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkce.|  
|<xref:Microsoft.VisualBasic.OpenAccess>|Určuje, jak otevřít soubor při volání metody přístupu k souborům funkcí.|  
|<xref:Microsoft.VisualBasic.OpenMode>|Určuje, jak otevřít soubor při volání metody přístupu k souborům funkcí.|  
|<xref:Microsoft.VisualBasic.OpenShare>|Určuje, jak otevřít soubor při volání metody přístupu k souborům funkcí.|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|Určuje, zda by měl být soubor trvale odstraněn nebo umístěny v koši.|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|Určuje, jestli má vyhledat všechny nebo pouze nejvyšší úrovně adresáře.|  
|<xref:Microsoft.VisualBasic.TriState>|Označuje `Boolean` hodnotu nebo výchozí jestli se mají použít při volání funkcí formátování čísel.|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|Určuje, jaké je třeba provést v případě, že uživatel klikne na **zrušit** během operace.|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|Určuje, zda se má zobrazit dialogové okno průběhu při kopírování, odstranění nebo přesunutí souborů či adresářů.|  
|<xref:Microsoft.VisualBasic.VariantType>|Určuje typ variant objekt vrácený <xref:Microsoft.VisualBasic.Information.VarType%2A> funkce.|  
|<xref:Microsoft.VisualBasic.VbStrConv>|Určuje, jaký typ převodu se provede při volání <xref:Microsoft.VisualBasic.Strings.StrConv%2A> funkce.|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka Visual Basic](../../visual-basic/language-reference/index.md)  
 [Visual Basic](../../visual-basic/index.md)  
 [Přehled konstant](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Přehled výčtů](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)

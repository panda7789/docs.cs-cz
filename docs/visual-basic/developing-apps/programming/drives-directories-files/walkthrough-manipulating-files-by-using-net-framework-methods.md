---
title: Manipulace se soubory pomocí metod rozhraní .NET Framework (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], walkthroughs
- text files [Visual Basic], writing to
- reading text files [Visual Basic]
- text, writing to files
- files [Visual Basic], searching
- StreamReader class, walkthroughs
- files [Visual Basic], accessing
- I/O [Visual Basic], writing text to files
- writing to files [Visual Basic], walkthroughs
- StreamWriter class, walkthroughs
- text files [Visual Basic], reading
- I/O [Visual Basic], reading text from files
ms.assetid: 7d2109eb-f98a-4389-b43d-30f384aaa7d5
ms.openlocfilehash: 56d753c9bb4e3585049eb98929774ac810d8ed40
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978173"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a>Návod: Manipulace se soubory pomocí metod rozhraní .NET Framework (Visual Basic)
Tento návod ukazuje, jak otevřít a přečíst soubor pomocí <xref:System.IO.StreamReader> třídy, zkontrolujte, pokud je přístupu k souboru, hledání řetězce v rámci souboru pro čtení s instancí <xref:System.IO.StreamReader> třídy a zápis do souboru pomocí <xref:System.IO.StreamWriter> třídy.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-application"></a>Vytvoření aplikace  
 Spusťte sadu Visual Studio a začněte projektu tak, že vytvoříte formuláře, který může uživatel použít k zápisu do určeného souboru.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Na **souboru** nabídce vyberte možnost **nový projekt**.  
  
2.  V **nový projekt** podokně klikněte na tlačítko **aplikace Windows**.  
  
3.  V **název** zadejte `MyDiary` a klikněte na tlačítko **OK**.  
  
     Visual Studio přidá projekt do **Průzkumníka řešení**a **Návrháře formulářů Windows** otevře.  
  
4.  Přidat ovládací prvky do formuláře v následující tabulce a nastavit odpovídající hodnoty pro jejich vlastností.  
  
|**objekt**|**Vlastnosti**|**Hodnota**|  
|---|---|---|   
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**|`Submit`<br /><br /> **Odeslat položku**|  
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**|`Clear`<br /><br /> **Vymazat položky**|  
|<xref:System.Windows.Forms.TextBox>|**Název**<br /><br /> **Text**<br /><br /> **Multiline**|`Entry`<br /><br /> **Zadejte prosím něco.**<br /><br /> `False`|  
  
## <a name="writing-to-the-file"></a>Při zápisu do souboru  
 Chcete-li přidat možnost zapisovat do souboru pomocí aplikace, použijte <xref:System.IO.StreamWriter> třídy. <xref:System.IO.StreamWriter> je navržená pro výstup znaků v určitém kódování, že <xref:System.IO.Stream> třídy je navržená pro bajtový vstup a výstup. Použití <xref:System.IO.StreamWriter> pro řádky informace do standardního textového souboru. Další informace o <xref:System.IO.StreamWriter> najdete v tématu <xref:System.IO.StreamWriter>.  
  
#### <a name="to-add-writing-functionality"></a>Chcete-li přidat funkce zápisu  
  
1.  Z **zobrazení** nabídce zvolte **kód** otevřete Editor kódu.  
  
2.  Vzhledem k tomu, že aplikace musí odkazovat <xref:System.IO> obor názvů, přidejte následující příkazy na začátek vašeho kódu, před deklaraci třídy pro formulář, který začíná `Public Class Form1`.  
  
     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]  
  
     Před zápisem do souboru, je nutné vytvořit instanci <xref:System.IO.StreamWriter> třídy.  
  
3.  Z **zobrazení** nabídce zvolte **návrháře** se vraťte do **Návrháře formulářů Windows**. Dvakrát klikněte `Submit` pro vytvoření <xref:System.Windows.Forms.Control.Click> obslužnou rutinu události pro tlačítko a pak přidejte následující kód.  
  
     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]  
  
> [!NOTE]
>  Visual Studio integrované vývojové prostředí (IDE) se vraťte do editoru kódu a umístěte kurzor v rámci obslužné rutiny událostí, kde by měl přidat kód.  
  
1.  Chcete-li zapsat do souboru, použijte <xref:System.IO.StreamWriter.Write%2A> metodu <xref:System.IO.StreamWriter> třídy. Následující kód přidejte přímo po `Dim fw As StreamWriter`. Nemusíte se obávat, bude vyvolána výjimka pokud soubor není nalezen, protože se vytvoří, pokud ještě neexistuje.  
  
     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]  
  
2.  Ujistěte se, že uživatel nemůže odeslat prázdná položka přidáním následujícího kódu přímo po `Dim ReadString As String`.  
  
     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]  
  
3.  Protože se jedná o zápisník, uživatel bude chtít přiřadit data u každé položky. Vložte kód následující po `fw = New StreamWriter("C:\MyDiary.txt", True)` nastavit proměnnou `Today` k aktuálnímu datu.  
  
     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]  
  
4.  Nakonec připojení kódu k vymazání <xref:System.Windows.Forms.TextBox>. Přidejte následující kód, který `Clear` tlačítka <xref:System.Windows.Forms.Control.Click> událostí.  
  
     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]  
  
## <a name="adding-display-features-to-the-diary"></a>Přidání funkcí zobrazení do deníku  
 V této části je přidána funkce, která zobrazuje poslední položka v `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Můžete také přidat <xref:System.Windows.Forms.ComboBox> , který zobrazí různé položky a ze kterého může uživatel vybrat položku v zobrazení `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Instance <xref:System.IO.StreamReader> třídy čtení záznamů z `MyDiary.txt`. Podobně jako <xref:System.IO.StreamWriter> třídy, <xref:System.IO.StreamReader> je určena pro použití s textovými soubory.  
  
 Pro tato část návodu přidejte do formuláře ovládací prvky v následující tabulce a nastavte odpovídající hodnoty pro jejich vlastností.  
  
|Control|Vlastnosti|Hodnoty|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.TextBox>|**Název**<br /><br /> **Viditelné**<br /><br /> **Velikost**<br /><br /> **Multiline**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|  
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**|`Display`<br /><br /> **Zobrazení**|  
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**|`GetEntries`<br /><br /> **Získání položky**|  
|<xref:System.Windows.Forms.ComboBox>|**Název**<br /><br /> **Text**<br /><br /> **Povoleno**|`PickEntries`<br /><br /> **Vyberte položku**<br /><br /> `False`|  
  
#### <a name="to-populate-the-combo-box"></a>K naplnění pole se seznamem  
  
1.  `PickEntries` <xref:System.Windows.Forms.ComboBox> Slouží k zobrazení kalendářních dat, na kterých uživatel odešle jednotlivých položek, takže uživatel může vybrat položku z konkrétní datum. Vytvoření <xref:System.Windows.Forms.Control.Click> obslužnou rutinu události `GetEntries` tlačítko a přidejte následující kód.  
  
     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]  
  
2.  K testování kódu, stiskněte klávesu F5 a který aplikaci zkompiluje a potom klikněte na tlačítko **najít položky**. Klikněte na šipku rozevíracího seznamu v <xref:System.Windows.Forms.ComboBox> zobrazíte vstupní data.  
  
#### <a name="to-choose-and-display-individual-entries"></a>Vybrat a zobrazit jednotlivé položky  
  
1.  Vytvoření <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro `Display` tlačítko a přidejte následující kód.  
  
     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]  
  
2.  K testování kódu, stiskněte klávesu F5, chcete-li zkompilovat aplikaci a pak odeslat záznam. Klikněte na tlačítko **najít položky**, vyberte položku ze <xref:System.Windows.Forms.ComboBox>a potom klikněte na tlačítko **zobrazení**. Obsah vybrané položky se zobrazí v `DisplayEntry` <xref:System.Windows.Forms.TextBox>.  
  
## <a name="enabling-users-to-delete-or-modify-entries"></a>Povolení uživatelům odstranit nebo upravit položky  
 A konečně může obsahovat další funkce umožňuje uživatelům odstranit nebo upravit záznam pomocí `DeleteEntry` a `EditEntry` tlačítka. Obě tlačítka zůstanou zakázané, pokud se zobrazí záznam.  
  
 Přidat ovládací prvky do formuláře v následující tabulce a nastavit odpovídající hodnoty pro jejich vlastností.  
  
|Control|Vlastnosti|Hodnoty|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**<br /><br /> **Povoleno**|`DeleteEntry`<br /><br /> **Odstranit položku**<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**<br /><br /> **Povoleno**|`EditEntry`<br /><br /> **Upravit položku**<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Název**<br /><br /> **Text**<br /><br /> **Povoleno**|`SubmitEdit`<br /><br /> **Odeslání úpravy**<br /><br /> `False`|  
  
#### <a name="to-enable-deletion-and-modification-of-entries"></a>Chcete-li povolit odstraňování a úpravy záznamů  
  
1.  Přidejte následující kód, který `Display` tlačítka <xref:System.Windows.Forms.Control.Click> události, poté, co `DisplayEntry.Text = ReadString`.  
  
     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]  
  
2.  Vytvoření <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro `DeleteEntry` tlačítko a přidejte následující kód.  
  
     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]  
  
3.  Když uživatel zobrazí záznam, `EditEntry` aktivuje tlačítko. Přidejte následující kód, který <xref:System.Windows.Forms.Control.Click> událost `Display` tlačítko po `DisplayEntry.Text = ReadString`.  
  
     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]  
  
4.  Vytvoření <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro `EditEntry` tlačítko a přidejte následující kód.  
  
     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]  
  
5.  Vytvoření <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro `SubmitEdit` tlačítko a přidejte následující kód  
  
     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]  
  
 K testování kódu, stiskněte klávesu F5 pro kompilaci aplikace. Klikněte na tlačítko **najít položky**, vyberte položku a pak klikněte na tlačítko **zobrazení**. Položka se zobrazí v `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Klikněte na tlačítko **upravte položku**. Položka se zobrazí v `Entry` <xref:System.Windows.Forms.TextBox>. Upravte položku ve `Entry` <xref:System.Windows.Forms.TextBox> a klikněte na tlačítko **Odeslat úpravu**. Otevřít `MyDiary.txt` souboru k ověření vašich oprav. Teď vyberte položku a klikněte na tlačítko **odstranit položku**. Když <xref:System.Windows.Forms.MessageBox> požádá o potvrzení, klikněte na tlačítko **OK**. Ukončete aplikaci a otevřete `MyDiary.txt` potvrďte odstranění.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [Návody](../../../../visual-basic/walkthroughs.md)

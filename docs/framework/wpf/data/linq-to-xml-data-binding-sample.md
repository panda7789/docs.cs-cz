---
title: Příklad datové vazby LINQ to XML
ms.date: 10/22/2019
ms.topic: sample
helpviewer_keywords:
- linq to xml data binding sample
ms.openlocfilehash: aac814e4768a863a93e69e34cd18c941a9b35c89
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920935"
---
# <a name="linq-to-xml-data-binding-sample"></a>Ukázka datové vazby LINQ to XML

Tento článek popisuje ukázku příkladu LinqToXmlDataBinding, aplikaci Windows Presentation Foundation (WPF), která váže součásti uživatelského rozhraní k vloženému zdroji dat XML.

## <a name="overview"></a>Přehled

Ukázka příkladu LinqToXmlDataBinding je aplikace Windows Presentation Foundation (WPF), která obsahuje C# zdrojové soubory a XAML. Vložený dokument XML definuje seznam knih. Aplikace umožňuje uživateli zobrazovat, přidávat, odstraňovat a upravovat položky knihy.

Existují dva primární zdrojové soubory:

- [Zdrojový kód L2DBForm. XAML](l2dbform-xaml-source-code.md) obsahuje kód deklarace XAML pro uživatelské rozhraní (UI) hlavního okna. Obsahuje také oddíl prostředků okna definující poskytovatele dat a vložený dokument XML pro výpisy knih.

- [L2DBForm.XAML.cs](l2dbform-xaml-cs-source-code.md) obsahuje metody inicializace a zpracování událostí přidružené k uživatelskému rozhraní.

Hlavní okno je rozdělené do následujících čtyř oddílů vertikálního uživatelského rozhraní:

- **XML** zobrazí nezpracovaný zdroj XML se seznamem vložených knih.

- **Seznam knih** zobrazuje položky knihy jako standardní text a umožňuje uživateli vybrat a odstranit jednotlivé položky.

- **Možnost upravit vybranou knihu** umožňuje uživateli upravovat hodnoty spojené s aktuálně vybranou položkou knihy.

- Možnost **Přidat novou knihu** umožňuje vytvořit novou položku knihy na základě hodnot zadaných uživatelem.

## <a name="run-the-sample"></a>Spuštění ukázky

V této části se dozvíte, jak vytvořit a sestavit projekt příkladu LinqToXmlDataBinding v aplikaci Visual Studio a jak spustit výslednou aplikaci v příkladu LinqToXmlDataBinding Windows Presentation Foundation (WPF).

### <a name="create-the-project"></a>Vytvoření projektu

1. Otevřete Visual Studio a vytvořte C# **aplikaci WPF** s názvem **příkladu LinqToXmlDataBinding**.

   Projekt by měl cílit na .NET Framework 3,5 (nebo novější).

1. Pokud ještě není k dispozici, přidejte odkazy na projekt pro následující sestavení .NET:

    - System.Data
    - System. data. DataSetExtensions
    - System.Xml
    - System.Xml

1. Sestavte řešení stisknutím **kombinace kláves Ctrl** +**SHIFT** +**B**a pak ho spusťte stisknutím klávesy **F5**.

   Projekt by se měl kompilovat bez chyb a spustit jako obecná aplikace WPF.

### <a name="add-code"></a>Přidat kód

1. V **Průzkumník řešení**přejmenujte zdrojový soubor **Window1. XAML** na **L2XDBForm. XAML**.

   Závislý zdrojový soubor Window1.xaml.cs se automaticky přejmenuje na L2XDBForm.xaml.cs.

1. Nahraďte zdrojový kód, který se nachází v souboru **L2XDBForm. XAML** , pomocí [zdrojového kódu zdrojový kód L2DBForm. XAML](l2dbform-xaml-source-code.md). Pro práci s tímto souborem použijte zobrazení zdroje XAML.

1. Podobně nahraďte zdroj v **L2XDBForm.XAML.cs** [zdrojovým kódem L2DBForm.XAML.cs](l2dbform-xaml-cs-source-code.md).

1. V souboru **App. XAML**nahraďte všechny výskyty řetězce **Window1. XAML** pomocí **L2XDBForm. XAML**.

1. Sestavte řešení stisknutím **kombinace kláves Ctrl** +**SHIFT** +**B**.

### <a name="run-the-app"></a>Spuštění aplikace

Aplikace příkladu LinqToXmlDataBinding umožňuje uživateli zobrazit a manipulovat se seznamem knih, které jsou uloženy jako vložený prvek XML. Spusťte aplikaci stisknutím klávesy **F5** (Spustit ladění) nebo **kombinací kláves CTRL**+**F5** (spustit bez ladění).

Zobrazí se okno programu s názvem **datová vazba WPF pomocí LINQ to XML** .

V horní části uživatelského rozhraní se zobrazuje nezpracovaný **soubor XML** , který představuje seznam knih. Zobrazuje se pomocí ovládacího prvku WPF <xref:System.Windows.Controls.TextBlock>, který neumožňuje interakci přes myš ani klávesnici.

Druhá svislá sekce, označená jako **seznam knihy**, zobrazuje knihy jako seznam seřazený jako prostý text. Používá ovládací prvek <xref:System.Windows.Controls.ListBox>, který umožňuje výběr i přes myš nebo klávesnici.

### <a name="add-and-delete-books"></a>Přidávání a odstraňování knih

Pokud chcete do seznamu přidat novou knihu, zadejte hodnoty do pole **ID** a **hodnota** <xref:System.Windows.Controls.TextBox> ovládací prvky v poslední části, **přidejte novou knihu**a pak vyberte **Přidat knihu**. Kniha se připojí k seznamu v knize i ve výpisech XML. Tento program neověřuje vstupní hodnoty.

Pokud chcete odstranit existující knihu ze seznamu, vyberte ji v části **seznam knih** a pak vyberte **Odebrat vybranou knihu**. Položka knihy se odebere z knihy i z nezpracovaného zdrojového seznamu XML.

### <a name="edit-a-book-entry"></a>Úprava položky knihy

1. V části seznamu druhých **knih** vyberte položku kniha.

   Aktuální hodnoty se zobrazí v oddílu **Upravit vybranou knihu** .

1. Upravte hodnoty pomocí klávesnice. Jakmile <xref:System.Windows.Controls.TextBox> ovládací prvek ztratí fokus, změny se automaticky rozšíří do seznamů zdrojů a knih XML.

---
title: Postup přidání úvodní obrazovky
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 39f53e21c40f036c65894b4f275cd5fb414999be
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740448"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a>Postupy: Přidání úvodní obrazovky do aplikace WPF

Toto téma ukazuje, jak přidat spouštěcí okno nebo *úvodní obrazovku*do aplikace Windows Presentation Foundation (WPF).

## <a name="to-add-an-existing-image-as-a-splash-screen"></a>Přidání existujícího obrázku jako úvodní obrazovky

1. Vytvořte nebo najděte obrázek, který chcete použít pro úvodní obrazovku. Můžete použít libovolný formát obrázku, který podporuje součást WIC (Windows Imaging Component). Můžete například použít formát BMP, GIF, JPEG, PNG nebo TIFF.

2. Přidejte soubor obrázku do projektu aplikace WPF.

3. V **Průzkumník řešení**vyberte bitovou kopii.

4. V okno Vlastnosti klikněte na šipku rozevíracího seznamu vlastnosti **Akce sestavení** .

5. V rozevíracím seznamu vyberte **třídy SplashScreen** .

6. Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.

     Obrázek úvodní obrazovky se zobrazí uprostřed obrazovky a po zobrazení okna hlavní aplikace zmizí.

## <a name="to-exclude-the-splash-screen-from-build"></a>Vyloučení úvodní obrazovky ze sestavení

1. V **Průzkumník řešení**vyberte obrázek úvodní obrazovky.

2. V okně **vlastnosti** nastavte **akci sestavení** na **žádná**.

## <a name="to-remove-the-splash-screen-from-an-application"></a>Odebrání úvodní obrazovky z aplikace

V **Průzkumník řešení**odstraňte obrázek úvodní obrazovky.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.SplashScreen>
- [Postupy: Přidání existujících položek do projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))

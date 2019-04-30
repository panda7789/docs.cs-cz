---
title: 'Postupy: Přidání úvodní obrazovky do aplikace WPF'
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 3120ee64d65822d323800a89466c6b707169aaaa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947898"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a>Postupy: Přidání úvodní obrazovky do aplikace WPF

Toto téma ukazuje, jak přidat časové období při spuštění nebo *úvodní obrazovka*, k aplikaci Windows Presentation Foundation (WPF).

## <a name="to-add-an-existing-image-as-a-splash-screen"></a>Chcete-li přidat existující image jako úvodní obrazovka

1. Vytvořit nebo vyhledat bitovou kopii, kterou chcete použít pro úvodní obrazovku. Můžete použít libovolný formát obrázku, který je podporovaný službou Windows Imaging Component (WIC). Například můžete pomocí formátu BMP, GIF, JPEG, PNG nebo ve formátu TIFF.

2. Přidání souboru obrázku do projektu aplikace WPF.

3. V **Průzkumníka řešení**, vyberte bitovou kopii.

4. V okně Vlastnosti klikněte na šipku rozevíracího seznamu pro **akce sestavení** vlastnost.

5. Vyberte **SplashScreen** z rozevíracího seznamu.

6. Stisknutím klávesy **F5** sestavíte a spustíte aplikaci.

     Na úvodní obrazovce je zobrazena ve středu obrazovky a pak sníží (zesvětlí) až se zobrazí hlavního okna aplikace.

## <a name="to-exclude-the-splash-screen-from-build"></a>Na úvodní obrazovce vyloučit ze sestavení

1. V **Průzkumníka řešení**, vyberte obrázek úvodní obrazovky.

2. V **vlastnosti** okno, nastaveno **akce sestavení** k **žádný**.

## <a name="to-remove-the-splash-screen-from-an-application"></a>Chcete-li odebrat úvodní obrazovky z aplikace

V **Průzkumníka řešení**, odstraňte na úvodní obrazovce.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.SplashScreen>
- [Postupy: Přidání existující položky do projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))

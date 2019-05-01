---
title: Vytvoření objektu InkCanvas v aplikaci WPF v sadě Visual Studio
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- XAML [WPF], procedural code in lieu of
- InkCanvas (WPF)
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: d633111c5abc572b0fc27c1a5b32050681504073
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807964"
---
# <a name="get-started-with-ink-in-wpf"></a>Začínáme s inkoustem v subsystému WPF

Windows Presentation Foundation (WPF) obsahuje funkci rukopisu, se kterou snadno začlenit digitálních inkoust do vaší aplikace.

## <a name="prerequisites"></a>Požadavky

Pokud chcete použít v následujících příkladech, nejprve nainstalujte [sady Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019). Pomáhá také vědět, jak zapsat základní aplikace pro WPF. Začínáme s WPF pomoc najdete v tématu [názorný postup: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).

## <a name="quick-start"></a>Rychlý Start

Tato část vám pomůže psát jednoduché aplikace WPF, která shromažďuje rukopisu.

### <a name="got-ink"></a>Máte inkoustu?

Vytvoření aplikace WPF, která podporuje rukopisu:

1. Otevřít Visual Studio.

2. Vytvořte nový **aplikace WPF**.

   V **nový projekt** dialogového okna, rozbalte **nainstalováno** > **Visual C#** nebo **jazyka Visual Basic**  >   **Windows Desktop** kategorie. Vyberte **aplikace WPF (.NET Framework)** šablony aplikace. Zadejte název a potom vyberte **OK**.

   Visual Studio vytvoří projekt, a *souboru MainWindow.xaml* otevře v návrháři.

3. Typ `<InkCanvas/>` mezi `<Grid>` značky.

   ![Návrhář XAML s inkcanvas – značka](./media/getting-started-with-ink/inkcanvas-xaml.png)

4. Stisknutím klávesy **F5** ke spuštění aplikace v ladicím programu.

5. Pomocí pera nebo myš, zápis **hello world** v okně.

Jste napsali ekvivalent inkoustu aplikace "hello world" pomocí pouze 12 stisknutí kláves!

### <a name="spice-up-your-app"></a>Okořeňte kapacity aplikace

Můžeme využít některé funkce WPF. Nahradit vše, co mezi otevírací a zavírací \<okna > značky následujícím kódem:

```xaml
<Page>
  <InkCanvas Name="myInkCanvas" MouseRightButtonUp="RightMouseUpHandler">
    <InkCanvas.Background>
      <LinearGradientBrush>
        <GradientStop Color="Yellow" Offset="0.0" />
          <GradientStop Color="Blue" Offset="0.5" />
            <GradientStop Color="HotPink" Offset="1.0" />
              </LinearGradientBrush>
    </InkCanvas.Background>
  </InkCanvas>
</Page>
```

Tento XAML vytvoří štětce přechodu pozadí na pera surface.

![Barvy přechodu na rukopis plochu v aplikaci WPF](./media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a>Přidat některé kódu na pozadí XAML

Zatímco XAML velmi usnadňuje návrh uživatelského rozhraní, žádné reálné aplikaci je potřeba přidat kód pro zpracování událostí. Tady je jednoduchý příklad, který se přiblíží rukopisu v reakci klikněte pravým tlačítkem myši.

1. Nastavte `MouseRightButtonUp` obslužné rutiny ve vaší XAML:

   [!code-xaml[DigitalInkTopics#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. V **Průzkumníka řešení**, rozbalte soubor MainWindow.xaml a otevřete soubor kódu na pozadí (MainWindow.xaml.cs nebo soubor MainWindow.xaml.vb). Přidejte následující kód obslužné rutiny události:

   [!code-csharp[DigitalInkTopics#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. Spusťte aplikaci. Přidat nějaký inkoust a potom klikněte pravým tlačítkem myši nebo provést ekvivalent stiskněte a podržte pomocí pera.

   Zobrazení přiblíží pokaždé, když klepnete pravým tlačítkem myši.

### <a name="use-procedural-code-instead-of-xaml"></a>Použít kód procedury namísto XAML

Všechny funkce WPF můžete přistupovat z kódu procedury. Postupujte podle těchto kroků můžete vytvořit "inkoustu aplikace Hello World" pro WPF, která nebude vůbec používat jakékoli XAML.

1. Vytvořte nový projekt konzolové aplikace v sadě Visual Studio.

   V **nový projekt** dialogového okna, rozbalte **nainstalováno** > **Visual C#** nebo **jazyka Visual Basic**  >   **Windows Desktop** kategorie. Vyberte **Konzolová aplikace (.NET Framework)** šablony aplikace. Zadejte název a potom vyberte **OK**.

1. Vložte následující kód do souboru Program.cs nebo soubor Program.vb:

   [!code-csharp[InkCanvasConsoleApp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. Přidat odkazy na sestavení PresentationCore PresentationFramework a WindowsBase kliknutím pravým tlačítkem na **odkazy** v **Průzkumníka řešení** a zvolíte **přidat odkaz**.

   ![Zobrazuje PresentationCore a PresentationFramework správce odkazů](./media/getting-started-with-ink/reference-manager-presentationcore-presentationframework.png)

1. Sestavte aplikaci stisknutím klávesy **F5**.

## <a name="see-also"></a>Viz také:

- [Rukopis](digital-ink.md)
- [Shromáždění rukopisu](collecting-ink.md)
- [Rozpoznávání textu psaného rukou](handwriting-recognition.md)
- [Uložení rukopisu](storing-ink.md)

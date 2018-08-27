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
ms.openlocfilehash: 600d8528125606c6e1af5b031e2fc31aabb79206
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925041"
---
# <a name="get-started-with-ink-in-wpf"></a>Začínáme s inkoustem v subsystému WPF

Windows Presentation Foundation (WPF) obsahuje funkci rukopisu, se kterou snadno začlenit digitálních inkoust do vaší aplikace.

## <a name="prerequisites"></a>Požadavky

Chcete-li nejprve použít následující příklady, [instalaci sady Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017). Pomáhá také vědět, jak zapsat základní aplikace pro WPF. Začínáme s WPF pomoc najdete v tématu [návod: Moje první desktopová aplikace WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).

## <a name="quick-start"></a>Rychlý Start

Tato část vám pomůže psát jednoduché aplikace WPF, která shromažďuje rukopisu.

### <a name="got-ink"></a>Máte inkoustu?

Vytvoření aplikace WPF, která podporuje rukopisu:

1. Otevřít Visual Studio.

2. Vytvořte nový **aplikace WPF**.

   V **nový projekt** dialogového okna, rozbalte **nainstalováno** > **Visual C#** nebo **jazyka Visual Basic**  >   **Windows Desktop** kategorie. Vyberte **aplikace WPF (.NET Framework)** šablony aplikace. Zadejte název a potom vyberte **OK**.

   Visual Studio vytvoří projekt, a *souboru MainWindow.xaml* otevře v návrháři.

3. Typ `<InkCanvas/>` mezi `<Grid>` značky.

   ![Návrhář XAML s inkcanvas – značka](media/getting-started-with-ink/inkcanvas-xaml.png)

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

![Barvy přechodu na rukopis plochu v aplikaci WPF](media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a>Přidat některé kódu na pozadí XAML

Zatímco XAML velmi usnadňuje návrh uživatelského rozhraní, žádné reálné aplikaci je potřeba přidat kód pro zpracování událostí. Tady je jednoduchý příklad, který se přiblíží rukopisu v reakci klikněte pravým tlačítkem myši.

1. Nastavte `MouseRightButtonUp` obslužné rutiny ve vaší XAML:

   [!code-xaml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. V **Průzkumníka řešení**, rozbalte soubor MainWindow.xaml a otevřete soubor kódu na pozadí (MainWindow.xaml.cs nebo soubor MainWindow.xaml.vb). Přidejte následující kód obslužné rutiny události:

   [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. Spusťte aplikaci. Přidat nějaký inkoust a potom klikněte pravým tlačítkem myši nebo provést ekvivalent stiskněte a podržte pomocí pera.

   Zobrazení přiblíží pokaždé, když klepnete pravým tlačítkem myši.

### <a name="use-procedural-code-instead-of-xaml"></a>Použít kód procedury namísto XAML

Všechny funkce WPF můžete přistupovat z kódu procedury. Postupujte podle těchto kroků můžete vytvořit "inkoustu aplikace Hello World" pro WPF, která nebude vůbec používat jakékoli XAML.

1. Vytvořte nový projekt konzolové aplikace v sadě Visual Studio.

   V **nový projekt** dialogového okna, rozbalte **nainstalováno** > **Visual C#** nebo **jazyka Visual Basic**  >   **Windows Desktop** kategorie. Vyberte **Konzolová aplikace (.NET Framework)** šablony aplikace. Zadejte název a potom vyberte **OK**.

1. Vložte následující kód do souboru Program.cs nebo soubor Program.vb:

   [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. Přidat odkazy na sestavení PresentationCore PresentationFramework a WindowsBase kliknutím pravým tlačítkem na **odkazy** v **Průzkumníka řešení** a zvolíte **přidat odkaz**.

   ![Zobrazuje PresentationCore a PresentationFramework správce odkazů](media/getting-started-with-ink/references.png)

1. Sestavte aplikaci stisknutím klávesy **F5**.

## <a name="see-also"></a>Viz také

- [Rukopis](../../../../docs/framework/wpf/advanced/digital-ink.md)
- [Shromáždění rukopisu](../../../../docs/framework/wpf/advanced/collecting-ink.md)
- [Rozpoznávání textu psaného rukou](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)
- [Uložení rukopisu](../../../../docs/framework/wpf/advanced/storing-ink.md)

---
title: Vytvoření InkCanvas v aplikaci WPF v aplikaci Visual Studio
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- XAML [WPF], procedural code in lieu of
- InkCanvas (WPF)
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: ebbf25037921e7802b2bfcb6ffa562d16a849ffa
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920254"
---
# <a name="get-started-with-ink-in-wpf"></a>Začínáme s rukopisem v subsystému WPF

Windows Presentation Foundation (WPF) má funkci rukopisu, která usnadňuje začleňování digitálního inkoustu do vaší aplikace.

## <a name="prerequisites"></a>Požadavky

Chcete-li použít následující příklady, nejprve nainstalujte [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019). Pomáhá také zjistit, jak psát základní aplikace WPF. Nápovědu Začínáme s WPF naleznete v tématu [Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).

## <a name="quick-start"></a>rychlé zprovoznění

Tato část vám pomůže napsat jednoduchou aplikaci WPF, která shromažďuje rukopis.

### <a name="got-ink"></a>Máte inkoust?

Vytvoření aplikace WPF podporující rukopis:

1. Otevřete Visual Studio.

2. Vytvořte novou **aplikaci WPF**.

   V dialogovém okně **Nový projekt** rozbalte kategorii **nainstalované** > **Visual C#**  nebo **Visual Basic** > **Windows Desktop** . Pak vyberte šablonu aplikace **WPF App (.NET Framework)** . Zadejte název a pak vyberte **OK**.

   Visual Studio vytvoří projekt a v návrháři se otevře *MainWindow. XAML* .

3. Zadejte `<InkCanvas/>` mezi značkami `<Grid>`.

   ![Návrhář XAML se značkou InkCanvas](./media/getting-started-with-ink/inkcanvas-xaml.png)

4. Stisknutím klávesy **F5** spusťte aplikaci v ladicím programu.

5. Pomocí pera nebo myši napište do okna **Hello World** .

Napsali jste ekvivalent inkoustu aplikace "Hello World" s pouze 12 klávesami.

### <a name="spice-up-your-app"></a>Spice své aplikace

Pojďme využít některé funkce WPF. Nahraďte vše mezi otevíracím a zavíracím \<oknem > značky následujícím kódem:

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

Tento kód XAML vytvoří pozadí barevného štětce na ploše pro rukopis.

![Barvy přechodu na rukopisné ploše v aplikaci WPF](./media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a>Přidat kód za XAML

Zatímco XAML usnadňuje návrh uživatelského rozhraní, všechny reálné aplikace musí přidat kód pro zpracování událostí. Tady je jednoduchý příklad, který se přiblíží inkoustu v reakci na pravé tlačítko myši.

1. Nastavte obslužnou rutinu `MouseRightButtonUp` ve vašem kódu XAML:

   [!code-xaml[DigitalInkTopics#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. V **Průzkumník řešení**rozbalte MainWindow. XAML a otevřete soubor kódu na pozadí (MainWindow.XAML.cs nebo MainWindow. XAML. vb). Přidejte následující kód obslužné rutiny události:

   [!code-csharp[DigitalInkTopics#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. Spusťte aplikaci. Přidejte nějaký rukopis, klikněte na něj pravým tlačítkem myši nebo proveďte ekvivalent stisknutí klávesy stylus a podržením stylusu.

   Zobrazení se přiblíží pokaždé, když kliknete pravým tlačítkem myši.

### <a name="use-procedural-code-instead-of-xaml"></a>Použití procedurálního kódu místo XAML

Ke všem funkcím WPF můžete přistupovat z procedurálního kódu. Pomocí těchto kroků můžete vytvořit aplikaci Hello World Ink World pro WPF, která vůbec nepoužívá žádný XAML.

1. Vytvořte nový projekt konzolové aplikace v aplikaci Visual Studio.

   V dialogovém okně **Nový projekt** rozbalte kategorii **nainstalované** > **Visual C#**  nebo **Visual Basic** > **Windows Desktop** . Pak vyberte šablonu aplikace **Konzolová aplikace (.NET Framework)** . Zadejte název a pak vyberte **OK**.

1. Vložte následující kód do souboru Program.cs nebo program. vb:

   [!code-csharp[InkCanvasConsoleApp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. Přidejte odkazy na PresentationCore, PresentationFramework a WindowsBase sestavení tak, že kliknete pravým tlačítkem na **odkazy** v **Průzkumník řešení** a zvolíte **Přidat odkaz**.

   ![Správce odkazů zobrazující PresentationCore a PresentationFramework](./media/getting-started-with-ink/reference-manager-presentationcore-presentationframework.png)

1. Sestavte aplikaci stisknutím klávesy **F5**.

## <a name="see-also"></a>Viz také:

- [Rukopis](digital-ink.md)
- [Shromáždění rukopisu](collecting-ink.md)
- [Rozpoznávání textu psaného rukou](handwriting-recognition.md)
- [Uložení rukopisu](storing-ink.md)

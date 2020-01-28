---
title: Vytváření přístupových klíčů pro ovládací prvky
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4faa0991-28ec-4eca-91db-51dc2cd6a7ac
ms.openlocfilehash: 7f6b0a5838cacfc1189fba819a54b3423d567ea0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731169"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a>Postupy: vytváření přístupových klíčů pro model Windows Forms ovládací prvky

*Přístupový klíč* je podtržený znak v textu nabídky, položky nabídky nebo popisku ovládacího prvku, jako je tlačítko. V případě přístupového klíče může uživatel "kliknout" tlačítko stisknutím klávesy ALT v kombinaci s předdefinovaným přístupovým klíčem. Například Pokud tlačítko spustí proceduru pro tisk formuláře, a proto je jeho vlastnost `Text` nastavena na "Tisk", přidání ampersandu před písmeno "P" způsobí, že písmeno "P" bude v textu tlačítka v době běhu podtrženo. Uživatel může spustit příkaz přidružený k tlačítku stisknutím kombinace kláves ALT + P.

Ovládací prvky, které nemůžou získat fokus, nemůžou mít přístupové klíče.

## <a name="programmatic"></a>Blokují

Nastavte vlastnost `Text` na řetězec, který obsahuje ampersand (&) před písmenem, které bude zástupcem.

```vb
' Set the letter "P" as an access key.
Button1.Text = "&Print"
```

```csharp
// Set the letter "P" as an access key.
button1.Text = "&Print";
```

```cpp
// Set the letter "P" as an access key.
button1->Text = "&Print";
```

> [!NOTE]
> Chcete-li v titulku použít ampersand bez vytvoření přístupového klíče, přidejte dva ampersandy (& &). V titulku se zobrazí jeden ampersand a žádné znaky nejsou podtržené.

## <a name="designer"></a>Návrhář

V okně **vlastnosti** sady Visual Studio nastavte vlastnost **text** na řetězec, který obsahuje ampersand (' & ') před písmenem, které bude přístupový klíč. Chcete-li například nastavit písmeno "P" jako přístupový klíč, zadejte **& tisk**.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Button>
- [Postupy: Reakce na kliknutí na tlačítko Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)

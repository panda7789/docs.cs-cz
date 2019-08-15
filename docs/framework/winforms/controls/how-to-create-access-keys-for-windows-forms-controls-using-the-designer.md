---
title: 'Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
ms.openlocfilehash: 01bed04483702ba2e62162b675aa1138bc1b0e01
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039524"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a>Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms pomocí Návrháře
*Přístupový klíč* je podtržený znak v textu nabídky, položky nabídky nebo popisku ovládacího prvku, jako je tlačítko. Umožňuje uživateli "kliknout na tlačítko" stisknutím klávesy ALT v kombinaci s předdefinovaným přístupovým klíčem. Například Pokud tlačítko spustí proceduru pro tisk formuláře, a proto je jeho `Text` vlastnost nastavena na "Tisk", přidání ampersandu (&) před písmenem "p" způsobí, že písmeno "p" bude v textu tlačítka v době běhu podtrženo. Uživatel může spustit příkaz přidružený k tlačítku stisknutím kombinace kláves ALT + P. Nemůžete mít přístupový klíč pro ovládací prvek, který nemůže získat fokus.

## <a name="to-create-an-access-key-for-a-control"></a>Vytvoření přístupového klíče pro ovládací prvek

1. V okně **vlastnosti** nastavte `Text` vlastnost na řetězec, který obsahuje ampersand (&) před písmenem, který bude přístupovým klíčem. Chcete-li například nastavit písmeno "P" jako přístupový klíč, zadejte **& tisk** do mřížky.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Button>
- [Postupy: Reakce na model Windows Forms kliknutí na tlačítko](how-to-respond-to-windows-forms-button-clicks.md)
- [Postupy: Nastavení textu zobrazovaného ovládacím prvkem model Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)

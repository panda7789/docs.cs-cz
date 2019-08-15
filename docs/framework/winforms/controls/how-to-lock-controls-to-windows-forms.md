---
title: 'Postupy: Uzamykání ovládacích prvků ve Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: cbf82f1481ee9779cec5cfbf3fb057b7ea399a1c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039907"
---
# <a name="how-to-lock-controls-to-windows-forms"></a>Postupy: Uzamykání ovládacích prvků ve Windows Forms
Při návrhu uživatelského rozhraní (UI) aplikace systému Windows můžete ovládací prvky uzamknout, jakmile jsou umístěny správně, takže při nastavování dalších vlastností je neúmyslně přesunovat ani měnit jejich velikost.

 Kromě toho můžete uzamknout a odemknout všechny ovládací prvky ve formuláři najednou, což je užitečné pro formuláře s mnoha ovládacími prvky, nebo můžete odemknout jednotlivé ovládací prvky. Po umístění všech ovládacích prvků tam, kde je chcete umístit do formuláře, je všechny zablokované, aby nedocházelo k chybnému přesunu.

## <a name="to-lock-a-control"></a>Uzamčení ovládacího prvku

1. V okně **vlastnosti** klikněte na vlastnost **Uzamčeno** a vyberte `true`. (Dvojitým kliknutím na název přepínáte nastavení vlastnosti.)

     Případně klikněte pravým tlačítkem myši na ovládací prvek a vyberte **Zamknout ovládací prvky**.

    > [!NOTE]
    >  Blokovací ovládací prvky zabraňují jejich přetažení na novou velikost nebo umístění na návrhové ploše. Můžete však i nadále měnit velikost nebo umístění ovládacích prvků pomocí okna **vlastnosti** nebo v kódu.

## <a name="to-lock-all-the-controls-on-a-form"></a>Uzamčení všech ovládacích prvků ve formuláři

1. V nabídce **Formát** vyberte možnost **Zamknout ovládací prvky**.

    > [!NOTE]
    >  Tento příkaz zamkne i velikost formuláře, protože formulář je ovládací prvek.

## <a name="to-unlock-all-locked-controls-on-a-form"></a>Odemčení všech uzamčených ovládacích prvků na formuláři

1. V nabídce **Formát** vyberte možnost **Zamknout ovládací prvky**.

     Všechny dříve uzamčené ovládací prvky ve formuláři jsou nyní odemčeny.

## <a name="to-unlock-locked-controls-individually"></a>Chcete-li odemknout uzamčené ovládací prvky individuálně

1. V okně **vlastnosti** klikněte na vlastnost **Uzamčeno** a vyberte `false`. (Dvojitým kliknutím na název přepínáte nastavení vlastnosti.)

## <a name="see-also"></a>Viz také:

- [Windows Forms – ovládací prvky](index.md)
- [Uspořádávání ovládacích prvků ve Windows Forms](arranging-controls-on-windows-forms.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Ovládací prvky Windows Forms podle funkce](windows-forms-controls-by-function.md)

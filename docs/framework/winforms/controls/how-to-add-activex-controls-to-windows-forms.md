---
title: 'Postupy: Přidávání ovládacích prvků ActiveX do Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 8c4c6c3f96c49401b032e360314794cc800c0551
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987060"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>Postupy: Přidávání ovládacích prvků ActiveX do Windows Forms

I když je Návrhář formulářů v aplikaci Visual Studio optimalizováno pro hostování model Windows Formsch ovládacích prvků, můžete také umístit ovládací prvky ActiveX na model Windows Forms.

> [!CAUTION]
> Existují omezení výkonu pro model Windows Forms, když jsou do nich přidány ovládací prvky ActiveX.

Než přidáte ovládací prvky ActiveX do formuláře, je nutné je přidat do panelu nástrojů. Další informace naleznete v tématu [komponenty modelu COM, dialogové okno přizpůsobení sady nástrojů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).

## <a name="add-an-activex-control-to-your-windows-form"></a>Přidání ovládacího prvku ActiveX do formuláře Windows

Chcete-li přidat ovládací prvek ActiveX do formuláře Windows, dvakrát klikněte na ovládací prvek na panelu nástrojů.

Visual Studio přidá všechny odkazy na ovládací prvek v projektu. Další informace o akcích, které je potřeba vzít v úvahu při používání ovládacích prvků ActiveX na model Windows Forms, najdete v tématu [aspekty hostování ovládacího prvku ActiveX ve formuláři Windows](considerations-when-hosting-an-activex-control-on-a-windows-form.md).

> [!NOTE]
> Nástroj pro import ovládacího prvku ActiveX (AxImp. exe) vytvoří argumenty události jiného typu, než model Windows Forms se čekalo při dovozu dynamických knihoven ActiveX. Argumenty vytvořené pomocí AxImp. exe jsou podobné následujícímu: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, když `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` je očekáváno. Mějte na paměti, že tato nepravidelnost nebrání v normálním fungování kódu. Podrobnosti najdete v tématu [model Windows Forms Importéru ovládacího prvku ActiveX (Aximp. exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).

## <a name="see-also"></a>Viz také:

- [Windows Forms – ovládací prvky](index.md)
- [Ovládací prvky a programovatelné objekty v porovnání s různými jazyky a knihovnami](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [Postupy: Přidat ovládací prvky do model Windows Forms](how-to-add-controls-to-windows-forms.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Ovládací prvky Windows Forms podle funkce](windows-forms-controls-by-function.md)

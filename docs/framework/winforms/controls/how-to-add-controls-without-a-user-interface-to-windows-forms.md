---
title: Přidání ovládacích prvků bez uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
ms.openlocfilehash: 43f13b4f009fcd6e5d82fa2c00113a77d48877b6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744754"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a>Postupy: Přidávání ovládacích prvků bez uživatelského rozhraní do formulářů Windows

Nevizuální ovládací prvek (nebo komponenta) poskytuje vaší aplikaci funkce. Na rozdíl od jiných ovládacích prvků komponenty neposkytují uživatelské rozhraní uživateli, a proto nemusí být zobrazeny na Návrhář formulářů ploše. Když je do formuláře přidána součást, Návrhář formulářů zobrazí v dolní části formuláře, kde jsou zobrazeny všechny komponenty, zásobník s možností změny velikosti. Po přidání ovládacího prvku do zásobníku komponenty můžete vybrat komponentu a nastavit její vlastnosti stejným způsobem jako jakýkoli jiný ovládací prvek ve formuláři.

## <a name="add-a-component-to-a-windows-form"></a>Přidání komponenty do formuláře Windows

1. Otevřete formulář v aplikaci Visual Studio. Podrobnosti naleznete v tématu [How to: Display model Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).

2. V sadě **nástrojů**klikněte na součást a přetáhněte ji do formuláře.

     Vaše komponenta se zobrazí v zásobníku součásti.

Kromě toho je možné přidat komponenty do formuláře za běhu. Toto je běžný scénář, zejména protože komponenty nemají vizuální výraz, na rozdíl od ovládacích prvků, které mají uživatelské rozhraní. V následujícím příkladu je přidána komponenta <xref:System.Windows.Forms.Timer> v době běhu. (Všimněte si, že Visual Studio obsahuje několik různých časovačů. v takovém případě použijte komponentu model Windows Forms <xref:System.Windows.Forms.Timer>. Další informace o různých časovačích v aplikaci Visual Studio naleznete v tématu [Úvod do časovačů na serveru](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)

> [!CAUTION]
> Komponenty mají často vlastnosti specifické pro ovládací prvky, které je třeba nastavit, aby součást fungovala efektivně. V případě <xref:System.Windows.Forms.Timer> komponenty níže nastavte vlastnost `Interval`. Ujistěte se, že při přidávání součástí do projektu jste nastavili vlastnosti nezbytné pro danou součást.

## <a name="add-a-component-to-a-windows-form-programmatically"></a>Programové přidání komponenty do formuláře Windows

1. Vytvoří instanci třídy <xref:System.Windows.Forms.Timer> v kódu.

2. Nastavením vlastnosti `Interval` určíte dobu mezi takty časovače.

3. Nakonfigurujte všechny další nezbytné vlastnosti pro komponentu.

     Následující kód ukazuje vytvoření <xref:System.Windows.Forms.Timer> s nastavenou vlastností `Interval`.

    ```vb
    Public Sub CreateTimer()
       Dim timerKeepTrack As New System.Windows.Forms.Timer
       timerKeepTrack.Interval = 1000
    End Sub
    ```

    ```csharp
    public void createTimer()
    {
       System.Windows.Forms.Timer timerKeepTrack = new
           System.Windows.Forms.Timer();
       timerKeepTrack.Interval = 1000;
    }
    ```

    ```cpp
    public:
       void createTimer()
       {
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew
             System::Windows::Forms::Timer();
          timerKeepTrack->Interval = 1000;
       }
    ```

    > [!IMPORTANT]
    > Místní počítač můžete vystavit bezpečnostnímu riziku prostřednictvím sítě odkazem na škodlivý prvek UserControl. To by mělo být obavy jenom v případě, že by škodlivá osoba vytvořila škodlivý vlastní ovládací prvek, a pak ji nepřidali do projektu omylem.

## <a name="see-also"></a>Viz také

- [Windows Forms – ovládací prvky](index.md)
- [Postupy: Přidávání ovládacích prvků do Windows Forms](how-to-add-controls-to-windows-forms.md)
- [Postupy: Přidávání ovládacích prvků ActiveX do Windows Forms](how-to-add-activex-controls-to-windows-forms.md)
- [Vkládání ovládacích prvků do Windows Forms](putting-controls-on-windows-forms.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Ovládací prvky Windows Forms podle funkce](windows-forms-controls-by-function.md)

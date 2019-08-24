---
title: 'Postupy: Přidávání ovládacích prvků bez uživatelského rozhraní do Windows Forms'
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
ms.openlocfilehash: bc1f844e5a2cf4d4f3b64ebf20e935f36ff85e12
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987090"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a>Postupy: Přidávání ovládacích prvků bez uživatelského rozhraní do Windows Forms

Nevizuální ovládací prvek (nebo komponenta) poskytuje vaší aplikaci funkce. Na rozdíl od jiných ovládacích prvků komponenty neposkytují uživatelské rozhraní uživateli, a proto nemusí být zobrazeny na Návrhář formulářů ploše. Když je do formuláře přidána součást, Návrhář formulářů zobrazí v dolní části formuláře, kde jsou zobrazeny všechny komponenty, zásobník s možností změny velikosti. Po přidání ovládacího prvku do zásobníku komponenty můžete vybrat komponentu a nastavit její vlastnosti stejným způsobem jako jakýkoli jiný ovládací prvek ve formuláři.

## <a name="add-a-component-to-a-windows-form"></a>Přidání komponenty do formuláře Windows

1. Otevřete formulář v aplikaci Visual Studio. Podrobnosti najdete v tématu [How to: Zobrazit model Windows Forms v Návrháři](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))

2. V sadě **nástrojů**klikněte na součást a přetáhněte ji do formuláře.

     Vaše komponenta se zobrazí v zásobníku součásti.

Kromě toho je možné přidat komponenty do formuláře za běhu. Toto je běžný scénář, zejména protože komponenty nemají vizuální výraz, na rozdíl od ovládacích prvků, které mají uživatelské rozhraní. V následujícím <xref:System.Windows.Forms.Timer> příkladu je přidána komponenta v době běhu. (Všimněte si, že Visual Studio obsahuje několik různých časovačů. v takovém případě použijte model Windows Forms <xref:System.Windows.Forms.Timer> komponentu. Další informace o různých časovačích v aplikaci Visual Studio naleznete v tématu [Úvod do časovačů na serveru](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)

> [!CAUTION]
> Komponenty mají často vlastnosti specifické pro ovládací prvky, které je třeba nastavit, aby součást fungovala efektivně. V případě <xref:System.Windows.Forms.Timer> komponenty níže `Interval` nastavte vlastnost. Ujistěte se, že při přidávání součástí do projektu jste nastavili vlastnosti nezbytné pro danou součást.

## <a name="add-a-component-to-a-windows-form-programmatically"></a>Programové přidání komponenty do formuláře Windows

1. Vytvoří instanci <xref:System.Windows.Forms.Timer> třídy v kódu.

2. `Interval` Nastavte vlastnost tak, aby určovala dobu mezi takty časovače.

3. Nakonfigurujte všechny další nezbytné vlastnosti pro komponentu.

     Následující kód ukazuje vytvoření a <xref:System.Windows.Forms.Timer> `Interval` s nastavenou vlastností.

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

## <a name="see-also"></a>Viz také:

- [Windows Forms – ovládací prvky](index.md)
- [Postupy: Přidat ovládací prvky do model Windows Forms](how-to-add-controls-to-windows-forms.md)
- [Postupy: Přidat ovládací prvky ActiveX do model Windows Forms](how-to-add-activex-controls-to-windows-forms.md)
- [Vkládání ovládacích prvků do Windows Forms](putting-controls-on-windows-forms.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Ovládací prvky Windows Forms podle funkce](windows-forms-controls-by-function.md)

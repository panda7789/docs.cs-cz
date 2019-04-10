---
title: 'Postupy: Vytváření nadřazených formulářů MDI'
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
ms.openlocfilehash: 120a7d45e01b0460f0c5e50896f58d026c4c3b9f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216311"
---
# <a name="how-to-create-mdi-parent-forms"></a>Postupy: Vytváření nadřazených formulářů MDI
> [!IMPORTANT]
>  Toto téma používá <xref:System.Windows.Forms.MainMenu> ovládací prvek, který byl nahrazen <xref:System.Windows.Forms.MenuStrip> ovládacího prvku. <xref:System.Windows.Forms.MainMenu> Ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.  Informace o vytváření MDI nadřazený formulář s využitím <xref:System.Windows.Forms.MenuStrip>, naleznete v tématu [jak: Vytvoření seznamu okna MDI pomocí MenuStrip](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).  
  
 Základ pro aplikace rozhraní více dokumentů (MDI) je nadřazený formulář MDI. Toto je formulář, který obsahuje podřízených oken MDI, které jsou dílčí windows, ve kterém uživatel pracuje v aplikaci MDI. Vytvoření nadřazený formulář MDI je jednoduché, v Návrháři formulářů Windows a prostřednictvím kódu programu.  
  
### <a name="to-create-an-mdi-parent-form-at-design-time"></a>Chcete-li vytvořit nadřazený formulář MDI v době návrhu  
  
1.  Vytvoření projektu aplikace Windows.  
  
2.  V **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost **true**.  
  
     Ta určuje formuláře jako kontejnerem MDI pro podřízená okna.  
  
    > [!NOTE]
    >  Při nastavování vlastností **vlastnosti** okna, můžete také nastavit `WindowState` vlastnost **Maximized**, pokud chcete, můžete, protože je nejjednodušší k manipulaci s podřízených oken MDI, pokud je nadřazený formulář maximalizované. Kromě toho mějte na paměti, že okraj nadřazený formulář MDI vyzvedne, až bude systémovou barvou (nastavení v Ovládacích panelech systému Windows), nikoli barva pozadí nastavíte pomocí <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> vlastnost.  
  
3.  Z **nástrojů**, přetáhněte **MenuStrip** ovládacího prvku na formuláři. Vytvoření položky nabídek nejvyšší úrovně s **Text** vlastnost nastavena na hodnotu **& soubor** s názvem položky podnabídky **& Nový** a **Zavřít**. Také vytvořit nabídek nejvyšší úrovně položky volá **& okno**.  
  
     Vytvoří a skrytí položek nabídky v době běhu nabídce první a druhé nabídky bude sledovat, otevřete podřízených oken MDI. V tomto okamžiku jste vytvořili nadřazeného okna MDI.  
  
4.  Stisknutím klávesy **F5** ke spuštění aplikace. Informace o vytváření podřízeného MDI windows, které působí v rámci nadřazený formulář MDI, naleznete v tématu [jak: Vytváření podřízených formulářů MDI](how-to-create-mdi-child-forms.md).  
  
## <a name="see-also"></a>Viz také:

- [Aplikace MDI (Multiple-Document Interface)](multiple-document-interface-mdi-applications.md)
- [Postupy: Vytváření podřízených formulářů MDI](how-to-create-mdi-child-forms.md)
- [Postupy: Určení aktivního podřízeného formuláře MDI](how-to-determine-the-active-mdi-child.md)
- [Postupy: Odesílání dat do aktivního podřízeného formuláře MDI](how-to-send-data-to-the-active-mdi-child.md)
- [Postupy: Uspořádání podřízených formulářů MDI](how-to-arrange-mdi-child-forms.md)

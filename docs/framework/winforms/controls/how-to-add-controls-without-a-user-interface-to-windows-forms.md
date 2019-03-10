---
title: 'Postupy: Přidání ovládacích prvků bez uživatelského rozhraní do formulářů Windows'
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
ms.openlocfilehash: 4d99f56710fa1d879aed5000edb5424a0727ae3c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703623"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a>Postupy: Přidání ovládacích prvků bez uživatelského rozhraní do formulářů Windows
Nevizuální ovládací prvek (nebo komponenta) poskytuje funkce, které vaše aplikace. Na rozdíl od jiných ovládacích prvků součástí neposkytují uživatelského rozhraní pro uživatele a proto není potřeba zobrazovat na plochu návrháře formulářů Windows. Při přidání komponenty do formuláře, zobrazí Návrhář formulářů Windows umožňující změnu velikosti na hlavním panelu v dolní části formuláře, ve kterém jsou zobrazeny všechny součásti. Jakmile ovládací prvek byl přidán do panelu komponent, můžete vybrat komponentu a nastavit jeho vlastnosti, stejně jako jakýkoli jiný ovládací prvek na formuláři.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-a-component-to-a-windows-form"></a>K přidání komponenty do formuláře Windows  
  
1.  Otevřete formulář. Podrobnosti najdete v tématu [jak: Zobrazení formulářů Windows v návrháři](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).  
  
2.  V **nástrojů**, klikněte na komponentu a přetáhněte ji do svého formuláře.  
  
     V panelu komponent se zobrazí vaše komponenta.  
  
 Kromě toho můžete přidávat součásti do formuláře v době běhu. Totiž běžný scénář, zejména komponenty nemají visual výrazu, na rozdíl od ovládacích prvků, které mají uživatelské rozhraní. V následujícím příkladu <xref:System.Windows.Forms.Timer> přidání komponenty v době běhu. (Všimněte si, že Visual Studio obsahuje několik různých časovače; v takovém případě použijte prvku Windows Forms <xref:System.Windows.Forms.Timer> komponenty. Další informace o různých časovače v sadě Visual Studio najdete v tématu [Úvod do serverových časovače](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)  
  
> [!CAUTION]
>  Součásti mají často vlastnosti specifické pro ovládací prvek, které musí být nastavena pro komponentu funkce efektivně. V případě třídy <xref:System.Windows.Forms.Timer> součásti, můžete nastavit `Interval` vlastnost. Ujistěte se, při přidávání součástí do projektu, nastavit vlastnosti pro tuto součást.  
  
#### <a name="to-add-a-component-to-a-windows-form-programmatically"></a>K přidání komponenty do formuláře Windows prostřednictvím kódu programu  
  
1.  Vytvoření instance <xref:System.Windows.Forms.Timer> třídu v kódu.  
  
2.  Nastavte `Interval` a určí čas mezi značkami časovače.  
  
3.  Nakonfigurujte další nezbytné vlastnosti pro komponentu.  
  
     Následující kód ukazuje vytvoření objektu <xref:System.Windows.Forms.Timer> s jeho `Interval` sadu vlastností.  
  
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
    >  Pomocí odkazu na škodlivý uživatelský ovládací prvek může zveřejnit místního počítače k ohrožení zabezpečení prostřednictvím sítě. To může být pouze v případě nežádoucí osoba vytváření škodlivé vlastního ovládacího prvku, za nímž následuje omylem přidání do projektu žádný problém.  
  
## <a name="see-also"></a>Viz také:
- [Windows Forms – ovládací prvky](index.md)
- [Postupy: Přidání ovládacích prvků do formulářů Windows](how-to-add-controls-to-windows-forms.md)
- [Postupy: Přidávání ovládacích prvků ActiveX do formulářů Windows](how-to-add-activex-controls-to-windows-forms.md)
- [Postupy: Kopírování ovládacích prvků mezi formuláři Windows](how-to-copy-controls-between-windows-forms.md)
- [Vkládání ovládacích prvků do Windows Forms](putting-controls-on-windows-forms.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Ovládací prvky Windows Forms podle funkce](windows-forms-controls-by-function.md)

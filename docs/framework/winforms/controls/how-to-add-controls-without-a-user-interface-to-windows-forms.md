---
title: 'Postupy: Přidávání ovládacích prvků bez uživatelského rozhraní do formulářů Windows'
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
ms.openlocfilehash: 0a3e9ab5a048e085b192ffc0eb796caae1e58efe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529469"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a>Postupy: Přidávání ovládacích prvků bez uživatelského rozhraní do formulářů Windows
Nevizuální ovládací prvek (nebo součást) poskytuje funkce, které vaše aplikace. Na rozdíl od jiných ovládacích prvků součástí neposkytují uživatelské rozhraní pro uživatele a proto není nutné zobrazit na povrchu Návrhář formulářů Windows. Když součást je přidán do formuláře, zobrazí Návrhář formulářů Windows s možností změny velikosti panelu v dolní části formuláře, kde jsou zobrazeny všechny součásti. Po přidání ovládacího prvku do komponent, můžete vybrat součásti a nastavit jeho vlastnosti, stejně jako další ovládací prvek na formuláři.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-a-component-to-a-windows-form"></a>Chcete-li přidat součást na formuláři Windows  
  
1.  Otevřete formulář. Podrobnosti najdete v tématu [postupy: zobrazení Windows Forms v návrháři](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).  
  
2.  V **sada nástrojů**, klikněte na komponentu a přetáhněte ji do svého formuláře.  
  
     Na hlavním panelu součást se zobrazí příslušné součásti.  
  
 Kromě toho součásti lze přidat do formuláře za běhu. Toto je běžný scénář, zvlášť, protože součásti nemají výraz visual, na rozdíl od ovládací prvky, které mají uživatelské rozhraní. V příkladu níže <xref:System.Windows.Forms.Timer> přidání komponenty v době běhu. (Všimněte si, že Visual Studio obsahuje několik různých časovače; v takovém případě pomocí Windows Forms <xref:System.Windows.Forms.Timer> součásti. Další informace o různých časovače v sadě Visual Studio najdete v tématu [Úvod do serverové časovače](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).)  
  
> [!CAUTION]
>  Součásti mají často prvek specifické vlastnosti, které musejí být nastaveny pro součást efektivní fungování. U <xref:System.Windows.Forms.Timer> níže uvedené součásti, nastavíte `Interval` vlastnost. Ujistěte se, při přidávání součástí do projektu, že nastavíte vlastnosti potřebné pro tuto součást.  
  
#### <a name="to-add-a-component-to-a-windows-form-programmatically"></a>Chcete-li přidat součást na formuláři Windows prostřednictvím kódu programu  
  
1.  Vytvoření instance <xref:System.Windows.Forms.Timer> – třída v kódu.  
  
2.  Nastavte `Interval` vlastnosti k určení doby mezi rysky časovač.  
  
3.  Nakonfigurujte všechny nezbytné vlastnosti pro příslušné součásti.  
  
     Následující kód ukazuje vytvoření <xref:System.Windows.Forms.Timer> s jeho `Interval` sadu vlastností.  
  
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
    >  Pod položkou škodlivý UserControl mohou být vystaveny místního počítače k ohrožení zabezpečení přes síť. To může být pouze o problém v případě osoba se zlými úmysly vytváření škodlivé vlastního ovládacího prvku, za nímž následuje jste omylem ho přidáte do projektu.  
  
## <a name="see-also"></a>Viz také  
 [Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/index.md)  
 [Postupy: Přidávání ovládacích prvků do Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [Postupy: Přidávání ovládacích prvků ActiveX do Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [Postupy: Kopírování ovládacích prvků mezi formuláři Windows Forms](../../../../docs/framework/winforms/controls/how-to-copy-controls-between-windows-forms.md)  
 [Vkládání ovládacích prvků do Windows Forms](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Ovládací prvky Windows Forms podle funkce](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)

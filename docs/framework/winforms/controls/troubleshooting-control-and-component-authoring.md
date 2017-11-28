---
title: "Řešení potíží s vytvářením ovládacích prvků a komponent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting components
- troubleshooting controls [Windows Forms]
- controls [Windows Forms], troubleshooting
- components [Windows Forms], troubleshooting
- Windows Forms controls, debugging
ms.assetid: e9c8c099-2271-4737-882f-50f336c7a55e
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e027a5b60e066a8d38db530c37a394227f2e892
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-control-and-component-authoring"></a>Řešení potíží s vytvářením ovládacích prvků a komponent
Toto téma obsahuje následující běžné problémy, které nastat při vývoji komponent a ovládacích prvků. Další informace najdete v tématu [programování s komponentami](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).  
  
-   Ovládací prvek nelze přidat do sady nástrojů  
  
-   Nelze ladění ovládacího prvku Windows Forms uživatele nebo součást  
  
-   Událost se vyvolá dvakrát v komponenta nebo ovládací prvek zděděné  
  
-   Chyba při návrhu: "Nepodařilo se vytvořit komponentu '*název komponenty*'"  
  
-   STAThreadAttribute  
  
-   Ikona součást nezobrazí v sadě nástrojů  
  
## <a name="cannot-add-control-to-toolbox"></a>Ovládací prvek nelze přidat do sady nástrojů  
 Pokud chcete přidat vlastní ovládací prvek, který jste vytvořili v jiném projektu nebo ovládacím prvkem třetí strany, který **sada nástrojů**, je potřeba udělat to ručně. Pokud aktuální projekt obsahuje komponenta nebo ovládací prvek, mělo by se zobrazit v **sada nástrojů** automaticky. Další informace najdete v tématu [návod: Automatické vyplnění nástrojů s komponentami vlastní](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
#### <a name="to-add-a-control-to-the-toolbox"></a>Přidání ovládacího prvku do sady nástrojů  
  
1.  Klikněte pravým tlačítkem myši **sada nástrojů** a z místní nabídky vyberte **zvolit položky**.  
  
2.  V **výběr položek sady nástrojů** dialogové okno pole, přidejte komponentu:  
  
    -   Pokud chcete přidat součásti rozhraní .NET Framework nebo ovládací prvek, klikněte **součásti rozhraní .NET Framework** kartě.  
  
         – nebo –  
  
    -   Pokud chcete přidat komponenty modelu COM nebo ovládací prvek ActiveX, klikněte **COM – součásti** kartě.  
  
3.  Pokud vlastní ovládací prvek je uveden v dialogovém okně, potvrďte je vybrána a potom klikněte na **OK**.  
  
     Ovládací prvek je přidán do **sada nástrojů**.  
  
4.  Pokud vlastní ovládací prvek není uveden v dialogovém okně, postupujte takto:  
  
    1.  Klikněte **Procházet** tlačítko.  
  
    2.  Přejděte do složky, která obsahuje soubor .dll, který obsahuje vlastní ovládací prvek.  
  
    3.  Vyberte soubor .dll a klikněte na tlačítko **otevřete**.  
  
         V dialogovém okně se zobrazí vlastního ovládacího prvku.  
  
    4.  Potvrďte, že je vybraná vlastního ovládacího prvku a pak klikněte na **OK**.  
  
         Vlastní ovládací prvek je přidán do **sada nástrojů**.  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a>Nelze ladění ovládacího prvku Windows Forms uživatele nebo součást  
 Pokud vaše ovládací prvek odvozen z <xref:System.Windows.Forms.UserControl> třídu, můžete ladit, její chování pomocí testovacího kontejneru. Další informace najdete v tématu [postupy: testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
 Další vlastní ovládací prvky a součásti nejsou samostatné projekty. Musí být hostované aplikací, třeba Windows Forms projektu. Chcete-li ladit komponenta nebo ovládací prvek, musíte jej přidat do projektu Windows Forms.  
  
#### <a name="to-debug-a-control-or-component"></a>Chcete-li ladit komponenta nebo ovládací prvek  
  
1.  Z **sestavení** nabídky, klikněte na tlačítko **sestavit řešení** k vytvoření vlastního řešení.  
  
2.  Z **soubor** nabídce zvolte **přidat**a potom **nový projekt** k přidání testovacího projektu do aplikace.  
  
3.  V **přidat nový projekt** dialogové okno Vybrat **aplikace Windows** pro typ projektu.  
  
4.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **odkazy** uzel pro nový projekt. V místní nabídce klikněte na tlačítko **přidat odkaz na** se přidat odkaz na projekt obsahující komponenta nebo ovládací prvek.  
  
5.  Vytvoření instance komponenta nebo ovládací prvek v k testovacímu projektu. Pokud příslušné součásti **sada nástrojů**, přetáhněte jej do vaší plochu návrháře, nebo můžete vytvořit instanci programově, jak je znázorněno v následujícím příkladu kódu.  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     Můžete teď ladit komponenta nebo ovládací prvek jako obvykle.  
  
 Další informace o ladění najdete v tématu [ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) a [návod: ladění vlastních ovládacích prvků Windows Forms v době návrhu](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a>Událost se vyvolá dvakrát v komponenta nebo ovládací prvek zděděné  
 Je to pravděpodobně z důvodu duplicitní `Handles` klauzule. Další informace najdete v tématu [řešení potíží s zděděná obslužné rutiny událostí v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a>Chyba při návrhu: "Nepodařilo se vytvořit komponentu 'název komponenty."  
 Komponenta nebo ovládací prvek, musíte zadat výchozí konstruktor bez parametrů. Při návrhu prostředí vytvoří instanci komponenta nebo ovládací prvek, nepokouší poskytnout ke konstruktor přetížení, které provést parametry žádné parametry.  
  
## <a name="stathreadattribute"></a>STAThreadAttribute  
 <xref:System.STAThreadAttribute> Common language runtime (CLR) informuje, že Windows Forms používá model single-threaded apartment. Nežádoucí chování může dojít, pokud tento atribut nelze použít k vaší aplikaci Windows Forms `Main` metoda. Obrázky na pozadí nemusí zobrazit třeba pro ovládací prvky <xref:System.Windows.Forms.ListView>. Některé ovládací prvky může také vyžadovat tento atribut pro správné automatického dokončování a chování přetažení myší.  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a>Ikona součást nezobrazí v sadě nástrojů  
 Při použití <xref:System.Drawing.ToolboxBitmapAttribute> pro vaše vlastní komponenta přidružit ikonu, bitmapy nezobrazí v sadě nástrojů pro součásti generován automaticky. Informace o bitové mapy, znovu načíst ovládacího prvku pomocí **výběr položek sady nástrojů** dialogové okno. Další informace najdete v tématu [postupy: poskytování rastrového obrázku panelu nástrojů pro ovládací prvek](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md).  
  
## <a name="see-also"></a>Viz také  
 [Vývoj Windows Forms – ovládací prvky v době návrhu](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [Návod: Automatické vyplnění nástrojů vlastními komponentami](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [Postupy: testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [Návod: Ladění vlastních Windows Forms – ovládací prvky v době návrhu](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 [Tvorba komponent](http://msdn.microsoft.com/library/4a5a5e49-0378-4a31-83bc-24da0f1a727d)  
 [Řešení potíží s vývoj návrhu](http://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [Programování s komponentami](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)

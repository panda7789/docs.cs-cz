---
title: Řešení potíží s vytvářením ovládacích prvků a komponent
ms.date: 03/30/2017
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
ms.openlocfilehash: 6494a154b9b4bd5bf29fc0e2fbd0b4e5e84550ff
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364162"
---
# <a name="troubleshooting-control-and-component-authoring"></a>Řešení potíží s vytvářením ovládacích prvků a komponent
Toto téma uvádí následující běžné problémy, které vznikají při vývoji komponent a ovládacích prvků. Další informace najdete v tématu [programování s komponentami](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).  
  
- Nelze přidat ovládací prvek do panelu nástrojů.  
  
- Nelze ladit model Windows Forms uživatelský ovládací prvek nebo komponentu  
  
- Událost je vyvolána dvakrát v zděděném ovládacím prvku nebo komponentě.  
  
- Chyba v době návrhu: "Nepovedlo se vytvořit součást s*názvem součásti*".  
  
- STAThreadAttribute  
  
- Ikona součásti se nezobrazí v sadě nástrojů.  
  
## <a name="cannot-add-control-to-toolbox"></a>Nelze přidat ovládací prvek do panelu nástrojů.  
 Chcete-li přidat vlastní ovládací prvek, který jste vytvořili v jiném projektu nebo ovládacím prvku třetí strany do **sady nástrojů**, musíte to provést ručně. Pokud aktuální projekt obsahuje ovládací prvek nebo komponentu, měla by se automaticky zobrazit v **sadě nástrojů** . Další informace najdete v tématu [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
#### <a name="to-add-a-control-to-the-toolbox"></a>Přidání ovládacího prvku do panelu nástrojů  
  
1. Klikněte pravým tlačítkem myši na **panel nástrojů** a v místní nabídce vyberte možnost **zvolit položky**.  
  
2. V dialogovém okně **zvolit položky sady nástrojů** přidejte komponentu:  
  
    - Chcete-li přidat komponentu .NET Framework nebo ovládací prvek, klikněte na kartu **komponenty .NET Framework** .  
  
         – nebo –  
  
    - Chcete-li přidat komponentu modelu COM nebo ovládací prvek ActiveX, klikněte na kartu **komponenty modelu COM** .  
  
3. Pokud je ovládací prvek uveden v dialogovém okně, potvrďte jeho výběr a klikněte na tlačítko **OK**.  
  
     Ovládací prvek je přidán do **sady nástrojů**.  
  
4. Pokud váš ovládací prvek není uveden v dialogovém okně, udělejte toto:  
  
    1. Klikněte na tlačítko **Procházet** .  
  
    2. Přejděte do složky, která obsahuje soubor. dll, který obsahuje váš ovládací prvek.  
  
    3. Vyberte soubor. dll a klikněte na **otevřít**.  
  
         Ovládací prvek se zobrazí v dialogovém okně.  
  
    4. Potvrďte, že je váš ovládací prvek vybraný, a pak klikněte na **OK**.  
  
         Váš ovládací prvek je přidán do **sady nástrojů**.  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a>Nelze ladit model Windows Forms uživatelský ovládací prvek nebo komponentu  
 Pokud je váš ovládací prvek odvozen z <xref:System.Windows.Forms.UserControl> třídy, můžete ladit chování za běhu pomocí kontejneru testů. Další informace najdete v tématu [jak: Otestuje chování prvku UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)v době běhu.  
  
 Další vlastní ovládací prvky a komponenty nejsou samostatné projekty. Musí být hostovány aplikací, jako je model Windows Forms projekt. Chcete-li ladit ovládací prvek nebo komponentu, je nutné ji přidat do projektu model Windows Forms.  
  
#### <a name="to-debug-a-control-or-component"></a>Ladění ovládacího prvku nebo komponenty  
  
1. V nabídce **sestavení** klikněte na **Sestavit řešení** a sestavte řešení.  
  
2. V nabídce **soubor** zvolte možnost **Přidat**a pak **Nový projekt** a přidejte do své aplikace testovací projekt.  
  
3. V dialogovém okně **Přidat nový projekt** vyberte možnost **aplikace systému Windows** pro typ projektu.  
  
4. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** pro nový projekt. V místní nabídce klikněte na **Přidat odkaz** a přidejte odkaz na projekt, který obsahuje ovládací prvek nebo komponentu.  
  
5. Vytvořte instanci ovládacího prvku nebo komponenty v testovacím projektu. Pokud je vaše komponenta v sadě **nástrojů**, můžete ji přetáhnout na plochu návrháře, nebo můžete instanci vytvořit programově, jak je znázorněno v následujícím příkladu kódu.  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     Nyní můžete ladit ovládací prvek nebo komponentu obvyklým způsobem.  
  
 Další informace o ladění naleznete v tématu [ladění v aplikaci Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) a [Návod: Ladění vlastních ovládacích prvků model Windows Forms v době](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)návrhu.  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a>Událost je vyvolána dvakrát v zděděném ovládacím prvku nebo komponentě.  
 Pravděpodobnou příčinou je duplicitní `Handles` klauzule. Další informace najdete v tématu [řešení potíží se zděděnými obslužnými rutinami událostí v Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a>Chyba v době návrhu: "Nepovedlo se vytvořit součást s názvem součásti".  
 Komponenta nebo ovládací prvek musí poskytovat konstruktor bez parametrů bez parametrů. Když vývojové prostředí vytvoří instanci vaší komponenty nebo ovládacího prvku, nepokusí se poskytnout žádné parametry přetížení konstruktoru, které přijímají parametry.  
  
## <a name="stathreadattribute"></a>STAThreadAttribute  
 <xref:System.STAThreadAttribute> Informuje modul CLR (Common Language Runtime), který model Windows Forms používá model Apartment s jedním vláknem. Pokud nepoužijete tento atribut na `Main` metodu model Windows Forms aplikace, můžete si všimnout nezamýšleného chování. Například obrázky na pozadí se nemusí zobrazit pro ovládací prvky jako <xref:System.Windows.Forms.ListView>. Některé ovládací prvky mohou také vyžadovat tento atribut pro správné automatické dokončování a chování při přetahování.  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a>Ikona součásti se nezobrazí v sadě nástrojů.  
 Když použijete <xref:System.Drawing.ToolboxBitmapAttribute> nástroj k přidružení ikony k vlastní komponentě, bitmapa se nezobrazí v sadě nástrojů pro automaticky generované součásti. Chcete-li zobrazit rastrový obrázek, načtěte ovládací prvek znovu pomocí dialogového okna **zvolit položky sady nástrojů** . Další informace najdete v tématu [jak: Poskytnutí rastrového obrázku panelu nástrojů pro](how-to-provide-a-toolbox-bitmap-for-a-control.md)ovládací prvek.  
  
## <a name="see-also"></a>Viz také:

- [Vývoj ovládacích prvků Windows Forms v době návrhu](developing-windows-forms-controls-at-design-time.md)
- [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [Postupy: Testování chování prvku UserControl v době běhu](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [Návod: Ladění vlastních ovládacích prvků model Windows Forms v době návrhu](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
- [Vytváření součástí](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))
- [Řešení potíží s vývojem v době návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))

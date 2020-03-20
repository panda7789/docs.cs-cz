---
title: 'Postupy: Zákaz stránek karet'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
ms.openlocfilehash: 9074aedb81a485267dc4faff92e0fe8d0d3b467f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182163"
---
# <a name="how-to-disable-tab-pages"></a>Postupy: Zákaz stránek karet
V některých případech budete chtít omezit přístup k datům, která jsou k dispozici v aplikaci Windows Forms. Jedním z příkladů může být, pokud máte data zobrazená na stránkách karty ovládacího prvku karta; Správci mohou mít na stránce karty informace, které byste chtěli omezit na uživatele hosta nebo uživatele nižší úrovně.  
  
### <a name="to-disable-tab-pages-programmatically"></a>Programové zakázání stránek tabulátorů  
  
1. Napište kód pro zpracování <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> události ovládacího prvku karty. Toto je událost, která je vyvolána, když uživatel přepne z jedné karty na další.  
  
2. Zkontrolujte přihlašovací údaje. V závislosti na předložených informacích můžete před povolením zobrazení karty zkontrolovat uživatelské jméno, ke kterým se uživatel přihlásil, nebo jinou formu pověření.  
  
3. Pokud má uživatel příslušná pověření, zobrazte kartu, na kterou jste klikli. Pokud uživatel nemá příslušná pověření, zobrazte okno se zprávou nebo jiné uživatelské rozhraní označující, že nemají přístup, a vraťte se na počáteční kartu.  
  
    > [!NOTE]
    > Při implementaci této funkce v produkčních aplikacích můžete tuto kontrolu <xref:System.Windows.Forms.Form.Load> pověření provést během události formuláře. To vám umožní skrýt kartu před zobrazením libovolného uživatelského rozhraní, což je mnohem čistší přístup k programování. Níže použitá metodika (kontrola přihlašovacích údajů a zakázání karty během <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> události) slouží pro ilustrativní účely.  
  
4. Pokud máte více než dvě stránky karet, zobrazte stránku karty odlišnou od původní.  
  
     V níže uvedeném <xref:System.Windows.Forms.CheckBox> příkladu se místo kontroly pověření používá ovládací prvek, protože kritéria pro přístup k kartě se budou lišit podle aplikace. Když <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> je vyvolána událost, pokud je kontrola pověření true (to znamená, že `TabPage2` zaškrtávací políčko je zaškrtnuto) a vybraná karta je (karta s důvěrnými informacemi, v tomto příkladu), pak `TabPage2` se zobrazí. V `TabPage3` opačném případě se zobrazí a zobrazí se uživateli okno se zprávou, které označuje, že neměl i příslušná přístupová oprávnění. Níže uvedený kód předpokládá formulář <xref:System.Windows.Forms.CheckBox> s`CredentialCheck`ovládacím <xref:System.Windows.Forms.TabControl> prvkem ( ) a ovládací prvek se třemi stránkami karet.  
  
    ```vb  
    Private Sub TabControl1_SelectedIndexChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles TabControl1.SelectedIndexChanged  
       ' Check Credentials Here  
  
       If CredentialCheck.Checked = True And _
       TabControl1.SelectedTab Is TabPage2 Then  
          TabControl1.SelectedTab = TabPage2  
       ElseIf CredentialCheck.Checked = False _
       And TabControl1.SelectedTab Is TabPage2 Then  
          MessageBox.Show _
         ("Unable to load tab. You have insufficient access privileges.")  
          TabControl1.SelectedTab = TabPage3  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void tabControl1_SelectedIndexChanged(object sender, System.EventArgs e)  
    {  
        // Check Credentials Here  
  
        if ((CredentialCheck.Checked == true) && (tabControl1.SelectedTab == tabPage2))
        {  
            tabControl1.SelectedTab = tabPage2;  
        }  
        else if ((CredentialCheck.Checked == false) && (tabControl1.SelectedTab == tabPage2))  
        {  
            MessageBox.Show("Unable to load tab. You have insufficient access privileges.");  
            tabControl1.SelectedTab = tabPage3;  
        }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void tabControl1_SelectedIndexChanged(  
          System::Object ^ sender,  
          System::EventArgs ^  e)  
       {  
          // Check Credentials Here  
          if ((CredentialCheck->Checked == true) &&  
              (tabControl1->SelectedTab == tabPage2))  
          {  
             tabControl1->SelectedTab = tabPage2;  
          }  
          else if ((CredentialCheck->Checked == false) &&  
                   (tabControl1->SelectedTab == tabPage2))  
          {  
             MessageBox::Show(String::Concat("Unable to load tab. ",  
                "You have insufficient access privileges."));  
             tabControl1->SelectedTab = tabPage3;  
          }  
       }  
    ```  
  
     (Visual C#, Visual C++) Umístěte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a>Viz také

- [TabControl – přehled ovládacího prvku](tabcontrol-control-overview-windows-forms.md)
- [Postupy: Přidání ovládacího prvku na kartu](how-to-add-a-control-to-a-tab-page.md)
- [Postupy: Přidání a odebrání karet pomocí ovládacího prvku Windows Forms TabControl](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [Postupy: Změna vzhledu Windows Forms TabControl](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)

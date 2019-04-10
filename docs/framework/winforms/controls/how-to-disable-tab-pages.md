---
title: 'Postupy: Zakázání karet'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
ms.openlocfilehash: 21592fdd74c43d40310e0fcbc96af6565a42e08b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336067"
---
# <a name="how-to-disable-tab-pages"></a>Postupy: Zakázání karet
V některých případech budete chtít omezit přístup k datům, která je k dispozici v rámci vaší aplikace Windows Forms. Jedním z příkladů může být, pokud máte data zobrazí na stránkách kartu ovládacího prvku karta; Správce může mít informace na stránce kartu, kterou chcete omezit z hosta nebo uživatelé na nižší úrovni.  
  
### <a name="to-disable-tab-pages-programmatically"></a>Chcete-li zákaz stránek karet prostřednictvím kódu programu  
  
1. Napište kód pro zpracování ovládacího prvku karta <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> událostí. Toto je událost, která se vyvolá, když uživatel přepíná z jedné karty na další.  
  
2. Zkontrolujte přihlašovací údaje. V závislosti na informace uvedené, můžete chtít zkontrolovat uživatelské jméno, které má uživatel s přihlášením nebo jiné formy přihlašovacích údajů předtím, než uživatel zobrazíte na kartě.  
  
3. Pokud má uživatel příslušná pověření, zobrazení, ke které došlo ke kliknutí na karty. Pokud uživatel nemá příslušná oprávnění, zobrazí okno se zprávou nebo některé jiné uživatelské rozhraní, což indikuje, že se nemají přístup a vrátit na první kartě.  
  
    > [!NOTE]
    >  Při implementaci této funkce ve svých aplikacích v produkčním prostředí, můžete tuto kontrolu můžete provést přihlašovacích údajů během formuláře <xref:System.Windows.Forms.Form.Load> událostí. To vám umožní skrýt kartě předtím, než se zobrazí uživatelské rozhraní, což je mnohem přehlednější přístup k programování. Metoda použitá níže (kontrola přihlašovacích údajů a na kartě při zakázání <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> události) je pro ilustraci.  
  
4. Volitelně Pokud máte více než dvě stránky karet, zobrazte stránky karty liší od původní.  
  
     V následujícím příkladu <xref:System.Windows.Forms.CheckBox> ovládací prvek se používá namísto kontrole přihlašovacích údajů, jako kritéria pro přístup ke kartě se liší podle aplikace. Když <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> událost se vyvolá, pokud je kontrola přihlašovacích údajů má hodnotu true (to znamená, že je zaškrtnuto zaškrtávací políčko) a je vybraná karta `TabPage2` (na kartě s důvěrné informace v tomto příkladu), pak `TabPage2` se zobrazí. V opačném případě `TabPage3` se zobrazí a zobrazí se okno se zprávou pro uživatele, označující, že nemá dostatečná oprávnění. Následující kód předpokládá formulář s <xref:System.Windows.Forms.CheckBox> ovládacího prvku (`CredentialCheck`) a <xref:System.Windows.Forms.TabControl> ovládací prvek s tři stránky karet.  
  
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
  
     (Visual C#, Visual C++) Umístěte následující kód do konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Přehled ovládacího prvku TabControl](tabcontrol-control-overview-windows-forms.md)
- [Postupy: Přidání ovládacího prvku na kartu](how-to-add-a-control-to-a-tab-page.md)
- [Postupy: Přidání a odebrání karet pomocí ovládacího prvku Windows Forms TabControl](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [Postupy: Změna vzhledu ovládacího prvku Windows Forms TabControl](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)

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
ms.openlocfilehash: 888228c28dce591b237be16b6a321afee0105208
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967140"
---
# <a name="how-to-disable-tab-pages"></a>Postupy: Zakázání karet
V některých případech budete chtít omezit přístup k datům, která jsou k dispozici v rámci vaší aplikace model Windows Forms. Příkladem může být, když máte data zobrazená na kartách ovládacího prvku karta; Správci mohou mít informace na stránce karet, které byste chtěli omezit od uživatelů typu Host nebo nižší úrovně.  
  
### <a name="to-disable-tab-pages-programmatically"></a>Chcete-li zakázat stránky karet programově  
  
1. Napište kód pro zpracování <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> události ovládacího prvku karta. Toto je událost, která je vyvolána, když uživatel přepne z jedné karty na další.  
  
2. Ověřte přihlašovací údaje. V závislosti na informacích, které jsou k dispozici, můžete chtít ověřit, že uživatel se přihlásil pomocí nebo jinou formu přihlašovacích údajů, než umožní uživateli zobrazit kartu.  
  
3. Pokud má uživatel odpovídající přihlašovací údaje, zobrazte kartu, na kterou jste klikli. Pokud uživatel nemá příslušná pověření, zobrazí okno se zprávou nebo jiné uživatelské rozhraní, které indikuje, že nemají přístup, a vrátí se na úvodní kartu.  
  
    > [!NOTE]
    > Při implementaci této funkce v produkčních aplikacích můžete tuto kontrolu přihlašovacích údajů provést během <xref:System.Windows.Forms.Form.Load> události formuláře. To vám umožní Skrýt kartu před zobrazením libovolného uživatelského rozhraní, což je mnohem čistší přístup k programování. Níže uvedená metodika (kontrola přihlašovacích údajů a zakázání karty během <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> události) je určena pro ilustrativní účely.  
  
4. Případně, pokud máte více než dvě stránky karet, zobrazte stránku karet odlišnou od původní.  
  
     V následujícím <xref:System.Windows.Forms.CheckBox> příkladu se místo kontroly přihlašovacích údajů používá ovládací prvek, protože kritéria pro přístup k této kartě se budou lišit v závislosti na aplikaci. Je-li vyvolána `TabPage2` `TabPage2` událost, pokud je provedena kontrola přihlašovacích údajů (tj. zaškrtávací políčko je zaškrtnuto) a vybraná karta je (karta s důvěrnými informacemi v tomto příkladu), zobrazí se. <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> V opačném případě se zobrazí okno se zprávou, že uživatel nemá příslušná přístupová oprávnění. `TabPage3` Níže uvedený kód předpokládá, že formulář má <xref:System.Windows.Forms.CheckBox> ovládací prvek`CredentialCheck`() a <xref:System.Windows.Forms.TabControl> ovládací prvek se třemi stránkami karet.  
  
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
  
     (Vizuál C#, vizuál C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
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
- [Postupy: Přidání ovládacího prvku na stránku karty](how-to-add-a-control-to-a-tab-page.md)
- [Postupy: Přidání a odebrání karet pomocí model Windows Forms TabControl](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [Postupy: Změna vzhledu model Windows Forms TabControl](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)

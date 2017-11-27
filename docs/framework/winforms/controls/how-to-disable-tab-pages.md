---
title: "Postupy: Zákaz stránek karet"
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
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 20674a93459f42a793ddf5f7ee5dffb1fa122d0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-disable-tab-pages"></a>Postupy: Zákaz stránek karet
V některých případech můžete omezit přístup k datům, která je k dispozici v rámci vaší aplikace Windows Forms. Příkladem toho může být v případě, že se data zobrazí na kartě stránkách ovládacího prvku karta; Správce může mít informace na kartě stránky, kterou chcete omezit hosta nebo nižší úrovně uživatelů.  
  
### <a name="to-disable-tab-pages-programmatically"></a>Chcete-li zákaz stránek karet prostřednictvím kódu programu  
  
1.  Napsat kód pro zpracování ovládacího prvku karta <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> událostí. Toto je událost, která se vyvolá, když uživatel přepíná z jedné karty na další.  
  
2.  Zkontrolujte přihlašovací údaje. V závislosti na informace uvedené, můžete před povolením uživateli zobrazit kartu zkontrolovat uživatelské jméno, které se uživatel přihlásí pomocí nebo jiné formy přihlašovacích údajů.  
  
3.  Pokud uživatel má příslušná pověření, zobrazí kartu označeného. Pokud uživatel nemá příslušná pověření, zobrazit okno se zprávou nebo některé jiné uživatelské rozhraní, což indikuje, že se nemají přístup a vraťte na kartu počáteční.  
  
    > [!NOTE]
    >  Pokud implementujete tuto funkci v provozních aplikací, můžete tuto kontrolu můžete provést přihlašovacích údajů během formuláře <xref:System.Windows.Forms.Form.Load> událostí. To vám umožní skrýt kartě předtím, než se zobrazí všechny uživatelské rozhraní, což je mnoho čištění přístup k programování. Metoda použitá níže (Kontrola přihlašovací údaje a zakázání kartě během <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> událostí) je pro ilustraci.  
  
4.  Pokud máte více než dvou karet, zobrazte stránky karty liší od originálu.  
  
     V příkladu níže <xref:System.Windows.Forms.CheckBox> řízení se používá místo kontrola přihlašovací údaje, jako kritéria pro přístup ke kartě se liší podle aplikace. Když <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> událost se vyvolá, pokud je hodnota true, zkontrolujte pověření (to znamená, že je zaškrtnuto zaškrtávací políčko) a je vybraná karta `TabPage2` (karta s důvěrné informace v tomto příkladu), pak `TabPage2` se zobrazí. V opačném `TabPage3` se zobrazí a zobrazí se okno se zprávou uživateli, označující neměl správná přístupová oprávnění. Následující kód předpokládá formulář s <xref:System.Windows.Forms.CheckBox> ovládací prvek (`CredentialCheck`) a <xref:System.Windows.Forms.TabControl> ovládacího prvku pomocí stránky tří karet.  
  
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
  
     (Visual C#, Visual C++) Vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Přehled ovládacího prvku TabControl](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [Postupy: Přidání ovládacího prvku do stránky karty](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [Postupy: přidávání a odebírání karet s prvkem Windows Forms TabControl](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)  
 [Postupy: Změna vzhledu Windows Forms TabControl](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)

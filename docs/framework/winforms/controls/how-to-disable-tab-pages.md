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
# <a name="how-to-disable-tab-pages"></a><span data-ttu-id="964e5-102">Postupy: Zakázání karet</span><span class="sxs-lookup"><span data-stu-id="964e5-102">How to: Disable Tab Pages</span></span>
<span data-ttu-id="964e5-103">V některých případech budete chtít omezit přístup k datům, která je k dispozici v rámci vaší aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="964e5-103">On some occasions, you will want to restrict access to data that is available within your Windows Forms application.</span></span> <span data-ttu-id="964e5-104">Jedním z příkladů může být, pokud máte data zobrazí na stránkách kartu ovládacího prvku karta; Správce může mít informace na stránce kartu, kterou chcete omezit z hosta nebo uživatelé na nižší úrovni.</span><span class="sxs-lookup"><span data-stu-id="964e5-104">One example of this might be when you have data displayed in the tab pages of a tab control; administrators could have information on a tab page that you would want to restrict from guest or lower-level users.</span></span>  
  
### <a name="to-disable-tab-pages-programmatically"></a><span data-ttu-id="964e5-105">Chcete-li zákaz stránek karet prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="964e5-105">To disable tab pages programmatically</span></span>  
  
1. <span data-ttu-id="964e5-106">Napište kód pro zpracování ovládacího prvku karta <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> událostí.</span><span class="sxs-lookup"><span data-stu-id="964e5-106">Write code to handle the tab control's <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event.</span></span> <span data-ttu-id="964e5-107">Toto je událost, která se vyvolá, když uživatel přepíná z jedné karty na další.</span><span class="sxs-lookup"><span data-stu-id="964e5-107">This is the event that is raised when the user switches from one tab to the next.</span></span>  
  
2. <span data-ttu-id="964e5-108">Zkontrolujte přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="964e5-108">Check credentials.</span></span> <span data-ttu-id="964e5-109">V závislosti na informace uvedené, můžete chtít zkontrolovat uživatelské jméno, které má uživatel s přihlášením nebo jiné formy přihlašovacích údajů předtím, než uživatel zobrazíte na kartě.</span><span class="sxs-lookup"><span data-stu-id="964e5-109">Depending upon the information presented, you may want to check the user name the user has logged in with or some other form of credentials before allowing the user to view the tab.</span></span>  
  
3. <span data-ttu-id="964e5-110">Pokud má uživatel příslušná pověření, zobrazení, ke které došlo ke kliknutí na karty.</span><span class="sxs-lookup"><span data-stu-id="964e5-110">If the user has appropriate credentials, display the tab that was clicked.</span></span> <span data-ttu-id="964e5-111">Pokud uživatel nemá příslušná oprávnění, zobrazí okno se zprávou nebo některé jiné uživatelské rozhraní, což indikuje, že se nemají přístup a vrátit na první kartě.</span><span class="sxs-lookup"><span data-stu-id="964e5-111">If the user does not have appropriate credentials, display a message box or some other user interface indicating that they do not have access, and return to the initial tab.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="964e5-112">Při implementaci této funkce ve svých aplikacích v produkčním prostředí, můžete tuto kontrolu můžete provést přihlašovacích údajů během formuláře <xref:System.Windows.Forms.Form.Load> událostí.</span><span class="sxs-lookup"><span data-stu-id="964e5-112">When you implement this functionality in your production applications, you can perform this credential check during the form's <xref:System.Windows.Forms.Form.Load> event.</span></span> <span data-ttu-id="964e5-113">To vám umožní skrýt kartě předtím, než se zobrazí uživatelské rozhraní, což je mnohem přehlednější přístup k programování.</span><span class="sxs-lookup"><span data-stu-id="964e5-113">This will allow you to hide the tab before any user interface is shown, which is a much cleaner approach to programming.</span></span> <span data-ttu-id="964e5-114">Metoda použitá níže (kontrola přihlašovacích údajů a na kartě při zakázání <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> události) je pro ilustraci.</span><span class="sxs-lookup"><span data-stu-id="964e5-114">The methodology used below (checking credentials and disabling the tab during the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event) is for illustrative purposes.</span></span>  
  
4. <span data-ttu-id="964e5-115">Volitelně Pokud máte více než dvě stránky karet, zobrazte stránky karty liší od původní.</span><span class="sxs-lookup"><span data-stu-id="964e5-115">Optionally, if you have more than two tab pages, display a tab page different from the original.</span></span>  
  
     <span data-ttu-id="964e5-116">V následujícím příkladu <xref:System.Windows.Forms.CheckBox> ovládací prvek se používá namísto kontrole přihlašovacích údajů, jako kritéria pro přístup ke kartě se liší podle aplikace.</span><span class="sxs-lookup"><span data-stu-id="964e5-116">In the example below, a <xref:System.Windows.Forms.CheckBox> control is used in lieu of checking the credentials, as the criteria for access to the tab will vary by application.</span></span> <span data-ttu-id="964e5-117">Když <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> událost se vyvolá, pokud je kontrola přihlašovacích údajů má hodnotu true (to znamená, že je zaškrtnuto zaškrtávací políčko) a je vybraná karta `TabPage2` (na kartě s důvěrné informace v tomto příkladu), pak `TabPage2` se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="964e5-117">When the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event is raised, if the credential check is true (that is, the check box is checked) and the selected tab is `TabPage2` (the tab with the confidential information, in this example), then `TabPage2` is displayed.</span></span> <span data-ttu-id="964e5-118">V opačném případě `TabPage3` se zobrazí a zobrazí se okno se zprávou pro uživatele, označující, že nemá dostatečná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="964e5-118">Otherwise, `TabPage3` is displayed and a message box is shown to the user, indicating they did not have appropriate access privileges.</span></span> <span data-ttu-id="964e5-119">Následující kód předpokládá formulář s <xref:System.Windows.Forms.CheckBox> ovládacího prvku (`CredentialCheck`) a <xref:System.Windows.Forms.TabControl> ovládací prvek s tři stránky karet.</span><span class="sxs-lookup"><span data-stu-id="964e5-119">The code below assumes a form with a <xref:System.Windows.Forms.CheckBox> control (`CredentialCheck`) and a <xref:System.Windows.Forms.TabControl> control with three tab pages.</span></span>  
  
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
  
     <span data-ttu-id="964e5-120">(Visual C#, Visual C++) Umístěte následující kód do konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="964e5-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="964e5-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="964e5-121">See also</span></span>

- [<span data-ttu-id="964e5-122">Přehled ovládacího prvku TabControl</span><span class="sxs-lookup"><span data-stu-id="964e5-122">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="964e5-123">Postupy: Přidání ovládacího prvku na kartu</span><span class="sxs-lookup"><span data-stu-id="964e5-123">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="964e5-124">Postupy: Přidání a odebrání karet pomocí ovládacího prvku Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="964e5-124">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="964e5-125">Postupy: Změna vzhledu ovládacího prvku Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="964e5-125">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)

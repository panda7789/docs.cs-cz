---
title: Dodatečné informace o zabezpečení ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, secure calls to Windows API
- security [Windows Forms]
- security [Windows Forms], calling APIs
- Clipboard [Windows Forms], securing access
ms.assetid: 15abda8b-0527-47c7-aedb-77ab595f2bf1
ms.openlocfilehash: a1d8606eb972a6e3bea52f6230cb893a4bbb5aac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519909"
---
# <a name="additional-security-considerations-in-windows-forms"></a>Dodatečné informace o zabezpečení ve Windows Forms
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nastavení zabezpečení může způsobit, že aplikace na spouštění v prostředí s částečnou důvěryhodností než jinak v místním počítači. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Omezuje přístup k takové kritické místním prostředkům jako systém souborů, sítě a nespravované rozhraní API, mimo jiné. Nastavení zabezpečení vliv na schopnost volat rozhraní API Win32 Microsoft nebo jiná rozhraní API, který nemůže být ověřen systémem zabezpečení. Zabezpečení ovlivní také dalších aspektů vaší aplikace, včetně souborů a dat přístupu a tisku. Další informace o přístupu k souborům a data v prostředí s částečnou důvěryhodností najdete v tématu [další soubor zabezpečení a přístup k datům ve Windows Forms](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md). Další informace o tisku v prostředí s částečnou důvěryhodností najdete v tématu [další Secure tiskem v systému Windows Forms](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md).  
  
 Následující části popisují, jak pracovat s schránky, provádět okno zpracování a volání rozhraní API Win32 z aplikací, které běží v prostředí s částečnou důvěryhodností.  
  
## <a name="clipboard-access"></a>Přístup schránky  
 <xref:System.Security.Permissions.UIPermission> Třída určuje přístup do schránky a přidružené <xref:System.Security.Permissions.UIPermissionClipboard> hodnota výčtu určuje úroveň přístupu. Následující tabulka uvádí možné oprávnění úrovně.  
  
|Hodnota UIPermissionClipboard|Popis|  
|---------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard>|Schránky můžete použít bez omezení.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard>|Schránky lze použít s určitými omezeními. Umožňuje umístit data do schránky (kopírování nebo vyjmutí příkaz operace) není omezeno. Vnitřní ovládací prvky, které přijímají vložení, jako je například textové pole, může přijmout data ze schránky, ale uživatelské ovládací prvky nelze přečíst prostřednictvím kódu programu ze schránky.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.NoClipboard>|Schránku nelze použít.|  
  
 Ve výchozím nastavení, obdrží zóny místního intranetu <xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard> přístup a zóně Internet obdrží <xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard> přístup. To znamená, že aplikace může kopírovat data do schránky, ale aplikace prostřednictvím kódu programu nelze vložit do nebo čtení ze schránky. Tato omezení zabránit programy bez úplný vztah důvěryhodnosti ve čtení obsahu zkopírován do schránky jiná aplikace. Pokud vaše aplikace vyžaduje úplný přístup schránky, ale nemáte oprávnění, budete muset zvýšení oprávnění pro vaši aplikaci. Další informace o zvyšování oprávnění najdete v tématu [obecné Správa zásad zabezpečení](http://msdn.microsoft.com/library/5121fe35-f0e3-402c-94ab-4f35b0a87b4b).  
  
## <a name="window-manipulation"></a>Manipulace s okna  
 <xref:System.Security.Permissions.UIPermission> Třída ovládací prvky také oprávnění k provedení okno manipulaci a další akce související s uživatelského rozhraní a přidruženého <xref:System.Security.Permissions.UIPermissionWindow> hodnota výčtu určuje úroveň přístupu. Následující tabulka uvádí možné oprávnění úrovně.  
  
 Ve výchozím nastavení, obdrží zóny místního intranetu <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> přístup a zóně Internet obdrží <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> přístup. To znamená, že v zóně Internet, aplikace můžete provádět většinu akcí uživatelského rozhraní a okna, ale vzhled okna budou upraveny. Okno upravené zobrazí oznámení bublinách při prvním spuštění, obsahuje text záhlaví změny a vyžaduje Zavřít v záhlaví okna. Oznámení bublinách a záhlaví identifikovat uživateli aplikace, který používá aplikace s částečnou důvěryhodností.  
  
|Hodnota UIPermissionWindow|Popis|  
|------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>|Uživatelé mohou používat všechna okna a vstupních událostech uživatele bez omezení.|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>|Uživatele můžete použít pouze bezpečnější nejvyšší úrovně windows a bezpečnější subwindows pro vykreslování a pouze vstupní události uživatele můžete použít pro uživatelské rozhraní v těchto windows nejvyšší úrovně a subwindows. Tyto bezpečnější windows jsou označeny jasně a mají omezení minimální a maximální velikost. Omezení bránit potenciálně škodlivé podvodným útokům, jako je například imitating systému přihlašovací obrazovky nebo plochy systému a omezuje programový přístup k nadřazené windows, rozhraní API související s fokus a použití <xref:System.Windows.Forms.ToolTip> řízení,|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>|Uživatele můžete použít pouze bezpečnější subwindows pro vykreslování a pouze vstupní události uživatele můžete použít pro uživatelské rozhraní v rámci této subwindow. Ovládací prvek zobrazí v prohlížeči je příkladem bezpečnější subwindow.|  
|<xref:System.Security.Permissions.UIPermissionWindow.NoWindows>|Uživatele nelze použít všechny windows nebo uživatelské rozhraní události. Můžete použít bez uživatelského rozhraní.|  
  
 Každá úroveň oprávnění identifikovaný <xref:System.Security.Permissions.UIPermissionWindow> výčtu umožňuje akce méně než úroveň nad ním. Následující tabulka uvádí akce, které jsou omezeny <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> a <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> hodnoty. Pro přesné oprávnění, které jsou požadovány pro každého člena naleznete v tématu odkaz na tohoto člena v dokumentaci ke knihovně tříd rozhraní .NET Framework.  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> oprávnění omezuje akce uvedené v následující tabulce.  
  
|Součást|Akce s omezeným přístupem|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.Application>|-Nastavení <xref:System.Windows.Forms.Application.SafeTopLevelCaptionFormat%2A> vlastnost.|  
|<xref:System.Windows.Forms.Control>|-Získávání <xref:System.Windows.Forms.Control.Parent%2A> vlastnost.<br />-Nastavení `Region` vlastnost.<br />-Volání <xref:System.Windows.Forms.Control.FindForm%2A> , <xref:System.Windows.Forms.Control.Focus%2A>, <xref:System.Windows.Forms.Control.FromChildHandle%2A> a <xref:System.Windows.Forms.Control.FromHandle%2A>, <xref:System.Windows.Forms.Control.PreProcessMessage%2A>, <xref:System.Windows.Forms.Control.ReflectMessage%2A>, nebo <xref:System.Windows.Forms.Control.SetTopLevel%2A> metoda.<br />-Volání <xref:System.Windows.Forms.Control.GetChildAtPoint%2A> metoda vrácen ovládací prvek není podřízeným volání ovládacího prvku.<br />-Upravte aktivního ovládacího prvku v ovládacím prvku kontejneru.|  
|<xref:System.Windows.Forms.Cursor>|-Nastavení <xref:System.Windows.Forms.Cursor.Clip%2A> vlastnost.<br />-Volání <xref:System.Windows.Forms.Control.Hide%2A> metoda.|  
|<xref:System.Windows.Forms.DataGrid>|-Volání <xref:System.Windows.Forms.ContainerControl.ProcessTabKey%2A> metoda.|  
|<xref:System.Windows.Forms.Form>|-Získávání <xref:System.Windows.Forms.Form.ActiveForm%2A> nebo <xref:System.Windows.Forms.Form.MdiParent%2A> vlastnost.<br />-Nastavení <xref:System.Windows.Forms.Form.ControlBox%2A>, <xref:System.Windows.Forms.Form.ShowInTaskbar%2A>, nebo <xref:System.Windows.Forms.Form.TopMost%2A> vlastnost.<br />-Nastavení <xref:System.Windows.Forms.Form.Opacity%2A> vlastnost menší než 50 %.<br />-Nastavení <xref:System.Windows.Forms.Form.WindowState%2A> vlastnost <xref:System.Windows.Forms.FormWindowState.Minimized> prostřednictvím kódu programu.<br />-Volání <xref:System.Windows.Forms.Form.Activate%2A> metoda.<br />– Pomocí <xref:System.Windows.Forms.FormBorderStyle.None>, <xref:System.Windows.Forms.FormBorderStyle.FixedToolWindow>, a <xref:System.Windows.Forms.FormBorderStyle.SizableToolWindow> <xref:System.Windows.Forms.FormBorderStyle> hodnot výčtu.|  
|<xref:System.Windows.Forms.NotifyIcon>|– Pomocí <xref:System.Windows.Forms.NotifyIcon> součást se úplně s omezeným přístupem.|  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> Hodnota omezuje akce uvedené v následující tabulce, kromě omezení, které umísťuje <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> hodnotu.  
  
|Součást|Akce s omezeným přístupem|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.CommonDialog>|-Znázorňující dialogové okno odvozené z <xref:System.Windows.Forms.CommonDialog> třídy.|  
|<xref:System.Windows.Forms.Control>|-Volání <xref:System.Windows.Forms.Control.CreateGraphics%2A> metoda.<br />-Nastavení <xref:System.Windows.Forms.Control.Cursor%2A> vlastnost.|  
|<xref:System.Windows.Forms.Control.Cursor%2A>|-Nastavení <xref:System.Windows.Forms.Cursor.Current%2A> vlastnost.|  
|<xref:System.Windows.Forms.MessageBox>|-Volání <xref:System.Windows.Forms.Form.Show%2A> metoda.|  
  
### <a name="hosting-third-party-controls"></a>Hostování ovládacích prvků třetích stran  
 Jiný druh okno zpracování může dojít, pokud svých formulářů hostování ovládacích prvků třetích stran. Ovládací prvek třetích stran, je vlastní <xref:System.Windows.Forms.UserControl> ještě nebyly vyvíjí a zkompilovat sami. Přestože scénáři pro hostování je obtížné před zneužitím, je možné teoreticky ovládacího prvku třetích stran, rozbalte prostor vykreslování tak, aby pokrývalo celé oblasti formuláře. Tento ovládací prvek pak může napodobovat kritické dialogové okno a požádat o informace, jako je kombinace uživatelského jména a hesla nebo čísla účtů bank vaše uživatele.  
  
 Toto potenciální riziko omezit, pomocí ovládacích prvků třetích stran pouze od dodavatelů, které můžete důvěřovat. Pokud chcete použít ovládací prvky třetích stran, které jste si stáhli z neověřitelný zdroje, doporučujeme, abyste si prošli zdrojový kód pro potenciální zneužití. Jakmile ověříte, zdroj je řádných, by měl kompilace sestavení si, že zdroj odpovídá sestavení.  
  
## <a name="win32-api-calls"></a>Volání rozhraní API Win32  
 Pokud váš návrh aplikace vyžaduje volání funkce z rozhraní API Win32, přistupují nespravovaného kódu. Akce kódu do okna nebo operačního systému v tomto případě nelze určit, když pracujete s volání rozhraní API Win32 nebo hodnoty. <xref:System.Security.Permissions.SecurityPermission> Třídy a <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> hodnotu <xref:System.Security.Permissions.SecurityPermissionFlag> výčtu řízení přístupu na nespravovaný kód. Aplikace můžete přístup k nespravovanému kódu jenom v případě, že jsou udělena <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> oprávnění. Ve výchozím nastavení můžete jenom aplikace, které běží místně volat nespravovaný kód.  
  
 Někteří členové Windows Forms poskytují nespravované přístup, který vyžaduje <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> oprávnění. Následující tabulka uvádí členy v <xref:System.Windows.Forms> obor názvů, které vyžadují oprávnění. Další informace o oprávněních, která jsou požadovány pro člena najdete v dokumentaci ke knihovně tříd rozhraní .NET Framework.  
  
|Součást|Člen|  
|---------------|------------|  
|<xref:System.Windows.Forms.Application>|-   <xref:System.Windows.Forms.Application.AddMessageFilter%2A> – Metoda<br />-   <xref:System.Windows.Forms.Application.CurrentInputLanguage%2A> Vlastnost<br />-   `Exit` – Metoda<br />-   <xref:System.Windows.Forms.Application.ExitThread%2A> – Metoda<br />-   <xref:System.Windows.Forms.Application.ThreadException> Události|  
|<xref:System.Windows.Forms.CommonDialog>|-   <xref:System.Windows.Forms.CommonDialog.HookProc%2A> – Metoda<br />-   <xref:System.Windows.Forms.CommonDialog.OwnerWndProc%2A>\ – metoda<br />-   <xref:System.Windows.Forms.CommonDialog.Reset%2A> – Metoda<br />-   <xref:System.Windows.Forms.CommonDialog.RunDialog%2A> – Metoda|  
|<xref:System.Windows.Forms.Control>|-   <xref:System.Windows.Forms.Control.CreateParams%2A> – Metoda<br />-   <xref:System.Windows.Forms.Control.DefWndProc%2A> – Metoda<br />-   <xref:System.Windows.Forms.Control.DestroyHandle%2A> – Metoda<br />-   <xref:System.Windows.Forms.Control.WndProc%2A> – Metoda|  
|<xref:System.Windows.Forms.Help>|-   <xref:System.Windows.Forms.Help.ShowHelp%2A> Metody<br />-   <xref:System.Windows.Forms.Help.ShowHelpIndex%2A> – Metoda|  
|<xref:System.Windows.Forms.NativeWindow>|-   <xref:System.Windows.Forms.NativeWindow> – Třída|  
|<xref:System.Windows.Forms.Screen>|-   <xref:System.Windows.Forms.Screen.FromHandle%2A> – Metoda|  
|<xref:System.Windows.Forms.SendKeys>|-   <xref:System.Windows.Forms.SendKeys.Send%2A> – Metoda<br />-   <xref:System.Windows.Forms.SendKeys.SendWait%2A> – Metoda|  
  
 Pokud aplikace nemá oprávnění k volání nespravovaného kódu, vaše aplikace musí požádat <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> oprávnění nebo je nutné vzít v úvahu alternativní způsoby implementace funkce; v mnoha případech Windows Forms poskytuje spravovaná alternativa k rozhraní API Win32 funkce. Pokud není možnost znamená, že existují a aplikace musí přístup k nespravovanému kódu, budete muset zvýšit úroveň oprávnění pro aplikace.  
  
 Oprávnění k volání nespravovaného kódu umožňuje provádět většinu nic aplikaci. Proto by oprávnění k volání nespravovaného kódu by měla lze udělit pouze pro aplikace, které pocházejí z důvěryhodného zdroje. V závislosti na aplikaci, může případně tímto druhem funkce aplikace, která provádí volání nespravovaného kódu být, volitelné nebo povoleno v prostředím úplný vztah důvěryhodnosti. Další informace o nebezpečná oprávnění najdete v tématu [nebezpečných oprávnění a Správa zásad](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md). Další informace o zvyšování oprávnění najdete v tématu [NIB: Obecné Správa zásad zabezpečení](http://msdn.microsoft.com/library/5121fe35-f0e3-402c-94ab-4f35b0a87b4b).  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečenější přístup k souborům a datům ve Windows Forms](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 [Zabezpečenější tisk ve Windows Forms](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 [Přehled zabezpečení ve Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [Windows Forms – zabezpečení](../../../docs/framework/winforms/windows-forms-security.md)  
 [Zabezpečování aplikací ClickOnce](/visualstudio/deployment/securing-clickonce-applications)

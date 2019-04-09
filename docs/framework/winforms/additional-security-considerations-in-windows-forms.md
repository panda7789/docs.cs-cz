---
title: Dodatečné informace o zabezpečení ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, secure calls to Windows API
- security [Windows Forms]
- security [Windows Forms], calling APIs
- Clipboard [Windows Forms], securing access
ms.assetid: 15abda8b-0527-47c7-aedb-77ab595f2bf1
ms.openlocfilehash: a101b5838b843f0130d16aab6eb199c7a54ca6b9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139526"
---
# <a name="additional-security-considerations-in-windows-forms"></a>Dodatečné informace o zabezpečení ve Windows Forms
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nastavení zabezpečení může způsobit, že aplikace na spouštění v prostředí částečným vztahem důvěryhodnosti než jinak než v místním počítači. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Omezuje přístup k takové kritické místním prostředkům jako systém souborů, síťové a nespravované rozhraní API, mimo jiné. Nastavení zabezpečení ovlivňuje možnost volat rozhraní API Microsoft Windows nebo jiná rozhraní API, který nelze ověřit pomocí zabezpečení systému. Zabezpečení má vliv také na dalších aspektů vaší aplikace, včetně přístupu k souborům a dat a tisku. Další informace o přístupu k souborům a data v částečně důvěryhodném prostředí, najdete v části [další soubor zabezpečení a přístup k datům ve Windows Forms](more-secure-file-and-data-access-in-windows-forms.md). Další informace o tisku v prostředí částečné důvěryhodnosti, naleznete v tématu [další zabezpečení tisku ve Windows Forms](more-secure-printing-in-windows-forms.md).  
  
 Následující části popisují, jak pracovat s schránky, provádět manipulace s okna a volání rozhraní Windows API z aplikace, které jsou spuštěny v prostředí s částečnou důvěryhodností.  
  
## <a name="clipboard-access"></a>Přístup schránky  
 <xref:System.Security.Permissions.UIPermission> Třída určuje přístup do schránky a přidružené <xref:System.Security.Permissions.UIPermissionClipboard> hodnota výčtu určuje úroveň přístupu. V následující tabulce jsou uvedeny úrovně oprávnění je to možné.  
  
|Hodnota UIPermissionClipboard|Popis|  
|---------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard>|Bez omezení je možné do schránky.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard>|S určitými omezeními je možné do schránky. Umožňuje vložit data do schránky (kopírování nebo vyjmutí příkaz operations) neomezený. Vnitřní ovládací prvky, které přijímají vložení, jako je textové pole, můžete přijímat data ze schránky, ale uživatelské ovládací prvky nelze číst prostřednictvím kódu programu ze schránky.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.NoClipboard>|Schránku nelze použít.|  
  
 Ve výchozím nastavení, obdrží zóny místního intranetu <xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard> přístup a zóně Internet obdrží <xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard> přístup. To znamená, že aplikace může kopírovat data do schránky, ale aplikace prostřednictvím kódu programu nelze vložit do nebo číst ze schránky. Tato omezení zabránit programy bez úplný vztah důvěryhodnosti z čtení obsahu zkopíroval do schránky. jiná aplikace. Pokud vaše aplikace vyžaduje úplný přístup schránky, ale nemáte oprávnění, budete muset zvýšení oprávnění pro vaši aplikaci. Další informace o zvyšování oprávnění najdete v tématu [obecné Správa zásad zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100)).  
  
## <a name="window-manipulation"></a>Manipulace s okna  
 <xref:System.Security.Permissions.UIPermission> Třídy také určuje oprávnění k provedení okno manipulaci a další akce související s Uživatelským rozhraním a přidružené <xref:System.Security.Permissions.UIPermissionWindow> hodnota výčtu určuje úroveň přístupu. V následující tabulce jsou uvedeny úrovně oprávnění je to možné.  
  
 Ve výchozím nastavení, obdrží zóny místního intranetu <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> přístup a zóně Internet obdrží <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> přístup. To znamená, že v zóně Internet, aplikace může provádět většinu časová okna a akce uživatelského rozhraní, ale vzhled v okně budou upraveny. Okno upravené bublinu oznámení při prvním spuštění se zobrazí, obsahuje text záhlaví upravené a vyžaduje tlačítko pro uzavření v záhlaví okna. Oznamovací bublina a záhlaví okna identifikovat uživatele, na kterém aplikace běží v částečném vztahu důvěryhodnosti aplikace.  
  
|Hodnota UIPermissionWindow|Popis|  
|------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>|Uživatelé mohou používat všechna okna a události uživatelského vstupu bez omezení.|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>|Uživatelé mohou používat pouze bezpečnější oknům nejvyšší úrovně a podoken bezpečnější pro kreslení a lze použít pouze události uživatelského vstupu pro uživatelské rozhraní v rámci těchto oken nejvyšší úrovně a podoken. Tyto bezpečnější windows jsou jasně označené a mají omezení minimální a maximální velikost. Omezení brání potenciálně škodlivé podvodným útokům, jako je například imitating systému přihlašovací obrazovky nebo plocha systému a omezuje programový přístup k nadřazenému objektu systému windows, rozhraní API související s fokus a použití <xref:System.Windows.Forms.ToolTip> ovládacího prvku|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>|Uživatele můžete použít pouze bezpečnější podoken pro kreslení a můžete použít pouze události uživatelského vstupu pro uživatelské rozhraní v rámci této subwindow. Ovládací prvek zobrazí v prohlížeči je příkladem bezpečnější subwindow.|  
|<xref:System.Security.Permissions.UIPermissionWindow.NoWindows>|Uživatelé nemůžou používat jakékoli windows nebo uživatelské rozhraní události. Je možné bez uživatelského rozhraní.|  
  
 Každá úroveň oprávnění identifikován <xref:System.Security.Permissions.UIPermissionWindow> výčet umožňuje méně než úroveň nad ním. Následující tabulka uvádí akce, které jsou omezené na základě <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> a <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> hodnoty. Konkrétní oprávnění, které jsou požadovány pro každého člena najdete v odkazu pro tohoto člena v dokumentaci knihovny tříd rozhraní .NET Framework.  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> oprávnění omezuje akce uvedené v následující tabulce.  
  
|Součást|Akce s omezeným přístupem|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.Application>|-Nastavení <xref:System.Windows.Forms.Application.SafeTopLevelCaptionFormat%2A> vlastnost.|  
|<xref:System.Windows.Forms.Control>|-Získávání <xref:System.Windows.Forms.Control.Parent%2A> vlastnost.<br />-Nastavení `Region` vlastnost.<br />-Volání <xref:System.Windows.Forms.Control.FindForm%2A> , <xref:System.Windows.Forms.Control.Focus%2A>, <xref:System.Windows.Forms.Control.FromChildHandle%2A> a <xref:System.Windows.Forms.Control.FromHandle%2A>, <xref:System.Windows.Forms.Control.PreProcessMessage%2A>, <xref:System.Windows.Forms.Control.ReflectMessage%2A>, nebo <xref:System.Windows.Forms.Control.SetTopLevel%2A> metody.<br />-Volání <xref:System.Windows.Forms.Control.GetChildAtPoint%2A> metodu, pokud se ovládací prvek není podřízeným volání ovládacího prvku.<br />– Úprava aktivního ovládacího prvku uvnitř ovládacího prvku kontejneru.|  
|<xref:System.Windows.Forms.Cursor>|-Nastavení <xref:System.Windows.Forms.Cursor.Clip%2A> vlastnost.<br />-Volání <xref:System.Windows.Forms.Control.Hide%2A> metody.|  
|<xref:System.Windows.Forms.DataGrid>|-Volání <xref:System.Windows.Forms.ContainerControl.ProcessTabKey%2A> metody.|  
|<xref:System.Windows.Forms.Form>|-Získávání <xref:System.Windows.Forms.Form.ActiveForm%2A> nebo <xref:System.Windows.Forms.Form.MdiParent%2A> vlastnost.<br />-Nastavení <xref:System.Windows.Forms.Form.ControlBox%2A>, <xref:System.Windows.Forms.Form.ShowInTaskbar%2A>, nebo <xref:System.Windows.Forms.Form.TopMost%2A> vlastnost.<br />-Nastavení <xref:System.Windows.Forms.Form.Opacity%2A> vlastnost pod 50 %.<br />-Nastavení <xref:System.Windows.Forms.Form.WindowState%2A> vlastnost <xref:System.Windows.Forms.FormWindowState.Minimized> prostřednictvím kódu programu.<br />-Volání <xref:System.Windows.Forms.Form.Activate%2A> metody.<br />– Používání <xref:System.Windows.Forms.FormBorderStyle.None>, <xref:System.Windows.Forms.FormBorderStyle.FixedToolWindow>, a <xref:System.Windows.Forms.FormBorderStyle.SizableToolWindow><xref:System.Windows.Forms.FormBorderStyle> hodnot výčtu.|  
|<xref:System.Windows.Forms.NotifyIcon>|– Používání <xref:System.Windows.Forms.NotifyIcon> komponenta je zcela omezen.|  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> Hodnota omezuje akce uvedené v následující tabulce, kromě omezení umístí <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> hodnotu.  
  
|Součást|Akce s omezeným přístupem|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.CommonDialog>|– Zobrazuje dialogové okno odvozené od <xref:System.Windows.Forms.CommonDialog> třídy.|  
|<xref:System.Windows.Forms.Control>|-Volání <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody.<br />-Nastavení <xref:System.Windows.Forms.Control.Cursor%2A> vlastnost.|  
|<xref:System.Windows.Forms.Control.Cursor%2A>|-Nastavení <xref:System.Windows.Forms.Cursor.Current%2A> vlastnost.|  
|<xref:System.Windows.Forms.MessageBox>|-Volání <xref:System.Windows.Forms.Form.Show%2A> metody.|  
  
### <a name="hosting-third-party-controls"></a>Hostování ovládacích prvků třetích stran  
 Jiný typ okno zpracování může dojít, pokud vaše formuláře hostovat ovládací prvky třetích stran. Ovládací prvek třetích stran je vlastní <xref:System.Windows.Forms.UserControl> , že jste vyvinuli a zkompilovány sami. I když scénáři hostování je obtížné využít, je teoreticky může pro ovládací prvek třetích stran a rozbalte jeho vykreslovací plochu pokrývá celou oblast formuláře. Tento ovládací prvek může potom napodobují kritické dialogovému oknu a žádost o informace, jako je kombinace uživatelského jména a hesla nebo účtu bank čísla od uživatelů.  
  
 Chcete-li toto riziko omezit, použijte ovládací prvky třetích stran pouze od dodavatelů, kterému můžete důvěřovat. Pokud používáte ovládací prvky třetích stran, které jste si stáhli z neověřitelný zdroje, doporučujeme, abyste si zdrojový kód pro potenciální zneužití. Po ověření, že je zdroj bez zlých, byste měli kompilovat sestavení sobě a zajistěte, aby odpovídal zdroj sestavení.  
  
## <a name="windows-api-calls"></a>Volání rozhraní API Windows  
 Pokud váš návrh aplikace vyžaduje volání funkce z rozhraní Windows API, se přístup k nespravovanému kódu. Akce kódu do okna nebo operační systém v tomto případě nelze určit, když pracujete s volání Windows API nebo hodnoty. <xref:System.Security.Permissions.SecurityPermission> Třídy a <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> hodnotu <xref:System.Security.Permissions.SecurityPermissionFlag> výčet řízení přístupu na nespravovaný kód. Aplikace můžete přístup k nespravovanému kódu, jenom když jsou udělena <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> oprávnění. Ve výchozím nastavení můžete pouze aplikace, které jsou spuštěné místně volání nespravovaného kódu.  
  
 Někteří členové Windows Forms poskytují nespravovaný přístup, který vyžaduje <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> oprávnění. Následující tabulka uvádí členy <xref:System.Windows.Forms> obor názvů, které vyžadují oprávnění. Další informace o oprávněních, které jsou požadovány pro člena najdete v dokumentaci knihovny tříd rozhraní .NET Framework.  
  
|Součást|Člen|  
|---------------|------------|  
|<xref:System.Windows.Forms.Application>|-   <xref:System.Windows.Forms.Application.AddMessageFilter%2A> – Metoda<br />-   <xref:System.Windows.Forms.Application.CurrentInputLanguage%2A> Vlastnost<br />-   `Exit` – Metoda<br />-   <xref:System.Windows.Forms.Application.ExitThread%2A> – Metoda<br />-   <xref:System.Windows.Forms.Application.ThreadException> Události|  
|<xref:System.Windows.Forms.CommonDialog>|-   <xref:System.Windows.Forms.CommonDialog.HookProc%2A> – Metoda<br />-   <xref:System.Windows.Forms.CommonDialog.OwnerWndProc%2A>\ – metoda<br />-   <xref:System.Windows.Forms.CommonDialog.Reset%2A> – Metoda<br />-   <xref:System.Windows.Forms.CommonDialog.RunDialog%2A> – Metoda|  
|<xref:System.Windows.Forms.Control>|-   <xref:System.Windows.Forms.Control.CreateParams%2A> – Metoda<br />-   <xref:System.Windows.Forms.Control.DefWndProc%2A> – Metoda<br />-   <xref:System.Windows.Forms.Control.DestroyHandle%2A> – Metoda<br />-   <xref:System.Windows.Forms.Control.WndProc%2A> – Metoda|  
|<xref:System.Windows.Forms.Help>|-   <xref:System.Windows.Forms.Help.ShowHelp%2A> Metody<br />-   <xref:System.Windows.Forms.Help.ShowHelpIndex%2A> – Metoda|  
|<xref:System.Windows.Forms.NativeWindow>|-   <xref:System.Windows.Forms.NativeWindow> Třída|  
|<xref:System.Windows.Forms.Screen>|-   <xref:System.Windows.Forms.Screen.FromHandle%2A> – Metoda|  
|<xref:System.Windows.Forms.SendKeys>|-   <xref:System.Windows.Forms.SendKeys.Send%2A> – Metoda<br />-   <xref:System.Windows.Forms.SendKeys.SendWait%2A> – Metoda|  
  
 Pokud aplikace nemá oprávnění volat nespravovaný kód, vaše aplikace musí požádat o <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> oprávnění, nebo musíte zvážit alternativní způsoby implementace funkce; v mnoha případech Windows Forms poskytuje spravované alternativy k Windows Funkce rozhraní API. Pokud žádná alternativa znamená, že existují a aplikace musí přístup k nespravovanému kódu, budete muset zvýšení oprávnění pro aplikaci.  
  
 Oprávnění pro volání nespravovaného kódu umožňuje aplikaci provést nejvíce cokoli. Proto by měl oprávnění pro volání nespravovaného kódu udělena pouze pro aplikace, které pocházejí z důvěryhodného zdroje. V závislosti na aplikaci, může také část funkčnost aplikace, která provádí volání nespravovaného kódu být, volitelné, nebo není povolen v úplném vztahu důvěryhodnosti pouze prostředí. Další informace o nebezpečná oprávnění najdete v tématu [Správa nebezpečných oprávnění a zásad](../misc/dangerous-permissions-and-policy-administration.md). Další informace o zvyšování oprávnění najdete v tématu [obecné Správa zásad zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100)).  
  
## <a name="see-also"></a>Viz také:

- [Více zabezpečený přístup k souborům a datům ve Windows Forms](more-secure-file-and-data-access-in-windows-forms.md)
- [Bezpečnější tisk ve Windows Forms](more-secure-printing-in-windows-forms.md)
- [Přehled zabezpečení ve Windows Forms](security-in-windows-forms-overview.md)
- [Windows Forms – zabezpečení](windows-forms-security.md)
- [Zabezpečování aplikací ClickOnce](/visualstudio/deployment/securing-clickonce-applications)

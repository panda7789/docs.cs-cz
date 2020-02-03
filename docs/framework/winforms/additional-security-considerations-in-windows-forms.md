---
title: Další požadavky na zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, secure calls to Windows API
- security [Windows Forms]
- security [Windows Forms], calling APIs
- Clipboard [Windows Forms], securing access
ms.assetid: 15abda8b-0527-47c7-aedb-77ab595f2bf1
ms.openlocfilehash: c8d51a57194f1dc536bc4b5d0376987dbfd3b2cf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739819"
---
# <a name="additional-security-considerations-in-windows-forms"></a>Dodatečné informace o zabezpečení ve Windows Forms
Nastavení zabezpečení .NET Framework může způsobit, že vaše aplikace bude běžet jinak v prostředí s částečným vztahem důvěryhodnosti, než na místním počítači. .NET Framework kromě jiných věcí omezuje přístup k takovým důležitým místním prostředkům jako systém souborů, síť a nespravovaná rozhraní API. Nastavení zabezpečení má vliv na možnost volání rozhraní Microsoft Windows API nebo jiných rozhraní API, která nelze ověřit systémem zabezpečení. Zabezpečení má vliv také na další aspekty aplikace, včetně souborů a přístupu k datům a tisku. Další informace o přístupu k souborům a datům v prostředí s částečným vztahem důvěryhodnosti najdete [v tématu bezpečnější přístup k souborům a datům v model Windows Forms](more-secure-file-and-data-access-in-windows-forms.md). Další informace o tisku v prostředí s částečným vztahem důvěryhodnosti najdete v tématu bezpečnější [Tisk v model Windows Forms](more-secure-printing-in-windows-forms.md).  
  
 Následující části popisují, jak pracovat se schránkou, provádět manipulaci s okny a volat rozhraní Windows API z aplikací, které běží v prostředí s částečným vztahem důvěryhodnosti.  
  
## <a name="clipboard-access"></a>Přístup do schránky  
 Třída <xref:System.Security.Permissions.UIPermission> řídí přístup ke schránce a přidružená hodnota výčtu <xref:System.Security.Permissions.UIPermissionClipboard> označuje úroveň přístupu. V následující tabulce jsou uvedeny možné úrovně oprávnění.  
  
|Hodnota UIPermissionClipboard|Popis|  
|---------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard>|Schránku lze použít bez omezení.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard>|Schránku lze použít s některými omezeními. Možnost vkládat data do schránky (operace kopírování nebo vyjmutí příkazu) nejsou omezeny. Vnitřní ovládací prvky, které přijímají vložení, jako je například textové pole, mohou přijímat data ze schránky, ale uživatelské ovládací prvky nemohou číst ze schránky programově.|  
|<xref:System.Security.Permissions.UIPermissionClipboard.NoClipboard>|Schránku nelze použít.|  
  
 Ve výchozím nastavení obdrží zóna místního intranetu přístup <xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard> a zóna Internetu obdrží přístup <xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard>. To znamená, že aplikace může kopírovat data do schránky, ale aplikace nemůže programově vkládat nebo číst ze schránky. Tato omezení zabraňují programům bez úplné důvěryhodnosti v čtení obsahu zkopírovaného do schránky jinou aplikací. Pokud vaše aplikace vyžaduje úplný přístup do schránky, ale nemáte oprávnění, budete muset zvýšit oprávnění pro vaši aplikaci. Další informace o oprávněních ke zvýšení oprávnění najdete v tématu [Obecná Správa zásad zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100)).  
  
## <a name="window-manipulation"></a>Manipulace s Windows  
 Třída <xref:System.Security.Permissions.UIPermission> také ovládá oprávnění k provádění manipulace s oknem a dalších akcí souvisejících s uživatelským rozhraním a přidružená hodnota výčtu <xref:System.Security.Permissions.UIPermissionWindow> označuje úroveň přístupu. V následující tabulce jsou uvedeny možné úrovně oprávnění.  
  
 Ve výchozím nastavení obdrží zóna místního intranetu přístup <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> a zóna Internetu obdrží přístup <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>. To znamená, že v zóně Internet může aplikace provádět většinu oken a akcí uživatelského rozhraní, ale vzhled okna se upraví. Změněné okno zobrazí při prvním spuštění oznámení s bublinou, obsahuje upravený text záhlaví a vyžaduje na záhlaví tlačítko Zavřít. Oznámení a záhlaví v bublině se identifikují uživateli aplikace, že aplikace běží v částečném vztahu důvěryhodnosti.  
  
|Hodnota UIPermissionWindow|Popis|  
|------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>|Uživatelé můžou bez omezení použít všechny události vstupu v systému Windows a uživatelem.|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>|Uživatelé můžou použít jenom bezpečnější okna na nejvyšší úrovni a bezpečněji pro vykreslování a můžou použít jenom události vstupu uživatele pro uživatelské rozhraní v rámci těchto oken a podoken na nejvyšší úrovni. Tato bezpečnější okna jsou jasně označená a mají omezení minimální a maximální velikosti. Tato omezení zabraňují potenciálně škodlivým útokům prostřednictvím falešného poškození, jako je například napodobení přihlašovacích obrazovek systému nebo plochy systému, a omezují programový přístup k nadřazeným systémům Windows, rozhraním API souvisejících s fokusem a použití ovládacího prvku <xref:System.Windows.Forms.ToolTip>,|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>|Uživatelé můžou použít jenom bezpečnější podoken k vykreslování a můžou pro uživatelské rozhraní v tomto podoknì používat jenom události vstupu uživatele. Příkladem bezpečnějšího podoken je ovládací prvek zobrazený v prohlížeči.|  
|<xref:System.Security.Permissions.UIPermissionWindow.NoWindows>|Uživatelé nemůžou používat žádné události Windows ani uživatelského rozhraní. Nelze použít žádné uživatelské rozhraní.|  
  
 Každá úroveň oprávnění identifikovaná výčtem <xref:System.Security.Permissions.UIPermissionWindow> umožňuje méně akcí než úroveň nad ní. Následující tabulky označují akce, které jsou omezeny hodnotami <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> a <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>. Pro přesná oprávnění, která jsou vyžadována pro každého člena, se podívejte na odkaz pro tohoto člena v dokumentaci knihovny tříd .NET Framework.  
  
 oprávnění <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> omezuje akce uvedené v následující tabulce.  
  
|Komponenta|Omezené akce|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.Application>|-Nastavení vlastnosti <xref:System.Windows.Forms.Application.SafeTopLevelCaptionFormat%2A>.|  
|<xref:System.Windows.Forms.Control>|– Získávání vlastnosti <xref:System.Windows.Forms.Control.Parent%2A>.<br />-Nastavení vlastnosti `Region`.<br />– Voláním metody <xref:System.Windows.Forms.Control.FindForm%2A>, <xref:System.Windows.Forms.Control.Focus%2A>, <xref:System.Windows.Forms.Control.FromChildHandle%2A> a <xref:System.Windows.Forms.Control.FromHandle%2A>, <xref:System.Windows.Forms.Control.PreProcessMessage%2A>, <xref:System.Windows.Forms.Control.ReflectMessage%2A>nebo <xref:System.Windows.Forms.Control.SetTopLevel%2A>.<br />– Volání metody <xref:System.Windows.Forms.Control.GetChildAtPoint%2A>, pokud ovládací prvek není podřízený ovládacímu prvku volání.<br />-Změnit fokus ovládacího prvku uvnitř ovládacího prvku kontejneru.|  
|<xref:System.Windows.Forms.Cursor>|-Nastavení vlastnosti <xref:System.Windows.Forms.Cursor.Clip%2A>.<br />– Volání metody <xref:System.Windows.Forms.Control.Hide%2A>.|  
|<xref:System.Windows.Forms.DataGrid>|– Volání metody <xref:System.Windows.Forms.ContainerControl.ProcessTabKey%2A>.|  
|<xref:System.Windows.Forms.Form>|– Načítá se vlastnost <xref:System.Windows.Forms.Form.ActiveForm%2A> nebo <xref:System.Windows.Forms.Form.MdiParent%2A>.<br />-Nastavení vlastnosti <xref:System.Windows.Forms.Form.ControlBox%2A>, <xref:System.Windows.Forms.Form.ShowInTaskbar%2A>nebo <xref:System.Windows.Forms.Form.TopMost%2A>.<br />– Nastavení vlastnosti <xref:System.Windows.Forms.Form.Opacity%2A> pod 50%.<br />– Nastavení vlastnosti <xref:System.Windows.Forms.Form.WindowState%2A> na <xref:System.Windows.Forms.FormWindowState.Minimized> programově.<br />– Volání metody <xref:System.Windows.Forms.Form.Activate%2A>.<br />– Použití hodnot výčtu <xref:System.Windows.Forms.FormBorderStyle> <xref:System.Windows.Forms.FormBorderStyle.None>, <xref:System.Windows.Forms.FormBorderStyle.FixedToolWindow>a <xref:System.Windows.Forms.FormBorderStyle.SizableToolWindow>.|  
|<xref:System.Windows.Forms.NotifyIcon>|-Použití součásti <xref:System.Windows.Forms.NotifyIcon> je zcela omezené.|  
  
 Hodnota <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> omezuje akce uvedené v následující tabulce Kromě omezení zadaných <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> hodnotou.  
  
|Komponenta|Omezené akce|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.CommonDialog>|-Zobrazení dialogového okna odvozeného od <xref:System.Windows.Forms.CommonDialog> třídy.|  
|<xref:System.Windows.Forms.Control>|– Volání metody <xref:System.Windows.Forms.Control.CreateGraphics%2A>.<br />-Nastavení vlastnosti <xref:System.Windows.Forms.Control.Cursor%2A>.|  
|<xref:System.Windows.Forms.Control.Cursor%2A>|-Nastavení vlastnosti <xref:System.Windows.Forms.Cursor.Current%2A>.|  
|<xref:System.Windows.Forms.MessageBox>|– Volání metody <xref:System.Windows.Forms.Form.Show%2A>.|  
  
### <a name="hosting-third-party-controls"></a>Hostování ovládacích prvků třetích stran  
 Další druh manipulace s oknem může nastat, pokud vaše formuláře hostují ovládací prvky třetích stran. Ovládací prvek třetí strany je libovolný vlastní <xref:System.Windows.Forms.UserControl>, který jste nevyvinuli a zkompilujete sami. I když hostující scénář je obtížné zneužít, je teoreticky možné rozšířit plochu vykreslování tak, aby pokryla celou oblast formuláře. Tento ovládací prvek by pak mohl napodobovat kritické dialogové okno a vyžadovat informace, jako jsou kombinace uživatelského jména a hesla nebo čísla bankovních účtů od uživatelů.  
  
 Chcete-li toto riziko omezit, použijte ovládací prvky třetích stran pouze od dodavatelů, kterým můžete důvěřovat. Pokud používáte ovládací prvky třetích stran, které jste stáhli z neověřeného zdroje, doporučujeme zkontrolovat zdrojový kód pro potenciální zneužití. Po ověření, že je zdroj neškodlivý, byste měli zkompilovat sestavení sami, abyste zajistili, že zdroj odpovídá sestavení.  
  
## <a name="windows-api-calls"></a>Volání rozhraní API systému Windows  
 Pokud návrh aplikace vyžaduje volání funkce z rozhraní API systému Windows, přistupujete k nespravovanému kódu. V takovém případě nelze při práci s voláním nebo hodnotami rozhraní API systému Windows určit akce kódu pro okno nebo operační systém. Třída <xref:System.Security.Permissions.SecurityPermission> a hodnota <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> ovládacího prvku <xref:System.Security.Permissions.SecurityPermissionFlag> výčtu mají přístup k nespravovanému kódu. Aplikace má přístup k nespravovanému kódu pouze tehdy, je-li uděleno oprávnění <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>. Ve výchozím nastavení mohou volat nespravovaný kód pouze aplikace, které jsou spuštěny místně.  
  
 Někteří model Windows Forms členové poskytují nespravovaný přístup, který vyžaduje oprávnění <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>. V následující tabulce je uveden seznam členů v oboru názvů <xref:System.Windows.Forms>, který vyžaduje oprávnění. Další informace o oprávněních, která jsou vyžadována pro člena, naleznete v dokumentaci knihovny tříd .NET Framework.  
  
|Komponenta|Člen|  
|---------------|------------|  
|<xref:System.Windows.Forms.Application>|Metoda -   <xref:System.Windows.Forms.Application.AddMessageFilter%2A><br />vlastnost -   <xref:System.Windows.Forms.Application.CurrentInputLanguage%2A><br />Metoda -   `Exit`<br />Metoda -   <xref:System.Windows.Forms.Application.ExitThread%2A><br />událost <xref:System.Windows.Forms.Application.ThreadException> -   |  
|<xref:System.Windows.Forms.CommonDialog>|Metoda -   <xref:System.Windows.Forms.CommonDialog.HookProc%2A><br />-   <xref:System.Windows.Forms.CommonDialog.OwnerWndProc%2A>\ metoda<br />Metoda -   <xref:System.Windows.Forms.CommonDialog.Reset%2A><br />Metoda -   <xref:System.Windows.Forms.CommonDialog.RunDialog%2A>|  
|<xref:System.Windows.Forms.Control>|Metoda -   <xref:System.Windows.Forms.Control.CreateParams%2A><br />Metoda -   <xref:System.Windows.Forms.Control.DefWndProc%2A><br />Metoda -   <xref:System.Windows.Forms.Control.DestroyHandle%2A><br />Metoda -   <xref:System.Windows.Forms.Control.WndProc%2A>|  
|<xref:System.Windows.Forms.Help>|metody -   <xref:System.Windows.Forms.Help.ShowHelp%2A><br />Metoda -   <xref:System.Windows.Forms.Help.ShowHelpIndex%2A>|  
|<xref:System.Windows.Forms.NativeWindow>|Třída -   <xref:System.Windows.Forms.NativeWindow>|  
|<xref:System.Windows.Forms.Screen>|Metoda -   <xref:System.Windows.Forms.Screen.FromHandle%2A>|  
|<xref:System.Windows.Forms.SendKeys>|Metoda -   <xref:System.Windows.Forms.SendKeys.Send%2A><br />Metoda -   <xref:System.Windows.Forms.SendKeys.SendWait%2A>|  
  
 Pokud vaše aplikace nemá oprávnění k volání nespravovaného kódu, musí vaše aplikace požádat o <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> oprávnění, nebo je nutné vzít v úvahu alternativní způsoby implementace funkcí; v mnoha případech model Windows Forms poskytuje spravovanou alternativu funkcí rozhraní API systému Windows. Pokud neexistuje žádný alternativní význam a aplikace musí mít přístup k nespravovanému kódu, bude nutné zvýšit oprávnění pro aplikaci.  
  
 Oprávnění k volání nespravovaného kódu umožňuje aplikaci provést většinu všeho. Proto oprávnění k volání nespravovaného kódu by měla být udělena pouze aplikacím, které pocházejí z důvěryhodného zdroje. Alternativně, v závislosti na aplikaci, může být část funkce aplikace, která volá nespravovaný kód, volitelná nebo povolená jenom v prostředí s plnou důvěryhodností. Další informace o nebezpečných oprávněních najdete v tématu [Správa nebezpečných oprávnění a zásad](../misc/dangerous-permissions-and-policy-administration.md). Další informace o oprávněních ke zvýšení oprávnění najdete v tématu [Obecná Správa zásad zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100)).  
  
## <a name="see-also"></a>Viz také

- [Zabezpečenější přístup k souborům a datům ve Windows Forms](more-secure-file-and-data-access-in-windows-forms.md)
- [Zabezpečenější tisk ve Windows Forms](more-secure-printing-in-windows-forms.md)
- [Přehled zabezpečení ve Windows Forms](security-in-windows-forms-overview.md)
- [Windows Forms – zabezpečení](windows-forms-security.md)
- [Zabezpečování aplikací ClickOnce](/visualstudio/deployment/securing-clickonce-applications)

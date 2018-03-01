---
title: "Přehled nastavení aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ApplicationsSettingsOverview
helpviewer_keywords:
- application settings [Windows Forms], about application settings
- dynamic properties
- user preferences [Windows Forms], tracking
ms.assetid: 0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f74595ce672079db69fd36fb2b2eb982bc90b448
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="application-settings-overview"></a>Přehled nastavení aplikace
Toto téma popisuje postup vytvoření a uložení dat nastavení jménem vaší aplikace a uživatele.  
  
 Funkce nastavení aplikace Windows Forms umožňuje snadno vytvářet, ukládat a spravovat vlastní aplikaci a uživatelské předvolby v klientském počítači. Pomocí nastavení aplikace Windows Forms můžete uložit pouze data aplikací, jako je například databázové připojovací řetězce, ale také uživatelská data, jako třeba uživatelské předvolby aplikace. Pomocí sady Visual Studio nebo vlastní spravovaného kódu, můžete vytvořit nové nastavení, přečtěte si je z a zapíše je na disk, je svázat s vlastnostmi svých formulářů a ověřit nastavení data před načítání a ukládání.  
  
 Nastavení aplikace umožňuje vývojářům uložit stav ve svých aplikacích pomocí velmi malé vlastního kódu a je to náhrada za dynamické vlastnosti v předchozích verzích [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Nastavení aplikace obsahuje mnoho vylepšení přes dynamické vlastnosti, které jsou jen pro čtení, pozdní vazbou a vyžadovat další vlastní programování. Dynamických vlastností třídy byly ponechány v [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], ale jsou právě prostředí třídy, které dynamicky balí třídy nastavení aplikace.  
  
## <a name="what-are-application-settings"></a>Co jsou nastavení aplikace?  
 Aplikace Windows Forms často vyžadují data, která jsou kritická pro spuštění aplikace, ale které nechcete zahrnout přímo v kódu aplikace. Pokud vaše aplikace používá webová služba nebo databázový server, můžete tyto informace ukládaly do samostatného souboru, abyste ho v budoucnu změnit bez znovu kompilace. Podobně vaše aplikace může vyžadovat ukládání dat, která je specifická pro aktuálního uživatele. Většina aplikací mít například uživatelských předvoleb, které přizpůsobit vzhled a chování aplikace.  
  
 Nastavení adresy aplikace oba musí tím, že poskytuje snadný způsob, jak uložit nastavení jak obor aplikace a nastavení uživatele v klientském počítači. Pomocí sady Visual Studio nebo editoru kódu, definovat nastavení pro danou vlastnost zadáním jeho název, datový typ a oboru (aplikaci nebo uživatele). Dokonce můžete umístit související nastavení do skupiny s názvem pro snadnější použití a čitelnost. Jakmile definovány, tato nastavení jsou nastavené jako trvalé a automaticky načíst zpět do paměti v době běhu. Modulární architektura umožňuje mechanismus trvalosti změnit, ale ve výchozím nastavení, je použít místního systému souborů.  
  
 Nastavení aplikace funguje tak, že zachování dat ve formátu XML na jiném konfiguračním (config) souborů, odpovídající jestli nastavení je obor aplikace nebo nastavení uživatele. Ve většině případů nastavení rozsahu aplikace jsou jen pro čtení; protože jsou informace o programu, obvykle nemusíte je přepsat. Naopak nastavení rozsahu uživatele můžete číst a zapisovat bezpečně za běhu, i v případě, že vaše aplikace běží v částečné důvěryhodnosti. Další informace o částečné důvěryhodnosti najdete v tématu [zabezpečení ve Windows Forms přehled](../../../../docs/framework/winforms/security-in-windows-forms-overview.md).  
  
 Nastavení se ukládají jako fragmenty XML v konfiguračních souborech. Nastavení rozsahu aplikace jsou reprezentované pomocí `<application.Settings>` elementu a obecně jsou umístěny v *aplikace*. exe.config, kde *aplikace* je název hlavního spustitelného souboru. Nastavení rozsahu uživatele jsou reprezentované pomocí `<userSettings>` elementu a jsou umístěny v *uživatele*.config, kde *uživatele* je uživatelské jméno osoby, které jsou aktuálně spuštěna aplikace. Je nutné nasadit *aplikace*. exe.config souboru s vaší aplikací; nastavení architektura vytvoří *uživatele*soubory .config na vyžádání první času aplikace uloží nastavení pro tohoto uživatele. Můžete také definovat `<userSettings>` blokovat v rámci *aplikace*. exe.config zadat výchozí hodnoty pro nastavení rozsahu uživatele.  
  
 Vlastní ovládací prvky můžete také uložit vlastní nastavení implementací <xref:System.Configuration.IPersistComponentSettings> rozhraní, které zpřístupňuje <xref:System.Configuration.IPersistComponentSettings.SaveSettings%2A> metoda. Windows Forms <xref:System.Windows.Forms.ToolStrip> ovládací prvek implementuje toto rozhraní Uložit pozici panelů nástrojů a položek panelu nástrojů mezi relacemi aplikace. Další informace o vlastní ovládací prvky a nastavení aplikací, najdete v tématu [nastavení aplikace pro vlastní ovládací prvky](../../../../docs/framework/winforms/advanced/application-settings-for-custom-controls.md).  
  
## <a name="limitations-of-application-settings"></a>Omezení nastavení aplikace  
 Nastavení aplikace nelze použít v nespravované aplikaci, která hostuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Nastavení nebude fungovat v těchto prostředích, jako Visual Studio doplňků, C++ pro Microsoft Office, řídit hostování v aplikaci Internet Explorer nebo doplňky Microsoft Outlook a projekty.  
  
 Momentálně nelze vázat na některé vlastnosti v systému Windows Forms. Nejdůležitějším příkladem je <xref:System.Windows.Forms.Form.ClientSize%2A> vlastnost jako vazba této vlastnosti by způsobit nepředvídatelné chování za běhu. Tyto problémy můžete vyřešit obvykle tak ukládání a načítání tato nastavení prostřednictvím kódu programu.  
  
 Nastavení aplikace nemá žádné předdefinované zařízení pro šifrování informací automaticky. Měli byste nikdy uložit informace týkající se zabezpečení, jako jsou databáze hesla ve formátu prostého textu. Pokud chcete uložit tyto citlivé informace, jako vývojář aplikací jste zodpovědní za tak, že je bezpečné. Pokud chcete uložit připojovací řetězce, doporučujeme použít integrované zabezpečení systému Windows a není pevně kódováno hesla uchýlit k adrese URL. Další informace najdete v tématu [zabezpečení přístupu kódu a ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md).  
  
## <a name="getting-started-with-application-settings"></a>Začínáme s nastavení aplikace  
 Pokud používáte Visual Studio, můžete definovat nastavení v Návrháři formulářů Windows pomocí **(ApplicationSettings)** vlastnost **vlastnosti** okno. Když definujete nastavení tímto způsobem, Visual Studio automaticky vytvoří vlastní spravovaná obálka třídu, která přidruží každé nastavení vlastnosti třídy. Visual Studio také postará nastavení vazby na vlastnost ve formuláři nebo ovládací prvek, aby nastavení ovládacího prvku se automaticky obnoví, pokud jeho formulář se zobrazí a automaticky uloženy při zavření formuláře.  
  
 Pokud chcete podrobnější kontrolu nad nastavení, můžete definovat vlastní třídu obálky nastavení vlastních aplikací. To lze provést odvození třídy z <xref:System.Configuration.ApplicationSettingsBase>, přidání vlastnosti, která odpovídá pro každé nastavení a použití zvláštní atributů tyto vlastnosti. Podrobnosti o vytváření Obálka – třídy najdete v tématu [architektura nastavení aplikace](../../../../docs/framework/winforms/advanced/application-settings-architecture.md).  
  
 Můžete také <xref:System.Windows.Forms.Binding> třídy prostřednictvím kódu programu svázat nastavení s vlastnostmi formuláře a ovládací prvky.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.SettingsProvider>  
 <xref:System.Configuration.LocalFileSettingsProvider>  
 <xref:System.Configuration.IPersistComponentSettings>  
 [Postupy: Ověření nastavení aplikace](../../../../docs/framework/winforms/advanced/how-to-validate-application-settings.md)  
 [Správa nastavení aplikace (.NET)](http://msdn.microsoft.com/library/35254321-ad14-47d9-b8c6-39ab3203c5d9)  
 [Postupy: Čtení uživatelských nastavení při běhu pomocí C#](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)  
 [Použití nastavení aplikace a uživatelských nastavení](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [Architektura nastavení aplikace](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)  
 [Nastavení aplikace pro vlastní ovládací prvky](../../../../docs/framework/winforms/advanced/application-settings-for-custom-controls.md)

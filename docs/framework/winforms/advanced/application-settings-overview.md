---
title: Přehled nastavení aplikace
description: Přečtěte si o funkci nastavení aplikace model Windows Forms, například o tom, jak vytvořit a uložit data nastavení jménem vaší aplikace a uživatelů.
ms.date: 03/30/2017
f1_keywords:
- ApplicationsSettingsOverview
helpviewer_keywords:
- application settings [Windows Forms], about application settings
- dynamic properties
- user preferences [Windows Forms], tracking
ms.assetid: 0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc
ms.openlocfilehash: 864cab72b26ff7989c570347fb88b4009e7d705a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324213"
---
# <a name="application-settings-overview"></a>Přehled nastavení aplikace

Tento článek popisuje, jak vytvořit a uložit data nastavení jménem vaší aplikace a uživatelů.

 Funkce nastavení aplikace model Windows Forms umožňuje snadno vytvořit, Uložit a udržovat vlastní aplikace a uživatelské předvolby v klientském počítači. Pomocí model Windows Forms nastavení aplikace můžete ukládat nejen data aplikací, jako jsou databázové připojovací řetězce, ale také data specifická pro uživatele, jako jsou předvolby uživatelské aplikace. Pomocí sady Visual Studio nebo vlastního spravovaného kódu můžete vytvořit nová nastavení, přečíst si je z a zapsat je na disk, vytvořit jejich vazby k vlastnostem ve formulářích a ověřit data nastavení před načtením a uložením.

 Nastavení aplikace umožňuje vývojářům ukládat do své aplikace stav pomocí velmi malého vlastního kódu a je náhradou za dynamické vlastnosti v předchozích verzích .NET Framework. Nastavení aplikace obsahuje mnoho vylepšení pro dynamické vlastnosti, které jsou jen pro čtení, pozdní vazby a vyžadují více vlastního programování. Třídy dynamických vlastností byly uchovány v .NET Framework 2,0, ale jsou to pouze třídy prostředí, které dynamicky zabalí třídy nastavení aplikace.

## <a name="what-are-application-settings"></a>Co jsou nastavení aplikace?
 Vaše aplikace model Windows Forms budou často vyžadovat data, která jsou pro spuštění aplikace kritická, ale nechcete zahrnout přímo do kódu aplikace. Pokud vaše aplikace používá webovou službu nebo databázový server, můžete tyto informace uložit do samostatného souboru, abyste je mohli v budoucnu změnit, aniž by bylo třeba znovu kompilovat. Podobně můžou vaše aplikace vyžadovat ukládání dat, která jsou specifická pro aktuálního uživatele. Většina aplikací má například předvolby pro uživatele, které přizpůsobují vzhled a chování aplikace.

 Nastavení aplikace řeší obě požadavky tím, že poskytují snadný způsob, jak uložit nastavení s rozsahem aplikace i uživatele v klientském počítači. Pomocí sady Visual Studio nebo editoru kódu můžete definovat nastavení pro danou vlastnost zadáním jejího názvu, datového typu a oboru (aplikace nebo uživatel). Můžete dokonce umístit související nastavení do pojmenovaných skupin pro snazší použití a čitelnost. Po definování jsou tato nastavení trvalá a v době běhu se automaticky čtou do paměti. Připojitelná architektura umožňuje změnit mechanismus trvalosti, ale ve výchozím nastavení se použije místní systém souborů.

 Nastavení aplikace funguje tak, že uchovává data jako XML do různých konfiguračních souborů (. config), což odpovídá tom, zda se jedná o nastavení s rozsahem aplikace nebo uživatelem. Ve většině případů jsou nastavení s rozsahem aplikace jen pro čtení; vzhledem k tomu, že se jedná o informace o programu, obvykle je nebudete muset přepsat. Naproti tomu může být nastavení s rozsahem uživatele čtena a zapsána bezpečně za běhu, a to i v případě, že vaše aplikace běží v částečném vztahu důvěryhodnosti. Další informace o částečném vztahu důvěryhodnosti naleznete [v tématu Security in model Windows Forms Overview](../security-in-windows-forms-overview.md).

 Nastavení se ukládají jako fragmenty XML v konfiguračních souborech. Nastavení s rozsahem aplikace jsou reprezentována `<applicationSettings>` prvkem a obecně jsou umístěna do *aplikace*.exe.config, kde *aplikace* je název vašeho hlavního spustitelného souboru. Nastavení s rozsahem uživatele je reprezentované `<userSettings>` prvkem a je umístěno v souboru *User*. config, kde *uživatel* je uživatelské jméno osoby, která aktuálně spouští aplikaci. Musíte nasadit soubor.exe.config *aplikace* s vaší aplikací. Architektura nastavení vytvoří soubory *User*. config na vyžádání, když aplikace poprvé uloží nastavení pro daného uživatele. Můžete také definovat `<userSettings>` blok v rámci *aplikace*.exe.config a poskytnout tak výchozí hodnoty pro nastavení s rozsahem uživatele.

 Vlastní ovládací prvky mohou také uložit vlastní nastavení implementací <xref:System.Configuration.IPersistComponentSettings> rozhraní, které zpřístupňuje <xref:System.Configuration.IPersistComponentSettings.SaveSettings%2A> metodu. <xref:System.Windows.Forms.ToolStrip>Ovládací prvek model Windows Forms implementuje toto rozhraní, aby bylo možné uložit umístění panelů nástrojů a položek panelu nástrojů mezi relacemi aplikace. Další informace o vlastních ovládacích prvcích a nastaveních aplikace naleznete v tématu [nastavení aplikace pro vlastní ovládací prvky](application-settings-for-custom-controls.md).

## <a name="limitations-of-application-settings"></a>Omezení nastavení aplikace
 Nastavení aplikace nemůžete použít v nespravované aplikaci, která je hostitelem .NET Framework. Nastavení v těchto prostředích nebudou fungovat jako doplňky sady Visual Studio, C++ pro systém Microsoft Office, hostování ovládacích prvků v Internet Exploreru nebo doplňky a projekty aplikace Microsoft Outlook.

 V tuto chvíli nemůžete vytvořit vazby na některé vlastnosti v model Windows Forms. Nejvýraznějším příkladem je <xref:System.Windows.Forms.Form.ClientSize%2A> vlastnost, protože vazba na tuto vlastnost by způsobila nepředvídatelné chování v době běhu. Tyto problémy obvykle můžete obejít tak, že tato nastavení uložíte a načtete programově.

 Nastavení aplikace nemá k dispozici žádné integrované zařízení pro automatické šifrování informací. Nikdy byste neměli ukládat informace související se zabezpečením, jako jsou například hesla databáze, ve formátu prostého textu. Pokud chcete uložit takové důvěrné informace, je jako vývojář aplikace zodpovědný za zajištění zabezpečení. Pokud chcete uložit připojovací řetězce, doporučujeme použít integrované zabezpečení systému Windows a nemusíte ho používat k pevnému kódování hesla na adresu URL. Další informace najdete v tématu [zabezpečení přístupu kódu a ADO.NET](../../data/adonet/code-access-security.md).

## <a name="getting-started-with-application-settings"></a>Začínáme s nastavením aplikace
 Pokud používáte aplikaci Visual Studio, můžete definovat nastavení v rámci Návrhář formulářů pomocí vlastnosti **(ApplicationSettings)** v okně **vlastnosti** . Při definování nastavení tímto způsobem Visual Studio automaticky vytvoří vlastní spravovanou obálkovou třídu, která přidruží každé nastavení k vlastnosti Class. Visual Studio také postará o vazbu nastavení na vlastnost ve formuláři nebo ovládacím prvku tak, aby se nastavení ovládacího prvku automaticky obnovilo při zobrazení jeho formuláře a automaticky se uložilo při zavření formuláře.

 Pokud chcete podrobnější kontrolu nad nastavením, můžete definovat vlastní obálkovou třídu nastavení vlastní aplikace. To je provedeno odvozením třídy z <xref:System.Configuration.ApplicationSettingsBase> , přidáním vlastnosti, která odpovídá jednotlivým nastavením, a aplikováním speciálních atributů na tyto vlastnosti. Podrobnosti o vytváření obálkových tříd naleznete v tématu [Architektura nastavení aplikace](application-settings-architecture.md).

 Můžete také použít <xref:System.Windows.Forms.Binding> třídu k navázání nastavení do vlastností pro formuláře a ovládací prvky prostřednictvím kódu programu.

## <a name="see-also"></a>Viz také

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- <xref:System.Configuration.IPersistComponentSettings>
- [Postupy: Ověření nastavení aplikace](how-to-validate-application-settings.md)
- [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
- [Postupy: Čtení uživatelských nastavení při běhu pomocí C#](how-to-read-settings-at-run-time-with-csharp.md)
- [Použití nastavení aplikace a uživatelských nastavení](using-application-settings-and-user-settings.md)
- [Architektura nastavení aplikace](application-settings-architecture.md)
- [Nastavení aplikace pro vlastní ovládací prvky](application-settings-for-custom-controls.md)

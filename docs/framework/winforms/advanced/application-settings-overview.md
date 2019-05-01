---
title: Přehled nastavení aplikace
ms.date: 03/30/2017
f1_keywords:
- ApplicationsSettingsOverview
helpviewer_keywords:
- application settings [Windows Forms], about application settings
- dynamic properties
- user preferences [Windows Forms], tracking
ms.assetid: 0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc
ms.openlocfilehash: b603e81a342652a6639f54a78fb998cda5fdc35a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972416"
---
# <a name="application-settings-overview"></a>Přehled nastavení aplikace
Toto téma popisuje, jak vytvářet a ukládat nastavení data jménem aplikace i vaše uživatele.  
  
 Funkce nastavení aplikace Windows Forms umožňuje snadno vytvářet, ukládat a spravovat vlastní aplikace a preference uživatelů v klientském počítači. S nastavením aplikace Windows Forms lze uložit pouze data aplikací, například databázové připojovací řetězce, ale také uživatelská data, jako je například uživatelova aplikace. Pomocí sady Visual Studio nebo vlastní spravovaný kód, můžete vytvořit nové nastavení, přečtěte si je z a zapisovat na disku a svázat ho s vlastnostmi formuláře a ověřit nastavení data před načítání a ukládání.  
  
 Nastavení aplikace umožňuje vývojářům pro uložení stavu ve svých aplikacích pomocí velmi málo vlastního kódu a je náhradou za dynamické vlastnosti v předchozích verzích [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Nastavení aplikace obsahuje mnoho vylepšení přes dynamické vlastnosti, které jsou jen pro čtení, s pozdní vazbou a vyžadovat další vlastní programování. Dynamické vlastnosti třídy mají byla zachována ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], ale jsou právě třídy prostředí, které dynamicky balí třídy nastavení aplikace.  
  
## <a name="what-are-application-settings"></a>Co jsou nastavení aplikace?  
 Vaše aplikace Windows Forms se často vyžadují data, která jsou kritická pro spuštění aplikace, ale který nechcete zahrnout přímo v kódu vaší aplikace. Pokud vaše aplikace používá webovou službu nebo databázový server, můžete k ukládání příslušných informací v samostatném souboru, takže můžete v budoucnu ho změnit bez opětovné kompilace. Podobně vaše aplikace můžou vyžadovat ukládání dat, která je specifická pro aktuálního uživatele. Většina aplikací, například má uživatelské předvolby, přizpůsobte vzhled a chování aplikace.  
  
 Aplikace nastavení adresy obou musí tím, že poskytuje snadný způsob, jak ukládat nastavení oboru aplikace i s rozsahem uživatele na klientském počítači. Pomocí sady Visual Studio nebo editor kódu, definovat nastavení pro danou vlastnost tak, že zadáte jeho název, datový typ a obor (aplikaci nebo uživatele). Dokonce můžete umístit do pojmenované skupiny pro použití snadněji a čitelnost související nastavení. Po definování, tato nastavení jsou trvalé a automaticky číst zpět do paměti v době běhu. Připojitelná architektura umožňuje mechanismu trvalosti změnit, ale ve výchozím nastavení, je použít místní systém souborů.  
  
 Nastavení aplikace funguje tak, že trvalá data ve formátu XML pro jinou konfiguraci (.config) soubory odpovídající Určuje, zda nastavení je aplikace s rozsahem nebo rozsahem uživatele. Ve většině případů nastavení oboru aplikace jsou jen pro čtení; protože jsou informace o programu, obvykle nemusíte jejich přepsání. Naopak nastavení rozsahu uživatele může číst a zapsat bezpečné v době běhu, i v případě, že vaše aplikace běží v částečném vztahu důvěryhodnosti. Další informace o částečné důvěryhodnosti, naleznete v tématu [Přehled zabezpečení ve Windows Forms](../security-in-windows-forms-overview.md).  
  
 Nastavení se ukládají jako fragmenty XML v konfiguračních souborech. Nastavení oboru aplikace jsou reprezentovány `<application.Settings>` prvek a jsou obecně umístěny do *aplikace*. exe.config, kde *aplikace* je název hlavního spustitelného souboru. Nastavení rozsahu uživatele jsou reprezentovány `<userSettings>` element a jsou umístěny v *uživatele*.config, kde *uživatele* je uživatelské jméno osoby, které jsou aktuálně spuštěné aplikace. Je nutné nasadit *aplikace*. exe.config soubor s vaší aplikací; nastavení architektura vytvoří *uživatele*souborech .config na vyžádání první čas aplikace ukládá nastavení pro tohoto uživatele. Můžete také definujte `<userSettings>` blokovat v rámci *aplikace*. exe.config zadat výchozí hodnoty pro nastavení rozsahu uživatele.  
  
 Vlastní ovládací prvky můžete také uložit své vlastní nastavení implementací <xref:System.Configuration.IPersistComponentSettings> rozhraní, která zveřejňuje <xref:System.Configuration.IPersistComponentSettings.SaveSettings%2A> metody. Windows Forms <xref:System.Windows.Forms.ToolStrip> ovládací prvek implementuje toto rozhraní se uložit pozici panelů nástrojů a nástrojů položek mezi jednotlivými relacemi aplikace. Další informace o vlastních ovládacích prvků a nastavení aplikací, najdete v části [nastavení aplikace pro vlastní ovládací prvky](application-settings-for-custom-controls.md).  
  
## <a name="limitations-of-application-settings"></a>Omezení nastavení aplikace  
 Nastavení aplikace nelze použít v nespravované aplikaci, která hostuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Nastavení nebude fungovat v těchto prostředích, jako Visual Studio doplňků, C++ pro systém Microsoft Office, řídit hostování v aplikaci Internet Explorer nebo doplňky aplikace Microsoft Outlook a projekty.  
  
 Momentálně nelze vázat na některé vlastnosti v modelu Windows Forms. Nejdůležitějším příkladem je <xref:System.Windows.Forms.Form.ClientSize%2A> vlastnosti, jako vazbu k této vlastnosti by způsobit nepředvídatelné chování za běhu. Tyto potíže obvykle můžete obejít tak ukládání a načítání tato nastavení programově.  
  
 Nastavení aplikace nemá žádné předdefinované zařízení pro šifrování informací automaticky. Nikdy byste měli uložit informace související se zabezpečením, jako jsou databáze hesla ve formátu prostého textu. Pokud chcete uložit tyto citlivé informace, jako vývojář aplikace zodpovídáte za to, že je zabezpečení. Pokud chcete uložit připojovací řetězce, doporučujeme použít integrované zabezpečení Windows a ne se uchýlíte k pevnému zakódování hesel do adresy URL. Další informace najdete v tématu [zabezpečení přístupu kódu a ADO.NET](../../data/adonet/code-access-security.md).  
  
## <a name="getting-started-with-application-settings"></a>Začínáme s nastavením aplikace  
 Pokud používáte sadu Visual Studio, můžete definovat nastavení v Návrháři formulářů Windows pomocí **(ApplicationSettings)** vlastnost **vlastnosti** okna. Při definování nastavení tímto způsobem, Visual Studio automaticky vytvoří vlastní spravované obálkovou třídu, která přidruží každé nastavení vlastnosti třídy. Visual Studio také se postará o nastavení vazby na vlastnost formuláře nebo ovládacího prvku tak, aby při jeho formulář se zobrazí a automaticky uloženy při uzavření formuláře se automaticky obnoví nastavení ovládacího prvku.  
  
 Pokud chcete mít podrobnější kontrolu nad nastavení, můžete definovat vlastní třídu obálky nastavení vlastních aplikací. Toho lze dosáhnout odvození třídy z <xref:System.Configuration.ApplicationSettingsBase>, přidání vlastnosti, která odpovídá každé nastavení a použití speciální atributy pro tyto vlastnosti. Podrobnosti o vytvoření obálkové třídy najdete v tématu [architektura nastavení aplikace](application-settings-architecture.md).  
  
 Můžete také použít <xref:System.Windows.Forms.Binding> třídy prostřednictvím kódu programu vytvořit vazbu nastavení s vlastnostmi formuláře a ovládací prvky.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- <xref:System.Configuration.IPersistComponentSettings>
- [Postupy: Ověření nastavení aplikace](how-to-validate-application-settings.md)
- [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
- [Postupy: Čtení uživatelských nastavení při běhu pomocíC#](how-to-read-settings-at-run-time-with-csharp.md)
- [Použití nastavení aplikace a uživatelských nastavení](using-application-settings-and-user-settings.md)
- [Architektura nastavení aplikace](application-settings-architecture.md)
- [Nastavení aplikace pro vlastní ovládací prvky](application-settings-for-custom-controls.md)

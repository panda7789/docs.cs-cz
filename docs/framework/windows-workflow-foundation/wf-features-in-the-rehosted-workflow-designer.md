---
title: Podpora nových funkcí Workflow Foundation 4.5 v Návrháři postupu provádění se změněným hostováním
ms.date: 03/30/2017
ms.assetid: 1a4a4038-d8e6-41dd-99ea-93bd76286772
ms.openlocfilehash: 2b893fede30606789c82a64a19fa368e3fd74c4d
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74142064"
---
# <a name="support-for-new-workflow-foundation-45-features-in-the-rehosted-workflow-designer"></a>Podpora nových funkcí Workflow Foundation 4.5 v Návrháři postupu provádění se změněným hostováním
Programovací model Windows Workflow Foundation (WF) v .NET Framework 4,5 představil mnoho nových funkcí, včetně několika vylepšení prostředí návrháře pracovních postupů. Toto téma obsahuje podrobnosti o tom, které z těchto funkcí jsou podporovány v Návrháři s příponou a které nejsou aktuálně podporovány.

> [!NOTE]
> Seznam všech nových funkcí programovací model Windows Workflow Foundation (WF) zavedených v .NET Framework 4,5, včetně těch, které nesouvisí s opětovným hostováním návrháře, najdete v tématu [novinky v programovací model Windows Workflow Foundation v rozhraní .net 4,5](whats-new-in-wf-in-dotnet.md).

## <a name="activities"></a>Aktivity
 Integrovaná knihovna aktivit obsahuje nové aktivity a nové funkce pro existující aktivity. Všechny tyto nové aktivity jsou podporovány v novém hostovaném návrháři. Další informace o těchto nových aktivitách najdete v části věnované [aktivitám](whats-new-in-wf-in-dotnet.md#BKMK_NewActivities) [v tématu Co je nového v programovací model Windows Workflow Foundation v rozhraní .NET 4,5](whats-new-in-wf-in-dotnet.md).

## <a name="c-expressions"></a>Výrazy C#
 Před .NET Framework 4,5 se všechny výrazy v pracovních postupech daly zapisovat jenom v Visual Basic. V .NET Framework 4,5 jsou výrazy Visual Basic používány pouze pro projekty vytvořené pomocí Visual Basic. Vizuální C# projekty se nyní C# používají pro výrazy. Při vytváření pracovních postupů v aplikaci Visual Studio 2012 je k C# dispozici plně funkční editor výrazů, které nabízí funkce, jako je například zvýrazňování gramatiky a IntelliSense. C#projekty pracovního postupu vytvořené v předchozích verzích, které používají Visual Basic výrazy budou fungovat i nadále.

> [!WARNING]
> C#výrazy nejsou podporovány v rehostujícím návrháři.

## <a name="new-designer-capabilities"></a>Nové možnosti návrháře

### <a name="designer-search"></a>Hledání návrháře
 Funkce [rychlého hledání](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) a [hledání v souborech](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) zavedené s .NET Framework 4,5 nejsou podporované v novém hostovaném návrháři. Hledání `Toolbox` je podporováno v přehostujícím návrháři. Další informace o těchto funkcích najdete v tématu [hledání návrháře](whats-new-in-wf-in-dotnet.md#BKMK_DesignerSearch).

> [!WARNING]
> [Rychlé hledání](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) a [hledání v souborech](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) nejsou podporovány v přehostujícím návrháři.

### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a>Odstranit položku kontextové nabídky v Návrháři proměnných a argumentů
 V .NET Framework 4 lze proměnné a argumenty odstranit pouze v Návrháři pomocí klávesnice. Počínaje .NET Framework 4,5 lze proměnné a argumenty odstranit pomocí místní nabídky. Tato funkce je podporována v rehostujícím návrháři.

 Následující snímek obrazovky ukazuje kontextovou nabídku návrháře proměnných a argumentů.

 ![Kontextová nabídka návrháře proměnných a argumentů](./media/wf-features-in-the-rehosted-workflow-designer/designer-context-menu.png)

### <a name="auto-surround-with-sequence"></a>Automaticky uzavřít sekvencí
 Vzhledem k tomu, že pracovní postup nebo určité aktivity kontejneru (například <xref:System.Activities.Statements.NoPersistScope>) můžou obsahovat jenom jednu aktivitu těla, přidání druhé aktivity, která vývojář vyžádala k odstranění první aktivity, přidání aktivity <xref:System.Activities.Statements.Sequence> a přidání obou aktivit do aktivity sekvence. Počínaje .NET Framework 4,5 se při přidávání druhé aktivity na plochu návrháře automaticky vytvoří `Sequence` aktivita, která zabalí obě aktivity. Tato funkce je podporována v rehostujícím návrháři.

 Následující snímek obrazovky ukazuje `WriteLine` aktivitu v `Body` `NoPersistScope`.

 ![Aktivita WriteLine v těle aktivity oboru NoPersistScope](./media/wf-features-in-the-rehosted-workflow-designer/auto-surround-write-line-activity.png)

 Následující snímek obrazovky ukazuje automaticky vytvořenou aktivitu `Sequence` v `Body` při prvním vyřazení druhého `WriteLine` pod první.

 ![Automaticky vytvořená sekvence v těle oboru nopersistscopeu.](./media/wf-features-in-the-rehosted-workflow-designer/auto-surround-sequence-activity.png)

### <a name="pan-mode"></a>Režim posouvání
 Chcete-li snadněji procházet rozsáhlý pracovní postup v návrháři, můžete povolit režim posouvání, který vývojářům umožňuje kliknout a přetáhnout, aby přesunul viditelnou část pracovního postupu, místo aby bylo nutné používat posuvníky. Tlačítko pro aktivaci režimu posunu je v pravém dolním rohu návrháře. Tato funkce je podporována v rehostujícím návrháři.

 Na následujícím snímku obrazovky vidíte tlačítko posouvání, které se nachází v pravém dolním rohu návrháře pracovních postupů.

 ![Tlačítko posouvání zvýrazněné v Návrháři postupu.](./media/wf-features-in-the-rehosted-workflow-designer/pan-button-workflow-designer.png)

 K posouvání návrháře pracovních postupů můžete použít také prostřední tlačítko myši nebo MEZERNÍK.

### <a name="multi-select"></a>Vícenásobný výběr
 Najednou lze vybrat více aktivit, buď přetažením obdélníku kolem nich (když režim posouvání není povolen), nebo podržením klávesy CTRL a kliknutím na požadované aktivity jednu po druhé. Tato funkce je podporována v rehostujícím návrháři.

 V Návrháři lze také přetáhnout a vyřadit více výběrů aktivit a lze je také interagovat pomocí místní nabídky.

### <a name="outline-view-of-workflow-items"></a>zobrazení Osnova položek pracovního postupu
 Aby bylo možné hierarchické pracovní postupy snáze procházet, jsou komponenty pracovního postupu zobrazeny v zobrazení osnovy ve stylu stromu. Zobrazení Osnova se zobrazí v zobrazení **Osnova dokumentu** . Chcete-li otevřít toto zobrazení v aplikaci Visual Studio, vyberte v horní nabídce možnost **zobrazení**, **ostatní okna**, **Osnova dokumentu**nebo stiskněte klávesovou zkratku CTRL W, U. Kliknutím na uzel v zobrazení osnovy přejdete na odpovídající aktivitu v Návrháři pracovních postupů a zobrazení osnovy se aktualizuje tak, aby se zobrazily aktivity vybrané v návrháři. Tato funkce je podporována v rehostujícím návrháři.

 Následující snímek obrazovky dokončeného pracovního postupu z [kurzu Začínáme](getting-started-tutorial.md) ukazuje zobrazení osnovy s sekvenčním pracovním postupem.

 ![Snímek obrazovky se zobrazením osnovy a sekvenčním pracovním postupem v aplikaci Visual Studio](./media/wf-features-in-the-rehosted-workflow-designer/outline-view-in-workflow-designer.jpg)

### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a>Větší kontrola nad viditelností položek v panelu prostředí a v záhlaví
 V přehostujícím Návrháři nemusí některé standardní ovládací prvky uživatelského rozhraní mít význam pro daný pracovní postup a mohou být vypnuty. V .NET Framework 4 se toto přizpůsobení podporuje jenom na panelu prostředí v dolní části návrháře. V .NET Framework 4,5 lze upravit zobrazení položek hlaviček prostředí v horní části návrháře nastavením <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> pomocí příslušné <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> hodnoty.

### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a>Automatické připojení a automatické vkládání v pracovních postupech vývojových diagramů a stavových počítačů
 V .NET Framework 4 bylo nutné přidat připojení mezi uzly v pracovním postupu vývojového diagramu ručně. V uzlech .NET Framework 4,5 mají uzly vývojového a stavového počítače automaticky propojené body, které se zobrazí při přetažení aktivity z panelu nástrojů na plochu návrháře. Vyřazení aktivity v jednom z těchto bodů automaticky přidá aktivitu spolu s potřebným připojením.

 Následující snímek obrazovky ukazuje body připojení, které se zobrazí při přetažení aktivity ze sady nástrojů.

 ![Počáteční uzel vývojového diagramu znázorňující body automatického připojení](./media/wf-features-in-the-rehosted-workflow-designer/auto-connect-points-start-node.png)

 Aktivity lze také přetáhnout na propojení mezi uzly vývojového diagramu a stavy a automaticky tak vkládat uzel mezi dva ostatní uzly. Na následujícím snímku obrazovky vidíte zvýrazněný spojovací řádek, kde je možné aktivity přetáhnout z panelu nástrojů a vyřadit.

 ![Automatický vložení popisovače pro vyřazování aktivit](./media/wf-features-in-the-rehosted-workflow-designer/auto-insert-connecting-line.png)

 Automatické připojení a automatické vkládání jsou podporovány v přehostujícím návrháři.

### <a name="designer-annotations"></a>Poznámky návrháře
 Aby bylo možné vyvíjet větší pracovní postupy, Návrhář nyní podporuje přidávání poznámek, které pomáhají sledovat proces návrhu. Anotace lze přidat k aktivitám, stavům, uzlům vývojového diagramu, proměnným a argumentům. Následující snímek obrazovky ukazuje místní nabídku, která se používá k přidání poznámek do návrháře.

 ![Snímek obrazovky, který zobrazuje nabídku pro přidávání zápisů.](./media/wf-features-in-the-rehosted-workflow-designer/designer-annotations-context-menu.png)

 Poznámky návrháře jsou podporovány v rehostujícím návrháři.

### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a>Definování a využívání objektů ActivityDelegate v Návrháři
 Aktivity v .NET Framework 4 používaly <xref:System.Activities.ActivityDelegate> objektů k vystavování bodů spouštění, kdy mohou jiné části pracovního postupu spolupracovat s prováděním pracovního postupu, ale použití těchto bodů spuštění obvykle vyžaduje spravedlivé množství kódu. V této verzi můžou vývojáři definovat a využívat delegáty aktivity pomocí návrháře pracovních postupů. Další informace naleznete v tématu [How to: Define and spotřebovávají Delegates Activity Delegates in the Návrhář postupu provádění](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).

 Delegáti aktivit jsou podporováni v přehostujícím návrháři.

### <a name="build-time-validation"></a>Ověřování při sestavení
 V .NET Framework 4 se chyby ověření pracovního postupu nepočítají jako chyby sestavení během sestavování projektu pracovního postupu. To znamenalo, že sestavení projektu pracovního postupu může být úspěšné i v případě, že došlo k chybám ověření pracovního postupu. V .NET Framework 4,5 způsobí chyby ověření pracovního postupu selhání sestavení.

> [!WARNING]
> Ověřování v době sestavení není v přehostujícím návrháři podporováno.  
  
### <a name="design-time-background-validation"></a>Ověřování na pozadí v době návrhu  
 V .NET Framework 4 byly pracovní postupy ověřeny jako proces na popředí, což by mohlo potenciálně blokovat uživatelské rozhraní během složitých nebo časově náročných ověřovacích procesů. Ověření pracovního postupu teď probíhá na vlákně na pozadí, takže uživatelské rozhraní není blokované.  
  
 V případě opětovného hostování návrháře je podporováno ověřování na pozadí v době návrhu.  
  
### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a>Zobrazit stav umístěný v samostatném umístění v souborech XAML  
 V .NET Framework 4 jsou informace o stavu pracovního postupu uloženy v rámci souboru XAML v mnoha různých umístěních. To je nepraktické pro vývojáře, kteří chtějí přímo číst XAML, nebo psát kód pro odebrání informací o stavu zobrazení. V .NET Framework 4,5 jsou informace o stavu zobrazení v souboru XAML serializovány jako samostatný prvek v souboru XAML.  Vývojáři můžou snadno vyhledat a upravit informace o stavu aktivity nebo stav zobrazení úplně odebrat.  
  
 Tato funkce je podporována v Návrháři pracovního postupu pro opětovné hostování.  
  
### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a>Výslovný souhlas s funkcemi pracovního postupu 4,5 v přehostovaném návrháři  
 Aby se zachovala zpětná kompatibilita, některé nové funkce, které jsou součástí .NET Framework 4,5, nejsou ve výchozím nastavení v přehostujícím návrháři povolené. K tomu je potřeba zajistit, aby existující aplikace používající znovu hostujícího návrháře nebyly přerušeny aktualizací na nejnovější verzi. Chcete-li povolit nové funkce v novém hostovaném návrháři, buď nastavte <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> na ".NET Framework 4,5", nebo nastavte jednotlivé členy <xref:System.Activities.Presentation.DesignerConfigurationService> tak, aby umožňovaly jednotlivé funkce.  
  
## <a name="new-workflow-development-models"></a>Nové modely vývoje pracovního postupu  
 Kromě vývojových a sekvenčních vývojových modelů pracovních postupů tato verze zahrnuje pracovní postupy stavového počítače a služby pracovního postupu pro první kontrakt.  
  
### <a name="state-machine-workflows"></a>Pracovní postupy stavového stroje  
 Pracovní postupy stavového počítače byly představeny jako součást .NET Framework 4.0.1 ve verzi [Microsoft .NET Framework 4 Platform Update 1](https://go.microsoft.com/fwlink/?LinkID=215092). Tato aktualizace obsahuje několik nových tříd a aktivit, které vývojářům umožňují vytvářet pracovní postupy stavového počítače. Tyto třídy a aktivity byly aktualizovány pro .NET Framework 4,5. Aktualizace zahrnují:  
  
1. Možnost nastavovat zarážky na stavech  
  
2. Možnost Kopírovat a vkládat přechody v Návrháři pracovních postupů  
  
3. Podpora návrháře pro vytvoření přechodu na sdílené triggery  
  
4. Aktivity, které slouží k vytváření pracovních postupů stavového počítače, včetně: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>a <xref:System.Activities.Statements.Transition>  
  
 Následující snímek obrazovky ukazuje pracovní postup dokončeného stavu počítače z kroku [Začínáme kurzu](getting-started-tutorial.md) [Postup: vytvoření pracovního postupu stavového stroje](how-to-create-a-state-machine-workflow.md).  
  
 ![Obrázek zobrazující pracovní postup dokončeného stavového počítače.](./media/wf-features-in-the-rehosted-workflow-designer/complete-state-machine-workflow.jpg)  
  
 Další informace o vytváření pracovních postupů stavových počítačů najdete v tématu [pracovní postupy stavového stroje](state-machine-workflows.md). Pracovní postupy stavového stroje jsou podporovány v rehostujícím návrháři.  
  
### <a name="contract-first-workflow-development"></a>Vývoj pracovního postupu prvního kontraktu  
 Nástroj pro vývoj pracovního postupu první smlouvy umožňuje vývojářům nejprve navrhnout kontrakt v kódu a pak s několika kliknutími v sadě Visual Studio automaticky vygenerovat šablonu aktivity v sadě nástrojů reprezentující jednotlivé operace. Tyto aktivity se pak použijí k vytvoření pracovního postupu, který implementuje operace definované smlouvou. Návrhář pracovního postupu ověří službu pracovního postupu, aby se zajistilo, že tyto operace budou implementované a že signatura pracovního postupu odpovídá signatuře smlouvy. Vývojář může také přidružit službu pracovního postupu ke kolekci implementovaných smluv. Další informace o vývoji služeb pracovních postupů prvního kontraktu najdete v tématu [Postupy: vytvoření služby pracovního postupu, která využívá stávající kontrakt služby](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).  
  
> [!WARNING]
> Vývoj pracovního postupu prvního kontraktu není v Návrháři pracovních postupů podporován.

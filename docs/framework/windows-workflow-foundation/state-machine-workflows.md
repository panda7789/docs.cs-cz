---
title: Pracovní postupy stavového stroje
ms.date: 03/30/2017
ms.assetid: 344caacd-bf3b-4716-bd5a-eca74fc5a61d
ms.openlocfilehash: e27b9bdc43ec13e90325f5e709c5c97758daa58c
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710913"
---
# <a name="state-machine-workflows"></a>Pracovní postupy stavového stroje
Stavový počítač je dobře známé paradigma pro vývoj programů. K sestavování stavových pracovních postupů je možné použít aktivitu <xref:System.Activities.Statements.StateMachine> společně s <xref:System.Activities.Statements.State>, <xref:System.Activities.Statements.Transition>a dalšími aktivitami. Toto téma poskytuje přehled o vytváření pracovních postupů stavových počítačů.  
  
## <a name="state-machine-workflow-overview"></a>Přehled pracovního postupu stavového stroje  
 Pracovní postupy stavového počítače poskytují styl modelování, pomocí kterého můžete modelovat svůj pracovní postup způsobem řízeným událostmi. Aktivita <xref:System.Activities.Statements.StateMachine> obsahuje stavy a přechody, které tvoří logiku stavového počítače, a lze je použít kdekoli, kde lze použít aktivitu. V modulu runtime stavového stroje je několik tříd:  
  
- <xref:System.Activities.Statements.StateMachine>  
  
- <xref:System.Activities.Statements.State>  
  
- <xref:System.Activities.Statements.Transition>  
  
 Chcete-li vytvořit pracovní postup stavového stroje, jsou do aktivity <xref:System.Activities.Statements.StateMachine> přidány stavy a k řízení toku mezi stavy se používají přechody. Následující snímek obrazovky popisuje, jak v [kurzu Začínáme](getting-started-tutorial.md) [vytvořit pracovní postup stavového stroje](how-to-create-a-state-machine-workflow.md), zobrazuje pracovní postup stavového stroje se třemi stavy a třemi přechody. **Inicializační cíl** je počáteční stav a představuje první stav v pracovním postupu. To je určeno řádkem, který je z **počátečního** uzlu od začátku. Konečný stav pracovního postupu má název **FinalState**a představuje bod, ve kterém byl pracovní postup dokončen.  
  
 ![Obrázek zobrazující pracovní postup dokončeného stavového počítače.](./media/state-machine-workflows/complete-state-machine-workflow.jpg)  
  
 Pracovní postup stavového stroje musí mít pouze jeden počáteční stav a alespoň jeden konečný stav. Každý stav, který není konečným stavem, musí mít alespoň jeden přechod. V následujících částech jsou pokryty vytváření a konfigurace stavů a přechodů.  
  
## <a name="creating-and-configuring-states"></a>Vytváření a konfigurace stavů  
 <xref:System.Activities.Statements.State> představuje stav, ve kterém může být Stavový počítač v. Chcete-li přidat <xref:System.Activities.Statements.State> do pracovního postupu, přetáhněte návrháře aktivity **stavu** z části **Stavový počítač** v **panelu nástrojů** a přetáhněte jej na <xref:System.Activities.Statements.StateMachine>ovou aktivitu na Návrhář postupu provádění ploše systému Windows.  
  
 ![Snímek obrazovky oddílu Stavový počítač v sadě nástrojů](./media/state-machine-workflows/state-machine-section-toolbox.jpg)  
  
 Chcete-li konfigurovat stav jako **počáteční**, klikněte pravým tlačítkem myši na stav a vyberte možnost **nastavit jako počáteční stav**. Kromě toho, pokud neexistuje aktuální počáteční stav, lze počáteční stav označit přetažením čáry z **počátečního** uzlu v horní části pracovního postupu do požadovaného stavu. Když se aktivita <xref:System.Activities.Statements.StateMachine> do návrháře pracovních postupů přeruší, je předem nakonfigurovaná s počátečním stavem s názvem **State1**. Pracovní postup stavového stroje musí mít pouze jeden počáteční stav.  
  
 Stav, který představuje ukončovací stav ve stavovém počítači, se nazývá konečný stav. Konečný stav je stav, který má vlastnost <xref:System.Activities.Statements.State.IsFinal%2A> nastavenou na `true`, nemá žádnou <xref:System.Activities.Statements.State.Exit%2A> aktivitu a z něj pocházejí žádné přechody. Chcete-li do pracovního postupu přidat konečný stav, přetáhněte návrháře aktivity **FinalState** z oddílu **Stavový počítač** v **panelu nástrojů** a přetáhněte jej na <xref:System.Activities.Statements.StateMachine>ovou aktivitu na ploše systému Windows Návrhář postupu provádění. Pracovní postup stavového stroje musí mít alespoň jeden konečný stav.  
  
### <a name="configuring-entry-and-exit-actions"></a>Konfigurace akcí vstupu a výstupu  
 Stav může mít <xref:System.Activities.Statements.State.Entry%2A> a akci <xref:System.Activities.Statements.State.Exit%2A>. (Stav nakonfigurovaný jako konečný stav může mít jenom akci položky). Když instance pracovního postupu vstoupí do stavu, spustí se všechny aktivity v akci vstupu. Po dokončení akce zadání se naplánují aktivační události pro přechody stavu. Když je potvrzen přechod do jiného stavu, jsou provedeny aktivity v akci ukončení, i když se změní stav zpět do stejného stavu. Po dokončení akce ukončit se aktivity v akci přechodu spustí a pak se nový stav převede na a naplánují se jeho akce vstupu.  
  
> [!NOTE]
> Při ladění pracovního postupu stavového stroje můžete zarážky umístit do aktivity kořenového stavového počítače a stavy v pracovním postupu stavového stroje. Zarážky se nedají umístit přímo na přechody, ale můžou se umístit na všechny aktivity obsažené v rámci stavů a přechodů.  
  
## <a name="creating-and-configuring-transitions"></a>Vytváření a konfigurace přechodů  
 Všechny stavy musí mít alespoň jeden přechod, s výjimkou konečného stavu, který nesmí mít žádné přechody. Přechody mohou být přidány po přidání stavu do pracovního postupu stavového stroje, nebo mohou být vytvořeny, protože stav je vyřazen.  
  
 Chcete-li přidat <xref:System.Activities.Statements.State> a vytvořit přechod v jednom kroku, přetáhněte aktivitu **stavu** z části **Stavový počítač** v **sadě nástrojů** a umístěte ji do jiného stavu v Návrháři postupu. Když je přetažené <xref:System.Activities.Statements.State> nad jiným <xref:System.Activities.Statements.State>, zobrazí se kolem ostatních <xref:System.Activities.Statements.State>čtyři trojúhelníky. Pokud je <xref:System.Activities.Statements.State> přehozena na jeden ze čtyř trojúhelníků, přidá se do stavového počítače a ze zdrojového <xref:System.Activities.Statements.State> se vytvoří přechod na vyřazený cílový <xref:System.Activities.Statements.State>. Další informace najdete v tématu [Přechod k Návrháři aktivit](/visualstudio/workflow-designer/transition-activity-designer).  
  
 Chcete-li vytvořit přechod po přidání stavu, existují dvě možnosti. První možností je přetáhnout stav z plochy návrháře pracovního postupu a najeďte ho na stávající stav a umístit ho na jeden z bodů odkládacích souborů. To je velmi podobné metodě popsané v předchozí části. Můžete také umístit ukazatel myši na požadovaný zdrojový stav a přetáhnout čáru do požadovaného cílového stavu.  
  
> [!NOTE]
> Jeden stav stavového počítače může mít až 76 přechodů vytvořených pomocí návrháře pracovních postupů. Omezení přechodů pro stav pracovních postupů vytvořených mimo návrháře je omezeno pouze systémovými prostředky.  
  
 Přechod může mít <xref:System.Activities.Statements.Transition.Trigger%2A>, <xref:System.Activities.Statements.Transition.Condition%2A>a <xref:System.Activities.Statements.Transition.Action%2A>. <xref:System.Activities.Statements.Transition.Trigger%2A> přechodu se naplánuje, když je dokončená akce <xref:System.Activities.Statements.State.Entry%2A> stavu zdroje přechodu. <xref:System.Activities.Statements.Transition.Trigger%2A> je typicky aktivita, která čeká na výskyt určitého typu události, ale může to být jakákoli aktivita nebo žádná aktivita. Po dokončení aktivity <xref:System.Activities.Statements.Transition.Trigger%2A> se vyhodnotí <xref:System.Activities.Statements.Transition.Condition%2A>, pokud je k dispozici. Pokud neexistují žádné aktivity <xref:System.Activities.Statements.Transition.Trigger%2A>, <xref:System.Activities.Statements.Transition.Condition%2A> se hned vyhodnotí. Pokud je podmínka vyhodnocena jako `false`, přechod je zrušen a aktivita <xref:System.Activities.Statements.Transition.Trigger%2A> pro všechny přechody ze stavu bude přeplánována. Pokud jsou k dispozici jiné přechody, které sdílejí stejný zdrojový stav jako aktuální přechod, jsou tyto akce <xref:System.Activities.Statements.Transition.Trigger%2A> také zrušeny a přeplánovány. Pokud se <xref:System.Activities.Statements.Transition.Condition%2A> vyhodnotí jako `true`nebo neexistuje žádná podmínka, je provedena akce <xref:System.Activities.Statements.State.Exit%2A> zdrojového stavu a následně se spustí <xref:System.Activities.Statements.Transition.Action%2A> přechodu. Po dokončení <xref:System.Activities.Statements.Transition.Action%2A> řízení předává do **cílového** stavu  
  
 Přechody, které sdílí společnou aktivační událost, se označují jako přechody sdílených triggerů. Každý přechod ve skupině přechodů sdílených triggerů má stejný Trigger, ale jedinečný <xref:System.Activities.Statements.Transition.Condition%2A> a akci. Chcete-li do přechodu přidat další akce a vytvořit sdílený přechod, klikněte na kroužek, který indikuje začátek požadovaného přechodu a přetáhněte ho do požadovaného stavu. Nový přechod bude sdílet stejný Trigger jako počáteční přechod, ale bude mít jedinečnou podmínku a akci. Sdílené přechody je také možné vytvořit v Návrháři přechodu kliknutím na **přidat přechod sdílené triggery** v dolní části návrháře přechodu a pak výběrem požadovaného cílového stavu z rozevíracího seznamu **dostupné stavy pro připojení** .  
  
> [!NOTE]
> Všimněte si, že pokud je <xref:System.Activities.Statements.Transition.Condition%2A> přechodu vyhodnocen jako `False` (nebo všechny podmínky přechodu sdílené triggery vyhodnoceny na `False`), přechod nebude proveden a všechny aktivační události pro všechny přechody ze stavu budou přeplánovány.  
  
 Další informace o vytváření pracovních postupů stavových počítačů najdete v tématu [Postupy: vytvoření pracovního postupu stavového stroje](how-to-create-a-state-machine-workflow.md), [návrháře aktivit StateMachine](/visualstudio/workflow-designer/statemachine-activity-designer), návrháře aktivity [stavu](/visualstudio/workflow-designer/state-activity-designer), [Návrháře aktivity FinalState](/visualstudio/workflow-designer/finalstate-activity-designer)a [Návrháře přechodu aktivit](/visualstudio/workflow-designer/transition-activity-designer).  
  
## <a name="state-machine-terminology"></a>Terminologie stavového stroje  
 Tato část definuje slovník stavového počítače použitý v rámci tohoto tématu.  
  
 Stát  
 Jednotka Basic, která vytváří Stavový počítač. Stavový počítač může být v každém okamžiku v jednom stavu.  
  
 Akce vstupu  
 Aktivita spuštěná při vstupu do stavu  
  
 Akce ukončení  
 Aktivita spuštěná při ukončování stavu  
  
 Transition  
 Směrná relace mezi dvěma stavy, které představují kompletní odpověď stavového počítače na výskyt události konkrétního typu.  
  
 Sdílený přechod  
 Přechod, který sdílí stav zdroje a Trigger s jedním nebo více přechody, ale má jedinečnou podmínku a akci.  
  
 Aktivační událost  
 Spuštění aktivity, která způsobí, že dojde k přechodu.  
  
 Podmínka  
 Omezení, které se musí vyhodnotit, aby se `true` po triggeru, aby se přechod dokončil.  
  
 Akce přechodu  
 Aktivita, která se spustí při provádění určitého přechodu.  
  
 Podmíněný přechod  
 Přechod s explicitní podmínkou.  
  
 Samoobslužný přechod  
 Přechod, který je přepravován ze stavu do sebe samé.  
  
 Počáteční stav  
 Stav, který představuje počáteční bod stavového počítače.  
  
 Konečný stav  
 Stav, který představuje dokončení stavového počítače.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření pracovního postupu stavového stroje](how-to-create-a-state-machine-workflow.md)
- [Návrhář aktivity StateMachine](/visualstudio/workflow-designer/statemachine-activity-designer)
- [Návrhář aktivity State](/visualstudio/workflow-designer/state-activity-designer)
- [Návrhář aktivity FinalState](/visualstudio/workflow-designer/finalstate-activity-designer)
- [Návrhář aktivity Transition](/visualstudio/workflow-designer/transition-activity-designer)

---
title: Pracovní postupy stavového stroje
ms.date: 03/30/2017
ms.assetid: 344caacd-bf3b-4716-bd5a-eca74fc5a61d
ms.openlocfilehash: 7b655208f4cc8274cdc5a8dad68ff1fa9eaad5ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948989"
---
# <a name="state-machine-workflows"></a>Pracovní postupy stavového stroje
Stavový počítač je dobře známé paradigma pro vývoj programů. Aktivitu spolu s <xref:System.Activities.Statements.State> ,<xref:System.Activities.Statements.Transition>a další aktivity lze použít k sestavování pracovních postupů pro stavové zařízení. <xref:System.Activities.Statements.StateMachine> Toto téma poskytuje přehled o vytváření pracovních postupů stavových počítačů.  
  
## <a name="state-machine-workflow-overview"></a>Přehled pracovního postupu stavového stroje  
 Pracovní postupy stavového počítače poskytují styl modelování, pomocí kterého můžete modelovat svůj pracovní postup způsobem řízeným událostmi. <xref:System.Activities.Statements.StateMachine> Aktivita obsahuje stavy a přechody, které tvoří logiku stavového počítače a lze je použít kdekoli, kde lze použít aktivitu. V modulu runtime stavového stroje je několik tříd:  
  
- <xref:System.Activities.Statements.StateMachine>  
  
- <xref:System.Activities.Statements.State>  
  
- <xref:System.Activities.Statements.Transition>  
  
 Chcete-li vytvořit pracovní postup stavového stroje, jsou do <xref:System.Activities.Statements.StateMachine> aktivity přidány stavy a přechody se používají k řízení toku mezi stavy. Následující snímek obrazovky [popisuje postup v následujícím [kurzu Začínáme](getting-started-tutorial.md) : Vytvoření pracovního postupu](how-to-create-a-state-machine-workflow.md)stavového stroje zobrazuje pracovní postup stavového stroje se třemi stavy a třemi přechody. **Inicializační cíl** je počáteční stav a představuje první stav v pracovním postupu. To je určeno řádkem, který je z počátečního uzlu od začátku. Konečný stav pracovního postupu má název **FinalState**a představuje bod, ve kterém byl pracovní postup dokončen.  
  
 ![Obrázek zobrazující pracovní postup dokončeného stavového počítače.](./media/state-machine-workflows/complete-state-machine-workflow.jpg)  
  
 Pracovní postup stavového stroje musí mít pouze jeden počáteční stav a alespoň jeden konečný stav. Každý stav, který není konečným stavem, musí mít alespoň jeden přechod. V následujících částech jsou pokryty vytváření a konfigurace stavů a přechodů.  
  
## <a name="creating-and-configuring-states"></a>Vytváření a konfigurace stavů  
 <xref:System.Activities.Statements.State> Představuje stav, ve kterém může být Stavový počítač v. Chcete-li <xref:System.Activities.Statements.State> přidat do pracovního postupu, přetáhněte návrháře aktivity **stavu** z části **Stavový počítač** v [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] **panelu nástrojů** a přetáhněte jej <xref:System.Activities.Statements.StateMachine> na aktivitu na povrchu.  
  
 ![Snímek obrazovky oddílu Stavový počítač v sadě nástrojů](./media/state-machine-workflows/state-machine-section-toolbox.jpg)  
  
 Chcete-li konfigurovat stav jako **počáteční**, klikněte pravým tlačítkem myši na stav a vyberte možnost **nastavit jako počáteční stav**. Kromě toho, pokud neexistuje aktuální počáteční stav, lze počáteční stav označit přetažením čáry z počátečního uzlu v horní části pracovního postupu do požadovaného stavu. Když je aktivita vyřazena do návrháře pracovních postupů, je předem nakonfigurována s počátečním stavem s názvem **State1.** <xref:System.Activities.Statements.StateMachine> Pracovní postup stavového stroje musí mít pouze jeden počáteční stav.  
  
 Stav, který představuje ukončovací stav ve stavovém počítači, se nazývá konečný stav. Konečný stav je stav, který má <xref:System.Activities.Statements.State.IsFinal%2A> vlastnost nastavenou na `true`, nemá žádnou <xref:System.Activities.Statements.State.Exit%2A> aktivitu a z něj pocházejí žádné přechody. Chcete-li do pracovního postupu přidat konečný stav, přetáhněte návrháře aktivity **FinalState** z oddílu **Stavový počítač** v **sadě nástrojů** <xref:System.Activities.Statements.StateMachine> a přetáhněte jej [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] na aktivitu na povrchu. Pracovní postup stavového stroje musí mít alespoň jeden konečný stav.  
  
### <a name="configuring-entry-and-exit-actions"></a>Konfigurace akcí vstupu a výstupu  
 Stav může mít <xref:System.Activities.Statements.State.Entry%2A> <xref:System.Activities.Statements.State.Exit%2A> akci a. (Stav nakonfigurovaný jako konečný stav může mít jenom akci položky). Když instance pracovního postupu vstoupí do stavu, spustí se všechny aktivity v akci vstupu. Po dokončení akce zadání se naplánují aktivační události pro přechody stavu. Když je potvrzen přechod do jiného stavu, jsou provedeny aktivity v akci ukončení, i když se změní stav zpět do stejného stavu. Po dokončení akce ukončit se aktivity v akci přechodu spustí a pak se nový stav převede na a naplánují se jeho akce vstupu.  
  
> [!NOTE]
> Při ladění pracovního postupu stavového stroje můžete zarážky umístit do aktivity kořenového stavového počítače a stavy v pracovním postupu stavového stroje. Zarážky se nedají umístit přímo na přechody, ale můžou se umístit na všechny aktivity obsažené v rámci stavů a přechodů.  
  
## <a name="creating-and-configuring-transitions"></a>Vytváření a konfigurace přechodů  
 Všechny stavy musí mít alespoň jeden přechod, s výjimkou konečného stavu, který nesmí mít žádné přechody. Přechody mohou být přidány po přidání stavu do pracovního postupu stavového stroje, nebo mohou být vytvořeny, protože stav je vyřazen.  
  
 Chcete-li <xref:System.Activities.Statements.State> přidat a vytvořit přechod v jednom kroku, přetáhněte aktivitu **stavu** z části **Stavový počítač** v **sadě nástrojů** a umístěte ji do jiného stavu v Návrháři postupu. Když <xref:System.Activities.Statements.State> je přetažení nad jiným <xref:System.Activities.Statements.State>, zobrazí se kolem sebe <xref:System.Activities.Statements.State>čtyři trojúhelníky. Pokud je vyhozena na jeden ze čtyř trojúhelníků, je přidána do stavového počítače a přechod je vytvořen ze zdroje <xref:System.Activities.Statements.State> do vyřazeného cíle <xref:System.Activities.Statements.State>. <xref:System.Activities.Statements.State> Další informace najdete v tématu [Přechod k Návrháři aktivit](/visualstudio/workflow-designer/transition-activity-designer).  
  
 Chcete-li vytvořit přechod po přidání stavu, existují dvě možnosti. První možností je přetáhnout stav z plochy návrháře pracovního postupu a najeďte ho na stávající stav a umístit ho na jeden z bodů odkládacích souborů. To je velmi podobné metodě popsané v předchozí části. Můžete také umístit ukazatel myši na požadovaný zdrojový stav a přetáhnout čáru do požadovaného cílového stavu.  
  
> [!NOTE]
> Jeden stav stavového počítače může mít až 76 přechodů vytvořených pomocí návrháře pracovních postupů. Omezení přechodů pro stav pracovních postupů vytvořených mimo návrháře je omezeno pouze systémovými prostředky.  
  
 Přechod může mít <xref:System.Activities.Statements.Transition.Trigger%2A> <xref:System.Activities.Statements.Transition.Condition%2A> a.<xref:System.Activities.Statements.Transition.Action%2A> Při dokončení <xref:System.Activities.Statements.State.Entry%2A> akce <xref:System.Activities.Statements.Transition.Trigger%2A> stavu zdroje přechodu je naplánován přechod. <xref:System.Activities.Statements.Transition.Trigger%2A> Obvykle je aktivita, která čeká na výskyt určitého typu události, ale může to být jakákoli aktivita nebo žádná aktivita. Po dokončení <xref:System.Activities.Statements.Transition.Trigger%2A> <xref:System.Activities.Statements.Transition.Condition%2A>aktivity se vyhodnotí, jestli je k dispozici. Pokud není žádná <xref:System.Activities.Statements.Transition.Trigger%2A> aktivita, <xref:System.Activities.Statements.Transition.Condition%2A> je okamžitě vyhodnocena. Pokud je podmínka vyhodnocena `false`jako, přechod je zrušen <xref:System.Activities.Statements.Transition.Trigger%2A> a aktivita pro všechny přechody ze stavu budou přeplánována. Pokud existují další přechody, které sdílejí stejný zdrojový stav jako aktuální přechod, tyto <xref:System.Activities.Statements.Transition.Trigger%2A> akce se zruší a naplánují také. Pokud se <xref:System.Activities.Statements.Transition.Condition%2A> vyhodnotí `true`jako nebo není k dispozici <xref:System.Activities.Statements.State.Exit%2A> žádná podmínka, je provedena akce stavu <xref:System.Activities.Statements.Transition.Action%2A> zdroje a následně je proveden přechod. Po dokončení řízení projde do **cílového stavu** <xref:System.Activities.Statements.Transition.Action%2A>  
  
 Přechody, které sdílí společnou aktivační událost, se označují jako přechody sdílených triggerů. Každý přechod ve skupině přechodů sdílených triggerů má stejný Trigger, ale jedinečný <xref:System.Activities.Statements.Transition.Condition%2A> a akci. Chcete-li do přechodu přidat další akce a vytvořit sdílený přechod, klikněte na kroužek, který indikuje začátek požadovaného přechodu a přetáhněte ho do požadovaného stavu. Nový přechod bude sdílet stejný Trigger jako počáteční přechod, ale bude mít jedinečnou podmínku a akci. Sdílené přechody je také možné vytvořit v Návrháři přechodu kliknutím na **přidat přechod sdílené triggery** v dolní části návrháře přechodu a následným výběrem požadovaného cílového stavu ze stavů k **připojení** . rozevírací seznam.  
  
> [!NOTE]
> Všimněte si, že <xref:System.Activities.Statements.Transition.Condition%2A> Pokud je z přechodu vyhodnocen `False` (nebo všechny podmínky přechodu na sdílený Trigger vyhodnoceny na `False`hodnotu), přechod nebude proveden a všechny aktivační události pro všechny přechody ze stavu budou změněn.  
  
 Další informace o vytváření pracovních postupů stavových počítačů najdete [v tématu How to: Vytvořte](how-to-create-a-state-machine-workflow.md)pracovní postup stavového stroje, [Návrhář aktivity StateMachine](/visualstudio/workflow-designer/statemachine-activity-designer), Návrhář aktivity [stavu](/visualstudio/workflow-designer/state-activity-designer), [Návrhář aktivity FinalState](/visualstudio/workflow-designer/finalstate-activity-designer)a [Návrhář aktivity přechodu](/visualstudio/workflow-designer/transition-activity-designer).  
  
## <a name="state-machine-terminology"></a>Terminologie stavového stroje  
 Tato část definuje slovník stavového počítače použitý v rámci tohoto tématu.  
  
 Stav  
 Jednotka Basic, která vytváří Stavový počítač. Stavový počítač může být v každém okamžiku v jednom stavu.  
  
 Akce vstupu  
 Aktivita spuštěná při vstupu do stavu  
  
 Akce ukončení  
 Aktivita spuštěná při ukončování stavu  
  
 Transition  
 Směrná relace mezi dvěma stavy, které představují kompletní odpověď stavového počítače na výskyt události konkrétního typu.  
  
 Sdílený přechod  
 Přechod, který sdílí stav zdroje a Trigger s jedním nebo více přechody, ale má jedinečnou podmínku a akci.  
  
 Trigger  
 Spuštění aktivity, která způsobí, že dojde k přechodu.  
  
 Podmínka  
 Omezení, které se musí vyhodnotit, `true` když dojde k triggeru, aby se přechod dokončil.  
  
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

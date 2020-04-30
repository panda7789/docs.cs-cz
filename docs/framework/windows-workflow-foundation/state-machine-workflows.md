---
title: Pracovní postupy stavového stroje
ms.date: 03/30/2017
ms.assetid: 344caacd-bf3b-4716-bd5a-eca74fc5a61d
ms.openlocfilehash: 12f6383a52c7eaf0d66ce6680f66a5df0b314dfd
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595933"
---
# <a name="state-machine-workflows"></a>Pracovní postupy stavového stroje
Stavový počítač je dobře známé paradigma pro vývoj programů. <xref:System.Activities.Statements.StateMachine> Aktivitu spolu s <xref:System.Activities.Statements.State>, <xref:System.Activities.Statements.Transition>a další aktivity lze použít k sestavování pracovních postupů pro stavové zařízení. Toto téma poskytuje přehled o vytváření pracovních postupů stavových počítačů.  
  
## <a name="state-machine-workflow-overview"></a>Přehled pracovního postupu stavového stroje  
 Pracovní postupy stavového počítače poskytují styl modelování, pomocí kterého můžete modelovat svůj pracovní postup způsobem řízeným událostmi. <xref:System.Activities.Statements.StateMachine> Aktivita obsahuje stavy a přechody, které tvoří logiku stavového počítače a lze je použít kdekoli, kde lze použít aktivitu. V modulu runtime stavového stroje je několik tříd:  
  
- <xref:System.Activities.Statements.StateMachine>  
  
- <xref:System.Activities.Statements.State>  
  
- <xref:System.Activities.Statements.Transition>  
  
 Chcete-li vytvořit pracovní postup stavového stroje, jsou do <xref:System.Activities.Statements.StateMachine> aktivity přidány stavy a přechody slouží k řízení toku mezi stavy. Následující snímek obrazovky popisuje, jak v [kurzu Začínáme](getting-started-tutorial.md) [vytvořit pracovní postup stavového stroje](how-to-create-a-state-machine-workflow.md), zobrazuje pracovní postup stavového stroje se třemi stavy a třemi přechody. **Inicializační cíl** je počáteční stav a představuje první stav v pracovním postupu. To je určeno řádkem, který je z **počátečního** uzlu od začátku. Konečný stav pracovního postupu má název **FinalState**a představuje bod, ve kterém byl pracovní postup dokončen.  
  
 ![Obrázek zobrazující pracovní postup dokončeného stavového počítače.](./media/state-machine-workflows/complete-state-machine-workflow.jpg)  
  
 Pracovní postup stavového stroje musí mít pouze jeden počáteční stav a alespoň jeden konečný stav. Každý stav, který není konečným stavem, musí mít alespoň jeden přechod. V následujících částech jsou pokryty vytváření a konfigurace stavů a přechodů.  
  
## <a name="creating-and-configuring-states"></a>Vytváření a konfigurace stavů  
 <xref:System.Activities.Statements.State> Představuje stav, ve kterém může být Stavový počítač v. Chcete-li <xref:System.Activities.Statements.State> přidat do pracovního postupu, přetáhněte návrháře aktivity **stavu** z části **Stavový počítač** v **panelu nástrojů** a přetáhněte jej na <xref:System.Activities.Statements.StateMachine> aktivitu na Návrhář postupu provádění ploše pro Windows.  
  
 ![Snímek obrazovky oddílu Stavový počítač v sadě nástrojů](./media/state-machine-workflows/state-machine-section-toolbox.jpg)  
  
 Chcete-li konfigurovat stav jako **počáteční**, klikněte pravým tlačítkem myši na stav a vyberte možnost **nastavit jako počáteční stav**. Kromě toho, pokud neexistuje aktuální počáteční stav, lze počáteční stav označit přetažením čáry z **počátečního** uzlu v horní části pracovního postupu do požadovaného stavu. Když je <xref:System.Activities.Statements.StateMachine> aktivita vyřazena do návrháře pracovních postupů, je předem nakonfigurována s počátečním stavem s názvem **State1**. Pracovní postup stavového stroje musí mít pouze jeden počáteční stav.  
  
 Stav, který představuje ukončovací stav ve stavovém počítači, se nazývá konečný stav. Konečný stav je stav, který má <xref:System.Activities.Statements.State.IsFinal%2A> vlastnost nastavenou na `true`, nemá žádnou <xref:System.Activities.Statements.State.Exit%2A> aktivitu a z něj pocházejí žádné přechody. Chcete-li do pracovního postupu přidat konečný stav, přetáhněte návrháře aktivity **FinalState** z oddílu **Stavový počítač** v **sadě nástrojů** a umístěte jej do <xref:System.Activities.Statements.StateMachine> aktivity na Návrhář postupu provádění ploše pro Windows. Pracovní postup stavového stroje musí mít alespoň jeden konečný stav.  
  
### <a name="configuring-entry-and-exit-actions"></a>Konfigurace akcí vstupu a výstupu  
 Stav může mít <xref:System.Activities.Statements.State.Entry%2A> <xref:System.Activities.Statements.State.Exit%2A> akci a. (Stav nakonfigurovaný jako konečný stav může mít jenom akci položky). Když instance pracovního postupu vstoupí do stavu, spustí se všechny aktivity v akci vstupu. Po dokončení akce zadání se naplánují aktivační události pro přechody stavu. Když je potvrzen přechod do jiného stavu, jsou provedeny aktivity v akci ukončení, i když se změní stav zpět do stejného stavu. Po dokončení akce ukončit se aktivity v akci přechodu spustí a pak se nový stav převede na a naplánují se jeho akce vstupu.  
  
> [!NOTE]
> Při ladění pracovního postupu stavového stroje můžete zarážky umístit do aktivity kořenového stavového počítače a stavy v pracovním postupu stavového stroje. Zarážky se nedají umístit přímo na přechody, ale můžou se umístit na všechny aktivity obsažené v rámci stavů a přechodů.  
  
## <a name="creating-and-configuring-transitions"></a>Vytváření a konfigurace přechodů  
 Všechny stavy musí mít alespoň jeden přechod, s výjimkou konečného stavu, který nesmí mít žádné přechody. Přechody mohou být přidány po přidání stavu do pracovního postupu stavového stroje, nebo mohou být vytvořeny, protože stav je vyřazen.  
  
 Chcete-li <xref:System.Activities.Statements.State> přidat a vytvořit přechod v jednom kroku, přetáhněte aktivitu **stavu** z části **Stavový počítač** v **sadě nástrojů** a umístěte ji do jiného stavu v Návrháři postupu. Když <xref:System.Activities.Statements.State> je přetažení nad jiným <xref:System.Activities.Statements.State>, zobrazí se kolem sebe <xref:System.Activities.Statements.State>čtyři trojúhelníky. Pokud <xref:System.Activities.Statements.State> je vyhozena na jeden ze čtyř trojúhelníků, je přidána do stavového počítače a přechod je vytvořen ze zdroje <xref:System.Activities.Statements.State> do vyřazeného cíle. <xref:System.Activities.Statements.State> Další informace najdete v tématu [Přechod k Návrháři aktivit](/visualstudio/workflow-designer/transition-activity-designer).  
  
 Chcete-li vytvořit přechod po přidání stavu, existují dvě možnosti. První možností je přetáhnout stav z plochy návrháře pracovního postupu a najeďte ho na stávající stav a umístit ho na jeden z bodů odkládacích souborů. To je velmi podobné metodě popsané v předchozí části. Můžete také umístit ukazatel myši na požadovaný zdrojový stav a přetáhnout čáru do požadovaného cílového stavu.  
  
> [!NOTE]
> Jeden stav stavového počítače může mít až 76 přechodů vytvořených pomocí návrháře pracovních postupů. Omezení přechodů pro stav pracovních postupů vytvořených mimo návrháře je omezeno pouze systémovými prostředky.  
  
 Přechod může mít <xref:System.Activities.Statements.Transition.Trigger%2A> <xref:System.Activities.Statements.Transition.Condition%2A>a <xref:System.Activities.Statements.Transition.Action%2A>. Při dokončení <xref:System.Activities.Statements.State.Entry%2A> akce <xref:System.Activities.Statements.Transition.Trigger%2A> stavu zdroje přechodu je naplánován přechod. Obvykle <xref:System.Activities.Statements.Transition.Trigger%2A> je aktivita, která čeká na výskyt určitého typu události, ale může to být jakákoli aktivita nebo žádná aktivita. Po dokončení <xref:System.Activities.Statements.Transition.Trigger%2A> aktivity se vyhodnotí <xref:System.Activities.Statements.Transition.Condition%2A>, jestli je k dispozici. Pokud není žádná <xref:System.Activities.Statements.Transition.Trigger%2A> aktivita, <xref:System.Activities.Statements.Transition.Condition%2A> je okamžitě vyhodnocena. Pokud je podmínka vyhodnocena `false`jako, přechod je zrušen a <xref:System.Activities.Statements.Transition.Trigger%2A> aktivita pro všechny přechody ze stavu budou přeplánována. Pokud existují další přechody, které sdílejí stejný zdrojový stav jako aktuální přechod, tyto <xref:System.Activities.Statements.Transition.Trigger%2A> akce se zruší a naplánují také. Pokud se <xref:System.Activities.Statements.Transition.Condition%2A> vyhodnotí `true`jako nebo není k dispozici žádná podmínka, <xref:System.Activities.Statements.State.Exit%2A> je provedena akce stavu zdroje a následně <xref:System.Activities.Statements.Transition.Action%2A> je proveden přechod. Po <xref:System.Activities.Statements.Transition.Action%2A> dokončení řízení projde do **cílového** stavu  
  
 Přechody, které sdílí společnou aktivační událost, se označují jako přechody sdílených triggerů. Každý přechod ve skupině přechodů sdílených triggerů má stejný Trigger, ale jedinečný <xref:System.Activities.Statements.Transition.Condition%2A> a akci. Chcete-li do přechodu přidat další akce a vytvořit sdílený přechod, klikněte na kroužek, který indikuje začátek požadovaného přechodu a přetáhněte ho do požadovaného stavu. Nový přechod bude sdílet stejný Trigger jako počáteční přechod, ale bude mít jedinečnou podmínku a akci. Sdílené přechody je také možné vytvořit v Návrháři přechodu kliknutím na **přidat přechod sdílené triggery** v dolní části návrháře přechodu a pak výběrem požadovaného cílového stavu z rozevíracího seznamu **dostupné stavy pro připojení** .  
  
> [!NOTE]
> Všimněte si, že <xref:System.Activities.Statements.Transition.Condition%2A> Pokud je z přechodu vyhodnocen `False` (nebo všechny podmínky přechodu na sdílený Trigger vyhodnoceny na `False`hodnotu), přechod nebude proveden a všechny aktivační události pro všechny přechody ze stavu budou přeplánovány.  
  
 Další informace o vytváření pracovních postupů stavových počítačů najdete v tématu [Postupy: vytvoření pracovního postupu stavového stroje](how-to-create-a-state-machine-workflow.md), [návrháře aktivit StateMachine](/visualstudio/workflow-designer/statemachine-activity-designer), návrháře aktivity [stavu](/visualstudio/workflow-designer/state-activity-designer), [Návrháře aktivity FinalState](/visualstudio/workflow-designer/finalstate-activity-designer)a [Návrháře přechodu aktivit](/visualstudio/workflow-designer/transition-activity-designer).  
  
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
  
## <a name="see-also"></a>Viz také

- [Postupy: Vytvoření pracovního postupu stavového stroje](how-to-create-a-state-machine-workflow.md)
- [Návrhář aktivity StateMachine](/visualstudio/workflow-designer/statemachine-activity-designer)
- [Návrhář aktivity State](/visualstudio/workflow-designer/state-activity-designer)
- [Návrhář aktivity FinalState](/visualstudio/workflow-designer/finalstate-activity-designer)
- [Návrhář aktivity Transition](/visualstudio/workflow-designer/transition-activity-designer)

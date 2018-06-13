---
title: Pracovní postupy stavu počítače
ms.date: 03/30/2017
ms.assetid: 344caacd-bf3b-4716-bd5a-eca74fc5a61d
ms.openlocfilehash: a6dedffda6654cb0acb7ab507129cba9f0bdb7f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519636"
---
# <a name="state-machine-workflows"></a>Pracovní postupy stavu počítače
Stavový stroj je dobře známé zlepší pro vývoj programy. <xref:System.Activities.Statements.StateMachine> Aktivity, spolu s <xref:System.Activities.Statements.State>, <xref:System.Activities.Statements.Transition>, a dalších aktivit můžete použít k sestavení stavu počítače pracovního postupu programy. Toto téma obsahuje přehled vytváření pracovních postupů stav počítače.  
  
## <a name="state-machine-workflow-overview"></a>Přehled stavu počítače pracovního postupu  
 Pracovní postupy stavu počítače zadejte modelování styl, pomocí kterého můžete model pracovní postup způsobem založeného na událostech. A <xref:System.Activities.Statements.StateMachine> aktivity obsahuje stavy a přechody, které tvoří logiku stavu počítače a lze použít kdekoli aktivitu je možné. V modulu runtime stavu počítače jsou několik tříd:  
  
-   <xref:System.Activities.Statements.StateMachine>  
  
-   <xref:System.Activities.Statements.State>  
  
-   <xref:System.Activities.Statements.Transition>  
  
 Pokud chcete vytvořit pracovní postup stavového stroje, jsou stavy přidány do <xref:System.Activities.Statements.StateMachine> používají aktivity a přechody řídit tok mezi stavy. Na následujícím snímku obrazovky z [kurzu Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) krok [postup: vytvoření pracovního postupu stavu počítače](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md), zobrazuje stav pracovního postupu počítač s tři stavy a přechody tři. **Inicializace cíl** je počáteční stav a představuje první stav v pracovním postupu. To je určen čára vedoucí k z **spustit** uzlu. Konečný stav v pracovním postupu jmenuje **FinalState**a představuje bod dokončení pracovního postupu.  
  
 ![Dokončit pracovní postup stavového stroje](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 Pracovní postup stavového stroje musí mít pouze jednu počáteční stav a alespoň jeden konečného stavu. Každý stav, který není do konečného stavu musí mít alespoň jeden přechod. Následující části se věnují vytváření a konfiguraci stavy a přechody.  
  
## <a name="creating-and-configuring-states"></a>Vytváření a konfiguraci stavy  
 A <xref:System.Activities.Statements.State> představuje stavu, ve kterém může být stav stavového stroje v. Přidat <xref:System.Activities.Statements.State> do pracovního postupu, přetáhněte **stavu** Návrhář aktivity z **stavu počítače** části **sada nástrojů** a umístěte jej do <xref:System.Activities.Statements.StateMachine> aktivity na [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] prostor.  
  
 ![WF4 Stavu aktivity počítače](../../../docs/framework/windows-workflow-foundation/media/netframework4platformupdate1statemachineactivities.jpg "NETFramework4PlatformUpdate1StateMachineActivities")  
  
 Ke konfiguraci stavu, jako **počáteční stav**, klikněte pravým tlačítkem na stav a vyberte **nastavit jako počáteční stav**. Kromě toho, pokud není žádný aktuální počáteční stav, počáteční stav lze označit tak, že přetáhnete řádek z **spustit** uzlu v horní části pracovního postupu požadovaný stav. Když <xref:System.Activities.Statements.StateMachine> aktivity umístění na návrháře pracovních postupů, je předem nakonfigurovaný s počáteční stav s názvem **State1**. Pracovní postup stavového stroje musí mít pouze jednu počáteční stav.  
  
 Stav, který představuje ukončující stavu stavový stroj je volána konečného stavu. Konečný stav je stav, který má jeho <xref:System.Activities.Statements.State.IsFinal%2A> vlastnost nastavena na hodnotu `true`, neobsahuje žádné <xref:System.Activities.Statements.State.Exit%2A> aktivity a žádné přechody pocházející z něj. Pokud chcete přidat do konečného stavu do pracovního postupu, přetáhněte **FinalState** Návrhář aktivity z **stavu počítače** části **sada nástrojů** a umístěte jej do <xref:System.Activities.Statements.StateMachine> aktivity na [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] prostor. Pracovní postup stavového stroje musí mít alespoň jeden konečného stavu.  
  
### <a name="configuring-entry-and-exit-actions"></a>Konfigurace vstupní a výstupní akce  
 Stav může mít <xref:System.Activities.Statements.State.Entry%2A> a <xref:System.Activities.Statements.State.Exit%2A> akce. (Stavu nakonfigurovaný jako konečného stavu může mít pouze akce položku). Pokud instance pracovního postupu vstupuje do stavu, spustit všechny aktivity v akci pro položku. Po dokončení akce položky jsou naplánovány aktivačních událostí pro přechody stavu. Při přechodu na jiný stav potvrdí, provedení aktivity v akci pro ukončení, i když přechodů mezi stavy zpět do stejného stavu. Po dokončení akce ukončení aktivity v přechodu na akci provést a potom nový stav převedena na a jeho položky Akce jsou naplánovány.  
  
> [!NOTE]
>  Při ladění pracovní postup stavového stroje, zarážky se může u kořenové stavu počítače aktivity a stavy v pracovním postupu stav počítače. Zarážky nesmí být uvedeny přímo na přechody, ale může být umístěn na žádné aktivity obsažené v stavy a přechody.  
  
## <a name="creating-and-configuring-transitions"></a>Vytváření a konfiguraci přechody  
 Všechny stavy musí mít alespoň jeden přechodu, s výjimkou konečného stavu, který nemusí mít všechny přechody. Přechody lze přidat po stavu se přidá do pracovního postupu stavu počítače, nebo se může vytvořit, protože stav je vyřazeno.  
  
 Přidat <xref:System.Activities.Statements.State> a vytvoření přechodu v jednom kroku, přetáhněte **stavu** aktivity z **stavový stroj** části **sada nástrojů** a najeďte myší na jiný stav v Návrháři pracovních postupů. Když taženou <xref:System.Activities.Statements.State> je oproti jinému <xref:System.Activities.Statements.State>, kolem druhé se zobrazí čtyři trojúhelníčky <xref:System.Activities.Statements.State>. Pokud <xref:System.Activities.Statements.State> vyřazen na jednom ze čtyř trojúhelníčky, se přidá do stavu počítače a vytvoření přechodu ze zdroje <xref:System.Activities.Statements.State> vynechaných cílovou <xref:System.Activities.Statements.State>. Další informace najdete v tématu [Návrhář aktivity přechod](/visualstudio/workflow-designer/transition-activity-designer).  
  
 Pokud chcete vytvořit přechod po přidání stavu, existují dvě možnosti. První možností je stav z plochu návrháře pracovního postupu a pozastavte ukazatel myši nad existující stavu přetažení ji na jeden z bodů vyřaďte. Toto je velmi podobné metody popsané v předchozí části. Můžete také najeďte myší stavu požadovaného zdroje a přetáhněte ji na řádku požadované cílové stavu.  
  
> [!NOTE]
>  Jednoho stavu ve stavu počítač může mít až 76 přechody vytvořené pomocí návrháře pracovních postupů. Limit přechody stavu vytvořen vně návrháře pracovních postupů pro je omezena pouze systémové prostředky.  
  
 Může mít přechod <xref:System.Activities.Statements.Transition.Trigger%2A>, <xref:System.Activities.Statements.Transition.Condition%2A>a <xref:System.Activities.Statements.Transition.Action%2A>. Přechod na <xref:System.Activities.Statements.Transition.Trigger%2A> je naplánováno při stavu zdroje je přechod <xref:System.Activities.Statements.State.Entry%2A> se dokončila akce. Obvykle <xref:System.Activities.Statements.Transition.Trigger%2A> je aktivitou, která čeká na nějaký typ událostem, ale žádnou aktivitu, nebo žádná aktivita může být vůbec. Jednou <xref:System.Activities.Statements.Transition.Trigger%2A> aktivity skončí, <xref:System.Activities.Statements.Transition.Condition%2A>, pokud existuje, vyhodnotí. Pokud není žádná <xref:System.Activities.Statements.Transition.Trigger%2A> aktivity potom <xref:System.Activities.Statements.Transition.Condition%2A> okamžitě vyhodnotí. Pokud je podmínka vyhodnocena jako `false`, byla zrušena, přechodu a <xref:System.Activities.Statements.Transition.Trigger%2A> jsou přeplánovat aktivity pro všechny přechody ze stavu. Pokud existují další přechody, které sdílejí stejnou stavu zdroje jako aktuální přechod těchto <xref:System.Activities.Statements.Transition.Trigger%2A> zrušena a také přeplánovat akcí. Pokud <xref:System.Activities.Statements.Transition.Condition%2A> vyhodnotí jako `true`, nebo je k dispozici žádná podmínka, pak se <xref:System.Activities.Statements.State.Exit%2A> provedení akce stavu zdroje a potom <xref:System.Activities.Statements.Transition.Action%2A> přechodu se spustí. Když <xref:System.Activities.Statements.Transition.Action%2A> dokončení ovládací prvek předává do **cíl** stavu  
  
 Přechody, které sdílejí společné aktivační událost se označují jako přechody sdílené aktivační události. Každý přechod ve skupině přechodů sdílené aktivační událost má stejné aktivační událost, ale jedinečný <xref:System.Activities.Statements.Transition.Condition%2A> a akce. Pokud chcete přidat další akce pro přechod a vytvořit sdílený přechodu, klikněte na kruh označující začátek požadované přechodu a přetáhněte ji do požadovaného stavu. Nový přechod budou sdílet stejnou aktivační událost jako počáteční přechodu, ale bude mít jedinečný podmínku a akce. Sdílené přechody můžete také vytvořit z v Návrháři přechod kliknutím **přidat sdílený aktivační událost přechod** v dolní části návrháře přechod a pak vybrat požadovanou cílového stavu z  **Dostupné stavy připojení** rozevíracího seznamu.  
  
> [!NOTE]
>  Všimněte si, že pokud <xref:System.Activities.Statements.Transition.Condition%2A> přechodu se vyhodnocuje `False` (nebo všechny podmínky přechod sdílené aktivační událost vyhodnocení `False`), přechod nedojde a budou všechny aktivační události pro všechny přechody ze stavu znovu naplánován.  
  
 Další informace o vytváření pracovních postupů stavu počítače najdete v tématu [postupy: vytvoření pracovního postupu stavu počítače](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md), [Návrhář aktivity StateMachine](/visualstudio/workflow-designer/statemachine-activity-designer), [Návrhář aktivity stavu](/visualstudio/workflow-designer/state-activity-designer), [Návrhář aktivity FinalState](/visualstudio/workflow-designer/finalstate-activity-designer), a [přechod Návrhář aktivity](/visualstudio/workflow-designer/transition-activity-designer).  
  
## <a name="state-machine-terminology"></a>Terminologie stavu počítače  
 Tento oddíl definuje slovníku stavu počítače v tomto tématu.  
  
 Stav  
 Základní jednotka, ve které vytvoří stav počítače. Stav počítač může být v jednom stavu konkrétní kdykoli.  
  
 Záznam akcí  
 Provést při zadávání stavu aktivity  
  
 Ukončete akci  
 Aktivita spustit při ukončení stavu  
  
 Přechod  
 Řízené vztah mezi dvěma stavy, které představuje dokončení odpověď stavu počítače k výskytu události určitého typu.  
  
 Sdílené přechodu  
 Přechod, který sdílí stavu zdroje a aktivační události jeden nebo více přechody, ale má jedinečný podmínku a akce.  
  
 Aktivační události  
 Spouštěcí aktivitu, která způsobí, že dojde k přechodu.  
  
 Podmínka  
 Omezení, které se musí vyhodnotit `true` po aktivační událost probíhá v pořadí pro přechod na Dokončit.  
  
 Akce přechodu  
 Aktivita, která se spustí při provádění určitých přechod.  
  
 Podmíněné přechodu  
 Přechod s explicitní podmínku.  
  
 Vlastní přechodu  
 Přechod, který tranzit ze stavu na sebe sama.  
  
 Počáteční stav  
 Stav, který představuje bod počáteční stav stavového stroje.  
  
 Konečný stav  
 Stav, který představuje dokončení stav stavového stroje.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytvoření pracovního postupu stavového stroje](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md)  
 [Návrhář aktivity StateMachine](/visualstudio/workflow-designer/statemachine-activity-designer)  
 [Návrhář aktivity State](/visualstudio/workflow-designer/state-activity-designer)  
 [Návrhář aktivity FinalState](/visualstudio/workflow-designer/finalstate-activity-designer)  
 [Návrhář aktivity Transition](/visualstudio/workflow-designer/transition-activity-designer)

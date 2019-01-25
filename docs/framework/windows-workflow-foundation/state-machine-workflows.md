---
title: Pracovní postupy stavového stroje
ms.date: 03/30/2017
ms.assetid: 344caacd-bf3b-4716-bd5a-eca74fc5a61d
ms.openlocfilehash: 89819f6b37fdaf601cf4e8b99fd5156c8e40af99
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521293"
---
# <a name="state-machine-workflows"></a>Pracovní postupy stavového stroje
Stavový stroj je dobře známé paradigma pro vývoj aplikací. <xref:System.Activities.Statements.StateMachine> Aktivity, spolu s <xref:System.Activities.Statements.State>, <xref:System.Activities.Statements.Transition>, a dalších aktivit slouží k vytváření programů stavu počítače pracovního postupu. Toto téma obsahuje přehled o vytváření pracovní postupy stavu počítače.  
  
## <a name="state-machine-workflow-overview"></a>Přehled pracovního postupu stavového stroje  
 Pracovní postupy stavového stroje zadejte styl modelování, pomocí kterého lze modelovat pracovního postupu způsobem založený na událostech. A <xref:System.Activities.Statements.StateMachine> aktivita obsahuje stavy a přechody, které tvoří logiky stavového počítače a mohou být použity kdekoli lze použít aktivitu. V modulu runtime stavu počítače jsou několik tříd:  
  
-   <xref:System.Activities.Statements.StateMachine>  
  
-   <xref:System.Activities.Statements.State>  
  
-   <xref:System.Activities.Statements.Transition>  
  
 Pokud chcete vytvořit pracovní postup stavového stroje, jsou stavy přidány do <xref:System.Activities.Statements.StateMachine> používají aktivity a přechody řídit tok mezi stavy. Na následujícím snímku obrazovky z [kurz Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) krok [jak: Vytvořit pracovní postup stavového stroje](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md), zobrazuje pracovní postup stavového stroje s tři stavy a přechody tři. **Inicializovat cílové** je počáteční stav a představuje první stav v pracovním postupu. To je označen řádek, což vede k němu z **Start** uzlu. Konečný stav v pracovním postupu jmenuje **FinalState**a reprezentuje bod dokončení pracovního postupu.  
  
 ![Dokončení pracovního postupu stavového stroje](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 Pracovní postup stavového stroje musí mít jeden a pouze jeden počáteční stav a aspoň jeden koncový stav. Každý stav, který není konečný stav musí mít aspoň jeden přechod. Následující části se věnují vytváření a konfiguraci stavy a přechody.  
  
## <a name="creating-and-configuring-states"></a>Vytváření a konfiguraci stavů  
 A <xref:System.Activities.Statements.State> představuje stavu, ve kterém může být stavového stroje v. Přidat <xref:System.Activities.Statements.State> do pracovního postupu, přetáhněte **stavu** Návrhář aktivity z **stavového stroje** část **nástrojů** a umístěte ho do <xref:System.Activities.Statements.StateMachine> aktivity [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] povrchu.  
  
 ![WF4 State Machine Activities](../../../docs/framework/windows-workflow-foundation/media/netframework4platformupdate1statemachineactivities.jpg "NETFramework4PlatformUpdate1StateMachineActivities")  
  
 Konfigurace stavu jako **počáteční stav**, klikněte pravým tlačítkem na stav a vyberte **nastavit jako počáteční stav**. Kromě toho pokud neexistuje žádné aktuální počáteční stav, počáteční stav lze označit přetažením řádek z **Start** uzlu v horní části pracovního postupu do požadovaného stavu. Když <xref:System.Activities.Statements.StateMachine> aktivity je přetaženy návrháře postupu provádění, je nakonfigurovaná s počátečním stavem s názvem **nazvané State1**. Pracovní postup stavového stroje musí mít jeden a pouze jeden počáteční stav.  
  
 Stav, který představuje ukončující stav stavového stroje se nazývá koncový stav. Konečný stav je stavu, ve kterém má jeho <xref:System.Activities.Statements.State.IsFinal%2A> vlastnost nastavena na hodnotu `true`, nemá žádné <xref:System.Activities.Statements.State.Exit%2A> aktivity a žádné přechody pocházející z něj. Přidat koncový stav do pracovního postupu, přetáhněte **FinalState** Návrhář aktivity z **stavového stroje** část **nástrojů** a umístěte ho do <xref:System.Activities.Statements.StateMachine> aktivitu na [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] povrchu. Pracovní postup stavového stroje musí mít aspoň jeden koncový stav.  
  
### <a name="configuring-entry-and-exit-actions"></a>Konfigurace vstupu a výstupu akce  
 Stav může mít <xref:System.Activities.Statements.State.Entry%2A> a <xref:System.Activities.Statements.State.Exit%2A> akce. (Stav nakonfigurovaný jako koncový stav může mít pouze akce položky). Když instance pracovního postupu přejde do stavu, spustit všechny aktivity v záznam akce. Po dokončení akce položky jsou naplánované aktivační procedury přechodů. Při přechodu na jiný stav potvrdí, aktivity ve výstupní akci jsou prováděny, i v případě, že přechody stavu zpět do stejného stavu. Po dokončení výstupní akci aktivity v akci tento přechod provést a potom nový stav je převeden na a jeho záznam akce jsou naplánovány.  
  
> [!NOTE]
>  Při ladění pracovní postup stavového stroje, zarážky můžete umístit na kořenovou aktivitou počítače stav a stavy v rámci pracovní postup stavového stroje. Nelze umístit zarážky přímo na přechodů, ale můžete umístit na libovolné aktivity obsažené v rámci stavy a přechody.  
  
## <a name="creating-and-configuring-transitions"></a>Vytváření a konfiguraci přechody  
 Všechny stavy musí mít aspoň jeden přechod, s výjimkou konečného stavu, který nemusí obsahovat všechny přechody. Přechody jsou přidány po stavu je přidán do pracovní postup stavového stroje nebo je lze vytvořit podle stavu se zahodí.  
  
 Přidání <xref:System.Activities.Statements.State> a vytvoření přechodu v jednom kroku, přetáhněte **stavu** aktivita z **stavového stroje** část **nástrojů** a při najetí myší nad jiný stav v Návrháři pracovních postupů. Když přetaženou <xref:System.Activities.Statements.State> je před jiným <xref:System.Activities.Statements.State>, čtyři trojúhelníky se zobrazí kolem nich <xref:System.Activities.Statements.State>. Pokud <xref:System.Activities.Statements.State> se ukončí na jednom ze čtyř trojúhelníků, přidá se do stavového stroje a vytvoření přechodu ze zdroje <xref:System.Activities.Statements.State> do vynechané cíle <xref:System.Activities.Statements.State>. Další informace najdete v tématu [Návrhář aktivity Transition](/visualstudio/workflow-designer/transition-activity-designer).  
  
 Pokud chcete vytvořit přechod po přidání do stavu, existují dvě možnosti. První možností je stav z na plochu návrháře pracovního postupu a při najetí myší nad stávající stav přetáhnout na jednom rozevíracím bodů. To je velmi podobné metody popsané v předchozí části. Můžete také najeďte myší stavu požadovaného zdroje a přetáhněte čáru na požadovaný cílový stav.  
  
> [!NOTE]
>  Jeden stav stavového stroje. může mít až 76 přechody vytvořené pomocí návrháře postupu provádění. Omezení přechodů pro stav pro pracovní postupy vytvořené mimo návrháře je omezen pouze systémové prostředky.  
  
 Může mít s přechodem <xref:System.Activities.Statements.Transition.Trigger%2A>, <xref:System.Activities.Statements.Transition.Condition%2A>a <xref:System.Activities.Statements.Transition.Action%2A>. S přechodem <xref:System.Activities.Statements.Transition.Trigger%2A> je naplánováno po stavu zdroje na přechod <xref:System.Activities.Statements.State.Entry%2A> se dokončila akce. Obvykle <xref:System.Activities.Statements.Transition.Trigger%2A> je aktivitou, která čeká na nějaký typ na výskyt události, ale to může být vůbec žádnou aktivitu, nebo žádná aktivita. Jednou <xref:System.Activities.Statements.Transition.Trigger%2A> dokončení aktivity <xref:System.Activities.Statements.Transition.Condition%2A>, pokud jsou k dispozici, je vyhodnocen. Pokud není žádný <xref:System.Activities.Statements.Transition.Trigger%2A> aktivita pak bude <xref:System.Activities.Statements.Transition.Condition%2A> se okamžitě vyhodnotí. Pokud je podmínka vyhodnocena jako `false`, přechodu se zrušila a <xref:System.Activities.Statements.Transition.Trigger%2A> jsou přeplánovat aktivity pro všechny přechody ze stavu. Pokud existují další přechody, které sdílejí stejný zdroj stavu jako aktuální transakce, tyto <xref:System.Activities.Statements.Transition.Trigger%2A> zrušit a znovu naplánována také akcí. Pokud <xref:System.Activities.Statements.Transition.Condition%2A> vyhodnotí jako `true`, nebo neexistuje žádná podmínka, pak bude <xref:System.Activities.Statements.State.Exit%2A> provedením akce stavu zdroje a pak <xref:System.Activities.Statements.Transition.Action%2A> přechodu je proveden. Když <xref:System.Activities.Statements.Transition.Action%2A> dokončí, řízení se předá **cílové** stavu  
  
 Přechody, které sdílejí běžně používaným triggerem jsou označovány jako přechody sdílené spouštěcí události. Každý přechod ve skupině přechodů sdílené spouštěcí události má stejnou spouštěcí událost, ale jedinečnou <xref:System.Activities.Statements.Transition.Condition%2A> a akce. Přidání další akce k přechodu a vytvořit sdílené přechod, klikněte na kruh, který označuje začátek požadované přechodu a přetáhněte ho do požadovaného stavu. Nový přechod budou sdílet stejnou spouštěcí událost jako počáteční přechodu, ale bude mít jedinečné podmínku a akce. Sdílené přechody lze také vytvořit z v rámci přechodu návrháře kliknutím **přidat sdílené triggeru, přechod** v dolní části návrháře přechod a pak vyberete požadovanou cílovou stavu z  **Dostupné stavy připojení** rozevíracího seznamu.  
  
> [!NOTE]
>  Všimněte si, že pokud <xref:System.Activities.Statements.Transition.Condition%2A> přechodu vyhodnocen `False` (nebo vyhodnotit všechny podmínky sdílené spouštěcí události přechodu `False`), nedojde k přechodu a budou všechny aktivační události pro všechny přechody ze stavu znovu naplánována.  
  
 Další informace o vytváření pracovní postupy stavu počítače, naleznete v tématu [jak: Vytvoření pracovního postupu stavového stroje](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md), [Návrhář aktivity StateMachine](/visualstudio/workflow-designer/statemachine-activity-designer), [stavu Návrhář aktivity](/visualstudio/workflow-designer/state-activity-designer), [Návrhář aktivity Finalstate](/visualstudio/workflow-designer/finalstate-activity-designer)a [Přechod Návrhář aktivity](/visualstudio/workflow-designer/transition-activity-designer).  
  
## <a name="state-machine-terminology"></a>Terminologie stavového stroje  
 Tento oddíl definuje slovník stavu počítače používají v tomto tématu.  
  
 Stav  
 Základní jednotky, ve kterých lze kombinovat stavového stroje. Stavový počítač může být v jednom ze stavů v určitém čase.  
  
 Akce položky  
 Spustí se při zadávání stavu aktivity  
  
 Výstupní akci  
 Spustí se při ukončení stav aktivity  
  
 Přechod  
 Řízené vztah mezi dvěma stavy, které představuje úplnou odpověď stavový počítač na výskyt události určitého typu.  
  
 Sdílené přechodu  
 Přechod, který sdílí stavu zdroje a aktivační události se jeden nebo více přechodů, ale má jedinečný podmínku a akce.  
  
 Trigger  
 Spouštěcí aktivita, která způsobí, že s přechodem na dojít.  
  
 Podmínka  
 Omezení, které se musí vyhodnotit na `true` po triggeru v pořadí pro přechod na dokončení.  
  
 Akce přechodu  
 Aktivita, která se spouští při provádění určitých přechod.  
  
 Podmíněné transakce  
 Přechod s podmínkou explicitní.  
  
 Přechod  
 Přechod, který tranzit ze stavu na sebe sama.  
  
 Počáteční stav  
 Stav, který představuje bod počáteční stav stavového stroje.  
  
 Konečný stav  
 Stav, který představuje dokončení stav stavového stroje.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Vytvoření pracovního postupu stavového stroje](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md)
- [Návrhář aktivity StateMachine](/visualstudio/workflow-designer/statemachine-activity-designer)
- [Návrhář aktivity State](/visualstudio/workflow-designer/state-activity-designer)
- [Návrhář aktivity FinalState](/visualstudio/workflow-designer/finalstate-activity-designer)
- [Návrhář aktivity Transition](/visualstudio/workflow-designer/transition-activity-designer)

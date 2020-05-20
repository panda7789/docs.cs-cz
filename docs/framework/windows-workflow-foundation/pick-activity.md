---
title: Výběr aktivity
description: V rámci Workflow Foundation aktivita výběru zjednodušuje modelování sady triggerů událostí následovaný jejich odpovídajícími obslužnými rutinami.
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: eb59dc20919ed2d30a48f920ad154d4b0d99c41f
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421459"
---
# <a name="pick-activity"></a>Výběr aktivity
<xref:System.Activities.Statements.Pick>Aktivita zjednodušuje modelování sady triggerů událostí následovaný jejich odpovídajícími obslužnými rutinami.  <xref:System.Activities.Statements.Pick>Aktivita obsahuje kolekci <xref:System.Activities.Statements.PickBranch> aktivit, kde každá <xref:System.Activities.Statements.PickBranch> je párování mezi <xref:System.Activities.Statements.PickBranch.Trigger%2A> aktivitou a <xref:System.Activities.Statements.PickBranch.Action%2A> aktivitou.  V době spuštění jsou triggery pro všechny větve spouštěny paralelně.  Po dokončení jedné triggeru se spustí jeho odpovídající akce a všechny ostatní triggery se zruší.  Chování [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> aktivity se podobá <xref:System.Workflow.Activities.ListenActivity> aktivitě .NET Framework 3,5.  
  
 Následující snímek obrazovky z ukázka [použití sady SDK pro výběr aktivity](./samples/using-the-pick-activity.md) zobrazuje aktivitu výběru se dvěma větvemi.  Jedna větev obsahuje aktivační událost s názvem **čtení vstupu**, vlastní aktivita, která čte vstup z příkazového řádku. Druhá větev obsahuje <xref:System.Activities.Statements.Delay> aktivační událost aktivity. Pokud aktivita **čtení vstupu** přijme data před <xref:System.Activities.Statements.Delay> dokončením aktivity, <xref:System.Activities.Statements.Delay> zpoždění se zruší a do konzoly se zapíše pozdrav.  V opačném případě, pokud aktivita **čtení vstupu** neobdrží data v přiděleném čase, bude zrušena a do konzoly bude zapsána zpráva s časovým limitem.  Toto je společný vzor, pomocí kterého lze přidat časový limit k jakékoli akci.  
  
 ![Výběr aktivity](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a>Osvědčené postupy  
 Při použití výběru je větev, která se spustí, větev, jejíž Trigger se dokončí jako první.  V koncepčním případě se všechny triggery spouštějí paralelně a jedna aktivační událost mohla provést většinu logiky předtím, než se zruší dokončením jiného triggeru.  S ohledem na to, že při použití aktivity výběru se má při použití aktivity výběru postupovat, je třeba se zacházet s triggerem, který představuje jedinou událost, a vložit do něj co nejmenší logiku.  V ideálním případě by měl aktivační událost obsahovat pouze dostatečnou logiku pro příjem události a všechny zpracování této události by měly přejít do akce větve.  Tato metoda minimalizuje velikost překryvu mezi spuštěním triggerů.  Zvažte například <xref:System.Activities.Statements.Pick> se dvěma triggery, kde každá aktivační událost obsahuje <xref:System.ServiceModel.Activities.Receive> aktivitu následovanou další logikou.  Pokud další logika představuje bod nečinnosti, existuje možnost, že obě <xref:System.ServiceModel.Activities.Receive> aktivity budou úspěšně dokončeny.  Jedna aktivační událost se kompletně dokončí, zatímco další se částečně dokončí.  V některých scénářích přijímá zprávu a pak částečně dokončuje zpracování je nepřijmoutelné.  Proto při použití integrovaných aktivit zasílání zpráv, jako jsou <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> , zatímco <xref:System.ServiceModel.Activities.Receive> se běžně používají v triggeru, <xref:System.ServiceModel.Activities.SendReply> a pokud je to možné, další logika by měla být vložena do akce.  
  
## <a name="using-the-pick-activity-in-the-designer"></a>Použití aktivity výběru v Návrháři  
 Chcete-li použít příkaz vybrat v návrháři, vyhledejte v sadě nástrojů příkaz **Vybrat** a **operace PickBranch** .  **Vyberte položku vybrat** a přetáhněte ji na plátno.  Ve výchozím nastavení bude nová aktivita **výběru** v Návrháři obsahovat dvě větve.  Chcete-li přidat další větve, přetáhněte aktivitu **operace PickBranch** a umístěte ji vedle existujících větví. Aktivity mohou být do aktivity **výběru** přesunuty buď do oblasti **triggeru** , nebo do oblasti **akcí** všech **operace PickBranch**.  
  
## <a name="using-the-pick-activity-in-code"></a>Použití aktivity výběru v kódu  
 <xref:System.Activities.Statements.Pick>Aktivita se používá k naplnění <xref:System.Activities.Statements.Pick.Branches%2A> kolekce s <xref:System.Activities.Statements.PickBranch> aktivitami. <xref:System.Activities.Statements.PickBranch>Jednotlivé aktivity mají <xref:System.Activities.Statements.PickBranch.Trigger%2A> vlastnost typu <xref:System.Activities.Activity> . Když zadaná aktivita dokončí provádění, <xref:System.Activities.Statements.PickBranch.Action%2A> provede se.  
  
 Následující příklad kódu ukazuje, jak použít <xref:System.Activities.Statements.Pick> aktivitu k implementaci časového limitu aktivity, která čte řádek z konzoly.  
  
```csharp  
Sequence body = new Sequence()  
{  
    Variables = { name },  
    Activities =
   {  
       new System.Activities.Statements.Pick  
        {  
           Branches =
           {  
               new PickBranch  
               {  
                   Trigger = new ReadLine  
                   {  
                      Result = name,  
                      BookmarkName = "name"  
                   },  
                   Action = new WriteLine
                   {
                       Text = ExpressionServices.Convert<string>(ctx => "Hello " +
                           name.Get(ctx))
                   }  
               },  
               new PickBranch  
               {  
                   Trigger = new Delay  
                   {  
                      Duration = new TimeSpan(0, 0, 5)  
                   },  
                   Action = new WriteLine  
                   {  
                      Text = "Time is up."  
                   }  
               }  
           }  
       }  
   }  
};  
```  
  
```xaml  
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <Variable x:TypeArguments="x:String" Name="username" />  
  </Sequence.Variables>  
  <Pick>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <ReadLine BookmarkName="name" Result="username" />  
      </PickBranch.Trigger>  
      <WriteLine>[String.Concat("Hello ", username)]</WriteLine>  
    </PickBranch>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <Delay>00:00:05</Delay>  
      </PickBranch.Trigger>  
      <WriteLine>Time is up.</WriteLine>  
    </PickBranch>  
  </Pick>  
</Sequence>  
```

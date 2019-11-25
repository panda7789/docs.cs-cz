---
title: Výběr aktivity
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: 51caf020042212b570ae915ead00a4225df2c588
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283183"
---
# <a name="pick-activity"></a>Výběr aktivity
Aktivita <xref:System.Activities.Statements.Pick> zjednodušuje modelování sady triggerů událostí následovaný jejich odpovídajícími obslužnými rutinami.  Aktivita <xref:System.Activities.Statements.Pick> obsahuje kolekci aktivit <xref:System.Activities.Statements.PickBranch>, kde jsou jednotlivé <xref:System.Activities.Statements.PickBranch> párování mezi <xref:System.Activities.Statements.PickBranch.Trigger%2A> aktivitou a aktivitou <xref:System.Activities.Statements.PickBranch.Action%2A>.  V době spuštění jsou triggery pro všechny větve spouštěny paralelně.  Po dokončení jedné triggeru se spustí jeho odpovídající akce a všechny ostatní triggery se zruší.  Chování aktivity [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> je podobné aktivitě .NET Framework 3,5 <xref:System.Workflow.Activities.ListenActivity>.  
  
 Následující snímek obrazovky z ukázka [použití sady SDK pro výběr aktivity](./samples/using-the-pick-activity.md) zobrazuje aktivitu výběru se dvěma větvemi.  Jedna větev obsahuje aktivační událost s názvem **čtení vstupu**, vlastní aktivita, která čte vstup z příkazového řádku. Druhá větev má Trigger <xref:System.Activities.Statements.Delay> aktivity. Pokud aktivita **čtení vstupu** přijme data před dokončením <xref:System.Activities.Statements.Delay> aktivity, <xref:System.Activities.Statements.Delay> zpoždění se zruší a do konzoly se zapíše pozdrav.  V opačném případě, pokud aktivita **čtení vstupu** neobdrží data v přiděleném čase, bude zrušena a do konzoly bude zapsána zpráva s časovým limitem.  Toto je společný vzor, pomocí kterého lze přidat časový limit k jakékoli akci.  
  
 ![Výběr aktivity](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a>Osvědčené postupy  
 Při použití výběru je větev, která se spustí, větev, jejíž Trigger se dokončí jako první.  V koncepčním případě se všechny triggery spouštějí paralelně a jedna aktivační událost mohla provést většinu logiky předtím, než se zruší dokončením jiného triggeru.  S ohledem na to, že při použití aktivity výběru se má při použití aktivity výběru postupovat, je třeba se zacházet s triggerem, který představuje jedinou událost, a vložit do něj co nejmenší logiku.  V ideálním případě by měl aktivační událost obsahovat pouze dostatečnou logiku pro příjem události a všechny zpracování této události by měly přejít do akce větve.  Tato metoda minimalizuje velikost překryvu mezi spuštěním triggerů.  Představte si například <xref:System.Activities.Statements.Pick> se dvěma triggery, kde každá aktivační událost obsahuje aktivitu <xref:System.ServiceModel.Activities.Receive> následovanou další logikou.  Pokud další logika zavádí bod nečinnosti, existuje možnost, že obě <xref:System.ServiceModel.Activities.Receive> aktivity budou úspěšně dokončeny.  Jedna aktivační událost se kompletně dokončí, zatímco další se částečně dokončí.  V některých scénářích přijímá zprávu a pak částečně dokončuje zpracování je nepřijmoutelné.  Proto při použití integrovaných aktivit zasílání zpráv, jako jsou <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Receive> se běžně používá v triggeru, <xref:System.ServiceModel.Activities.SendReply> a další logiky by měly být vloženy do akce, kdykoli je to možné.  
  
## <a name="using-the-pick-activity-in-the-designer"></a>Použití aktivity výběru v Návrháři  
 Chcete-li použít příkaz vybrat v návrháři, vyhledejte v sadě nástrojů příkaz **Vybrat** a **operace PickBranch** .  **Vyberte položku vybrat** a přetáhněte ji na plátno.  Ve výchozím nastavení bude nová aktivita **výběru** v Návrháři obsahovat dvě větve.  Chcete-li přidat další větve, přetáhněte aktivitu **operace PickBranch** a umístěte ji vedle existujících větví. Aktivity mohou být do aktivity **výběru** přesunuty buď do oblasti **triggeru** , nebo do oblasti **akcí** všech **operace PickBranch**.  
  
## <a name="using-the-pick-activity-in-code"></a>Použití aktivity výběru v kódu  
 <xref:System.Activities.Statements.Pick> aktivita se používá k naplnění kolekce <xref:System.Activities.Statements.Pick.Branches%2A> s <xref:System.Activities.Statements.PickBranch> aktivitami. <xref:System.Activities.Statements.PickBranch> aktivity mají vlastnost <xref:System.Activities.Statements.PickBranch.Trigger%2A> typu <xref:System.Activities.Activity>. Když zadaná aktivita dokončí provádění, <xref:System.Activities.Statements.PickBranch.Action%2A> se spustí.  
  
 Následující příklad kódu ukazuje, jak použít aktivitu <xref:System.Activities.Statements.Pick> k implementaci časového limitu aktivity, která čte řádek z konzoly.  
  
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
